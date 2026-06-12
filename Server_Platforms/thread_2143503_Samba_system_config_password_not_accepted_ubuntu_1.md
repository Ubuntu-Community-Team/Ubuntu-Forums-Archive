---
title: "Samba system config password not accepted ubuntu 13.04"
date: 2013-05-09
forum: Server Platforms
---

### Post by siamesekatz on 2013-05-09
Hi all,

After a long hiatus of not using Ubuntu (working in a windows server world these days) I have just found a project that made me want to give the ol' ubuntu another go.
We have need of a media\file server and had an old 1u rack mount server lying around that would be perfect for the job. I downloaded and installed ubuntu server 13.04 and added the xubuntu desktop.
I installed samba system config since the rest of samba was already installed. 

I logged in with my account (administrator) with admin rights but when I click on the samba system config tool it asked for a password, but none of my password were accepted. I then thought I needed to add the samba user and I did that with the same username and password, then I restated samba and tried again and I had the same issue. I made another user with admin rights and logged in with that account but still the same problem.
Last night I tried the same thing on a mint 14 box and it worked fine.

Can any one tell me what I'm doing wrong or how I can go about fixing this.

Thanks in advance

Justin

---

### Post by matt_symes on 2013-05-09
Thread moved to **server platforms**.

You're more likely to get a response in this sub forum.

---

### Post by bab1 on 2013-05-10
> **siamesekatz said:**
> Hi all,

After a long hiatus of not using Ubuntu (working in a windows server world these days) I have just found a project that made me want to give the ol' ubuntu another go.
We have need of a media\file server and had an old 1u rack mount server lying around that would be perfect for the job. I downloaded and installed ubuntu server 13.04 and added the xubuntu desktop.
I installed samba system config since the rest of samba was already installed. 
 Post the results of this 
```
ps aux|grep mbd
```> 

I logged in with my account (administrator) with admin rights but when I click on the samba system config tool it asked for a password, but none of my password were accepted. I then thought I needed to add the samba user and I did that with the same username and password, then I restated samba and tried again and I had the same issue. I made another user with admin rights and logged in with that account but still the same problem.

Last night I tried the same thing on a mint 14 box and it worked fine.

Post the results of this from Ubuntu```
sudo pdbedit -L
```

---

### Post by siamesekatz on 2013-05-10
Hi there,

Thanks for the help, I can see from the results where the problems are but how to fix?:confused:

anmmedia@ubuntu-media:~$ ps aux|grep mbd
root       589  0.0  0.2  23204  2148 ?        Ss   May08   0:03 smbd -F
root       734  0.0  0.0  23720   620 ?        S    May08   0:00 smbd -F
root      1000  0.0  0.0  13344   904 ?        Ss   May08   0:04 nmbd -D
anmmedia 13413  0.0  0.0   4428   812 pts/1    S+   12:37   0:00 grep --color=auto mbd

anmmedia@ubuntu-media:~$ sudo pdbedit -L
[sudo] password for anmmedia:
anmmedia is not in the sudoers file.  This incident will be reported

---

### Post by siamesekatz on 2013-05-10
Ok so I googled how to set the root password, so I can now open the samba config tool :-) let see if I can do the rest my self, if not I will report back here!

Thanks for the help!

---

