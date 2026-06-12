---
title: "How do i make shared directories using Samba?"
date: 2010-02-11
forum: Server Platforms
---

### Post by The Sorrow on 2010-02-11
I'm running Ubuntu Server 9.10 and I wanted to make a directory for windows shares on my mini domain and am lost as to how to create one. Ive looked but I cant seem to find much on the topic. Any and all help is appreciated.

---

### Post by joberly on 2010-02-11
1. Have you installed Samba? (Terminal: smbd -V)
2. How are you configuring Samba? Directly editing the file? SWAT?

---

### Post by Anxious Nut on 2010-02-11
try: (right click on the folder --> sharing Options) then see what you need, it'll install the programs it needs

---

### Post by joberly on 2010-02-11
What anxious nut said works as well, just make sure you are only using 1 way of managing shares. IE, don't use the folder options way AND SWAT.

---

### Post by The Sorrow on 2010-02-11
As reply to Right click, Ubuntu server has no GUI, so i need to use command line. Samba is installed, its default config (AKA i haven't touched it since i installed it with the live CD)

---

### Post by joberly on 2010-02-11
You need to edit the /etc/samba/smb.conf file directly with root privileges, with information that matches your network including the correct WORKGROUP.

The base file that gets installed has good basic documentation, so when you open the file for editing, you can see the examples.

This is a pretty in depth guide: [http://www.samba.org/samba/docs/man/Samba-Guide/](http://www.samba.org/samba/docs/man/Samba-Guide/)

Once you edit, save, and restart samba, run the command 'testparm' to test the configuration, and samba will yell if it finds any obvious errors.

'smbtree' also shows a list of all currently configured shares, if any.

---

### Post by The Sorrow on 2010-02-26
Thanks a ton guys, helped out a lot.

---

