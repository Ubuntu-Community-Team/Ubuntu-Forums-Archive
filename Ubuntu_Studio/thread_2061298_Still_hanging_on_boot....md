---
title: "Still hanging on boot..."
date: 2012-09-22
forum: Ubuntu Studio
---

### Post by Alecossy on 2012-09-22
Hey there... 
This issue has been already discussed before but we didn't come to a solution.
While booting my distro, past the log-in window the system hangs for about a minute before loading the DE...
Any idea what (and where) i might look into to solve it out?

---

### Post by krishna.988 on 2012-09-22
> **Alecossy said:**
> Hey there... 
This issue has been already discussed before but we didn't come to a solution.
While booting my distro, past the log-in window the system hangs for about a minute before loading the DE...
Any idea what (and where) i might look into to solve it out?


What is the hardware using?

---

### Post by Alecossy on 2012-09-22
i'm using an aspire 5742ZG... it only happens with xfce... with Unity (which I installed following the official guide on the website) it doesn't happen...

---

### Post by krishna.988 on 2012-09-22
> **Alecossy said:**
> i'm using an aspire 5742ZG... it only happens with xfce... with Unity (which I installed following the official guide on the website) it doesn't happen...


I think it is better to choose unity as ubuntu is much more optimized with unity

---

### Post by Alecossy on 2012-09-22
> **krishna.988 said:**
> I think it is better to choose unity as ubuntu is much more optimized with unity
Ubuntu Studio is based on Xubuntu, and uses xfce as its default Desktop Environment... changing to unity is a test I wanted to do but I don't suppose it should happen by default.

---

### Post by Alecossy on 2012-09-22
> **Alecossy said:**
> Ubuntu Studio is based on Xubuntu, and uses xfce as its default Desktop Environment... changing to unity is a test I wanted to do but I don't suppose it should happen by default.
Edit: I just found out that there's a similar behaviour while logging out from a xfce session...
It will hang on the black screen for about a minute and when it finally gets back to the user selection screen the name of the user u just logged out from is not listed anymore...
This is starting to **** me off.. :S

---

### Post by gdesilva on 2012-09-23
From what you have described it appears you are not getting the Plymouth screen but going straight into logon screen. After the grub screen do you see a rotating arrow with a caption "Linux for creative humans"? If not that means the Plymouth screen is not working and to fix it check out the following.

[http://ubuntuforums.org/showthread.php?t=2012413](http://ubuntuforums.org/showthread.php?t=2012413)

Hope this helps.

---

### Post by Alecossy on 2012-09-23
I do... 
I see the rotating screen, then I pick my account, choose the DE i want to use (ubuntustudio by default), input my password and press enter...
Then I see the background but instead of loading, the DE just hangs on for about a minute, then loads normally...

---

### Post by gdesilva on 2012-09-23
A couple of things to consider....

1. Does the same happen if you choose xfce4 rather than ubuntustudio as the desktop manager?
2. Perhaps, worth checking out the logs in /var/log/ for any errors.
3. Are you using a customized wallpaper? If so, what would happen if you go back to a system default wallpaper?

---

