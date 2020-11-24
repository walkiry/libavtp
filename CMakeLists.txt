project("libavtp" LANGUAGES C)

cmake_minimum_required(VERSION 3.17)
cmake_policy(SET CMP0048 NEW)
set(PROJECT_VERSION "0.1.0")

set(AVTP_SRCS
	 src/avtp.c
	 src/avtp_aaf.c
	 src/avtp_crf.c
	 src/avtp_cvf.c
	 src/avtp_ieciidc.c
	 src/avtp_stream.c
)

set(AVTP_PUBLIC_HEADERS
	include/avtp_aaf.h
	include/avtp_crf.h
	include/avtp_cvf.h
	include/avtp.h
	include/avtp_ieciidc.h 
)

set(AVTP_INCLUDE_DIRS
	include/
)
	
add_library(avtp SHARED ${AVTP_SRCS})
set_target_properties(avtp PROPERTIES VERSION ${PROJECT_VERSION})
target_include_directories(avtp PUBLIC ${AVTP_INCLUDE_DIRS})

install(TARGETS avtp LIBRARY DESTINATION lib)
install(FILES ${AVTP_PUBLIC_HEADERS} DESTINATION include/avtp)
