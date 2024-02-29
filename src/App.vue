<script setup lang="ts">
import { reactive, ref } from "vue";
import { RouterLink, RouterView } from "vue-router";
import HelloWorld from "./components/HelloWorld.vue";
const menuList = [
    { id: 1, name: "功能功能功能A" },
    { id: 2, name: "功能功能B" },
    { id: 3, name: "功能功能C" },
    { id: 4, name: "功能功能D" },
    { id: 5, name: "功能功能E" },
    { id: 6, name: "功能功能F" },
];
const headerList = [
    { id: 1, name: "首页" },
    { id: 2, name: "主数据" },
    { id: 3, name: "辖区管理" },
    { id: 4, name: "畅销通" },
];
const rules = reactive<FormRules<RuleForm>>({
    user: [{ required: true, message: "Please input Activity name" }],
});
const formInline = reactive({
    user: "上海正也医药有限公司",
    region: "shanghai",
    date: "",
    gj: "jine",
    jine: "",
    time: "2024-02-29",
    time2: "2024-02-29 - 2024-02-29",
});
const tableData = [
    {
        code: "2016-05-03",
        name: "有限公司",
        address: "浙江省",
    },
    {
        code: "2016-05-02",
        name: "有限公司",
        address: "浙江省",
    },
    {
        code: "2016-05-04",
        name: "有限公司",
        address: "浙江省",
    },
];
const tableData2 = [
    {
        xieyijia: "2",
        piaozhe: "2",
        goujinda: "2",
        goujinxiao: "2",
        goujine: "2",
        chunxiao: "2",
    },
];
const activeName = ref("first");
const textarea = ref('')
const tabList = [
    { label: "补充协议1", name: "first" },
    { label: "补充协议2", name: "second" },
    { label: "补充协议3", name: "third" },
];

const onSubmit = () => {
    console.log("submit!");
};
const handleOpen = (key: string, keyPath: string[]) => {
    console.log(key, keyPath);
};
const handleClose = (key: string, keyPath: string[]) => {
    console.log(key, keyPath);
};
</script>

<template>
    <div class="container">
        <div class="content">
            <div class="menu">
                <div class="logo">
                    <img src="./assets/logo.jpg" alt="">
                </div>
                <el-menu default-active="2" text-color="#fff" background-color="#2b3138"
                    class="el-menu-vertical-demo" :collapse="isCollapse" @open="handleOpen"
                    @close="handleClose">
                    <el-menu-item v-for="item in menuList" :index="`item.id`">
                        <el-icon>
                            <setting />
                        </el-icon>
                        <template #title>{{item.name}}</template>
                    </el-menu-item>
                </el-menu>
            </div>
            <div class="wrap">
                <header>
                    <div class="header-item" v-for="item in headerList" :key="item.id">
                        <div class="header-item-icon">
                            <el-icon>
                                <setting />
                            </el-icon>
                        </div>
                        <div class="header-item-text">{{item.name}}</div>
                    </div>
                </header>
                <div class="main-container">
                    <nav>
                        <div class="nav-mbq">
                            首页/年度协议管理/二级商协议/新增二级商协议
                        </div>
                        <div class="nav-router">
                            新增二级商协议
                        </div>
                    </nav>
                    <div class="main-content">
                        <el-divider border-style="dashed">
                            ①协议主体
                        </el-divider>
                        <div class="form">
                            <el-form size="small" label-width="100" label-position="right"
                                :rules="rules" :inline="true" :model="formInline"
                                class="demo-form-inline">
                                <el-row>
                                    <el-col :span="12">
                                        <el-form-item label="协议客户: " prop="user">
                                            <el-button style="margin-right:20px;">选择客户</el-button>
                                            {{formInline.user}}
                                        </el-form-item>
                                    </el-col>
                                    <el-col :span="12">
                                        <el-form-item label="协议状态: ">
                                            <el-select v-model="formInline.region"
                                                placeholder="Activity zone" clearable>
                                                <el-option label="正常" value="shanghai" />
                                                <el-option label="不正常" value="beijing" />
                                            </el-select>
                                        </el-form-item>
                                    </el-col>
                                </el-row>
                                <el-row>
                                    <el-col :span="12">
                                        <el-form-item label="购进指标: ">
                                            <el-select style="width:88px;margin-right:20px;"
                                                v-model="formInline.gj" placeholder="Activity zone"
                                                clearable>
                                                <el-option label="金额" value="jine" />
                                                <el-option label="金额1" value="jine1" />
                                            </el-select>
                                            <el-input style="width:190px" disabled
                                                placeholder="输入金额/数量" v-model="formInline.jine" />
                                        </el-form-item>
                                    </el-col>
                                    <el-col :span="12">
                                        <el-form-item label="纯销指标: ">
                                            <el-select style="width:88px;margin-right:20px;"
                                                v-model="formInline.gj" placeholder="Activity zone"
                                                clearable>
                                                <el-option label="金额" value="jine" />
                                                <el-option label="金额1" value="jine1" />
                                            </el-select>
                                            <el-input style="width:190px" disabled
                                                placeholder="输入金额/数量" v-model="formInline.jine" />
                                        </el-form-item>
                                    </el-col>
                                </el-row>
                                <el-row>
                                    <el-col :span="12">
                                        <el-form-item label="销售区域: " prop="user">
                                            <el-button style="margin-right:20px;">选择区域</el-button>
                                            <el-tag closable type="primary">
                                                全国
                                            </el-tag>
                                        </el-form-item>
                                    </el-col>
                                    <el-col :span="12">
                                        <el-form-item label="签订时间: ">
                                            <el-input style="width:190px" placeholder="输入金额/数量"
                                                v-model="formInline.time" />
                                        </el-form-item>
                                    </el-col>
                                </el-row>
                            </el-form>
                            <div class="table">
                                <el-table max-height="100px" header-cell-class-name="gray"
                                    size="small" :data="tableData" height="250" style="width: 100%">
                                    <el-table-column prop="code" label="指定渠道编码" />
                                    <el-table-column prop="name" label="指定渠道名称" />
                                    <el-table-column prop="address" label="所在省" />
                                </el-table>
                            </div>
                        </div>

                        <el-divider border-style="dashed">
                            ②产品政策
                        </el-divider>
                        <div class="cp-top">
                            <el-button size="small" type="primary">添加产品</el-button>
                            <span class="cp-top-item">购进总指标( 万元 ): <span
                                    class="value">¥152.65</span></span>
                            <span class="cp-top-item">指标按季度分解( 万元 ): <span class="value">【Q1】¥12.5,
                                    【Q2】¥12.5, 【Q3】¥12.5,</span></span>
                            <span class="cp-top-item">纯销售总指标( 万元 ): <span
                                    class="value">¥152.65</span></span>
                        </div>
                        <div class="form">
                            <el-form size="small" label-width="100" :inline="true"
                                label-position="right" :model="formInline" class="demo-form-inline">
                                <el-form-item label="产品: ">
                                    <el-button style="margin-right:20px;">选择产品</el-button>
                                    <span class="link">美复胶囊</span>
                                </el-form-item>
                                <el-form-item label="协议效期: ">
                                    <el-input style="width:190px" placeholder="输入金额/数量"
                                        v-model="formInline.time2" />
                                </el-form-item>
                                <el-form-item>
                                    <el-button class="warning">删除</el-button>
                                </el-form-item>
                            </el-form>
                            <el-table border max-height="100px" header-cell-class-name="gray"
                                size="small" :data="tableData2" height="70"
                                style="width: 100%;margin-bottom:10px">
                                <el-table-column v-for="(value, key) in tableData2[0]" :key="key"
                                    label="协议价( 元 )">
                                    <template #default="scope">
                                        <el-input style="width:140px" size="small" disabled
                                            placeholder="请输入" />
                                    </template>
                                </el-table-column>
                            </el-table>
                            <el-table border max-height="100px" header-cell-class-name="gray"
                                size="small" :data="tableData2" height="70" style="width: 100%">
                                <el-table-column v-for="(value, key) in tableData2[0]" :key="key"
                                    label="协议价( 元 )">
                                    <template #default="scope">
                                        <el-input style="width:140px" size="small" disabled
                                            placeholder="请输入" />
                                    </template>
                                </el-table-column>
                            </el-table>

                        </div>
                        <el-divider border-style="dashed">
                            ②补充协议
                        </el-divider>
                        <el-tabs type="border-card" v-model="activeName" class="demo-tabs">
                            <el-tab-pane v-for="item in tabList" :key="item.name"
                                :label="item.label" :name="item.name">
                                <div class="tab-top">
                                    <p>协议内容: </p>
                                    <el-button size="small" class="warning">删除</el-button>
                                </div>
                                <el-input disabled v-model="textarea" :rows="5" type="textarea"
                                    placeholder="" />
                            </el-tab-pane>
                        </el-tabs>
                    </div>
                    <footer>
                        <el-button type="primary">保存</el-button>
                    </footer>
                </div>
            </div>
        </div>

    </div>
