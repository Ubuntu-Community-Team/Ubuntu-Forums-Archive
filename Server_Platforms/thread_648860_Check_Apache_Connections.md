---
title: "Check Apache Connections"
date: 2007-12-24
forum: Server Platforms
---

### Post by Syndacate on 2007-12-24
Yeah, I'm not good with servers, I'm not good with linux, so take anything I say lightly and unknowingly.

I always (on any machine I have) run an apache server, b/c to me it's easier than FTP for file sharing, so on and so forth.

I haven't actually "seen" apache on this machien, I just typed suto apt-get install apache - and php5, so it installed, works for what I use it for, etc.

Though like I said, I've never actually seen any info about it on my computer (at least the one for windows had a monitor).

The one for windows had a log of all connection actions from all IP's.  I was just wondering due to the nature of linux if there's a way to monitor the system....like check all current connections, or something of that sort...

I realize I'm kinda ambiguous here, so any help would be appreciated.

---

### Post by Maxtorm on 2007-12-24
It's not the prettiest way to do it, but you could use ```
netstat -tc
```

---

### Post by Syndacate on 2007-12-24
> **Maxtorm said:**
> It's not the prettiest way to do it, but you could use ```
netstat -tc
```

Yeah, I think I have to agree that that's not the prettiest way to do it, I would be able to deal with it if I was actually able to read it, lol.

Is there any commands apache specific?  Though "apache" isn't a valid command, I thought it would at least find the program and give me some options :-\

---

### Post by Syndacate on 2007-12-25
Anybody?

C'mon, most servers are UNIX based, I'm sure some people know the comman(s) ;).

---

### Post by conjur3r on 2007-12-25
I've used a program called apachetop to monitor apache traffic in realtime. It does a fairly nice job at it too. It runs in a terminal which means you can easily use it via a ssh connection. It doesn't come standard with the rest of apache so install it and give it a go

# sudo apt-get install apachetop

As for logs, check out **/var/log/apache** or there abouts. I don't have access to my boxes atm.

---

### Post by Syndacate on 2007-12-26
> **conjur3r said:**
> I've used a program called apachetop to monitor apache traffic in realtime. It does a fairly nice job at it too. It runs in a terminal which means you can easily use it via a ssh connection. It doesn't come standard with the rest of apache so install it and give it a go

# sudo apt-get install apachetop

As for logs, check out **/var/log/apache** or there abouts. I don't have access to my boxes atm.

Blah

```

syndacate@syndacate-desktop:~$ sudo apt-get install apachetop
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  apachetop: Depends: libadns1 but it is not going to be installed
  noip2: Depends: libc6 (>= 2.7-1) but 2.6.1-1ubuntu10 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
syndacate@syndacate-desktop:~$ sudo apt-get -f install apachetop
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  apachetop: Depends: libadns1 but it is not going to be installed
  noip2: Depends: libc6 (>= 2.7-1) but 2.6.1-1ubuntu10 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
syndacate@syndacate-desktop:~$

```

---

### Post by conjur3r on 2007-12-26
You may have an issue with the **noip2** package.  I'm not sure what this is and it doesn't come back from searches from the package list so I'm assuming it's third party software.  You will most likely need to fix noip2 first.  Or you can remove it and then try installing apachetop again.

---

### Post by Syndacate on 2007-12-26
> **conjur3r said:**
> You may have an issue with the **noip2** package.  I'm not sure what this is and it doesn't come back from searches from the package list so I'm assuming it's third party software.  You will most likely need to fix noip2 first.  Or you can remove it and then try installing apachetop again.

Ah, that's crap.

I need a domain name, and don't feel like paying for one, typing IP's are crap.

What if I didn't have no-ip, how is this depedent on no-ip at all??  It should be a local monitor...

---

### Post by Maxtorm on 2007-12-26
> **Syndacate said:**
> What if I didn't have no-ip, how is this depedent on no-ip at all??  It should be a local monitor...
It looks as though noip's client is dependent on a newer version of libc6 that the installation of apachetop wants to downgrade. I believe ddclient is compatible with no-ip services. You could try uninstalling the no-ip client and installing ddclient in its place. (no guarantees that ddclient isn't dependent on a different version of libc6 as well though)

---

### Post by Syndacate on 2007-12-26
> **Maxtorm said:**
> It looks as though noip's client is dependent on a newer version of libc6 that the installation of apachetop wants to downgrade. I believe ddclient is compatible with no-ip services. You could try uninstalling the no-ip client and installing ddclient in its place. (no guarantees that ddclient isn't dependent on a different version of libc6 as well though)

What does ddclient do?

---

### Post by Maxtorm on 2007-12-26
> **Syndacate said:**
> What does ddclient do?
It keeps the dynamic DNS provider updated with your current IP address -- much the same as the no-ip client I would imagine.

---

### Post by Syndacate on 2007-12-26
> **Maxtorm said:**
> It keeps the dynamic DNS provider updated with your current IP address -- much the same as the no-ip client I would imagine.

Hrm, what does the actual client part do?

Because it uninstalled noip2 (**sudo apt-get -f install**) and my domain name is still works..

So if it's not there, and it's running, what's the purpose of the client in the first place?

---

### Post by Maxtorm on 2007-12-26
As long as your IP address hasn't changed since the last time your dynamic DNS client sent an update to the server, your domain name will still work.

However, if your IP address changes, no-ip's servers will not be updated (since the client is no longer running) and will be directing requests for your domain to the old IP address. The point of the client is to send regular updates to no-ip's servers so that requests for your domain name get to your current IP address.

---

### Post by Syndacate on 2007-12-27
> **Maxtorm said:**
> As long as your IP address hasn't changed since the last time your dynamic DNS client sent an update to the server, your domain name will still work.

However, if your IP address changes, no-ip's servers will not be updated (since the client is no longer running) and will be directing requests for your domain to the old IP address. The point of the client is to send regular updates to no-ip's servers so that requests for your domain name get to your current IP address.

Why can't I just go to the site and update it when I change IP?

---

### Post by conjur3r on 2007-12-27
You can still go to the site and change your IP address.  The client is useful if your IP address changes frequently and you don't want the hassel of changing the dns entry all the time.

---

### Post by Syndacate on 2007-12-27
> **conjur3r said:**
> You can still go to the site and change your IP address.  The client is useful if your IP address changes frequently and you don't want the hassel of changing the dns entry all the time.

Ah, I see

Screw NOIP client then, my IP is pretty damn static.

---

