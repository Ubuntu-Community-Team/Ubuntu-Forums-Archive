---
title: "A scaring newbie question"
date: 2008-06-21
forum: Security
---

### Post by rey1321 on 2008-06-21
HI guys, I'm just running ubuntu 8.04, everything run perfect, the problem is that I'm sharing an internet cable with my roommate, both of us are connected in the same router no problem with that, but one of this day I opened my network icon and to my surprise !!!! i saw all my roommate home folder files!!!.

I got fu**ing scared, cause if I can see his files, he can see mine too!!!!!!
now my question is:
How can I disable or prevent my roommate to see all my downloaded porno movies and all my projects.
please help me, he's running Ubuntu 8.04 too
Thanks

---

### Post by Joeb454 on 2008-06-21
Applications &#8594; Accessories &#8594; Terminal then enter ```
chmod o-rwx *
``` That should do the trick, though wait for someone else to confirm that :)

---

### Post by sp0nge on 2008-06-21
Unless one or both of you has opened more folders to be shared, you should have little to worry about. The only files accessible should be whatever is in the shared folders. Don't keep anything in there and you have no problem.

---

### Post by rey1321 on 2008-06-21
thanks guys, I feel better now, but why can i see his folders and files,  I just click this Places>network>mshome>boxin>my roommate name folder and then i can see all his folders and i can opened and everything
please help me

---

### Post by rey1321 on 2008-06-21
I click where  the icon say JohnBoxin and it  mounted in my desktop like another drive (his hard  drive or home folder) and from there I can open all his folder like another drive.!!!!!!!!!!!!

---

### Post by bikeboy on 2008-06-21
That would be a mis-configuration on his end. The settings on *your* computer (shared folder preferences) will determine whether he can see your folder/s or not.

---

### Post by rey1321 on 2008-06-21
thanks bikeboy, but how can I set my preferences in folder sharing, I new on this.
thanks

---

### Post by cariboo on 2008-06-21
The way to stop this is to tell your roommate to smarten up and not share all of his files and foldsers. It could lead to disaster. The only way your roommate is going  to have access to your files is if he has your password and you use autologin so you don't have to enter your password to access your system

Jim

---

### Post by rey1321 on 2008-06-21
Thanks you guys, I don't have autologin, but I gonna start changing my password at least every month, can someone tell me how can i check if i sharing folders or files in the network or I mean the sharing router???

---

### Post by rey1321 on 2008-06-21
Hey guys, I just found out that i don't have any sharing service installed,  like NFS or Samba, am I OK like that or I still vulnerable??

---

### Post by Chayak on 2008-06-21
You're fine and if you don't share any services you can always turn the firewall included in Ubuntu on.

```
At the terminal
<type sudo here> ufw enable
<type sudo again> ufw default deny
```

That way even if you do have services running that someone could connect to by default it's going to deny any outside connections in.  This will block everything, including things like bittorrent so if you use it you'll have to do a
```
<type sudo here> ufw allow <port number or service such as ftp/samba/nfs/etc...>
```

A last note to check any commands someone puts up here so check ufw in the documentation first so you know what it is before running those commands.

---

### Post by rey1321 on 2008-06-21
Thanks Chayak, I'll check UFW documentation

---

### Post by The Cog on 2008-06-22
If you don't install any services, you don't need a firewall at all. 

If you haven't installed samba, nfs or openssh-server than you are not sharing any files in any way. Rest easy.

And tell your room-mate he is sharing his files with the world - he probably doesn't know it's happening.

---

### Post by hyper_ch on 2008-06-22
> **cariboo907 said:**
> The way to stop this is to tell your roommate to smarten up and not share all of his files and foldsers. It could lead to disaster.

Wrong... if he can get physical access to the machine he just needs to boot from a live cd and mount the computer's hardisk(s). Forget about username and password and auto-login. that does not prevent from physical access.

Only way to protect yourself frm physical access by other people is encryption of the files or whole system.

---

