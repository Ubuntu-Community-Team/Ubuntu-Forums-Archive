---
title: "Setting up USB printer on Ubuntu server 8.10 - totally stuck"
date: 2008-11-21
forum: Server Platforms
---

### Post by Oceanwatcher on 2008-11-21
I have Ubuntu server 8.10 freshly installed.

At install I chose to add LAMP, SSH, DNS, SAMBA.

Added proftpd and webmin.

Have set up filesharing via Samba/Webmin. Works perfectly.

Have set up bind via Webmin. I think it works :)

Have tried installing WordPress, but did not get that to work yet. But that will go in a different thread.

My big headache right now is that I can not get printing to work. I have spent this whole day searching how-to's, blogs, forums and I am still not there yet.

If I do a lpinfo -v , I get this:

```
network socket
network beh
direct usb://Brother/HL-1070%20series
direct hpfax
direct hp
direct parallel:/dev/lp0
direct scsi
network smb
```

I was able to add a printer in Webmin, but I am not sure if Webmin has the rights to complete the setup, or maybe the Webmin module does not fit Ubuntu server completely. I had to change the path to get Webmin to be able to start and stop cups.

One setting in the Webmin printer admin module is

Directory containing interface programs: /usr/share/cups/model

Does anyone know if this is correct? Or what it is?

I have added the printer in Samba. I can add it on a Win XP client. I can print a testpage from Win XP, but it never comes out on the printer. In the list of printers in Webmin, it shows that one job is in the que. So to me it seems like I have it all ok up to actually getting it out on the USB.

When adding the printer, I get this error from lpadmin:

lpadmin: Unable to copy interface script - No such file or directory!

This, to me, seems to be related to the interface program mentioned earlier.

So for now, I seem pretty stuck. The printer works like a charm in Windows.

---

### Post by baggins on 2008-11-21
Rather than using webmin have you tried using cups own web interface?
I will admit it been a few years sinve I last did a cups configuration from scratch, but I remember going that way.
The interface is available on port 631 on the server. So if your server ip is 10.110.2.101 then the URL for the cups interface is [http://10.110.2.101:631/](http://10.110.2.101:631/)

Its pretty straight forward, but you need to have made a cups admin password if you want to add or modify printers.
you can find most of the settings in /etc/cups/cupsd.conf

-- Jon

---

### Post by baggins on 2008-11-21
Ok I have just been corrected by someone else, on a standart desktop machine your normal account (the one that have sudo rights) can be used to manage cups via the web interface. This ought to be true for a server install as well.

--Jon

---

### Post by cariboo on 2008-11-21
Once you are using the cups interface you can modify it so that you can access it from other coputers on your network. I usually use elinks to access cups on the server, as it isn't running a gui and X forwarding won't work as firefox is running on the remote computer. eLinks is in the repositories.

Jim

---

### Post by Oceanwatcher on 2008-11-21
Did a little research on how to get the cups web interface up and running. It is working now, but I could not find the printer. Maybe a reboot will help.

After rebooting the USB printer was gone from the lpinfo -v list. So I changed USB port and tried again. This time it came up and after reloading the cups web interface, it shows in the printerlist.

I was able to add the printer and eventually print a testpage!

Thank you for your help so far. Now I just need to get the printersharing in Samba to work properly. Of course, after getting things to work from the server, it does not work via Samba... :-(

When I try to add a printer in Windows XP I get a request for username and password. After giving this, it fails and can not add the printer claiming the name was typed incorrectly or the specified printer has lost its connection to the server. Maybe it has lost the connection to the Samba server...

I have this strange problem on my pc - I am not able to browse the local network. This has been on and off on most computers I have worked on. Any idea why?

---

### Post by Thirtysixway on 2008-11-21
> **Oceanwatcher said:**
> Did a little research on how to get the cups web interface up and running. It is working now, but I could not find the printer. Maybe a reboot will help.

After rebooting the USB printer was gone from the lpinfo -v list. So I changed USB port and tried again. This time it came up and after reloading the cups web interface, it shows in the printerlist.

I was able to add the printer and eventually print a testpage!

Thank you for your help so far. Now I just need to get the printersharing in Samba to work properly.

I couldn't get my printer to share in samba, so what I did was on the cups interface, checked the box to allow printing from the internet.  Then on the computers on my network, I simply added the printer as a URL/web address using ```
http://lan_ip_of_server:631/printers/printername
```

on xp it's the last option on the printer list, on ubuntu you would use the "Other" option and put that url in.  Make sure port 631 is NOT opened to the internet and only to lan

---

### Post by Oceanwatcher on 2008-11-21
Got it running half way. Under the printer icon in Win XP it says "Access denied, unable to connect". I could still print a testpage. All pc's say the same, but the ability to print vary. Seems to have something to do with permissions?

---

### Post by Oceanwatcher on 2008-11-23
> **Thirtysixway said:**
> I couldn't get my printer to share in samba, so what I did was on the cups interface, checked the box to allow printing from the internet.

I have had some problems getting printing to work from some of the Windows XP systems. So I took your advice. BIG mistake. After writing the settings, it tried to restart cups. Now I can not even get the webinterface to load.

I can see in Webmin that the scheduler is not running. So I click to start it. I can then try to load the webinterface for cups and I get a white page. If I go back to check in Webmin, the scheduler is down again. So if I try to load the webinterface for cups more than once I get an error...

Seems like this setup is seriously messed up! Might be easier to reinstall than figure out what is wrong..

Why is this so hard to do? Why is there not a simple and easy interface to get a server like this up and running? This should be plain sailing. But Webmin is not adapted to Ubuntu server. There should be a special release that you can choose at install time, just as the LAMP server.. Sorry - do not mind my rant. Just a bit frustrated!

---

### Post by Thirtysixway on 2008-11-23
> **Oceanwatcher said:**
> I have had some problems getting printing to work from some of the Windows XP systems. So I took your advice. BIG mistake. After writing the settings, it tried to restart cups. Now I can not even get the webinterface to load.

I can see in Webmin that the scheduler is not running. So I click to start it. I can then try to load the webinterface for cups and I get a white page. If I go back to check in Webmin, the scheduler is down again. So if I try to load the webinterface for cups more than once I get an error...

Seems like this setup is seriously messed up! Might be easier to reinstall than figure out what is wrong..

Why is this so hard to do? Why is there not a simple and easy interface to get a server like this up and running? This should be plain sailing. But Webmin is not adapted to Ubuntu server. There should be a special release that you can shoose at install time, just as the LAMP server.. Sorry - do not mind my rant. Just a bit frustrated!

[[img]http://img167.imageshack.us/img167/5411/26257235uj9.png[/img]](http://imagemirror.co.cc)

That's what I was talking about.  Did you manage to get it working again? :(

---

### Post by Oceanwatcher on 2008-11-24
Like I said - this is what I did, and should not have done... Oh well..

I am going to reinstall it all today. A little bit of a pain, but less than spending hours trying to figure out what is wrong.

---

