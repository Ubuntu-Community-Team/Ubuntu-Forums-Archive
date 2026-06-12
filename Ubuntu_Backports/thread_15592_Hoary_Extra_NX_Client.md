---
title: "Hoary Extra: NX Client"
date: 2005-02-15
forum: Ubuntu Backports
---

### Post by jdong on 2005-02-15
**Synopsis**
*NoMachine NX is the next-generation X compression and roundtrip suppression scheme. It can operate remote X11 sessions over 56k modem dialup links or anything better.*

This is the client for FreeNX.

**Backporting Process**
Source kame from Kanotix.


**Packaging Status:**
i386 -- Staging at revision 35
amd64 -- Not packaged
ppc -- Not packaged

**Beta tester notes:**

---

### Post by Dromio on 2005-03-17
[QUOTE=jdong]**Synopsis**
*NoMachine NX is the next-generation X compression and roundtrip suppression scheme. It can operate remote X11 sessions over 56k modem dialup links or anything better.*

This is the client for FreeNX.

**Backporting Process**
Source kame from Kanotix.


**Packaging Status:**
i386 -- Staging at revision 35
amd64 -- Not packaged
ppc -- Not packaged

**Beta tester notes:**[/QUOTE]
 Sure would love this for amd64.  I know nothing about building packages.  Would this be a good place to start?

---

### Post by jdong on 2005-03-17
Unfortunately, FreeNX has been known not to compile under AMD64. I do not have the time to invest in getting that to work -- it's been ongoing in Gentoo, unsure what the current resolution is.

---

### Post by dare2dreamer on 2005-03-31
freenx server doesn't work on hoary for me. I tried setting it up with the nomachine key, and it still refuses to allow me to login.

---

### Post by dare2dreamer on 2005-03-31
Ok, a little further hacking and I got it working. Seems that it didn't properly set up the /home/.nx directory or the nomachine key by default. I created the directory, ran nxsetup as root and then it started up. To get my user able to log in, I had to manually set the password with nxserver though.

As I recall, I did not have these issues with the kalyxo.org freenx builds.

---

### Post by jdong on 2005-04-04
I need to investigate on these backports, including the FreeNX server for Hoary.

It seems like some R-Deps were updated by Canonical since the package was compiled.

---

### Post by A-star on 2005-04-05
I installed the nxserver this mornong (05/04/2005), it installed fine, but gave me a message about "authentication" or something.

After using it for a whille , it seems that the warty version is more stable then the hoary version
*k3b and the servers just cuts the connection.
*same with mplayer (not even opening a movie, just changing the preferences).

---

### Post by btdown on 2005-04-14
Could someone give me instructions on the right way to install freenx? (server)  I noticed another thread, but it seemed geared toward warty and i really dont want to screw up my distro.

Any help for setting this up on hoary 5.04 would be greatly appreciated.

Thanks,
BT

---

### Post by jdong on 2005-04-14
As I said a few posts up, recompiling Hoary NX is on my todo list... Many things have changed in Hoary since I initially packaged this.

Kalyxo's site (which contains NX Debian sources) is pretty quirky recently, so it may be a while before I can get this packaged (read: next week ;))

---

### Post by jdong on 2005-04-14
[https://sourceforge.net/pm/task.php?func=detailtask&project_task_id=114431&group_id=125877&group_project_id=42440](https://sourceforge.net/pm/task.php?func=detailtask&project_task_id=114431&group_id=125877&group_project_id=42440)

I've assigned a task to rebuild NX. However, it'll be a while (due to Kalyxo being down) before it can be actually built.

---

### Post by btdown on 2005-04-15
Thank you for the info!
BT

---

### Post by marko on 2005-04-22
[QUOTE=jdong][https://sourceforge.net/pm/task.php?func=detailtask&project_task_id=114431&group_id=125877&group_project_id=42440](https://sourceforge.net/pm/task.php?func=detailtask&project_task_id=114431&group_id=125877&group_project_id=42440)

I've assigned a task to rebuild NX. However, it'll be a while (due to Kalyxo being down) before it can be actually built.[/QUOTE]

Any progress.  I am antsy to get my Freenx going on Hoary!  Thanks much in advance.

---

### Post by btdown on 2005-04-22
ditto...

BTW i was able to get it working on 5.04 test laptop using the how-to found somewhere on this site, however, I'm hestitant to put it on my "real" machine because it seems sorta hinky.

---

### Post by jdong on 2005-04-24
Kalyxo.org has been a mess after that break-in... I'm still working on it.

---

### Post by boskone on 2005-04-24
For what it's worth, to get it working all I had to do was edit /usr/bin/nxsetup, line 83.  Remove the '/' between $NX_HOME_DIR and $NX_AUTHORIZED_KEYS_FILE.  There's probably a less hackish way of doing this, but I didn't bother finding out where those variables are set.

---

### Post by btdown on 2005-04-24
Thanks for the update Jdong!

-=BT

---

