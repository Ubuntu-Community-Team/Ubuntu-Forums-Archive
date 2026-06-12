---
title: "Ubuntu server and port security"
date: 2009-03-03
forum: Server Platforms
---

### Post by three_jeeps on 2009-03-03
Hi:
I recently installed Ubuntu server, configuring Apache 2, Samba, Email, and mysql servers.  Now that I got through the configuration stumbling blocks I want to look at security issues....I've been looking at the system logs and have seen evidence of root login attempts on various ports (ftp, ssh, http..)
So, I am interested in 2 things:
1) A pointer/description of how to lock down ubuntu server.
2) A pointer to a program that will monitor all port sensing attempts and log the transactions, make a humanreadable report, and provide some security measures, e.g, if repeated port scanning on a number of ports, prevent ANY requests from that ip address.  I used a program some time ago called portsentry that did this.  Is there anything better?
3) (I lied). What is the best port scanning program for Ubuntu server?

Thanks for the pointers
John

---

### Post by E_K on 2009-03-03
you have had root logon attepts on port 80?

1, change standard ports for ssh etc 
   visit google

2, fail2ban

3, nmap

---

### Post by albinootje on 2009-03-03
> **three_jeeps said:**
> I've been looking at the system logs and have seen evidence of root login attempts on various ports (ftp, ssh, http..)
So, I am interested in 2 things:
1) A pointer/description of how to lock down ubuntu server.

Is this server directly connected to the internet, or is there a DSL-router/modem or cable-modem in between ?
If the first, I would firewall the samba ports (137-139,445)
See which ports you're using :
```

netstat -tacn
or :
netstat -tac

```
If you're really paranoid, and have weak passwords in use, take a look at denyhosts or fail2ban.
Also I would replace ftp access by sftp/scp through ssh with chrooted shells for the users.
And last but not least, make sure to make regular backups of your data.
> 
3) (I lied). What is the best port scanning program for Ubuntu server?

Nmap is good enough for me. 
Make sure you scan from outside your network, not just inside your LAN.

---

### Post by three_jeeps on 2009-03-04
> **E_K said:**
> you have had root logon attepts on port 80?

1, change standard ports for ssh etc 
   visit google

2, fail2ban

3, nmap

Sorry, typo...I have had no login attempts on port 80 or 8080
Thanks for the pointers...I did google the subjects of interest.  I mainly wanted to find out the top-level programs, what other ppl trust.  I have changed the standard ports on ssh, but if a scanner just increments through the ports, it is going to find the new one.

thanks again for the help.
-J

---

### Post by three_jeeps on 2009-03-04
> **albinootje said:**
> Is this server directly connected to the internet, or is there a DSL-router/modem or cable-modem in between ?

There is a router in front of it, which port forwards a lot of the standard ports.  Yes the samba ports are wide open

> 
If you're really paranoid, and have weak passwords in use, take a look at denyhosts or fail2ban.
Also I would replace ftp access by sftp/scp through ssh with chrooted shells for the users.
And last but not least, make sure to make regular backups of your data.

I am really paranoid..lol, have a strong password and want to go the extra step.  I kept  ftp as a 'back door' but will shut it off.  I use ssh exclusively.  Using sftp/scp with chrooted shells is a good idea...I didn't think of that.  Thank you. 

Yes, daily, weekly, monthly backups are part of the plan/procedure.

-J


Nmap is good enough for me. 
Make sure you scan from outside your network, not just inside your LAN.

---

### Post by kpatz on 2009-03-04
> **three_jeeps said:**
> There is a router in front of it, which port forwards a lot of the standard ports.  Yes the samba ports are wide openThere's no need to open the samba ports to the internet.  Many ISPs block those ports anyway ever since the Blaster and Sasser worms a few years back.

On your router, forward only the ports you need internet access to.  Those would be your ssh port (use something other than the default), and if you're running a webserver accessible to the 'net, 80 and 443 (for SSL if you're using it).  25 if you're running a mail server that receives mail.

Any other services you (but not others) need to access yourself can be done securely via ssh tunneling.

---

