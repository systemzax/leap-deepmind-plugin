set(Sources
	DisassemblyNames.cpp
	Operators.cpp
	Types.cpp
	Validate.cpp)

set(PublicHeaders
	${WAVM_INCLUDE_DIR}/IR/IR.h
	${WAVM_INCLUDE_DIR}/IR/Module.h
	${WAVM_INCLUDE_DIR}/IR/OperatorPrinter.h
	${WAVM_INCLUDE_DIR}/IR/Operators.h
	${WAVM_INCLUDE_DIR}/IR/Types.h
	${WAVM_INCLUDE_DIR}/IR/Validate.h)
include_directories(${WAVM_INCLUDE_DIR}/IR)

add_library(IR STATIC ${Sources} ${PublicHeaders})
add_definitions(-DIR_API=DLL_EXPORT)
target_link_libraries(IR Logging)

install(TARGETS IR 
   LIBRARY DESTINATION ${CMAKE_INSTALL_FULL_LIBDIR}
   ARCHIVE DESTINATION ${CMAKE_INSTALL_FULL_LIBDIR}
	COMPONENT dev EXCLUDE_FROM_ALL)

