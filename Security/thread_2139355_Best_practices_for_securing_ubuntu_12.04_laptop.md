---
title: "Best practices for securing ubuntu 12.04 laptop"
date: 2013-04-26
forum: Security
---

### Post by jsvidyad on 2013-04-26
Hello,

    I am planning to install ubuntu 12.04 on my laptop. What I usually do for security is to lock the root account, edit the file /etc/hosts.deny and add the line ALL: ALL , set up a firewall (ufw/Gufw in this case) with default rules of Incoming:Deny, Outgoing:Allow. Is this enough for providing reasonable security for my laptop? If you have ideas about what else I can do to secure the planned ubuntu 12.04 installation on my laptop, please let me know.

---

### Post by CharlesA on 2013-04-26
Root is disable by default, by the way. :)

If you have the firewall set to block incoming connections, I doubt there is a need for DenyHosts.

---

### Post by kevdog on 2013-04-28
If there are no running services on your laptop (which there are not by default) there isn't any point to set the default input chain to deny.  Wouldn't it be better to run noscript or equivalent from the browser?

---

### Post by Soul-Sing on 2013-04-28
consider your laptop as an usb stick with some extra's, so: encryption, encryption, encryption==> home, or better the entire disk.

---

### Post by CharlesA on 2013-04-29
> **Soul-Sing said:**
> consider your laptop as an usb stick with some extra's, so: encryption, encryption, encryption==> home, or better the entire disk.

Pretty much. That is doubly important if you travel with your laptop.

Which doesn't stop me from not doing it. >.>

---

### Post by JessicaTsang on 2013-04-29
> **CharlesA said:**
> Root is disable by default, by the way. :)

If you have the firewall set to block incoming connections, I doubt there is a need for DenyHosts.

Everytime I restart my computer, I have to load up the firewall configuration again to turn it on. Is there a way where I don't have to do this at all?

---

### Post by jsvidyad on 2013-04-29
> **JessicaTsang said:**
> Everytime I restart my computer, I have to load up the firewall configuration again to turn it on. Is there a way where I don't have to do this at all?

Are you using a ufw/Gufw firewall ?

---

### Post by jsvidyad on 2013-04-29
Hello,

   I think my first post wasn't too clear. I wasn't asking about securing physical security of my laptop. I was asking about protecting my laptop from intruders over the internet and preventing them from taking over the ubuntu 12.04 installation on my laptop or being able to access my personal files in my home directory on the laptop.

---

### Post by CharlesA on 2013-04-29
> **jsvidyad said:**
> Hello,

   I think my first post wasn't too clear. I wasn't asking about securing physical security of my laptop. I was asking about protecting my laptop from intruders over the internet and preventing them from taking over the ubuntu 12.04 installation on my laptop or being able to access my personal files in my home directory on the laptop.

As long as you don't install any remote access software like SSH or VNC, you should be fine.

Enable your firewall too.

---

### Post by jsvidyad on 2013-04-29
What does adding the line
ALL: ALL

to my /etc/hosts.deny file actually do ? What does it accomplish?

---

### Post by CharlesA on 2013-04-29
> **jsvidyad said:**
> What does adding the line
ALL: ALL

to my /etc/hosts.deny file actually do ? What does it accomplish?

It will deny access to any services that support tcpwrappers. Unless you have installed a service like ssh or vnc, you don't need that.

---

### Post by jsvidyad on 2013-04-29
Can you tell me what those two ALL statements stand for?

---

### Post by CharlesA on 2013-04-29
> **jsvidyad said:**
> Can you tell me what those two ALL statements stand for?

