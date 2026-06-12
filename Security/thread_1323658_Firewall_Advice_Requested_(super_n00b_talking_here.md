---
title: "Firewall Advice Requested (super n00b talking here)"
date: 2009-11-11
forum: Security
---

### Post by cat2005 on 2009-11-11
I want to use the Firestarter firewall, but find it hard to understand (super n00b talking here).  Its website helped some but I am still confused..

I just want something that will adequately monitor, and if needed block, inbound and outbound traffic.  

Any resources, suggestions, etc?

Right now, I am just hiding behind a router but it wouldn't hurt to have a firewall, would it?

Thanks.

---

### Post by cariboo on 2009-11-12
If you are behind a router with a firewall, you really don't need anything else. If you feel the need for another firewall, there is one installed by default, Firestarter is just a gui front end that allows you to set firewall rules and monitors the connection. Firestarter is no longer supported, so the preferred tool for setting firewall rules is ufw which is also installed by default.

Have a look [here]("http:////www.ubuntugeek.com/ufw-uncomplicated-firewall-for-ubuntu-hardy.html") for more on ufw and [here]("http://www.ubuntugeek.com/gufw-simple-gui-for-ufw-uncomplicated-firewall.html") for more on Gufw.

---

### Post by cat2005 on 2009-11-12
> **cariboo907 said:**
> If you are behind a router with a firewall, you really don't need anything else. If you feel the need for another firewall, there is one installed by default, Firestarter is just a gui front end that allows you to set firewall rules and monitors the connection. Firestarter is no longer supported, so the preferred tool for setting firewall rules is ufw which is also installed by default.

Have a look [here]("http:////www.ubuntugeek.com/ufw-uncomplicated-firewall-for-ubuntu-hardy.html") for more on ufw and [here]("http://www.ubuntugeek.com/gufw-simple-gui-for-ufw-uncomplicated-firewall.html") for more on Gufw.


How can I determine if my router has a firewall?  Sorry, I am a fish out of water on this topic.

Router = Linksys BEFSR41

---

### Post by cariboo on 2009-11-12
Firewalls are usually turned on by default, you can access the management interface by typing in your browser:

```
http://192.168.1.1
```

enter the password you setup when you installed the router, and click the security tab.

---

### Post by espressobeanie on 2009-11-13
I use Firestarter and I filter it based on the ports my programs use. Your computer has up to 65535 ports that are open to hackers without a firewall. You could also employ an ip blocklist if you're looking for more security.

---

### Post by OrangeCrate on 2009-11-13
> **cariboo907 said:**
> If you are behind a router with a firewall, you really don't need anything else. If you feel the need for another firewall, there is one installed by default, Firestarter is just a gui front end that allows you to set firewall rules and monitors the connection. **Firestarter is no longer supported**, so the preferred tool for setting firewall rules is ufw which is also installed by default.

Have a look [here]("http:////www.ubuntugeek.com/ufw-uncomplicated-firewall-for-ubuntu-hardy.html") for more on ufw and [here]("http://www.ubuntugeek.com/gufw-simple-gui-for-ufw-uncomplicated-firewall.html") for more on Gufw.

Firestarter is maintained in Debian, and is made available to Ubuntu users, through the Universe repository.

See here:

[http://packages.debian.org/changelogs/pool/main/f/firestarter/firestarter_1.0.3-8/changelog](http://packages.debian.org/changelogs/pool/main/f/firestarter/firestarter_1.0.3-8/changelog)

---

### Post by cariboo on 2009-11-13
The current version came out in 2005, the debian package maintainer is just adding bug fixes.

---

### Post by bodhi.zazen on 2009-11-13
> **espressobeanie said:**
> I use Firestarter and I filter it based on the ports my programs use. Your computer has up to 65535 ports that are open to hackers without a firewall. You could also employ an ip blocklist if you're looking for more security.

By default there are no significant open ports on Ubuntu.

The default firewall on Linux is iptables. By default the firwall is disabled (permissive).

The default configuration tool is ufw

[Uncomplicated Firewall - UFW - Community Ubuntu Documentation]("https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw") 

To configure your firewall, open a terminal and enter:

```
sudo ufw enable
```

If you prefer a gui tool install gufw.

If you are new to Ubuntu I suggest : 

[Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812") 

If you want an overview of iptables I suggest :

[http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)

---

### Post by cat2005 on 2009-11-14
"By default there are no significant open ports on Ubuntu."

So, does that mean I really don't need a firewall?  

When I used Windows, firewalls were such a pain to configure and maintain.  Are they difficult to maintain / run in Linux?

/ will check out the links others posted...thanks

---

### Post by PoachedSalmon on 2009-11-14
"So, does that mean I really don't need a firewall?"

My guess is that you will probably get a variety of responses to that question. I prefer using a firewall, more for peace of mind.

"When I used Windows, firewalls were such a pain to configure and maintain.  Are they difficult to maintain / run in Linux?"

I'm completely new to Linux and Ubuntu and enabled ufw and installed gufw from the command line with minimal effort. So, it's not hard to do. I'm using the default setting of Deny incoming traffic.

I would also suggest that you confirm that your router firewall is really turned ON. I thought mine was only to discover that Verizon DSL had the firewall turned OFF by default.

---

### Post by cat2005 on 2009-11-14
I found gufw and selected "Deny incoming traffic"

How do I deny / alter "outgoing" traffic?  I can not find that option.

Thank you.

/ ubuntu 9.04

---

### Post by cat2005 on 2009-11-16
bump....anyone?

---

### Post by bodhi.zazen on 2009-11-16
Blocking outgoing traffic is a bit more complex and to do that you will need to either learn iptables or user a more sophisticated configuration tool such as guarddog (I think guard dog has this capability).

A better question is , why do you feel you need to firewall outgoing traffic ? What is it you ar trying to accomplish ?

---

### Post by cat2005 on 2009-11-17
> **bodhi.zazen said:**
> Blocking outgoing traffic is a bit more complex and to do that you will need to either learn iptables or user a more sophisticated configuration tool such as guarddog (I think guard dog has this capability).

A better question is , why do you feel you need to firewall outgoing traffic ? What is it you ar trying to accomplish ?


bodhi.zazen,

I just thought it was odd I was given the option to alter inbound traffic but not outbound traffic.  I was unaware that altering outbound traffic was more difficult.

Would guarddog run on ubuntu?  I used to have that on Mepis but I didn't dare touch it; it looked too confusing.

Truthfully, I don't know "why" I want to alter outbound traffic.  I just assumed that if I am altering inbound traffic, then I should also be altering outbound traffic.  Is that a reasonable assumption or not?

For a newbie noob, would you consider tackling outbound traffic to be more difficult than tackling inbound traffic?  

Thank you for your input.

---

### Post by bodhi.zazen on 2009-11-17
Blocking outbound traffic is more difficult because your clients use pseudo-random ports.

For example, firefox. Firefox will block use a random port on your computer to connect to port 80 on the server.

In addition, I assume you want to allow firefox to connect to some servers ?

So how then are you going to configure your ports so that firefox can use some ports to connect to some servers, but other applications can not use these same ports to connect ot other services ?

You could block all outbound traffic and allow connections out to common destination ports, such as 53 (DNS), 80 (http), an 443 (https).

If you want to use ufw:

```
sudo ufw allow out 53 # this allows traffic to DNS
sudo allow out 80,443 #this allows outboud traffic for web surfing
sudo deny out to any # this denies all other trafic
```You may want or need to add ports such as 22 (ssh), 23 (ftp), and any other traffic you wish to allow. Keep in mind, order is important in iptables, so allow traffic, then deny all.

Note: all clients may send traffic out destined to port 80, this includes links, firefox, wget, etc.


Again, the question is , what are you trying to accomplish ? What is  you want to disallow ?

---

### Post by EJeanmaire on 2009-11-18
> **bodhi.zazen said:**
> By default there are no significant open ports on Ubuntu.

I would somewhat disagree with that, by default mDNS / Avahi spams out on the network and discloses quite a bit of information about you.  But that depends on one's level of paranoia.

---

### Post by Pjotr123 on 2009-11-18
You don't need to monitor or alter outbound traffic for the sake of security. Ubuntu doesn't suffer from spyware, keystroke loggers and malware like that: it's not Windows... :)

You may find this interesting to read:
[http://sites.google.com/site/easylinuxtipsproject/security](http://sites.google.com/site/easylinuxtipsproject/security)

---

### Post by HermanAB on 2009-11-18
Hmm, firewalls are mostly a Windows thing.  With a default Ubuntu install, you don't really need a firewall thingy, since the internet protocol stack is pretty strong as is.  Consider that most firewall devices run Linux and firewalls don't have firewalls...

So, relax and enjoy your Linux system!

---

### Post by Pjotr123 on 2009-11-18
> **HermanAB said:**
> Hmm, firewalls are mostly a Windows thing.  With a default Ubuntu install, you don't really need a firewall thingy, since the internet protocol stack is pretty strong as is.

Agreed, but when you connect your laptop to a shared public access point, activating the firewall (e.g. by means of ufw) is generally a good idea. ;)

---

### Post by jessiebrownjr on 2009-11-18
I just installed NFS as client/server on both my desktop and laptop. I have my hosts.allow/deny set up to allow only my other PC to mount, and deny the rest..

But I opened up more ports during this correct? Im semi newb as well, but do I need to "block all incoming traffic" now as well? Besides of course the IP of the PC i want to mount with?

---

### Post by bodhi.zazen on 2009-11-18
If you wish to allow other computers to mount the NFS shares, yes you will have to allow those computers to connect through your firewall. If you block all incoming traffic no other computer will be able to mount the nfs shares.

You will need to look at these documents :

[http://tldp.org/HOWTO/NFS-HOWTO/security.html](http://tldp.org/HOWTO/NFS-HOWTO/security.html)

[http://rlworkman.net/howtos/NFS_Firewall_HOWTO](http://rlworkman.net/howtos/NFS_Firewall_HOWTO)

As an aside, this is one area where Fedora / Centos is easier, IMO, in that these distros include tools to configure your firewall :

See the attached screen shot. On Fedora simply click the button to allow NFS.

---

### Post by cat2005 on 2009-11-22
Hmmm.....I will skip the outbound monitoring for now and be content with the inbound monitoring.

Thanks to all for the input!

---

### Post by bodhi.zazen on 2009-11-23
Because this is a FAQ, I bloged on this topic :

[http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/](http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/)

I shall *try* to follow that with a blog on Ubuntu Servers =)

---

### Post by cat2005 on 2009-11-25
> **bodhi.zazen said:**
> Because this is a FAQ, I bloged on this topic :

[http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/](http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/)

I shall *try* to follow that with a blog on Ubuntu Servers =)


Very interesting read....thanks.

---

### Post by bodhi.zazen on 2009-11-26
You are most welcome, glad you found it helpful.

---

