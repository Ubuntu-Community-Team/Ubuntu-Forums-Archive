---
title: "Program runs at Ubuntu 14.04 but doesn't run at Ubuntu 16.04"
date: 2016-06-29
forum: Ubuntu Application Development
---

### Post by vladt1000 on 2016-06-29
I have program, that injects ip-address to the packets. Program have next includes: 
#include <stdio.h> 
#include <stdint.h>
#include <dlfcn.h>                               /* header required for dlsym() */
#include <sys/types.h>
#include <sys/socket.h>
#include <netinet/in.h>
#include <netinet/ip.h>
#include <arpa/inet.h>
#include <string.h>
#include <malloc.h>
#include <semaphore.h>
In my opinion there is a problem in some dll, because everything runs correctly in Ubuntu 14.04, but in 16.04 it did nothing.
Please help, sorry about my English.

---

