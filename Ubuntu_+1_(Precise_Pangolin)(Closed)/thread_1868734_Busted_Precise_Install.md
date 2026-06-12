---
title: "Busted Precise Install ?"
date: 2011-10-24
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by ventrical on 2011-10-24
I think my install of Precise is busted. I cannot post any screenshots because all of a sudden I am getting the Black Screenshots of Death every time I try to take a screenshot. I did the larger updates today and all went well. Then, I was trying to  replicate a problem reported about UM and synpatic and everything went south !

 The only thing I notice is that the Ubuntuone Syncdaemon in System manager is using about 41MB of memeory .. thats a lot of memory for a program I don't use - or am I missing somthing here.

Any idea on how to get a quick fix of my install of Precise?

(I tried to fall back to a different kernel version and no luck.)

---

### Post by paul_in_london on 2011-10-24
@ventrical: gnome-screenshot has been broken for me for a while (before I upgraded to precise), but shutter works ok.

Are you having other issues apart from that?

---

### Post by ventrical on 2011-10-24
Yes, both CPUs are running at 100% and my processor is reporting 65C.   I was running comfortable at 380MB ddr and then it jumped up about 200MB. 

Screenshot was working just fine , excellent. There were some compiz updates also. i am wondering if somthing is really wrong with ccsm and the compiz core. Unity is working fine, but when I try to get some work done, things just slow down, high CPU usage and then crash/bang !

 So I just hard boot then.

But that does not good because problem persists.  I did update either lastnight or today. There was a rarther large update.

---

### Post by paul_in_london on 2011-10-24
Hmm. I use Gnome Shell instead of Unity and when I was running htop earlier today I noticed that with kernel 3.1.0-1 one of my two CPU cores was spiking at 100% so I tried today's 3.1.0-999 daily and the problem seemed to go away. Apart from that, everything seems ok.

---

### Post by Harry33 on 2011-10-25
There is another thread with kernel 3.1 issues with latest Compiz.
[http://ubuntuforums.org/showthread.php?t=1868610](http://ubuntuforums.org/showthread.php?t=1868610)

I have also found something odd about the latest PP kernel 3.1 rc 10 (regarding Adobe flash-plugin)
However, I am using Gnome-shell (Ricotz Staging PPA) and Nvidia-current 290.03 plus Xserver 1.11.1 (Xorg-edgers).

---

### Post by ventrical on 2011-10-25
> **Harry33 said:**
> There is another thread with kernel 3.1 issues with latest Compiz.
[http://ubuntuforums.org/showthread.php?t=1868610](http://ubuntuforums.org/showthread.php?t=1868610)

I have also found something odd about the latest PP kernel 3.1 rc 10 (regarding Adobe flash-plugin)
However, I am using Gnome-shell (Ricotz Staging PPA) and Nvidia-current 290.03 plus Xserver 1.11.1 (Xorg-edgers).


Thanks harry33. That  is my next move. To remove adobe-flash-plugin (if I can). I think that is what it is because I have been having probs with some video. I removed ccsm and gnome-shell , but to no avail. I rolled back to 3.0.0-12, 3.0.0-11, but to no avail. The most info I get is that <gnome-terminal> is running at 100% of cpu.

I'm using nvidia current 280.13 and have no probs with it on other installs.

---

### Post by ventrical on 2011-10-25
The two other packages installed but nit the first. I did it all in order as suggested.

dale@ubuntu:~/Downloads$ sudo dpkg -i linux-headers-3.1.0-030100-generic_3.1.0-030100.201110241006_i386.deb
[sudo] password for dale: 
Selecting previously unselected package linux-headers-3.1.0-030100-generic.
(Reading database ... 265531 files and directories currently installed.)
Unpacking linux-headers-3.1.0-030100-generic (from linux-headers-3.1.0-030100-generic_3.1.0-030100.201110241006_i386.deb) ...
dpkg: dependency problems prevent configuration of linux-headers-3.1.0-030100-generic:
 linux-headers-3.1.0-030100-generic depends on linux-headers-3.1.0-030100; however:
  Package linux-headers-3.1.0-030100 is not installed.
dpkg: error processing linux-headers-3.1.0-030100-generic (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-headers-3.1.0-030100-generic

---

### Post by ricotz on 2011-10-25
> **ventrical said:**
> Thanks harry33. That  is my next move. To remove adobe-flash-plugin (if I can). I think that is what it is because I have been having probs with some video. I removed ccsm and gnome-shell , but to no avail. I rolled back to 3.0.0-12, 3.0.0-11, but to no avail. The most info I get is that <gnome-terminal> is running at 100% of cpu.

I'm using nvidia current 280.13 and have no probs with it on other installs.

If you are using the cairo 1.11.3+ packages (from ppa:ricotz/staging) you need to make sure to use nvidia-current >= 285.05.09. The cairo packages are compile with enabled GL backend which causes problems with older nvidia drivers.

---

### Post by effenberg0x0 on 2011-10-25
If your have all your cores at 100% but cannot identify a clear culprit using top/htop, couldn't it be that your CPU is being wrongly recognized at a lower frequency and/or stuck at a performance governor? That is something that could be related to a kernel issue. EX: powernow-k8, that is builtin in kernel for AMD CPUs can't actually recognize the correct speeds of my CPU (but it underclocks it), and so cpufreq must me manually set. I also had to manually change /etc/init.d/ondemand to fix the steps of my cpu, otherwise, even on "ondemand" governor, it would not scale down. But in my case it's something that kernel developers are working on for a while, a known behavior. I helped a guy here once that had one core of its dual core cpu stuck at max_speed an the other one scaling normally so...better have a look at some info like this:

```
dmesg | grep -i processor
sudo cat /proc/cpuinfo
sudo cat /sys/devices/system/cpu/cpu{0..5}/cpufreq/bios_limit

sudo cat /sys/devices/system/cpu/cpu{0..5}/cpufreq/cpuinfo_min_freq
sudo cat /sys/devices/system/cpu/cpu{0..5}/cpufreq/cpuinfo_cur_freq
sudo cat /sys/devices/system/cpu/cpu{0..5}/cpufreq/cpuinfo_max_freq

sudo cat /sys/devices/system/cpu/cpu{0..5}/cpufreq/scaling_available_frequencies
sudo cat /sys/devices/system/cpu/cpu{0..5}/cpufreq/scaling_min_freq
sudo cat /sys/devices/system/cpu/cpu{0..5}/cpufreq/scaling_cur_freq
sudo cat /sys/devices/system/cpu/cpu{0..5}/cpufreq/scaling_max_freq

sudo cat /sys/devices/system/cpu/cpu{0..5}/cpufreq/scaling_available_governors
sudo cat /sys/devices/system/cpu/cpu{0..5}/cpufreq/scaling_governor

cpufreq-info


```PS: I just used bash expansion for 6-core because I don't know what your CPU is and was too lazy to create a if condition script :)

---

### Post by Harry33 on 2011-10-25
> **ventrical said:**
> The two other packages installed but nit the first. I did it all in order as suggested.

dale@ubuntu:~/Downloads$ sudo dpkg -i linux-headers-3.1.0-030100-generic_3.1.0-030100.201110241006_i386.deb
[sudo] password for dale: 
Selecting previously unselected package linux-headers-3.1.0-030100-generic.
(Reading database ... 265531 files and directories currently installed.)
Unpacking linux-headers-3.1.0-030100-generic (from linux-headers-3.1.0-030100-generic_3.1.0-030100.201110241006_i386.deb) ...
dpkg: dependency problems prevent configuration of linux-headers-3.1.0-030100-generic:
 linux-headers-3.1.0-030100-generic depends on linux-headers-3.1.0-030100; however:
  Package linux-headers-3.1.0-030100 is not installed.
dpkg: error processing linux-headers-3.1.0-030100-generic (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-headers-3.1.0-030100-generic

So you need to install linux-headers-3.1.0-030100_3.1.0-030100.201110241006_all.deb first.

For a kernel installation these must be installed (32-bit) and in that order:
linux-headers-x.x.x-x_x.x.x-x_all.deb
linux-headers-x.x.x-x-generic_x.x.x-x_i386.deb
linux-image-x.x.x-x-generic_x.x.x-x_i386.deb

---

### Post by ventrical on 2011-10-25
> **ricotz said:**
> If you are using the cairo 1.11.3+ packages (from ppa:ricotz/staging) you need to make sure to use nvidia-current >= 285.05.09. The cairo packages are compile with enabled GL backend which causes problems with older nvidia drivers.


Yes I am using the Cairo ppas. I uninstalled (nvidia-current-updates) and installed (nvidia-current) and I get this svreenshot:

*note* I am able to log on to Gnome_Classic with no problem with the Precise kernel.


----nope .. sorry .. I am still getting the Black Sceenshot of Death, Can' t take screenshots.

However.. when I use the Nvidia Settings tool it says:


You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server


??

---

### Post by ventrical on 2011-10-25
> **Harry33 said:**
> So you need to install linux-headers-3.1.0-030100_3.1.0-030100.201110241006_all.deb first.

For a kernel installation these must be installed (32-bit) and in that order:
linux-headers-x.x.x-x_x.x.x-x_all.deb
linux-headers-x.x.x-x-generic_x.x.x-x_i386.deb
linux-image-x.x.x-x-generic_x.x.x-x_i386.deb


Thanks Harry33. I'll do that shortly.

add-on = Done!

---

### Post by ventrical on 2011-10-25
> **effenberg0x0 said:**
> If your have all your cores at 100% but cannot identify a clear culprit using top/htop, couldn't it be that your CPU is being wrongly recognized at a lower frequency and/or stuck at a performance governor? That is something that could be related to a kernel issue. EX: powernow-k8, that is builtin in kernel for AMD CPUs can't actually recognize the correct speeds of my CPU (but it underclocks it), and so cpufreq must me manually set. I also had to manually change /etc/init.d/ondemand to fix the steps of my cpu, otherwise, even on "ondemand" governor, it would not scale down. But in my case it's something that kernel developers are working on for a while, a known behavior. I helped a guy here once that had one core of its dual core cpu stuck at max_speed an the other one scaling normally so...better have a look at some info like this:

```
dmesg | grep -i processor
sudo cat /proc/cpuinfo
sudo cat /sys/devices/system/cpu/cpu{0..5}/cpufreq/bios_limit

sudo cat /sys/devices/system/cpu/cpu{0..5}/cpufreq/cpuinfo_min_freq
sudo cat /sys/devices/system/cpu/cpu{0..5}/cpufreq/cpuinfo_cur_freq
sudo cat /sys/devices/system/cpu/cpu{0..5}/cpufreq/cpuinfo_max_freq

sudo cat /sys/devices/system/cpu/cpu{0..5}/cpufreq/scaling_available_frequencies
sudo cat /sys/devices/system/cpu/cpu{0..5}/cpufreq/scaling_min_freq
sudo cat /sys/devices/system/cpu/cpu{0..5}/cpufreq/scaling_cur_freq
sudo cat /sys/devices/system/cpu/cpu{0..5}/cpufreq/scaling_max_freq

sudo cat /sys/devices/system/cpu/cpu{0..5}/cpufreq/scaling_available_governors
sudo cat /sys/devices/system/cpu/cpu{0..5}/cpufreq/scaling_governor

cpufreq-info


```PS: I just used bash expansion for 6-core because I don't know what your CPU is and was too lazy to create a if condition script :)


Thats an Intel P4-2.66GHz dualcore.

  I'll retry to install the new kernel first.. also looks like I got a problem with NVIDIA driver also.

 I'll go a step at a time. thanks  for your help. I know you worked on this a while back for someone else.

---

### Post by ventrical on 2011-10-25
I got all the new kernel installed. Still, no go. It has to be Unity (I think). My CPU is working great on Gnome-Classic and I re-installed the NVIDIA driver - but unity, Unity 2d Desktop will just lock up... so I will remove Unity with synaptic and then reinstall it and see if this works.

Fun !:)

---

### Post by cariboo on 2011-10-25
This is a little drastic, but sometimes if you are desperate, you have to resort to desperate measures. Try removing ~/.config, and rebooting. You will of course lose all your settings, but if you want to get Precise going without doing a re-install, this might help.

---

### Post by ventrical on 2011-10-25
> **ricotz said:**
> If you are using the cairo 1.11.3+ packages (from ppa:ricotz/staging) you need to make sure to use nvidia-current >= 285.05.09. The cairo packages are compile with enabled GL backend which causes problems with older nvidia drivers.


How to I update to this?

 Thanks.

---

### Post by zika on 2011-10-25
> **cariboo907 said:**
> This is a little drastic, but sometimes if you are desperate, you have to resort to desperate measures. Try removing ~/.config, and rebooting. You will of course lose all your settings, but if you want to get Precise going without doing a re-install, this might help.Simple Move not REMove could do the trick... ;) After getting to a working Unity, what ever, sifting through this directory could save You all that is important...

---

### Post by effenberg0x0 on 2011-10-25
> **ventrical said:**
> Thats an Intel P4-2.66GHz dualcore.

  I'll retry to install the new kernel first.. also looks like I got a problem with NVIDIA driver also.

 I'll go a step at a time. thanks  for your help. I know you worked on this a while back for someone else.

I went back from nvidia proprietary 290.03 to 285.05.09 and noticed the GPU colder and smoother transition effects on screen (as well as some weird compiz/unityshell segfaults). In the first case, it was not like the GPU or it's mem was running overclocked, but 290.03 seems to be less conservative for scaling than 285.03: You move your mouse and the GPU goes 100% for a second and back. Maybe you can go down a couple versions, see if it helps. It helped me.

Just a thought: If you're installing / removing kernels, sometimes you don't actually have a nvidia problem. You just need to install the kernel module. dkms can and does fail sometimes. Just run the installer with option -K (--kernel-module-only) if it's the case.

---

### Post by ventrical on 2011-10-25
> **cariboo907 said:**
> This is a little drastic, but sometimes if you are desperate, you have to resort to desperate measures. Try removing ~/.config, and rebooting. You will of course lose all your settings, but if you want to get Precise going without doing a re-install, this might help.


Yeah ... thanks .... like where exactly do I find the (ffftt) file ~/.config  ??  :)

 and I'm not deperate .. :)

well.. yes I am desperate ... now , out of a gazillion config files  I have no idea which config file you are talking about ... 

thanks in advance

---

### Post by effenberg0x0 on 2011-10-25
/home/YourLogin/.config is a directory and inside it there are other files and directories.

Do something like mv ~/.config ~/.config.backup 
That way you can easily restore things if everything goes wild.

**EDIT**
> **ventrical said:**
> 
 and I'm not deperate .. :smile: well.. yes I am desperate ... 

Dude, don't take that bad, ok? When I get to situation like that, the first thing I do is step away from the keyboard, calm down, open a beer, light a cigarette, take a 10 minute walk around the block, talk to other people about stupid things, etc. When you clear your head, a simple solution comes. It generally is something stupid, most of the times. You've been here helping and reading about what other users were dealing with long enough. You probably know the answer... you're just not seeing it.

---

### Post by Harry33 on 2011-10-25
> **ventrical said:**
> How to I update to this?

 Thanks.

You can get both of those from Xorg-edgers PPA. I use all the time nvidia-current 290.03.
Nvidia-current 290.03 is the Oneiric branch of XE PPA.
Cairo 1.11.3+git is in both Oneiric and Precise branches of XE PPA.

I do not use that cairo version, however.
It pulls in libwayland0 too.

---

### Post by ventrical on 2011-10-25
> **effenberg0x0 said:**
> /home/YourLogin/.config is a directory and inside it there are other files and directories.

Do something like mv ~/.config ~/.config.backup 
That way you can easily restore things if everything goes wild.

**EDIT**


Dude, don't take that bad, ok? When I get to situation like that, the first thing I do is step away from the keyboard, calm down, open a beer, light a cigarette, take a 10 minute walk around the block, talk to other people about stupid things, etc. When you clear your head, a simple solution comes. It generally is something stupid, most of the times. You've been here helping and reading about what other users were dealing with long enough. You probably know the answer... you're just not seeing it.


Yes you are right dude.  I walked two miles then spent 3 hours  removing  malware and cleaning the registry  of a clients PC.3 and 1/2 hours on that.  I guess that cleaned my sinues out ::) Don't drink, don't smoke... but I love tearing PCs apart :)


 I'll take a break .. :) 

