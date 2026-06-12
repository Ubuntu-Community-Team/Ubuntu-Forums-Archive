---
title: "Troubleless network printer install"
date: 2007-01-02
forum: Testimonials &amp; Experiences
---

### Post by rev_b on 2007-01-02
I bought an excelent HP deskjet 6940, reported to work perfectly in [http://www.linuxprinting.org/show_printer.cgi?recnum=HP-DeskJet_6940](http://www.linuxprinting.org/show_printer.cgi?recnum=HP-DeskJet_6940)

And so it is. Just plug in the ethernet cable to the router, find out what IP address it leases, add new printer -> network printer. I selected HP JetDirect first, just typed in the IP address and selected the printer from a list. Ok, worked nicely first time. Took, what, 2 minutes?

On the XP laptop, it's more straightforward, just put the HP cd in, click setup and eventually it'll detect the network printer and set it up without you even having to know what a IP is.

But why even the smallest installation option has to install 200 Mb of garbage on the hard-disk and take like 15 minutes?? It really remembered me why I ran away of windows and sticked with ubuntu... 

Congratulations to HP linux support, it's amazing. =D>

---

### Post by meng on 2007-01-02
> **rev_b said:**
> But why even the smallest installation option has to install 200 Mb of garbage on the hard-disk and take like 15 minutes?? It really remembered me why I ran away of windows and sticked with ubuntu... 
I had exactly the same problem with a Windows install of an HP printer recently (PSC 2510). It dumped 450 MB of junk on my system, only 350 MB of which can be removed without breaking printer support. 100 MB just to run a printer? You have to be kidding me!!

---

### Post by rev_b on 2007-01-02
I have 2 driver options - hpijs and hpijs - HPLIP 1.6.9
What would you recommend?

---

### Post by Chuck_W on 2007-01-20
Thanks for your post. I just got an HP 6940 printer and was having some problems setting it up. Neither CUPS or LPD would work. Your tip of using HP Jetdirect was great-worked like a charm! As far as setting it up under Windows, I agree. While the photo software might be nice it's not really needed along with all the other stuff that comes with it. To make it worse, the autostart function didn't work and I had to turn off both antivirus and firewall software to get the installer to work. And the registration function failed to find a connection. No biggee, I don't need more spam in my inbox.
The driver I used was "HP-Deskjet_6940-hpijs.ppd" that I got from linuxprinting. Seems to work ok although so far I've only printed a test page.
BTW-I prefer to keep my printer IP's outside of the DHCP range of my router. The IP person where I work recommends this. You can point your browser to 192.168.xxx.xxx (whatever your setting happens to be) and change from DHCP to manual if you want. Of course you will then have to change the settings on each computer which can be a pain. I've found that in Ubuntu it's easier to delete a printer and create a new one than it is to change settings on an existing one. Just doesn't seem to work for me.

---

### Post by rev_b on 2007-01-21
Yes I actually tried HP Jetdirect first, and it worked. Maybe you have to specify a port in the other settings, HP jetdirect mentions port 9100 by default.

I already changed the printer IP to a manual one; I looked out for the leased IP in the router and acessed it with the browser. I have my network (3 PC and printer) all with manual IP adresses.

As I said, HP support for Linux is very good; coincidence or not, after reading lots of horror stories about laptop installations gone wrong, Edgy Eft installed flawlessly in my HP laptop.
And yes, it was much easier and quick to install in Linux than Windows.

What driver is that? I didn't have to install anything, the printer was mentioned in gnome-cups printer database, I only selected it.

---

### Post by jepling on 2007-01-21
Oh my goodness - after DAYS of trying to figure out LPD and IPP and CUPS to get my wirelessly networked HP Photosmart 6180 to work, I read the above post and it worked within 30 seconds.
AAAArrgh.
I love Linux, but episodes like this make me crazy.
FWIW, I used the 6100 driver, and the default port (9100) for the JetDirect server.

I had Kubuntu installed before, and went through none of this (to my recollection...though as I think about it, I may have unthinkingly chosen JetDirect...hmmm).

Thanks rev_b

---

### Post by rev_b on 2007-01-21
> **jepling said:**
> Oh my goodness - after DAYS of trying to figure out LPD and IPP and CUPS to get my wirelessly networked HP Photosmart 6180 to work, I read the above post and it worked within 30 seconds.
AAAArrgh.
I love Linux, but episodes like this make me crazy.
FWIW, I used the 6100 driver, and the default port (9100) for the JetDirect server.

I had Kubuntu installed before, and went through none of this (to my recollection...though as I think about it, I may have unthinkingly chosen JetDirect...hmmm).

Thanks rev_b

Well, I though if I am installing a network HP printer, let's try this HP network thingie first. Never tried the other options, but it should be possible to configure a network printer with CUPS... maybe more complicated. I really never tried it, as setting it with HP jetdirect worked first time.   

Sometimes the simplest solution works better. :wink:

---

### Post by Chuck_W on 2007-01-27
I don't think the printer list for 5.1 is as extensive as it may be for 6.1. I searched for .ppd files on my computer and the closest thing was for the 6840, which might have worked but the 6940 ppd was easily obtained so I went for that.
My previous experience was adding a Kyocera Mita laser printer to the network by way of a Hawking Tech ethernet-to-usb print server. That worked using Unix (LPD) printing so I originally tried to set up the HP using that or CUPS. Neither worked but it may have been the port setting that tripped me up. Jetdirect took care of that. All is ok now.

---

