---
title: "Nvidia Driver Problems"
date: 2011-02-28
forum: Ubuntu Studio
---

### Post by Precipitous on 2011-02-28
I am running UbuntuStudo 10.10 and have an Nvidia Geforce 7300 LE video card. Every time there is an update to either the kernel, or the Nvidia  Current driver, I get a black screen and log-in prompt when I reboot,  unless I boot into an older kernel. This hasn't been too much trouble  until the last couple of updates. Now the only way I am able to boot  into a working desktop is to install and run the Nvidia driver release 260.19.36 from the Nvidia website, and to boot into kernel 2.6.35.25. None of the other kernels will work, including the real time kernel I use for music production!

I desperately need to be able to use either the low latency or real time  kernels, but am now unable to do so. In the past I have had to patch the  video driver before being able to do so, but now I am unable to do that  either. I am assuming because of the driver being downloaded from Nvidia instead of from one of the repositories?

Surely there has to be an easy way to resolve these issues, but I haven't been able to figure it out...  Does anybody have any  suggestions? If not, what would be the best inexpensive video card to purchase?

---

### Post by cchhrriiss121212 on 2011-02-28
> Does anybody have any  suggestions?
Basically: try more kernels until you find one that works with the non-free drivers. Or switch to the open source drivers. 

I'm not sure if you know this or not but just in case:
After installing an nvidia driver manually, you will need to install it again for the new kernel, which you should be able to do from the CLI prompt. Installing the driver for one kernel will overwrite the profile for the older one.

