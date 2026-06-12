---
title: "how do I configure CUPS on 10.4"
date: 2010-05-16
forum: Server Platforms
---

### Post by ZizzerZuz on 2010-05-16
After struggling with a bad LP cable I have finally proven that the cable, printer and port all work.  I booted in to another OS and was able to finally print.  Now, I'm trying to get server 10.4 to recognize the printer and then I want to configure CUPs so I can run this machine as a headless print server, among other things.

Apache is running as I managed to get nagios to run and I can pull it up from another PC via a browser.

sshd is running as I'm logged in from another PC via ssh.

I've read and read and read but everything seems to be for older versions and I'm having a hard time figuring out what exactly to do as the file names and some other details are not the same.

Problem number 1 is how do I install a driver for an NEC Superscript 870 printer?  As it is lpstat returnes with :

karl@zeus:/etc/cups$ lpstat -t
scheduler is not running
no system default destination

Once I am able to print then I need to print to the server from other hosts on the network.

Any help would be very much appreciated

ZizzerZuz

---

### Post by mituw16 on 2010-05-16
Well I'm not sure about how to install drivers onto the system, but once you do install samba and avahi-daemon to share the printer across the network

---

### Post by ZizzerZuz on 2010-05-16
I installed samba at install, but I've done no configuration on it at all yet.  I think I need to get  the thing to print before I can worry about cups.

I'm printing directly to lp0.

The port appears not to be configured at all ...

karl@[COLOR=Red]zeus[/COLOR]:/etc/cups$ ls -al /dev/lp0
ls: cannot access /dev/lp0: No such file or directory

Shouldn't that come up with something like this?

karl@[COLOR=Red]daphne[/COLOR]:/$ ls -al /dev/lp0
crw-rw---- 1 root lp 6, 0 2010-05-15 14:40 /dev/lp0

karl@[COLOR=Red]zeus[/COLOR]:/etc/cups$ dmesg | grep lp0
karl@[COLOR=Red]zeus[/COLOR]:/etc/cups$ dmesg | grep parport
karl@[COLOR=Red]zeus[/COLOR]:/etc/cups$ 

by contrast ...
karl@[COLOR=Red]daphne[/COLOR]:/$ dmesg | grep lp0
[   10.316279] lp0: using parport0 (interrupt-driven).[   10.169152] parport_pc 00:09: reported by Plug and Play ACPI
[   10.169242] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE
,COMPAT,ECP,DMA]
[   10.316279] lp0: using parport0 (interrupt-driven).
[22986.208036] parport0: FIFO is stuck
[22986.256034] parport0: BUSY timeout (1) in compat_write_block_pio
[23066.280529] parport0: FIFO is stuck

and then that repeats for MANY rows.  I can only assume that's because I removed the printer from Daphne.

How do I get a local printer on lp0 to print?

Ziz

---

### Post by ZizzerZuz on 2010-05-16
man lpoptions

ROOT ACCOUNT OPTIONS
       When  run  by  the  root  user, lpoptions gets and sets default options and
       instances for all users in the /etc/cups/lpoptions file.


karl@zeus:/etc/cups$ ls -al lpop*
ls: cannot access lpop*: No such file or director

I'm missing something essential here.

Ziz

---

### Post by ZizzerZuz on 2010-05-16
several posts recomended installing Webmin and configuring the printer through that.  I've gotten webmin to work and I can bring it up on my desktop box, but I can't get the printer to work.

How do I get the standard foomatic driver installed and can someone point me at a how-to that actualy covers cups running under 10.4?

Again, any help would be appreciated.

Ziz

---

### Post by TJet1.8 on 2010-05-16
You can easily add/configure printers via the built in cups web administration interface.

1.) Install cups:

sudo apt-get install cups

2.) Edit your cups config file with your favourite editor:

/etc/cups/cupsd.conf

3.) Set your listening IP <your cups server IP address> in the config file:

Listen 127.0.0.1:631           # existing loopback Listen
Listen /var/run/cups/cups.sock # existing socket Listen
Listen <your_ip_address>:631      # Listen on the LAN interface, Port 631 (IPP)
Note: You can comment out the first line above (i.e. - loopback) as it is not required...the rest IS NEEDED.

4.) Edit the stanza below (i.e. - Allow 192.168.1.100) if you are trying access the interface from 192.168.1.100:

# Restrict access to the admin pages...
<Location /admin>
Order allow,deny
Allow 192.168.1.*  # or 192.168.1.100 if you want to restrict access to one computer.
</Location>  

