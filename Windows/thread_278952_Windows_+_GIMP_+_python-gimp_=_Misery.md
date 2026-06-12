---
title: "Windows + GIMP + python-gimp = Misery"
date: 2006-10-17
forum: Windows
---

### Post by Grey on 2006-10-17
I've been forced to taint my beautiful laptop with Windows once more for the purposes of work.  Being an exclusive Linux user for the last 2 years, with the exception of the odd game... needless to say, I am going absolutely nuts.  It's not that I don't know how to administer Windows, it's just that I've long since tired of it.

Anyways, down to the point, I have been trying to get Python-Fu working in Windows for the last two hours.  Python-GTK installs and functions just fine.  GIMP installs and runs just fine.  I select Python-Fu to be installed with the GIMP.  But lo and behold, 20 installs later, along with various tweaks, I still cannot run the scripts that I need, and I am seriously considering writing my own crappy program to do the job of the scripts.

So, I am begging for help.  Has ANYONE ever gotten Python-Fu working in Windows?  Or am I going to be forced to reboot every 10 minutes for the next few days everytime I want to edit an image?  I've tried googling for answers, but all I see are people in the same boat as me.

---

### Post by kopilo on 2006-10-17
The only imaging program I have got Python to work with on windows is Paint Shop Pro.
:(

Hope you work something out.

---

### Post by Dr. C on 2006-10-21
> **Grey said:**
> I've been forced to taint my beautiful laptop with Windows once more for the purposes of work.  Being an exclusive Linux user for the last 2 years, with the exception of the odd game... needless to say, I am going absolutely nuts.  It's not that I don't know how to administer Windows, it's just that I've long since tired of it.

Anyways, down to the point, I have been trying to get Python-Fu working in Windows for the last two hours.  Python-GTK installs and functions just fine.  GIMP installs and runs just fine.  I select Python-Fu to be installed with the GIMP.  But lo and behold, 20 installs later, along with various tweaks, I still cannot run the scripts that I need, and I am seriously considering writing my own crappy program to do the job of the scripts.

So, I am begging for help.  Has ANYONE ever gotten Python-Fu working in Windows?  Or am I going to be forced to reboot every 10 minutes for the next few days everytime I want to edit an image?  I've tried googling for answers, but all I see are people in the same boat as me.

One suggestion is virtualization. One can run an XP guest in VMware with an Ubuntu host and I understand it can also be done the other way around. It may be simpler to just install Ubuntu in a VM on top of XP.

---

### Post by Grey on 2006-10-22
I've considered that, but I really loathe the idea of VMs.  Besides, I already spent a day wrangling some functionality out of Windows.  The original question in this thread isn't as big of an issue as it once was though, as I have written my own tool to do the job.  That's made it a bit easier.

Let me explain though.  I recently was hired as a Nintendo DS developer, and that's why I am using Windows.  I have a special piece of hardware that I connect to my laptop with a USB connection.  Since it's proprietary confidential hardware, only Windows drivers exist, and it's very integrated with Windows software (CodeWarrior).  If I were to use a VM at some point, would I be able to install drivers for my hardware?  That's the thing that's really been worrying me, in that I'm not sure how that would work.

But I would LOVE to see my Linux partition again.  I miss it.

---

### Post by kopilo on 2006-10-23
Maybe look into one of those install on top of Windows Distributions such as [mulinux]("http://mulinux.dotsrc.org/dos_install.html"), I used dragon linux a long time ago but I can't remember exactly how it works. From what I remember you can load up linux on a windows OS but it isn't an emulation or a virtual engine. I think it only loads the Linux side if you have the boot disk in the drive, otherwise it boots Windows.

The drivers probably could only work on linux if you were to hack them or create a hack for them, in either case I don't recommend doing that on many different grounds.

Cool that you worked out a way around the original problem.

---

### Post by Dr. C on 2006-10-23
I would run Windows as the host in this case. It is possible to run Ubuntu using VMware on Windows XP or Windows 2003. If fact one can download a preconfigured Ubuntu Dapper VM from the VMware site 

[http://www.vmware.com/vmtn/appliances/directory/]("http://www.vmware.com/vmtn/appliances/directory/")

Just install VMware player on Windows XP or 2003, and run your Ubuntu VM.

---

### Post by Grey on 2006-10-24
Fair enough.  Sounds like a no-go for me then.  :(  I have allocated about 95% of my hard drive for Linux partitions, so I am stuck with a 8GB C drive in Windows.  That's not a whole lot of space, and I can't really spare that much space for user preferences.  Really, I just prefer the Linux versions of most software that I use.  And system administration is easier in Linux.  Anyways, thanks for your help guys.  :)

---

### Post by edwagner on 2006-10-31
I have gotten Python to work with Gimp on Windows (ActiveState Python 2.4, gtk 2.8, Gimp 2.3.12) after experiencing much the same frustration as you. The key for me was that I had neglected to install pycairo in addition to pygtk ([http://www.pcpm.ucl.ac.be/~gustin/win32_ports/)](http://www.pcpm.ucl.ac.be/~gustin/win32_ports/)). Once I installed pycairo and forced Gimp to recreate my user files (i.e. re-register plug-ins), all was well.

-- Ed

---

### Post by Grey on 2006-11-09
The need for it has since passed... but thank you very much.  I'll try that the next time that I have such a need.  =)

---

