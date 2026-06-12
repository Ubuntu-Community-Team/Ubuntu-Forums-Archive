---
title: "vmware server doesn't start virtual machine"
date: 2008-02-27
forum: Virtualisation
---

### Post by monkman on 2008-02-27
hello.
ubuntu 7.10
vmware 1.0.4 build-56528

I would like to use a Windows 2000 Professional in ubuntu via vmware server, but it doenst start the virtualmache up. i created an iso-file with k3b which is selcted in this machine. but the only thing i get is a black screen. so i even don't get to install win2000.

what can i do about it? i've reinstalled vmware server but it didn't solve this issue.

thank you!

---

### Post by blink0072005 on 2008-03-06
I have what seems to be a very similar problem.

I've installed the newest version VMware Server from the repository with no problems, and also created a Windows XP Professional virtual machine quite easily; it's even created it's own 10gb disk space already.  I have the CD-ROM drive mapping to an XP Pro .iso that I made from the CD (I'm dual booting with XP Professional, but left my CD at the dorm).  When I hit "Power On", it goes to a black screen just like the screenshot from the poster above me, and then backs out.  The buttons become enabled for about two seconds, but if I try to press "Suspend" I get this error:

"Unable to change virtual machine power state: Pipe: Read failed."

The only thing that happens when I turn debugging information is that on the very bottom screen it says "You do not have VMware Tools installed", but I can't install that because the VM does not stay loaded long enough.  If I try to hit it very quickly it says:

"Error toggling VMware Tools Install: Pipe: Read failed."

Does anyone know what's wrong?  I am relatively new with Ubuntu Gutsy (about 3 weeks in), but really like it so far.  Any suggestions would be greatly appreciated.

---

### Post by monkman on 2008-03-06
i figured out that the iso files i made with linux are not liked by vmware...

---

### Post by blink0072005 on 2008-03-06
So does yours work now that you use an actual CD?  I also made a copy of my CD with Linux, so the .iso could be a problem.  It will take me a couple of days to get a real CD, but I can try that if you had positive results.

---

### Post by blink0072005 on 2008-03-06
Ok, so I found the reason (mine anyway) on the forums.  I was trying to run VMware off my external hard drive, but apparently VMware won't run correctly off anything in NTFS format.  However, there's a workaround:  open the .vmx in a text editor and add this line:

mainMem.useNamedFile="FALSE"

After I did this, my virtual machine booted off the .iso (I'm currently installing as I type this). 

Source:
[http://ubuntuforums.org/showthread.php?t=684615](http://ubuntuforums.org/showthread.php?t=684615)

---

### Post by monkman on 2008-03-06
you're right. i mixed something up. that was the reason here too... i tried the vm on a ntfs system...   great you solved it, i then installed my vm on a vfat partition...

---