Here is what I get with that config file...
dale@dale:~$ ~/.config
bash: /home/dale/.config: Is a directory
dale@dale:~$ gedit /home/dale/.config
dale@dale:~$ cd home/dale/.config
bash: cd: home/dale/.config: No such file or directory
dale@dale:~$ cd home/dale/
bash: cd: home/dale/: No such file or directory
dale@dale:~$ cd /home/dale/
dale@dale:~$ gedit .config
dale@dale:~$ cd /.config
bash: cd: /.config: No such file or directory
dale@dale:~$

---

### Post by mc4man on 2011-10-25
You almost had it there -
cd .config

---

### Post by effenberg0x0 on 2011-10-25
> **ventrical said:**
> Yes you are right dude.  I walked two miles then spent 3 hours  removing  malware and cleaning the registry  of a clients PC.3 and 1/2 hours on that.  I guess that cleaned my sinues out ::) Don't drink, don't smoke... but I love tearing PCs apart :)


 I'll take a break .. :) 

Here is what I get with that config file...
dale@dale:~$ ~/.config
bash: /home/dale/.config: Is a directory
dale@dale:~$ gedit /home/dale/.config
dale@dale:~$ cd home/dale/.config
bash: cd: home/dale/.config: No such file or directory
dale@dale:~$ cd home/dale/
bash: cd: home/dale/: No such file or directory
dale@dale:~$ cd /home/dale/
dale@dale:~$ gedit .config
dale@dale:~$ cd /.config
bash: cd: /.config: No such file or directory
dale@dale:~$


You're tense :) Notice the mistakes you're making man. 

dale@dale:~$ ~/.config [COLOR=DarkRed]**(You can't execute a directory)**[/COLOR]
bash: /home/dale/.config: Is a directory 
dale@dale:~$ gedit /home/dale/.config **[COLOR=DarkRed](You can't edit a directory)[/COLOR]**
dale@dale:~$ cd home/dale/.config **[COLOR=DarkRed](Missed a slash before home)[/COLOR]**
bash: cd: home/dale/.config: No such file or directory **[COLOR=DarkRed](Missed a slash before home)[/COLOR]** 
dale@dale:~$ cd home/dale/ **[COLOR=DarkRed](Missed a slash before home)[/COLOR]**
bash: cd: home/dale/: No such file or directory **[COLOR=DarkRed](Missed a slash before home)[/COLOR]**
dale@dale:~$ cd /home/dale/ 
dale@dale:~$ gedit .config **[COLOR=DarkRed](You can't edit a directory)[/COLOR]**
dale@dale:~$ cd /.config **[COLOR=DarkRed](.config is not in root)[/COLOR]**
bash: cd: /.config: No such file or directory **[COLOR=DarkRed](.config is not in root)[/COLOR]** 

 Just do it like this:

```

cd
pwd (it will tell you that you are at /home/dale - just to check if you're not logged in as other user)
mv .config .config.backup

```Regards,
Effenberg


**EDIT: **Better yet, run **cd && ls -lhag .*** in your home. You're failing to comprehend and explore "hidden" directories (that start with a dot in name). Once you explore them, you'll understand.

---

### Post by ventrical on 2011-10-26
I will try that mv command.

 I was able to finally extract a screenshot by downloading the program *shutter*. I highlighted an area where there are some profiles I had exported in the compiz preferences (during beta testing) .. and I am just wondering what they may be doing there.

thanks

---

### Post by ventrical on 2011-10-26
> **mc4man said:**
> You almost had it there -
cd .config

ehehe... certainly not dos is it ?  :)

I finally moved that file.  It burped , then , went right back to lock-ups freezes and kernel panics it appears. It has to be Unity or Compiz core (that last update really did  Precise in) because I can use the Desktop Manager FVWM-Crystal with no problems.

  So my other options are to install the other NVIDIA driver (I installed the xorg-edgers ppa but have no idea where to download the NVIDIA driver) and re-install unity.

 So anyone have any tips on how to purge unity ? :)

---

### Post by Harry33 on 2011-10-26
> **ventrical said:**
> ehehe... certainly not dos is it ?  :)

I finally moved that file.  It burped , then , went right back to lock-ups freezes and kernel panics it appears. It has to be Unity or Compiz core (that last update really did  Precise in) because I can use the Desktop Manager FVWM-Crystal with no problems.

  So my other options are to install the other NVIDIA driver (I installed the xorg-edgers ppa but have no idea where to download the NVIDIA driver) and re-install unity.

 So anyone have any tips on how to purge unity ? :)

Removing Unity:
- remove all unity packages except libunity6 (search with Synaptic)
- remove all nux packages (search with Synaptic)
- after that install deborpan and run it from terminal (sudo) and it shows the orphaned packages that can be removed.

