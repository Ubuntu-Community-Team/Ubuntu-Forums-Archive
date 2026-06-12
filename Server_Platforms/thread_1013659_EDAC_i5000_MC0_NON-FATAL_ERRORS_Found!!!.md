---
title: "EDAC i5000 MC0: NON-FATAL ERRORS Found!!!"
date: 2008-12-17
forum: Server Platforms
---

### Post by liung on 2008-12-17
Hi, today when I cat /var/log/messages , I found some errors , I need somebody to tell me what I shoule do next !

Thanks !

The system os is Ubuntu 8.04.1 x86_64 server edition , I enable LAMP server on it.
dmesg command is the same result at the tail .

Dec 16 06:44:44 ubuntu syslogd 1.5.0#1ubuntu1: restart.
Dec 16 06:58:43 ubuntu -- MARK --
......
Dec 16 10:18:44 ubuntu -- MARK --
Dec 16 10:25:04 ubuntu kernel: [3712331.131535] EDAC i5000 MC0: NON-FATAL ERRORS Found!!! 1st NON-FATAL Err Reg= 0x800
Dec 16 10:25:04 ubuntu kernel: [3712331.131542] EDAC i5000: ^INON-Retry  Errors, bits= 0x800
Dec 16 10:38:44 ubuntu -- MARK --
......
Dec 16 11:38:44 ubuntu -- MARK --
Dec 16 11:50:44 ubuntu kernel: [3717463.182668] EDAC i5000 MC0: NON-FATAL ERRORS Found!!! 1st NON-FATAL Err Reg= 0x800
Dec 16 11:50:44 ubuntu kernel: [3717463.182676] EDAC i5000: ^INON-Retry  Errors, bits= 0x800
Dec 16 12:18:44 ubuntu -- MARK --
......
Dec 17 01:58:44 ubuntu -- MARK --
Dec 17 02:10:02 ubuntu kernel: [3768941.352464] EDAC i5000 MC0: NON-FATAL ERRORS Found!!! 1st NON-FATAL Err Reg= 0x800
Dec 17 02:10:02 ubuntu kernel: [3768941.352471] EDAC i5000: ^INON-Retry  Errors, bits= 0x800
Dec 17 06:18:44 ubuntu -- MARK --
Dec 17 06:28:22 ubuntu syslogd 1.5.0#1ubuntu1: restart.
Dec 17 06:38:44 ubuntu -- MARK --
......
Dec 17 13:58:44 ubuntu -- MARK --
Dec 17 14:07:06 ubuntu kernel: [3811899.271666] EDAC i5000 MC0: NON-FATAL ERRORS Found!!! 1st NON-FATAL Err Reg= 0x800
Dec 17 14:07:06 ubuntu kernel: [3811899.271673] EDAC i5000: ^INON-Retry  Errors, bits= 0x800
Dec 17 14:18:44 ubuntu -- MARK --
Dec 17 14:25:09 ubuntu kernel: [3812980.825917] EDAC i5000 MC0: NON-FATAL ERRORS Found!!! 1st NON-FATAL Err Reg= 0x800
Dec 17 14:25:09 ubuntu kernel: [3812980.825924] EDAC i5000: ^INON-Retry  Errors, bits= 0x800
Dec 17 14:38:44 ubuntu -- MARK --
Dec 17 14:45:03 ubuntu kernel: [3814172.225967] EDAC i5000 MC0: NON-FATAL ERRORS Found!!! 1st NON-FATAL Err Reg= 0x800
Dec 17 14:45:03 ubuntu kernel: [3814172.225973] EDAC i5000: ^INON-Retry  Errors, bits= 0x800
Dec 17 14:58:44 ubuntu -- MARK --
Dec 17 15:10:04 ubuntu kernel: [3815671.112720] EDAC i5000 MC0: NON-FATAL ERRORS Found!!! 1st NON-FATAL Err Reg= 0x800
Dec 17 15:10:04 ubuntu kernel: [3815671.112727] EDAC i5000: ^INON-Retry  Errors, bits= 0x800
Dec 17 15:38:44 ubuntu -- MARK --
Dec 17 15:40:09 ubuntu kernel: [3817473.551599] EDAC i5000 MC0: NON-FATAL ERRORS Found!!! 1st NON-FATAL Err Reg= 0x800
Dec 17 15:40:09 ubuntu kernel: [3817473.551617] EDAC i5000: ^INON-Retry  Errors, bits= 0x800
Dec 17 15:50:03 ubuntu kernel: [3818066.691438] EDAC i5000 MC0: NON-FATAL ERRORS Found!!! 1st NON-FATAL Err Reg= 0x800
Dec 17 15:50:03 ubuntu kernel: [3818066.691446] EDAC i5000: ^INON-Retry  Errors, bits= 0x800
Dec 17 16:18:44 ubuntu -- MARK --

---

### Post by liung on 2008-12-17
Is here some body can help me ?

---

### Post by liung on 2008-12-22
Anybody know how to do ? Or should I submit a bug ?

Thanks for yours attention .

---

### Post by windependence on 2008-12-23
There is already a bug report submitted. It seems this RAM reports non-important errors a bit too verbosely in certain kernels. It doesn't seem to affect anything though.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/276444](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/276444)

BTW, there are tons of these on Google. You may want to search before posting and getting too excited.

-Tim

---

### Post by liung on 2008-12-27
Yes , I found in google , but I also found they have no ideas ...... , so ......

---

