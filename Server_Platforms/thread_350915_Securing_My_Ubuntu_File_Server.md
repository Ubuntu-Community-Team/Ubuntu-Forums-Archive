---
title: "Securing My Ubuntu File Server"
date: 2007-02-01
forum: Server Platforms
---

### Post by thornomad on 2007-02-01
Hello,

I have a static IP address and am setting up a Ubuntu File Server.  My goal: to keep all my files in a centralized location that I can access locally for day-to-day use and also when I am traveling.  Have a couple laptops, a couple desktops, and my girlfriend and I use all of them interchangeably.  (This centralized file server would also perform backups and be data redundant to help with recovery in case of a failure of some sort.)  I run Ubuntu and Mac systems only.

My concern, of course, is security.

My home network exists behind a router/firewall; I only open the ports that are necessary to accessing the file server from the big scary world.  At home (local network) I plan to use NFS (or maybe AFP, whatever is fastest) to access the files quickly on a gigabit network.  On the road, I plan to connect via SSH (using FUSE: sshfs).

My questions are:

1. I currently have another older machine running an apache web server; is it safer to keep the web server (port 80) and my file server on seperate machines?  Any compromised security if they are in the same box?  I would prefer them be in the same box to save power.

2. If I secure SSH with public/private key access (and pass phrases), and only open ports 22 and 80 to the box, is that enough to keep my files safe ?  What more should I be doing to make sure that things are secure on my end?

Thanks!

---

### Post by scrooge_74 on 2007-02-01
I think you are in the right track, maybe having to separate machines for the web server and the file server is a good idea

---

### Post by Moldz on 2007-02-01
The only safety advantage to keeping the services on separate boxes is that if there is a vulnerability on Apache, then it can help keep your other box secure.  Keep in mind though, now an attacker is inside your network without the need to bypass your SSH tunnel.

If you are really concerned about it, there are two things you can do.  First, make sure to keep up-to-date with security patches for SSH and Apache.  You could join the appropriate mailing lists to get a heads up for problems.  Second, you could put Apache on the same box but in a chroot jail.

One simple thing you can do is move your SSH port from 22 to another random port 43124.  At least for now, all those automated scans for SSH don't bother checking other ports.  Make sure to take any warnings about the server key fingerprint changing seriously, it is probably an attacker.

---

### Post by PetePete on 2007-02-01
install fail2ban

after X failed login attempts on ssh/apache it will ban that IP for a given duration

---

### Post by thornomad on 2007-02-01
Hey everyone,

Thanks for your responses; sounds like hit or miss with keeping separate boxes.  Certainly sounds like the easiest thing to do.  Smile.  

I will look into the chroot jail -- I had never heard of that.  And fail2ban sounds great too.  

And, good for me to think of Apache as the real weakness; I don't know much about Apache at all, and was really worried about what you said: that someone could hack through Apache and then have access to everything else on that system.  I will look into whether or not the chroot jail would prevent that from happening.  I don't mind so much if they took down Apache ... just wouldn't want them to be able to get at the data stored on other hard drives.

D

---

### Post by elst on 2007-02-01
If the hardware specification is sufficient then you could run the Web server in a virtual machine, and separate the services that way.

---

### Post by vargasman on 2007-02-26
> **elst said:**
> If the hardware specification is sufficient then you could run the Web server in a virtual machine, and separate the services that way.

How would one set up a server in a vitual machine? This option sounds great for me.

---

### Post by thornomad on 2007-02-27
I am not sure, but am interested as well; I have a second older laptop that I can run the Apache server on -- but a part of m me would rather save the energy and only power one dedicated machine to handle all my needs.  Seems wasteful, energy-wise, to have them both running side by side.  But: if security is a problem ...

I don't know.  I am not sold either way yet.

---

### Post by MJN on 2007-02-27
> **thornomad said:**
> But: if security is a problem ...
 
Let's not get carried away here. Apache is after all the most common web server on the Internet by far and so if there are any outstanding vulnerabilities we'd all be doomed.
 
If you're concerned about its security check out the known vulnerabilities for it at [http://httpd.apache.org/security_report.html](http://httpd.apache.org/security_report.html) and make sure you're patched up-to-date. It's as simple as that really.
 
Mathew

---

### Post by elst on 2007-02-28
> **vargasman said:**
> How would one set up a server in a vitual machine? This option sounds great for me.

There are several different products and technologies for doing this. The most easy and polished is the proprietary (but no-fee) VMware server. QEMU is an Open Source product that offers most of the capabilities of VMware, but requires a bit more work. Xen is another Open Source virtualization system, and I beleive that there are experimental Ubuntu packages for it.

To clarify virtual machines and security - a virtual machine isn't inherently more secure than a physical one, but if you have dedicated systems built for particular tasks you can much more aggressively configure each one for minimum loopholes. A lot of security breaches result from very simple and easily avoidable errors in configuration.

A side benefit of virtualization is that it makes disaster recovery *much* simpler since you can snapshot systems at will, and that applies to both recovery from hardware or  system compromise.

---

### Post by gaten on 2007-03-01
If you're worried about security with Apache, check out mod_chroot ([http://core.segfault.pl/~hobbit/mod_chroot/](http://core.segfault.pl/~hobbit/mod_chroot/)) and mod_security ([http://www.modsecurity.org/)](http://www.modsecurity.org/)). 

mod_chroot is an easy way to jail a process without all the moving around and copying a billion different files. 

mod_security is a "firewall" for your webserver; it can detect and prevent many different attacks. This one is a little more involved as far as installation and configuration, and even more in reading the log files. 

The suggestions everyone else gave are great too, this is my suggestions for a good security posture (many repeats from the above posts, just reiterating for clarity and completeness)

[LIST=1]
[*]Use SSH keys, completely disable password authentication (use strong passwords on your keys of course)
[*]Forward EVERYTHING through SSH. FTP, VNC, whatever.
[*]Change the default ports of any services that you can. You can do this in the service configuration or just make your life easy and forward the ports with your router.
[*]Install fail2ban
[*]Install mod_security and mod_chroot for Apache
[*]If you have any databases or server side scripting services (PHP for example) make sure you jail those processes as well.[/LIST]That's about as complete as I can think without writing a whole tutorial. Check out these tuts for some real good security advice:

Securing Apache: [http://www.securityfocus.com/infocus/1786](http://www.securityfocus.com/infocus/1786)
Securing Apache2: [http://www.securityfocus.com/infocus/1694](http://www.securityfocus.com/infocus/1694)

Securing PHP: [http://www.securityfocus.com/infocus/1706](http://www.securityfocus.com/infocus/1706)

Securing MySQL: [http://www.securityfocus.com/infocus/1726](http://www.securityfocus.com/infocus/1726)

Search for more SSH tuts, think about jailing SSH too. OK, hope that helps.

---

### Post by thornomad on 2007-03-03
Hey thanks for those resources and that extra information; I appreciate it.  I am still going back and forth about whether or not I want the file server to also do the web serving.

I originally planned to only allow access via SSH (passkey with password); but would be nice to do the web on the same box.  Just worried something bad will happen between them.  (And me just wanting to save power.)

---

