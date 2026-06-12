---
title: "Intrepid and Vmware Server 2"
date: 2008-11-17
forum: Virtualisation
---

### Post by karlito83 on 2008-11-17
Hi,

I recently installed 8.10 64 bit version of ubuntu and vmware server 2.0. Everything works fine until I try to start a VM then i get an error: Failed to initialize monitor device. 

Can anyone help me?

---

### Post by karlito83 on 2008-11-18
Is anybody else having this issue? If not what did you do with your 64 bit install? Maybe I made an error along the way. I could really use someones help!

---

### Post by bodhi.zazen on 2008-11-18
I have not had this problem (Running 8.10 , 64 bit, Server 2.0).

I would say the Server 2.0 does not seem a "solid" as 1.0.7. I do not know if it helps, but did you try restarting vmware ?

```
sudo /etc/init.d/vmware restart
```

Any error messages ?

---

### Post by karlito83 on 2008-11-19
Yes I have tried all of that. All I can think of is to do a re-install of the OS because i did choose virtualization server as an option when seting up the system and then I installed vmware, so I am hoping that there is something there that is causing my issue, so I will not check that option the second go around.

---

### Post by Russianspi on 2008-11-19
Never mind, don't do that.  This just hosed my system...
I was going to tell you to use tasksel to remove the Virtualization Host package set, but I ran into [this REALLY NASTY BUG]("https://bugs.launchpad.net/ubuntu/+source/tasksel/+bug/150252") when fine tuning the instructions I gave you...

---

### Post by drumkilling on 2008-11-20
I have the same problem. I'll come back in case I have a solution

---

### Post by jrettyw691 on 2008-11-20
We are a professional, loyal and reliable [**wow gold**](http://veryge.com/) store online. We supply wow gold to our loyal customers that you may buy on our website.

---

### Post by [pl]ice on 2008-11-30
any luck yet? i'm stuck too :(

should I try ver 1.x or something instead of server 2 ?

EDIT:_ Guys, mine actually works now ..._

  i don't have error with the "Failed to initialize monitor device. "

Using the  VMware Server 2.0.0 build-122956 with 2.6.27-9-generic
 when I reinstalled it straight(no patches for vmware) it somehow confused the admin so i couldn't log in at all. Turned out that the user was '' (empty) strange, as this didn't happen before. So i installed it again, and put my username as admin. Now i can start the virtual machine withouth that error . . . 
  figure that out :)
I think its just premissions to access the display

---

