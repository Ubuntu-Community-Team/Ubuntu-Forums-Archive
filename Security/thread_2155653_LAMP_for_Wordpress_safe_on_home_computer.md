---
title: "LAMP for Wordpress safe on home computer?"
date: 2013-06-19
forum: Security
---

### Post by daKoolaid on 2013-06-19
I would like to learn Wordpress for building websites. LAMP installs Apache, Mysql and php servers. Is this safe to use from a home computer? I won't be hosting websites at home, only building them.

---

### Post by Lars Noodén on 2013-06-19
If your home router is like most people's it will not forward connections to your desktop unless you specifically configure it to do so.   

If you are really worried, you can use UFW or GUFW to block incomming connnections to ports 80 and 443 (http and https) from everywhere except the localhost.  That works then only if you are sitting at the same machine that the LAMP stack is installed on.

The short answer is, yes, it's probably safe enough.

---

### Post by sh4d0w808 on 2013-06-19
If you worry then install a virtualbox with a LAMP system inside.

---

### Post by Lars Noodén on 2013-06-19
> **sh4d0w808 said:**
> If you worry then install a virtualbox with a LAMP system inside.

That won't make it any more secure.  It just makes it easier to clean up.  For learning it might be better to take advantage of VM snapshots.  But for security, there's no advantage.  In fact there is an extra layer in which things might go wrong and be exploitable.

---

### Post by sh4d0w808 on 2013-06-19
> **Lars Noodén said:**
> That won't make it any more secure.  It just makes it easier to clean up.  For learning it might be better to take advantage of VM snapshots.  But for security, there's no advantage.  In fact there is an extra layer in which things might go wrong and be exploitable.

Don't agree. If you set up your VM to communicate only with your host OS, then you cannot get attack from there, so the LAMP is secure and not lowering your host system's security (except vulnerabilities in VB of course).

---

### Post by Lars Noodén on 2013-06-19
That's still about the same as restricting access to localhost for non-VM'd services.  That kind of access control is something you have to learn any way.  VMs do add another layer where something can break or otherwise go wrong.  They also add a fair amount of processing and memory overhead, so system resources are just going to waste there.  Though on the plus side you have snapshots which make random messing around much safer and more convenient.  So from a learning perspective VMs are ok, but [for security virtualization is nothing noteworthy](http://www.kugutsumen.com/showthread.php?32395-virtualization-!-security).

---

### Post by sh4d0w808 on 2013-06-19
> **Lars Noodén said:**
> That's still about the same as restricting access to localhost for non-VM'd services.  That kind of access control is something you have to learn any way.  VMs do add another layer where something can break or otherwise go wrong.  They also add a fair amount of processing and memory overhead, so system resources are just going to waste there.  Though on the plus side you have snapshots which make random messing around much safer and more convenient.  So from a learning perspective VMs are ok, but [for security virtualization is nothing noteworthy](http://www.kugutsumen.com/showthread.php?32395-virtualization-!-security).

Thanks for the link, I will check that.

---

### Post by CharlesA on 2013-06-19
> **Lars Noodén said:**
> That's still about the same as restricting access to localhost for non-VM'd services.  That kind of access control is something you have to learn any way.  VMs do add another layer where something can break or otherwise go wrong.  They also add a fair amount of processing and memory overhead, so system resources are just going to waste there.  Though on the plus side you have snapshots which make random messing around much safer and more convenient.  So from a learning perspective VMs are ok, but [for security virtualization is nothing noteworthy](http://www.kugutsumen.com/showthread.php?32395-virtualization-!-security).

Good link. I run VMs when I am testing stuff and as more of a separation of services type thing if I am running a publicly accessible service. It won't be any more secure than a physical box, which is why it helps to learn about security services and (especially) web applications instead of leaving it as a free-for-all on the VM and just wiping it when it gets owned.

---

### Post by daKoolaid on 2013-06-19
Thanks for all the replies! The Wordpress installation walkthroughs I found all set it up with localhost. I can't block all incoming connections to 80 and 443 because then I'd block all web browsing so I guess I will rely on the router to filter connections. This computer is 5 years old, I don't know how well it will run visualization.

If I set Wordpress to localhost, would it be useful still to follow guides to secure apache, mysql and php?

---

### Post by Lars Noodén on 2013-06-19
Your browsing connects to port 80 and 443 on the remote server, not your machine.  On your own machine some high port will be outgoing.   Surf a little and then check with [netstat](http://manpages.ubuntu.com/manpages/raring/en/man8/netstat.8.html).  It's a little more readable if you widen the terminal window a little first.

 ```

netstat -ntp | less

```

So you can safely block 80 and 443 incoming.

---

### Post by 2Stoned on 2013-06-19
> **daKoolaid said:**
> I can't block all incoming connections to 80 and 443 because then I'd block all web browsing so I guess I will rely on the router to filter connections. This computer is 5 years old, I don't know how well it will run visualization.

Do you want to have only certain IP's that are allowed to connect from outside your network? What are the system specs? 

> **daKoolaid said:**
> If I set Wordpress to localhost, would it be useful still to follow guides to secure apache, mysql and php?

If you want to have this LAMP server just to test files/scripts, it's not really necessary to secure it, just make sure ports 22, 80 and 443 are closed from outside. Still it would do no harm te learn yourself hardening the LAMP server.

---

### Post by daKoolaid on 2013-06-19
> **Lars Noodén said:**
> Your browsing connects to port 80 and 443 on the remote server, not your machine.  On your own machine some high port will be outgoing.   Surf a little and then check with [netstat]("http://manpages.ubuntu.com/manpages/raring/en/man8/netstat.8.html").  It's a little more readable if you widen the terminal window a little first.

 ```

netstat -ntp | less

```

So you can safely block 80 and 443 incoming.
Thanks Lars Noodén. I do have ufw enabled. I did some reading and the default is to deny incoming connections so then ports 80 and 443 would be covered. That is what I assume.

> **2Stoned said:**
> Do you want to have only certain IP's that are allowed to connect from outside your network? What are the system specs? 



If you want to have this LAMP server just to test files/scripts, it's not really necessary to secure it, just make sure ports 22, 80 and 443 are closed from outside. Still it would do no harm te learn yourself hardening the LAMP server.
I do not need to only allow certain IP's. Basic system specs are a Core 2 duo 2.4 gighertz with 2 gb of ram. This lamp server is only for local page development so I assume again ufw and localhost are all I need to be safe. Seems correct?

Thanks for the help! I will still look at the LAMP hardening tips just to see them.

---

### Post by CharlesA on 2013-06-19
Should be fine if you are just using it for local development.

---

### Post by 2Stoned on 2013-06-20
> **daKoolaid said:**
> Basic system specs are a Core 2 duo 2.4 gighertz with 2 gb of ram.

Good enough to run a VM.

---

### Post by daKoolaid on 2013-06-20
I went with the no-VM option. Installing everything was easy with tasksel but making all the permissions work right took some searching. I found in the Ubuntu Wiki that I can change ports.conf and add the fqdn file to get everything listenting on 127.0.0.1:80.
[https://help.ubuntu.com/community/ApacheMySQLPHP#Installing_Apache_2](https://help.ubuntu.com/community/ApacheMySQLPHP#Installing_Apache_2)

This is what netstat shows now. Looks good:)
```
[FONT=Verdana]PID/Program name[/FONT]
[FONT=Verdana]tcp 0 0  127.0.0.1:3306   0.0.0.0:*   LISTEN[/FONT]
[FONT=Verdana]tcp 0 0  127.0.0.1:80   0.0.0.0:*   LISTEN[/FONT]
```

---

