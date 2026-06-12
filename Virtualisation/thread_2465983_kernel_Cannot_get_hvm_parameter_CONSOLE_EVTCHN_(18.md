---
title: "kernel: Cannot get hvm parameter CONSOLE_EVTCHN (18): -22!"
date: 2021-08-17
forum: Virtualisation
---

### Post by travinan on 2021-08-17
Linux version 5.8.0-59-generic (buildd@lcy01-amd64-022) (gcc (Ubuntu 9.3.0-17ubuntu1~20.04) 9.3.0, GNU ld (GNU Binutils for Ubuntu) 2.34) #66~20.04.1-Ubuntu SMP Thu Jun 17 11:14:10 UTC 2021 (Ubuntu 5.8.0-59.66~20.04.1-generic 5.8.18)
Command line: BOOT_IMAGE=/boot/bzImage root=LABEL=root1 console=ttyS0,115200n8 console=tty0 earlyprintk=ttyS0,115200 rootdelay=300 nomodeset quiet splash noresume tsc=reliable net.ifnames=0 biosdevname=0


Issue: 
**Cannot get hvm parameter CONSOLE_EVTCHN (18): -22!**
Create AWS virtual machine using ubuntu AMI.
Above messages are observed after reboot every time.


Similar issue is logged for redhat - [https://access.redhat.com/solutions/6134291](https://access.redhat.com/solutions/6134291) (Solution In Progress                                              - Updated  June 23 2021 )
Is there any solution available for ubuntu?

Thanks,
Thulasi R

---

### Post by MAFoElffen on 2021-08-17
And from you have said, it displays when you boot 
> Create AWS virtual machine using ubuntu AMI.
Above messages are observed after reboot every time.

But then continues fine(???)

I have a RedHat account, so I logged in and looked at what that said... it says it's an AWS environmental configuration problem and that the mesasage is making you aware of that.
>        **Environment**

         
[LIST]
[*]Red Hat Enterprise Linux 7 
[*]Using Xen Hypervisor on AWS(Amazon Web Services) 
[/LIST]
             **Issue**

         
[LIST]
[*]kernel: Cannot get hvm parameter CONSOLE_EVTCHN (18): -22! in messages after reboot every time. 
[/LIST]
             **Resolution**

         Since this message is outputted in RHEL guest [COLOR=#ff0000]because the  CONSOLE_EVTCHN debug option is not enabled on AWS Hypervisor [/COLOR], if you  encounter any problems in RHEL virtual guest environment, you need to  check the details with AWS Support.
             **Root Cause**

         Since this message is outputted in RHEL guest [COLOR=#ff0000]because the CONSOLE_EVTCHN debug option is not enabled on AWS Hypervisor[/COLOR]


That's what that says right? It looks like they submitted the code there to AWS... for them to make a change.

I think that is how that reads... Right?

---

### Post by travinan on 2021-08-18
>>>But then continues fine(???)
[TD]: AWS VM instance is created but most of the console logs are missing. Since login prompt is not seen it looks as if the VM is hung.

>>>it says it's an AWS environmental configuration problem and that the mesasage is making you aware of that
[TD]: Thanks for confirming that it is AWS environmental configuration problem. I was wondering if any ubuntu package needed a fix?

>>>you need to  check the details with AWS Support.
[TD]: Thanks. will check with AWS to enable[COLOR=#ff0000] CONSOLE_EVTCHN debug option on AWS Hypervisor.

[/COLOR]Thanks,
Thulasi R[COLOR=#ff0000]
[/COLOR]

---

### Post by MAFoElffen on 2021-08-18
Please tell us how that goes, as "others" also may be interested in this and what it means...

---

