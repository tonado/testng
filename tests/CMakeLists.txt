
CMAKE_MINIMUM_REQUIRED(VERSION 2.6)

PROJECT(testngpp-ut)

SET(PROJECT_HOME ${PROJECT_SOURCE_DIR}/..)

INCLUDE(${PROJECT_HOME}/ProjectVar.txt)

FIND_LIBRARY(TESTNGPP testngpp 
  PATHS ${PROJECT_HOME}/src 
  NAMES testngpp 
  NO_DEFAULT_PATH
  NO_SYSTEM_ENVIRONMENT_PATH)

IF(TESTNGPP_NOTFOUND)
  MESSAGE(FATAL_ERROR "you should build testngpp first")
ENDIF(TESTNGPP_NOTFOUND)

FIND_LIBRARY(TESTNGPP_RUNNER_LIB testngpp-runner-lib 
  PATHS ${PROJECT_HOME}/src/runner 
  NAMES testngpp-runner-lib 
  NO_DEFAULT_PATH
  NO_SYSTEM_ENVIRONMENT_PATH)


IF(TESTNGPP_RUNNER_LIB_NOTFOUND)
  MESSAGE(FATAL_ERROR "you should build testngpp first")
ENDIF(TESTNGPP_RUNNER_LIB_NOTFOUND)

ADD_SUBDIRECTORY(3rdparty/mockcpp/src)
ADD_SUBDIRECTORY(ut)

