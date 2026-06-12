---
title: "VMware AMD-V is disabled, new installation"
date: 2017-12-08
forum: Virtualisation
---

### Post by cressrt2 on 2017-12-08
I cannot run VMware as the AMD-V is disabled, there are no options to activate this in the bios, so I assume I need to update the bios, however I have never done this before and cannot find any recent posts/threads on this. I have looked at this thread [https://ubuntuforums.org/showthread.php?t=318789](https://ubuntuforums.org/showthread.php?t=318789) but not sure what is still relevant and/or to my OS and am a bit reluctant to try.
My PC is an Acer with an A6-9210 processor with only Ubuntu 17.10 installed.
I have looked at the Acer site and can download the latest version but this is a zip file.
I have also looked at Virtual Box which I have used before but that needs the AMD-V activated as well!
Any suggestions?

---

### Post by QIII on 2017-12-08
Hello!

A bit more info might help people help you.

What is the model of the laptop and the BIOS and version?  UEFI install or legacy?  Do you have the user manual?

Cheers!

---

### Post by cressrt2 on 2017-12-08
Sorry,
The PC is an Acer Aspire-E5-523, the bios is set to a legacy, the System Bios is V1.09, the VGA Bios is ATI VGA  VER015.049.000.012.046738. I do not have any manual, the PC did not come with one.

---

### Post by QIII on 2017-12-08
From what I can see, enabling AMD-v is not supported by the motherboard.  Although the processor is AMD-v ready, the motherboard has to support it as well.

You might want to get in touch with Acer support to confirm that.

---

### Post by cressrt2 on 2017-12-08
I will do, however if that is the case is there any other options that I can use to run Windows, I need this for a single programme.

---

### Post by QIII on 2017-12-13
You can dual boot.  But installing Windows for dual booting after installing Linux can be a bit tricky.  Are you up for that?

You might also research your particular software and see if it will work on Wine.  The database of tested software can be found [here]("https://appdb.winehq.org/").

---

### Post by cressrt2 on 2017-12-14
I have looked at Wine, the programme is Family Tree Maker, and it gives a garbage rating! I have looked at installing Windows, it does appear to be complicated but am willing to give it a go.   The worst that could happen is that I would need to start over again but starting with Windows.
Successfully installed Win10, now alongside Ubuntu, was quite easy to install, a little bit longer to reinstall Grub, but both working well!

---

