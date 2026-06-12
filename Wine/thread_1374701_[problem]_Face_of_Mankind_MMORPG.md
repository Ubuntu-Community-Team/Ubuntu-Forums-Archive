---
title: "[problem] Face of Mankind MMORPG"
date: 2010-01-07
forum: Wine
---

### Post by Apila-- on 2010-01-07
Well guys, I am trying to run Face of Mankind on Ubuntu 9.10 (even though its risky and not recommended by developers of FOM).

With wine I was able to install fom succesfully and the launcher starts normally. When I finally started patching, I encountered my first error: The launcher checked all the patches normally, but right when it was about to start installing, it encountered an error saying that there is an error downloading the patches. (Didnt even start downloading.)

Screenshot of the event:
[http://img137.imageshack.us/img137/5726/screenshotpha.png](http://img137.imageshack.us/img137/5726/screenshotpha.png)

My hardware is meeting the requirement and I am also able to run other similiar softwares which have launchers. 

Just a note: I tried disableing Ubuntu's default firewall UFW through terminan and after I rebooted to test this defaulted firewall, the problem persisted.

If there are any ideas you are able to throw at me, I'd be more than happy to test them.

---

### Post by pedro_orange on 2010-01-07
If the launcher is not letting you download the patches; can you not download them manually and run them outside of the launcher?

---

### Post by Apila-- on 2010-01-07
> **pedro_orange said:**
> If the launcher is not letting you download the patches; can you not download them manually and run them outside of the launcher?

I'm afraid that manual patching is not available at the moment. All the patches have to go through the launcher.

---

### Post by Apila-- on 2010-01-11
Bump

---

### Post by 666j.e.t on 2010-05-03
there is a way you can download them mauly but one of the files are missing from here [http://forum.fomportal.com/showthread.php?t=27487](http://forum.fomportal.com/showthread.php?t=27487) or though there are files missing like im stuck on getting 1540.irz.

---

### Post by Stefano74 on 2010-05-31
> **Apila-- said:**
> Well guys, I am trying to run Face of Mankind on Ubuntu 9.10 (even though its risky and not recommended by developers of FOM).

With wine I was able to install fom succesfully and the launcher starts normally. When I finally started patching, I encountered my first error: The launcher checked all the patches normally, but right when it was about to start installing, it encountered an error saying that there is an error downloading the patches. (Didnt even start downloading.)

Screenshot of the event:
[http://img137.imageshack.us/img137/5726/screenshotpha.png](http://img137.imageshack.us/img137/5726/screenshotpha.png)

My hardware is meeting the requirement and I am also able to run other similiar softwares which have launchers. 

Just a note: I tried disableing Ubuntu's default firewall UFW through terminan and after I rebooted to test this defaulted firewall, the problem persisted.

If there are any ideas you are able to throw at me, I'd be more than happy to test them.

I have your same problem! Did you find the solution?

---

### Post by DirtyV on 2010-06-13
If you need any of the patch files let me know and ill upload them.

---

### Post by Gibbs on 2010-07-26
Install wininet through winetricks.

I'm getting FOM organised on the AppDB. Check out [http://appdb.winehq.org/objectManager.php?sClass=version&iId=20574](http://appdb.winehq.org/objectManager.php?sClass=version&iId=20574)

---

