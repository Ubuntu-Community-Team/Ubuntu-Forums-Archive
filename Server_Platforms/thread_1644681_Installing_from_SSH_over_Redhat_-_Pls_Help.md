---
title: "Installing from SSH over Redhat - Pls Help"
date: 2010-12-13
forum: Server Platforms
---

### Post by rbalaa on 2010-12-13
Hello,
 
I currently have a hosting provider that has Redhat installed on my server. I can't get to that server physically, I can only SSH into it. Is there anyway I can install Ubuntu Server 10.4 LTS on there via SSH to go over the Redhat on there ?
 
Your help is much appreciated.
 
Thanks

---

### Post by stlsaint on 2010-12-13
[https://help.ubuntu.com/community/Installation#Server%20and%20network%20installations](https://help.ubuntu.com/community/Installation#Server%20and%20network%20installations)

---

### Post by elico on 2010-12-13
you can somehow do that but if it's critical server you will need to do some acrobatics.

if you can partition from ssh then you should be able yo do something about it that will make it much more safer then risking your server the option to not boot at all.
and you can make some grub and scripting to make sure that you wont have any problem getting into situation you wont be able to boot the machine from one kernel\system.

---