5.) You need to change this stanza also to whatever your local network is:

# Restrict access to the server...
<Location />
Order allow,deny
Allow from @LOCAL
Allow 192.168.1.*
</Location>

6.) Add your local cups server "admin" account to the lpadmin group:

sudo usermod -aG lpadmin <your_admin_account_name>

7.) Restart your cups daemon:

sudo /etc/init.d/cups restart

8.) Access the cups web administration interface:

http://<your_cups_server_IP_address>:631/admin

Once you are in the interface, you can configure your printers and install printer drivers via the interface.

Note that at some point, the interface will ask you to login to perform administrative tasks (i.e. - Add/remove printers, printer drivers. etc...).
This is where your local cups server admin account (see step 6 above) comes into action.

Enjoy.

:)

---

### Post by hartunnoo on 2010-05-17
If you behind firewall, make sure you allow port 631 first. :)

---

### Post by ZizzerZuz on 2010-05-17
> **hartunnoo said:**
> If you behind firewall, make sure you allow port 631 first. :)
 
The headless server and the desktop are side by side on the same switch, no firewall between them.
 
Ziz

---

### Post by ZizzerZuz on 2010-05-17
TJet1.8 ... I think I understand what I was doing wrong now.  The instructions all say to remove the local part of local:631 and just leave the 631 ... I'll try with the full IP of my desktop.
 
lpadmin is a group?  Should I create a special lpadmin user?  Should I create a different user and join them to the lpadmin group? 
 
I'll post this evening when I'm home and can try again.
 
Thank you very much!
 
Ziz

---

### Post by ZizzerZuz on 2010-05-18
This finaly worked.  I can now access CUPS admin from another PC via a browser.  I was editing the file incorrectly.
 
I'm starting to think this was all for naught ...
 
When I try to configure the printer with CUPS, via the web interface on another PC is comes up with "No device found" for lp0.
 
karl@[COLOR=red]zeus[/COLOR]:/etc/cups$ ls -al /dev/lp0
ls: cannot access /dev/lp0: No such file or directory
[EMAIL="karl@zeus:/etc/cups$"]karl@[COLOR=red]zeus[/COLOR]:/etc/cups$[/EMAIL] dmesg | grep lp0
karl@[COLOR=red]zeus[/COLOR]:/etc/cups$ dmesg | grep parport
 
:confused:
 
argh ....

---

### Post by TJet1.8 on 2010-05-20
> **ZizzerZuz said:**
> TJet1.8 ... I think I understand what I was doing wrong now.  The instructions all say to remove the local part of local:631 and just leave the 631 ... I'll try with the full IP of my desktop.
 
lpadmin is a group?  Should I create a special lpadmin user?  Should I create a different user and join them to the lpadmin group? 
 
I'll post this evening when I'm home and can try again.
 
Thank you very much!
 
Ziz
Yes...lpadmin is a default group created when you install CUPS.
CUPS will reference users in that group for administration purposes.

You can create another userid to add to the lpadmin group if you wish...it's up to you how you want to manage CUPS.

The only requirement is that there is A userid in the lpadmin group to manage CUPS.

---

### Post by brhad56 on 2010-06-26
Confirming that this method worked for me on getting the NEC Superscript 870 working on Kubuntu 10.4.   I was able to skip some of your steps though because the cups config was already setup for localhost, and only did the following

6.) Add your local cups server "admin" account to the lpadmin group:

sudo usermod -aG lpadmin <your_admin_account_name>

7.) Restart your cups daemon:  (not sure if this was necessary)

sudo /etc/init.d/cups restart

8.) Access the cups web administration interface:

[http://localhost:631/admin](http://localhost:631/admin)

Notes: When adding the printer, the NEC wasn't there.. So I clicked on HP.  I didn't like what I saw, so I clicked back.. Then where LPT1 was, now was the NEC SuperScript 870.   Followed the instructions and upon completion, the printer was setup in the standard printer manager (where it wasn't before).  I was able to set it as default printer and test page did print.

Not sure why I had to go through these procedures, in the 8 years I've owned this printer, it was always found by the standard add a printer.

---

### Post by drdos2006 on 2010-07-06
TJet1.8
Thanks for this HOWTO, worked perfectly for me on Ubuntu 9.10 64bit with a Canon PIXMA iP4300 USB connection. I had tried with Webmin but was unable to utilise lpadmin.
Excellent tutorial.

regards

---

