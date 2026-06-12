---
title: "Vmware Workstation 6 in Gutsy"
date: 2007-10-25
forum: Virtualisation
---

### Post by bensode on 2007-10-25
**(EDIT) : There seems to have been an update release of Vmware Workstation 6 that does not require the patch in the link below.  Since this update to Vmware, my system performance is back to normal and working like a dream.  Good to know that this was not an Ubuntu problem!**

I've done a fresh install of Gutsy (over my then working Fiesty) and installed Vmware Workstation 6 according to this thread:

[http://ubuntu-tutorials.com/2007/09/26/how-to-install-vmware-server-on-ubuntu-710/](http://ubuntu-tutorials.com/2007/09/26/how-to-install-vmware-server-on-ubuntu-710/)

I've noticed that performance within the vm has been greatly degraded and I can't explain why.  I've increased the amount of RAM that my XP vm uses from 512M to 1024M and there's a slight improvement but still overall very sluggish within the vm.

I run the same XP Pro SP2 vm on 7.04(and earlier) with 512M RAM and it runs perfectly.  I can't explain why this is happening but thought that I would bring this up in case someone might want to investigate this or have any insight.  Again it's only within the vm.

The only setup/config differences between 7.04 and 7.10 is that I am using the binary nVidia driver but I've also reverted back to the opensource nv driver with the same results.  The performance hit is only within the vm everything else is peachy,

My hardware hasn't changed and using the following:

Dell Precision M70 Centrino with 2G RAM
nVidia NV41 (Quadra FX Go1400 with Xinerama)
80G hd
External Dell 1907FP monitor


Software wise, other than the default installation of Ubuntu I'm using Crossover Linux 6.2, Vmware WS 6 and restricted audio codecs to play mp3/aac files with Rythmbox.

Bensode

---

### Post by jbardin on 2007-10-26
Hi,

I'm seeing the same issue with vmware server on gutsy.
Everything is as identical as possible from my ubuntu 7.04 install, and I did a clean install of 7.10.

I can't really pinpoint the problem, but both host and guest seem very sluggish.

I'm getting a LOT of clock sync requests in syslog if that's related.
/dev/vmmon[9933]: host clock rate change request 35 -> 0

-jim

---

### Post by bensode on 2007-10-30
Haven't seen any responses here or anywhere else and not having much luck on my own.  My next step is to remove the Workstation 6 installation and see what the performance looks like for the vmware-player that comes with Ubuntu 7.10.  If that works without a hitch, my guess is the custom patch to the vmware install is the issue and will wait for appropriate support to come from Ubuntu or Vmware directly.  I'll post again shortly ...

---

### Post by jbardin on 2007-10-30
I got a few replies from the vmware forums, but nothing really helpful. 

Others are having problems though. Vmware may have issues with the latest kernels, not necessarily just ubuntu.

---

### Post by gb64 on 2007-10-30
Wonder if someone installing the latest free VMware server could report in this thread whether they are also having slower responses. I installed the server in a testbed VM  with no problems. I am planning to actually re-install later on an actual drive, thus converting over to a full Ubuntu install, rather than continue testing within limited VMs under XP.
It would be nice to have this information prior to making that switch.

---

### Post by n01mower on 2007-10-30
Good day all, i am brand new to vmware workstation and Ubunto as of today. i have xp and installed vmware workstion. 
I have been trying to install ubuntu and have had no luck. I verified that the cd is correct I can see all the files on the disk and it comes up at boot.
when the vmware starts up I can see options to start or install and several other options. when i click in the vmwindow i can high light an options and hit enter but the install does not start. The cd rom is the 1st in line to boot.  i could use some hints if you have some. 
clean install of xp. fresh install of vm. any help would be great. 
thanks

---

### Post by jbardin on 2007-10-31
n01mower,

The problems that started this thread were for vmware running with ubuntu as the host os. It doesn't sound like an ubuntu problem if you haven't gotten the installer to boot yet.

Installs tend to work better if you point the vmware cdrom drive at the iso image. Maybe vmware is having trouble accessing the hardware cdrom drive?? I'm not sure otherwise.


gb64,

The problems I'm seeing are using the latest vmware server.

---

### Post by timcredible on 2007-10-31
i have gutsy installed, nvidia proprietary driver installed, and installed vmplayer to run an XP image created by vmware converter, and it runs the same as it did when the machine had feisty.  i don't have vmware server, just player.  i had to reduce the amount of memory in the .vmx file from 1536MB to 512MB (the PC only has 1GB), because if I didn't, it constantly tried to use swap space as memory.  But that was the only setting I had to change.

---

### Post by jbardin on 2007-10-31
bensode,

I tried re-configuring vmware server gain, and this time it couldn't build the modules. I used this patch (unsupported by vmware, but I found it linked from their KB)
[http://knihovny.cvut.cz/ftp/pub/vmware/vmware-any-any-update114.tar.gz](http://knihovny.cvut.cz/ftp/pub/vmware/vmware-any-any-update114.tar.gz)

After building the modules again, the system seem to be running better. I'm not sure if it's as good as it was previously, but I don't notice the host bogging down anymore.

---

### Post by johnchud on 2007-11-02
i also run vmworkstaion in feisty with no dramas then did the upgrade to gutsy 
it is the kernel that broke vm so unistalled and did a clean install of vmworkstation
after adding the vmnet file from the anyany release to it before installing
everything was sweet ran as before no degredation xp with 512ram

now i have added the studioubuntu and this has caused more problems vm installs but cant config its looking for a kernel that isnt on this computer

and vmplayer isnt supported by gutsy (i386)

---

### Post by bensode on 2007-11-12
> **n01mower said:**
> Good day all, i am brand new to vmware workstation and Ubunto as of today. i have xp and installed vmware workstion. 
I have been trying to install ubuntu and have had no luck. I verified that the cd is correct I can see all the files on the disk and it comes up at boot.
when the vmware starts up I can see options to start or install and several other options. when i click in the vmwindow i can high light an options and hit enter but the install does not start. The cd rom is the 1st in line to boot.  i could use some hints if you have some. 
clean install of xp. fresh install of vm. any help would be great. 
thanks

I haven't worked with the Windows version of vmware but you can try this as an option.  When you create the initial VM edit the cdrom drive to use an iso image file in place of the physical cd drive.  In order for this to work, though, you will need to make your XP setup disk an iso image.  I found this to be much more reliable and incredibly faster, too.

---

### Post by bensode on 2007-11-12
> **jbardin said:**
> bensode,

I tried re-configuring vmware server gain, and this time it couldn't build the modules. I used this patch (unsupported by vmware, but I found it linked from their KB)
[http://knihovny.cvut.cz/ftp/pub/vmware/vmware-any-any-update114.tar.gz](http://knihovny.cvut.cz/ftp/pub/vmware/vmware-any-any-update114.tar.gz)

After building the modules again, the system seem to be running better. I'm not sure if it's as good as it was previously, but I don't notice the host bogging down anymore.

Yep I use the vmanywhere unsupported patch running as well that seemed to do the trick for the installation.  I tried tweaking settings a bit within the vm and in the configuration of the vm that seemed to make minor improvements but it just didn't "feel" right.  I could have lived with that as I don't rely heavily on the vm I use cxoffice locally for all my MS apps anyway.

After reading around that several people had similar problems I just reverted back to 7.04 until Vmware can address the issues with the kernel and there are binaries in the 7.10 repositories.

---

### Post by lptr on 2007-11-12
Upgraded from Feisty to Gutsy, too. Reinstalled VMworkstation newly. I admit I did not too much with Feisty before, so I cannot directly compare regarding efficiency. Having several XP installations and one Vista. Seems to work as far as I can see. 

Even though I recognized some problems with external USB drives. Under some conditions that making heavy usage of this external devices, USB connection sometimes fails during access. I could not find out the closer conditions, yet.

Another point (sorry for somewhat OT here, but all experts seem to be here ;-) ) is that I cannot get ordinary other USB devices like webcams or iPod or such stuff, that are not directly supported by Gutsy to get recognized inside the VMs. Maybe anyone could point me to that, what I'm doing wrong, here - or even if it isn't possible at all?

rob*

---

### Post by jbardin on 2007-11-13
> I cannot get ordinary other USB devices like webcams or iPod or such stuff, that are not directly supported by Gutsy to get recognized inside the VMs. Maybe anyone could point me to that, what I'm doing wrong, here - or even if it isn't possible at all?

rob*

With this type of virtualization, the guest doesn't have direct access to the hardware. If the host doesn't support the device, the guest won't be able to get at it. 

-jim

---

### Post by jcottier on 2007-11-26
vmware will support any USB device, regardless of whether Linux supports it. Thats why its so excellent! However on Gutsy they have made a change to the USB system that requires a tweak to make it compatible with vmware again which still uses the 'now out of date' system:-

Please open the following file: /etc/init.d/mountdevsubfs.sh by following command - gksudo gedit /etc/init.d/mountdevsubfs.sh

Find the following lines:
#mkdir -p /dev/bus/usb/.usbfs
#domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
#ln -s .usbfs/devices /dev/bus/usb/devices
#mount --rbind /dev/bus/usb /proc/bus/usb


Unmark them so that look like this:
mkdir -p /dev/bus/usb/.usbfs
domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
ln -s .usbfs/devices /dev/bus/usb/devices
mount --rbind /dev/bus/usb /proc/bus/usb


Restart and your usb devices will be recognised

This is related to Bug #151585 and affects other VM's too.

---

### Post by lptr on 2007-11-26
@[jcottier]("http://ubuntuforums.org/member.php?u=382231"):
Thanks for information.
Do you know when vmware will change things to use the non outdated way of detecting/using USB devices? Or is there no known alternative, yet. Do you have some more details for us - especially why in Gutsy things have changed?

Does this break anything in Gutsy - or more specific: Are there any known side effects?

rob*

---

### Post by dpj23 on 2007-11-26
I have noticed the differences... I have one laptop running 7.04 and one running 7.10 both with workstation 6 installed on each of them... 

So, since I spend most of my time with a virtual machine running it was clear that adjustments had to made...

So, I reduced the visual effects to none... While this may only be one solution it solved my performance issues...  

I hope this helps...

---

### Post by dpj23 on 2007-11-26
With the upgrade you may need to re-configure the workstation using this command with escalated privileges...


vmware-config.pl.

---

### Post by 11hjpphty76lkjj on 2007-11-26
Not to change the subject per se, but you may want to check out VirtualBox.

[http://www.virtualbox.org/](http://www.virtualbox.org/)

It's an open source solution to the virtual machine. and works great.

A

---

### Post by serhito on 2007-11-26
Nobody laughs, but i installed VMware on Ubuntu 7.10, but how do I start VMware ?
A tutorial mentionned that it would be in Applications/System Tools/
but there's nothing there, only VirtualBox,
Also, can you have both VMware and VirtualBox installed at the same time ?

Thanks

---

### Post by lptr on 2007-11-27
Did what jcottier suggested. Editing in file 
```
/etc/init.d/mountdevsubfs.sh
```following lines (removing remarks #):
```
#mkdir -p /dev/bus/usb/.usbfs
#domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
#ln -s .usbfs/devices /dev/bus/usb/devices
#mount --rbind /dev/bus/usb /proc/bus/usb
```solved the problem.

No vmware workstation configuration change  was necessary. Simple reboot and iPod was detected as USB device. This afternoon I will continue testing. I hope that more important devices like our scanner (Canon) will be supported, too.

I appreciated your help. Many thanks again.

rob*

---

### Post by johnin on 2007-11-27
The high cpu usage on the host and the guest is because of the new kernel 2.6.22-14 that comes with Gutsy Gibon. Tried loads of stuff. Nothing helped. So I compiled kernel version 2.6.20-16. Installed workstation. Host and cpu usage are normal and Gutsy Gibon simply rocks!!!

---

### Post by jcottier on 2007-11-27
You need to run sudo vmware-config.pl and usually accept all the default answers. But I would recommend you read the relevant bits of the manual as you may want a different network connection type. Its gives good instructions for Linux install and running. After that you just run "vmware" for workstation. But if you have upgraded to Gutsy then vmware needs to be rebuilt for you current kernel. Uninstall the old version, download the latest version from vmware and run their script.You will need the build-essential meta package so that you have all the kernel headers, compilers and stuff the script needs.

---

### Post by jcottier on 2007-11-27
rob* I only know this stuff because I use vmware at work a lot. Apparently they now use /proc/bus/usb instead of /dev/bus/usb for some reason, I think it was better permission control and security. I was bit annoyed I had to trawl though so many formums/bugs to find this. Its been on the cards for over a year apparently, so vmware etc are blamed, but its you and I that have to suffer! Shame it was not in the Gutsy release notes. Anyway vmware 5 had 2  USB 1.1 ports, vmware 6 has these and also 6 USB 2 ports and is compatible with streaming devices. Some older devices may need a bit of extra stuff on the vmx file (a sort of hardware script) but I only had to do this once on vmware 5 for an old ebookman (its all in the vmware manual. Just search for it in the pdf). Everything  else just works out the box, or at least as well as it does in native windows anyway ;-)

---

### Post by lptr on 2007-11-27
jcottier: Thanks for your infos.

Like others I also recognized a high system load. 

```
root@kulix:~# top
top - 14:19:32 up  5:23,  1 user,  load average: 1.14, 0.49, 0.20
Tasks: 138 total,   3 running, 134 sleeping,   0 stopped,   1 zombie
Cpu(s):  2.5%us, 12.9%sy,  0.0%ni, 84.2%id,  0.0%wa,  0.2%hi,  0.2%si,  0.0%st
Mem:   3107664k total,  2980448k used,   127216k free,    77520k buffers
Swap:  4996172k total,    19012k used,  4977160k free,  2529068k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 8604 roberts    5 -10 1705m 858m 847m S   26 28.3   1:00.24 vmware-vmx
 7229 roberts   15   0 34264  16m  12m S    4  0.5   0:00.69 konsole
```One member here downgraded to Kernel 2.6.20. This seemed to solve that peak load symptom. Is there anybody here, knowing if kernel guys/vmware are already working to find a solution for current load problems ? 

rob*

---

### Post by bensode on 2007-11-29
> **dpj23 said:**
> I have noticed the differences... I have one laptop running 7.04 and one running 7.10 both with workstation 6 installed on each of them... 

So, since I spend most of my time with a virtual machine running it was clear that adjustments had to made...

So, I reduced the visual effects to none... While this may only be one solution it solved my performance issues...  

I hope this helps...

You know as stupid as this may sound ... I didn't even think to check those settings.  I've just installed 7.10 on my new laptop because 7.04 won't even boot to it but that's another story.  I've just found that pesky Vista-esque "feature" that adds glitz and other crap to the UI so I'm going to re-attempt with Vmware 6 today.  

/shakes fist at f-tard that added cludge to default desktop

---

