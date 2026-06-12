---
title: "Unable to make makefiles for maverick"
date: 2012-09-20
forum: Ubuntu Application Development
---

### Post by Pulock2012 on 2012-09-20
i am new to Ubuntu. i have been trying to port to linux but the region from which i come is still relatively new to computers and hence adheres to windows OSes. i have intermediate level knowledge of the c programming language. i have been trying to develop a driver for an USB device and i am stuck at making makefiles in maverick. my .c file is this:
```

#include<linux/module.h>
#include<linux/kernel.h>
#include<linux/usb.h>
static int usb_notify_subscriber(struct notifier_block *self,unsigned long action,void *dev)
{
     printk(KERN_INFO "usb_notify_subscriber\n");
     switch(action)
     {
           case USB_DEVICE_ADD: printk(KERN_INFO"usb_notify_subscriber:USB     device added\n");break;
           case USB_DEVICE_REMOVE: printk(KERN_INFO"usb_notify_subscriber:USB device removed\n");break;
           case USB_BUS_ADD: printk(KERN_INFO"usb_notify_subscriber:USB bus added\n");break;
           case USB_BUS_REMOVE: printk(KERN_INFO"usb_notify_subscriber:USB bus removed\n");
     }
     return NOTIFY_OK;
}
int init_module(void)
{
     printk(KERN_INFO"Init USB simple subscriber.\n");
     usb_register_notify(&usb_simple_nb);
     return 0;
}
void cleanup_module(void)
{
     usb_unregister_notify(&usb_simple_nb);
     printk(KERN_INFO"remove USB simple subscriber\n");
}
MODULE_LICENSE("GPL");


```
and my makefile is this:
```

obj-m+=simple_usb_subscriber.o
all:
      make -C/lib/modules/$(shell uname -r)/build M=$(PWD)modules
clean:
      make -C/lib/modules/$(shell uname -r)/build M=$(PWD)clean

```

while trying to run the makefile i get the error message :
make: nothing to be done for 'all'.

please help.

---

### Post by steeldriver on 2012-09-20
Hi, that sounds like a classic case of using spaces instead of a tab to indent the make command

```

obj-m+=simple_usb_subscriber.o
all:
[COLOR=Red]**--->**[/COLOR]make -C/lib/modules/$(shell uname -r)/build M=$(PWD)modules
clean:
**[COLOR=Red]--->[/COLOR]**make -C/lib/modules/$(shell uname -r)/build M=$(PWD)clean

```

**[COLOR=Red]--->[/COLOR]** must be tabs

---

### Post by cariboo on 2012-09-22
FYI, support for Maverick 10.10 ended in April 2012. We are now using kernel version 3.2.24, in the latest release, so you may want to upgrade to 12.04.1 if you want to release your driver for general use.

---

### Post by Pulock2012 on 2012-09-24
> **steeldriver said:**
> Hi, that sounds like a classic case of using spaces instead of a tab to indent the make command

```

obj-m+=simple_usb_subscriber.o
all:
[COLOR=Red]**--->**[/COLOR]make -C/lib/modules/$(shell uname -r)/build M=$(PWD)modules
clean:
**[COLOR=Red]--->[/COLOR]**make -C/lib/modules/$(shell uname -r)/build M=$(PWD)clean

```**[COLOR=Red]--->[/COLOR]** must be tabs

thanks a lot. its working.

---

