---
title: "viruses travel from Linux to Windows and vice versa ?"
date: 2009-01-24
forum: Security
---

### Post by lse123 on 2009-01-24
viruses travel from Linux to Windows and vice versa ?

---

### Post by Dr Small on 2009-01-24
No.

---

### Post by lukjad on 2009-01-24
If you download a trojan in Ubuntu and then move it to Winsows and install it, it will infect the Windows operating system. Also, there are some forms of malware that can damage whole partitions, even whole hard drives. So, if Windows gets infected this way, or if they come up with a a way to infect Linux (Heaven forbid ;) ) then they damage each other. Though from what I've heard, this is pretty rare.

---

### Post by OrangeCrate on 2009-01-24
> **lse123 said:**
> viruses travel from Linux to Windows and vice versa ?

> If you dual boot Linux and Windows and get a virus-infected mail in Linux, it can NOT jump to your Windows partition. Nor can it spread over the local network to other systems. You can even store the attachment in your /home directory and open the zip or click the file, and it will be dead in the water. Windows executables won't run under Linux. Linux files need to be granted permission to become executable. And even then, it can't spread beyond the home folder. (This is also why Linux AV programs do not have a "live guard" module in them — the virus does not execute or move.) You could even leave a virus executable there as long as you wanted to without risk. Windows will not get infected, unless you deliberately copy the virus to your Windows partition

[http://www.linuxclues.com/articles/21.htm](http://www.linuxclues.com/articles/21.htm)

---

### Post by person9 on 2009-01-25
What about using a LiveCD? 

I have a new laptop with Windows Vista (running Norton AntiVirus) and have never had an issue. I'll be using the LiveCD in a few days, and I'm wondering if I should just keep my WiFi switch off when I am.

Is this wise? Can I get a Windows virus while using the internet off my Ubuntu LiveCD? I'd rather not infect my computer.

---

### Post by perlluver on 2009-01-25
> **person9 said:**
> What about using a LiveCD? 

I have a new laptop with Windows Vista (running Norton AntiVirus) and have never had an issue. I'll be using the LiveCD in a few days, and I'm wondering if I should just keep my WiFi switch off when I am.

Is this wise? Can I get a Windows virus while using the internet off my Ubuntu LiveCD? I'd rather not infect my computer.

No you can't since the LiveCD has no access to the Hard Drive.

---

### Post by person9 on 2009-01-25
Awesome, thanks.

Not to get too off topic, but I assume this means I can't access or save files to my hard drive?

---

### Post by Hobgoblin on 2009-01-25
> **person9 said:**
> 
Not to get too off topic, but I assume this means I can't access or save files to my hard drive?

You can access your hard drive from the live CD (perlluver is incorrect in saying the live CD has no access to the HDD).

There is no risk of being infected by a worm or virus while running from the live CD but you could get your windows system infected if you download something dodgy, save it to the Windows partition then execute it after rebooting into Windows.

Common sense is your best protection in this case.  Only download from trusted sites, virus scan the files before opening them in Windows.

---

### Post by nubdora on 2009-01-26
All live CDs allow you to read data from the HDD, but most do not allow an accessible way for the user to write data to the HDD.

---

### Post by cdenley on 2009-01-26
> **nubdora said:**
> All live CDs allow you to read data from the HDD, but most do not allow an accessible way for the user to write data to the HDD.

The last few Ubuntu releases have had write support for NTFS on the Desktop livecd. I think all they have to do is click the drive in nautilus, then they can write to it.

---

### Post by person9 on 2009-02-02
Im using Ubuntu now after having installed it through Wubi.
I allowed it only 6 Gig of space .. :(
Now I'm stuck, because it turns out I like Ubuntu and want to use it.
Dunno if I can allot it more space after-the-fact but I'm researching that.

---

### Post by cjacobsen on 2009-02-02
> **nubdora said:**
> All live CDs allow you to read data from the HDD, but most do not allow an accessible way for the user to write data to the HDD.

To be able to write data from an Ubuntu LiveCD to HDD is to become a superuser. All you need is this command

```

sudo nautilus

```

Then you can read and write on the HDD via Nautilus either it's Ext3, fat or ntfs.

---

