---
title: "synaptic menu item not working"
date: 2014-03-13
forum: Ubuntu Development Version
---

### Post by ajgreeny on 2014-03-13
I have just (10:15 GMT) updated two installations of Lubuntu Trusty 32bit, one on real hardware, the second in VirtualBox, and in both cases I have lost the ability to start synaptic package manager from the menu or from the panel application launcher icon I have set, or even direct from the synaptic.desktop file in /usr/share/applications.

I have opened the .desktop file in leafpad and it all looks OK to me, and if I change the Exec command in that file from **synaptic-pkexec** to **gksudo synaptic** it works as expected.  The command **synaptic-pkexec** still works in terminal, so I am baffled.

Anyone else seen this and got any clues?

---

### Post by mc4man on 2014-03-13
In ubuntu haven't seen anything similar, maybe return .desktop to original Exec= & see if this produces anything in terminal
```
gtk-launch synaptic
```

---

### Post by ajgreeny on 2014-03-13
I do not have the problem in a VM of either Ubuntu or Xubuntu either only in Lubuntu for some reason, all of them fully updated.

Your suggested command produces
```
gkt-launch synaptic
No command 'gkt-launch' found, did you mean:
 Command 'gtk-launch' from package 'libgtk-3-bin' (main)
 Command 'gst-launch' from package 'gstreamer-tools' (main)
gkt-launch: command not found
``` I already have that **libgtk-3-bin** package installed, but the question is why has the synaptic.desktop file stopped working after the update?

Whatever the reason I have for now edited the Exec command in the synaptic.desktop file to **Exec=gksudo synaptic** to get it working again.

---

### Post by bapoumba on 2014-03-13
Same here. I upgraded to Trusty because your thread got me curious. lubuntu here.

---

### Post by ajgreeny on 2014-03-13
> **bapoumba said:**
> Same here. I upgraded to Trusty because your thread got me curious. lubuntu here.
Well, I'm glad it isn't just me, and although it's not a total show-stopper for me, nor you I guess, it would be difficult for less able users who may not know how to start synaptic other than using the menu.

Just to see if it helped I purged synaptic (and lubuntu-desktop), rebooted and then re-installed both packages, but the problem remains.

It seems to be only that synaptic.desktop file that is not working; I have changes the permissions of the file to see if that made any difference, but it seems not to have any effect.  I have not tried the 64 bit Lubuntu system to see if that is the same

---

### Post by bapoumba on 2014-03-14
Is this your bug ? [https://bugs.launchpad.net/ubuntu/+source/policykit-1/+bug/1288786](https://bugs.launchpad.net/ubuntu/+source/policykit-1/+bug/1288786)
Marked as affecting me.

---

### Post by ajgreeny on 2014-03-14
No not my bug, but I have now added my comments to it.

I see the bug was first reported 6 March, but I did not see the problem until 13 March, and had been updating all through that period without problems using synaptic which is always my preferred application for package management whichever of the *ubuntu family I am using.

---

### Post by Elfy on 2014-03-14
> **ajgreeny said:**
> I do not have the problem in a VM of either Ubuntu or Xubuntu either only in Lubuntu for some reason, all of them fully updated.

Your suggested command produces
```
gkt-launch synaptic
No command 'gkt-launch' found, did you mean:
 Command 'gtk-launch' from package 'libgtk-3-bin' (main)
 Command 'gst-launch' from package 'gstreamer-tools' (main)
gkt-launch: command not found
``` I already have that **libgtk-3-bin** package installed, but the question is why has the synaptic.desktop file stopped working after the update?

Whatever the reason I have for now edited the Exec command in the synaptic.desktop file to **Exec=gksudo synaptic** to get it working again.

typo?

The command from  mc4man is gtk-launch not gkt-launch ;)

---

### Post by ajgreeny on 2014-03-14
Oh WOW!

I must read a bit more carefully next time as I didn't notice that typo.

Now having edited the synaptic.desktop file back to original command **synaptic-pkexec** and run **gtk-launch synaptic** command from terminal I get the following error
```
$ ==== AUTHENTICATING FOR com.ubuntu.pkexec.synaptic ===
Authentication is required to run the Synaptic Package Manager
Authenticating as: My Name,,, (username)
Password: 
** (process:1937): ERROR **: Got unexpected EOF while reading from controlling terminal.
polkit-agent-helper-1: pam_authenticate failed: Authentication failure
Trace/breakpoint trap (core dumped)
```

---

