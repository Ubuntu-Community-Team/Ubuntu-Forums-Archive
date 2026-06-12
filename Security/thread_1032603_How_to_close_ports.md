---
title: "How to close ports?"
date: 2009-01-06
forum: Security
---

### Post by LinuxKnight89 on 2009-01-06
I would like to know how hard it would be to close all unnecessary ports. I would like to be able to manually open ports that I need. Please post any necessary ports to computer operation.

---

### Post by HermanAB on 2009-01-06
Easy - install ufw and run it once.

Cheers,

Herman

---

### Post by cdenley on 2009-01-06
> **LinuxKnight89 said:**
> I would like to know how hard it would be to close all unnecessary ports. I would like to be able to manually open ports that I need. Please post any necessary ports to computer operation.

You don't need any open TCP ports for typical computer usage. To close unnecessary TCP ports, don't install servers.
```

sudo netstat -tulnp

```
By default, avahi-daemon listens on a UDP port. I don't think it's necessary, but I don't think it's a security risk, either.

If you think you might install servers by accident, use a firewall.
```

sudo apt-get install gufw
gksudo gufw

```

---

### Post by bodhi.zazen on 2009-01-06
> **LinuxKnight89 said:**
> I would like to know how hard it would be to close all unnecessary ports. I would like to be able to manually open ports that I need. Please post any necessary ports to computer operation.

Well, Linux is not windows. With a default installation there are no open ports.

You "open" a port by installing a srver (FTP, HTTP, SSH, etc).

In terms of "closing" ports, do you use a router ? If so, your ports are not accessable unless you forward them.

If you wish to restrict access you will need to configure your firewall (iptables). There are many applications to do this, UFW is installed by default.

```
sudo ufw default deny
sudo ufw enable
```

[https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw](https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw)

See also 

[Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812")

---

### Post by LinuxKnight89 on 2009-01-06
Thanks for all the posts.

Does anybody know of any good distros that come almost completely bare. Something that doesnt have anything on it that would require a port to be open. I mean obviously they would need to be opened at some point but I would like to install only specifics thing that use specific ports that I can keep track of.

I know this seems wierd but a friend of mine thinks he is a really good hacker of some sort and says no matter what I do he will be able to get in. He does consulting for corportations. So I figure the less I have on my computer for him to exploit the better. 

The agreement is that I need to have an IM, Email, Browser, Ftp, Telnet clients installed. But there was no agreement for me to close all other ports but those and then carefully monitor those ports.

Any good firewalls, anti-spyware, and anti-virus would help as well and anything else anyone can think of.

I use a cable modem connected directly to my nic. I dont have a static ip or anything along those lines either.

Thanks for any help.

---

### Post by bodhi.zazen on 2009-01-06
Any Linux distro will do

If you want to make his life difficult , install Fedora and enable SELinux.

The weak links in your listing are ftp and telnet. Telnet especially is almost like asking you to leave the keys in the ignition.

Tell your friend no on telnet, but that you are willing to install ssh. Then look here to secure it :

[https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH)

If you need a ftp server at least go with a more secure one such as proftp or vsftp (or better scp over your ssh server).

Your friend does not sound like a leet h3xor, s/he is asking you to open up your system and that is different then breaking in. You should not install any server or application you do not use. If you use telnet, convert to ssh. If you use ftp, convert to a more secure ftp server or scp.

I am a leet car thief. Please leave the keys in the Porsche, write your PIN on your bank card, and leave the doors open and I will show you how leet I really am :)

---

### Post by brandon88tube on 2009-01-06
Lol, I found that funny. Also what about ftps? I'm not good with this stuff, but I think I've seen that pop up before. Something like how https is to http.

---

### Post by LinuxKnight89 on 2009-01-07
I told him no telnet and ftp. He said that those were more of an inside joke kind of thing and that they were not necessary. To tell you the truth this guy is not much of a friend, and seems to get cockier every time we speak. I really want to stick it to this guy and keep him out of my com. Someone please help me shut this guy up step by step. This is also a learning exp. for me so tutorials would be nice. I have officially moved from linux noob to script kiddy in the last year so I am comfortable with CLI.

---

### Post by bodhi.zazen on 2009-01-07
> **LinuxKnight89 said:**
> I told him no telnet and ftp. He said that those were more of an inside joke kind of thing and that they were not necessary. To tell you the truth this guy is not much of a friend, and seems to get cockier every time we speak. I really want to stick it to this guy and keep him out of my com. Someone please help me shut this guy up step by step. This is also a learning exp. for me so tutorials would be nice. I have officially moved from linux noob to script kiddy in the last year so I am comfortable with CLI.

