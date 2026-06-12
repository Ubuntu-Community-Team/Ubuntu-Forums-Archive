---
title: "Sharing Printer from 9.04 Server to 9.04 Desktop Client"
date: 2009-06-19
forum: Server Platforms
---

### Post by Lucky. on 2009-06-19
I don't know whether to laugh or cry, but here's what happened:

1.  I installed CUPS on my server, and set it up with SAMBA to share my printer to Windows clients.  It works beautifully.

2.  Ironically I can get Windows clients to connect, but I can't get my Ubuntu 9.04 desktop client to connect.

For giggles, here's how I set up the CUPS server:

> 

1.  Installed CUPS:

sudo apt-get install cupsys

2.  Installed foo2zjs pack, which supports my LaserJet 1020.

sudo apt-get install foo2zjs

3.  Traveled to the following directory:

/usr/share/ppd/foo2zjs

4.  Unzipped the ppd file like so:

gunzip HP-LaserJet_1020.ppd.gz

This left me with a file in the following location:

/usr/share/ppd/foo2zjs/HP-LaserJet_1020.ppd

5.  Typed the following:

lpinfo -v

This gave me a list of printing devices.  One of them was my usb laserjet printer.  I wrote the following down:

direct usb://HP/LaserJet%201020

3.  I added the printer with the following:

lpadmin -p myprintername -v usb://HP/LaserJet%201020 -P /usr/share/ppd/foo2zjs/HP-LaserJet_1020.ppd -u allow:all

4.  I enabled the printer:

cupsenable myprintername

5.  I began accepting jobs:

accept myprintername

6.  To verify that the printer was installed, I typed the following:

lpstat -s

This listed the printers installed.

7.  I edited the following file:

/etc/samba/smb.conf

And added the following:

[printers]
path=/var/spool/samba
guest ok = yes
printable = yes

8.  I restarted Samba:

/etc/init.d/samba restart



Again, works great with Windows clients...no worky for my Jaunty desktop client.  Any ideas?  Is Samba the wrong way to go here?

---

### Post by HermanAB on 2009-06-19
Well, if the Windows clients work, then leave Samba alone - it works!

For the Linux clients, just send the file directly to the print server using lpr or ipp://serveripaddress/printername.

See this:
[http://aeronetworks.ca/print-howto.html](http://aeronetworks.ca/print-howto.html)

---

### Post by cariboo on 2009-06-19
Make sure you have hplip installed on the server. Your printer should show up automagically in the printer wizard. You don't need samba for printer sharing.

---

### Post by Lucky. on 2009-06-19
Thanks guys.  I looked around and found [this link](http://opensuse.swerdna.org/suseprintipp.html), and it helped me out.  Thinks are working great now, and the printer automagically shows up in the printer browser like you said.

I did the following in addition to the stuff in the original post:

> 

Edit the following file:

/etc/cups/cupsd.conf

Changed the following:

Browing Off

to:

Browsing On

Found the following:

<Location />
Order allow, deny
</Location/>

And I changed it to

<Location />
Order Deny,Allow
Deny From All
Allow From 127.0.0.1
Allow From 192.168.1.*  (Of course this could change according to the network)
</Location>

I commented the following lines:

Listen localhost:631
Listen /var/run/cups/cups.sock

And added the following line:

Port 631

...So the section looked like this:

#Listen localhost:631
#Listen /var/run/cups/cups.sock
Port 631

Restarted CUPS:

sudo /etc/init.d/cups restart

Bam, things worked!



In the link it outlines how to have the Windows client connect to CUPS without using Samba.  I found a couple of other links that detail the same way.  It works good, but the problem is that the printer doesn't seem to show up in the Network Neighborhood when used in this fashion, and the Windows client has to have the exact address, port, and name of the printer to connect.

This isn't a complete loss to me.  Both work fine for the Windows clients, but I think I'll stick with Samba so it's easy to connect to for my wife and other guests.  I'm stoked that I have both Linux and Windows working now as clients.

Thanks again!

---

