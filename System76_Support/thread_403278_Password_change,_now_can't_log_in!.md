---
title: "Password change, now can't log in!"
date: 2007-04-06
forum: System76 Support
---

### Post by madcitybrit on 2007-04-06
Hello

I have a Darter, running the default Gnome, and while logged in earlier today decided to change my password to make things a little more secure. So, logged into Gnome, and via the users/groups admin tool, I essentially updated my password with one additional character at the beginning. Because I was just adding an additional character, I didn't re-type the whole password as it was already there (masked though of course), just added the additional character instead. I did the same for the 'confirm password' box also and closed the dialog no problem. I also went and updated the root password the same way. After doing this I locked my screen for a bathroom break, and when I came back couldn't unlock it; Neither my new password or the old one worked. I had to hard-reset the machine. At this point I can no longer log in as my user or root; neither the old or new passwords are accepted. Luckily the laptop is quite new and I don't yet have much on there or everything configured to my liking. What files I do have are backed up so I won't be losing any files if I do need to restore. I do have an old Knoppix CD too, if that can be used to attempt any password resets, but I don't want to spend much time 'messing' with this.

Is there anything I can do? Or do I need to restore my system (using the restore CD supplied by System76)? 

Any help is much appreciated. 

Cheers.

---

### Post by gborzi on 2007-04-06
Start your system in recovery mode, it shouldn't ask you any password and log in as root. Then change the passwords for root and your user. BTW, I think that may now your password is the first letter you have type followed by asterisks.

---

### Post by madcitybrit on 2007-04-07
Yeah, I tried the first new letter followed by asterisks for the rest, and that didn't work. Also, I had changed the root password the same way as my user (with one new character at the front) and can't log in as root either. Tried booting in recovery mode, but that didn't work either. I also tried upper case for the first new letter, in the event Caps was on when I changed both passwords, and I tried all surrounding characters to the one I typed in case I hit the wrong key, but still no luck. Something somewhere goofed up. Looks like I may have to restore my system, unless anyone has any other suggestions as to a quick fix. 

Thanks.

---

### Post by gborzi on 2007-04-07
I have found this [http://ubuntuforums.org/showthread.php?t=396954](http://ubuntuforums.org/showthread.php?t=396954) . I hope it works.

---

### Post by madcitybrit on 2007-04-07
Thanks for the link. I booted with an old Knoppix CD and followed all instructions to the letter, which seemed to work okay, except that I still couldn't log in when rebooting to Ubuntu with no password for either root or my regular user. I'll try following the process again for resetting the password in case I missed something and let you know.

In the mean time, if I do end up re-installing, do you know whether the Darter ships with 32 or 64 bit Ubuntu? I'm going to download 6.10 as, disappointingly, the Darter doesn't ship with a copy of its own, and I didn't know which to get to recover my system back to its original state.

Thanks.

---

### Post by gborzi on 2007-04-07
> **madcitybrit said:**
> Thanks for the link. I booted with an old Knoppix CD and followed all instructions to the letter, which seemed to work okay, except that I still couldn't log in when rebooting to Ubuntu with no password for either root or my regular user. I'll try following the process again for resetting the password in case I missed something and let you know.

I don't understand what do you mean by "log with no password". Do you mean autologin ? If this is the case, autologin is activated by *Administration -> Login Window -> Security -> Enable Automatic Login*.

> **madcitybrit said:**
> In the mean time, if I do end up re-installing, do you know whether the Darter ships with 32 or 64 bit Ubuntu? I'm going to download 6.10 as, disappointingly, the Darter doesn't ship with a copy of its own, and I didn't know which to get to recover my system back to its original state.

Thanks.
What's "the Darter" ? BTW, to see if a system is a 32 or 64 bit system, type *uname -m* in the command line. The output will be x86_64 for 64 bit systems, i686 for 32 bit systems.

---

### Post by maniacmusician on 2007-04-07
> **madcitybrit said:**
> Thanks for the link. I booted with an old Knoppix CD and followed all instructions to the letter, which seemed to work okay, except that I still couldn't log in when rebooting to Ubuntu with no password for either root or my regular user. I'll try following the process again for resetting the password in case I missed something and let you know.

In the mean time, if I do end up re-installing, do you know whether the Darter ships with 32 or 64 bit Ubuntu? I'm going to download 6.10 as, disappointingly, the Darter doesn't ship with a copy of its own, and I didn't know which to get to recover my system back to its original state.

Thanks.
I think it's 32-bit.  System76 also has a driver that you can obtain from their site to get  your OS functioning perfectly with their hardware once you reinstall.

@gborzi: the Darter is a laptop that is offered by System76

---

### Post by madcitybrit on 2007-04-07
> **gborzi said:**
> I don't understand what do you mean by "log with no password". Do you mean autologin ? If this is the case, autologin is activated by *Administration -> Login Window -> Security -> Enable Automatic Login*.

The instructions from the link you provided had me editing the shadow file, removing a key that contains the password, so that upon rebooting I should be able to log into my system as root with no password (just leaving pwd blank). Didn't work for me though! :)

>  What's "the Darter" ? BTW, to see if a system is a 32 or 64 bit system, type *uname -m* in the command line. The output will be x86_64 for 64 bit systems, i686 for 32 bit systems.

Darter is the model name of a System76 laptop, which I have. [www.system76.com](www.system76.com). The Darter is on the front page.

Thanks for your help.

---

### Post by madcitybrit on 2007-04-07
> **maniacmusician said:**
> I think it's 32-bit.  System76 also has a driver that you can obtain from their site to get  your OS functioning perfectly with their hardware once you reinstall.

@gborzi: the Darter is a laptop that is offered by System76

I downloaded both 32 and 64 bit versions this morning just in case as I am now currently on the road. I'll begin installing the 32 bit version as some other posts appear to be saying the same thing (but still no definite answer though!).

I noticed in the System76 knowledge base some simple instructions for getting their drivers. Looks like it should be an easy process.

Thanks for the insight. Here I go... :)

---

### Post by gborzi on 2007-04-07
I didn't know about this new system76 laptop. I looked for a system76 laptop some times ago, when I had to replace my Compaq evo610, but since they don't ship to Italy, I stopped looking at their site. Thanks @madcitybrit and @maniacmusician for the information about the Darter.

---