Read the manpage:
[http://linux.die.net/man/5/hosts.deny](http://linux.die.net/man/5/hosts.deny)

> ALL: ALL
This denies all service to all hosts, unless they are permitted access by entries in the allow file. 

---

### Post by jsvidyad on 2013-05-04
So, if I add the line
ALL: ALL
to my /etc/hosts.deny file, it will block any and all external computers(and therefore any potential intruders) from being able to connect to or access my computer and thus prevent someone else from being able to break into my computer??

---

### Post by Stonecold1995 on 2013-05-04
> **jsvidyad said:**
> So, if I add the line
ALL: ALL
to my /etc/hosts.deny file, it will block any and all external computers(and therefore any potential intruders) from being able to connect to or access my computer and thus prevent someone else from being able to break into my computer??
Yes.  The only way a person can break into a computer is by "tricking it" into thinking the intruder is a legit user, then taking advantage of that trust.  But if your computer is instructed to deny all non-physical access, there's no way it can be hacked in that way.

Unless you are using a service like SSH, you will not have any problems with adding that to hosts.deny.

Remember though, by default Ubuntu doesn't come installed with any software which can be taken advantage of anyways (such as OpenSSH, Apache, etc).

---

### Post by jsvidyad on 2013-05-06
So, adding the line
ALL: ALL
to my /etc/hosts.deny file will deny all non-physical network based access attempts to get into my computer, right?

Also, isn't the VNC server Vino installed by default in ubuntu? Isn't that a security issue? I would think that ideally the default install should not have a VNC server

---

### Post by Irihapeti on 2013-05-06
> **jsvidyad said:**
> Also, isn't the VNC server Vino installed by default in ubuntu? Isn't that a security issue? I would think that ideally the default install should not have a VNC server

Yes, Vino is installed by default, but not enabled. It's very (too?) easy to enable, and as a result it's been one of the most common causes of security breach seen on the forums. The other common one is ssh with a weak password.

The suggestion has been made that it shouldn't be installed by default, but for some reason it was rejected.

---

### Post by jsvidyad on 2013-05-06
Hello,

   I just wanted to ask if anyone had any more suggestions for how to secure a new ubuntu 12.04 fresh install from network based threats.

---

### Post by sammiev on 2013-05-06
> **jsvidyad said:**
> Hello,

   I just wanted to ask if anyone had any more suggestions for how to secure a new ubuntu 12.04 fresh install from network based threats.

Enable the [firewall]("http://ubuntuforums.org/showthread.php?t=1876124") and surfing habits do wonders.

---

### Post by jsvidyad on 2013-05-06
What do you mean by surfing habits?

---

### Post by jsvidyad on 2013-05-06
When I set up the ufw/Gufw firewall, I'm planning to use default rules of incoming:deny and outgoing:allow and right now I'm not planning to set up any other ufw firewall rules. Do you think this is a secure enough firewall configuration?

---

### Post by sammiev on 2013-05-06
> **jsvidyad said:**
> When I set up the ufw/Gufw firewall, I'm planning to use default rules of incoming:deny and outgoing:allow and right now I'm not planning to set up any other ufw firewall rules. Do you think this is a secure enough firewall configuration?

It all depends on your rules but I'm set to Deny all in and out. Then I allow what I want out only.

---

### Post by jsvidyad on 2013-05-07
The reason why I'm setting the default outgoing rule to allow is because it can be a bit of a headache otherwise trying to find out which ports have to be allowed for specific applications. For example, in my university it seems for the wireless connection, certain ports have to be allowed outbound access. 

Is using a default outgoing rule of allow a big security risk? I will be setting the default incoming rule to deny.

---

### Post by Irihapeti on 2013-05-07
From what I've observed over the last five years or so on these forums, the main security problems seem to be due to enabling VNC, and installing an ssh server and using only a weak password to protect it.

I know that there's some discussion, heated at times, about the need to block outgoing connections. However, I can't say that I've seen any problems that were definitely caused by not blocking outgoing connections.

Note that I'm talking about ordinary desktop computing here. Once you start setting up web and mail servers and so on, it's a whole different ball game.

---

### Post by jsvidyad on 2013-05-07
I'm going to install ubuntu 12.04 on a laptop and use it for personal purposes. I won't be installing any servers on the laptop.

---

### Post by Irihapeti on 2013-05-07
> **jsvidyad said:**
> I'm going to install ubuntu 12.04 on a laptop and use it for personal purposes. I won't be installing any servers on the laptop.

Then I'd suggest enabling ufw with the default settings (deny in, allow out) and uninstalling Vino. That, and being sensible about which websites you visit, should be enough for most purposes.

---

### Post by jsvidyad on 2013-05-07
> **Irihapeti said:**
> Then I'd suggest enabling ufw with the default settings (deny in, allow out) and uninstalling Vino. That, and being sensible about which websites you visit, should be enough for most purposes.

Do you know the name of the VNC server installed by default in kubuntu 10.04, by any chance?

---

### Post by Irihapeti on 2013-05-07
Possibly Krfb, though I don't know for sure - I've never used Kubuntu.

---

### Post by conquerorodueko on 2013-05-07
You are not interested in physical access protection then the usual most obvious place to look to defend your PC on the internet is the firewall
Then perhaps install apparmor {sudo apt-get install apparmor apparmor-profiles apparmor-utils apparmor-notify} and activate all apparmor profiles as enforce mode

---

### Post by jsvidyad on 2013-05-07
How do I go about activating the apparmor profiles?

---

### Post by CharlesA on 2013-05-07
[http://ubuntuforums.org/showthread.php?t=1008906](http://ubuntuforums.org/showthread.php?t=1008906)

Have fun. :)

---

### Post by Stonecold1995 on 2013-05-08
> **jsvidyad said:**
> What do you mean by surfing habits?
As in, don't download "hawt_pr0n.avi.exe" from sketchy-porn.somesite.ru.

---

### Post by pfeiffep on 2013-05-08
Physical security is also important - consider setting a BIOS password to prevent others from booting using a USB or DVD

---

