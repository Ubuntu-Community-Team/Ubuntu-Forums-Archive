---
title: "Noob Needs Help With VirtualBox"
date: 2016-09-25
forum: Virtualisation
---

### Post by jerdoggmckoy on 2016-09-25
Hello, I need to find some sort of preinstalled OVA file of Ubuntu, preferrably a GUI based, NOOB-FRIENDLY, install I can import into VirtualBox. Anyone able to help or point me in the right direction please? Thanks in advance!

---

### Post by &amp;KyT$0P# on 2016-09-25
What version of Ubuntu?
What version of VirtualBox?
What went wrong with installing Ubuntu from the ISO?

---

### Post by jerdoggmckoy on 2016-09-25
Virtual Box 5.1.6.

I haven't downloaded Ubuntu or tried installing by ISO because I thought I had to install on ova file. I don't have a CD drive nor do I want to try and install using a USB stick. I thought ova was the means to bypass that. #NoobIssues

So can I just import the iso file then?

---

### Post by &amp;KyT$0P# on 2016-09-25
Yes, you can just select the ISO file as the CD for the virtual machine's optical drive (the technical term for a CD/DVD reader).  This is one instance where the virtual machine hardware is not related to your physical hardware.

---

### Post by oldos2er on 2016-09-25
Thread moved to *Virtualisation*.

---

### Post by jerdoggmckoy on 2016-09-25
Awesome, thank you so much! Here are the specific instructions I had to track down to accomplish this:


[LIST=1]
[*]Right click on the VM you want to run the .iso in
[*]Click on 'Storage' (On Oracle VM virtualBox, Click on 'Settings' first to get to 'Storage')
[*]Under 'IDE Controller' There should be an icon that shows a CD with a + sign on it, to create a new disc drive
[*]A box will come up, click 'Choose Disk'
[*]Choose your .iso
[/LIST]
[COLOR=#111111][FONT=Ubuntu]Should boot into the iso like it's in the disc drive.

Thanks again![/FONT][/COLOR]

---

### Post by &amp;KyT$0P# on 2016-09-25
You're welcome!  :KS

---

