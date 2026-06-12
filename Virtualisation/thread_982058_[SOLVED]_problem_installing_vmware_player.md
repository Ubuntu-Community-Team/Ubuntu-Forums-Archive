---
title: "[SOLVED] problem installing vmware player"
date: 2008-11-14
forum: Virtualisation
---

### Post by frost151n on 2008-11-14
Hello, umm... I'm having a problem installing VM Ware Player 2.5.0-118166 on Ubuntu Intrepid Ibex (8.10)

I've been using this tutorial -- [https://help.ubuntu.com/community/VMware/Player#Installing%20VMware%20Player%20on%20Ubuntu%208.04%20LTS](https://help.ubuntu.com/community/VMware/Player#Installing%20VMware%20Player%20on%20Ubuntu%208.04%20LTS) --

But when I type the command
-- gksudo bash ./VMware-Player-2.5.0-118166.i386.bundle --

I get the out put
-- frost@ubuntu:~$ gksudo bash ./VMware-Player-2.5.0-118166.i386.bundle
bash: ./VMware-Player-2.5.0-118166.i386.bundle: No such file or directory
frost@ubuntu:~$ --

The file is of the same name, i checked, and its on the desktop.

Please help.

P.S. If this doesn't belong here please lemme know. 

P.P.S. Also please let me know how to move a thread!

---

### Post by jpdamigaman on 2008-11-14
HI move VMware-Player-2.5.0-118166.i386.bundle -- to home folder

let me know how u get on.

JPD

---

### Post by jpdamigaman on 2008-11-14
HI when I have vmplayer installed I try to run a win 2000 VM which works in windows but I get a syntax error

see pic

---

### Post by bodhi.zazen on 2008-11-14
First off, IMO, you are better off with VMWare Server (or VirtualBox) rather then player. Server is also freely available and more powerful.

> **frost151n said:**
> Hello, umm... I'm having a problem installing VM Ware Player 2.5.0-118166 on Ubuntu Intrepid Ibex (8.10)

I've been using this tutorial -- [https://help.ubuntu.com/community/VMware/Player#Installing%20VMware%20Player%20on%20Ubuntu%208.04%20LTS](https://help.ubuntu.com/community/VMware/Player#Installing%20VMware%20Player%20on%20Ubuntu%208.04%20LTS) --

But when I type the command
-- gksudo bash ./VMware-Player-2.5.0-118166.i386.bundle --

I get the out put
-- frost@ubuntu:~$ gksudo bash ./VMware-Player-2.5.0-118166.i386.bundle
bash: ./VMware-Player-2.5.0-118166.i386.bundle: No such file or directory
frost@ubuntu:~$ --

The file is of the same name, i checked, and its on the desktop.

Please help.

P.S. If this doesn't belong here please lemme know. 

P.P.S. Also please let me know how to move a thread!

Well. your command seems a little off.

Open a terminal and :

```
cd Desktop
```

Then run your command.

Also I would think the command would be more like:

gksu ./VMware-Player-2.5.0-118166.i386.bundle

but I am not sure.

> **jpdamigaman said:**
> HI when I have vmplayer installed I try to run a win 2000 VM which works in windows but I get a syntax error

see pic

Did you move your virtual hard drive to your linux partition and set the permissions or are you trying to access it from your Windows partition ?

Also, hijacking threads is considered rude, you should start your own :twisted:

---

### Post by jpdamigaman on 2008-11-14
HI Tried both options running from linux and windows partition

installed virtual box but wouldn't allow me to use VM I already have.

I heard V Box should work now with microsoft VMs
 
JPD

---

### Post by frost151n on 2008-11-15
thnx bodhi.zazen, xp is installing as i type this.
I think there's a problem with the keyboard in vm ware. won't know for certain until the installation completes.

should i mark this thread as solved or should i wait untill jpdamigaman issue is solved????

---

### Post by bodhi.zazen on 2008-11-15
> **frost151n said:**
> thnx bodhi.zazen, xp is installing as i type this.
I think there's a problem with the keyboard in vm ware. won't know for certain until the installation completes.

should i mark this thread as solved or should i wait untill jpdamigaman issue is solved????

Yes, there is an issues with the keyboard. It is "easy" to fix. Take a look at the thread(s) I posted on Vmware (there is a link in the mega thread at the top of these forums).

---

### Post by frost151n on 2008-11-16
kool man, thnx again.

---

