---
title: "Printer problems"
date: 2009-02-18
forum: System76 Support
---

### Post by pseudotheist on 2009-02-18
Hey, not sure this is the right forum for this one, but I didn't see a better one...

I have a Darter Ultra running Ibex, and a networked HP Officejet J6450.  I had it setup just fine using hp-setup, but yesterday it broke.  When I try to print, the printer displays a status of "/usr/lib/cups/filter/foomatic-rip failed".  I tried deleting and re-installing the printer, but that didn't help.  I'm wondering if it might have anything to do with recent system updates, but can't figure out where to look at those.  I got troubleshooting logs (attached), but can't parse them well enough to figure out what's up.  Help?

---

### Post by Lee_Machine on 2009-02-18
When you say networked, do you mean you have the printer hooked into another computer acting as a print server? Is the other computer turned on?

---

### Post by pseudotheist on 2009-02-19
The printer itself has an IP address assigned through static DHCP.  I'm pretty sure network connectivity still works, because every time I try to print it spits out a blank page.

---

### Post by Lee_Machine on 2009-02-19
Ah ok, its an actual printer with networking capabilities. I'm used to having either 1) use a printer server, or 2) hook it into my wireless router. Both via USB.


So it's getting the signal. Have you tried printing a test page? Checked the ink? Try hooking the printer straight into the darter, and see if that works. Can you print from another computer? I know that this may sound stupid, but you always troubleshoot starting with the easiest stuff.

---

### Post by pseudotheist on 2009-02-19
Apparently I'm narrow-minded, reactionary, and incompetent.  It prints the test page just fine, as well as .pdfs and .jpgs, just not this particular .jpg.  I guess that makes it a file issue and not a printer issue.

Thanks!

---

### Post by 2scott on 2009-02-21
Hello - sorry for butting into this thread - but I have a similar problem and hope you can help me.

I am running 8.10 and trying to print to an HP Deskjet D1320 vi a Linksys wireless printsrever WPS54-G RM.  It works when I am running windows.  I can see the printserver on the Ubuntu network.  I think I may need a LINUX driver - but can't find one.

Any recommendations would be most appreciated.

Thanks

---

### Post by 2scott on 2009-02-21
I did find a link at the HP site for a LINUX driver : [http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)
so I downloaded it, but it asks for a link to an application before it will run.  

Any hints?

---

### Post by Lee_Machine on 2009-02-21
Your driver is already be there. It was included in hplip 1.6.6, and the newest one in ubuntu is 2.3. So it should work. But if not then install the newest version of HPLIP which is 3.x.x, but first try this.

Administration > Printing 

Then click on NEW, and following the instructions.

If not try:

sudo apt-get install hplip-gui

Then System > Preference > HPLIP Toolbok.

Then in the Gui try adding via  Device > Setup New Device

If that doesn't work the instruction for installing the newest hplip is here:

[http://hplipopensource.com/hplip-web/install/install/index.html](http://hplipopensource.com/hplip-web/install/install/index.html)

Here is a detailed analyses for support of your printer in Ubuntu 8.10.it Works out of the box 

[http://hplipopensource.com/hplt](http://hplipopensource.com/hplt) p-web/models/deskjet/deskjet_d1300_series.html

First try plugging your printer directly into your computer. Does that work?

---

### Post by pseudotheist on 2009-02-23
> **2scott said:**
> Hello - sorry for butting into this thread - but I have a similar problem and hope you can help me.

I am running 8.10 and trying to print to an HP Deskjet D1320 vi a Linksys wireless printsrever WPS54-G RM.  It works when I am running windows.  I can see the printserver on the Ubuntu network.  I think I may need a LINUX driver - but can't find one.

Any recommendations would be most appreciated.

Thanks
So, on the Windows network, is it seen as an HP printer available on the network?  Does the print server just provide an IP address to use for printer communication?  If you have not already tried it, I would run "sudo hp-setup" from a terminal session, and see if that sets everything up for you.

---

### Post by steveneddy on 2009-02-23
I have found that if you are going to use HPLIP for an HP printer, let the application HPLIP set up the driver.

Do not set up a printer driver in Administration --> Printing prior to running HPLIP for the first time.

Trust me, I thought I was going crazy.

Just get HPLIP from the repos and run it, should be in Applications --> Accessories under

HP Device Manager

I use an HP J6480 in my home office and it works great on our home network. It's the only printer we use now.

We can actually fax from any PC in the house as long as that PC is on our network by using the HPLIP utility application.

---

