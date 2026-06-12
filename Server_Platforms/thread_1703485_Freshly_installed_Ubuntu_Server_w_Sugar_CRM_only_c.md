---
title: "Freshly installed Ubuntu Server w/ Sugar CRM only connects to apache via localhost."
date: 2011-03-09
forum: Server Platforms
---

### Post by Sargasm on 2011-03-09
I just finished an install of sugar crm (using the bitnami stack).

The sugar console can only be accessed via localhost:8080.  Any attempt to connect to the internal lan ip 192.168.0.7:8080 = fail.

I have considered it might be a routing issue or some setting in apache server, but I am really bumbling around in the dark and I'd rather not hose my system monkeying around right now.  (I know that's the best way to learn, but it will be time consuming)

Are the default routing settings on ubuntu server such that routing has to be added to get from eth0 to localhost?  If so, what is the command to do so?

Much appreciated, sorry for newbing up the place :D

---

### Post by arrrghhh on 2011-03-09
Well, by default the ubuntu firewall (ufw) is disabled - as there's no ports open, there's nothing to block.

However, have you turned it on?  I have it set to allow all local traffic so for better or worse if someone is on my LAN they have full access to my server.

Do you have any other firewalls on the LAN?  Are the devices on the same subnet or switch?

---

### Post by Sargasm on 2011-03-09
Nope... just naked LAN.  If I try to connect on localhost:8080 or 127.0.0.1:8080 from the machine, it connects no prob.

If I go to another machine and type in its ip 192.168.0.7:8080, no dice.

[edit] how would I set it to accept all incoming traffic?  I am going to keep this thing behind my firewall for the time being, I just need it ready to bring into my office so I can work on configuration.

---

### Post by Sargasm on 2011-03-09
Ok, I did sudo iptables -P INPUT ACCEPT and no dice. 

Could this be an apache problem?

---

### Post by arrrghhh on 2011-03-09
> **Sargasm said:**
> Ok, I did sudo iptables -P INPUT ACCEPT and no dice. 

Could this be an apache problem?

I am no iptables expert, I prefer UFW cuz... I'm dumb :p.

Is ufw enabled?  ```
sudo ufw status
```

---

### Post by Sargasm on 2011-03-09
Nope.  Not active.  :/

I feel like it might be an apache setting, but I'm super frustrated.  I'm pretty close to just taking the performance hit and setting up the machine on windows 7 and migrating to linux later.

---

### Post by wongo888 on 2011-03-09
Are you running this sugar app on a virtual machine? Running on a bridged adapter?

Check your routing if you want to see it:

```
$ route
```

Check apache's listening port:

```
$ sudo apache2ctl fullstatus
```

Have you checked your open ports?

```
$ netstat -aunt
```

```
$ sudo lsof -i
```

From another machine run:

```
$ nmap -A -T4 YOUR_MACHINE_IP
```

I'm assuming that you already tried:

```
$ sudo iptables -L
```

and

```
$ cat /etc/apache2/ports.conf

# If you just change the port or add more ports here, you will likely also
# have to change the VirtualHost statement in
# /etc/apache2/sites-enabled/000-default
# This is also true if you have upgraded from before 2.2.9-3 (i.e. from
# Debian etch). See /usr/share/doc/apache2.2-common/NEWS.Debian.gz and
# README.Debian.gz

NameVirtualHost *:80
Listen 80

<IfModule mod_ssl.c>
    # If you add NameVirtualHost *:443 here, you will also have to change
    # the VirtualHost statement in /etc/apache2/sites-available/default-ssl
    # to <VirtualHost *:443>
    # Server Name Indication for SSL named virtual hosts is currently not
    # supported by MSIE on Windows XP.
    Listen 443
</IfModule>

<IfModule mod_gnutls.c>
    Listen 443
</IfModule>

```

Check your virtual host configuration or paste it. Look for allow deny issues or VirtualHost misconfiguration. Check your apache error logs if your remote browser is giving 403 errors.

---

