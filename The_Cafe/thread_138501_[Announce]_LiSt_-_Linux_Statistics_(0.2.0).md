---
title: "[Announce] LiSt - Linux Statistics (0.2.0)"
date: 2006-03-02
forum: The Cafe
---

### Post by dma147 on 2006-03-02
I want to announce a project which was in discussion a bit beside klive.

Linux Statistics [1] or LiSt how this project is called, is a client/server project which generates accurate statistics of the linux userbase and their hard- and software.
For this it provides a small client called "LiSt" which is written in python and which everybody has to install to register his machine in our database. This client application will then collect the following hard- and software information from your linux system (use "LiSt -p" to see the information which will be sent):
 
 - The installation date of your distribution
 - The hostname (no fqdn or ips)
 - The architecture (x86/i586/i686, ppc, and so on)
 - CPU information: vendor, model, number of cpus, frequencies
 - RAM
 - Swap
 - Timezone
 - user defined locales
 - Windowmanager
 - Kernel version
 - Uptime information
 - The size of mounted partitions (no shares)
 - the used filesystems
 - the complete kernel configuration (.config)
 - the complete list of loaded kernel modules (lsmod)
 - the complete X11 configuration
 - The hardware-IDs of used ISA/PCI/AGP and USB hardware

The client will send these information to our server, which stores them in our database and generates accurate statistics out of them.
**All of the collected information and data is absolutly anonymous!**

You can see an example on how your personal system overview can look like on the public system overview page of the autor of this project: [dma147' system overview](http://www.linux-stats.org/index.php?c=userpage&sys=283)
You can switch your own system overview page to be public in your preferences of your account.

**Where else can you submit your *complete* system configuration and publish it to the whole world especially in such an easy way??**

Also read our privacy policy [2] to become sure that all is anonymous and safe.
Some more information on frequently asked questions can be found in our FAQ [3].
 


Sincerely

Alex

[1] [http://www.linux-stats.org](http://www.linux-stats.org)
[2] [http://www.linux-stats.org/?c=privacy](http://www.linux-stats.org/?c=privacy)
[3] [http://www.linux-stats.org/?c=faq](http://www.linux-stats.org/?c=faq)

---

### Post by Lovechild on 2006-03-02
would xml-rpc and using HAL not make sense for something like this?

I would have no problem partaking in a project as long as I was sure it had vendor buy in, I know Fedora are looking into making a system like this for tracking hardware configurations and known issues. Ubuntu also has a hardware detection system but I'm unsure if we can get the code for that one currently and it's design.

It would be really nice to have an agreed upon standard for doing this and having it handled by a 3rd party like Linux-stats to minimize the "evil" factor (Or evilility for Lugradio fans)

---

### Post by dma147 on 2006-03-02
[QUOTE=Lovechild]would xml-rpc and using HAL not make sense for something like this?[/quote]

Well, because I really don't have a clue about these stuff, I've written it in python using the python-modules.
But sure, I'm very pleased about every critism and I want to make the project as good and portable as even possible. So can you please explain me, what xml-rpc and/or HAL would do better?

> I would have no problem partaking in a project as long as I was sure it had vendor buy in, I know Fedora are looking into making a system like this for tracking hardware configurations and known issues. Ubuntu also has a hardware detection system but I'm unsure if we can get the code for that one currently and it's design.

I'm sorry, but I think I didn't understand this part correctly.
Maybe you wonder if you can get the code of the Ubuntu-hardware-detection for using this in LiSt? Or the other way around?

> It would be really nice to have an agreed upon standard for doing this and having it handled by a 3rd party like Linux-stats to minimize the "evil" factor (Or evilility for Lugradio fans)

Well, linux does have some unofficial "standards" which are luckily used by most of the distributions. This makes most of the detection stuff relatively easy to implement.
But there are still some things which are very, very complicated and very different from distribution to distribution. The most complicated part for example is the detection of the used windowmanager and version if any, because most distributions are all using different files for configuring this.

This is the only part of LiSt which is still not really bug free. It depends on which distribution you are using and how the wm is configured.

**So a call to everybody who is using a wm but where LiStdid not detect it correctly:**
Please tell me! Either in the forums on [http://forum.linux-stats.org](http://forum.linux-stats.org), or in the bugtracker!
Thanks.

---

### Post by Lovechild on 2006-03-02
hal-device gives you a listing of all the HAL database, you could use that to gather information on the system.

---

