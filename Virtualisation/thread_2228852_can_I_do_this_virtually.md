---
title: "can I do this virtually?"
date: 2014-06-09
forum: Virtualisation
---

### Post by dgermann on 2014-06-09
Friends--

Need some high level thinking here, please. No need for technical details, I suspect. 

(I have been running linux in this office environment for 10 years and am pretty comfortable with most things I have to do, and with cli.)

1. Production environment with 6 ubuntu boxes, currently 12.04 lts, one WinXP. There are some legacy programs on XP that have prevented me from going 100% ubuntu. Now with the XP eol, I wonder....

2. On the XP are Abbyy Finereader 7.0 Professional edition (with a scanner), Timeslips (which is a Win95 program running under Win95 compatibililty mode), and Quickbooks.

3. These programs are all accessed from the ubuntu workstations via rdesktop, and the WinXP box allows multiple logins.

4. The WinXP box is a workstation as well, running mainly LibreOffice.

5. The network is on an ubuntu server running samba.


Q1. So can I just buy an up to date box, put 14.04 lts on it, then virtualbox, within which I would run  WinXP, and get all the same functionality and connectivity I have now?

Q2. Should I? Is it safe? Is it cumbersome?

Q3. What else should I be asking?

Thanks!

---

### Post by sudodus on 2014-06-10
A3. what else:

- How can I get this functionality with up to date systems that receive security updates?

- How can I isolate the XP server from the internet and at the same time connect to it from other computers in the office (and still be able to connect to the internet from the other computers)?

- Or should this XP computer be run locally without any connection to the LAN?

---

### Post by dgermann on 2014-06-10
sudodus--

Thanks! Good questions indeed.

Keeping this machine off the LAN is not practical, but I ran across another post somewhere that suggested a regular restore of the virtual machine to the original disk image. That is something I am willing to do, and maybe that could be done as a cron job.

Your question about isolation: is there a way to do that? I suppose one thing would be to delete all instances of browsers and email from the virtual XP....

Thanks!.

---

### Post by TheFu on 2014-06-10
To remove the XP machine from the network, remove the network adapters. Anything less just isn't safe anymore.
The desktops could remote into the hostOS (running the VM hypervisor you select), then run XP under that ... without any networking.  I wouldn't let XP even on a safe, secure, internal network, if any other machines there can connect to the internet.

I would NOT trust Quickbooks to work under XP next year. Time to get on Win8/7 for your accounting, at least - IMHO.  It is probably time to switch timesheet programs too. When it is time to get updated tax data, the newer version will probably be necessary anyway.  Plan for that now.

A web-based timesheet program would be my go-to choice - google "timesheets sourceforge" to see some options.

As to scanners/fax/printers - check the linux compatibility for the hardware. Linux is **really, really, really** good at file, print for supported hardware.  My scanner works great too - using gscan2pdf - basically if a scanner supports SANE, you are good.  Unless the software does something special that none of the software created the last 10 yrs does - unlikely.

USB passthru to client VMs generally works and works well, but sometimes it doesn't. The only way to know is to try it.

So ... at clients we've replaced 20 out-of-support servers with 2 or 3 new servers running virtualization. The newer machines ARE that much more powerful.  The most fun was having them sell their 25KVA UPS and replace it with a 4K UPS.  Helped pay for the new servers and the monthly power and lower cooling costs were great for the client.  

Dumping Windows whenever possible also reduces license costs, tracking, CALs, hassles.  It is hard to remove MS completely, but we can keep trying. ;)  Keep fighting the good fight!

---

### Post by dgermann on 2014-06-10
TheFu--

You do good things for your clients, fighting the good fight!

Thanks for helping me think this through.

A couple of notes to let you know I am following you, but might not come to the same conclusions as you. 1. The accounting stuff we use now primarily as an accounts payable listing of bills due. So updating might be better done with a Linux program. Recommend any? GnuCash is in the repositories.

