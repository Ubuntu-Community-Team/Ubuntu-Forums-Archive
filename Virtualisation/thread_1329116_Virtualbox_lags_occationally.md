---
title: "Virtualbox lags occationally"
date: 2009-11-17
forum: Virtualisation
---

### Post by nisukka on 2009-11-17
Hi!

I have Sun Virtualbox 3.0.10 on my Kubuntu 9.10 machine and I have installed a virtual Windows XP and Ubuntu 9.10.
Both the XP and Ubuntu lag occationally.
When the lag occurs, I can still move the mouse pointer, but clicking buttons has no response until a few seconds later with a delay.

I have tried with and without installing the guest additions but no difference. I also have tried different RAM sizes.

My host machine is Acer 7520 laptop with 4 GB RAM and Kubuntu 9.10 64-bit.

Any suggestions?

---

### Post by anagor on 2009-11-17
Same here, disabling compiz should help, or if you absolutely need compiz, go to compiz configuration,  in the workarounds section, play with the bottom 3 settings there:
AIGLX Fragment fix, Fix Screen updates in XGL, Force synchronization

You will have to shutdown and restart the VM after every setting change. This helped, at least for me.

Also, the problem maybe because of the "Enable 3D acceleration" setting in the Vbox itself, if it is indeeed enabled for your VM.

Cheers;

---

### Post by nisukka on 2009-11-17
Thanks, I will try to disable desktop effects first and see if it helps.

Currently I have disabled the 3D-acceleration in Virtualbox settings because I noticed that it lags the virtual system more frequently.
But disabling it, it didn't disable the lagging.

---

### Post by nisukka on 2009-11-17
No, disabling desktop effects didn't help.
Any other ideas?

---

### Post by anagor on 2009-11-17
I also have 64bit karmic, as you undestood already :)
And I had the same lagging problem as you do, but in my case, changing the settings in compiz, helped with that.

BTW: I have ATI card, if you have ATI also, it will help to install the closed source ATI drivers, but from the ATI itself, and not the repository version.
In the "amdcccle", I have also changed the, sync to vblank, setting which might also help.

But if you have NVIDIA, or Intel card, then I don't know, what can cause it. 
On the laptop I have Nvidia card, virtual Box installed there also, and always worked fine.

Maybe someone else will have something more helpfull.
Sorry ;)

---

### Post by nisukka on 2009-11-17
Thanks for your input.
I have NVIDIA card.
Hoping to get some clues to resolving this.

---

### Post by anagor on 2009-11-18
I had a chance to think about it, as I expirienced the lags myself yesterday, it wasn't happening for me for a long time now, and a system reboot solved it (ohh, great, just like in windows world).
There are two different types of lags that I've noticed:

1. Right from the start of the virtual machine, sometimes even the VM's bios is already lagging, in such a case I just shutdown the machine, close the VirtualBox and kill any remaining VBOX processes.

2. The VM starts ok, but then, after the OS is loaded it starts to lag with no apparent reason. This I suspect is related to pulseaudio, even if your guest OS doesn't produce any sounds, the driver of the VM is still needs to sync itself with pulseaudio.
Next time I will notice this type of lagging, I will turn the Audio hardware of the VM off, to try and confirm it.

cheers;

---

### Post by nisukka on 2009-11-20
According to this forum thread, there could be something in the latest Karmic kernel

[http://forums.virtualbox.org/viewtopic.php?f=7&t=24117](http://forums.virtualbox.org/viewtopic.php?f=7&t=24117)

I have tried updating to VBox 3.0.12 and disabling audio in VM but no effect.

---

### Post by Markkreuzz on 2009-11-20
> **nisukka said:**
> Hi!

I have Sun Virtualbox 3.0.10 on my Kubuntu 9.10 machine and I have installed a virtual Windows XP and Ubuntu 9.10.
Both the XP and Ubuntu lag occationally.
When the lag occurs, I can still move the mouse pointer, but clicking buttons has no response until a few seconds later with a delay.

I have tried with and without installing the guest additions but no difference. I also have tried different RAM sizes.

My host machine is Acer 7520 laptop with 4 GB RAM and Kubuntu 9.10 64-bit.

Any suggestions?

Yes Virtualbox 3.0.10 really lags. try updating to 3.0.12(oops, i see you already did that 1) or try this **GUIDE** that i've put up together [**[COLOR="DarkOrange"]HERE[/COLOR]**]("http://ubuntuforums.org/showthread.php?p=8342357#post8342357") and post back results :D

Also I 'had' some sound issues before where it randomly stops making sound, but i fixed it using the Pulse-Audio(buggy b*tch) PPA fixes. I also use Nvidia proprietary drivers and have no issues about it.

Oh also try installing guest additions for 3.0.12 as stated here in this bug ticket [**[COLOR="DarkOrange"]#4392[/COLOR]**]("http://www.virtualbox.org/ticket/4392")

> The performance will not improve until you installed the guest additions and until they are active. That is, the fix/workaround will not work during boot.

I think it is not necessary to re-install the guest additions after you changed the HAL but it cannot hurt. Make sure to use 3.0.12 additions in any case.


---

### Post by nisukka on 2009-11-24
Now the lagging seems to be gone.
Here is what I did from my last situation:

1. Installed VBox Guest Additions 3.0.12 (still lag)

2. Got a new kernel (2.6.31.15) from Software Updates (still lag)

3. Inspired by Markkreuzz's posted guide to disable IO APIC, I tried to change the driver of ACPI Uniprocessor PC from Device Manager. The driver was already "Advanced Power and Configuration Interface (ACPI) PC", so just for fun, I tried the other driver I could choose, which was "Standard-PC".

I rebooted the virtual XP (quick test, no lag!) and Add a new hardware wizard opened asking me to install the Guest Additions drivers again. So I installed them and rebooted. So far the lag seems to be gone.

I've been playing around with Solitaire, Access and Excel for less than an hour now and there is no lag at all, like I had before. Everything seems to work as it should be.
I even enabled the sounds and 3D-acceleration in VBox settings.

Maybe others can try this same fix and report how it worked?

---

### Post by anagor on 2009-11-24
In my case, the IO APIC was never enabled on my VM, but since I've updated the vbox and the guest additions to 3.0.12 I hadn't seen any lags on either of the VMs I have.

---

### Post by Markkreuzz on 2009-11-24
Glad that worked for you nicely :D..

---

