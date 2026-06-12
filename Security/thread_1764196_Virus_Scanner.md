---
title: "Virus Scanner"
date: 2011-05-21
forum: Security
---

### Post by MidnightbluRose on 2011-05-21
Hello,  What is a good virus scanner for Ubuntu?  I need to send some files over to a Windows computer and want to make sure that they are good to go!  Thanks, MBR

---

### Post by 73ckn797 on 2011-05-21
Avast has a Linux version and there is also Clamscan in the repositories. Both will work just fine.

[http://www.avast.com/linux-home-edition](http://www.avast.com/linux-home-edition)

---

### Post by MidnightbluRose on 2011-05-21
> **73ckn797 said:**
> Avast has a Linux version and there is also Clamscan in the repositories. Both will work just fine.

[http://www.avast.com/linux-home-edition](http://www.avast.com/linux-home-edition)

 Avast will install but it won't start.  Is ClamTK the same as clamscan?

---

### Post by yetiman64 on 2011-05-21
> **MidnightbluRose said:**
> Avast will install but it won't start.  Is ClamTK the same as clamscan?

If you want to get Avast working in Ubuntu you need to adjust the kernel.shmmax value. This is because the virus database of Avast is too large for the default shared memory value set in the kernel.

To fix it you can follow the instructions here :[[COLOR=Blue] http://ubuntuforums.org/showpost.php?p=9512526&postcount=9[/COLOR]]("http://ubuntuforums.org/showpost.php?p=9512526&postcount=9")

I used the value of 100000000 in those instructions, though I usually see the value of 128000000 given elsewhere. I suggest you use 128000000 to allow for further growth in the virus database (should be ample size).

---

### Post by gandaran on 2011-05-21
> **MidnightbluRose said:**
> Hello,  What is a good virus scanner for Ubuntu?  I need to send some files over to a Windows computer and want to make sure that they are good to go!  Thanks, MBR
[http://www.tuxradar.com/content/get-best-virus-scanner-linux](http://www.tuxradar.com/content/get-best-virus-scanner-linux)

---

### Post by weezyrider on 2011-05-21
I bought Eset's NOD32. I've used it on windows computers since it first came out.

---

### Post by Mr. Shannon on 2011-05-21
I would wither go with **clamtk**, but that is better for scanning an entire directory.  If you just what to scan a few files before you send them to a Windows computer then I would use **nautilus-clamscan**.  It allows you to scan files with a menu entry in nautilus.

I can't say anthing about how good they are since I never found a virus on my computer since switching to Ubuntu and I have not used nautilus-clamscan.

---

### Post by z61t on 2011-05-21
Been using Ubuntu for almost a week now, do I really need an antivirus or firewall?

---

### Post by rbowen1 on 2011-05-21
> **yetiman64 said:**
> If you want to get Avast working in Ubuntu you need to adjust the kernel.shmmax value. This is because the virus database of Avast is too large for the default shared memory value set in the kernel.

To fix it you can follow the instructions here :[[COLOR=Blue] http://ubuntuforums.org/showpost.php?p=9512526&postcount=9[/COLOR]]("http://ubuntuforums.org/showpost.php?p=9512526&postcount=9")

I used the value of 100000000 in those instructions, though I usually see the value of 128000000 given elsewhere. I suggest you use 128000000 to allow for further growth in the virus database (should be ample size).


Followed [yetiman64]("http://ubuntuforums.org/member.php?u=1043255")  instructions and worked great.  Just finished a completed a through scan on all files with current virus definations

---

### Post by syntr on 2011-05-21
> **z61t said:**
> Been using Ubuntu for almost a week now, do I really need an antivirus or firewall?
Only as a precaution if you're going to be sending executable files to a Windows machine.

---

### Post by Lateralis on 2011-05-21
> **z61t said:**
> Been using Ubuntu for almost a week now, do I really need an antivirus or firewall?

As an individual user, no, not really.  I've personally never used an antivirus as there are no viruses which target desktop/laptop users.  

But, if you're going to be extensively sharing or distributing files and executables with users of Windows, then you might consider a virus scanner to ensure these files are clean, as a courtesy towards these other computer users.  But Windows viruses do not run on Linux, so you will be entirely safe from such things.

---

### Post by uRock on 2011-05-21
> **z61t said:**
> Been using Ubuntu for almost a week now, do I really need an antivirus or firewall?

No. The firewall is built in already and as long as you do not install an server services you will not havve any ports open to the public. If you want to make your PC invisible to other hosts, then simply run **sudo ufw enble** in a terminal or install GUFW via the Ubuntu Software Center or Synaptic Package Manager, then you can enable/disable the firewall as well as open/close/block ports.

I have AV installed, but I have not come across a Linux virus yet. Most of them are decent for scanning files prior to sharing them with a Windows system. [BitDefender]("https://help.ubuntu.com/community/BitDefender") is my choice for that operation.

---

### Post by nemilar on 2011-05-21
In response to the original poster's question, I wanted to make sure it's clear that antivirus programs for Linux detect Windows viruses.  The purpose of these programs is two fold:
[LIST]
[*]Prevent you from passing along a virus to a Windows machine
[*]For linux-based servers with Windows clients (file servers especially)
[/LIST]

I've written about this more extensively on my blog: [Do I need an antivirus program on Linux?]("http://techthrob.com/2009/03/02/do-i-need-an-antivirus-program-on-linux/")

For the company I work for, we have a Linux-based jumphost that is used to transfer files in and out of our datacenter.  Everything that gets transferred to/from the datacenter has to go through this jumphost, and ClamAV is configured to automatically scan all files for viruses.  In this way, the Linux box (impervious to the viruses) serves as a gate-keeper, keeping the environment clean.

---

### Post by z61t on 2011-05-21
> **syntr said:**
> Only as a precaution if you're going to be sending executable files to a Windows machine.

That's what I needed to know. kool. Thanks!

---

### Post by MidnightbluRose on 2011-05-21
> **yetiman64 said:**
> If you want to get Avast working in Ubuntu you need to adjust the kernel.shmmax value. This is because the virus database of Avast is too large for the default shared memory value set in the kernel.

To fix it you can follow the instructions here :[[COLOR=Blue] http://ubuntuforums.org/showpost.php?p=9512526&postcount=9[/COLOR]]("http://ubuntuforums.org/showpost.php?p=9512526&postcount=9")

I used the value of 100000000 in those instructions, though I uUser Namesually see the value of 128000000 given elsewhere. I suggest you use 128000000 to allow for further growth in the virus database (should be ample size).

Worked great thanks!

Question about bitdefender.  I hear people recommending it but when I search for bitdefender linux the page I go to for it wants me to buy it.  It's not free.

---

### Post by uRock on 2011-05-21
> **MidnightbluRose said:**
> Worked great thanks!

Question about bitdefender.  I hear people recommending it but when I search for bitdefender linux the page I go to for it wants me to buy it.  It's not free.

There is a link to the Ubuntu doc page in my above post explaining how to install it with a free one month key, then it explains how to go to the BitDefender site to get a one year key for free. [https://help.ubuntu.com/community/BitDefender](https://help.ubuntu.com/community/BitDefender)

---

