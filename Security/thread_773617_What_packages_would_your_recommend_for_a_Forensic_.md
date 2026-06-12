---
title: "What packages would your recommend for a Forensic Laptop"
date: 2008-04-29
forum: Security
---

### Post by felixdzerzhinsky on 2008-04-29
I have installed Ubuntu Hardy on my laptop with Windows XP Professional running in Virtualbox (close source edition. (I couldn't get the usb and filesharing to work in virtualbox-ose)What packages would you recommend for forensic work? I am interested in  Ubuntu, other linux (compile from source or alien) and Windows XP programs.

Thanks

---

### Post by fxw1121 on 2008-04-29
I would also like to know

[http://www.c9c8.net/]("http://www.c9c8.net/")

---

### Post by pytheas22 on 2008-04-29
I'm not sure exactly what kind of forensics stuff you want to do, but Nessus (network scanner and security evaluator), nmap (port scanner) and snort (packet inspection) are the top three programs that come to mind for basic security stuff.  OSSEC (ossec.net --there's no package; you have to compile from source but it's easy) is also really nice if you are looking for ways to secure your machine or a network, or as a means of centralizing other security software (because OSSEC can read the logs of snort and lots of other things, and report stuff to you at a centralized location).

---

### Post by lemming465 on 2008-04-30
If you want to play around with stuff, Linux distributions specialized for the task at hand are a good route.

For disk forensics, maybe [Helix]("http://www.e-fense.com/helix/")
For network forensics, perhaps [Knoppix-STD]("http://knoppix-std.org/tools.html")
For penetration testing, [Backtrack]("http://www.remote-exploit.org/backtrack.html")

If you just want to find tools to add to an existing distribution, an excellent list of candidates is [Insecure top 100 security tools]("http://sectools.org/")

---

### Post by felixdzerzhinsky on 2008-05-01
Thanks for the replies.

I have since found this:

[http://www.ubuntugeek.com/list-of-security-tools-available-in-ubuntu.html#more-474](http://www.ubuntugeek.com/list-of-security-tools-available-in-ubuntu.html#more-474) 

and 

[http://ubuntulinuxhelp.com/digital-forensics-in-linux-reclaiming-data-off-a-failed-hard-drive/](http://ubuntulinuxhelp.com/digital-forensics-in-linux-reclaiming-data-off-a-failed-hard-drive/)


> I'm not sure exactly what kind of forensics stuff you want to do...

At this stage I am mostly going to use my personal laptop for learning. However I am looking to get a laptop procured by my organisation. 

I am also interested in the physical stuff such as evidence bags, cables etc. If I want it I need to procure it at the same time.

I am hoping this will be useful for other people wanting to start out in forensics.

---

### Post by felixdzerzhinsky on 2008-08-04
**Getting started, or forensic analysis on the cheap **

[http://windowsir.blogspot.com/2008/02/getting-started-or-forensic-analysis-on.html](http://windowsir.blogspot.com/2008/02/getting-started-or-forensic-analysis-on.html)

**Forensic Analysis Applications **

[http://windowsir.blogspot.com/2008/07/forensic-analysis-applications.html](http://windowsir.blogspot.com/2008/07/forensic-analysis-applications.html)

---

### Post by /////// on 2008-08-05
Backtrack 3

---

### Post by felixdzerzhinsky on 2008-08-06
[http://homes.esat.kuleuven.be/~decockd/site/myHowTos/applications/viewers_for_browser_cookies,_index.dat,.../index.html](http://homes.esat.kuleuven.be/~decockd/site/myHowTos/applications/viewers_for_browser_cookies,_index.dat,.../index.html)

and

[http://www.foundstone.com/us/resources-free-tools.asp](http://www.foundstone.com/us/resources-free-tools.asp)

Thanks for the responses so far. I hope they are useful for other people.

---

### Post by pigphish on 2008-09-13
How is read-only usb drive access accomplished?

---

### Post by pytheas22 on 2008-09-13
> How is read-only usb drive access accomplished?

Are you thinking about [TrueCrypt]("http://www.truecrypt.org")?

---

### Post by CarrotRevelation on 2008-09-13
> How is read-only usb drive access accomplished?

Google "Write Blocking". There is a bunch of good pdf's, slideshows, and technical papers out there.

---

### Post by CarrotRevelation on 2008-09-13
> **felixdzerzhinsky said:**
> I have installed Ubuntu Hardy on my laptop with Windows XP Professional running in Virtualbox (close source edition. (I couldn't get the usb and filesharing to work in virtualbox-ose)What packages would you recommend for forensic work? I am interested in  Ubuntu, other linux (compile from source or alien) and Windows XP programs.

Thanks

Security and Forensics are two similar but very different fields. Backtrack3, Nessus, Retina, Metasploit, Knoppix-std...etc, etc would all be great to use if you are trying to find out what types of changes an attack causes to memory and physical devices.

_What you really want is this. _
[http://www.forensicswiki.org]("http://www.forensicswiki.org")
[http://www.myharddrivedied.com/]("http://www.myharddrivedied.com/")
You may need this one one day =>[http://muchtall.com/modules.php?name=News&file=article&sid=194]("http://muchtall.com/modules.php?name=News&file=article&sid=194")

There are some good live linux distro's like DEFTv3x, Helix, FCCU
Some good reads are techical papers on ATA, OHCI, EHCI, UHCI.
Also, you may want to know how a file is constructed (i.e. JFIF).

I mostly use Linux for forensics training, but I also find myself using VMWare (Check out live View). Also, a lot of Windows based file recovery software (file carving) is loaded with file definitions/headers. Testdisk is also good on Windows.

I guess I could go on forever, but the bottom line is that ForensicsWiki.org has more than enough information to get you started.

---

### Post by felixdzerzhinsky on 2010-02-28
Been a while since I looked at this thread.

I just want to thank some of the previous posters. There are some useful links here.

---