Nvidia-current 290.03:
From Xorg-edgers - look for Oneiric branch: nvidia-graphics-drivers
[https://launchpad.net/~xorg-edgers/+archive/ppa/+packages?field.name_filter=&field.status_filter=published&field.series_filter=oneiric]("https://launchpad.net/%7Exorg-edgers/+archive/ppa/+packages?field.name_filter=&field.status_filter=published&field.series_filter=oneiric")

Install (correct architecture):
- nvidia-current_290.03
- nvidia-settings_290.03

---

### Post by ventrical on 2011-10-26
> **Harry33 said:**
> Removing Unity:
- remove all unity packages except libunity6 (search with Synaptic)
- remove all nux packages (search with Synaptic)
- after that install deborpan and run it from terminal (sudo) and it shows the orphaned packages that can be removed.

Nvidia-current 290.03:
From Xorg-edgers - look for Oneiric branch: nvidia-graphics-drivers
[https://launchpad.net/~xorg-edgers/+archive/ppa/+packages?field.name_filter=&field.status_filter=published&field.series_filter=oneiric]("https://launchpad.net/%7Exorg-edgers/+archive/ppa/+packages?field.name_filter=&field.status_filter=published&field.series_filter=oneiric")

Install (correct architecture):
- nvidia-current_290.03
- nvidia-settings_290.03

Harry33,


Thanks a million. I removed just the main Unity package(using synaptic) last night (on a hunch) and sure enough I got Gnome-Shell working just beautiful under 3.1.0-1-generic. (haven't tested the other kernels yet.)

  Thanks for the Unity removal info.  Definitely a Unity package problem from day-befores earlier updates.

  I will continue the removal process, re-install unity , try to install that new Nvidia-currewnt and report back in.

One note I wanted to make. I noticed that the updates re-updated (or called from hdd) the file <squircle1_base_54.png> from the usr/share/unity directory. Why is this important?? Because I edited that file (which is a transparent layer for the  launcher) and I embedded the letters (Unity3D)  on it and layered it. This was to help me differentiate (as a possible work-a-round also) between Unity 3D and Unity 2D. However , after the update, it was restored to it's original motif!! So I am just curious as to why the synaptic updater updated those files in the usr/share/unity directory.

regards,

ventrical

---

### Post by effenberg0x0 on 2011-10-26
Just a comment / tip. If you need to test a bunch of nvidia-proprietary versions, you can download them all at once and save them to your downloads folder easily by using NVidia FTP Server at download.nvidia.com. It's also a good idea to remember their ftp cause sometimes we are stuck with no GUI and need a driver... See the list of versions below:

```
[04:13 ][al:AL-DESK:~]
$ ftp download.nvidia.com
Connected to download.nvidia.com.
220 spftp/1.0.0000 Server [207.138.133.238]
Name (download.nvidia.com:al): anonymous
331 Password required for USER.
Password:
230- 
230- ---------------------------------------------------------------------------
230- WARNING:  This is a restricted access system.  If you do not have explicit
230-           permission to access this system, please disconnect immediately!
230 ----------------------------------------------------------------------------
Remote system type is UNIX.
ftp> bin
200 TYPE set to I.
ftp> hash
Hash mark printing on (1024 bytes/hash mark).
ftp> cd XFree86/Linux-x86_64
250 CWD command successful.
ftp> ls
200 PORT command successful.
150 Opening ASCII mode data connection for /XFree86/Linux-x86_64.
drwxrwxr-x   1     1994     1994        0 Oct 24 15:40 1.0-5332
drwxrwxr-x   1     1994     1994        0 Oct 24 15:40 1.0-6106
drwxrwxr-x   1     1994     1994        0 Oct 24 15:40 1.0-6111
drwxrwxr-x   1     1994     1994        0 Oct 24 15:40 1.0-6629
drwxrwxr-x   1     1994     1994        0 Oct 24 15:40 1.0-7167
drwxrwxr-x   1     1994     1994        0 Oct 24 15:40 1.0-7174
drwxrwxr-x   1     1994     1994        0 Oct 24 16:21 1.0-7182
drwxrwxr-x   1     1994     1994        0 Oct 24 16:21 1.0-7184
drwxrwxr-x   1     1994     1994        0 Oct 24 16:21 1.0-7185
drwxrwxr-x   1     1994     1994        0 Oct 24 15:40 1.0-7664
drwxrwxr-x   1     1994     1994        0 Oct 24 15:40 1.0-7667
drwxrwxr-x   1     1994     1994        0 Oct 24 15:40 1.0-7676
drwxrwxr-x   1     1994     1994        0 Oct 24 17:05 1.0-8174
drwxrwxr-x   1     1994     1994        0 Oct 24 16:21 1.0-8178
drwxrwxr-x   1     1994     1994        0 Oct 24 15:41 1.0-8181
drwxrwxr-x   1     1994     1994        0 Oct 24 16:21 1.0-8756
drwxrwxr-x   1     1994     1994        0 Oct 24 16:21 1.0-8762
drwxrwxr-x   1     1994     1994        0 Oct 24 16:21 1.0-8774
drwxrwxr-x   1     1994     1994        0 Oct 24 16:21 1.0-8776
drwxrwxr-x   1     1994     1994        0 Oct 24 16:21 1.0-9625
drwxrwxr-x   1     1994     1994        0 Oct 24 16:22 1.0-9626
drwxrwxr-x   1     1994     1994        0 Oct 24 16:22 1.0-9629
drwxrwxr-x   1     1994     1994        0 Oct 24 16:22 1.0-9631
drwxrwxr-x   1     1994     1994        0 Oct 24 16:22 1.0-9639
drwxrwxr-x   1     1994     1994        0 Oct 24 16:22 1.0-9746
drwxrwxr-x   1     1994     1994        0 Oct 24 16:22 1.0-9755
drwxrwxr-x   1     1994     1994        0 Oct 24 16:22 1.0-9762
drwxrwxr-x   1     1994     1994        0 Oct 24 16:22 100.14.03
drwxrwxr-x   1     1994     1994        0 Oct 24 16:23 100.14.06
drwxrwxr-x   1     1994     1994        0 Oct 24 16:23 100.14.09
drwxrwxr-x   1     1994     1994        0 Oct 24 16:23 100.14.11
drwxrwxr-x   1     1994     1994        0 Oct 24 16:23 100.14.19
drwxrwxr-x   1     1994     1994        0 Oct 24 16:23 100.14.23
drwxrwxr-x   1     1994     1994        0 Oct 24 16:23 165.33.09
drwxrwxr-x   1     1994     1994        0 Oct 24 16:23 169.04
drwxrwxr-x   1     1994     1994        0 Oct 24 16:23 169.07
drwxrwxr-x   1     1994     1994        0 Oct 24 16:24 169.09
drwxrwxr-x   1     1994     1994        0 Oct 24 16:24 169.12
drwxrwxr-x   1     1994     1994        0 Oct 24 16:24 171.05
drwxrwxr-x   1     1994     1994        0 Oct 24 16:24 171.06
drwxrwxr-x   1     1994     1994        0 Oct 24 16:24 171.06.01
drwxrwxr-x   1     1994     1994        0 Oct 24 16:24 173.08
drwxrwxr-x   1     1994     1994        0 Oct 24 16:24 173.14.05
drwxrwxr-x   1     1994     1994        0 Oct 24 16:24 173.14.12
drwxrwxr-x   1     1994     1994        0 Oct 24 16:25 173.14.15
drwxrwxr-x   1     1994     1994        0 Oct 24 16:25 173.14.16
drwxrwxr-x   1     1994     1994        0 Oct 24 16:25 173.14.17
drwxrwxr-x   1     1994     1994        0 Oct 24 16:25 173.14.18
drwxrwxr-x   1     1994     1994        0 Oct 24 16:25 173.14.19
drwxrwxr-x   1     1994     1994        0 Oct 24 16:25 173.14.20
drwxrwxr-x   1     1994     1994        0 Oct 24 16:25 173.14.22
drwxrwxr-x   1     1994     1994        0 Oct 24 16:25 173.14.25
drwxrwxr-x   1     1994     1994        0 Oct 24 16:26 173.14.27
drwxrwxr-x   1     1994     1994        0 Oct 24 16:26 173.14.28
drwxrwxr-x   1     1994     1994        0 Oct 24 16:26 173.14.30
drwxrwxr-x   1     1994     1994        0 Oct 24 16:39 173.14.31
drwxrwxr-x   1     1994     1994        0 Oct 24 15:44 177.61.02
drwxrwxr-x   1     1994     1994        0 Oct 24 16:26 177.67
drwxrwxr-x   1     1994     1994        0 Oct 24 16:26 177.68
drwxrwxr-x   1     1994     1994        0 Oct 24 16:26 177.70
drwxrwxr-x   1     1994     1994        0 Oct 24 16:26 177.76
drwxrwxr-x   1     1994     1994        0 Oct 24 16:27 177.78
drwxrwxr-x   1     1994     1994        0 Oct 24 16:27 177.80
drwxrwxr-x   1     1994     1994        0 Oct 24 16:27 177.82
drwxrwxr-x   1     1994     1994        0 Oct 24 16:27 180.06
drwxrwxr-x   1     1994     1994        0 Oct 24 16:27 180.08
drwxrwxr-x   1     1994     1994        0 Oct 24 16:27 180.11
drwxrwxr-x   1     1994     1994        0 Oct 24 16:27 180.11.02
drwxrwxr-x   1     1994     1994        0 Oct 24 16:28 180.16
drwxrwxr-x   1     1994     1994        0 Oct 24 16:28 180.18
drwxrwxr-x   1     1994     1994        0 Oct 24 16:28 180.22
drwxrwxr-x   1     1994     1994        0 Oct 24 16:28 180.25
drwxrwxr-x   1     1994     1994        0 Oct 24 16:28 180.27
drwxrwxr-x   1     1994     1994        0 Oct 24 16:28 180.29
drwxrwxr-x   1     1994     1994        0 Oct 24 16:28 180.35
drwxrwxr-x   1     1994     1994        0 Oct 24 16:29 180.37
drwxrwxr-x   1     1994     1994        0 Oct 24 16:29 180.37.05
drwxrwxr-x   1     1994     1994        0 Oct 24 16:29 180.41
drwxrwxr-x   1     1994     1994        0 Oct 24 16:29 180.44
drwxrwxr-x   1     1994     1994        0 Oct 24 16:29 180.50
drwxrwxr-x   1     1994     1994        0 Oct 24 16:29 180.51
drwxrwxr-x   1     1994     1994        0 Oct 24 16:30 180.53
drwxrwxr-x   1     1994     1994        0 Oct 24 16:30 180.60
drwxrwxr-x   1     1994     1994        0 Oct 24 16:30 185.13
drwxrwxr-x   1     1994     1994        0 Oct 24 16:30 185.18.04
drwxrwxr-x   1     1994     1994        0 Oct 24 16:30 185.18.08
drwxrwxr-x   1     1994     1994        0 Oct 24 16:31 185.18.10
drwxrwxr-x   1     1994     1994        0 Oct 24 16:31 185.18.14
drwxrwxr-x   1     1994     1994        0 Oct 24 16:31 185.18.29
drwxrwxr-x   1     1994     1994        0 Oct 24 16:31 185.18.31
drwxrwxr-x   1     1994     1994        0 Oct 24 16:31 185.18.36
drwxrwxr-x   1     1994     1994        0 Oct 24 16:31 185.19
drwxrwxr-x   1     1994     1994        0 Oct 24 16:32 190.18
drwxrwxr-x   1     1994     1994        0 Oct 24 16:32 190.18.05
drwxrwxr-x   1     1994     1994        0 Oct 24 16:32 190.25
drwxrwxr-x   1     1994     1994        0 Oct 24 16:32 190.32
drwxrwxr-x   1     1994     1994        0 Oct 24 16:32 190.36
drwxrwxr-x   1     1994     1994        0 Oct 24 16:32 190.40
drwxrwxr-x   1     1994     1994        0 Oct 24 16:33 190.42
drwxrwxr-x   1     1994     1994        0 Oct 24 16:33 190.53
drwxrwxr-x   1     1994     1994        0 Oct 24 16:33 195.22
drwxrwxr-x   1     1994     1994        0 Oct 24 16:33 195.30
drwxrwxr-x   1     1994     1994        0 Oct 24 16:33 195.36.15
drwxrwxr-x   1     1994     1994        0 Oct 24 16:33 195.36.24
drwxrwxr-x   1     1994     1994        0 Oct 24 16:33 195.36.31
drwxrwxr-x   1     1994     1994        0 Oct 24 16:34 256.25
drwxrwxr-x   1     1994     1994        0 Oct 24 16:34 256.29
drwxrwxr-x   1     1994     1994        0 Oct 24 16:34 256.35
drwxrwxr-x   1     1994     1994        0 Oct 24 16:34 256.38.02
drwxrwxr-x   1     1994     1994        0 Oct 24 16:34 256.38.03
drwxrwxr-x   1     1994     1994        0 Oct 24 16:34 256.44
drwxrwxr-x   1     1994     1994        0 Oct 24 16:34 256.52
drwxrwxr-x   1     1994     1994        0 Oct 24 16:34 256.53
drwxrwxr-x   1     1994     1994        0 Oct 24 16:35 260.19.04
drwxrwxr-x   1     1994     1994        0 Oct 24 16:35 260.19.06
drwxrwxr-x   1     1994     1994        0 Oct 24 16:35 260.19.12
drwxrwxr-x   1     1994     1994        0 Oct 24 16:35 260.19.21
drwxrwxr-x   1     1994     1994        0 Oct 24 16:35 260.19.26
drwxrwxr-x   1     1994     1994        0 Oct 24 16:35 260.19.29
drwxrwxr-x   1     1994     1994        0 Oct 24 16:35 260.19.36
drwxrwxr-x   1     1994     1994        0 Oct 24 16:36 260.19.44
drwxrwxr-x   1     1994     1994        0 Oct 24 16:35 270.18
drwxrwxr-x   1     1994     1994        0 Oct 24 16:36 270.26
drwxrwxr-x   1     1994     1994        0 Oct 24 16:36 270.29
drwxrwxr-x   1     1994     1994        0 Oct 24 16:36 270.30
drwxrwxr-x   1     1994     1994        0 Oct 24 16:36 270.41.03
drwxrwxr-x   1     1994     1994        0 Oct 24 16:36 270.41.06
drwxrwxr-x   1     1994     1994        0 Oct 24 16:36 270.41.19
drwxrwxr-x   1     1994     1994        0 Oct 24 16:37 275.09
drwxrwxr-x   1     1994     1994        0 Oct 24 16:38 275.09.04
drwxrwxr-x   1     1994     1994        0 Oct 24 16:38 275.09.07
drwxrwxr-x   1     1994     1994        0 Oct 24 16:39 275.19
drwxrwxr-x   1     1994     1994        0 Oct 24 16:39 275.21
drwxrwxr-x   1     1994     1994        0 Oct 24 16:40 275.28
drwxrwxr-x   1     1994     1994        0 Oct 24 16:39 280.04
drwxrwxr-x   1     1994     1994        0 Oct 24 16:39 280.11
drwxrwxr-x   1     1994     1994        0 Oct 24 16:39 280.13
drwxrwxr-x   1     1994     1994        0 Oct 24 16:40 285.03
drwxrwxr-x   1     1994     1994        0 Oct 24 16:40 285.05.09
drwxrwxr-x   1     1994     1994        0 Oct 24 16:40 290.03
drwxrwxr-x   1     1994     1994        0 Oct 24 16:37 71.86.01
drwxrwxr-x   1     1994     1994        0 Oct 24 16:37 71.86.04
drwxrwxr-x   1     1994     1994        0 Oct 24 16:37 71.86.07
drwxrwxr-x   1     1994     1994        0 Oct 24 16:37 71.86.08
drwxrwxr-x   1     1994     1994        0 Oct 24 16:37 71.86.09
drwxrwxr-x   1     1994     1994        0 Oct 24 16:37 71.86.10
drwxrwxr-x   1     1994     1994        0 Oct 24 16:37 71.86.11
drwxrwxr-x   1     1994     1994        0 Oct 24 16:37 71.86.13
drwxrwxr-x   1     1994     1994        0 Oct 24 16:37 71.86.14
drwxrwxr-x   1     1994     1994        0 Oct 24 16:39 71.86.15
drwxrwxr-x   1     1994     1994        0 Oct 24 16:37 96.43.01
drwxrwxr-x   1     1994     1994        0 Oct 24 16:37 96.43.05
drwxrwxr-x   1     1994     1994        0 Oct 24 16:37 96.43.09
drwxrwxr-x   1     1994     1994        0 Oct 24 16:37 96.43.10
drwxrwxr-x   1     1994     1994        0 Oct 24 16:37 96.43.11
drwxrwxr-x   1     1994     1994        0 Oct 24 16:37 96.43.12
drwxrwxr-x   1     1994     1994        0 Oct 24 16:38 96.43.13
drwxrwxr-x   1     1994     1994        0 Oct 24 16:38 96.43.14
drwxrwxr-x   1     1994     1994        0 Oct 24 16:38 96.43.16
drwxrwxr-x   1     1994     1994        0 Oct 24 16:38 96.43.17
drwxrwxr-x   1     1994     1994        0 Oct 24 16:38 96.43.18
drwxrwxr-x   1     1994     1994        0 Oct 24 16:38 96.43.19
drwxrwxr-x   1     1994     1994        0 Oct 24 16:39 96.43.20
-rw-rw-r--   1     1994     1994       54 Oct 24 15:36 latest.txt
226 Transfer Complete
ftp> bye
221 Goodbye. 
```

---

### Post by ventrical on 2011-10-26
Thanks effenberg.

@harry33,effenberg

Ok .. removed unity, nux now I have no display or login screen after reboot. Just terminal. Tried to run synaptic, I get the report - cannot display.

Ok .. so how do I now re-install unity from terminal ??

thankyou

  :)

---

### Post by Harry33 on 2011-10-26
> **ventrical said:**
> Thanks effenberg.

@harry33,effenberg

Ok .. removed unity, nux now I have no display or login screen after reboot. Just terminal. Tried to run synaptic, I get the report - cannot display.

Ok .. so how do I now re-install unity from terminal ??

thankyou

  :)

This should bring back sessions unity and unity 2d.

```
sudo apt-get install unity unity-2d
```

But simply removing all the packages with the name unity or nux does not destroy in any way gnome-shell nor gnome-panel nor X.
I would like to see the list of packages you have removed.

But if you removed the package libunity6 too (which I said should not be removed), also the packages Nautilus and gnome-session would have been removed.
In this case run this first:

```
sudo apt-get install nautilus gnome-session
```

---

### Post by ventrical on 2011-10-26
> **Harry33 said:**
> This should bring back sessions unity and unity 2d.

```
sudo apt-get install unity unity-2d
```But simply removing all the packages with the name unity or nux does not destroy in any way gnome-shell nor gnome-panel nor X.
I would like to see the list of packages you have removed.

But if you removed the package libunity6 too (which I said should not be removed), also the packages Nautilus and gnome-session would have been removed.
In this case run this first:

```
sudo apt-get install nautilus gnome-session
```


gnome session was already installed. I *did* not remove libunity6!

  I re-installed unity and all the other packs you suggested. Also I installed:

sudo apt-get ubuntu desktop

It downloaded and installed a file.

 I tried start lightdm and all that did was bring me back to the start page with verbose error messages.

I know I'm missing something . It wants to start .. but seems   to be missing a hook somewhere.

 I knew what I was getting into when I started this project. if I have to re-install I will (I have 2 other Precise installs) but I really like to try and bring busted systems back up to par.. even manually if I have to.

 I'm still open to other directions and suggestions. Thanks for all your help harry33.

side note... what log file would tell me which pkgs were removed? and how would I get to that ?

thanks

---

### Post by ventrical on 2011-10-26
I did think it strange that it removed the unity-greeter ?? does that have anything to do with it?

---

### Post by effenberg0x0 on 2011-10-26
If it's just lightdm misconfig, I have some some settings on a script, that usually fix most problems... but they to be run at a VT, not terminal.

```
sudo service lightdm stop
sudo service gdm stop
sudo killall -s KILL /usr/bin/X
sudo killall -s KILL /usr/sbin/lightdm
sudo killall -s KILL /usr/sbin/gdm
sudo killall -s KILL /usr/bin/gdm

export DISPLAY=:0.0
export XDG_CURRENT_DESKTOP=Unity
export XDG_DATA_DIRS=/usr/share/ubuntu:/usr/share/gnome:/usr/local/share/:/usr/share/
export COMPIZ_CONFIG_PROFILE=ubuntu
export GDMSESSION=ubuntu
export DESKTOP_SESSION=ubuntu
export PATH=/home/$USER:/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
export XDG_SESSION_PATH=/org/freedesktop/DisplayManager/Session0
export XDG_SEAT_PATH=/org/freedesktop/DisplayManager/Seat0
export DEFAULTS_PATH=/usr/share/gconf/ubuntu.default.path
sudo chown $USER:$USER /home/$USER -R && sudo chmod 750 /home/$USER -R
sudo apt-get remove --purge gdm
sudo apt-get install --reinstall lightdm lightdm-gtk-greeter unity-greeter
sudo service lightdm stop
if [ ! -f /etc/lightdm/lightdm.conf ]; then sudo touch /etc/lightdm/lightdm.conf
echo -e "[SeatDefaults]\r\nuser-session=ubuntu\r\ngreeter-session=unity-greeter" | sudo tee /etc/lightdm/lightdm.conf
if [ ! -f /etc/X11/default-display-manager ]; then sudo touch /etc/X11/default-display-manager
echo -e "/usr/sbin/lightdm" | sudo tee /etc/X11/default-display-manager
sudo mv ~/.Xauthority ~/.Xauthority.backup
sudo gconftool-2 --recursive-unset /apps/compiz-1
sudo gconftool-2 --recursive-unset /apps/compizconfig-1
sudo mv ~/.config/compiz-1/compizconfig ~/.config/compiz-1/compizconfig.old
sudo mv ~/.config/compiz-1 ~/.config/compiz.old
sudo mv ~/.compiz-1 ~/.compiz-1.old
sudo mv ~/.cache/compizconfig-1 ~/.cache/compizconfig-1.old
sudo service lightdm start

```If it fails... you can go deeper and reinstall all critical default packages for Unity/Compiz/Lightdm structure..

```
sudo apt-get install --reinstall --fix-broken --allow-unauthenticated lightdm unity unity-2d unity-2d-launcher unity-2d-panel unity unity-2d-places unity-greeter unity-lens-music unity-services unity-2d unity-2d-spread unity-lens-applications unity-place-applications unity-2d-launcher unity-asset-pool unity-lens-files unity-place-files unity-2d-panel unity-common unity-lens-gwibber unity-scope-musicstores compiz compiz-dev compiz-kde compiz-plugins-main-default compizconfig-backend-gconf compiz-fusion-bcop compiz-plugins compiz-plugins-main-dev compizconfig-backend-kconfig compiz-fusion-plugins-extra compiz-plugins-default compizconfig-settings-manager  compiz-fusion-plugins-main compiz-plugins-extra compiz-core compiz-gnome compiz-plugins-main
sudo reboot now
```[B]EDIT
[/B]You could just save the first block of code to something like **fix.sh **in your home directory, run **sudo chmod +x /home/dale/fix.sh** and run **sh /home/dale/fix.sh **in a VT to avoid having to type all lines of code...

**EDIT 2:** Also,** sudo nano /var/log/Xorg.0.log, ****sudo nano /var/log/dmesg.log, ****sudo nano /var/log/syslog, **because these files will give you tips for the reason the session is not starting. Can be video driver related, for example.

---

### Post by ventrical on 2011-10-26
@effenberg

bravo !!!!!!!!!!  It worked!! I lost all my configs but I got my FVWM-Crystal, Gnome Classic and Unity is working no prob. (just have to reconfigure it.)

  Looks like I narrowed it down to gnome_screenshot!1 As soon as I take a pic with that my CPU bumps up to 100% so I use shutter.

 I'll check over that code (there were some problems because you have to go into > when using 'if" commands.. so I missed a few lines .. but I did the bottom  line of code and all I missed was the places lenses :) eheheaheaheh...  long night ... zzzzzzzzzzzz time..

Thanks for sticking with this one  and an added bonus ,, no kernel panic or hogged up resources...with exception of gnome screenshot

thanks again

---

### Post by effenberg0x0 on 2011-10-26
Cool, all good then. If you look at the code, you'll see that in fact it does a backup of your compiz settings. Look at this part:
```

sudo mv ~/.config/compiz-1/compizconfig ~/.config/compiz-1/compizconfig.old
sudo mv ~/.config/compiz-1 ~/.config/compiz.old
sudo mv ~/.compiz-1 ~/.compiz-1.old

```So you may try to restore them and will probably succeed by restoring these directories.

**EDIT:** If you try to restore the previous settings, just take care with that issue with profiles. Find that thread where mc4man brilliantly explained us the best way to deal with them.

> 
I'll check over that code (there were some problems because you have to go into > when using 'if" commands.. so I missed a few lines
I'm not sure, works here for me. Unless a ', " or ` is missing somewhere. I'll check it. Anyway, the if condiditions were applied only twice and what they actually would do if == true is right below, so you'll see they just check if two configs of lightdm are correctly set.

> **ventrical said:**
> 
  Looks like I narrowed it down to gnome_screenshot!1 As soon as I take a  pic with that my CPU bumps up to 100% so I use shutter.

But does the process of gnome-screenshot stalls? I see it starts two pids here (**ps ax | grep -i gnome-screenshot**). If they get stuck there, just **sudo kill -s KILL `pidof gnome-screenshot`** to get rid if them.

---

### Post by ventrical on 2011-10-27
Ok.. problem came back with the kernel hanging, However I can use FVWM-Crystal windows manager and Gnome-Classic.

  I am going to ask to leave this thread open because I would like to keep this install as a relic-reference point - and perhaps I will try to take up purging it once again soon.

 I would just like to note that in all of this I find that there is some very good code that I believe can be deployed in the Grub Bootloader Recovery Options. A sort of like system restore concept being deployed.

  Thanks to harry33, effen , caribou and all  for your help . I have 2 other Precise Installs (har) that I have to tend to plus my usual job or malware removal for WinOs systems.
:)

