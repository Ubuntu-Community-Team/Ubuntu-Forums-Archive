---
title: "Xubuntu 8.10 and not being able to install realtime Kernel"
date: 2009-01-29
forum: Ubuntu Studio
---

### Post by pixelblip on 2009-01-29
Hello 
I've installed the realtime Kernel with Xubuntu 8.10 but Jack is not starting with the 'realtime' box ticked it the jack control panel.
Can you use it in real time on this version of Ubuntu?
I've installed all the apps from the studio version.

I used this command to install the realtime kernel:
gksudo aptitude install linux-rt

Will I just have to use Ubuntu Studio 8.10 instead?
I'd prefer Xubuntu...it's just a bit lighter.......
Thanks for your advice

---

### Post by snowpine on 2009-01-29
Reboot your computer. When you get to the Grub menu (you may have to hit Esc to see this menu), make sure you choose the "rt" kernel from the options.

Sorry but I am not a Jack expert. :(

---

### Post by eric71 on 2009-01-29
You will need to modify your limits.conf file.

This is set up in Ubuntustudio by default, but you need to do it yourself in Xubuntu. Here is the instructions from [https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)

"After you've got the kernel you still need to set up real-time access for your applications. 

All you have to do for this is give your audio group permissions to access the rtprio, nice, and memlock limits. To do this, you just need to run these commands, which will add some lines to the file /etc/security/limits.conf: 
 sudo su -c 'echo @audio - rtprio 99 >> /etc/security/limits.conf'
 sudo su -c 'echo @audio - nice -19 >> /etc/security/limits.conf'
 sudo su -c 'echo @audio - memlock unlimited >> /etc/security/limits.conf'

These value are suggested by [http://jackaudio.org/faq](http://jackaudio.org/faq). The memlock line determines how much of your memory can be locked by audio processes. Some recommend setting this as half of your total memory (RAM, in K). See Florian Paul Schmidt's page. 

In Intrepid, you have to create a user group named "audio" and add your user name (and other users of the workstation if needed) to this group. You can do that very simply in "System / Administration / User Group". 

Restart the workstation and it is ok."

Hope this helps.

Eric

---

### Post by pixelblip on 2009-01-29
Hi
Thanks for your reply Eric. I appreciate it!

Well the goodnews is that jack starts now with realtime kernel with no errors at 44.1khz on my onboard Intel soundcard. The bad news is there are no audio outputs ( ie I can't run e.g Hydrogen  as it says there are no jack audio outputs). ZynAddSubFx is silent but the audio meters are bouncing as though sound is coming out.

Alsa is working as I can play youtube / Hydrogen with Alsa.

Is something screwed up with Jack do you think? Reinstall?
It's not the mixer being muted or anything like that..........I've checked that and they are all up.

I don't know where to look now............arrrgh! :D

---

### Post by pixelblip on 2009-01-29
Just to add when I look at Qjackctl panel and the 'Audio' tab on the connection panel I can see under Readable Clients/ Output Ports

- ZynAddSubFX

  Out_1
  Out_2

so it's sorta working............just no sound

I notice Hydrogen won't play when you click 'Jack Transport'

---

### Post by pixelblip on 2009-01-29
Ok Panic stations over. 
Things are working again after lots of reboots!
One thing I was trying was to press ESC at the initial Grub bootup and select 'Ubuntu Real Time Kernel' . This doesn't work...........
I went back to the original default grub ubuntu and rebooted..........

For all noobs: Sometimes you gotta keep persevering with it....it's not easy at 2 in the morning when you just want to make music.........but it's nice when it finally works.

I would recommend everyone who wants to make music to take a look at Xubuntu with the real time Kernel. It's fast on my Pentium 4.......I am getting into Hyrogen and ZynAddSubFX after dealing with vsts all these years......I like the simplicity and sonic power of these apps.

---

### Post by raboofje on 2009-01-29
> **pixelblip said:**
> I would recommend everyone who wants to make music to take a look at Xubuntu with the real time Kernel. It's fast on my Pentium 4.

Unfortunately SMP and MIDI timing are both broken in the linux-image-2.6.27-3-rt kernels that come with Ubuntu 8.10...

[https://bugs.launchpad.net/ubuntu/+source/linux-rt/+bug/300806](https://bugs.launchpad.net/ubuntu/+source/linux-rt/+bug/300806)
[https://bugs.launchpad.net/ubuntu/+source/linux-rt/+bug/290498](https://bugs.launchpad.net/ubuntu/+source/linux-rt/+bug/290498)

---

### Post by shockdiode on 2009-02-01
For those having issues with this, I've gotten greatly improved performance out of jack (actually usable for audio work which the generic kernel simply is not on my machine) in 8.10 by compiling a kernel from the ubuntu kernel sources with the following options:

CONFIG_HZ=1000
CONFIG_HZ_1000=y
CONFIG_PREEMPT=y

That is, set the interrupt timer to 1000HZ instead of the default 250 and enable preemptable kernel. 

It's probably not for the faint of heart but you can find instructions on compiling a kernel 'the ubuntu way' here: 

[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

If you are uncomfortable with any of this, I highly recommend not doing it. 

Hope that's useful to someone.

---

