---
title: "Ubuntu Server edition - How do I share a printer?"
date: 2009-01-23
forum: Server Platforms
---

### Post by Sindre-d on 2009-01-23
Hi

I've just installed Ubuntu server edition on my new fileserver, and I'm trying to share the printer I've connected to it, through the network. I've googled around for a while, but it didn't amount to anything useful. 

So I was wondering if anyone could help me set it up?

- Sindre

---

### Post by Dr Small on 2009-01-23
Check out this guide on setting up CUPS:
[https://help.ubuntu.com/8.04/serverguide/C/cups.html](https://help.ubuntu.com/8.04/serverguide/C/cups.html)

Here is another guide also (it's for Debian, but there is no difference in setting it up from Debian or Ubuntu):
[http://www.debianadmin.com/setup-cups-common-unix-printing-system-server-and-client-in-debian.html](http://www.debianadmin.com/setup-cups-common-unix-printing-system-server-and-client-in-debian.html)

Once you have CUPS configured to listen on all interfaces, you will want to connect to the CUPS interface (probably from another computer on your LAN), setup the printer and then try printing to it from a separate computer (besides the sever).

---

### Post by acreech on 2009-05-12
> **Dr Small said:**
> Check out this guide on setting up CUPS:
[https://help.ubuntu.com/8.04/serverguide/C/cups.html](https://help.ubuntu.com/8.04/serverguide/C/cups.html)

Here is another guide also (it's for Debian, but there is no difference in setting it up from Debian or Ubuntu):
[http://www.debianadmin.com/setup-cups-common-unix-printing-system-server-and-client-in-debian.html](http://www.debianadmin.com/setup-cups-common-unix-printing-system-server-and-client-in-debian.html)

Once you have CUPS configured to listen on all interfaces, you will want to connect to the CUPS interface (probably from another computer on your LAN), setup the printer and then try printing to it from a separate computer (besides the sever).

Following the instrucions on the second link gives me an error. I was at the first part where I just changed the /etc/cups/cupsd.conf file. 

The directions say " Now you need to restart CUPS using the following command

#/etc/init.d/cupsys restart" 

I put sudo in front of the command and then get this error..... 

```

administrator@AKAA:~$ /etc/init.d/cupsys restart
-bash: /etc/init.d/cupsys: No such file or directory
administrator@AKAA:~$ sudo /etc/init.d/cupsys restart
sudo: /etc/init.d/cupsys: command not found

```

I am not sure why I get this error, but this has to be a start of why I can not get connected to my printer through the server. 

What should I do from here?

Thanks for the help.

---

### Post by lykwydchykyn on 2009-05-12
in ubuntu its "/etc/init.d/cups restart".  One of the few differences between Debian and Ubuntu.

---

### Post by HermanAB on 2009-05-12
Howdy,

The wizard is called system-config-printer

---

### Post by acreech on 2009-05-13
> **lykwydchykyn said:**
> in ubuntu its "/etc/init.d/cups restart".  One of the few differences between Debian and Ubuntu.

Thanks for the information. I followed the information on the second link and was able to print through my server for the first time.

---

