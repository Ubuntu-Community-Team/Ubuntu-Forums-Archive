---
title: "[SOLVED] Reactivation Problem - VMWare w/ XP Home"
date: 2008-04-03
forum: Virtualisation
---

### Post by jakornblum on 2008-04-03
OK... so here's what to do if you are having trouble with have a dual boot of Windows XP home and Ubuntu 7.10 and are simultaneously virtualizing XP inside of Ubuntu 7.10. If you are having trouble with Windows asking for reactivation everytime you switch from a native boot to vmware or vice versa:

1. Boot into XP natively. Activate (or reactivate) XP when prompted. Navigate to c:\WINDOWS\system32. Create a new folder called nativeboot (c:\WINDOWS\system32\nativeboot\) and copy the files wpa.bak and wpa.dbl (from the system32 folder) into the nativeboot folder.

2. Boot into Ubuntu. Boot the XP virtualization in VMWare. Reactivate when it asks you to upon startup. Go to c:\WINDOWS\system32. Create a new folder called vmware (c:\WINDOWS\system32\vmware\). Copy the files wpa.bak and wpa.dbl (from the system 32 folder) into the vmware folder.

3. Open up a terminal in Ubuntu. Use:
```
gksu gedit bootwindows.sh
```

4. Copy the following code into the text editor:

```
#!/bin/bash
gksu mount -t ntfs /dev/sdb1 /media/windowsdrive &&
gksu "cp --remove-destination /media/windowsdrive/WINDOWS/system32/vmware/wpa.bak /media/windowsdrive/WINDOWS/system32/wpa.bak" &&
gksu "cp --remove-destination /media/windowsdrive/WINDOWS/system32/vmware/wpa.dbl /media/windowsdrive/WINDOWS/system32/wpa.dbl" &&
gksu umount /media/windowsdrive &&

gksu "vmware -l -X -t -q /root/vmware/Windows\ XP\ Home\ Edition/Windows\ XP\ Home\ Edition.vmx"

gksu mount -t ntfs /dev/sdb1 /media/windowsdrive &&
gksu "cp --remove-destination /media/windowsdrive/WINDOWS/system32/nativeboot/wpa.bak /media/windowsdrive/WINDOWS/system32/wpa.bak" &&
gksu "cp --remove-destination /media/windowsdrive/WINDOWS/system32/nativeboot/wpa.dbl /media/windowsdrive/WINDOWS/system32/wpa.dbl" &&
gksu umount /media/windowsdrive
```

***obviously above you would replace /dev/sbd1 with the name of your Windows partition; replace /media/windowsdrive with the mounting location of your Windows partition; replace /root/vmware/Windows\ XP\ Home\ Edition/Windows\ XP\ Home\ Edition.vmx with the location of your VMWare .vmx file.

5. Save the file. Close the text editor. Use the command:
```
chmod 755 bootwindows.sh
```

6. Create a link to the bootwindows.sh file and run it. Everything should work fine! Be warned: if your system crashes while you're running the virtual machine, the wpa files from the virtual boot will remain active, so booting natively into XP at that point will trigger reactivation.

Another caveat:
Make sure that you are not running your virtual machine on a device that is already mounted in Ubuntu. This could cause partition corruption = not good at all.

If you need any clarification or this doesn't work for you, reply to the post and I will try to get you going. Good luck!




***ORIGINAL POST***
I currently have a dual boot setup of Ubuntu 7.10 and Windows XP Home.  Ubuntu is on the first partition of the master hard drive (SDA1), while XP is on the entire slave drive (SDB1).  I can boot natively into XP and I can virtualize it flawlessly with VMWare.  However, everytime I switch between a native boot and a virtual boot, Windows freaks out and makes me reactivate.  I can get around the reactivation by using copies of the WPA.bak and WPA.dbl (one set for the native boot and one set for the virtualization).  However, this is a pain to do manually every time, so I wrote a script to automate the process.  I was just wondering if the script would work, because I am too afraid to test it (sdb1 cannot be mounted when vmware starts the virtualization or else partition corruption will occur!).  Can someone please let me know if this will work?  It is very important that sdb1 is mounted, the files are copied, and sdb1 is unmounted before vmware starts.  Also, will the script wait for vmware to close before the drive is remounted, the second set of files are copied, and then is unmounted again?  Please let me know what you think.
THANKS!

