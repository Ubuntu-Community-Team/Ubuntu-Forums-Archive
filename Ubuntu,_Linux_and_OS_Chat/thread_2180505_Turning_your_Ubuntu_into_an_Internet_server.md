---
title: "Turning your Ubuntu into an Internet server"
date: 2013-10-13
forum: Ubuntu, Linux and OS Chat
---

### Post by Rebelli0us on 2013-10-13
I think Linux has an advantage here over Windows that is being unused.

For example, there are millions of people that would prefer to host their own videos instead of using Youtube, no need to upload, convert etc. Also, commercial sites like youtube impose censorship, and are pushing advertisements to your users.

It looks like one would have to set up an FTP server. Install Pure-FTP server in Synaptic package manager. Setup port forwarding config for the NAT router. Setup the FTP daemon and the NAT router to use PASV for the FTP server. Use something like Namecheap as a domain registrar and DDNS service

That ‘s way too technical for me and most users. It would be great if Ubuntu came with all that installed, it would help the Linux platform.

Can somebody post step-by-step instructions that anyone can follow?

---

### Post by JKyleOKC on 2013-10-13
> **Rebelli0us said:**
> That ‘s way too technical for me and most users. It would be great if Ubuntu came with all that installed, it would help the Linux platform.

Can somebody post step-by-step instructions that anyone can follow?It already does, if you install the Server version and select the appropriate servers from the menus offered during its installation.

Unfortunately for your hopes, that would be WAY more technical than the process to which you object. For starters, the Server version doesn't include a desktop at all. It's all run from the command line. And configuring your own web server means that you must account for every detail -- and take care of security yourself, to keep the bad guys from taking over your system and conscripting it into their armies of 'bots.

The installer provides the step-by-step instructions you seek, but assumes that you have the technical knowledge to perform each of the steps. Until some genius manages to implement the "Do What I Mean" instruction in a CPU, that's the best that can be offered, sorry...

---

### Post by Rebelli0us on 2013-10-13
What I'd like is under Preferences you select an option "**Enable Internet Server**". You appoint a "public" directory, and anything you put in there is browseable from the web. No techno-gibberish for the average user.  It's very doable. Where are all the creative devs? :popcorn:

---

### Post by sandyd on 2013-10-13
**[moved to Linux talk]**

---

### Post by sandyd on 2013-10-13
> **Rebelli0us said:**
> I think Linux has an advantage here over Windows that is being unused.

For example, there are millions of people that would prefer to host their own videos instead of using Youtube, no need to upload, convert etc. Also, commercial sites like youtube impose censorship, and are pushing advertisements to your users.

It looks like one would have to set up an FTP server. Install Pure-FTP server in Synaptic package manager. Setup port forwarding config for the NAT router. Setup the FTP daemon and the NAT router to use PASV for the FTP server. Use something like Namecheap as a domain registrar and DDNS service

That &#8216;s way too technical for me and most users. It would be great if Ubuntu came with all that installed, it would help the Linux platform.

Can somebody post step-by-step instructions that anyone can follow?
I introduce you to [pureadmin]("https://apps.ubuntu.com/cat/applications/pureadmin/"), which would probably benefit from a stripped down simpler user interface...

anyways, unless your doing upnp, the router isnt going to
a) set a static ip for the host via static dhcp
b) automatically open ports unless your configuring it via upnp
both of which is already a problem for your average user.

---

### Post by Iowan on 2013-10-13
My ISP agreement stipulates "No servers". I presume they mean "no Internet-accessible servers", since I have a few servers (DNS/DHCP, SAMBA, Apache) hiding behind my router. **"Enable Internet Server"** would/might need to include router modification, which would involve some "techno-gibberish for the average user" - unless the script was smart enough to auto-adjust whatever router might be attached.

---

### Post by mastablasta on 2013-10-16
then there is something like Zentyal which is made from the ground up for GUi non technical non command users. or clearOS.

---

