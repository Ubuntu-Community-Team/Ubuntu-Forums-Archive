---
title: "m-audio profire 610 as dac"
date: 2014-02-13
forum: Ubuntu Studio
---

### Post by scott_schinnerer on 2014-02-13
Perhaps I should put this in the absolute beginners forum.  I have just installed Ubuntu on my windows xp laptop.  I want to use this computer to stream music and digitalize LPs and want to use my firewire interface as my dac.  Now I realize I should have installed Ubuntu Studio to do this.  So, I see I can install a bunch of stuff on top of Ubuntu or delete Ubuntu and reinstall Ubuntu Studio.  As I have partitioned my hard drive and left XP on one of the partitions, I am unsure how to just delete Ubuntu and install Studio.  Do I need to remove the partition also?  How do I go about this.  Or is there something simpler I can do to be able to use my profire?
I am floundering here a bit and any help would be appreciated.  I have just installed Ubuntu and don't really have anything on there that I couldn't live without, so I don't mind starting from scratch here with Studio.  I just don't know how to proceed.

---

### Post by Bucky Ball on 2014-02-13
One option is to install 'ubuntustudio-audio'. You don't need to install the whole lot. You'll find it in Software Centre or Synaptics. 

What makes you think you need to run Studio to use your outboard as a DAC? I'm running an old Mbox 2 Mini and it works fine. The drivers are right there in the kernel. They might be for yours, too. Is it USB? If so, boot up with it unplugged, when you're at a desktop, plug it in, open a terminal and enter this:

dmesg

Press return. Post back the last part that should say something about the USB you just plugged in. ;)

Things can sometimes get tricky with Pulseaudio/ALSA and it might be a tweak is required. May as well check rather than install anything you don't need to.

* Ah, just reread your post. Firewire. Is that hot-pluggable? If so, shove it in and check 'dmesg'.

---

### Post by scott_schinnerer on 2014-02-13
It is firewire.  I have not tried to install it yet.  I had read, I thought, that I needed [COLOR=#000000][FONT=Verdana]ffado-mixer and jackd1 and a l[/FONT][/COLOR][COLOR=#000000][FONT=Verdana]ow-latency kernel:[/FONT][/COLOR][COLOR=#000000][FONT=Verdana]sudo apt-get install linux-lowlatency linux-headers-lowlatency.  And I thought I needed to do this in Studio.  This was confusing to me and I came here.  this is the thread I was reading: [http://ffado.org/?q=node/735](http://ffado.org/?q=node/735)[/FONT][/COLOR]

---

### Post by Bucky Ball on 2014-02-13
Nope, you don't need to be in UStudio. You can install a low-latency kernel (depending on the release you're using you might have one by default now) and the other stuff, too.

For jack, install QJackctl. That is a GUI that will drag in jack for you and let you control everything more easily. That way you don't need to install jack, just QJackctl.

The main thing is to find out if your audio device is supported. Can you hot-plug it and post the dmesg, as suggested previously? Another idea would be to install 'pavucontrol', launch it with your device plugged in, and see if it shows up in there anywhere. Also, without going that far, plug the device in and open alsamixer by typing in a terminal

alsamixer

You can change devices with F6.

---

### Post by scott_schinnerer on 2014-02-13
Ok, much of my problem is I do not know any code or whatever and therefore have a hard time with the terminal.  I did install QJackctl.  I don't see any mention of the interface using alsamixer.   or with dmesg. I hot plugged it, and also tried rebooting the computer with the firewire plugged in and the interface turned on. To install pavucontrol would I type "sudo apt-get install pavusontrol"? 
And, by the way, thanks for taking the time to help me out.

---

### Post by Bucky Ball on 2014-02-13
That's okay. None of this should mention anything about alsamixer. You simply open a terminal and type in 'alsamixer'. That will bring up the alsamixer and there, if it is not on your firewire device already, hit F6 and see if you can find it. 

Also, plug in the firewire device while the machine is on, open a terminal, type 'dmesg'. Post the output back here. 

QJackctl doesn't run ALSA. It runs jack and jack pretty much takes control of ALSA, Pulse and anything else audio. You control it all from there. Open QJackctl, with the device plugged in, click 'Setup' and in the right side, you should see a list of input/outputs. Click the '>>' to the far right.

Is the DAC there as an option?

---

### Post by jejeman on 2014-02-14
Alsamixer will never manage firewire device, because ALSA does not support/work with firewire devices, only PCI and USB. FFADO works with firewire audio devices.

To troubleshoot firewire audio device first check if there is a firewire device nodes
```
ls /dev/fw*
```
Although you have simple task in mind with this sound card, it would be easier (to us) if you install Ubuntu studio.

---

### Post by scott_schinnerer on 2014-02-18
It seems to me the easiest way to do this is to install Ubuntu studio, also.  So, one of my first questions was the best way to delete ubuntu and replace it with studio.  It is on a partitioned hard drive with my original windows xp, which I would like to keep as I have a few pieces of software on there that only runs with windows.  How can i delete what is on the partition containing ubuntu now without screwing up the other partition containing windows?  Another alternative is to simply use the windows partition with my DAC, and use ubuntu for all else.

---

### Post by Bucky Ball on 2014-02-18
Boot to a Live Ubuntu Studio install disk or USB, 'Try Ubuntu', when at the desktop launch Gparted and delete the Ubuntu partition. You can leave the swap there, and /home if you have that on a partition. 

Once done, hit the 'install' icon then choose 'Something Else' when you get to the partitioning section of the install. You'll see your Win partitions there so just don't go near them (NTFS or FAT). The free space you created when you deleted the Ubuntu partition should be there and ready for you to install to. Mark the swap 'to use' (and also /home partition if you have one, but NOT to format), make sure none of the Win partitions are set to format (ticked) or use and you're good to go.

Your other option is to install ubuntustudio-desktop, log out and choose 'xfce' or 'UStudio' from the 'Sessions' menu, login and you should be in Ubuntu Studio (but you will, of course, still have all default Ubuntu apps as well as UStudio apps).

---

### Post by Nosphky on 2014-03-02
> **Bucky Ball said:**
> Your other option is to install ubuntustudio-desktop, log out and choose 'xfce' or 'UStudio' from the 'Sessions' menu, login and you should be in Ubuntu Studio (but you will, of course, still have all default Ubuntu apps as well as UStudio apps).

Is 'ubuntustudio-desktop' a separate version/flavour ?  I can't see it as a download on either Studio or Ubuntu websites and from your reply, it seems an interesting alternative to dual booting.  

I'm looking at options for installing Ubuntu and Studio as an alternative to Windows.  I have live versions of both on USB sticks and I have read advice on the website that for general purpose (not audio) work, the low latency kernel of Studio does not give best response times.  So it would seem better to use Studio for audio work and vanilla Ubuntu for general work.

---

### Post by Bucky Ball on 2014-03-02
Software Centre. Always go there first.

Ubuntu Studio is a different flavour designed for A/V professionals and enthusiasts. ubuntustudio-desktop basically installs all default packages and the desktop environment (xfce4) on top of Ubuntu and its defaults. Messy.

But this is off-topic. Please post a new thread if you have questions about Ubuntu Studio. Thanks.

---

