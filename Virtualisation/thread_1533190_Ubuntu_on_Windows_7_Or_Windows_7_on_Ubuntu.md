---
title: "Ubuntu on Windows 7? Or Windows 7 on Ubuntu?"
date: 2010-07-17
forum: Virtualisation
---

### Post by Ghuloomo on 2010-07-17
Salaam,

Which one do you prefer? Installing Ubuntu on Windows 7? or Windows 7 on Ubuntu? I see both guides but I think there are advantages and disadvantages. For example, if you install ubuntu on windows 7 which we all know windows is not as stable as Linux, then if your windows 7 got any problem you need to format it, then you're loosing your ubuntu as well.

Keeping in mind I'm both want to use the 64bit version of both the OSs.

What do you think? Which one you prefer? Why?

---

### Post by dv3500ea on 2010-07-17
Why not dual boot? ie. Ubuntu and Windos side by side

---

### Post by 1Michael1 on 2010-07-17
Well I'd rather use W7 in Ubuntu with Virtual Box.
As you said yourself, Ubuntu is way more stable since it can stand on for a long time without rebooting while W7 drops performance the longer you have it on (As I've experienced myself). Agree with the formatting as well.

@ dv3500ea

It's always good to have it in a Virtual Box incase you need Windows without having to reboot to change OS. But it depends on what your specifications are, I myself have a weak laptop therefore I've to dual boot since a Virtual Box would burn my laptop to the ground while using PS in Win.

---

### Post by fjgaude on 2010-07-17
Go with Ubuntu as the host with Windows as the guest in VMware Player 3.1.0.

That's the hot ticket to ride!

---

### Post by Ghuloomo on 2010-07-17
Thanks, you guys just confirmed this which was really helpful. 

@dv3500ea
Dear, My kind of workflow doesn't allow me to reboot everytime. I am a photographer who is planning to use ubuntu for normal uses, and keep Windows 7 to use Adobe Lightroom, Adobe Creative suit cs5 at the time of designing. The reason I'm doing this is that if you use windows 7 for all your uses, it corrupts very fast. Stability is much better than other windows versions, but still. So I want to keep it clean, only designing programs, for the time of design need. I frequently need designing, therefor restarting everytime is not a good choice for me.

---

### Post by Ghuloomo on 2010-07-17
Another problem is that I just got an Internet Broadband connection from VIVA company in my country. It's a Huawei usb stick, with the model written on it as well. The problem is that I think it will not work on Ubuntu, therefor it will be so hard to download all the applications I need for visualization and other apps as well. I need to find a workaround for this, any suggestions?

---

### Post by fjgaude on 2010-07-17
Gosh, after you have VMware Player installed and install Windows as a VM, all you do is load all the Win apps into it, even the USB ones. Then you are good to go... you will have to do a simple patch to get USB 2.0 working. After you get everything else working come back and ask about USB 2.0 and how to add two lines to the .vmx text file in the Win VM.

---

### Post by Ghuloomo on 2010-07-17
Thank you brother for your help. Can you please tell me how can I install VMWare Player on my Ubuntu? I can't find it in the synaptic, so I downloaded it from their website. It's a .bundle file which I don't know how to install. I wished if I could get a .deb file for it.

---

### Post by fjgaude on 2010-07-18
It's easy once you know how. Run this command from a terminal.

```
sudo ./VMware-Player-...xxx.bundle
```

Do this from the folder where the Player bundle is. You will be prompted for your password and then everything else is automatic. You will find an icon in the Applications/System Tools menu of Ubuntu.

Let us know how you are doing.

---

### Post by JustinR on 2010-07-18
> **Ghuloomo said:**
> Thank you brother for your help. Can you please tell me how can I install VMWare Player on my Ubuntu? I can't find it in the synaptic, so I downloaded it from their website. It's a .bundle file which I don't know how to install. I wished if I could get a .deb file for it.

You could also try VirtualBox! Its a relatively smaller application that VMWare last time I tried it.

---

### Post by Dedoimedo on 2010-07-19
It depends on what you need. Identify your top priority and make that the default choice. If you must have games, for example, then you prolly want Windows. If you need certain programs to run natively and are only available for this or that, that will narrow down your choice further.
Dedoimedo

---

### Post by tonywhelan on 2010-07-20
> **Ghuloomo said:**
> Another problem is that I just got an Internet Broadband connection from VIVA company in my country. It's a Huawei usb stick, with the model written on it as well. The problem is that I think it will not work on Ubuntu, therefor it will be so hard to download all the applications I need for visualization and other apps as well. I need to find a workaround for this, any suggestions?

Huwaei USB 3G modems work fine in Ubuntu, it should prompt you when you plug it in - then you just need to enter the name of the "APN" (that's a network name) which should be printed on the doco from your wireless provider. Plenty of info on the web if you need to know more about that.

---

