---
title: "Adding a printer in SMB"
date: 2006-04-28
forum: Server Platforms
---

### Post by LuisC-SM on 2006-04-28
Hi mates.

Recently I installed Ubuntu Server following a very nice [Tutorial]("http://www.howtoforge.com/samba_setup_ubuntu_5.10").
I'm not new to linux but I've never add or configured a printer from the command line, and I've read some posts that some people are having big troubles with samba and could'nt find anything to guide me adding a printer.
I've tried to add a printer following this command: ```
cupsaddsmb -a Canon_iPixma_1000
``` but nothing happens. When I oppen the CUPS console (in my case [http://192.168.1.1:631](http://192.168.1.1:631)) I don't find the printer nor the driver.
Could someone assist me on how to do it, or provide me a link for better understanding on how to add a printer in samba?.

Kind Regards.

Luis C. Suárez

PS. Please, be so kind to not to post the [CUPS]("http://www.cups.org/") link or the [Samba]("http://us5.samba.org/samba/") link as far as I've already been there and still cannot find nor understand anything.

---

### Post by behemot on 2006-04-28
Hi Luis,

If you go over posts in Dapper forum, you will see that many people have problems with printing in Ubuntu.

Devs are posting updates to cups almost every day now.

I have been very fortunate and cups has always worked for me.
This is what i have done:

apt-get installed gnome-cups-manager,

modified cups.conf to enable browsing for printers.

Created printer using gnome-cups-manager and printed the test page.

Restarted cups and samba.

I am sure that you have done that already.
Please, post /var/log/cups/your-error.log

---

### Post by LuisC-SM on 2006-04-28
Hi behemot.

Thanks a lot for your promt response.

I've bad news...> root@server1:~# cat /var/log/cups/your-error.log
cat: /var/log/cups/your-error.log: No such file or directory

That's what I got.
I dunno if this was caused 'cose I installed "ubuntu-desktop" but I've already uninstalled it.... I've even lost my connection to internet

Kind Regards

Luis C. Suárez

EDIT: Are you using the Gnome Desktop?> Created printer using gnome-cups-manager and printed the test page.


---

### Post by behemot on 2006-04-28
Hi Luis,
Yes, I am running gnome on my desktop.

Of course you cannot find "your-error.log".
I just wanted to ask you to browse to folder /var/log/cups

You will find 3 log files there: access_log, error_log and page_log

Look for some clues there.

One of the recent problems with cups manifested itself with building very large log file if default printer was not present.

You can delete those files, and they will be recreated next time you restart cups.

I appologize for not being specific. I just did not want you to find my post patronizing or anything like that.

If you wish I could post my configuration files.

---

### Post by LuisC-SM on 2006-04-28
[QUOTE=behemot]Hi Luis,
Yes, I am running gnome on my desktop.

Of course you cannot find "your-error.log".
I just wanted to ask you to browse to folder /var/log/cups

You will find 3 log files there: access_log, error_log and page_log

Look for some clues there.[/quote]
Thanks for your response. I had seriuos problems with my /etc/resolv.conf file. when installing ubuntu desktop, it changed and linked. I tried to remove it and what a mess I made... so right know I'm reinstalling everything ](*,) 

> One of the recent problems with cups manifested itself with building very large log file if default printer was not present.

You can delete those files, and they will be recreated next time you restart cups.

I appologize for not being specific. I just did not want you to find my post patronizing or anything like that.

**If you wish I could post my configuration files**.Not a bad idea at all :mrgreen: 
In around 1hour I'll have everything ok... (I hope so:D )

Kind Regards

Luis C. Suárez

---

### Post by LuisC-SM on 2006-04-28
Ok. same story.....
here is my error log:> root@server1:~# cat /var/log/cups/error_log
I [28/Apr/2006:20:33:59 -0500] Listening to 7f000001:631
I [28/Apr/2006:20:33:59 -0500] Listening to c0a80132:631
E [28/Apr/2006:20:33:59 -0500] Unknown directive AuthGroupName on line 748.
I [28/Apr/2006:20:33:59 -0500] Loaded configuration file "/etc/cups/cupsd.conf"
I [28/Apr/2006:20:33:59 -0500] Configured for up to 100 clients.
I [28/Apr/2006:20:33:59 -0500] Allowing up to 100 client connections per host.
I [28/Apr/2006:20:33:59 -0500] Full reload is required.
I [28/Apr/2006:20:33:59 -0500] LoadPPDs: Read "/etc/cups/ppds.dat", 258 PPDs...
I [28/Apr/2006:20:33:59 -0500] LoadPPDs: No new or changed PPDs...
I [28/Apr/2006:20:33:59 -0500] Full reload complete.
I [28/Apr/2006:20:33:59 -0500] Started filter /usr/lib/cups/filter/pstops (PID 7909) for job 9.
I [28/Apr/2006:20:33:59 -0500] Started filter /usr/lib/cups/filter/pstocanonbj (PID 7910) for job 9.
I [28/Apr/2006:20:33:59 -0500] Started backend /usr/lib/cups/backend/usb (PID 7912) for job 9.
E [28/Apr/2006:20:34:00 -0500] PID 7910 stopped with status 1!
I [28/Apr/2006:20:34:00 -0500] Hint: Try setting the LogLevel to "debug" to find out more.
I [28/Apr/2006:20:34:12 -0500] Started "/usr/lib/cups/cgi-bin/printers.cgi" (pid=7915)
I [28/Apr/2006:20:34:12 -0500] Adding start banner page "none" to job 10.
I [28/Apr/2006:20:34:12 -0500] Adding end banner page "none" to job 10.
I [28/Apr/2006:20:34:12 -0500] Job 10 queued on 'Canon_PIXMA_iP1000' by 'root'.
I [28/Apr/2006:20:34:14 -0500] Started "/usr/lib/cups/cgi-bin/printers.cgi" (pid=7916)


Kind Regards

Luis C. Suárez

EDIT:
I forgot to mention that I found the printer and the driver but no printing anyhow...
this sux :(
Maybe there is something wrong with usb printers in ubuntu server

---

### Post by behemot on 2006-04-28
You could try to setup your printer with HP PCL6 cups driver.
It may just work with your Cannon.

---

### Post by LuisC-SM on 2006-04-28
[QUOTE=behemot]You could try to setup your printer with HP PCL6 cups driver.
It may just work with your Cannon.[/QUOTE]
There was a problem with the USB port I was using...
it seems that some ports are only for webcams or keyboards, etc. and I changed it to another port and I can see ubuntu reconganzes everything ... but still is not letting me print  ](*,) 

Your Idea was Ok yesterday... in fact I tried all HP drivers with no joy ...

Any ideas?

Kind Regards 

Luis C. Suárez

---

### Post by LuisC-SM on 2006-04-28
the error log after a cupsd restart
> root@server1:/etc# cat /var/log/cups/error_log
I [28/Apr/2006:21:45:37 -0500] Listening to 7f000001:631
I [28/Apr/2006:21:45:37 -0500] Listening to c0a80132:631
E [28/Apr/2006:21:45:37 -0500] Unknown directive AuthGroupName on line 748.
I [28/Apr/2006:21:45:37 -0500] Loaded configuration file "/etc/cups/cupsd.conf"
I [28/Apr/2006:21:45:37 -0500] Configured for up to 100 clients.
I [28/Apr/2006:21:45:37 -0500] Allowing up to 100 client connections per host.
I [28/Apr/2006:21:45:37 -0500] Full reload is required.
I [28/Apr/2006:21:45:37 -0500] LoadPPDs: Read "/etc/cups/ppds.dat", 258 PPDs...
I [28/Apr/2006:21:45:37 -0500] LoadPPDs: No new or changed PPDs...
I [28/Apr/2006:21:45:37 -0500] Full reload complete.
I [28/Apr/2006:21:46:18 -0500] Started "/usr/lib/cups/cgi-bin/printers.cgi" (pid=7494)
I [28/Apr/2006:21:46:22 -0500] Started "/usr/lib/cups/cgi-bin/printers.cgi" (pid=7495)
I [28/Apr/2006:21:46:22 -0500] Adding start banner page "none" to job 16.
I [28/Apr/2006:21:46:22 -0500] Adding end banner page "none" to job 16.
I [28/Apr/2006:21:46:22 -0500] Job 16 queued on 'Canon_PIXMA_iP1000' by 'root'.
I [28/Apr/2006:21:46:22 -0500] Started filter /usr/lib/cups/filter/pstops (PID 7496) for job 16.
I [28/Apr/2006:21:46:22 -0500] Started filter /usr/lib/cups/filter/pstocanonbj (PID 7497) for job 16.
I [28/Apr/2006:21:46:22 -0500] Started backend /usr/lib/cups/backend/usb (PID 7499) for job 16.
E [28/Apr/2006:21:46:22 -0500] PID 7497 stopped with status 1!
I [28/Apr/2006:21:46:22 -0500] Hint: Try setting the LogLevel to "debug" to find out more.
I [28/Apr/2006:21:46:25 -0500] Started "/usr/lib/cups/cgi-bin/printers.cgi" (pid=7502)

Something is missing.... mmmmm maybe I should add the printer to samba first....  ? ](*,)

EDIT:

No joy ](*,) don't know what to do

---

### Post by LuisC-SM on 2006-04-29
Ok. So I have to answer myself .....
Finally I fixed all... I have read all the wikkies from ubuntu, the wikkie guide, etc. and noting there... 
If anyone wants to ever use Ubuntu as a print server, follow the tutorial (given in my first post) and take a look at my posts in the [HowToForge forum]("http://www.howtoforge.com/forums/forumdisplay.php?f=2") (I use the same name) for the answer.

Kind Regards

Luis C. Suárez

EDIT:

By the way, **behemot**, thanks a lot for your help. 
I've been wanting to reply to your commet from yesteday about> apt-get installed gnome-cups-manager
as I said before, I've installed the **server** version not the **gnome-desktop** so the gnome cups manager cannot be used in a text environment (or at least I don't know how to call it).

---

