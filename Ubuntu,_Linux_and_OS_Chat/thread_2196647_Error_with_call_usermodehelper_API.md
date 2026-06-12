---
title: "Error with call_usermodehelper API"
date: 2013-12-30
forum: Ubuntu, Linux and OS Chat
---

### Post by kapilanand2 on 2013-12-30
I am having a problem with the use of *call_usermodehelper* API in linux kernel module. I am using this API inside Kernel jprobes module to trap *start_thread* function. This API works well if I provide *UMH_WAIT_EXEC* as wait parameter, but it fails to load the process when *UMH_WAIT_PROC* is passed as parameter. 

Specifically, the following code works properly.


    ```

#include <linux/kernel.h>
    #include <linux/module.h>
    #include <linux/sched.h>
    #include <linux/kprobes.h>
    #include <linux/kallsyms.h>
    #include <linux/ptrace.h>
    #include <linux/kmod.h>
    #include <linux/syscalls.h>
    #include <linux/delay.h>
    
    static struct jprobe start_thread_jprobe;
        
    static asmlinkage int kp_start_thread(struct pt_regs* regs, 
                            unsigned long new_ip,unsigned long new_sp){
        
        int retval;
        
        char * envp[] = { NULL };
        char* argv[]={"/bin/ls",NULL};
        
        //Only modifying this for a process named test1
        if(strcmp(current->comm,"test1")==0){
        
        retval=call_usermodehelper(argv[0], argv, envp, UMH_WAIT_EXEC);

        if(retval<0){
                printk("Failed in starting! %d\n",retval);
        }
        else {
            printk("Succeded in starting %d\n",retval);
        }
    }
    
    
    jprobe_return();
    /*NOTREACHED*/
    return (0);
    }
    
    int init_module(void)
    {
    int ret;
    start_thread_jprobe.entry = (kprobe_opcode_t *)kp_start_thread;
    start_thread_jprobe.kp.addr = (kprobe_opcode_t *)
    kallsyms_lookup_name("start_thread");
    
    if (!start_thread_jprobe.kp.addr) {
    printk("unable to lookup symbol\n");
    return (-1);
    }
    
    if ((ret = register_jprobe(&start_thread_jprobe)) <0) {
    printk("register_jprobe failed, returned %d\n", ret);
    return (-1);
    }
    return (0);
    }

```

But if I update the call to call_usemodehelper as follows.

     ```
retval=call_usermodehelper(argv[0], argv, envp, UMH_WAIT_PROC);
```

The above call fails to load *ls* using this API. It gives an error number -14 (EFAULT).


A simple test is as follows:

test1.c
   
    ```
#include <stdio.h>
       int main(){
              printf("This is test1\n");
              return 0;
       }
```

Makefile for module:

    ```
obj-m := kp-start-thread.o
    KDIR := /lib/modules/$(shell uname -r)/build
    PWD := $(shell pwd)
    default:
            $(MAKE) -C $(KDIR) SUBDIRS=$(PWD) modules
    clean:
            rm -f *.mod.c *.ko *.o

```

Test:
   

    ```
gcc test1.c -o test1 
       make 
       sudo insmod ./kp-start-thread.ko
       ./test1  
       dmesg ---> Will demonstrate success message with EXEC and failure with WAIT.
```

---

