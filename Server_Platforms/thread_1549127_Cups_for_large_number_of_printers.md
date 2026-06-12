---
title: "Cups for large number of printers"
date: 2010-08-09
forum: Server Platforms
---

### Post by hosseinyounesi on 2010-08-09
Hi everybody,

How many printers can a single Cups computer handle? Cups will use different queue for each printer? How about CPU usage and memory? Has Cups tested for large number of printers (say 100 up to 200) before?

Thanks in advance

---

### Post by arrrghhh on 2010-08-09
We use CUPS for hundreds of printers (probably 500 or so) and it works great.  Yes, there's a separate queue for each printer.

As far as CPU usage/memory, I'm not sure what hardware our CUPS server is running on... I'd imagine you'd need a fairly beefy server if you're going to run several hundred printers thru it.  RAM is probably more important than processor in this case.

---

### Post by hosseinyounesi on 2010-08-10
thanks "arrrghhh",

I found this page in cups official web site:
[[COLOR="Red"]System Requirements Estimator - Documentation - CUPS[/COLOR]]("http://www.cups.org/estimator.php")

Would you mind please check this out, fill the form and send me the output? Then we will try to compare your hardware and the system requirement suggested by cups.
It will help me a lot.
Thanks in advance

---

### Post by arrrghhh on 2010-08-10
Uhm... I don't know what hardware we're running CUPS on at present.  I also don't really know how many printers we have in the network, I'm just guessing based on how many branches we have, etc.

Unfortunately I don't have access to this stuff any longer as I no longer work in the dept that manages CUPS for the company.

Looks like you found a great sys req estimator, just put in your numbers and see what comes out!

---

### Post by hosseinyounesi on 2010-08-11
Thanks again,
> We use CUPS for hundreds of printers (probably 500 or so) and it works great. Yes, there's a separate queue for each printer.

You are using a SINGLE CUPS server for all printers OR a CUPS server for each location (department, school, ...) ?

Thanks in advance

---

### Post by arrrghhh on 2010-08-11
Single CUPS server for all printers.  We're a bank, with roughly 135 locations.  Several are out of state as well...

Now it doesn't do ALL of our printing... it only handles a certain type of printing that we generate reports from.  Mind you this doesn't mean it's used lightly - it's used quite heavily in the mornings - each bank will queue up 20 or so docs that are sometimes very long documents.

I just didn't want you to think we do ALL of our printing thru CUPS.  Workstation printing (from word, etc) is done thru IP directly from the machine to the printer.

---

### Post by hosseinyounesi on 2010-08-12
And another question:

Sharing printer via samba for windows users needs to copy that printer driver's in samba share. What should I do for more than one printer? Have I to install all of printers in one windows and then copy the files to samba share? What should I do to append a printer later?

Thanks in advance

---

### Post by hosseinyounesi on 2010-08-12
There is one more question:

Since all printers are shared via samba, all users can see all of the printers on samba share (although they can print only to some of them). Any way to tell samba (or any other way) to show available printers for each location?

Thanks in advance

---

### Post by arrrghhh on 2010-08-12
We use IP printing, so no sharing/samba.  All our printers are network-aware.

---

### Post by hosseinyounesi on 2010-08-15
Thanks again arrrghhh,

How CUPS handles simultaneous jobs? Consider this situation:
Job_1 arrives to CUPS for printer_1 and CUPS begins to send it the printer, job_2 arrives for printer_2 while job_1 is printing to printer_1. Which one will happen:
1. Job_2 has to wait for printing on printer_2 until job_1 finishes.
2. While these are two different jobs to two DIFFERENT printers and there is one independent queue for each printer, Job_1 and Job_2 will be printed simultaneously.

Thanks in advance

---

### Post by arrrghhh on 2010-08-16
I believe in that situation they'd be printed simultaneously... CUPS can spool jobs to many printers at once, although I've never actually tested it myself.

I'm sure there's tons of queue-related settings within CUPS as well...

---

### Post by LightningCrash on 2010-08-16
> **arrrghhh said:**
> We use CUPS for hundreds of printers (probably 500 or so) and it works great.  Yes, there's a separate queue for each printer.

As far as CPU usage/memory, I'm not sure what hardware our CUPS server is running on... I'd imagine you'd need a fairly beefy server if you're going to run several hundred printers thru it.  RAM is probably more important than processor in this case.

I run about a hundred printers through an UltraSPARC-IIe 500MHz w/ 1GB of RAM.

---

### Post by hosseinyounesi on 2010-08-17
Thanks to arrrghhh and  LightningCrash,

