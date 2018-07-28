<template>
  <div class="hello">
    <template>
               <el-dropdown @command="handleCityCommand">
           <span class="el-dropdown-link">
            城市<i class="el-icon-arrow-down el-icon--right"></i>
           </span>
           <el-dropdown-menu slot="dropdown">
            <el-dropdown-item command=1>北京</el-dropdown-item>
            <el-dropdown-item command=2>南京</el-dropdown-item>
          </el-dropdown-menu>
         </el-dropdown>
                    <el-table
                      :data="tableData"
                      style="width: 100%">
                      <el-table-column
                        prop="city"
                        label="城市"
                        :render-header="renderCity"
                        >
                      </el-table-column>
                      <el-table-column
                        prop="name"
                        label="姓名">
                      </el-table-column>
                      <el-table-column
                        prop="address"
                        label="地址">
                      </el-table-column>
                      
                </el-table>
</template>
  </div>
</template>

<script>
  export default {
    name: 'HelloWorld',
    mounted() {
  
      //this.createSomething(this.commandCityList)
  
    },
    data() {
      return {
  
        spanCity: "城市",
        commandCityList: {
          1: "北京",
          2: "南京"
        },
        tableData: [{
          city: '北京',
          name: '王小虎',
          address: '上海市普陀区金沙江路 1518 弄',
  
        }, {
          city: '北京',
          name: '王小虎',
          address: '上海市普陀区金沙江路 1517 弄',
  
        }, {
          city: '南京',
          name: '王小虎',
          address: '上海市普陀区金沙江路 1519 弄',
  
        }, {
          city: '南京',
          name: '王小虎',
          address: '上海市普陀区金沙江路 1516 弄',
  
        }]
      }
    },
    methods: {
      renderCity(createElement, {
        column,
        $index
      }) {
        return this.createDropdownColumnTitle(createElement, this.spanCity, this.commandCityList, this.handleCityCommand)
      },
      handleCityCommand(command) {
        console.log(command);
      },
      createDropdownColumnTitle(createElement, spanWord, commandList, handleCommand) {
        let dropdownMenu = []
        for (let key in commandList) {
          dropdownMenu.push(createElement(
            'el-dropdown-item', {
              props: {
                command: key
              }
            },
            commandList[key]
          ))
        }
        return createElement(
          'el-dropdown', {
            on: {
              command: handleCommand
            }
          }, [
            createElement(
              'span', {
                'class': 'el-dropdown-link'
              }, [
                spanWord,
                createElement(
                  'i', {
                    'class': "el-icon-arrow-down el-icon--right"
                  }
                )
              ]
            ),
            createElement(
              'el-dropdown-menu', {
                slot: "dropdown"
              },
              dropdownMenu
            )
          ]
        )
      },
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  
</style>
