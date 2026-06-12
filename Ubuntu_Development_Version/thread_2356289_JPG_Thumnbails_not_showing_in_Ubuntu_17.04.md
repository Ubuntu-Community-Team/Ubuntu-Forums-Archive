---
title: "JPG Thumnbails not showing in Ubuntu 17.04"
date: 2017-03-21
forum: Ubuntu Development Version
---

### Post by skanger on 2017-03-21
I tried setting and resetting the thumbnail settings multiple times but still no jpg thumbnails. I also tried sudo rm -rf ~/.thumbnails/* ~/.cache/thumbnails/* and nothing changes. 

Tiff thumbnails show up just fine, so this is a puzzling problem. Any help appreciated.


Sk.

---

### Post by QIII on 2017-03-21
*Moved to **Ubuntu Development Version***

---

### Post by harry332 on 2017-03-22
This is the bug (1665602) report:
[https://bugs.launchpad.net/ubuntu/+source/gdk-pixbuf/+bug/1665602](https://bugs.launchpad.net/ubuntu/+source/gdk-pixbuf/+bug/1665602)
And it has been fixed.
The new gnome-desktop3 needs to have the package libgdk-pixbuf2.0-bin installed, because it uses the gdk-pixbuf thumbnailer.
So this is solved.

---

### Post by Hewjr100 on 2017-03-22
Tried installing libgdk-pixbuf2.0-bin and this is what I got

```
sudo apt install libgdk-pixbuf2.0-bin
[sudo] password for henry:          
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libgdk-pixbuf2.0-bin
E: Couldn't find any package by glob 'libgdk-pixbuf2.0-bin'
E: Couldn't find any package by regex 'libgdk-pixbuf2.0-bin'
henry@wyatt:~$
```

Am I doing something wrong?

Henry

---

### Post by howefield on 2017-03-22
> **Hewjr100 said:**
> Am I doing something wrong?

No, not doing anything wrong, I believe the package may still be in the proposed repository, so if you don't have that source enabled you won't see it until it migrates in to the main repository.

```
apt-cache policy libgdk-pixbuf2.0-bin
libgdk-pixbuf2.0-bin:
  Installed: (none)
  Candidate: 2.36.5-3
  Version table:
     2.36.5-3 500
        500 http://gb.archive.ubuntu.com/ubuntu zesty-proposed/main amd64 Packages
```

---

### Post by Hewjr100 on 2017-03-22
OK thanks.

Henry

---

### Post by howefield on 2017-03-22
> **Hewjr100 said:**
> OK thanks.

You're welcome, quite a lot sitting in -proposed at the minute, for this machine 150 packages.

Probably being held back until after the Beta is released tomorrow.

---

### Post by skanger on 2017-03-22
> **howefield said:**
> You're welcome, quite a lot sitting in -proposed at the minute, for this machine 150 packages.

Probably being held back until after the Beta is released tomorrow.

I have the same problem as Henry. I'm using 17.04 pseudo beta. Should I re-install the newly released beta or will the necessary files come via update?

In software updates there is an update showing but it won't install. Clicking on the install button causes the button to gray out and change to "installing" but it quickly reverts back to the normal install button.

---

### Post by howefield on 2017-03-22
> **skanger said:**
> I have the same problem as Henry. I'm using 17.04 pseudo beta. Should I re-install the newly released beta or will the necessary files come via update?

No need to reinstall, the updates will come through.

> In software updates there is an update showing but it won't install. Clicking on the install button causes the button to gray out and change to "installing" but it quickly reverts back to the normal install button.

Does the terminal command give you anything..

```
apt list --upgradeable
```

All I do with the development version is a simple daily...

```
sudo apt update
```
and
```
sudo apt upgrade
```

---

### Post by skanger on 2017-03-22
Apt list --upgradeable returned a long list. From a quick look it appears that every line has the word upgradeable. If it would help I'll copy it here.

I forgot about the command line update/upgrade. It brought in a large number of files and the software center update tab shows everything is up to date.

It doesn't look like it resolved the thumbnail problem though as I'm getting the same results from the same commands above.

---

### Post by howefield on 2017-03-22
> **skanger said:**
> Apt list --upgradeable returned a long list. From a quick look it appears that every line has the word upgradeable. If it would help I'll copy it here.

I forgot about the command line update/upgrade. It brought in a large number of files and the software center update tab shows everything is up to date.

It doesn't look like it resolved the thumbnail problem though as I'm getting the same results from the same commands above.

Cool, sounds like you are now up to date, as you really should be given that you are testing the development version.

As explained above the package you want is still in the proposed repository - that means you won't get it until the moves from proposed to the main repository unless you switch on that particular repository. 

If you open up the Software & Updates application and go to the *Developer* tab and place a checkmark against *Pre-released updates (zesty-propsed)* then reload your software sources after closing out, you would see the package you want. However, by enabling the proposed repository you significantly increase the chance of breakage which may or may not bother you, after all it is a development release for testing not a production machine ? :)

---

### Post by jbicha on 2017-03-23
No need to enabled -proposed updates.

The Beta Freeze is ending today (Thursday) so if you just wait a few hours, you'll get this fix and more.

---

### Post by Cavsfan on 2017-03-23
Just wanted to mention that if you prefer to update/upgrade via CLI then add an alias to ~/.bashrc.
No need for root access, just open up the file with the notepad application available to you and add this (or nano .bashrc):

```
alias ud='sudo apt update && sudo apt upgrade && sudo apt autoclean'
```

Then just close the terminal if open and enter in terminal **ud** and it will ask for your password and do the updates.

---

### Post by skanger on 2017-03-25
Thanks for the suggestions. Late Thursday night the updates solved that problem and created a new one.

Starting up the next day, the machine halted after the Ubuntu logo screen with just a movable mouse pointer and nothing else. Multiple reboots made no difference. 

The thumbnails were being rapidly generated Thursday night and all seemed very well - and I was relieved to be free of the disastrous W|ndows |O. 

I tried booting into safe mode via the left shift key, but it just boots as described above.

---

### Post by howefield on 2017-03-25
> **skanger said:**
> ..the machine halted after the Ubuntu logo screen with just a movable mouse pointer and nothing else. Multiple reboots made no difference. 

If you still have the machine at the "movable mouse pointer" try pressing Ctrl + Alt + F1 keys simultaneously to get to a console and login using your user account details.

Then do a..

```
sudo apt install unity-settings-daemon
```
and
```
sudo reboot
```

Should put you back to the desktop, at least it worked for me.

---

### Post by skanger on 2017-03-25
Thanks for the suggestion. 

The unity-settings-daemon command returned a message that nothing was installed but 357mb of unnecessary packages could be removed using autoremove. I ran that command and sudo rebooted but came back to the same blank screen and mouse pointer.

At least I know how to get to the command line now. I'm sure this must be some minor hangup that occurred due to the update from pre-beta to  beta.

---

### Post by howefield on 2017-03-25
> **skanger said:**
> The unity-settings-daemon command returned a message that nothing was installed

So did you try to install the package ?

```
sudo apt install unity-settings-daemon
```

```
apt-cache policy unity-settings-daemon
unity-settings-daemon:
  Installed: 15.04.1+17.04.20170322-0ubuntu1.1
  Candidate: 15.04.1+17.04.20170322-0ubuntu1.1
  Version table:
 *** 15.04.1+17.04.20170322-0ubuntu1.1 500
        500 http://gb.archive.ubuntu.com/ubuntu zesty/main amd64 Packages
        100 /var/lib/dpkg/status
```

[https://ubuntuforums.org/showthread.php?t=2356536](https://ubuntuforums.org/showthread.php?t=2356536)

---

### Post by skanger on 2017-03-25
I did try to install several times and received the same message: 0 installed 0 removed, etc.

However, thanks to your info on how to get into the console again, I received a message that packages were waiting to be installed and upgraded. I ran both and everything is back to normal again.

Apparently it was nothing more than cleaning out some old packages and bringing in the new.

Thank you!

---

### Post by howefield on 2017-03-25
> **skanger said:**
> I did try to install several times and received the same message: 0 installed 0 removed, etc.

However, thanks to your info on how to get into the console again, I received a message that packages were waiting to be installed and upgraded. I ran both and everything is back to normal again.

Apparently it was nothing more than cleaning out some old packages and bringing in the new.

Thank you!

Cool, glad you got it sussed.

Quite why the package would not install on its own but did as part of a group of packages is a mystery, but hey ho.

---