Some rt kernels are released without being compatible with nvidia drivers, which was a major reason why I don't use them any more. Alessio's low latency ones were nvidia friendly the last time I tried one:
[https://launchpad.net/~abogani/+archive/ppa]("https://launchpad.net/%7Eabogani/+archive/ppa")

Whatever you decide, buying a new video card won't be necessary.

---

### Post by Precipitous on 2011-02-28
> **cchhrriiss121212 said:**
> Basically: try more kernels until you find one that works with the non-free drivers. Or switch to the open source drivers. 

I'm not sure if you know this or not but just in case:
After installing an nvidia driver manually, you will need to install it again for the new kernel, which you should be able to do from the CLI prompt. Installing the driver for one kernel will overwrite the profile for the older one.

Some rt kernels are released without being compatible with nvidia drivers, which was a major reason why I don't use them any more. Alessio's low latency ones were nvidia friendly the last time I tried one:
[https://launchpad.net/~abogani/+archive/ppa]("https://launchpad.net/%7Eabogani/+archive/ppa")

Whatever you decide, buying a new video card won't be necessary.
Thank you for the information. One quick question: Which open source driver are you referring to? Do you mean Nvidia Current from the X-Swat ppa?

Last time I tried to use any of the low latency kernels I was never able to get any of them to work properly with the Nvidia drivers. That was a while back, though, so I will try again. 

In the past I had the best luck with the 2.6.33-29.1 real time kernel. I had to patch the video driver first, but it wasn't too much of a hassle. Unfortunately, that hasn't worked for some time...

---

### Post by cchhrriiss121212 on 2011-02-28
> One quick question: Which open source driver are you referring to? Do you mean Nvidia Current from the X-Swat ppa?
I refer to nouveau, which is installed by default with Ubuntu:
[http://nouveau.freedesktop.org/wiki/]("http://nouveau.freedesktop.org/wiki/")
When you install the non free drivers, it is removed. It is OK for general usage but has no 3d support.

I never got around to patching any of the rt kernels, it is more involved than I would like to get with my OS. I switched to liquorix, which works great for audio and nvidia drivers. A few other users on here report good results with it too, worth a look if the low latency fails you.
Info here:
[http://ubuntuforums.org/showthread.php?t=1588760]("http://ubuntuforums.org/showthread.php?t=1588760")

---

### Post by Precipitous on 2011-02-28
> **cchhrriiss121212 said:**
> I refer to nouveau, which is installed by default with Ubuntu:
[http://nouveau.freedesktop.org/wiki/](http://nouveau.freedesktop.org/wiki/)
When you install the non free drivers, it is removed. It is OK for general usage but has no 3d support.

I never got around to patching any of the rt kernels, it is more involved than I would like to get with my OS. I switched to liquorix, which works great for audio and nvidia drivers. A few other users on here report good results with it too, worth a look if the low latency fails you.
Info here:
[http://ubuntuforums.org/showthread.php?t=1588760](http://ubuntuforums.org/showthread.php?t=1588760)
Thank you for the incredible liquorix information. I was not aware of its existence....  You can bet the first thing I will do when I get home from work today will be to try out the pae version from bandshed ([2.6.36-3.dmz.2-PAE]("http://bandshed.net/kernels/2.6.36-3.dmz.2-PAE.zip"))!

I will post the results...

---

### Post by Precipitous on 2011-03-01
I installed Liquorix successfully ([2.6.36-3.dmz.2-PAE]("http://bandshed.net/kernels/2.6.36-3.dmz.2-PAE.zip")), but I am not able to boot into it. I have tried three different video drivers - 260.19.36, 270.28 and 270.29 (all from the Nvidia website), but I only get a black screen with a text log-in prompt... Back to square one.

Does anybody know what video driver will work?

---

### Post by cchhrriiss121212 on 2011-03-01
What steps are you using to install the driver? Here is what I recommend:
sudo service gdm stop
cd yourdriverlocation
sudo ./yourdriver
sudo service gdm start

---

### Post by Precipitous on 2011-03-01
> **cchhrriiss121212 said:**
> What steps are you using to install the driver? Here is what I recommend:
sudo service gdm stop
cd yourdriverlocation
sudo ./yourdriver
sudo service gdm start
To install the driver I have normally rebooted the computer to a command prompt instead of a desktop. I then cd to the driver location, then sudo ./driver, then reboot. This essentially does the same thing as you are suggesting (or at least I think)... I will try it your way anyway and see what happens... Thanks for the advice.

---

### Post by Precipitous on 2011-03-02
> **Precipitous said:**
> To install the driver I have normally rebooted the computer to a command prompt instead of a desktop. I then cd to the driver location, then sudo ./driver, then reboot. This essentially does the same thing as you are suggesting (or at least I think)... I will try it your way anyway and see what happens... Thanks for the advice.
I was able to get booted into the Liquorix kernel by installing the Nvidia driver using your instructions. Unfortunately, if I reboot I end up with a black screen and text login prompt like before...  If I re-install the driver I am able to get back into the kernel, etc......  It is a hassle, but it is well worth it, as that the Liquorix kernel works wonderfully. I tried doing some really intense audio tasks through Jack and did not receive one X-Run!!! This is what I have been hoping for!

Now, if someone could help figure out why I have to re-install the Nvidia driver every time I reboot I would be a really happy camper....

---

### Post by cchhrriiss121212 on 2011-03-02
Are you sure you are booting into liquorix each time? (if you want to set this kernel as default, try using a program called startup manager)
Did you get any messages during the driver installation?
Did you agree to all the modifications the installer suggests?

---

### Post by Precipitous on 2011-03-02
> **cchhrriiss121212 said:**
> Are you sure you are booting into liquorix each time? (if you want to set this kernel as default, try using a program called startup manager)
Did you get any messages during the driver installation?
Did you agree to all the modifications the installer suggests?
cchhrriiss121212: Thanks for your continued assistance...

Yes -  I am booting into Liquorix each time.
No -  There were no error messages during driver install.
Yes - I agreed to all driver install defaults.

I am a software tech for a living and feel very competent in my skills, but this one has me really thrown. It is way outside of my comfort zone, so any additional help I can get (from anyone) is greatly appreciated!

---

### Post by cchhrriiss121212 on 2011-03-02
Found an older thread with similar problem:
[http://ubuntuforums.org/showthread.php?t=1565176](http://ubuntuforums.org/showthread.php?t=1565176)

You may need to do the blacklisting of other modules, or perhaps a simple:
```
sudo nvidia-xconfig
```
would fix it.

---

### Post by Precipitous on 2011-03-02
> **cchhrriiss121212 said:**
> Found an older thread with similar problem:
[http://ubuntuforums.org/showthread.php?t=1565176](http://ubuntuforums.org/showthread.php?t=1565176)

You may need to do the blacklisting of other modules, or perhaps a simple:
```
sudo nvidia-xconfig
```would fix it.
cchhrriiss121212: Thanks for the link to the older thread. It contains a LOT of really good information. I don't know how I missed it when I searched the forums earlier....

I will give your suggestions a go as soon as I get home from work (unfortunately, that will be several hours from now)...

Thanks again for all of your help!

---

### Post by cchhrriiss121212 on 2011-03-02
> I don't know how I missed it when I searched the forums earlier....
Yeah, the search feature on the forum is pretty weak. I always go through google like this:
ubuntu 7300 LE
Plus, no time limit on repeated searches.

---

### Post by Precipitous on 2011-03-03
cchhrriiss121212:

Success!!  Thank you for all of your help!

Just in case anyone has this same problem in the future, here are the steps I went through to resolve it:


[LIST=1]
[*]Download the latest driver from [http://www.nvidia.com/content/global/global.php](http://www.nvidia.com/content/global/global.php)
[*]Open module blacklist as admin:
```
sudo gedit /etc/modprobe.d/blacklist.conf
```
[*]Add the following lines, then save:

blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv
[*]Uninstall any previously installed Nvidia drivers
```
sudo apt-get --purge remove nvidia-*
```
[*]Reboot the computer (should boot to a black screen with a command window style text log in prompt)
[*]Log in as per normal
[*]Install the driver
```
sudo service gdm stop
cd (directory the driver was downloaded to in Step1)
sudo sh NVIDIA-Linux-x86-260.19.36.run   (substitute your driver version)
sudo service gdm start
```
[*]Log in to desktop
[*]When desktop has loaded re-configure X
```
sudo nvidia-xconfig
```
[/LIST]

---

