---
title: "Questions From A Begginner (Webmin)"
date: 2010-05-20
forum: Server Platforms
---

### Post by mjhasbach on 2010-05-20
I've spent several hours today installing and configuring Ubuntu Server. I have managed to get Webmin, LAMP, PHPMyAdmin, Dovecot, Postfix, an FTP server (can't remember the name), and a few other things up and running. This has been quite a learning experience for me considering the last time I had any experience with Linux was probably about three years ago. Also, the only previous experience I have had as far as LAMP goes was Windows programs such as XAMPP and Apache2Triad (also a while ago). Webmin was a great help as soon as I got past the libmd5-perl problem that others have been experiencing.

Anyway, I'm afraid I messed my install up...everything was going fine until I tried to assign a Static IP Address to my server via Webmin. I decided on 192.168.1.250 since it is pretty high up there with little chance of conflict with other machines on my network. When I reboot my server, it gets hung up on the Ubuntu 10.04 Loading Screen (purple background, white text, white/orange 'loading' dots). When I switch over to the terminal, it says

```

init: network-interface (lo) pre-start process (741) terminated with status 1
init: network-interface (eth1) pre-start process (743) terminated with status 1
init: network-interface (eth0) pre-start process (744) terminated with status 1
init: network-interface (lo) post-stop process (747) terminated with status 1
init: network-interface (eth1) post-stop process (748) terminated with status 1
init: network-interface (eth0) post-stop process (749) terminated with status 1

```

I am unable to access the terminal to make any changes and I'm not sure how to fix this.


I have a bunch of other questions that I'll throw out there in case anyone wants to answer:

[LIST]
[*]I bought a domain with GoDaddy a couple of days ago. Having that domain point to my server is something that I still need to accomplish. What all do I need for that? DHCP Server and BIND DNS Server, right? Any good tutorials?
[*]Bacula Backup System sounds pretty interresting. Does it have the capability to make network backups to a Windows machine?
[*]I think I've decided on Dovecot+Postfix for my mail solution based on what I've heard. Does that sound like a good combination? Any good tutorials on how to get that set up via Webmin
[*]I noticed with the Webmin Command Shell, it doesn't seem to like Yes or No questions (when the system asks for user input). I'm guessing this doesn't really replace SSH?
[*]Are there any other required modules that I may be missing if my goal is to run a website?
[/LIST]

Please forgive the length of the post and my lack of knowledge/experience with Linux.

---

### Post by Jive Turkey on 2010-05-20
It sounds like you have physical access to the machine, right?

If so you could try booting with a live cd and editing your /etc/network/interfaces file to reflect the settings you need.  There are lots of examples around.  

I would advise not using webmin.  It handles some things ok, but some other things are not really set up to configure ubuntu services correctly.  You'll be better off doing it all through ssh IMHO.

I've always used DynDNS for my home network, I don't know what you need to make your home server play nice with Godaddy's name servers.

I've stumbled across a couple of pretty good end to end tutorials for what you are trying to do.  You could try this one:
[http://www.howtoforge.com/perfect-server-ubuntu-10.04-lucid-lynx-ispconfig-3](http://www.howtoforge.com/perfect-server-ubuntu-10.04-lucid-lynx-ispconfig-3)

---

### Post by cdenley on 2010-05-20
> **mjhasbach said:**
> I bought a domain with GoDaddy a couple of days ago. Having that domain point to my server is something that I still need to accomplish. What all do I need for that? DHCP Server and BIND DNS Server, right? Any good tutorials?


No need to run your own DNS server when you can just use godaddy's. Just configure your DNS records in their web interface.

---

### Post by mjhasbach on 2010-05-20
I guess I'll just start over and follow the steps from the The Perfect Server guide.

I'm trying to get this website up an running with as small of a learning curve as possible, but I want to do it right the first time.

Is everything on a Linux server this fragile? There's no reason I shouldn't be able to boot and access the terminal if the network settings are messed up (if I have direct access to the machine). Is there a way to protect myself from making mistakes like this in the future (e.g. automatic backup of important configuration files that can be restored if something goes wrong)? I can't imagine I'm the only person who's ever made a mistake that has made their server unbootable. There should be a way that I can force myself past the network error and manually /etc/network/interfaces via the command line.

It's a shame, Webmin looked nice for the brief time I was using it, and I've heard good things about it.

[quote=cdenley]
No need to run your own DNS server when you can just use godaddy's. Just configure your DNS records in their web interface.
[/quote]

I'm not entirely sure how to do this, but I'll look into it when the time comes.

---

### Post by toraih on 2010-05-21
Insert your Ubuntu Server CD and choose "Rescue broken system" in the boot menu.

After configure language and keyboard-layout etc. choose your root-partition and choose "Execute a shell in [root-partition]".
(the rescue-shell has no comfort, you may want to use bash (type: bash <enter>))

Open interfaces-configuration in you favorite editor, for me:
```
joe /etc/network/interfaces
```
or 
```
nano /etc/network/interfaces
```

Check the correctness of the entries and for broken comment-lines.
(a broken comment was the problem i had today, seems to be broken by webmin)

I hope this helps....

---