regards

ventrical

---

### Post by effenberg0x0 on 2011-10-27
There has to be some tip for what exactly is going on there inside the log files. Linux allows for (and encourages) a more systematic and professional approach to system maintenance. It is transparent (and verbose) about its processes.  Otherwise this would be the typical Windows guessing game, which brings me very bad memories.

This small command below, for example, will search all the system log files for the words "segfault", "warning", "error" and "critical", copy the lines in which those words were found to a single text file in your home directory (log_analysis*.log) and open this new file with gedit. It will do that in less than 10 seconds. If you try to scroll the file to the date/time in which you sensed problems and filter this file even more, you will find out what is not working well there in your system. 

```
for LOGFILE in $(ls /var/log/*.log); do sudo grep -iHw 'segfault\|warning\|error\|critical' $LOGFILE >> $HOME/log_analysis$(date +%d.%m.%y-%H:%M).log; done && DISPLAY=:0.0 gedit $HOME/log_analysis*

```

Say you find an interesting line in this log_analysis.log, that my be related to the issue at hand, and its marked as coming from Xorg.0.log. You would then open /var/log/Xorg.0.log directly in gedit to perform a more detailed analysis. 

You'll lose something like 30 minutes with this approach, but your chances of finding what is wrong and fixing it increase dramatically.

Good Luck :)

Effenberg

---

### Post by ventrical on 2011-10-27
> **effenberg0x0 said:**
> There has to be some tip for what exactly is going on there inside the log files. Linux allows for (and encourages) a more systematic and professional approach to system maintenance. It is transparent (and verbose) about its processes.  Otherwise this would be the typical Windows guessing game, which brings me very bad memories.

This small command below, for example, will search all the system log files for the words "segfault", "warning", "error" and "critical", copy the lines in which those words were found to a single text file in your home directory (log_analysis*.log) and open this new file with gedit. It will do that in less than 10 seconds. If you try to scroll the file to the date/time in which you sensed problems and filter this file even more, you will find out what is not working well there in your system. 

```
for LOGFILE in $(ls /var/log/*.log); do sudo grep -iHw 'segfault\|warning\|error\|critical' $LOGFILE >> $HOME/log_analysis$(date +%d.%m.%y-%H:%M).log; done && DISPLAY=:0.0 gedit $HOME/log_analysis*

```Say you find an interesting line in this log_analysis.log, that my be related to the issue at hand, and its marked as coming from Xorg.0.log. You would then open /var/log/Xorg.0.log directly in gedit to perform a more detailed analysis. 

You'll lose something like 30 minutes with this approach, but your chances of finding what is wrong and fixing it increase dramatically.

Good Luck :)

Effenberg

Thanks .. I'll get back to this. I am working on another  Precise system for a while .. but I will get back to that one with probs a little later. as I say .. lots of work to do before 12.04 release day !! I'm glad I'm getting broken systems now .. it will keep me sharp for the rougher stuff comming down the pipe.

---

### Post by ventrical on 2011-10-27
> **effenberg0x0 said:**
> If it's just lightdm misconfig, I have some some settings on a script, that usually fix most problems... but they to be run at a VT, not terminal.



```
sudo apt-get install --reinstall --fix-broken --allow-unauthenticated lightdm unity unity-2d unity-2d-launcher unity-2d-panel unity unity-2d-places unity-greeter unity-lens-music unity-services unity-2d unity-2d-spread unity-lens-applications unity-place-applications unity-2d-launcher unity-asset-pool unity-lens-files unity-place-files unity-2d-panel unity-common unity-lens-gwibber unity-scope-musicstores compiz compiz-dev compiz-kde compiz-plugins-main-default compizconfig-backend-gconf compiz-fusion-bcop compiz-plugins compiz-plugins-main-dev compizconfig-backend-kconfig compiz-fusion-plugins-extra compiz-plugins-default compizconfig-settings-manager  compiz-fusion-plugins-main compiz-plugins-extra compiz-core compiz-gnome compiz-plugins-main
sudo reboot now
```[B]EDIT
[/B].

I just ran this again in Terminal and got Cairo and all compiz settings back.Amazing.

 The only thing missing is the Unity 3d apps icon... <places>/ the little thing that looks like books side by side between the home icon and the musical note icon.

 I was also having probs logging out and shutting down... ok . here goes.. try and try again :)

---

### Post by effenberg0x0 on 2011-10-27
> **ventrical said:**
> I just ran this again in Terminal and got Cairo and all compiz settings back.Amazing.

 The only thing missing is the Unity 3d apps icon... <places>/ the little thing that looks like books side by side between the home icon and the musical note icon.

 I was also having probs logging out and shutting down... ok . here goes.. try and try again :)

Hey,

When I typed that I tried to remember the more crucial packages for the Unity/Compiz/Lightdm combo one could reinstall in a single command to get a system up and running. But it's very likely that I probably forgot one or another lens and etc. You can install them easily anyway. The thing you're talking about is the application lens. You install it like this:

```
sudo apt-get install --reinstall unity-lens-applications
```

---

### Post by ventrical on 2011-10-27
hey ..

ok .. will do .. in the meantime ... here->

dale@ubuntu:~/Downloads$ sudo dpkg -i nvidia-current_290.03-0ubuntu1~xedgers~oneiric1_i386.deb
[sudo] password for dale: 
Selecting previously unselected package nvidia-current.
(Reading database ... 314051 files and directories currently installed.)
Unpacking nvidia-current (from nvidia-current_290.03-0ubuntu1~xedgers~oneiric1_i386.deb) ...
dpkg: dependency problems prevent configuration of nvidia-current:
 nvidia-current depends on xorg-video-abi-11; however:
  Package xorg-video-abi-11 is not installed.
 nvidia-current depends on xserver-xorg-core (>= 2:1.10.99.901); however:
  Version of xserver-xorg-core on system is 2:1.10.4-1ubuntu5.
