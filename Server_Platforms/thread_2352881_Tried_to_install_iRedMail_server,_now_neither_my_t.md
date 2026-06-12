---
title: "Tried to install iRedMail server, now neither my teamspeak or plex server works."
date: 2017-02-16
forum: Server Platforms
---

### Post by bjoen on 2017-02-16
Hello!

I have an Ubuntu Server running 16.04.1 which is use for Nextcloud, Plex, Teamspeak, NAS and a webserver. I enjoy trying new things with it and thought it would be fun to try installing a mailserver on it, I used iRedMail. 

I successfully got working but now no one can join my teamspeak server and when I go try to access Plex I can't access my server. The Teamspeak ports doesn't even show up on [www.canyouseeme.org]("http://www.canyouseeme.org") anymore. 

The one thing I could think of that might have caused the problems was when I edited the /etc/hosts and /etc/hostname files, but I believe I changed them back to the way they were.

Here's what they look like atm.
```
[FONT=&amp]127.0.0.1
localhost127.0.1.1
Server# The following lines are desirable for IPv6 capable hosts
::1localhost ip6-localhost ip6-loopback
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters[/FONT]
```
```
Server
```

I can't think of anything else that I might have messed up, any suggestions?
I'm not in a position where I'm able to reinstall the OS entirely.

---

### Post by SeijiSensei on 2017-02-16
If that's the /etc/hosts file, the syntax is wrong.  It should be
```
127.0.0.1     localhost
```
with the IP address in the first field and the hostname in the second field.  They must be separated by one or more spaces or tab characters.  You can add additional "aliases" like this:
```
127.0.0.1     localhost    localhost.localdomain
```

---

### Post by bjoen on 2017-02-16
> **SeijiSensei said:**
> If that's the /etc/hosts file, the syntax is wrong.  It should be
```
127.0.0.1     localhost
```
with the IP address in the first field and the hostname in the second field.  They must be separated by one or more spaces or tab characters.  You can add additional "aliases" like this:
```
127.0.0.1     localhost    localhost.localdomain
```

[COLOR=#1D2129][FONT=&quot]Ok, I've changed it but after a reboot the problems I have are still there. 




[FONT=inherit]While installing iRedMail I added an SSL certificate as well but I can't imagine that causing any problems here.[/FONT]
[/FONT][/COLOR]

---

### Post by Habitual on 2017-02-16
> **bjoen said:**
> ```
Server
```

I can't think of anything else that I might have messed up, any suggestions?
I'm not in a position where I'm able to reinstall the OS entirely.What's that about?
Just "Server" all by its self?

---

### Post by bjoen on 2017-02-16
> **Habitual said:**
> What's that about?
Just "Server" all by its self?

That's the Hostname file.

---

### Post by darkod on 2017-02-16
Did you miss the very important warning in the iRedMail install instructions that say to install it ONLY on brand new default ubuntu server installations? And not on a server that already has applications on it.

The install process is actually a script that is touching many things I would say... I don't know if you can easily get out of this.

---

### Post by bjoen on 2017-02-16
I guess I did, I get too eager sometimes and it backfires every now and then.

---

### Post by darkod on 2017-02-17
The thing is that iRedMail is not a "simple" email server. It has it's things like webUI, installing a number of packages, changing config files etc...

If you only installed postfix with apt-get probably nothing would have happened.

It would be better if you modify the thread title that you installed iRedMail not just saying mailserver (most people here would think postfix)... Maybe someone knows how to help. Not sure if you can modify the main thread title now or you have to ask an admin to do it.

---

### Post by bjoen on 2017-02-17
Hm, looks like someone did.

---

### Post by bjoen on 2017-02-18
> **darkod said:**
> The thing is that iRedMail is not a "simple" email server. It has it's things like webUI, installing a number of packages, changing config files etc...

If you only installed postfix with apt-get probably nothing would have happened.

However, the only software that it warns about is having any mail-related software installed. 
The only one I had was MySQL which I don't have any problems with at the moment. Apache2 as well but it doesn't warn about that.

---

### Post by darkod on 2017-02-18
I agree they could have (and should have) worded the warning much better, but the word FRESH says enough for me. Any server with applications already running on it can't be considered fresh installation.

Changing the apache config to install iredmail webmail and webGUI probably messed up any applications you have that used apache port 80/443. So if you want to troubleshoot you should start there.

Also the warning says it backs up files before modifying, so if you google around where these copies are saved, you might be able to easily put back apache related files as they were before. That's how I would start... In addition to that by checking which services and on which ports are actually running right now.

---

### Post by bjoen on 2017-02-18
> **darkod said:**
> I agree they could have (and should have) worded the warning much better, but the word FRESH says enough for me. Any server with applications already running on it can't be considered fresh installation.

Changing the apache config to install iredmail webmail and webGUI probably messed up any applications you have that used apache port 80/443. So if you want to troubleshoot you should start there.

Also the warning says it backs up files before modifying, so if you google around where these copies are saved, you might be able to easily put back apache related files as they were before. That's how I would start... In addition to that by checking which services and on which ports are actually running right now.

Yeah, I'm not blaming anyone but myself.

It actually made backups of the Apache configs itself. 
Checking "netstat" tells me that ports for teamspeak and plex is running but everything using port 80/443 is working fine.

---

### Post by bjoen on 2017-02-24
Ok, if anyone else would run into a similar problem. Configuring the iptables to accept by default solved the problem.

```

[COLOR=#242729][FONT=Consolas]iptables -P INPUT ACCEPT
[/FONT][/COLOR][COLOR=#242729][FONT=Consolas]iptables -P OUTPUT ACCEPT [/FONT][/COLOR][COLOR=#242729][FONT=Consolas]
[/FONT][/COLOR][COLOR=#242729][FONT=Consolas]iptables -P FORWARD ACCEPT

[/FONT][/COLOR]iptables -F INPUT
iptables -F OUTPUT 
iptables -F FORWARD[COLOR=#222222][FONT=Verdana]
```[/FONT][/COLOR]

---