2. For the same reason we have not been updating Quickbooks in years, so tax tables are irrelevant for us. My wife does this and prefers to calculate the 3-4 payroll checks manually from a paper Circular E.

Is there some other reason you don't think QB (mine is 6.0) will run under XP next year?

3. Abbyy is for OCR. I keep looking every year and so far have not found anything I like. Close is Abbyy's buy it as a service from them, and the cost seems reasonable, at first glance. So perhaps I can get that going under Linux.

4. I will check out your sourceforge timesheets and see what I see this year. Timeslips for an upgrade would cost me $1344 for 5 seats (I only need 4). That is just hard to swallow when I have something that works.

Thanks. You have given me some things to think through!

---

### Post by TheFu on 2014-06-11
Can't recommend any Linux-based accounting stuff - I lost that battle years ago. Not worth fighting inside my company.

OCR has come a long way on Linux.  gscan2pdf.

sourceforge is just a software project website - not mine - that has historically provided free project hosting for Linux and F/LOSS software projects.  If I don't know what I want, it is near the top of my search list.  Other, similar websites can be found here: [http://alternativeto.net/software/sourceforge/](http://alternativeto.net/software/sourceforge/)

If you don't change the software on XP and don't update anything around it, I cannot imagine why it would stop working - though Intuit does remove feature connections (thru the internet) from older software annually as a way to force upgrades. If you aren't using any of that network stuff, then I doubt it matters to you. The software is already broken if it doesn't handle the tax calculations according to our accountant.

---

### Post by KillerKelvUK on 2014-06-12
Hey Doug, what about running the XP apps in Wine on the linux box(es)?  WineHQ seems to report Abbyy and Quickbooks were functional at the software levels you've reported?

Finereader 7.0 [https://appdb.winehq.org/objectManager.php?sClass=version&iId=2971](https://appdb.winehq.org/objectManager.php?sClass=version&iId=2971)
Quickbooks 6.0 [http://appdb.winehq.org/objectManager.php?sClass=version&iId=868](http://appdb.winehq.org/objectManager.php?sClass=version&iId=868)
Timeslips ...erm not in the HQ but doesn't stop you trying it out and fiddling around.

Would get rid of XP if you can get them functional.

---

### Post by dgermann on 2014-06-16
KillerKelvUK--

Thanks! It may be time for me to try out Wine again. Last I tried, about a year ago, I was not able to figure out how to get Quickbooks to install.

But I wonder if Virtualbox would be easier, or perhaps more reliable. Have you compared the two?


@TheFu--

Tried gscan2pdf over the weekend, but it sure does not give me easily searchable results, such as I get with Abbyy: I can open an Abbyy produced pdf in evince and do a search there and find the text in the document. But with the results produced by gscan2pdf, it says 7 results on this page, but they are not highlighted. Perhaps I am using the results the wrong way, using the wrong viewer? How do you make this work?

---

### Post by KillerKelvUK on 2014-06-17
> **dgermann said:**
> KillerKelvUK--

Thanks! It may be time for me to try out Wine again. Last I tried, about a year ago, I was not able to figure out how to get Quickbooks to install.

But I wonder if Virtualbox would be easier, or perhaps more reliable. Have you compared the two?


When I've tested out Wine (Win version of Steam client + game) I used the PlayOnLinux (POL) application to carryout the Wine management i.e. Wine version download+install and config parameters as well as then the application installation...for Steam I simply pointed it at the .msi archive and POL resulted in a list of files the installer had put into the wine prefix, I simply had to select the main application executable which was then symlinked into the POL interface for easy access.

[http://www.playonlinux.com/](http://www.playonlinux.com/)
Some other promising references here...[http://ubuntuforums.org/showthread.php?t=2098181](http://ubuntuforums.org/showthread.php?t=2098181)

The main plus for using Wine vs. Virtualbox given your requirements is the removal of the Win XP operating system completely and thus the resulting vulnerability/risk mitigation.  I do however like virtualbox, tested it extensively from a SOHO perspective but settled with using KVM/qemu for OS virt.

---