dpkg: error processing nvidia-current (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db ...
Errors were encountered while processing:
 nvidia-current
dale@ubuntu:~/Downloads$ 


So now what?

---

### Post by ventrical on 2011-10-27
> **effenberg0x0 said:**
> Hey,

When I typed that I tried to remember the more crucial packages for the Unity/Compiz/Lightdm combo one could reinstall in a single command to get a system up and running. But it's very likely that I probably forgot one or another lens and etc. You can install them easily anyway. The thing you're talking about is the application lens. You install it like this:

```
sudo apt-get install --reinstall unity-lens-applications
```

Won't let me install until depends are met->


dale@ubuntu:~$ sudo apt-get install --reinstall unity-lens-applications
[sudo] password for dale: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 nvidia-current : Depends: xorg-video-abi-11 but it is not installable
                  Depends: xserver-xorg-core (>= 2:1.10.99.901) but 2:1.10.4-1ubuntu5 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
dale@ubuntu:~$

---

### Post by ventrical on 2011-10-27
k .. removed nvidia current and was able to install unity lens

---

### Post by effenberg0x0 on 2011-10-27
Oh, I see you have enabled non-standard repos, probably xorg-edgers or something. I can't help with that... no experience at all with the non-standard packages until now. So far I'm sticking to defaults.

---

### Post by paul_in_london on 2011-10-27
> **ventrical said:**
> Won't let me install until depends are met->


dale@ubuntu:~$ sudo apt-get install --reinstall unity-lens-applications
[sudo] password for dale: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 nvidia-current : Depends: xorg-video-abi-11 but it is not installable
                  Depends: xserver-xorg-core (>= 2:1.10.99.901) but 2:1.10.4-1ubuntu5 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
dale@ubuntu:~$

Posting this from PP 64 bit, but what do you get if you run this (see bit of the output highlighted in red)?

```
paul@precise-64:~$ apt-cache show xserver-xorg-core

Package: xserver-xorg-core
Priority: optional
Section: x11
Installed-Size: 4059
Maintainer: Ubuntu X-SWAT <ubuntu-x@lists.ubuntu.com>
Original-Maintainer: Debian X Strike Force <debian-x@lists.debian.org>
Architecture: amd64
Source: xorg-server
Version: 2:1.10.4-1ubuntu5
Provides: xorg-input-abi-12, xorg-video-abi-10
Depends: xserver-common (>= 2:1.10.4-1ubuntu5), keyboard-configuration, udev (>= 149), libc6 (>= 2.8), libdrm2 (>= 2.3.1), libgcrypt11 (>= 1.4.5), libpciaccess0 (>= 0.10.7), libpixman-1-0 (>= 0.15.16), libudev0 (>= 147), libxau6, libxdmcp6, libxfont1 (>= 1:1.4.2)
Recommends: libgl1-mesa-dri (>= 7.10.2-4)
Suggests: xfonts-100dpi | xfonts-75dpi, xfonts-scalable
Breaks: libgl1-mesa-dri (<< 7.10.2-4), libgl1-mesa-dri-experimental (<< 7.10.2-4), libgl1-mesa-dri-no-multiarch, xserver-xorg-input, xserver-xorg-input-2, xserver-xorg-input-2.1, xserver-xorg-input-4, xserver-xorg-input-7, xserver-xorg-input-joystick (<= 1:1.5.0-3), xserver-xorg-input-synaptics (<= 1.2.2-1ubuntu4), xserver-xorg-input-tslib (<= 0.0.6-3), xserver-xorg-input-vmmouse (<= 1:12.6.5-4ubuntu2), xserver-xorg-input-wacom (<= 0.10.5+20100415-1), xserver-xorg-video, xserver-xorg-video-1.0, xserver-xorg-video-1.9, xserver-xorg-video-2, xserver-xorg-video-4, xserver-xorg-video-5, xserver-xorg-video-6, xserver-xorg-video-cyrix (<= 1:1.1.0-8), xserver-xorg-video-i810 (<< 2:2.4), xserver-xorg-video-imstt (<= 1:1.1.0-7), xserver-xorg-video-nsc (<= 1:2.8.3-4), xserver-xorg-video-sunbw2 (<= 1:1.1.0-5), xserver-xorg-video-v4l (<< 1:0.2.0), xserver-xorg-video-vga (<= 1:4.1.0-8)
Filename: pool/main/x/xorg-server/xserver-xorg-core_1.10.4-1ubuntu5_amd64.deb
Size: 1695010
MD5sum: 6e731c03e4fdde0fc31d67ff488619fc
SHA1: b9a3650842ce4b0eb2b7de5efb60ccbf79b8e622
SHA256: 02303f3361cb7880aeffa77ec4ba0c7c794145f25ae736825435c197cf9fb0c5
Description-en: Xorg X server - core server
 The Xorg X server is an X server for several architectures and operating
 systems, which is derived from the XFree86 4.x series of X servers.
 .
 The Xorg server supports most modern graphics hardware from most vendors,
 and supersedes all XFree86 X servers.
 .
 More information about X.Org can be found at:
 <URL:http://www.X.org>
 .
 This package is built from the X.org xserver module.
Description-md5: e3826a765918b79dee4b90ec97f9302c
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
Supported: 18m
Task: ubuntu-desktop, ubuntu-usb, kubuntu-desktop, kubuntu-mobile-desktop, kubuntu-mobile, edubuntu-desktop, edubuntu-usb, xubuntu-desktop, mythbuntu-backend-master, mythbuntu-backend-slave, mythbuntu-desktop, mythbuntu-frontend, lubuntu-core, ubuntustudio-desktop

Package: xserver-xorg-core
Source: xorg-server
Priority: optional
Section: x11
Installed-Size: 4120
Maintainer: Ubuntu X-SWAT <ubuntu-x@lists.ubuntu.com>
Architecture: amd64
Version: 2:1.11.1.901+git20111024+server-1.11-branch.c8c5ed99-0ubuntu0sarvatt
Recommends: libgl1-mesa-dri (>= 7.10.2-4)
Suggests: xfonts-100dpi | xfonts-75dpi, xfonts-scalable
Provides: xorg-input-abi-13, **[COLOR="Red"]xorg-video-abi-11[/COLOR]**
Depends: xserver-common (>= 2:1.11.1.901+git20111024+server-1.11-branch.c8c5ed99-0ubuntu0sarvatt), keyboard-configuration, udev (>= 149), libc6 (>= 2.8), libdrm2 (>= 2.3.1), libgcrypt11 (>= 1.5.0-0), libpciaccess0 (>= 0.10.7), libpixman-1-0 (>= 0.21.6), libudev0 (>= 147), libxau6, libxdmcp6, libxfont1 (>= 1:1.4.2)
Breaks: libgl1-mesa-dri (<< 7.10.2-4), libgl1-mesa-dri-experimental (<< 7.10.2-4), xserver-xorg-input, xserver-xorg-input-2, xserver-xorg-input-2.1, xserver-xorg-input-4, xserver-xorg-input-7, xserver-xorg-input-joystick (<= 1:1.5.0-3), xserver-xorg-input-synaptics (<= 1.2.2-1ubuntu4), xserver-xorg-input-tslib (<= 0.0.6-3), xserver-xorg-input-vmmouse (<= 1:12.6.5-4ubuntu2), xserver-xorg-input-wacom (<< 0.7.8), xserver-xorg-video, xserver-xorg-video-1.0, xserver-xorg-video-1.9, xserver-xorg-video-2, xserver-xorg-video-4, xserver-xorg-video-5, xserver-xorg-video-6, xserver-xorg-video-cyrix (<= 1:1.1.0-8), xserver-xorg-video-i810 (<< 2:2.4), xserver-xorg-video-imstt (<= 1:1.1.0-7), xserver-xorg-video-nsc (<= 1:2.8.3-4), xserver-xorg-video-sunbw2 (<= 1:1.1.0-5), xserver-xorg-video-v4l (<< 1:0.2.0), xserver-xorg-video-vga (<= 1:4.1.0-8)
Filename: pool/main/x/xorg-server/xserver-xorg-core_1.11.1.901+git20111024+server-1.11-branch.c8c5ed99-0ubuntu0sarvatt_amd64.deb
Size: 1744130
MD5sum: f33632c49de3b32bcc7712f190d436b7
SHA1: 16590143ba2bd705eeec9807a3e06b24290e3071
Description-en: Xorg X server - core server
 The Xorg X server is an X server for several architectures and operating
 systems, which is derived from the XFree86 4.x series of X servers.
 .
 The Xorg server supports most modern graphics hardware from most vendors,
 and supersedes all XFree86 X servers.
 .
 More information about X.Org can be found at:
 <URL:http://www.X.org>
 .
 This package is built from the X.org xserver module.
Original-Maintainer: Debian X Strike Force <debian-x@lists.debian.org>

```

---

### Post by Harry33 on 2011-10-27
> **ventrical said:**
> hey ..

ok .. will do .. in the meantime ... here->

dale@ubuntu:~/Downloads$ sudo dpkg -i nvidia-current_290.03-0ubuntu1~xedgers~oneiric1_i386.deb
[sudo] password for dale: 
Selecting previously unselected package nvidia-current.
(Reading database ... 314051 files and directories currently installed.)
Unpacking nvidia-current (from nvidia-current_290.03-0ubuntu1~xedgers~oneiric1_i386.deb) ...
dpkg: dependency problems prevent configuration of nvidia-current:
 nvidia-current depends on xorg-video-abi-11; however:
  Package xorg-video-abi-11 is not installed.
 nvidia-current depends on xserver-xorg-core (>= 2:1.10.99.901); however:
  Version of xserver-xorg-core on system is 2:1.10.4-1ubuntu5.
dpkg: error processing nvidia-current (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db ...
Errors were encountered while processing:
 nvidia-current
dale@ubuntu:~/Downloads$ 
So now what?

That is true.
Xorg-edgers does have nvidia-current build against video-abi-11-
That is you need to install xserver 1.11 and appropriate input drivers too.

---

### Post by effenberg0x0 on 2011-10-27
@Ventrical

But if you're just trying to get back to defaults, know that you can safely remove a ppa and it's packages to revert to standard using **sudo ppa-purge ppa:something/ppa/**

---

### Post by ventrical on 2011-10-27
> **paul_in_london said:**
> Posting this from PP 64 bit, but what do you get if you run this (see bit of the output highlighted in red)?

```
paul@precise-64:~$ apt-cache show xserver-xorg-core

Package: xserver-xorg-core
Priority: optional
Section: x11
Installed-Size: 4059
Maintainer: Ubuntu X-SWAT <ubuntu-x@lists.ubuntu.com>
Original-Maintainer: Debian X Strike Force <debian-x@lists.debian.org>
Architecture: amd64
Source: xorg-server
Version: 2:1.10.4-1ubuntu5
Provides: xorg-input-abi-12, xorg-video-abi-10
Depends: xserver-common (>= 2:1.10.4-1ubuntu5), keyboard-configuration, udev (>= 149), libc6 (>= 2.8), libdrm2 (>= 2.3.1), libgcrypt11 (>= 1.4.5), libpciaccess0 (>= 0.10.7), libpixman-1-0 (>= 0.15.16), libudev0 (>= 147), libxau6, libxdmcp6, libxfont1 (>= 1:1.4.2)
Recommends: libgl1-mesa-dri (>= 7.10.2-4)
Suggests: xfonts-100dpi | xfonts-75dpi, xfonts-scalable
Breaks: libgl1-mesa-dri (<< 7.10.2-4), libgl1-mesa-dri-experimental (<< 7.10.2-4), libgl1-mesa-dri-no-multiarch, xserver-xorg-input, xserver-xorg-input-2, xserver-xorg-input-2.1, xserver-xorg-input-4, xserver-xorg-input-7, xserver-xorg-input-joystick (<= 1:1.5.0-3), xserver-xorg-input-synaptics (<= 1.2.2-1ubuntu4), xserver-xorg-input-tslib (<= 0.0.6-3), xserver-xorg-input-vmmouse (<= 1:12.6.5-4ubuntu2), xserver-xorg-input-wacom (<= 0.10.5+20100415-1), xserver-xorg-video, xserver-xorg-video-1.0, xserver-xorg-video-1.9, xserver-xorg-video-2, xserver-xorg-video-4, xserver-xorg-video-5, xserver-xorg-video-6, xserver-xorg-video-cyrix (<= 1:1.1.0-8), xserver-xorg-video-i810 (<< 2:2.4), xserver-xorg-video-imstt (<= 1:1.1.0-7), xserver-xorg-video-nsc (<= 1:2.8.3-4), xserver-xorg-video-sunbw2 (<= 1:1.1.0-5), xserver-xorg-video-v4l (<< 1:0.2.0), xserver-xorg-video-vga (<= 1:4.1.0-8)
Filename: pool/main/x/xorg-server/xserver-xorg-core_1.10.4-1ubuntu5_amd64.deb
Size: 1695010
MD5sum: 6e731c03e4fdde0fc31d67ff488619fc
SHA1: b9a3650842ce4b0eb2b7de5efb60ccbf79b8e622
SHA256: 02303f3361cb7880aeffa77ec4ba0c7c794145f25ae736825435c197cf9fb0c5
Description-en: Xorg X server - core server
 The Xorg X server is an X server for several architectures and operating
 systems, which is derived from the XFree86 4.x series of X servers.
 .
 The Xorg server supports most modern graphics hardware from most vendors,
 and supersedes all XFree86 X servers.
 .
 More information about X.Org can be found at:
 <URL:http://www.X.org>
 .
 This package is built from the X.org xserver module.
Description-md5: e3826a765918b79dee4b90ec97f9302c
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
Supported: 18m
Task: ubuntu-desktop, ubuntu-usb, kubuntu-desktop, kubuntu-mobile-desktop, kubuntu-mobile, edubuntu-desktop, edubuntu-usb, xubuntu-desktop, mythbuntu-backend-master, mythbuntu-backend-slave, mythbuntu-desktop, mythbuntu-frontend, lubuntu-core, ubuntustudio-desktop

Package: xserver-xorg-core
Source: xorg-server
Priority: optional
Section: x11
Installed-Size: 4120
Maintainer: Ubuntu X-SWAT <ubuntu-x@lists.ubuntu.com>
Architecture: amd64
Version: 2:1.11.1.901+git20111024+server-1.11-branch.c8c5ed99-0ubuntu0sarvatt
Recommends: libgl1-mesa-dri (>= 7.10.2-4)
Suggests: xfonts-100dpi | xfonts-75dpi, xfonts-scalable
Provides: xorg-input-abi-13, **[COLOR=Red]xorg-video-abi-11[/COLOR]**
Depends: xserver-common (>= 2:1.11.1.901+git20111024+server-1.11-branch.c8c5ed99-0ubuntu0sarvatt), keyboard-configuration, udev (>= 149), libc6 (>= 2.8), libdrm2 (>= 2.3.1), libgcrypt11 (>= 1.5.0-0), libpciaccess0 (>= 0.10.7), libpixman-1-0 (>= 0.21.6), libudev0 (>= 147), libxau6, libxdmcp6, libxfont1 (>= 1:1.4.2)
Breaks: libgl1-mesa-dri (<< 7.10.2-4), libgl1-mesa-dri-experimental (<< 7.10.2-4), xserver-xorg-input, xserver-xorg-input-2, xserver-xorg-input-2.1, xserver-xorg-input-4, xserver-xorg-input-7, xserver-xorg-input-joystick (<= 1:1.5.0-3), xserver-xorg-input-synaptics (<= 1.2.2-1ubuntu4), xserver-xorg-input-tslib (<= 0.0.6-3), xserver-xorg-input-vmmouse (<= 1:12.6.5-4ubuntu2), xserver-xorg-input-wacom (<< 0.7.8), xserver-xorg-video, xserver-xorg-video-1.0, xserver-xorg-video-1.9, xserver-xorg-video-2, xserver-xorg-video-4, xserver-xorg-video-5, xserver-xorg-video-6, xserver-xorg-video-cyrix (<= 1:1.1.0-8), xserver-xorg-video-i810 (<< 2:2.4), xserver-xorg-video-imstt (<= 1:1.1.0-7), xserver-xorg-video-nsc (<= 1:2.8.3-4), xserver-xorg-video-sunbw2 (<= 1:1.1.0-5), xserver-xorg-video-v4l (<< 1:0.2.0), xserver-xorg-video-vga (<= 1:4.1.0-8)
Filename: pool/main/x/xorg-server/xserver-xorg-core_1.11.1.901+git20111024+server-1.11-branch.c8c5ed99-0ubuntu0sarvatt_amd64.deb
Size: 1744130
MD5sum: f33632c49de3b32bcc7712f190d436b7
SHA1: 16590143ba2bd705eeec9807a3e06b24290e3071
Description-en: Xorg X server - core server
 The Xorg X server is an X server for several architectures and operating
 systems, which is derived from the XFree86 4.x series of X servers.
 .
 The Xorg server supports most modern graphics hardware from most vendors,
 and supersedes all XFree86 X servers.
 .
 More information about X.Org can be found at:
 <URL:http://www.X.org>
 .
 This package is built from the X.org xserver module.
Original-Maintainer: Debian X Strike Force <debian-x@lists.debian.org>

```


```

dale@ubuntu:~$ apt-cache show xserver-xorg-core
Package: xserver-xorg-core
Priority: optional
Section: x11
Installed-Size: 4110
Maintainer: Ubuntu X-SWAT <ubuntu-x@lists.ubuntu.com>
Original-Maintainer: Debian X Strike Force <debian-x@lists.debian.org>
Architecture: i386
Source: xorg-server
Version: 2:1.10.4-1ubuntu5
Provides: xorg-input-abi-12, xorg-video-abi-10
Depends: xserver-common (>= 2:1.10.4-1ubuntu5), keyboard-configuration, udev (>= 149), libc6 (>= 2.8), libdrm2 (>= 2.3.1), libgcrypt11 (>= 1.4.5), libpciaccess0 (>= 0.10.7), libpixman-1-0 (>= 0.15.16), libudev0 (>= 147), libxau6, libxdmcp6, libxfont1 (>= 1:1.4.2)
Recommends: libgl1-mesa-dri (>= 7.10.2-4)
Suggests: xfonts-100dpi | xfonts-75dpi, xfonts-scalable
Breaks: libgl1-mesa-dri (<< 7.10.2-4), libgl1-mesa-dri-experimental (<< 7.10.2-4), libgl1-mesa-dri-no-multiarch, xserver-xorg-input, xserver-xorg-input-2, xserver-xorg-input-2.1, xserver-xorg-input-4, xserver-xorg-input-7, xserver-xorg-input-joystick (<= 1:1.5.0-3), xserver-xorg-input-synaptics (<= 1.2.2-1ubuntu4), xserver-xorg-input-tslib (<= 0.0.6-3), xserver-xorg-input-vmmouse (<= 1:12.6.5-4ubuntu2), xserver-xorg-input-wacom (<= 0.10.5+20100415-1), xserver-xorg-video, xserver-xorg-video-1.0, xserver-xorg-video-1.9, xserver-xorg-video-2, xserver-xorg-video-4, xserver-xorg-video-5, xserver-xorg-video-6, xserver-xorg-video-cyrix (<= 1:1.1.0-8), xserver-xorg-video-i810 (<< 2:2.4), xserver-xorg-video-imstt (<= 1:1.1.0-7), xserver-xorg-video-nsc (<= 1:2.8.3-4), xserver-xorg-video-sunbw2 (<= 1:1.1.0-5), xserver-xorg-video-v4l (<< 1:0.2.0), xserver-xorg-video-vga (<= 1:4.1.0-8)
Filename: pool/main/x/xorg-server/xserver-xorg-core_1.10.4-1ubuntu5_i386.deb
Size: 1667610
MD5sum: e6899823ee4f2dbf351b69a8d0df59eb
SHA1: 2c3be27ef41bb05b64ec526b9e924d73650cf1a8
SHA256: 6cba9a055194d11482fb02feab33e6ef7596693c431a48b84e60528419f7085d
Description-en: Xorg X server - core server
 The Xorg X server is an X server for several architectures and operating
 systems, which is derived from the XFree86 4.x series of X servers.
 .
 The Xorg server supports most modern graphics hardware from most vendors,
 and supersedes all XFree86 X servers.
 .
 More information about X.Org can be found at:
 <URL:http://www.X.org>
 .
 This package is built from the X.org xserver module.
Description-md5: e3826a765918b79dee4b90ec97f9302c
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
Supported: 18m
Task: ubuntu-desktop, ubuntu-usb, kubuntu-desktop, kubuntu-mobile-desktop, kubuntu-mobile, edubuntu-desktop, edubuntu-usb, xubuntu-desktop, mythbuntu-backend-master, mythbuntu-backend-slave, mythbuntu-desktop, mythbuntu-frontend, lubuntu-core, ubuntustudio-desktop

dale@ubuntu:~$ 

```

---

### Post by ventrical on 2011-10-27
> **effenberg0x0 said:**
> @Ventrical

But if you're just trying to get back to defaults, know that you can safely remove a ppa and it's packages to revert to standard using **sudo ppa-purge ppa:something/ppa/**


Hmmmm.. perhaps this may be the course to take because I certainly do not want to cause anybody to have any down_time over all this. Simply, I could do a fresh install, but that's the easy way out. anyways .. it may be wise to pocket my stubborness and remove those ppas ... so I'm open to suggestions. I have the Cairo-Dock ppas and mabey that what the prob is. All my other PP installs work great.

  I'm open also to suggestions .. if I can get whatever I got to get ironed out .. or mabey purge those PPAs and then re-install them..

thanks again..

---

### Post by ventrical on 2011-10-27
> **Harry33 said:**
> That is true.
Xorg-edgers does have nvidia-current build against video-abi-11-
That is you need to install xserver 1.11 and appropriate input drivers too.


Yes ,, this seems ot be the problem .. unexpected by me of course. I assumed installing the new nvidia drivers would all that would be required .. but looks like more stuff :)

---

### Post by ventrical on 2011-10-27
> **effenberg0x0 said:**
> @Ventrical

But if you're just trying to get back to defaults, know that you can safely remove a ppa and it's packages to revert to standard using **sudo ppa-purge ppa:something/ppa/**

So....I remove these  and go back to standard ... ?

---

### Post by effenberg0x0 on 2011-10-27
> **ventrical said:**
>  or mabey purge those PPAs and then re-install them.

As a rule, I try to keep the machines that will be used by other people as standard as possible, with some small tweaks of course, but using the standard packages from main repos. Then I have test machines in which we can play with non-standard stuff, test, etc. 

If you're just trying to create a setup that will give you as little headaches as possible, I'd purge non standard PPAs and run that reinstall command I gave you, to make it download those packages from the standard Precise repos. From there, you can install nvidia proprietary easily and get the thing working ok.

Then you use your machine or test machines to play with the edgy stuff :)

---

### Post by ventrical on 2011-10-27
> **effenberg0x0 said:**
> As a rule, I try keep the machines that will be used by other people as standard as possible, with some small tweaks of course, but using the standard packages from main repos. Then I have test machines in which we can play with non-standard stuff, test, etc. 

If you're just trying to create a setup that will give you as little headaches as possible, I'd purge non standard PPAs and run that reinstall command I gave you, to make it download those packages from the standard Precise repos. From there, you can install nvidia proprietary easily and get the thing working ok.

Then you use your machine or test machines to play with the edgy stuff :)

I have three beta test machines to spare .. I have been at this for several decades .. so I'm not worried about borking a machine. My original training was in UNIX. I was invited in 1991 to join Linus Torvalds and the Linux group through FIDO_NET but I declined because I had decided to go into internet security (which is a rotten job). Mostly all Windows based machines. 2 years ago i took up Ubuntu but just most recently in an applied manner.

  I like the Ubuntu concept and I like beta testing - squeezing everything I can. I am a CODE e-junkie but with the linux structure.. well.. I'm catching on. :)

peace .. and thanks.. I'll do that purge
.. but  first .. suppertime  :)

---

### Post by effenberg0x0 on 2011-10-27
I'm not sure what happens when you simply uncheck the ppa from sources. The way I know how to do it is to use sudo ppa-purge, like sudo ppa-purge ppa:xorg-edgers/ppa

Using ppa-purge, the packages installed by that ppa are uninstalled.

---

### Post by effenberg0x0 on 2011-10-27
> **ventrical said:**
> I was invited in 1991 to join Linus Torvalds and the Linux group through FIDO_NET but I declined 

What an opportunity... I wish I could have a 30 minute talk with the guy, that would be enough.

---

### Post by ventrical on 2011-10-27
> **effenberg0x0 said:**
> What an opportunity... I wish I could have a 30 minute talk with the guy, that would be enough.


Didn't talk to him directly. Just a query from one of the group members on FIDO.  The early years. One would think with my UNIX training that it would all make sense to me...but we learn new stuff everyday..

btw  I get an error with the sudo ppa-purge .. etc.. command not found - so  I removed them using synaptic - reboot time.

 :) ..

---

### Post by effenberg0x0 on 2011-10-27
> **ventrical said:**
> Didn't talk to him directly. Just a query from one of the group members on FIDO.  The early years. One would think with my UNIX training that it would all make sense to me...but we learn new stuff everyday..

btw  I get an error with the sudo ppa-purge .. etc.. command not found - so  I removed them using synaptic - reboot time.

 :) ..

I'm not sure ppa-purge is installed by default, maybe not.
The only difference is that you'll have to reinstall the needed packages from default repos anyway.

```
[07:13 ][al:AL-DESK:~/dev/workspace/tesseract/Debug]
$ sudo apt-cache search ppa-purge
[sudo] password for al: 
ppa-purge - disables a PPA and reverts to official packages
```

---

### Post by paul_in_london on 2011-10-27
> **ventrical said:**
> Didn't talk to him directly. Just a query from one of the group members on FIDO.  The early years. One would think with my UNIX training that it would all make sense to me...but we learn new stuff everyday..

btw  I get an error with the sudo ppa-purge .. etc.. command not found - so  I removed them using synaptic - reboot time.

 :) ..

You should get it if you install python-software-properties :)

EDIT: Sorry, was thinking of add-apt-repository.

---

### Post by cariboo on 2011-10-27
ppa-purge isn't installed by default, but it is great way to revert to default packages, as it removes packages installed via a ppa, and replaces them with the equivalent from the repositories, if they are available. For example if you have the xorg-edgers ppa setup, and run the command it will remove xorg and whatever graphics driver you use, and replace them with packages from the repositories.

---

### Post by ventrical on 2011-10-27
> **cariboo907 said:**
> ppa-purge isn't installed by default, but it is great way to revert to default packages, as it removes packages installed via a ppa, and replaces them with the equivalent from the repositories, if they are available. For example if you have the xorg-edgers ppa setup, and run the command it will remove xorg and whatever graphics driver you use, and replace them with packages from the repositories.


ahh yes ...  I see that now in synaptic.

thanks caribou907

---

### Post by ventrical on 2011-10-28
Ok... ppa-purge went beautifully. I even got gnome-screenshot to work. One prob though .

I am just wondering if I have to re-edit my sources list?

---

### Post by effenberg0x0 on 2011-10-28
> **ventrical said:**
> Ok... ppa-purge went beautifully. I even got gnome-screenshot to work. One prob though .

I am just wondering if I have to re-edit my sources list?

Good morning,

No, have a look at your /etc/apt/sources.list.d/* . The alternate PPAs are there. The default sources are all inside one single file, which is /etc/apt/sources.list. If you're managing to use sudo apt-get update && sudo apt-get upgrade (with no ppa files in the directory I mentioned), it means you have a working default sources.list.

Check my sources.list and compare to your if you're in doubt:

```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://archive.ubuntu.com/ubuntu precise main restricted
deb-src http://archive.ubuntu.com/ubuntu precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu precise-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu precise universe
deb-src http://archive.ubuntu.com/ubuntu precise universe
deb http://archive.ubuntu.com/ubuntu precise-updates universe
deb-src http://archive.ubuntu.com/ubuntu precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu precise multiverse
deb-src http://archive.ubuntu.com/ubuntu precise multiverse
deb http://archive.ubuntu.com/ubuntu precise-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu precise-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu precise-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu precise-security main restricted
deb-src http://archive.ubuntu.com/ubuntu precise-security main restricted
deb http://archive.ubuntu.com/ubuntu precise-security universe
deb-src http://archive.ubuntu.com/ubuntu precise-security universe
deb http://archive.ubuntu.com/ubuntu precise-security multiverse
deb-src http://archive.ubuntu.com/ubuntu precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu natty partner
# deb-src http://archive.canonical.com/ubuntu natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb http://extras.ubuntu.com/ubuntu precise main
# deb-src http://extras.ubuntu.com/ubuntu precise main

```

---

### Post by ventrical on 2011-10-28
So I am just wondering how to get synaptic back working -(because of that error it will not work) .

```
# 

# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Beta i386 (20110901)]/ precise main restricted

# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Beta i386 (20110901)]/ precise main restricted

deb http://security.ubuntu.com/ubuntu precise-security main restricted
deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
deb http://security.ubuntu.com/ubuntu precise-security universe
deb-src http://security.ubuntu.com/ubuntu precise-security universe
deb http://security.ubuntu.com/ubuntu precise-security multiverse
deb-src http://security.ubuntu.com/ubuntu precise-security multiverse

## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu precise partner
deb-src http://archive.canonical.com/ubuntu precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb http://archive.ubuntu.com/ubuntu precise main universe restricted multiverse
deb http://archive.ubuntu.com/ubuntu precise-updates universe main multiverse restricted
deb-src http://extras.ubuntu.com/ubuntu precise main
deb http://archive.ubuntu.com/ubuntu precise-proposed universe main multiverse restricted
deb http://archive.ubuntu.com/ubuntu precise-backports universe main multiverse restricted
# deb http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu oneiric main
# deb-src http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu oneiric main
# deb http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu precise main
# deb-src http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu precise main
```


otherwise .. the system is working good after reboot. Only problem .. still do not have the application unity icon in Unity 3D.


thanks..

---

### Post by zika on 2011-10-28
Did You do this: [http://ubuntuforums.org/showpost.php?p=11347739&postcount=14](http://ubuntuforums.org/showpost.php?p=11347739&postcount=14) ...?

---

### Post by ventrical on 2011-10-28
I already have this :

```
ChangelogURI: [http://changelogs.ubuntu.com/changelogs/pool/%s/%s/%s/%s_%s/changelog]("http://changelogs.ubuntu.com/changelogs/pool/%s/%s/%s/%s_%s/changelog")

Suite: precise
RepositoryType: deb
BaseURI: [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/)
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)
MatchURI-amd64: archive.ubuntu.com/ubuntu
BaseURI-i386: [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)
MatchURI-i386: archive.ubuntu.com/ubuntu
MirrorsFile-amd64: Ubuntu.mirrors
MirrorsFile-i386: Ubuntu.mirrors
Description: Ubuntu 12.04 'Precise Pangolin'
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported Open Source software
Component: universe
CompDescription: Community-maintained
CompDescriptionLong: Community-maintained Open Source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
ParentComponent: universe
CompDescription: Restricted software
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: precise
ParentSuite: precise
RepositoryType: deb-src
BaseURI: [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Ubuntu 12.04 'Precise Pangolin'

Suite: precise
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*12.04
MatchURI: cdrom:\[Ubuntu.*12.04
Description: Cdrom with Ubuntu 12.04 'Precise Pangolin'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: precise
Official: false
RepositoryType: deb
BaseURI: [http://archive.canonical.com](http://archive.canonical.com)
MatchURI: archive.canonical.com
Description: Canonical Partners
Component: partner
CompDescription: Software packaged by Canonical for their partners
CompDescriptionLong: This software is not part of Ubuntu.

Suite: precise
Official: false
RepositoryType: deb
BaseURI: [http://extras.ubuntu.com](http://extras.ubuntu.com)
MatchURI: extras.ubuntu.com
Description: Independent
Component: main
CompDescription: Provided by third-party software developers
CompDescriptionLong: Software offered by third party developers.

Suite: precise-security
ParentSuite: precise
RepositoryType: deb
BaseURI: [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/)
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/)
MatchURI-amd64: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-i386: [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/)
MatchURI-i386: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: precise-security
ParentSuite: precise
RepositoryType: deb-src
BaseURI: [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports|security.ubuntu.com
Description: Important security updates

Suite: precise-updates
ParentSuite: precise
RepositoryType: deb
Description: Recommended updates

Suite: precise-updates
ParentSuite: precise
RepositoryType: deb-src
BaseURI: [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Recommended updates

Suite: precise-proposed
ParentSuite: precise
RepositoryType: deb
Description: Pre-released updates

Suite: precise-proposed
ParentSuite: precise
RepositoryType: deb-src
BaseURI: [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Pre-released updates

Suite: precise-backports
ParentSuite: precise
RepositoryType: deb
Description: Unsupported updates

Suite: precise-backports
ParentSuite: precise
RepositoryType: deb-src
BaseURI: [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Unsupported updates
```


but I guess I'll try it. Sources List is working .. but just not synaptic. ok here goes.. cut and paste..

---

### Post by ventrical on 2011-10-28
> **zika said:**
> Did You do this: [http://ubuntuforums.org/showpost.php?p=11347739&postcount=14](http://ubuntuforums.org/showpost.php?p=11347739&postcount=14) ...?


Nope .. didn't work zika

thanks anyways..

---

### Post by zika on 2011-10-28
> **ventrical said:**
> I already have this :

```
ChangelogURI: [http://changelogs.ubuntu.com/changelogs/pool/%s/%s/%s/%s_%s/changelog](http://changelogs.ubuntu.com/changelogs/pool/%s/%s/%s/%s_%s/changelog)

Suite: precise
RepositoryType: deb
BaseURI: [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/)
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)
MatchURI-amd64: archive.ubuntu.com/ubuntu
BaseURI-i386: [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)
MatchURI-i386: archive.ubuntu.com/ubuntu
MirrorsFile-amd64: Ubuntu.mirrors
MirrorsFile-i386: Ubuntu.mirrors
Description: Ubuntu 12.04 'Precise Pangolin'
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported Open Source software
Component: universe
CompDescription: Community-maintained
CompDescriptionLong: Community-maintained Open Source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
ParentComponent: universe
CompDescription: Restricted software
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: precise
ParentSuite: precise
RepositoryType: deb-src
BaseURI: [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Ubuntu 12.04 'Precise Pangolin'

Suite: precise
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*12.04
MatchURI: cdrom:\[Ubuntu.*12.04
Description: Cdrom with Ubuntu 12.04 'Precise Pangolin'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: precise
Official: false
RepositoryType: deb
BaseURI: [http://archive.canonical.com](http://archive.canonical.com)
MatchURI: archive.canonical.com
Description: Canonical Partners
Component: partner
CompDescription: Software packaged by Canonical for their partners
CompDescriptionLong: This software is not part of Ubuntu.

Suite: precise
Official: false
RepositoryType: deb
BaseURI: [http://extras.ubuntu.com](http://extras.ubuntu.com)
MatchURI: extras.ubuntu.com
Description: Independent
Component: main
CompDescription: Provided by third-party software developers
CompDescriptionLong: Software offered by third party developers.

Suite: precise-security
ParentSuite: precise
RepositoryType: deb
BaseURI: [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/)
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/)
MatchURI-amd64: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-i386: [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/)
MatchURI-i386: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: precise-security
ParentSuite: precise
RepositoryType: deb-src
BaseURI: [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports|security.ubuntu.com
Description: Important security updates

Suite: precise-updates
ParentSuite: precise
RepositoryType: deb
Description: Recommended updates

Suite: precise-updates
ParentSuite: precise
RepositoryType: deb-src
BaseURI: [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Recommended updates

Suite: precise-proposed
ParentSuite: precise
RepositoryType: deb
Description: Pre-released updates

Suite: precise-proposed
ParentSuite: precise
RepositoryType: deb-src
BaseURI: [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Pre-released updates

Suite: precise-backports
ParentSuite: precise
RepositoryType: deb
Description: Unsupported updates

Suite: precise-backports
ParentSuite: precise
RepositoryType: deb-src
BaseURI: [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Unsupported updates
```


but I guess I'll try it. Sources List is working .. but just not synaptic. ok here goes.. cut and paste..
It seems that You've done that already...

---

### Post by zika on 2011-10-28
I've had similar misbehaving Synaptic for the first few minutes while in Precise, I do not, really, remember how I did make it behave... I'll try to find notes in my notebook...

---

### Post by ventrical on 2011-10-28
I can call synaptic from terminal but it will not allow me permissions... it is not reall that big of prob .. considering that this install was nearer to the scrapheap than most other installs :)

---

### Post by effenberg0x0 on 2011-10-28
Purge synaptic:
```
sudo apt-get remove --purge synaptic
```Remove (backup) synaptic prefs for you and root:
```
sudo mv ~/.synaptic ~/.synaptic.backup
sudo mv /root/.synaptic /root/.synaptic.backup 
```Replace instances of "Oneiric" from sources.list for "Precise" to a new sources.list:
```
sudo cat /etc/apt/sources.list | sed -e 's|oneiric|precise|' | sudo tee /etc/apt/sources.list.new
```Backup current sources.list:
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
```Move new sources.list in:
```
sudo mv /etc/apt/sources.list.new /etc/apt/sources.list 
```Remove (Backup) non-standard ppa sources:
```
sudo mv /etc/apt/sources.list.d /etc/apt/sources.list.d.backup
```Update apt:
```
sudo apt-get update
```Reinstall Synaptic:
```
sudo apt-get install synaptic
```Run synaptic:
```
sudo synaptic as root, so we don't start with mixed prefs location between user and root
```

---

### Post by effenberg0x0 on 2011-10-28
Now that I think about it, we used sed to replace Oneiric for Precise in sources.list. But I guess it wouldn't hurt for you to manually gedit the file, after that step, and see if you have other wrong stuff in there, like something mentioning Natty, other non-standard repos, etc. Then you proceed with the following steps... 

Also, as we disabled your non-standard PPAs (which are backed up under /etc/apt/sources.list.d), but we have not properly purged the packages it installed, you may want to go to that dir and purge each ppa-purge you have there. Otherwise it will bore you to do a sudo apt-get upgrade and see that you may be running packages with unmet dependencies.

---

### Post by ventrical on 2011-10-28
I'm just in now . I saved my current sources.list (backed-up) and copy and pasted your sources.list. Did not work. Everything is working fine. Actually it is a lot faster and snappier. 

  I am about to try your most recent instructions.

  I tired zika's method but that did not work either. I also backed up my original ubuntu.info file from there.

I'll check in shortly.

---

### Post by ventrical on 2011-10-28
> **effenberg0x0 said:**
> Now that I think about it, we used sed to replace Oneiric for Precise in sources.list. But I guess it wouldn't hurt for you to manually gedit the file, after that step, and see if you have other wrong stuff in there, like something mentioning Natty, other non-standard repos, etc. Then you proceed with the following steps... 

Also, as we disabled your non-standard PPAs (which are backed up under /etc/apt/sources.list.d), but we have not properly purged the packages it installed, you may want to go to that dir and purge each ppa-purge you have there. Otherwise it will bore you to do a sudo apt-get upgrade and see that you may be running packages with unmet dependencies.


Thats pretty well clean:

root@ubuntu:~# cd /etc/apt/
root@ubuntu:/etc/apt# dir
apt.conf.d     sources.list~          sources.list.save  trusted.gpg~
preferences.d  sources.list.backup    trustdb.gpg     trusted.gpg.d
sources.list   sources.list.d.backup  trusted.gpg
root@ubuntu:/etc/apt# 


but I still get that pop-up

---

### Post by effenberg0x0 on 2011-10-28
> **effenberg0x0 said:**
>  Also, as we disabled your non-standard PPAs (which are backed up under  /etc/apt/sources.list.d), but we have not properly purged the packages  it installed, you may want to go to that dir and purge each ppa-purge  you have there. Otherwise it will bore you to do a sudo apt-get upgrade  and see that you may be running packages with unmet  dependencies.

About purging non-standard ppas (the ones that are stored in /etc/sources.list.d). I thought it could be a good idea to automatize it.

**EDIT**: This will copy from /etc/apt/sources.list,d or /etc/apt/sources.list.d.backup to the standard location, so we can proceed with purging process. As I can't predict the order in which commands are executed, you may or may not have already moved sources.list.d to a backup directory. This is a workaround. ```

cd /etc/apt/
if [ -d /etc/apt/sources.list.d.backup -a -d /etc/apt/sources.list.d ]; then sudo cp -axR /etc/apt/sources.list.d.backup/* /etc/apt/sources.list.d/; else sudo mkdir /etc/apt/sources.list.d && sudo cp -axR /etc/apt/sources.list.d.backup/* /etc/apt/sources.list.d/; fi
  
```This will read every file in that directory and translate its contents to the **ppa:someone/some_package** format, so that it can be used with the ppa-purge command. The list of PPAs in the correct format will be saved to file ppa_file.txt

```
for PPA_FILE in $(ls /etc/apt/sources.list.d/*); do sudo cat $PPA_FILE | grep "deb http" | sed -e 's|deb http://||' | sed -e 's|.launchpad.net/|\:|' | sed -e 's|/ubuntu||' | sed -e 's|natty||' | sed -e 's|maverick||' | sed -e 's|oneiric||' | sed -e 's|main||' | sudo tee -a /etc/apt/sources.list.d/ppa_file.txt; done
```Then one can simply open that file (ppa_file.txt) and do a ppa-purge of each ppa:someone/some_package line of the file or, more simply, run this:

```
for PPA in $(sudo cat /etc/apt/sources.list.d/ppa_file.txt); do sudo /usr/sbin/ppa-purge $PPA; done
```It's up to you if and when to purge your non-default PPAs and non-standard packages anyway. If you go for it, run sudo apt-get update after purging and you'll have to install the standard versions of the now missing (purged) packages. But it would be the best way to get back to defaults.

---

### Post by ventrical on 2011-10-28
I'll look at those files a little later I know whats wrong .. I just forget :)

---

### Post by effenberg0x0 on 2011-10-28
That is weird... The APT::Default-Release identifier is within Synaptic config file at each home directory (for you and root). I have recreated this error by manually editing those files. And the instructions I gave to you would purge synaptic, get rid of the old config files and reinstall synaptic... So I can't understand how and from where your newly installed synaptic might still be getting a wrong config (considering its been wiped of the system).

Look, just so I don't get confused, you do have this as the output for lsb_release, right?
```
[04:57 ][al:AL-DESK:~/downloads/vmware-player]
$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
[B]Description:    Ubuntu precise (development branch)
Release:    12.04
Codename:    precise[/B]

```**EDIT:** Hold on, I'm studying a viable solution.

---

### Post by ventrical on 2011-10-28
dale@ubuntu:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu precise (development branch)
Release:    12.04
Codename:    precise
dale@ubuntu:~$

---

### Post by effenberg0x0 on 2011-10-28
sudo apt-config dump gives me nothing about the default-release.
It's not anywhere in /etc/apt/*
It's not in ~.*
**EDIT:** Not in environment variables too.

I can only associate this setting as coming from the .synaptic/synaptic.conf files for each user, which I already gave you code above to get rid off, so it can't come from these files. And the code I suggested above would also purge/reinstall synaptic, so it should reset configs.

Your lsb_release is correct. Your sources.list also seem to be fine.

So, because of the lack of options, I'm scanning mostly all files in my desktop to search for the origin of this default-release setting.

```

sudo -s
grep -iHnR --binary-files=without-match --exclude-dir=/bin --exclude-dir=/boot --exclude-dir=/cdrom --exclude-dir=/dev --exclude-dir=/lib --exclude-dir=/lib32 --exclude-dir=/lib64 --exclude-dir=/lost+found --exclude-dir=/media --exclude-dir=/mnt --exclude-dir=/proc --exclude-dir=/sys --exclude=vmlinuz* "default-release" / | tee /home/al/dev/search-results.txt
```It will take a while... But eventually I'll find it.

---

### Post by ventrical on 2011-10-28
Here is my original sources.list. I was an original Oneiric beta install as you will see.

# 

# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Beta i386 (20110901)]/ precise main restricted

# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Beta i386 (20110901)]/ precise main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse

## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise main universe restricted multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates universe main multiverse restricted
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-proposed universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-backports universe main multiverse restricted
# deb [http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu](http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu) oneiric main
# deb-src [http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu](http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu) oneiric main
# deb [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) precise main
# deb-src [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) precise main

---

### Post by effenberg0x0 on 2011-10-28
> **ventrical said:**
> Here is my original sources.list. I was an original Oneiric beta install as you will see.

# 

# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Beta i386 (20110901)]/ precise main restricted

# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Beta i386 (20110901)]/ precise main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse

## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise main universe restricted multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates universe main multiverse restricted
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-proposed universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-backports universe main multiverse restricted
# deb [http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu](http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu) oneiric main
# deb-src [http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu](http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu) oneiric main
# deb [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) precise main
# deb-src [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) precise main

Yes, and the uncommented lines refer to precise repos. It is correct.
Do you have any error when you run sudo apt-get update?

---

### Post by ventrical on 2011-10-28
> **effenberg0x0 said:**
> sudo apt-config dump gives me nothing about the default-release.
It's not anywhere in /etc/apt/*
It's not in ~.*
**EDIT:** Not in environment variables too.

I can only associate this setting as coming from the .synaptic/synaptic.conf files for each user, which I already gave you code above to get rid off, so it can't come from these files. And the code I suggested above would also purge/reinstall synaptic, so it should reset configs.

Your lsb_release is correct. Your sources.list also seem to be fine.

So, because of the lack of options, I'm scanning mostly all files in my desktop to search for the origin of this default-release setting.

```

sudo -s
grep -iHnR --binary-files=without-match --exclude-dir=/bin --exclude-dir=/boot --exclude-dir=/cdrom --exclude-dir=/dev --exclude-dir=/lib --exclude-dir=/lib32 --exclude-dir=/lib64 --exclude-dir=/lost+found --exclude-dir=/media --exclude-dir=/mnt --exclude-dir=/proc --exclude-dir=/sys --exclude=vmlinuz* "default-release" / | tee /home/al/dev/search-results.txt
```It will take a while... But eventually I'll find it.

  I am running the same code.

  I seen this fly by and captured it -

grep: /usr/share/doc/libsdl1.2debian/README-SDL.txt: No such file or directory
grep: /usr/share/doc/libsdl1.2debian/CREDITS: No such file or directory
/usr/share/doc/aptitude/README:8201:      This corresponds to the configuration item APT::Default-Release.

---

### Post by effenberg0x0 on 2011-10-28
> **ventrical said:**
> I am running the same code.

  I seen this fly by and captured it -

grep: /usr/share/doc/libsdl1.2debian/README-SDL.txt: No such file or directory
grep: /usr/share/doc/libsdl1.2debian/CREDITS: No such file or directory
/usr/share/doc/aptitude/README:8201:      This corresponds to the configuration item APT::Default-Release.

Yes :) that one was hidden...

Try first at apt.conf.d directory
```
cd /etc/apt/apt.conf.d
sudo grep -iHn "default-release"
```

If you get no results, try one level up:
```

cd /etc/apt
sudo grep -iHn "default-release"
```

You can also check preferences.d directory
```
cd /etc/apt/preferences.d
sudo grep -iHn "default-release"
```


I have no results (I don't have synaptic, update-manager, update-notifier and some more apt stuff installed). But you'll probably get the name of the file / line number in which default-release is set.

---

### Post by ventrical on 2011-10-28
> **effenberg0x0 said:**
> Yes :) that one was hidden...

Try first at apt.conf.d directory
```
cd /etc/apt/apt.conf.d
sudo grep -iHn "default-release"
```If you get no results, try one level up:
```

cd /etc/apt
sudo grep -iHn "default-release"
```You can also check preferences.d directory
```
cd /etc/apt/preferences.d
sudo grep -iHn "default-release"
```
I have no results (I don't have synaptic, update-manager, update-notifier and some more apt stuff installed). But you'll probably get the name of the file / line number in which default-release is set.


Actually , when I went to that Readme file it was a manual on 'Aptitude' so I read it a bit and decided to run it in terminal and downloaded all the new kernel images - so I can use 'aptitude' for now .. however, i will try those commands you mentioned.

---

### Post by ventrical on 2011-10-28
> **effenberg0x0 said:**
> Yes :) that one was hidden...

Try first at apt.conf.d directory
```
cd /etc/apt/apt.conf.d
sudo grep -iHn "default-release"
```If you get no results, try one level up:
```

cd /etc/apt
sudo grep -iHn "default-release"
```You can also check preferences.d directory
```
cd /etc/apt/preferences.d
sudo grep -iHn "default-release"
```
I have no results (I don't have synaptic, update-manager, update-notifier and some more apt stuff installed). But you'll probably get the name of the file / line number in which default-release is set.


The command  <sudo grep -iHn> (with arguments)  just hung the terminal.

---

### Post by effenberg0x0 on 2011-10-28
> **ventrical said:**
> The command  <sudo grep -iHn> (with arguments)  just hung the terminal.

lol, well, this is  weird. You ran it when you were searching for any occurrence of the "default-release" :)

EDIT: Ah... My mistake, sorry. Add a space and an asterisk after each command. Like sudo grep -iHn "default-release" *

Sorry, doing a zillion things at once here...

---

### Post by ventrical on 2011-10-28
> **effenberg0x0 said:**
> lol, well, this is  weird. You ran it when you were searching for any occurrence of the "default-release" :)

EDIT: Ah... My mistake, sorry. Add a space and an asterisk after each command. Like sudo grep -iHn "default-release" *

Sorry, doing a zillion things at once here...


Nothing . no such file or directory..


I ran aptitude after I read the manual and the search had completed.

Stay busy with your other projects ..and I'm going to take a look at some more aptitude.. :)

---

### Post by effenberg0x0 on 2011-10-28
Man, I was absolutely sure you'd find the default-release setting under those directories... 
I'm really lost this time as to where those settings are coming from.

---

### Post by ventrical on 2011-10-28
> **effenberg0x0 said:**
> Man, I was absolutely sure you'd find the default-release setting under those directories... 
I'm really lost this time as to where those settings are coming from.



 I got er done !! :):):)




[https://answers.launchpad.net/ubuntu/+source/synaptic/+question/174349](https://answers.launchpad.net/ubuntu/+source/synaptic/+question/174349)

Pretty well completely restored busted system.! 

  I just changed 'oneiric' to 'precise'  !!

 I'm going to print this one out for sure .

ehaehaheae

 Have a great night effen

thanks again to everybody

---

### Post by mc4man on 2011-10-28
That may have been intended in post 71, -  possibly the command (there) was incomplete..

---

### Post by ventrical on 2011-10-28
> **mc4man said:**
> That may have been intended in post 71, -  possibly the command (there) was incomplete..


I would not have thought to edit the synaptic.conf in that directory .  I'm thankful to the person who initially filed that bug report.

 Thanks to all of you also for sticking it out. There were a few times I was just ready to pack it in and do a fresh install  but I thought I would perservere on this one. My bread and butter comes from fixing busted mS OS systems and I do not always have the opportunity to do fresh installs .. so I had learned to search out the tools needed to clean those systems as promptly and quickly  as possible.  In most of those cases , I'm on my own... but i would sure like to comment on the diverse and bright helpers here at Ubuntu Forums. Team work pays off . I just hope some of you can analyze some of the data and consider writing a more automated batch - because it borders on functioning like a system restore concept and that would be good for newer users to have that option in the Grub Menu.

Thanks again Mc4man

---

### Post by effenberg0x0 on 2011-10-28
> **mc4man said:**
> That may have been intended in post 71, -  possibly the command (there) was incomplete..

It may very well be... I admit to not having tested my scripts thoroughly today. I've been doing too much at the same time here, couldn't manage to focus as I normally do. Not to mention its 38°C and I'm dying of the heat wave. And it's been two days I'm getting beat by vmware-player 4, editing its vmmon headers by hand, then eclipse crashed on me out of nothing and I lost code, etc... a not so nice day lol...

Let me just open an exception for post #75 (auto convert from sources.list.d/* deb.yadayada to ppa:something format and purge), which I think it's a beauty, really enjoyed the idea. The code, of course, needs improvement (the chain of sed is ridiculous). But that one I tested and added to my snippets... :)

Glad it all worked out in the end :)

---

### Post by effenberg0x0 on 2011-10-28
> **ventrical said:**
> I would not have thought to edit the synaptic.conf in that directory .  I'm thankful to the person who initially filed that bug report.

 Thanks to all of you also for sticking it out. There were a few times I was just ready to pack it in and do a fresh install  but I thought I would perservere on this one. My bread and butter comes from fixing busted mS OS systems and I do not always have the opportunity to do fresh installs .. so I had learned to search out the tools needed to clean those systems as promptly and quickly  as possible.  In most of those cases , I'm on my own... but i would sure like to comment on the diverse and bright helpers here at Ubuntu Forums. Team work pays off . I just hope some of you can analyze some of the data and consider writing a more automated batch - because it borders on functioning like a system restore concept and that would be good for newer users to have that option in the Grub Menu.

Thanks again Mc4man

Challenges are fun :)

Ubuntu automated restore / Restoration point accessible via Grub / Bulletproof install-boot and Proactive System CHeck/Fix = My project :) I'll post details one of these days.

---

### Post by zika on 2011-10-29
> **effenberg0x0 said:**
> Purge synaptic:
```
sudo synaptic as root, so we don't start with mixed prefs location between user and root
```Shouldn't here be **gksu** instead of **sudo**?

---

### Post by ventrical on 2011-10-29
All in all it worked out really good. Getting the desktop back was the hardest part. Synaptic conf file was a tough one to get , to track that one down.

Thanks zika

---

