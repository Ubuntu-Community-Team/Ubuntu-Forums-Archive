---
title: "Problems printing with Samba"
date: 2011-06-15
forum: Server Platforms
---

### Post by kamaji792 on 2011-06-15
My set up is: Ubuntu 10.04 Samba server.  It has an Epson printer connected to one of its USB ports.

It’s clients are an Ubuntu 10.04 box and couple of WinXP boxes.

File sharing from the clients works fine.

I have been trying to get the the server to share the printer so that I can print from any of the clients.  I have spent some time today trying to get this to work without too much success.

Here I believe is the important parts of the **smb.conf** file:
```

[global]
…
   security = user
...
   load printers = yes

   printcap name = cups

…
[printers]

   comment = All Printers

   browseable = no

   path = /var/spool/samba

   printable = yes

   guest ok = yes

   read only = yes

   create mask = 0777



   printing = cups

   printable = yes

   use client driver = yes

```

I can set the printer up on the Ubuntu client.

I have looked at the /var/spool/samba directory on the server as I do a print job and I can see a file appearing in the directory and then disappearing, which make me think the problem may be CUPS related rather than Samba.

I have done little to change the CUPS set up apart from making sure it is installed. I don't see how it works as I have not told CUPS about the printer, even if I just want it to pass the data direct to the printer.

Any one know how I might track where the problem is?

K

---

### Post by kamaji792 on 2011-06-16
OK I think I may have solved my problems.

As I suspected it appeared to be CUPS that was holding things up.

I will try and list the issues I had and how I solved them, on the principle that you have a running samba install.

Phase one was I failed to install cups on my server.

```
sudo apt-get install cups
```

My next problem was I could not see the CUPS admin web page remotely (my server is headless, I ssh into it).  This was solved by editing the CUPS configuration file /etc/cups/cupsd.conf. Make a backup of the current config. file:
```
sudo cp /etc/cups/supsd.conf /etc/cups/supsd.conf
```

Look for the **<Location /admin>** section and modify it to look like:
```
<Location /admin>

  Order allow,deny

  Allow @LOCAL

</Location>
```

The next problem was I could not add a printer.  I think it started with giving me a 403 error and then asking me for a password.  The following seem to get round that problem:

Back to the CUPS config. file and look for the **<Location /admin/conf>**.  Set it to:
```
<Location /admin/conf>

  AuthType Default

#  Require user @SYSTEM

  Order allow,deny

  Allow @LOCAL

</Location>
```

I can’t guarantee that the following was needed but I found several references that said the following was required:

Add a **cupsys** user (Most people did not seem to have to do this as the users already existed) and them add them to the **shadow** group:
```
adduser cupsys
…
adduser cupsys shadow
```

Now would be a good time to restart the CUPS server:
```
sudo /etc/init.d/cups restart
```

You should be able to access the cups server with [http://*your-server-name](http://*your-server-name)*:631/

**Note:** when you access a part of the admin system that requires a password you may get a message about an unverified security certificate.  I ignored this and added an exception to my web browser.

Now when you are asked for a user name and password enter your main user name and password (the one you created when you installed ubuntu).

From that point on everything worked like a dream.  It found my Epson printer and I was able to add it and say it should be shared.

I was then able to add the samba shared printer from my server on my Ubuntu client.  I can’t quite do the same due to some permission issue with my WinXP clients but I will work on that.

K

---

