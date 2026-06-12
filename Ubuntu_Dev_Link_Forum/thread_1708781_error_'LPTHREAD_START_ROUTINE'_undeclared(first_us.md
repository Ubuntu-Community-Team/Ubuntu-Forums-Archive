---
title: "error: 'LPTHREAD_START_ROUTINE' undeclared(first use in this function)"
date: 2011-03-17
forum: Ubuntu Dev Link Forum
---

### Post by antonio1980 on 2011-03-17
hi,

i have this C code program to create thread:
 
double dwThreadId1;
CreateThread (NULL,
                      0,
                      (LPTHREAD_START_ROUTINE)&ThreadParam,
                      0,
                      &dwThreadId1,
                      );

when compiling, i receive these wornings and errors:

warning: implicit declaration of function 'CreatThread'
error: 'LPTHREAD_START_ROUTINE' undeclared(first use in this function)
error:'LPVOID' undeclared (first use  in this function)


could anyone help me to resolve this problem ??

Regards.

---

### Post by myforwik on 2011-03-27
CreateThread is a windows function.
 
On linux you need to use pthreads:
 
```
 
#include <pthread.h>
 
pthread_t thread;
double threadid;
pthread_create(&thread,NULL,ThreadParam,&threadid);

```
You will also need to change the definition of ThreadParam from probably ```
DWORD WINAPI ThreadParam(LPVOID *)
``` to ```
void *ThreadParam(void *param)
```.

---