```

#!/bin/bash
sudo mount -t ntfs /dev/sdb1 /media/windowsdrive
sudo cp /media/windowsdrive/WINDOWS/system32/vmware/wpa.bak /media/windowsdrive/WINDOWS/system32/wpa.bak
sudo cp /media/windowsdrive/WINDOWS/system32/vmware/wpa.dbl /media/windowsdrive/WINDOWS/system32/wpa.dbl
sudo umount /media/windowsdrive

gksu "vmware -l -X -t /root/vmware/Windows\ XP\ Home\ Edition/Windows\ XP\ Home\ Edition.vmx"

sudo mount -t ntfs /dev/sdb1 /media/windowsdrive
sudo cp /media/windowsdrive/WINDOWS/system32/nativeboot/wpa.bak /media/windowsdrive/WINDOWS/system32/wpa.bak
sudo cp /media/windowsdrive/WINDOWS/system32/nativeboot/wpa.dbl /media/windowsdrive/WINDOWS/system32/wpa.dbl
sudo umount /media/windowsdrive

```

---

### Post by prshah on 2008-04-03
> **jakornblum said:**
> ```

sudo umount /media/windowsdrive

gksu "vmware -l -X -t /root/vmware/Windows\ XP\ Home\ Edition/Windows\ XP\ Home\ Edition.vmx"


```

Why not replace the above two lines with ```

sudo umount /media/windowsdrive [color=red] && [/color] gksu "vmware -l -X -t /root/vmware/Windows\ XP\ Home\ Edition/Windows\ XP\ Home\ Edition.vmx"

```

In theory, the "&&" should hold off the next command until it gets a POSITIVE result from the previous command.

Note the "IN THEORY" disclaimer. Wish I could be more definite but am not willing to risk your data on my word.

---

### Post by jakornblum on 2008-04-03
Thanks for the help and the disclaimer.. I'm gonna hold off until someone confirms that this would work.. in that case, I would just link all the commands together using the && so that each line waits for the next:

```

sudo mount -t ntfs /dev/sdb1 /media/windowsdrive &&
sudo cp /media/windowsdrive/WINDOWS/system32/vmware/wpa.bak /media/windowsdrive/WINDOWS/system32/wpa.bak &&
sudo cp /media/windowsdrive/WINDOWS/system32/vmware/wpa.dbl /media/windowsdrive/WINDOWS/system32/wpa.dbl &&
sudo umount /media/windowsdrive &&

gksu "vmware -l -X -t /root/vmware/Windows\ XP\ Home\ Edition/Windows\ XP\ Home\ Edition.vmx"

```

You think this would work?  Would this make sure that each command holds off until the previous command finishes?  And what about the code underneath the vmware line?  Will this wait until vmware is closed before the commands run?

---

### Post by jakornblum on 2008-04-03
***post Deleted Due To Issue Being Resolved***

---

### Post by AniMo on 2008-07-07
Hello,

i have the exact same problem with virtualbox.
Does anybody know how to "adapt" this command for VB?
```
gksu "vmware -l -X -t /root/vmware/Windows\ XP\ Home\ Edition/Windows\ XP\ Home\ Edition.vmx"
```


thanks,

---

### Post by timmy334 on 2008-08-03
I'd like to do that as well. How do you do it for VirtualBox? :confused:

---

### Post by werries on 2008-09-02
yes, please, we need a virtualbox commaaaand.

---

### Post by Amael on 2009-01-18
Thank you for this script ! I adapted it to VirtualBox, and everything works nice.

Command to directly start a VirtualBox machine :
```
VBoxManage startvm "your_machine_name"
```

note that you DON'T have to start VBoxManage as root (sudo).

---

### Post by hejnal on 2009-02-24
Hello,

I have the problem using this script, I get 

/media/SYSTEM/WINDOWS/system32/wpa.bak': Input/output error

when I use the script. I remember that when I copied these files manually
at first, it worked without any problems.

Any ideas ??

---

### Post by wcasper4 on 2009-07-14
Does this work for SP3? Because I had tried altering these files in windows and created a startup script in windows based on [http://mazimi.wordpress.com/2007/07/11/getting-around-windows-activation-when-virtualizing/](http://mazimi.wordpress.com/2007/07/11/getting-around-windows-activation-when-virtualizing/) and [http://ubuntuforums.org/showpost.php?p=6259708&postcount=167](http://ubuntuforums.org/showpost.php?p=6259708&postcount=167) and it did not work. Any hope that this will?

---

### Post by wcasper4 on 2009-07-14
Also, I have XP professional.... how will this code differ?

---

