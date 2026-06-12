---
title: "Samba settings to fileserve to Mac &amp; Windows?"
date: 2010-12-13
forum: Server Platforms
---

### Post by molinus on 2010-12-13
Greetings,

I have 10.04 Lucid installed. 

It seems like Samba has already been beaten to death in these forums, but I have read 1000 different suggestions from 1000 different people, so I still have a general Samba networking question:

In order to serve files from a single Ubuntu fileserver to 3 Macs and 9 Windows XP hosts, can I get it done without configuring smb.conf as a WINS server or Domain Master, using WinBind, or setting up BIND DNS?

It seems easier to not worry about name resolution, when I can just map network drives from the clients to the server.

Thanks in advance for any pointers.

---

### Post by Bladeforger on 2010-12-13
The main hurdle is NOT the configuration of the smb.conf file--that's pretty easy.  There are some pretty good examples in the pdfs available for free download from the Samba website.

(The main hurdle for me has been the password protection that I haven't been able to quite figure out, but I'm going to get it done.)

Remember that changes you make to the config file aren't going to be seen by the workstations for a few minutes.

Keith

---

### Post by molinus on 2010-12-13
Thanks Keith.

I just found what looks like might be a very helpful guide: *Samba-3 by Example*, by John H. Terpstra.
It outlines several different networking scenarios, and the recommended approach to each scenario.
You can find it under [samba.org/docs]("http://samba.org/docs")

Happy Samba-ing!

---

### Post by Bladeforger on 2010-12-13
> **molinus said:**
> Thanks Keith.

I just found what looks like might be a very helpful guide: *Samba-3 by Example*, by John H. Terpstra.
It outlines several different networking scenarios, and the recommended approach to each scenario.
You can find it under [samba.org/docs]("http://samba.org/docs")

Happy Samba-ing!

That one is, indeed, very good.  Also, there is The Official Samba 3.2.x HOWTO and Reference Guide by Jelmer R. Vernooij, John H. Terpstra, and Gerald (Jerry) Carter May 27, 2009

I was having problems with an XP-Home virtual machine.  I had conquered a Win2k virtual machine already; however, I have ONE piece of software that requires XP or later--it just wouldn't install on Win2k.  And XP behaves differently.  XP-Home doesn't like to sign on to a domain or workgroup very well.  

What worked was system-config-samba, which you'll find in the repositories if you run Synaptic.  smbpasswd is supposed to assign user passwords and create users for you, but it didn't do it for me.  system-config-samba did it perfectly.  Now I'm up and running.  If all else fails and you haven't tried it, give it a try.  I steered away from SWAT because it removes all the comments from the smb.conf file.

Anyway, good luck.  I got my network issues fixed today, and I hope you get yours fixed SOOOOOON!!

Keith

---

