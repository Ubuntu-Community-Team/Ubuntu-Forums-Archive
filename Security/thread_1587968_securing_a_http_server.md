---
title: "securing a http server"
date: 2010-10-04
forum: Security
---

### Post by NoctisCaelum on 2010-10-04
Hi, Im running ubuntu server 9.10 and I would like to know what I have to do to protect all the files/system from possible intrusions/attacks.

I have apache, mysql, phpmyadmin and samba running and I connect to it via ssh.

- I already changed the default ssh port.
- Created a new account in phpmyadmin and deleted the root one.

Can someone lend me some tricks about protecting it ? I would be very thankful for it!!

---

### Post by wacky_sung on 2010-10-04
Running a SQL is prone to SQL injection and SSH is prone to dictionary attack.Beside that, running along with samba promote the spread of window worm / spywares.

There are many security you have took into account.

---

### Post by noway2 on 2010-10-04
Try the following: [http://bodhizazen.net/Tutorials/ssh/](http://bodhizazen.net/Tutorials/ssh/)

---

### Post by unspawn on 2010-10-04
Security is not a "fire and forget" thing but a continuous process. Hardening a net-facing machine starts with planning, at install-time and by addressing host issues before you work your way up to web stack issues. While changing ports and accounts is commendable, if you fail to address all host-related issues and decide to only concentrate on particular aspects your efforts IMNSHO are lost. I'd suggest you start at [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812).

---

### Post by kulshoks2121 on 2010-10-06
Make sure to put an option inside /etc/ssh/sshd_config

PermitRootLogin no

when one cracker does brute attack on your root account and gets it right, youre done

---

### Post by bodhi.zazen on 2010-10-06
> **kulshoks2121 said:**
> Make sure to put an option inside /etc/ssh/sshd_config

PermitRootLogin no

when one cracker does brute attack on your root account and gets it right, youre done

The only people who advise this on these forums are people who are new to Ubuntu :p

The root account is locked on Ubuntu, so you can not brute force it.

With that said, however, this advice is spot on with distros such as Fedora where there is a root password and ssh server is installed and listening by default.

Bottom line : Know your distro, know your services, and know your users.

---

### Post by SeijiSensei on 2010-10-06
It's trivial to give root a password and circumvent sudo.  That might not be "the Ubuntu way," but I'd be surprised if there aren't some people out there runnning Ubuntu servers with root passwords.

---

### Post by bodhi.zazen on 2010-10-06
> **SeijiSensei said:**
> It's trivial to give root a password and circumvent sudo.  That might not be "the Ubuntu way," but I'd be surprised if there aren't some people out there runnning Ubuntu servers with root passwords.

Probably, but that is still covered by my post. If you change the default behavior or security features and run servers, you must either understand the security repercussions or suffer the consequences.

---

### Post by anomie on 2010-10-07
[QUOTE=NoctisCaelum]I have apache, mysql, phpmyadmin and samba running and I connect to it via ssh.
...
Can someone lend me some tricks about protecting it ?[/QUOTE]

No tricks. More like a focused, ongoing effort. If possible, I recommend *not* connecting your server to the 'net until you understand how to harden and monitor it properly. 

Hopefully by now you've read through the thread unspawn mentioned in post #4? 

Service by service: 

**_sshd_**

IMO, this topic has become something of a bikeshed painting exercise (with so many reactive utilities to analyze failed logins - most of which I think are useless), but there are a few universal ideas that most folks agree on. I tried to document those here awhile back: 

[http://www.daemonforums.org/showthread.php?t=74](http://www.daemonforums.org/showthread.php?t=74)

On top of those basics, I'll say that I greatly prefer kludges like port knocking to methods like changing to a non-IANA specified port... But that's another discussion that's been done many times. 

**_Apache web server_**

Here is a *starting point*: 

[http://www.petefreitag.com/item/505.cfm](http://www.petefreitag.com/item/505.cfm)

But it's not enough on its own. If you are serious about hardening Apache web server, I implore you to visit your local library or bookstore, and pick up *Apache Security* by Ivan Ristic. (I am in no way affiliated with the author or publisher, and I don't get paid to suggest that. It is a fantastic, eye-opening book.) 

**_phpMyAdmin_**

There is a chapter devoted to PHP / mod_php in *Apache Security*. Read it. Although default configurations in many distros have gotten better over time, PHP is more or less a security nightmare. 

FWIW, I manage several servers that run phpMyAdmin, and I use its cookie authentication, plus I put it behind an HTTP Digest "perimeter authentication" (using Apache, of course). Given the choice between someone attacking Apache at the perimeter or directly attacking phpMyadmin, I choose the former. 

**_MySQL_**

I don't know enough to provide specific suggestions. Be sure that you're not accepting connections from the 'net. Be sure that you're using strong account passwords. Enable and monitor its logging. 

**_Samba_**

I don't know enough to provide specific suggestions. Out of curiosity, do you really need this? (i.e. Turn it off.)

---