Would you mind tell me more about your Hardware server and CUPS configurations, LightningCrash? You have heavy jobs on your CUPS server or how many simultaneous jobs? the average jobs per day?
How about windows users? You are using SAMBA? or all the printers are network printers?

Thanks in advance

---

### Post by LightningCrash on 2010-08-17
> **hosseinyounesi said:**
> Thanks to arrrghhh and  LightningCrash,

Would you mind tell me more about your Hardware server and CUPS configurations, LightningCrash? You have heavy jobs on your CUPS server or how many simultaneous jobs? the average jobs per day?
How about windows users? You are using SAMBA? or all the printers are network printers?

Thanks in advance

It's a Netra T1 I got with an E5000. It's not much of a box at all. CUPS is an older version that installed on Solaris 8.
I generally only accept Oracle output, everything is PostScript. We do some large batch runs on line printers in the control room (maybe 1000 pages duplex per job?), and lots of little jobs everywhere else. The organization has 900 employees.
I'll get you more specifics tomorrow if I can. Maybe some sar stats thrown in too.

---

### Post by LightningCrash on 2010-08-18
Yesterday we printed 669 jobs. This includes reformatting every job submitted with PStoPS.
Sar indicates that the box's CPU was 99% idle during that time, and on average it had 850MB of memory free (out of 1024MB)

This is well-formed, well-handled PostScript output from Oracle, though. If you have Suzy Secretary printing a 100 page word document with 1024x768x32bpp bitmaps on every page, a lot of things are going to choke.

---

### Post by spynappels on 2010-08-18
Forgive my ignorance, but how are these multiple printers connected to the CUPS server? I presume it is not through lots and lots of USB hubs, and how are older printers without USB support catered for?

---

### Post by arrrghhh on 2010-08-18
> **spynappels said:**
> Forgive my ignorance, but how are these multiple printers connected to the CUPS server? I presume it is not through lots and lots of USB hubs, and how are older printers without USB support catered for?

Oh heck no.  All of our printers have NICs, we IP print to everything.  I don't think there's a single printer on our network that isn't IP capable... even our "old" ones.

---

### Post by LightningCrash on 2010-08-18
> **spynappels said:**
> Forgive my ignorance, but how are these multiple printers connected to the CUPS server? I presume it is not through lots and lots of USB hubs, and how are older printers without USB support catered for?

Nothing here is connected via USB. Everything is networked.
I'm sure any older parallel port printers are on JetDirect print servers.

---

### Post by spynappels on 2010-08-18
OK, that makes a lot more sense. I presume these printers do not have integrated print servers like the two printers I have at home? If they do, is the advantage of using the CUPS just that they can all be accessed from one IP address, or are there other benefits too?

I presume it would work fine with USB printers too though?

---

### Post by LightningCrash on 2010-08-18
> **spynappels said:**
> OK, that makes a lot more sense. I presume these printers do not have integrated print servers like the two printers I have at home? If they do, is the advantage of using the CUPS just that they can all be accessed from one IP address, or are there other benefits too?

I presume it would work fine with USB printers too though?

CUPS gives my operations and helpdesk people a centralized way to manage all of the printers in the building. If operations is printing a large report on the line printer and need to stop their job, they can. Our line printers, while they support lpr, don't have queue control at all.

It also gives me the opportunity to fix fonts, insert fonts and fix formatting on screwed up outputs. This is very important when printing mailer barcodes and etc.

---

### Post by arrrghhh on 2010-08-18
Ditto.  We use it to have one central location to manage the printers.  Each of our printers does have its own queue, but printing from clients is a lot more difficult to manage than printing from a central location.  Plus because of the types of reports we print thru CUPS, it's not really possible to have the clients print (it's a very automated process that grabs reports from a server for the user...)

So we don't exactly use CUPS in what I would describe as 'standard manner'.  We only use it for mainframe jobs/reports basically.

---

### Post by hosseinyounesi on 2010-08-18
Thank you all,

What do you suggest me to use as an operating system? How about ubuntu 10.04 server? If no, so how about opensuse, fedora and centos? Anything to consider about Windows users while some of printers are not networked? 

Thanks in advance

---

### Post by arrrghhh on 2010-08-18
Well, any of those servers would work just fine.  If you want help in here, run Ubuntu.  If you're more familiar with another server distro, I'd encourage you to use that one.

We basically have all of our linux servers running SLES, so that's what our CUPS server is running on.  They should all be able to run a CUPS server, they all just have their own little idiosyncrasies.

---

