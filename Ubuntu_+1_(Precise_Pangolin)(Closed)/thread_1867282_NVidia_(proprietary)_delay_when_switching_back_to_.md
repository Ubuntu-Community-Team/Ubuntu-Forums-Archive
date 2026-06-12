---
title: "NVidia (proprietary) delay when switching back to VT7 on PP"
date: 2011-10-22
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by effenberg0x0 on 2011-10-22
A question for Nvidia proprietary drivers users: Do you have a considerable delay when switching back to X (Unity) from any VT? 

Example:
- Start Unity Session
- Switch to VT1 (very small delay, like 2 second before seeing console text)
- Switch to VT7 (very big delay, like 10-15 seconds before you can see the desktop)

I'm pretty sure this was fixed on Oneiric, but I'm seeing it again on PP using any proprietary driver version (tested 280.13, 285.03, 285.05.09, 290.03).

Since we don't get KMS support on proprietary, I am using a uvesafb framebuffer. My kernel line is:
```
GRUB_CMDLINE_LINUX_DEFAULT="video=uvesafb:mode_option=1024x768-24,mtrr=3,scroll=ywrap"
```

TwinView and Xinerama are off:```

Option         "NoTwinViewXineramaInfo" "true"
```
[LIST]
[*]I have the FB env var exported (FRAMEBUFFER=/dev/fb0)
[*]Switching from VT(n) to VT7 is faster on a Ubuntu-2D session.
[*]Switching to Lightdm is a lot faster.
[*]Disabling ccsm/Composite/"Detect Refresh Rate" seems to speed it up a little.
[*]"Sync to "VBlank", "Lighting" and "Texture Compression" disabled on OpenGL Compiz plugin at ccsm.
[*]"Sync to "VBlank" disabled on nvidia-settings for XVideo and OpenGL. All antialiasing options are OFF. Powermizer at "Adaptive". "Force Full GPU Scalling" if OFF.
[*]There are old reports that setting Option "UseEvents" to "false" on xorg.conf used to be a fix to this in older cards. I see no difference at all.
[/LIST]
The only ouput to /etc/X11/xorg.0.log I see when switching from VT(n) to VT7 is this:
```
[   417.644] (II) Open ACPI successful (/var/run/acpid.socket)
[   417.722] (II) NVIDIA(0): Setting mode "1920x1080_60+0+0"

```I'm detecting this behavior with GTS450 and GT9500. I'd appreciate if you could please test with your cards and report if you see this delay.

Regards,
Effenberg

---

### Post by ventrical on 2011-10-22
> **effenberg0x0 said:**
> A question for Nvidia proprietary drivers users: Do you have a considerable delay when switching back to X (Unity) from any VT? 

Example:
- Start Unity Session
- Switch to VT1 (very small delay, like 2 second before seeing console text)
- Switch to VT7 (very big delay, like 10-15 seconds before you can see the desktop)

I'm pretty sure this was fixed on Oneiric, but I'm seeing it again on PP using any proprietary driver version (tested 280.13, 285.03, 285.05.09, 290.03).

Since we don't get KMS support on proprietary, I am using a uvesafb framebuffer. My kernel line is:
```
GRUB_CMDLINE_LINUX_DEFAULT="video=uvesafb:mode_option=1024x768-24,mtrr=3,scroll=ywrap"
```TwinView and Xinerama are off:```

Option         "NoTwinViewXineramaInfo" "true"
```
[LIST]
[*]I have the FB env var exported (FRAMEBUFFER=/dev/fb0)
[*]Switching from VT(n) to VT7 is faster on a Ubuntu-2D session.
[*]Switching to Lightdm is a lot faster.
[*]Disabling ccsm/Composite/"Detect Refresh Rate" seems to speed it up a little.
[*]"Sync to "VBlank", "Lighting" and "Texture Compression" disabled on OpenGL Compiz plugin at ccsm.
[*]"Sync to "VBlank" disabled on nvidia-settings for XVideo and OpenGL. All antialiasing options are OFF. Powermizer at "Adaptive". "Force Full GPU Scalling" if OFF.
[*]There are old reports that setting Option "UseEvents" to "false" on xorg.conf used to be a fix to this in older cards. I see no difference at all.
[/LIST]
The only ouput to /etc/X11/xorg.0.log I see when switching from VT(n) to VT7 is this:
```
[   417.644] (II) Open ACPI successful (/var/run/acpid.socket)
[   417.722] (II) NVIDIA(0): Setting mode "1920x1080_60+0+0"

```I'm detecting this behavior with GTS450 and GT9500. I'd appreciate if you could please test with your cards and report if you see this delay.