:lolflag:

Well you are giving me the impression your "friend" is more bark then bite.

Although almost any Linux distro will do, if I were you I would install Fedora and use SELinux. Then install snort and ossec. Finally ban his IP address (with iptables) if he does anything "funny" (watch snort and your logs).

Do not install any services or applications you do not use. Start with a minimal installation and build up. If you do not use a FTP server, for example, do not install one. If you do look at how to secure it. Same with http, ssh, samba, nfs, etc ...

Get a router and do not forward ports.

It is installing server applications that opens ports.

Security is a process not an absolute. The only secure computer is one that is powered down, disconnected from the internet, and locked away in a vault.

With that said the only real protection you have is education and monitoring of your system. There is no turn key security solution and although Linux is more secure then Windows it is not a replacement for your own education.

Start with the security stickies at the top of this page.

---

### Post by brandon88tube on 2009-01-07
You recommend snort, but what if he has wireless? Wouldn't he need a wireless version? I also believe AirSnort is way out of date and they recommend you use aircrack-ng or something.

---

### Post by pdtpatrick on 2009-01-07
This is probably the funniest post ive seen so far.. you are on a mission to prove this fella wrong :) 

Like bodhi mentioned.. selinux is a pain, also just monitor your logs and watch for traffic, if you see an unwanted IP then block it. Also if you are going to use an IM, make sure the traffic is encrypted 

I think that fella is just yanking your chain but with a few settings you can make it very very tough for him to even get close to doing anything but it was take a few hardwork and research on your part.

---

### Post by pdtpatrick on 2009-01-07
> **brandon88tube said:**
> You recommend snort, but what if he has wireless? Wouldn't he need a wireless version? I also believe AirSnort is way out of date and they recommend you use aircrack-ng or something.

The person has to be around your area to try wirelessly hacking your computer which i dont think is the case here.. more than likely its from a remote location. 
BTW snort is IDS (Intrusion Detection System)

---

### Post by bodhi.zazen on 2009-01-07
> **brandon88tube said:**
> You recommend snort, but what if he has wireless? Wouldn't he need a wireless version? I also believe AirSnort is way out of date and they recommend you use aircrack-ng or something.

You raise god points, but wireless is a whole new ball of wax and aircrack-ng is the tip of the iceberg.

My first piece of advice it to avoid wireless if at all possible.

If you must, then again learn how to lock it down. Use encryption (WPA not WEP), Limit MAC access, secure (change from the default) you router password, etc.

aircrack-ng alone would be insufficient for the task at hand as you need to do more then snort.

---

### Post by ooobooontooo on 2009-01-21
@bodhi.zazen & open to others
I have a question at a comment that you made 2 weeks ago. You said:
> The weak links in your listing are ftp and telnet. Telnet especially is almost like asking you to leave the keys in the ignition.
However he asks for:
> The agreement is that I need to have an IM, Email, Browser, Ftp, Telnet **clients** installed.
Do the client sides also offer a risk? Wouldn't you have to be running telnetd and ftpd to be worrying? Or were you assuming he meant the sever side stuff? Thanks in advance.

EDIT: Of course I'm assuming he's never going to use those clients.

---

### Post by cdenley on 2009-01-21
Simply having the clients shouldn't be a problem. I think ubuntu has FTP and telnet clients installed by default. They can't be exploited unless they're actually running. Even then, I think it would require a specific action for you to take and an unpatched security vulnerability that the attacker knows how to exploit.

---

### Post by bodhi.zazen on 2009-01-21
+1 cdenley

The issue is someone claiming they are a leet hxor and can crack any system so long as xy and z is installed obviously has an exploit up his or her sleeve. Not the planned crack may (or may not) succeed but I see no point to comply with the request to install such requests.

It is like saying I can steel any car if you give me the keys, and amounts to nothing short of social engineering.

---

### Post by ooobooontooo on 2009-01-21
ok good. Thanks that's what I needed to know.

---

### Post by yamazaki1 on 2009-01-21
LinuxKnight, when you're done securing your system I would also highly recommend that you take care what web links / IM links your friend sends you from here out.  There are tricks that can be done with Javascript in 0% iframes that could allow him to brute force his way into any kind of browser-based app manager you're running locally (say, a browser-based app that lets you configure firewalls).

Of course, based on his initial set of requirements, he's likely not "leet" enough to do that.

---

