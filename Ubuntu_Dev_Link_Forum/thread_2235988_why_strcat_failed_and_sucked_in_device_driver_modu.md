---
title: "why strcat failed and sucked in device driver module?"
date: 2014-07-24
forum: Ubuntu Dev Link Forum
---

### Post by zerop2 on 2014-07-24
why strcat failed and sucked in device driver module?

```

#ifndef __KERNEL__
#  define __KERNEL__
#endif
#ifndef MODULE
#  define MODULE
#endif
//#include <string.h>
//#include <stdio.h>
#include <linux/kernel.h>
#include <linux/module.h>
#include <linux/proc_fs.h>
#include <linux/workqueue.h>
#include <linux/sched.h>
#include <linux/init.h>
#include <linux/interrupt.h>
#include <linux/delay.h> 
#include <asm/uaccess.h>
//wonder@wonder-VirtualBox:~/layer$ sudo make -C /usr/src/linux-headers-3.8.0-29-generic hello.c M=/home/wonder/layer modules
MODULE_LICENSE("GPL");
#define MODULE_VERS "1.0"
#define MODULE_NAME "procfs_example"
#define FOOBAR_LEN 8
struct fb_data_t {
    char name[FOOBAR_LEN + 1];
    char value[FOOBAR_LEN + 1];
};

static struct proc_dir_entry *example_dir, *bar_file, *symlink;
struct fb_data_t bar_data;
struct workqueue_struct *test_wq;
struct delayed_work test_dwq;

char *hello_str = "Hello, world!\n";
 
void delay_func(struct work_struct *work);

static struct tasklet_struct my_tasklet ;  
static void tasklet_handler(unsigned long data)
{
        printk(KERN_ALERT "3333tasklet_handler is running./n");
    //tasklet_schedule(&my_tasklet);
}  
void delay_func(struct work_struct *work)
{
    //int i;
 
    printk(KERN_INFO "My name is delay_func!\n");
    //int ret = queue_delayed_work(test_wq, &test_dwq, 0);
    //for (i = 0; i < 3; i++) {
        //printk(KERN_ERR "delay_fun:i=%d\n", i);
        //msleep(1000);
    //}
} 
static int
hello_read_proc(char *buffer, char **start, off_t offset, int size, int *eof, void *data)
{
        
        //char*hello_str = buffer;
        int len = strlen(hello_str); /* Don't include the null byte. */
        /*
         * We only support reading the whole string at once.
         */
        if(size < len)
           return -EINVAL;
        /*
         * If file position is non-zero, then assume the string has
         * been read and indicate there is no more data to be read.
         */
        if (offset != 0)
           return 0;
        /*
         * We know the buffer is big enough to hold the string.
         */
        strcpy(buffer, hello_str);
        /*
         * Signal EOF.
         */
        *eof = 1;

        return len;
}
char *strcat2(char *dst, char *src)
{
    char * cp = dst;
    while( *cp )
    cp++; /* find end of dst */

    while( *cp++ = *src++ ) ; /* Copy src to end of dst */

    return( dst ); /* return dst */
}
static int __init hello_init(void)
{
    int rv = 0;

    if (create_proc_read_entry("hello_world", 0, NULL, hello_read_proc, NULL) == 0) {
        printk(KERN_ERR
               "Unable to register \"Hello, world!\" proc file\n");
        return -ENOMEM;
    }
    hello_str = "Step0\n";
    //msleep(10000);
    char* hello_str1 = "Step0 ";
    char* hello_str2 = "Step1 ";
    hello_str = strcat2(hello_str1, hello_str2);
    //msleep(10000);
    hello_str2 = "Step2 ";
    hello_str = strcat2(hello_str1, hello_str2);
    //msleep(10000);
    remove_proc_entry("hello_world", NULL);

    tasklet_init(&my_tasklet, tasklet_handler, 0);
    tasklet_schedule(&my_tasklet);

    /* create symlink */
    //symlink = proc_symlink("jiffies_too", example_dir,"jiffies");
    //if(symlink == NULL) {
       //rv = -ENOMEM;
       //goto no_symlink;
    //}
    //symlink->owner = THIS_MODULE;
    //int i;
    //int ret;
 
    //test_wq = create_workqueue("test_wq");
    //if (!test_wq) {
        //printk(KERN_ERR "No memory for workqueue\n");
        //return 1;    
    //}
    //printk(KERN_INFO "Create Workqueue successful!\n");
 
    //INIT_DELAYED_WORK(&test_dwq, delay_func);
     
    //ret = queue_delayed_work(test_wq, &test_dwq, 0);
    //printk(KERN_INFO "444 first ret=%d!\n", ret);
    
    //for (i = 0; i <= 100; i++) {  
    //if(i==100)
    //{
            //printk(KERN_INFO "Example:ret= %d,i=%d\n", ret, i);
    //}
        //msleep(100);
    //}
 
    //ret = queue_delayed_work(test_wq, &test_dwq, 0);
    //printk(KERN_INFO "444 second ret=%d!\n", ret);
 
    return 0;
}
static void __exit hello_exit(void)
{
  tasklet_kill (&my_tasklet);
  remove_proc_entry("hello_world", NULL);
  //int ret;
  //ret = cancel_delayed_work(&test_dwq);
  //flush_workqueue(test_wq);
  //destroy_workqueue(test_wq);
  //printk(KERN_INFO "Goodday! ret=%d\n", ret); 
  printk("Unloading hello.\n");
  return;
}

module_init(hello_init);
module_exit(hello_exit);

```

---

