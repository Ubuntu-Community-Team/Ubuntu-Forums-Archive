---
title: "Should I configure FTP and Web server on same machine,?"
date: 2009-08-19
forum: Server Platforms
---

### Post by jocampo on 2009-08-19
Simple question but I would like to get opinion from you folks.
 
I am currently running a modest Ubuntu Headless server at home. I configured a VirtualMachine inside (another Ubuntu server) which current is my Web server. Should I deploy FTP on same one or create another VirtualMachine dedicated just for that? I want to keep the administration overhead at its minimum but the Web server is going to host an important site ... FTP is going to be more for fun and sharing stuff with family and friend.

Thanks,

---

### Post by Aptana on 2009-08-19
If they are for two seperate projects then I would install another virtual machine, personally. Although if you find you need FTP for both the website and sharing files with family and friends it'll probably be better to install it on the same virtual machine as the website, to minimise resource usage.

If you do install it on the same virtual machine as the website, you can always change the directory that users log into so you can make the directory completely seperate :)

Just out of curiosity, why did you install a webserver in a virtual machine and not your usual one? :)

---

### Post by jocampo on 2009-08-19
> **Aptana said:**
> If they are for two seperate projects then I would install another virtual machine, personally. Although if you find you need FTP for both the website and sharing files with family and friends it'll probably be better to install it on the same virtual machine as the website, to minimise resource usage.

If you do install it on the same virtual machine as the website, you can always change the directory that users log into so you can make the directory completely seperate :)

Just out of curiosity, why did you install a webserver in a virtual machine and not your usual one? :)

Hi

Thanks for reply. I totally missed the point that FTP will probably help me uploading my HTML content into the same WebServer, you are right about it.

The reason why I want to use the VirtualMachine is in order to keep everything on my physical server secure and safe. I do  use and have important information on that server and would not like to mix that with an FTP server that for now, I am just learning how to make it more secure. In fact, the WebServer (the VirtualMachine) is right now in a DMZ, but the physical server is behind the firewall. Let's say is easier for me backup and restore the vdi file than rebuild the real server from scratch if something catastrophic happens. ;-)

By the way, welcome to the forum and Ubuntu World! :-D

---

### Post by Aptana on 2009-08-19
Ah fair enough. That makes perfect sense. If you wanted to keep every secure as possible you can always just turn on the FTP server when you need it and turn it off when it isn't in use. To go a step further you can only make it connectable through LAN instead of over the internet if it suites you.

And thanks for the welcome. :P I've got my box set up with Ubuntu Server aswell, makes a nice change from CentOS. :)

---

### Post by jocampo on 2009-08-20
:-(

and that just happened last night... can't believe it... someone was trying to get into my server via ssh, brute force attack... checking log looks like was not able ...

---

### Post by cariboo on 2009-08-21
There are two things you can do to solve your problem:

[list=1]
[*] Change the port ssh listens on to something like 2200, and install denyhosts, it is in the repositories. Denyhosts will limit the number of tries to 5 then ban the ip address, for as long as you'd like
[*] Use sftp, it is part of openssh-server, most ftp clients can do sftp, and you can also use nautilus, in the location bar type:

```
sftp://user@server
```
[/list]

---

### Post by hessiess on 2009-08-21
> **jocampo said:**
> :-(

and that just happened last night... can't believe it... someone was trying to get into my server via ssh, brute force attack... checking log looks like was not able ...

if you are worried about security, DONT use ftp, it is not very secure and sends passwords in the clear(completely unencrypted). use sftp with ssh running on a non standard port, with an ultra secure random noise password from [https://www.grc.com/passwords.htm](https://www.grc.com/passwords.htm), imposable to brute force unless you have several billion years to spare;).

---

### Post by grantemsley on 2009-08-21
Instead of using FTP, I recommend scp.  A good windows client is WinSCP.  It works the same as FTP - it transfers files.  But it goes through the ssh server, and makes sure everything is nice and encrypted.

---

### Post by jocampo on 2009-08-21
> **cariboo907 said:**
> There are two things you can do to solve your problem:

[list=1]
[*] Change the port ssh listens on to something like 2200, and install denyhosts, it is in the repositories. Denyhosts will limit the number of tries to 5 then ban the ip address, for as long as you'd like
[*] Use sftp, it is part of openssh-server, most ftp clients can do sftp, and you can also use nautilus, in the location bar type:

```
sftp://user@server
```
[/list]

Yep :-) ...I installed denyhost and really pleased with it. It took me about 1 hr to recreate the whole machine again (was a vm) with Apache on it. I downloaded security updates and installed denyhost and about 7am today, they tried again but was locked ;-) ... I'm planning to change the port later but not so worried now 'cause this machine has no important data. The important one is inside the main firewall, not a DMZ.

BTW...I guess that for ssh, port is specified in /etc/ ... somewhere inside the conf file, right?

Edit: I do not think they were able to get in... but better for me, to build a "clean" machine if I can ...

---

### Post by cariboo on 2009-08-21
I'm not at my computer with Ubuntu on it, but you should look for /etc/ssh/sshd_config, to chnage the port that ssh listens on.

---

