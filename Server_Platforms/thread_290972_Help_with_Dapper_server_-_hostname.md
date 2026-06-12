---
title: "Help with Dapper server - hostname"
date: 2006-11-01
forum: Server Platforms
---

### Post by BackInTimeMan on 2006-11-01
Hi,

I'm just installing the Dapper server, using the "Install to hard drive" option and following "The Perfect Setup" guide from Howtoforge. I left the hostname as ubuntu for now because this is my first server install and I'm just using it to learn. When I've done a few installs (if it takes that many to get it right) I want to run a web and mail server.

My /etc/hosts looks like this:

```
127.0.0.1       localhost.localdomain localhost
192.168.0.100   ubuntu.example.com     ubuntu

[...]
```

When I type:

```
hostname
hostname -f
```

as in the instructions, the commands return these results:

```
hostname: ubuntu
hostname -f: ubuntu.example.com
```

they should both return:

```
ubuntu.example.com
```

I have rebooted as suggested but the output remains the same and it doesn't say anything about what to do if that happens.

How can I correct this?

---

### Post by dbott67 on 2006-11-01
I have the same problem (I followed the same guide).  It doesn't appear to be a problem for me, although I only use the server for testing purposes.   It's been that way for a few months and can't say that it's been an issue.

I installed ISPConfig, Webmin and a few other services.

I would be interested in knowing if it's a problem, what the implications are & how to fix it.

-Dave

---

### Post by BackInTimeMan on 2006-11-01
OK dbott67, I'll carry on with the next step then as it's only for testing here too ATM. BTW, did you use SSH (as suggested) for the next steps or carry on in the root login? Just wondered if it makes any difference.

---

### Post by dbott67 on 2006-11-01
I used the root login, although I seem to recall getting locked out (I couldn't login --- I don't remember the error message, but I had to login to failsafe terminal and edit the hosts file).

I had to add the host name to the end of the **127.0.0.1 localhost.localdomain localhost** line:
```
127.0.0.1       localhost.localdomain localhost **[COLOR="Red"]ubuntu[/COLOR]**
192.168.0.100   ubuntu.example.com     ubuntu
```

-Dave

---

### Post by BackInTimeMan on 2006-11-01
Well I'll just use the root account too, just tried to edit the sources.list via SSH but couldn't save it as it was read only. The vi command "ZZ!" didn't work, or I should say, I couldn't get it to work :)

You had to add the host name in order to get back in again or for some other reason?

---

### Post by dbott67 on 2006-11-01
> **BackInTimeMan said:**
> You had to add the host name in order to get back in again or for some other reason?

After completing all the steps, I re-booted and couldn't login... I just kept getting an error message (unable to resolve name? or something).  Anyhow, I just made the modification above and was able to login.

-Dave

---

### Post by BackInTimeMan on 2006-11-01
> **dbott67 said:**
> After completing all the steps, I re-booted and couldn't login... I just kept getting an error message (unable to resolve name? or something).  Anyhow, I just made the modification above and was able to login.


OK, thanks, I'll remember that if I lock myself out.

Found out why I couldn't save the file I edited over SSH, I hadn't logged in as root, only as user  ;)

Cheers.

---

### Post by aabento on 2006-11-05
I am with the same problem: :( 

localhost aabento 
localhost - f myserver.mydomain.com 

That is important for the functioning of the server? 8)

---

### Post by dbott67 on 2006-11-06
> **aabento said:**
> ... That is important for the functioning of the server? 8)

I don't seem to have any problems accessing the server, so it doesn't appear to be an issue for me.

-Dave

---

