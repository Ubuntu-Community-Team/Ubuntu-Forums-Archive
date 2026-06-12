---
title: "no ip address specified and hostname not found boot"
date: 2010-10-21
forum: Server Platforms
---

### Post by joeyoung25 on 2010-10-21
I have a ubuntu server 10.04 that will not boot. I says
no ip address specified and hostname not found 
refer to mount cifs blah blah blah
mountall mount /directory/share [863] terminate with status 32

I know its because I had a share mounted at boot but the server cannot mount the share for some reason. is there a way around this so I can boot the machine? please help.

I can ping the server. I just cant ssh to it. I need to get to a prompt some how so I can remove the mount from fstab.

---

### Post by James78 on 2010-10-21
If you can't SSH into it, you can only do what you're allowed to do.

E.g. I have alternate methods to manage my server and it's files. I have Webmin, which will allow me to see and edit files just like I need. I also have my server listed as a Samba share on the local network. And of course there's SSH. So I have 3 different ways of changing the files, even if I get locked out by 1 of them.

If you don't have any other ways, the only thing you have left it to attach a monitor and a keyboard to the server, and fix it from the terminal.

---