### Post by mc4man on 2014-03-14
I would take look in /var/crash & see if there is a .crash for this. If so then right click on the whatever.crash  & file a bug  report.
Can't hurt & may be more useful than current bug 
( or may inform you of a current report from same crash

---

### Post by bapoumba on 2014-03-14
Lol, I did run the correct command yesterday and got the same error message.

Sorry to ask a dumb question. I have a /var/crash/_usr_bin_pkexec.0.crash and I get a "permission denied" when I try to report a problem with it. Can it be attached to a bug report ? I cannot open it. I'll look :)

Edit :
```
-rw-rw----  1 root whoopsie      0 mars  14 22:03 .lock
-rw-r-----  1 root whoopsie 330947 mars  14 22:29 _usr_bin_pkexec.0.crash
```

---

### Post by ajgreeny on 2014-03-14
You could open it as root, but I wouldn't bother as it will not help you much, being mainly 
> CoreDump: base64
 H4sICAAAAAAC/0NvcmVEdW1wAA==
 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
and such-like.

However, if you right click on that file it should offer you the chance to open it with "Report a problem"

---

### Post by bapoumba on 2014-03-14
Yes, but as I stated above, I get a "permission denied" when I try to report a problem. I'll attach a screenshot.

---

### Post by mc4man on 2014-03-14
For root owned .crash files either open /var/crash in a root browser or try from terminal in various ways - 
```
sudo /usr/bin/apport-cli /path/to/whatever.crash

```

or maybe 
 ```
gksudo /usr/share/apport/apport-gtk /path/to/whatever.crash
```

---

### Post by bapoumba on 2014-03-14
Thanks mc4man, first one did it. I promise I looked how to get around the permission denied as the file was not owned by me, but could not find anything to use.
[https://bugs.launchpad.net/ubuntu/+source/policykit-1/+bug/1292722](https://bugs.launchpad.net/ubuntu/+source/policykit-1/+bug/1292722)

It says the bug contains private information.

---

### Post by mc4man on 2014-03-14
> **bapoumba said:**
> 
[https://bugs.launchpad.net/ubuntu/+source/policykit-1/+bug/1292722](https://bugs.launchpad.net/ubuntu/+source/policykit-1/+bug/1292722)

It says the bug contains private information.
all bug reports from crashers thru appoprt  are 'private' until someone removes possible personal info (a bug triager

Myself wait for a retrace & then if after a day or two if not looked at or duped  generally mark as public as there is nothing on my testing install that could be compromising or whatever. 
Sometimes apport crash reports contain useful info to debug, sometimes not..

---

### Post by bapoumba on 2014-03-14
Well, I had a look at the files, and there was no real private info I could see. But I'm not that well trained :)
I cannot make it public myself. I linked to the previous bug in a comment. We shall see, thanks again!

---

### Post by mc4man on 2014-03-14
> **bapoumba said:**
> 
I cannot make it public myself. 
If you get inclined at some point you should be able to. On bug pages any yellow circle can be clicked on for an action or more. 
see screens as example (I've no private bugs atm so picked latest open one

Certainly no harm in waiting either..

---

### Post by bapoumba on 2014-03-15
OK thanks, I can indeed mark it public. I can wait too :)
(Sorry, I have not filed bugs and used LP in a long while).

---

### Post by bapoumba on 2014-03-18
The bug ajgreeny reported has been marked as a duplicate of this one, which has been marked as fix released : [https://bugs.launchpad.net/ubuntu/+source/lxsession/+bug/1292868](https://bugs.launchpad.net/ubuntu/+source/lxsession/+bug/1292868).
lxsession is at the proper version here, but opening synaptic with gtk-launch synaptic still brings up the same error here (all updates applied). Using the menu item or the launcher icon still does not work. I wonder if ajgreeny's bug really is a duplicate..

---

### Post by mc4man on 2014-03-18
> **bapoumba said:**
> The bug ajgreeny reported has been marked as a duplicate of this one, which has been marked as fix released : [https://bugs.launchpad.net/ubuntu/+source/lxsession/+bug/1292868](https://bugs.launchpad.net/ubuntu/+source/lxsession/+bug/1292868).
lxsession is at the proper version here, but opening synaptic with gtk-launch synaptic still brings up the same error here (all updates applied). Using the menu item or the launcher icon still does not work. I wonder if ajgreeny's bug really is a duplicate..

Seems reasonable that that was the problem (if so then your bug could also be duped & done.
I did notice that you seem to have an upgrade install, if so check that this is installed -
policykit-desktop-privileges

---

### Post by bapoumba on 2014-03-19
OK thanks, will look into this when I get home tonight :)

---

### Post by bapoumba on 2014-03-19
> **mc4man said:**
> Seems reasonable that that was the problem (if so then your bug could also be duped & done.
I did notice that you seem to have an upgrade install, if so check that this is installed -
policykit-desktop-privileges
Yes, this was an upgrade. The package is at the latest version as far as I can tell.

```
apt-cache policy policykit-desktop-privileges
policykit-desktop-privileges:
  Installed: 0.17
  Candidate: 0.17
  Version table:
 *** 0.17 0
        500 http://archive.ubuntu.com/ubuntu/ trusty/main i386 Packages
        100 /var/lib/dpkg/status

```

---

### Post by mc4man on 2014-03-19
> **bapoumba said:**
> Yes, this was an upgrade. The package is at the latest version as far as I can tell.

```
apt-cache policy policykit-desktop-privileges
policykit-desktop-privileges:
  Installed: 0.17
  Candidate: 0.17
  Version table:
 *** 0.17 0
        500 http://archive.ubuntu.com/ubuntu/ trusty/main i386 Packages
        100 /var/lib/dpkg/status

```

Odd then.
I did just try an lubuntu live session from yesterdays image. Once up I set up an new admin user, logged into that user & synaptic started up fine from menu & from cli (synaptic-pkexec), ie. got the auth window, entered password, ect.

What you may want to try is something similar - 
Set up a new user account to test, make it an admin account.
Log into that account & see if opening synaptic works from menu & or cli.

---

### Post by bapoumba on 2014-03-19
> **mc4man said:**
> Odd then.
I did just try an lubuntu live session from yesterdays image. Once up I set up an new admin user, logged into that user & synaptic started up fine from menu & from cli (synaptic-pkexec), ie. got the auth window, entered password, ect.

What you may want to try is something similar - 
Set up a new user account to test, make it an admin account.
Log into that account & see if opening synaptic works from menu & or cli.

Interesting, it does work from the menu with a new user. More interesting : as I always set up 2 users with admin privileges on any install I make, I tried with this other user created last summer during my fresh install. It is the first user created during the install process. It does work from this one too. Must be a desktop config file. I do not recall making changes on default desktop files, but you never know :)

---

### Post by bapoumba on 2014-04-03
Just to say I noticed starting synaptic from the menu has started to work again after yesterday's updates. It may have been fixed before that, but I had not checked.

---

