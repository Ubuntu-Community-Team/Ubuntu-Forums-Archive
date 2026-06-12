---
title: "Misinformation on the Wiki about updating the Mozilla version of Firefox"
date: 2007-04-06
forum: The Cafe
---

### Post by aysiu on 2007-04-06
[The Wiki entry on installing (and, in this case, updating) the Mozilla version of Firefox](https://help.ubuntu.com/community/FirefoxNewVersion#head-63727d73c1ddc18dd45d4c74609fff93c3919abc) appears to have some misinformation: > **Note that the following alternative method may give some files in your home directory root ownership and cause problems.** The first method above is safer. To update firefox you can run Firefox from the terminal with  gksudo firefox . Be sure to close any running version of Firefox first. Enter your password where prompted. Then check update (Help -> Check for updates...). If updates are found, apply the update and when it asks to restart, use the "Later" option. If "Restart" is chosen, it can result in Firefox launching again with non-root privileges, causing the update to fail. After choosing "Later", close Firefox normally and relaunch with  gksudo firefox . When Firefox starts you should see a Mozilla page confirming that you're using the latest version. Close Firefox and open it as a normal user (the way you usually open it). Firefox should now be updated to the newest version for all users. This way you don't have to change any file permissions and you won't forget to not change them back. The use of ```
gksudo firefox
``` will not change ownership of files in your home directory to root. ```
sudo firefox
``` however, might. More details here:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

Is it okay if I just go in and edit that page and take out the warning? On what basis is that warning in there?

---

### Post by tbroderick on 2007-04-06
Maybe it means running gksudo firefox might cause anything new in your ~/.mozilla folder to have root ownership.

---

### Post by aysiu on 2007-04-06
> **tbroderick said:**
> Maybe it means running gksudo firefox might cause anything new in your ~/.mozilla folder to have root ownership.
And I'm saying that's incorrect.

```
sudo firefox
``` opens Firefox with root privileges but uses the user's .mozilla profile.

```
gksudo firefox
``` opens Firefox with root privileges and uses root's .mozilla profile. It does not affect the user's .mozilla profile at all.

That's why I'm saying it's misinformation. I understand *exactly* what the Wiki is saying. And the Wiki is wrong.

---

### Post by rai4shu2 on 2007-04-06
So, should we ever tell people to use sudo? Considering the goal of Ubuntu is more or less to get everything working in a graphical environment, maybe it would be better to tell people to use gksudo/kdesu for everything sudo-related.

Is there some important difference between gksudo and gksu?

---

### Post by aysiu on 2007-04-06
> **rai4shu2 said:**
> So, should we ever tell people to use sudo? Considering the goal of Ubuntu is more or less to get everything working in a graphical environment, maybe it would be better to tell people to use gksudo/kdesu for everything sudo-related.

Is there some important difference between gksudo and gksu?
*sudo* is for terminal applications. *gksudo* and *kdesu* are for graphical applications. I've explained more about this here:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

There is no difference between *gksudo* and *gksu*, though. In another thread, someone has already established that *gksudo* is just pointing to *gksu*.

---

### Post by TravisNewman on 2007-04-06
Edit away. If you see misinformation, correct it. IMO

---

### Post by tbroderick on 2007-04-06
> **aysiu said:**
> 
That's why I'm saying it's misinformation. I understand *exactly* what the Wiki is saying. And the Wiki is wrong.

Maybe you should test it out first to make sure it's misinformation before it's deleted. Maybe someone actually had the problem listed.

---

### Post by aysiu on 2007-04-06
> **tbroderick said:**
> Maybe you should test it out first to make sure it's misinformation before it's deleted. Maybe someone actually had the problem listed.
I have tested it, which is why I brought up the issue.

I've gone ahead and edited it. It nows says: > To update firefox you can run Firefox from the terminal with ```
gksudo firefox
``` Be sure to close any running version of Firefox first. Enter your password where prompted. Then check update (Help -> Check for updates...). If updates are found, apply the update and when it asks to restart, use the "Restart" option. When Firefox starts, you should see a Mozilla page confirming that you're using the latest version. Close Firefox and open it as a normal user (the way you usually open it). Firefox should now be updated to the newest version for all users. This way you don't have to change any file permissions and you won't forget to not change them back.

Note that in the second method, you must use the command  ```
gksudo firefox
```  Do not use ```
sudo firefox
```  instead as it may give some files in your home directory root ownership and cause problems. 

---

