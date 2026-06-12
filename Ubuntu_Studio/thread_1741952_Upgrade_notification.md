---
title: "Upgrade notification"
date: 2011-04-28
forum: Ubuntu Studio
---

### Post by rusty377 on 2011-04-28
I just received a notice from update manager that Natty 11.04 is available for upgrade. I am currently at 10.10. Question is - will upgrading via this notification keep me in Studio setup or just plain Natty? Current kernel is generic 10.10. Any known issues or improvements for audio recording via wine/reaper? I did select to upgrade and there are many changes but have 4 hours to cancel :0)

Wish I hadn't done it - completely unbootable system now. Startup says (essentially) it cannot find sda1, but info scrolls by so fast I cannot detail reasons.

After a little experimentation using the grub stuff I managed to get it up running natty 11.04. I had to boot into older version of Ubuntu 2.6.35-22 and then unload and reload the video driver for Nvidia. Funny thing is I don't have the new menu system- everything looks the same and audio stuff (jack and reaper via wine) works the same when in 10.10. I did check version- uname -a shows ubuntu 2.6.38-8-generic and other string (can't remember what it was) showed it was Natty 11.04.

It seems I upgraded but not absolutely sure about all functions working- there were some error messages initially bu do not show up now. Running System update shows current. Synaptic also.

Hope I don't have an "orphan" system

---

### Post by FuzzShifter on 2011-04-30
Is the new theme available at all?

It's possible that a customized theme which has been saved as the default session wouldn't change due to an upggrade.

---

### Post by rusty377 on 2011-04-30
> **FuzzShifter said:**
> Is the new theme available at all?

It's possible that a customized theme which has been saved as the default session wouldn't change due to an upggrade.

Fuzz,

I don't see any theme that looks like the natty layout they speak of on the Ubuntu site - just about 8 or 9 themes.

A question- my machine has an Nvidia driver- which I have loaded and is activated but when I look at "additional driver" screen it say "Not currently using this driver"- how do you make it use that driver? Doesn't seem to have a way to select it.

---

### Post by jejeman on 2011-04-30
You can see which module you're using with the folowong command:

```
lspci -knn|grep -i vga -A 5
```

---

### Post by rusty377 on 2011-04-30
> **jejeman said:**
> You can see which module you're using with the folowong command:

```
lspci -knn|grep -i vga -A 5
```

jejeman,

This is what it shows

rusty@ubuntu:~$ lspci -knn|grep -i vga -A 5
02:00.0 VGA compatible controller [0300]: nVidia Corporation G71 [GeForce 7300 GS] [10de:01df] (rev a1)
        Subsystem: Device [196e:034e]
        Kernel driver in use: nvidia
        Kernel modules: nvidia-173, nvidia-current, nouveau, nvidiafb
03:05.0 FireWire (IEEE 1394) [0c00]: Agere Systems FW322/323 [11c1:5811] (rev 61)
        Subsystem: Hewlett-Packard Company Device [103c:2a3a]


Is this using my video to the fullest? I have nvidia 7300S and driving 47" LG tv using HDMI.

Thanks

---

### Post by jejeman on 2011-04-30
You're defenitly using the properitary nvidia driver. What is little strange thou is that you have both nvidia-173 and nvidia-curent instaled. I would say that nvidia-173 is in use which is probably ok because you have an older card.
You can say that you are useing your card to it's fullest.

---

### Post by rusty377 on 2011-04-30
jejeman,

It is kind of weird- here is a screenshot.

Notice it says at the top "No proprietary drivers are in use" And at the bottom activated but not currently in use- do you know how to turn it on - or even if you can?

---

### Post by jejeman on 2011-04-30
As far I can tell you are using the nvidia properity driver. You can double check looking in the xorg.conf
```
 cat /etc/X11/xorg.conf
```
and starting the nvidia X server settings. If the driver is not in use the nvidia "control panel" will tell you that.

---

### Post by rusty377 on 2011-04-30
jejeman,

Does the proprietary video driver only load with certain programs maybe? Like heavy games?

---

### Post by jejeman on 2011-04-30
No, it loads at X startup. 
You sholud never take a sreenshot of text in terminal, its always better to copy text to the forum.
In Nvidia X server settings window you can see which driver is in use. You are using nvidia proprietary driver. Ignore what jockey-gtk is showing. But, maybe its that you are using the 173 dirver, thats why the nvidia-current is not in use as jockey said.

---

### Post by Ken UK on 2011-04-30
I read that in none generic distros based on Ubuntu you're not suppose to use the upgrade option unless it says on the website of the distributor's website that its safe to do so.

---

### Post by FuzzShifter on 2011-05-01
> **rusty377 said:**
> Fuzz,

I don't see any theme that looks like the natty layout they speak of on the Ubuntu site - just about 8 or 9 themes.

A question- my machine has an Nvidia driver- which I have loaded and is activated but when I look at "additional driver" screen it say "Not currently using this driver"- how do you make it use that driver? Doesn't seem to have a way to select it.


I have no experience with NV drivers (as an ATI user).

The theme may be available by searching Synaptic Package Manager.

We all have unique installations, but my experience revolves around installing the Ubuntu Studio components needed for my applications on a standard Ubuntu desktop install.

Been using the Ubuntu Studio theme for 2 years now (on this machine), but understand why you like the slick look of Natty.

Natty is on my 'bedroom' laptop and is very pretty.

As was mentioned by another poster, 'upgrade by fresh install' is the preferred method for getting a new distro on your machine.

---

### Post by rusty377 on 2011-05-01
> **Ken UK said:**
> I read that in none generic distros based on Ubuntu you're not suppose to use the upgrade option unless it says on the website of the distributor's website that its safe to do so.

Ken,

I think I will just do a clean install and be done with it- good idea.

Thanks

---

