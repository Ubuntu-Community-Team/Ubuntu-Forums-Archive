---
title: "Install TuxGuardian on Kubuntu Gutsy"
date: 2007-11-02
forum: Server Platforms
---

### Post by Ubunteras on 2007-11-02
Hi,

had anybody success installing TuxGuardian on Gutsy?

I followed the steps as described in [http://tuxguardian.sourceforge.net/documentation.php](http://tuxguardian.sourceforge.net/documentation.php) but I am receiving following error:

nick@ZEUS:~/tuxguardian-0.5$ sudo modprobe tuxg
FATAL: Error inserting tuxg (/lib/modules/2.6.22-14-generic/tuxg.ko): Invalid argument

I am a newbie so please try to explain as easy as possible.

Thanks in advance...

---

### Post by ruibernardo on 2007-11-02
I think the documentation you are following says something about your problem just a little bit bellow:

> ** Tips and random remarks **

  If you have any [COLOR=red]problems loading the module[/COLOR] with '*modprobe tuxg*', make sure you don't have any other security modules loaded. If this is the case, try to run (as root) the following: 

[I] $ su
<enter root password>
$ modprobe -r capability[/I]So, probably, you need to run 
```
sudo modprobe -r capability
```and then
```
sudo modprobe tuxg
```Not trying to make you give up on tuxguardian :---) or anything, but I think that tuxguardian isn't being maintained for some time now. I doubt it will compile without errors and work without problems.

Try Apparmor if you are running Feisty or Gutsy. It is installed by default on Gutsy. To install it in Feisty follow the instructions in this page: [https://help.ubuntu.com/community/AppArmor](https://help.ubuntu.com/community/AppArmor).

---

### Post by Ubunteras on 2007-11-08
Thanks for your answer epimeteo!

You are right about TuxGuardian that isn't being maintained for some time now.

I ´ve just wanted a kind of ZoneAlarm on Linux. 

Something that is capable of throwing pop up messages when an app is trying to "phone home".

I couldn´t find anything but TuxGuardian capable of doing something like that.

If you are aware of another app like ZoneAlarm on Linux please tell me...

Apparmor doesn´t seem to do this work, but I will look deeper.

---