</template>

<style scoped lang="scss">
$bgColor: #2b3138;
$headerBgColor: #242a31;
$mainBgColor: #f5f5f5;
.container {
    width: 100%;
    height: 100%;
    overflow: hidden;
    .content {
        display: flex;
        height: 100%;
        .menu {
            width: 200px;
            background: $bgColor;
            .logo {
                width: 100%;
                height: 77px;
                box-shadow: 20px 0px 30px 0 rgba($color: #000000, $alpha: 1);
            }
        }
        .wrap {
            flex: 1;
            
            header {
                width: 100%;
                height: 77px;
                background: $headerBgColor;
                padding-left: 60px;
                display: flex;
                .header-item {
                    display: flex;
                    align-items: center;
                    margin-right: 40px;
                    color: #bababa;
                    &-icon {
                        width: 40px;
                        height: 40px;
                        border-radius: 8px;
                        text-align: center;
                        line-height: 45px;
                        background: #52565b;
                        font-size: 30px;
                        margin-right: 10px;
                    }
                    &:hover {
                        color: #fff;
                        .header-item-icon {
                            background: #6cbf6f;
                        }
                    }
                }
            }
            .main-container {
                position: relative;
                height: calc(100% - 77px);
                overflow-y: auto;
                background: $mainBgColor;
                .warning {
                    color: coral;
                }
                footer{
                    background: #fff;
                    padding: 10px 30px;
                    margin-top: 30px;
                }
                nav {
                    background: #fff;
                    padding: 10px 30px;
                    .nav-mbq {
                        font-size: 12px;
                        color: gary;
                    }
                }
                .main-content {
                    padding: 0px 30px;
                    .form {
                        background: #fff;
                        padding: 10px 20px;
                        border-radius: 5px;
                        .el-select {
                            width: 200px;
                        }
                        .link {
                            color: skyblue;
                        }
                    }
                    .table {
                        padding-left: 100px;
                    }
                    .cp-top {
                        font-size: 12px;
                        padding: 10px 0px;
                        .el-button {
                            margin-right: 20px;
                        }
                        .value {
                            margin-left: 10px;
                            font-weight: 600;
                        }
                        &-item {
                            margin-right: 20px;
                        }
                    }
                    .tab-top{
                        display: flex;
                        justify-content: space-between;
                        font-size: 14px;
                        margin-bottom: 10px;
                    }
                }
            }
        }
    }
}
</style>
