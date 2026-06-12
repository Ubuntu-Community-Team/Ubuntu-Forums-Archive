---
title: "Best way for a noob to secure a linux box that's online 24/7?"
date: 2009-02-16
forum: Security
---

### Post by Casualuser on 2009-02-16
I haven't used unix(let alone linux) since around 1990.  There wasn't much of an internet back then, and no world wide web.  I got out of the computer field, and have been using Microsoft OS's since.  Well, someone just introduced me to Trinity and got into my Vista install in like 3 minutes.  Yikes, time to switch.

I'm on the road most of the time so I was planning to leave the computer on at home and using something like GoToMyPC to control it.  I'll have to find a linux alternative to that now.  The main reason is to remotely tell the home computer with a fast connection to download movies for me that would take a year to d/l with my wireless internet provider.  So when I get home, I can burn a few dvd's or transfer to an external hd, and be done with it.  I only stay home for 36 hrs or less.

After installing Ubuntu, is there anything else I need to install to reduce or eliminate the chances of someone remotely logging in on my unmonitored linux box?  I have a Linksys 54gl router with dd-wrt and a couple of unused computers lying around at home if that helps any.

Thank you.

---

### Post by matchstich on 2009-02-16
perhaps looking into the following would help

[http://www.linuxclues.com/articles/21.htm](http://www.linuxclues.com/articles/21.htm)

[http://www.rootkit.nl/](http://www.rootkit.nl/)

[http://www.chkrootkit.org/faq/#6](http://www.chkrootkit.org/faq/#6)

[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

[http://ubuntuforums.org/showthread.php?t=535401&highlight=chkrootkit](http://ubuntuforums.org/showthread.php?t=535401&highlight=chkrootkit)

[http://ubuntuforums.org/showthread.php?t=530183&highlight=pidgin](http://ubuntuforums.org/showthread.php?t=530183&highlight=pidgin)

[http://www.linuxforums.org/forum/linux-security/](http://www.linuxforums.org/forum/linux-security/)

[http://www.opendns.com/](http://www.opendns.com/)

---

### Post by HermanAB on 2009-02-17
Simple advice:
Use passwords longer than 9 characters for everything. (I use 16 chars)
Run the Ufw firewall wizard.
Install a rate limiting rule to guard against DOS and brute forcers:

# General new connection rate limiting for DOS and Brute Force protection
iptables -I INPUT -p TCP -m state --state NEW -m limit \
--limit 30/minute --limit -burst 5 -j ACCEPT

Relax and enjoy your new secure machine...

Cheers,

Herman

---

### Post by justin_c18 on 2009-02-21
> **HermanAB said:**
> Simple advice:
Use passwords longer than 9 characters for everything. (I use 16 chars)
Run the Ufw firewall wizard.
Install a rate limiting rule to guard against DOS and brute forcers:

# General new connection rate limiting for DOS and Brute Force protection
iptables -I INPUT -p TCP -m state --state NEW -m limit \
--limit 30/minute --limit -burst 5 -j ACCEPT

Relax and enjoy your new secure machine...

Cheers,

Herman

Where do I add the rule? I have ufw installed, same with gufw. But, it looks like you've added that file in a config somewhere because of the comment. Where would I add it? 

Thanks for letting me know of ufw, and gufw. I feel a lot more secure now.

---

### Post by cb951303 on 2009-02-21
I think the first rule is to install a well tested distro on it.
Debian stable would be a good choice.

---

### Post by kevdog on 2009-02-21
justin -- what services are going to be exposed on the linux box?  This makes a big difference!

---

### Post by HermanAB on 2009-02-22
Regarding the iptables rate limiting suggestion:
Run the command from the command line to make it take effect immediately.  Then edit /etc/rc.d/rc.local and add it to the bottom of the file so it will be loaded next time you reboot.

Cheers,

Herman

---

### Post by redroad55 on 2009-02-24
>  Re: Best way for a noob to secure a linux box that's online 24/7?
Simple advice:
Use passwords longer than 9 characters for everything. (I use 16 chars)
Run the Ufw firewall wizard.
Install a rate limiting rule to guard against DOS and brute forcers:

# General new connection rate limiting for DOS and Brute Force protection
iptables -I INPUT -p TCP -m state --state NEW -m limit \
--limit 30/minute --limit -burst 5 -j ACCEPT

Relax and enjoy your new secure machine...

Cheers,

Herman 

this is what I get:
> john@mediaman:~$ iptables -I INPUT -p TCP -m state --state NEW -m limit \
> --limit 30/minute --limit -burst 5 -j ACCEPT
iptables v1.3.8: bad rate `-burst'
Try `iptables -h' or 'iptables --help' for more information.
john@mediaman:~$ 


then this step:
> HermanAB  	
Re: Best way for a noob to secure a linux box that's online 24/7?
Regarding the iptables rate limiting suggestion:
Run the command from the command line to make it take effect immediately. Then edit /etc/rc.d/rc.local and add it to the bottom of the file so it will be loaded next time you reboot.

Cheers,

Herman 

I get this:
> john@mediaman:~$ edit /etc/rc.d/rc.local
Warning: unknown mime-type for "/etc/rc.d/rc.local" -- using "application/*"
Error: no write permission for file "/etc/rc.d/rc.local"


any help or comments I would appreciate .. Thanks in advance..

---

### Post by brian_p on 2009-02-24
> **redroad55 said:**
> 

any help or comments I would appreciate .. Thanks in advance..

brian@laptop:~$ whatis edit 
edit (1)             - execute programs via entries in the mailcap file

I think you have misunderstood HermanAB's use of the word 'edit'.

---

### Post by redroad55 on 2009-02-24
> Regarding the iptables rate limiting suggestion:
Run the command from the command line to make it take effect immediately. Then edit /etc/rc.d/rc.local and add it to the bottom of the file so it will be loaded next time you reboot.

If you could break down the command line here .. Thanks For Your Help

---

### Post by brian_p on 2009-02-24
> **redroad55 said:**
> If you could break down the command line here .. Thanks For Your Help

```
iptables -I INPUT -p TCP -m state --state NEW -m limit \
--limit 30/minute --limit -burst 5 -j ACCEPT
```

That is all one command. But it is split between two lines to make it look tidy. The '\' says that the command continues on another line. Very useful in a script or configuration file.

**It must not be typed as part of the command at a terminal prompt.**

---

### Post by redroad55 on 2009-02-24
So this is the Cl for terminal? ```
iptables -I INPUT -p TCP -m state --state NEW -m limit--limit 30/minute --limit -burst 5 -j ACCEPT
```

 How then to add it as proposed here?:
> Then edit /etc/rc.d/rc.local and add it to the bottom of the file so it will be loaded next time you reboot.

Thanks again for your help ..

---

### Post by ikisham on 2009-02-24
> **redroad55 said:**
> If you could break down the command line here .. Thanks For Your Help

I think it means
```
sudo gedit /etc/rc.d/rc.local
```

that opens the file with root permission so you can add the commands to it (edit it).

---

### Post by brian_p on 2009-02-24
> **redroad55 said:**
> So this is the Cl for terminal? ```
iptables -I INPUT -p TCP -m state --state NEW -m limit--limit 30/minute --limit -burst 5 -j ACCEPT
```

 How then to add it as proposed here?

Yes. Except there is a space after '-m limit'. And I hope you have 'edit' sorted!

---

### Post by redroad55 on 2009-02-24
> **ikisham said:**
> I think it means
```
sudo gedit /etc/rc.d/rc.local
```

that opens the file with root permission so you can add the commands to it (edit it).

I have nothing @ rc.local ? It opens but nothing there.. so I add:> # General new connection rate limiting for DOS and Brute Force protection
iptables -I INPUT -p TCP -m state --state NEW -m limit \
--limit 30/minute --limit -burst 5 -j ACCEPT

I remove "#" correct? 

Thanks for your help..

---

### Post by ikisham on 2009-02-24
No, you leave '#'. That is a 'comment', a description of the command added (it makes the system not consider the line after it as a command).

---

