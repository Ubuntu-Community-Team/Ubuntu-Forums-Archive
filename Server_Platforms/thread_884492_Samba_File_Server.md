---
title: "Samba File Server ?????"
date: 2008-08-09
forum: Server Platforms
---

### Post by railpostau on 2008-08-09
Have used 8.04 server to install onto a spare box..Install went ok, root etc all ok...

Have read through many posts...Now I am totally confused...

One post suggests using vim to set up server... and others suggest SSH and Firefox...

All I wanted to do was set up a Samba file server so that my 2 seperate computers can use the same files...Unfortunately they have to run XP due to the programs in use..

And I thought DOS, Win 3.11 was a *******...

Is there anybody who can tell me in simple language ie do this do that..without forgetting that many users do not yet have full control of ubuntu and all its commands etc.... How to set up a Samba server..

Thank you...:confused:

---

### Post by sprouty on 2008-08-09
Hi, 

here are the steps i done to set up a basic samba share. All these command were run from the terminal as root.

This install samba
```
apt-get install samba
```

from here you need to edit the samba configuration file. I used nano but you can use vi (nano is just like notepad)

```
nano /etc/samba/smb.conf
``` 

At the bottom of the file you need to add where you want to share

```
[share]
path = /share
available = yes
browsable = yes
public = yes
writable =yes
```
(F3 to save, F2 to exit)

So path is where you want the network share to be on the server.
i just created a partion on the root.

One thing that tripped me up was that you got to create the user on the Ubuntu server box, so for exaple

My username on xp is Administrator with a blank password. So for me to have write permision on the samba network i need to create the user Administrator on the ubuntu server.

Create the user is done by 
```
useradd Administrator
```

and then to let samba know 
```
smbpasswd -a Administrator
```
!!Password needs to be the same has the xp system!!!

and the last step is to chmod the directory (again so everyone can right to it)
```
chmod 777 /share
```

you can use ssh to step this up ssh is just used for remote access into the box and vim is add onto vi i used nano instead they are both text editors.

Think this is a basic overiew any question, is very early in the morning here so if i missed anything out give me a reply and i'll answer them has soon as i can.

---

### Post by railpostau on 2008-08-10
Thanks you for the info.. Looks like I have a lot of further study to do..But you got me on the right track...

---

