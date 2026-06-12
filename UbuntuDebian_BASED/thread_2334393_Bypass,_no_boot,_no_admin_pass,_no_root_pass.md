---
title: "Bypass, no boot, no admin pass, no root pass"
date: 2016-08-19
forum: Ubuntu/Debian BASED
---

### Post by neonred on 2016-08-19
So I caused my system not to boot by adding a line to fstab.
Booting into recovery mode, absolutely worthless as I set a root password which I could not remember.
Finally figured out how to get back into the system and fix everything.
Btw, my distro is linux lite 3.0; an offshore and the Big brother of Ubuntu.
So what you do is you load the same live cd of your distro, in my case linux lite 3.0
Once its done loading from the cd, open a terminal and type sudo Thunar (or whatever the default file manager for your distro)
Now go to /etc/fstab and remove faulty line, you can also choose to keep the file empty (no difference).
Save the file, it will save only if you opened via sudoed File manager.
Now restart your system.
The likely scenerio is you will have no GUI, and will be required to log in, do that.
There's a few reasons why it took so long to boot and why the GUI did not load.
What has happened is that during the boot, linux has basically erased /etc/fstab , but kept a backup file for reference only.
That's the reason the boot took so long.
The reason the gui didn't load is because of the former problem results in a read only system
Let's over rule that. first determine the directly of your main drive by typing: fdisk -l
Now type: sudo mount -o remount,rw /dev/sda1 (replace with your main system drive)
At this point, the GUI will probably load up, whether it does or does not matters not yet.
now type: sudo dpkg-reconfigure lightdm
Also make sure /etc/x11/default-display-manager contains /usr/sbin/lightdm (this file should only contain one entry)
That is the default entry for any Ubuntu based distro.  If it was wrong, you sudo FileManager, open, edit, save.
Now we need to fix the fstab, but we cannot rely on the reference file as the reference is no longer valid.
Go to /dev/disk/by-uuid/
There should be 2 entries in most cases, look to the type in my case one is sda1 and sda5
sda1 refers to main drive, and sda5 refers to the swap
Will copy the uuid from these two devices and paste to replace in the reference file, we will then copy the reference file, sudo file manager open stab, paste and save.
Finally we will run again sudo dpkg-reconfigure lightdm

Done!

---

### Post by coffeecat on 2016-08-19
> **neonred said:**
> my distro is linux lite 3.0;

Not an official flavour of Ubuntu.

*Thread moved to **Ubuntu/Debian BASED**.*

Was there a question for our members? I cannot make out one from your wall of text.

---

### Post by Habitual on 2016-08-19
linux lite 3.0; an offshore and the Big brother of Ubuntu?

---

### Post by neonred on 2016-08-19
Yes thank goodness its not an official flavour of Ubuntu as all official flavours of Ubuntu share the same annoying bugs release after release.
The top 2 most notorious is the password not working after a while (I suspect the keyboard mapping gets screwed up), and the update process often causes system instability; too many times have I rebooted after an update to only be greeted by a black screen or just the background with no terminal or ability to login.
This is stupid.
Hence Linux Lite 3.0, its the big brother because its 10X better than Ubuntu in every aspect and there are no bugs that I have ever come across; zero.
System stability is flawless, the login screen of somekind always shows up, traditional or gui depending on if you screw the system up.
Ubuntu is a joy up until the moment where nothing works then you never want to use it again.
How is linux suppose to get more market share, the when the basic ubuntu dev community avoids fixing the most annoying bugs; stupid.
There are 3 reasons people avoid linux: hardware capability nowdays looking very good, configuration instability; one day you use it, the next day you can't login, and finally general complexity compared to windows.  But when you have a stable OS like Linux Lite, it shines Linux in the best possible light the complexities are rather just memorized commands.  Why do you think Microsoft says it loves linux; because it fears it greatly.  Linux as a whole is so close to over-running windows, yet the general mystery remains elusive when it is so simple to understand and fix.  In my opinion, Linux Lite crushes Windows 10, even Windows XP.  Microsoft itself if it could would admit its code base is garbage compared to linux; but it has to keep its monopoly which even as a casual gamer annoys the hell out of me.  Especially when it has to be certain that Microsoft pays the major game studios (in some way) to keep its monopoly.  The only advantage for the linux community is the absence of malware due to low market share.  Linux is often over hipped for security, especially given the open source nature which is a strength for development, but a weakness for security.

---

### Post by coffeecat on 2016-08-19
> **neonred said:**
> 
This is stupid.

...

stupid.


...

garbage

@neonred, please read the forum [Code of conduct](https://ubuntuforums.org/misc.php?do=showrules).

Thread closed.

---

