---
title: "VirtualBox not starting up since Natty upgrade"
date: 2011-05-04
forum: Virtualisation
---

### Post by patman0623 on 2011-05-04
Since I upgraded yesterday to Natty, my VirtualBox machine has been unable to start up. I am using the OSE version, and I get the following message:

```
Failed to create the VirtualBox COM object.
The application will now terminate.
Given default machine folder '~/.VirtualBox/Machines' is not fully qualified.

Result Code: 
NS_ERROR_INVALID_ARG (0x80070057)
Component: 
SystemProperties
Interface: 
ISystemProperties {51c81048-b261-4fa2-a44e-fd756f0db589}
```

First off, I note that ~/.VirtualBox/Machines doesn't exist on my machine. So I created it and gave it full permissions, but the error message persisted.

I've also tried cleaning out my /tmp folder, force reinstalling VirtualBox from the repositories, and starting/stop by ```
sudo /etc/init.d/virtualbox-ose
```.

None of this has worked. Does anyone know what the problem might be?

---

### Post by _outlawed_ on 2011-05-04
Have you tried the Oracle VirtualBox to see if it produces the same results?

[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

---

### Post by Dr. Nick on 2011-05-04
I know virtual box use to be plagued with kernel updates, you would have to reinstall it or reconfigure the kernel module if you updated kernels, you could try selecting the old kernel from the grub screen and see if it works that way, or just completely remove it including config files are reinstall it.

---

### Post by patman0623 on 2011-05-04
> **_outlawed_ said:**
> Have you tried the Oracle VirtualBox to see if it produces the same results?

[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)No; I didn't know about that but I'll try it; but I don't want to lose my data from before.

> **Dr. Nick said:**
> I know virtual box use to be plagued with kernel updates, you would have to reinstall it or reconfigure the kernel module if you updated kernels, you could try selecting the old kernel from the grub screen and see if it works that way, or just completely remove it including config files are reinstall it.Yes, I've had issues with this before, but I can't seem to find a way to recompile vboxdrv from source like I did.

---

### Post by patman0623 on 2011-05-04
Alright, I have installed the new version of VirtualBox and it still has the error. I'd think that installing a new version would wipe the kernel drivers; I could be wrong though.

---

### Post by patman0623 on 2011-05-04
And now I've restarted under the old kernel, and it didn't work, and I've reinstalled the vboxdrv module via vboxdrv setup and it still isn't working. Same error message.

---

### Post by Dr. Nick on 2011-05-04
Only idea I have is try removing it from synaptic and make sure to mark for complete removal

---

### Post by patman0623 on 2011-05-04
> **Dr. Nick said:**
> Only idea I have is try removing it from synaptic and make sure to mark for complete removalI had to uninstall it to install the new version. But for complete removal, I fear I'll lose my virtual hard drive, which is bad, because it took a long time to set up.

---

### Post by Dr. Nick on 2011-05-04
You should not loose the virtual hd, I would back it up just in case though.  You would have to setup the virtual machine again but you should be able to select your existing image in the new machine. I have never had this problem before so take my advice accordingly. Good luck

---

### Post by patman0623 on 2011-05-05
Alright, I ran ```
sudo apt-get purge virtualbox
``` before reinstalling, and still no success (same error message). Running via command line and even using the debug switches is coming up with nothing but that error message.

The only clue I have is this this message I got when installing the .deb package: ```
Lintian check results for /home/patrick/Desktop/virtualbox-4.0_4.0.6-71344~Ubuntu~natty_i386.deb:
E: virtualbox-4.0: maintainer-script-removes-device-files prerm:27
```I have a sinking feeling I might need to take this to the virtualbox forums.

---

### Post by patman0623 on 2011-05-06
Well I don't know if this means anything, but when I ran a bug report on Xorg, part of the report showed this:

```
DkmsStatus:
 vboxhost, 4.0.6, 2.6.38-8-generic, i686: installed
 bcmwl, 5.100.82.38+bdcom, 2.6.38-8-generic, i686: installed
 bcmwl, 5.100.82.38+bdcom, 2.6.35-28-generic, i686: installed
 virtualbox-ose, 4.0.4, 2.6.38-8-generic, i686: installed (WARNING! Diff between built and installed module!) (WARNING! Diff between built and installed module!) (WARNING! Diff between built and installed module!)
 virtualbox-ose, 4.0.4, 2.6.35-28-generic, i686: installed (WARNING! Diff between built and installed module!) (WARNING! Diff between built and installed module!) (WARNING! Diff between built and installed module!)
```

Might this be part of my problem?

---

### Post by Ldx63 on 2011-05-07
> **patman0623 said:**
> Since I upgraded yesterday to Natty, my VirtualBox machine has been unable to start up. I am using the OSE version, and I get the following message:

(cut)


Hi, I've just got the same problem and solved this way:

[LIST=1]
[*]Edit the file .VirtualBox/VirtualBox.xml (you should show hidden files first to access the .VirtualBox folder).
[*]Locate the line with the "defaultMachineFolder" property: it contains the "offending" value like ".VirtualBox/Machines" or something like that.
[*] Change it by prepending the complete path of your home directory (i.e. "/home/yourname/.VirtualBox/Machines"). Save and start VirtualBox.
[/LIST]
 Hope this solves your problem.
Aldo

---

### Post by patman0623 on 2011-05-07
> **Ldx63 said:**
> Hi, I've just got the same problem and solved this way:

[LIST=1]
[*]Edit the file .VirtualBox/VirtualBox.xml (you should show hidden files first to access the .VirtualBox folder).
[*]Locate the line with the "defaultMachineFolder" property: it contains the "offending" value like ".VirtualBox/Machines" or something like that.
[*] Change it by prepending the complete path of your home directory (i.e. "/home/yourname/.VirtualBox/Machines"). Save and start VirtualBox.
[/LIST]
 Hope this solves your problem.
Aldo

Ha! Thanks! I thought it might be something like that! And indeed it was. Now, do I report this as a bug to Ubuntu (whose APIs aren't reading the "~" directory) or to VirtualBox?

---