Regards,
Effenberg

 How do we switch from VT1 to VT7 in aUnity session?

---

### Post by effenberg0x0 on 2011-10-22
> **ventrical said:**
> How do we switch from VT1 to VT7 in aUnity session?

Use **CTRL+ALT+F1** to go to VT1 (F2 to VT2, etc) and **CTRL+ALT+F7** to go back to X.

Regards,
Effenberg

---

### Post by effenberg0x0 on 2011-10-22
Workarounds mentioned at Ubuntu and other distros forums / bug reports. None of these produces any improvement for me.
[B]
xorg.conf options:[/B]
```

    Option         "NoTwinViewXineramaInfo" "true"
    Option         "NoTwinViewXinerama" "true"
    Option         "UseEvents" "false"

```

**Kernel Options:**
```

intel_iommu=off 
intel_iommu=igfx_off
nouveau.modeset=0 
rdblacklist=nouveau 
vmalloc=256MB 
```
[B]
Remove Nouveau packages:[/B]
```
sudo apt-get remove libdrm-nouveau1a
sudo apt-get remove --purge xserver-xorg-video-nouveau
```

---

### Post by ventrical on 2011-10-22
> **effenberg0x0 said:**
> Use **CTRL+ALT+F1** to go to VT1 (F2 to VT2, etc) and **CTRL+ALT+F7** to go back to X.

Regards,
Effenberg


Thanks .. .worked great here. F7 took about  3 seconds.

GF210
NDV 280.13

Can't find the xorg log file you mentioned. I suppose I would have to enable that somewhere.

EDIT: /etc/X11/xorg.0.log <can't find this file.

---

### Post by effenberg0x0 on 2011-10-22
> **ventrical said:**
> 
Can't find the xorg log file you mentioned. I suppose I would have to enable that somewhere.

No, see /var/log/Xorg.0.log. See the file inside the X session. See the last message. Switch to other VT and Back and look at the log. Maybe you have some different message than what I posted.

Thanks,
Effenberg

[B]EDIT:
[/B]What do you have for:
```

uname -a
cat /etc/default/grub | grep -i cmdline
```

---

### Post by ventrical on 2011-10-22
> **effenberg0x0 said:**
> No, see /var/log/Xorg.0.log. See the file inside the X session. See the last message. Switch to other VT and Back and look at the log. Maybe you have some different message than what I posted.

Thanks,
Effenberg

[B]EDIT:
[/B]What do you have for:
```

uname -a
cat /etc/default/grub | grep -i cmdline
```


dale@ubuntu:~$ uname -a
Linux ubuntu 3.1.0-1-generic #1-Ubuntu SMP Tue Oct 18 19:11:28 UTC 2011 i686 i686 i386 GNU/Linux
dale@ubuntu:~$ cat /etc/default/grub | grep -i cmdline
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
dale@ubuntu:~$

---

### Post by effenberg0x0 on 2011-10-22
> **ventrical said:**
> dale@ubuntu:~$ uname -a
Linux ubuntu 3.1.0-1-generic #1-Ubuntu SMP Tue Oct 18 19:11:28 UTC 2011 i686 i686 i386 GNU/Linux
dale@ubuntu:~$ cat /etc/default/grub | grep -i cmdline
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
dale@ubuntu:~$

Same kernel, no specific parameters. I have to assume it's some problem here. It's unlikely that only GT9500 and GTS4500 have some bug related to PP. I'll keep looking.

Thanks,
Effenberg

---

### Post by ventrical on 2011-10-22
[    21.300] (II) NVIDIA(0): Setting mode "nvidia-auto-select"

