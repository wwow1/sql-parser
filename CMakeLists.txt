cmake_minimum_required(VERSION 3.10)
project(sql_parser)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# 源文件
set(SQLPARSER_SRC
    src/parser/bison_parser.cpp
    src/parser/flex_lexer.cpp
    src/SQLParser.cpp
    src/sql/Expr.cpp
    src/sql/SQLStatement.cpp
    src/sql/statements.cpp
    src/util/sqlhelper.cpp
    src/sql/CreateStatement.cpp
    src/sql/PrepareStatement.cpp
    src/SQLParserResult.cpp
)

# 创建静态库
add_library(sqlparser STATIC ${SQLPARSER_SRC})

# 包含目录
target_include_directories(sqlparser
    PUBLIC
        ${CMAKE_CURRENT_SOURCE_DIR}/src
        ${CMAKE_CURRENT_SOURCE_DIR}/include
        ${CMAKE_CURRENT_SOURCE_DIR}
)

# 如果需要安装
install(TARGETS sqlparser
    ARCHIVE DESTINATION lib
    LIBRARY DESTINATION lib
) 
