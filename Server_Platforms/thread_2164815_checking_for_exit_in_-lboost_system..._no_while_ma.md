---
title: "checking for exit in -lboost_system... no while making libtorrent-rasterbar-0.16.10"
date: 2013-08-02
forum: Server Platforms
---

### Post by TheBuzzer on 2013-08-02
Hi,

I just have a problem with deluge 1.3.6 that any torrent want to start so I found a new libtorrent-rasterbar-0.16.10 but when I try to do ./configure it have the error on checking for exit in -lboost_system!!

I tryied to install all libboost but still the same thing!?

There is the tail of ./configure command:

Checking for posix thread support:
checking for the pthreads library -lpthreads... no
checking whether pthreads work without any flags... no
checking whether pthreads work with -Kthread... no
checking whether pthreads work with -kthread... no
checking for the pthreads library -llthread... no
checking whether pthreads work with -lpthread... no
checking whether pthreads work with -pthread... yes
checking for joinable pthread attribute... PTHREAD_CREATE_JOINABLE
checking if more special flags are required for pthreads... no
checking whether to check for GCC pthread/shared inconsistencies... yes
checking whether -lpthread fixes that... yes
Checking for visibility support:
checking for __attribute__((visibility("hidden")))... found
yes

Checking for boost libraries:
checking for boostlib >= 1.36... yes
checking whether the Boost::System library is available... yes
checking for exit in -lboost_system... no
configure: error: Could not link against boost_system !



Here is all boost lib I have:

ls /usr/lib/libboost*
/usr/lib/libboost_filesystem.so.1.46.1  
/usr/lib/libboost_python-py27.so.1.46.1  
/usr/lib/libboost_system.so.1.46.1  
/usr/lib/libboost_thread.so.1.49.0
/usr/lib/libboost_iostreams.so.1.49.0   
/usr/lib/libboost_python-py32.so.1.46.1  
/usr/lib/libboost_thread.so.1.46.1

So anyone have an idea??

---