[    19.964] (II) Open ACPI successful (/var/run/acpid.socket)

---

### Post by ventrical on 2011-10-22
> **effenberg0x0 said:**
> Same kernel, no specific parameters. I have to assume it's some problem here. It's unlikely that only GT9500 and GTS4500 have some bug related to PP. I'll keep looking.

Thanks,
Effenberg

Thanks for walking me through some of this.

Glad to be of help.

---

### Post by xyzzyman on 2011-10-22
I don't think this is PP specific. It happens to me on Oneiric using the 285 and the new 290beta's on a GeForce 9600M GS 512MB. It also makes any playing audio repeat until it's all reset.

---

### Post by effenberg0x0 on 2011-10-22
Update: It is not compiz. If only compiz is running, transition is fast. Delay happens only when the Unity Plugin is activated on ccsm.

---

### Post by ronacc on 2011-10-22
I'm seeing the same thing on GS so it's not compiz related since it isn't running in GS .

---

### Post by mc4man on 2011-10-23
5 & 1.5 sec here, same as 11.10 (5 is from a newly logged in VT, 1.5 from an already logged in Vt
Using unity, Vsync in both X & GL, ect ect.
Do not use a uvesafb framebuffer, don't see the point in doing so

---

### Post by tghe-retford on 2011-10-23
About one and a half seconds to switch to VT1 and then five seconds to switch back to VT7 here. Using Kubuntu with 280.13 drivers and a GT 555M graphics card, and VSync for both the video settings and OpenGL is on (not that Flash takes any notice of that).

---

### Post by effenberg0x0 on 2011-10-23
> **mc4man said:**
> 5 & 1.5 sec here, same as 11.10 (5 is from a newly logged in VT, 1.5 from an already logged in Vt
Using unity, Vsync in both X & GL, ect ect.
Do not use a uvesafb framebuffer, don't see the point in doing so

Hi, uvesafb was a legacy from another test. I've disabled it, but saw no change to VT switch issue. In fact, the only thing that can make the VT switch work fast for me is disabling the Unity Plugin. Still, it's far from being as fast as my notebook, which has Intel VGA (switch is almost immediate with or without the Unity Plugin enabled). I'm trying to trace what is going on when the screen is black. No Xorg message, no compiz message. I'm gonna try to look at unity debug log.

---

### Post by effenberg0x0 on 2011-10-23
> **tghe-retford said:**
> About one and a half seconds to switch to VT1 and then five seconds to switch back to VT7 here. Using Kubuntu with 280.13 drivers and a GT 555M graphics card, and VSync for both the video settings and OpenGL is on (not that Flash takes any notice of that).

But do you feel that this 5sec time is OK as it has always been in this hardware or has it slowed down in PP (which is the case here)? I had an almost immediate transition with Oneiric and now am looking at 10-15 seconds on PP (no hdd activity, sometimes monitor turns off while waiting, etc).

---

### Post by mc4man on 2011-10-23
At least here it's the exact same OO & PP. If using nouveau then it switches instantly, nvidia has the delay.

Though for whatever reason it becomes much less, (1 - 1.5) when switching back from an _already logged in_ VT..?
(as in VT1 > VT7 > VT1 > VT7
........ 5 sec ..... 1.5 sec

---

### Post by effenberg0x0 on 2011-10-23
> **mc4man said:**
> At least here it's the exact same OO & PP. If using nouveau then it switches instantly, nvidia has the delay.

Though for whatever reason it becomes much less, (1 - 1.5) when switching back from an _already logged in_ VT..?
(as in VT1 > VT7 > VT1 > VT7
........ 5 sec ..... 1.5 sec

True, time delay gets smaller. In my case not anywhere near something like 1,5 sec, but there's a sensible improvement. I have verified that with acpid service disabled I also get some small improvement. When the delay and "BlackScreen" happens, all I get on logs is that one acpi rule was loaded. I'm checking acpi rules, to see if any of them could stall the transition. 

Still, it would make no sense to mess with acpi, since switching from VT to Lightdm or to a metacity or compiz session (with no unityshell plugin) is much faster.

---

### Post by ttkaminski on 2011-11-06
I'm experiencing the same problem.  I have a NVIDIA GeForce GTX 460 SE card  running on a Asus P8P67 motherboard with Intel i5 2500k cpu.  Ubuntu 11.10 (oneiric), Linux venus 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux. 

I get a long delay before I see the prompt when switching from VT1 to VT7, and also when resuming from suspend (seem like this also causes a VT7 switch).  Very annoying.  

Has this bug been reported in launchpad yet?  If so, what is the link?

---

### Post by effenberg0x0 on 2011-11-06
> **ttkaminski said:**
> I'm experiencing the same problem.  I have a NVIDIA GeForce GTX 460 SE card  running on a Asus P8P67 motherboard with Intel i5 2500k cpu.  Ubuntu 11.10 (oneiric), Linux venus 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux. 

I get a long delay before I see the prompt when switching from VT1 to VT7, and also when resuming from suspend (seem like this also causes a VT7 switch).  Very annoying.  

Has this bug been reported in launchpad yet?  If so, what is the link?

I have not reported it, as I can't pinpoint where the problem is. I like my reports to be specific. One thing that I can't understand: I found that when a window is opened and running glxgears, the switch between VT7, VT1, VT7 is a little faster. It's like glxgears is forcing a speed-up in screen redraw when you switch back to the X session.

I have verified that although the only message in log when you switch from VTn to VT7 is acpi related (rule loaded), loading acpi rule takes virtually no time when manually loaded, so I doubt the answer will be there. I have tried running Unity in verbose mode during switch and piping the log to a file, but still could find no clear anomaly. I'm lost on this one. Can't pinpoint a culprit.

---

### Post by dfarrell07 on 2011-11-09
On [http://bit.ly/tOkqyq](http://bit.ly/tOkqyq), I have posted about a similar problem. I also noticed that the same user who started this thread, effenberg0x0, and I share another glitch ([http://bit.ly/rxwunv](http://bit.ly/rxwunv)). That glitch involves mouse pointers freezing up. I fixed that issue by disabling the 'disable touchpad while typing' option. As not many users are affected by either of these bugs, and at least two are affected by both, it seems plausible that they are related.

Is anyone here affected by the glitch described in my first link? Basically, the same lag bug here, but it happens when you loggin?

---

### Post by effenberg0x0 on 2011-11-09
> **dfarrell07 said:**
> On [http://bit.ly/tOkqyq](http://bit.ly/tOkqyq), I have posted about a similar problem. I also noticed that the same user who started this thread, effenberg0x0, and I share another glitch ([http://bit.ly/rxwunv](http://bit.ly/rxwunv)). That glitch involves mouse pointers freezing up. I fixed that issue by disabling the 'disable touchpad while typing' option. As not many users are affected by either of these bugs, and at least two are affected by both, it seems plausible that they are related.

Is anyone here affected by the glitch described in my first link? Basically, the same lag bug here, but it happens when you loggin?

Hey dfarrell, 

I gave up using Linux on laptops, at least for a while. I finally got sick of years fighting the continuous battle for battery life vs. decent performance, finding and setting up working drivers (that glitch again every major kernel release), etc on machines that, no matter how much you spend on them, perform worse and cost more than a desktop. Got tired of it all. So in regards of the second bug you mention (touchpad), I won't be of much assistance. Still, I'm very interested in the first one (VT switch delay). I'll try to talk to someone at NVidia, see if we can get some debugging on it.

---

### Post by mc4man on 2011-11-09
As  fas the cursor freeze, while i found that the disabling of the settings option effective it didn't seem to be 100% here. (would get maybe once a week or so with the option disabled.

Adding this has prevented it completely - 
```
gsettings set org.gnome.settings-daemon.plugins.mouse active false
```

The main bug on is in a bit of disarray, somewhat due to commenter's with a different bug - one where the cursor acts on it's own, also because it's likely hardware related as to happening & possible workarounds
(So I still think the cursor freeze on some laptop touchpads is a valid, unresolved  bug

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/868400](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/868400)

---

