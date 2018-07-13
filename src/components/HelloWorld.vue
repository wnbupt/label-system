<template>
  <el-container style="height: 500px; border: 1px solid #eee">
    <el-header style="height: 50px; font-weight: bold">知识图谱标注系统</el-header>
    <el-container>
    
      <el-aside width="200px" >
        <el-menu
          default-active="1"
          class="el-menu-vertical-demo"
          >
          <el-menu-item index="1" v-on:click="setShowTable('TechTable')">
            <i class="el-icon-setting"></i>
            <span slot="title">技术关键词标引</span>
          </el-menu-item>

          <el-menu-item index="2" @click="setShowTable('CompanyTable')">
            <i class="el-icon-menu"></i>
            <span slot="title">企业实体标引</span>
          </el-menu-item>

          <el-menu-item index="3" @click="setShowTable('RelationTable')">
            <i class="el-icon-document"></i>
            <span slot="title">关系标引</span>
          </el-menu-item>
        </el-menu>
      </el-aside>

      <el-main>
        <template v-if="showTable === 'TechTable'">
          <el-table :data="tableData" key="TechTable">
            <el-table-column prop="keyword" label="关键词" width="140">
              <template slot-scope="scope">
                <span>人脸识别</span>
              </template>
            </el-table-column>
            <el-table-column prop="origin" label="来源" width="280">
              <template slot-scope="scope">
                <span>新闻<el-tag type='danger' size="mini" style="margin: 0 5px">10</el-tag></span>
                <span>专利<el-tag type='danger' size="mini" style="margin: 0 5px">10</el-tag></span>
              </template>
            </el-table-column>
            <el-table-column prop="operation" label="标注">
              <template slot-scope="scope">
                <el-button type="info" size="mini" @click="open">非同义词</el-button>
                <el-button type="warning" size="mini">同义词</el-button>
                <el-button type="success" size="mini">新技术标签</el-button>
              </template>
            </el-table-column>
          </el-table>
        </template>

        <template v-else-if="showTable === 'CompanyTable'">
          <el-table :data="tableData" key="CompanyTable">
            <el-table-column prop="keyword" label="关键词" width="140">
              <template slot-scope="scope">
                <span>京东</span>
              </template>
            </el-table-column>
            <el-table-column prop="origin" label="来源" width="280">
              <template slot-scope="scope">
                <span>新闻<el-tag type='danger' size="mini" style="margin: 0 5px">10</el-tag></span>
              </template>
            </el-table-column>
            <el-table-column prop="operation" label="标注">
              <template slot-scope="scope">
                <el-button type="warning" size="mini">企业同义词</el-button>
                <el-button type="success" size="mini">新企业实体</el-button>
              </template>
            </el-table-column>
          </el-table>
        </template>

        <template v-else-if="showTable === 'RelationTable'">
          <el-table :data="tableData" key="RelationTable">
            <el-table-column prop="keyword" label="新闻来源" width="140">
              <template slot-scope="scope">
                <span>20198</span>
              </template>
            </el-table-column>
            <el-table-column prop="title" label="新闻标题" >
              <template slot-scope="scope">
                <span>阿里巴巴投资格林深瞳</span>
              </template>
            </el-table-column>
            <el-table-column prop="invest" label="投资方" >
              <template slot-scope="scope">
                <span>阿里巴巴</span>
              </template>
            </el-table-column>
            <el-table-column prop="investR" label="投资关系" >
              <template slot-scope="scope">
                <span>C轮</span>
              </template>
            </el-table-column>
             <el-table-column prop="invested" label="融资方" >
              <template slot-scope="scope">
                <span>格林深瞳</span>
              </template>
            </el-table-column>
            <el-table-column prop="operation" label="标注">
              <template slot-scope="scope">
                <el-button type="primary" size="mini" >确认</el-button>
                <el-button type="warning" size="mini">修正</el-button>
              </template>
            </el-table-column>
          </el-table>
        </template>
      </el-main>

    </el-container>
</el-container>
</template>

<script>
export default {
  data() {
    const item = {
      keyword: "图像识别"
    };
    return {
      tableData: Array(20).fill(item),
      showTable: "TechTable"
    };
  },
  methods: {
    setShowTable(showTable) {
      this.showTable = showTable;
    },
    open() {
      this.$alert("这是一段内容", "标题名称", {
        confirmButtonText: "确定",
        callback: action => {
          this.$message({
            type: "info",
            message: `action: ${action}`
          });
        }
      });
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
.el-header {
  background-color: #24292e;
  color: #fff;
  height: 50px;
  line-height: 50px;
  text-align: left;
}
.el-main {
  padding: 30px;
}
</style>
