---
title: "Xerox network printer holding jobs in CUPS"
date: 2008-03-19
forum: Server Platforms
---

### Post by mreynaga on 2008-03-19
Hello All,

i tried searching for this but came up empty. i am running an ubuntu 7.1 server no GUI as a virtual machine on my vm server 

i am extremely new to this and just completed my first server install without a GUI, i have successfully installed and have CUPS up and running for this to be my print server, i have already installed a few printers and everything appears to be working great but i am having a problem with one of my printers. 

a Xerox DocuColor 3535 will not print, it is on the following network port "network lpd://10.1.1.100/" the problem is that if i add it as a "socket://" port the jobs dont print and on the web page i get a comment saying that the printer is busy and it will retry in X seconds. if i add it as a lpd:// printer the jobs get held and if i release them to print they immediately return to being held and will not print and gives the error "/usr/lib/cups/backend/lpd failed" 

i have added another xerox printer which is working fine but this one will not work.

any help would be greatly appreciated.

thanks

---

### Post by tgalati4 on 2008-03-19
Try unplugging the printer for 5 minutes.  Then try again.  Look in /var/log/cups and report some of the errors.  Note the time and only report the errors after you reboot the printer.

---

### Post by mreynaga on 2008-03-19
would a reboot really be necessary? i can print fine if i install the printer directly on my machine. and it is printing fine from my windows  print server. i will reboot it in about 20 mins as soon as everyone clears out of the office

ill check the logs and post back. thanks

---

### Post by mreynaga on 2008-03-19
get alot of errors over and over 

CUPS-ADD-MODIFY PRINTER
CUPS-ACCEPT JOBS
CUPS-RESUME JOBS

all say UNAUTHORIZED let i get no errors when adding them and they show up in the list fine.

also have the following errors:

PID 4402 (/usr/lib/cups/backend/lpd) stopped with status 1!

---

### Post by tgalati4 on 2008-03-20
Since you are running in a virtual machine, it's possible that there is a suble networking handshaking problem that kills the print job.  I assume that you can ping the printer address without errors?

Have you tried:

network lpd://10.1.1.100:9100/

What do you get in a browser with:

[http://10.1.1.100](http://10.1.1.100) or [http://10.1.1.100:9100](http://10.1.1.100:9100)

---

### Post by mreynaga on 2008-03-20
yes i tried lpd://10.1.1.100:9100/ and it still just says busy will try again in 10..15..25 seconds. 

when i open a web browser and put 10.1.1.100 in the address bar it opens the Xerox Fiery web administrator page. 

yes i can ping the printer.

---

### Post by tgalati4 on 2008-03-20
Is the netmask and gateway on the printer set correctly?  255.255.255.0 or 255.255.0.0 for netmask and 10.1.1.1 or 10.1.1.254 for gateway?

Also put the address in your /etc/hosts file and give it a valid name:

10.1.1.100 xeroxprinterthatisgivingmefits

Finally check all of the settings in the web admin page.  As I recall some of these Xerox printers will only do USB or network, but not both.  So you have to change modes to set it to one or the other.  That has bitten me before.  The network card will still return pings, but the print engine is still looking for print data from the USB.  I'm not sure how it is switched on your particular model.

---

### Post by mreynaga on 2008-03-20
i know all the settings on the Xerox are correct because it is currently printing fine from my windows print server over the network, i just wanted to take that role away from that server and let this ubuntu one do it,

i will try adding the host name but dont see how that will make any difference as i am not trying to call to it by a name, i am using the ip address

---

### Post by somerville32 on 2008-04-03
Hi,

 I dunno if you've already done this but to get my Xerox network printer working, I had to download the PPD file from the Xerox website (ie. Download the windows driver and when you install the printer, tell it to use the PPD file shipped in the windows driver zip file). If you use a network controller, you might have to download the specific driver for that for your driver.

Thanks,

Cody

---

### Post by zimjim on 2008-05-23
Try lpd://10.1.1.100/print, I have tested it on a similar Xerox print & it works fine.

---

