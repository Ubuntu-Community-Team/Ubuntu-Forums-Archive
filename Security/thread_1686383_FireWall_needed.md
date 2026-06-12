---
title: "FireWall needed?"
date: 2011-02-12
forum: Security
---

### Post by debd on 2011-02-12
since I learned quite a bit how linux's design and process handling works I've left bothering about AVs.
but still not sure if I need a firewall.
do any of you have one installed?
also what does Snort really do? does it only monitors the in/out bound traffic or can also block malicious packets?

---

### Post by DanneStrat on 2011-02-12
> **debd said:**
> since I learned quite a bit how linux's design and process handling works I've left bothering about AVs.
but still not sure if I need a firewall.
do any of you have one installed?
also what does Snort really do? does it only monitors the in/out bound traffic or can also block malicious packets?

It depends on your network setup.

For example:

I'm connected to a router with a firewall

and I don't feel the need to have a software

firewall. One reason to have one is

if you want to control outbound connections,

but since linux is pretty secure in terms of getting malware

(when configured correctly), I don't think you need it.

I read somewhere that ubuntu comes with no open ports,

but if you're connected to the internet directly

without firewall I recommend you use "gufw" which is

a gui for "iptables" to give you better control

over your open ports. 

To your question about snort:

"Snort can perform protocol analysis and content searching/matching. It can be used to detect a variety of attacks and probes, such as buffer overflows, stealth port scans, CGI attacks, SMB probes, OS fingerprinting attempts, and much more. It uses a flexible rules language to describe traffic that it should collect or pass, as well as a detection engine that utilizes a modular plug-in architecture. Snort has a real-time alerting capability as well, incorporating alerting mechanisms for syslog, a user specified file, a UNIX socket, or WinPopup messages to Windows clients. Snort has three primary uses: a straight packet sniffer like tcpdump, a packet logger (useful for network traffic debugging, etc), or a full-blown network intrusion prevention system."


If you have any more questions feel free to ask.

---

### Post by HermanAB on 2011-02-12
Howdy,

Linux pretty much *is* a firewall.  So you don't need to add anything to the default Ubuntu setup.

If you want to see what is going on on the network, install Wireshark or tcpdump and ntop and have a looksee.

On my WWW serrvers, I only install one iptables firewall rule, a general purpose new connection rate limiter.  It suppresses most all kinds of DOS and brute force attacks.
```

# General new connection rate limiting for DOS and Brute Force protection
iptables -I INPUT -p TCP -m state --state NEW -m limit --limit 30/minute --limit-burst 5 -j ACCEPT
```

---

### Post by Hobbyist on 2011-02-12
Please correct me if I'm mistaken but doesn't the Linux kernel have a  firewall coded into it? I thought I read that in a book I recently  finished.

---

### Post by DanneStrat on 2011-02-12
> **Hobbyist said:**
> Please correct me if I'm mistaken but doesn't the Linux kernel have a  firewall coded into it? I thought I read that in a book I recently  finished.

Yes you're right, it comes with "iptables".

---

### Post by debd on 2011-02-13
can I view the findings of iptable in realtime through a terminal command?

if so   what's that?

---

### Post by debd on 2011-02-13
```
iptables -I INPUT -p TCP -m state --state NEW -m limit --limit 30/minute --limit-burst 5 -j ACCEPT
```

this should do well for any desktop too I think ..or should I use a lower conn. rate? 

.. thanks for all the replies you made folks!

---

### Post by DanneStrat on 2011-02-13
> **debd said:**
> can I view the findings of iptable in realtime through a terminal command?

if so   what's that?

I don't know exactly what you mean.

If you want to list the current

NAT rules you can try this in a terminal:

```
sudo iptables -t nat -n -L
```

Iptables manpage for more info:

[http://linux.die.net/man/8/iptables](http://linux.die.net/man/8/iptables)

---

### Post by linuxsyst on 2011-02-13
> sudo apt-get install firestarter
After the installation is finished, you can find the administration GUI at System \ Administration \ Firestarter

When you launch the GUI for the first time, it will take you through a setup wizard

Click forward, and you will be able to select the network device. If you are using DHCP for your machine, make sure you select that checkbox here:
IP adress assigned to DHCP.

Click Forward, and then Forward again. You will see the final screen of the wizard

Click the save button and you will see the normal GUI screen

This GUI is accessible from the tray icon on top right 
cheers.

---

### Post by debd on 2011-02-13
> I don't know exactly what you mean.

I actually meant to see the UFW log from the terminal :)

I've got myself the gufw.

thanks.

...waiting a rply from HermanAB.

---

### Post by Hobbyist on 2011-02-13
I thought Firestarter was no longer maintained. If that's true would it be a potential security threat?

---

### Post by cariboo on 2011-02-13
Firestarter isn't maintained any more, but if you only use the gui to set firewall rules, and then shut it down, firestarter still runs in the background. The only time there could be a problem is is you run the gui as root all the time to monitor firewall connections.

---

### Post by perspectoff on 2011-02-13
iptables is "off" by default. All ports are unblocked by default. The utility is there, but you have to configure it to block the ports.

The question is whether you trust the applications you run not to have spyware in them.

There is never a guarantee that one day you won't install some app that opens a backchannel to download data from your disk to some central location. That's the definition of spyware.

Linux IS IN NO WAY PROTECTED FROM TROJANS AND SPYWARE!

If you happen to download and run an app that has the stuff coded into it, all the advice on these forums won't help you.

A firewall serves to minimize the ability of spyware to communicate through backchannels without your knowledge.

Snort and other traffic monitoring programs give you a handle on the traffic going in and out of your computer (but, of course, there is a steep learning curve).

You know, there are people who will tell you it's ok to have sex without condoms, too. Don't believe it. Be protected.

---

### Post by perspectoff on 2011-02-13
> **cariboo907 said:**
> Firestarter isn't maintained any more, but if you only use the gui to set firewall rules, and then shut it down, firestarter still runs in the background. The only time there could be a problem is is you run the gui as root all the time to monitor firewall connections.

Firestarter may not be maintained, but it works fine for me. UFW and GUFW has always been a PITA for me. God forbid you try to take the advice of someone who tells you to write your own iptables rules by hand via the command line. That's for networking professionals.

Also, I don't think Firestarter "runs" in the background. Its only purpose, AFAIK, is to change the iptables rules. It has the appearance of running (like a Windows service), but it isn't actually doing anything unless you change settings.

Because iptables is the real firewall, not Firestarter, I think it relatively unimportant that Firestarter is not "maintained." It actually performs a very simple task. It doesn't work by heuristics or applications monitoring the way some Windows firewalls work, and therefore doesn't need the same type of "updating."

---

### Post by cariboo on 2011-02-13
Firestarter does in in the background, check you firewall rules using:

```
sudo iptables -L
```

Then type:

```
ps ax | grep firestarter
```

to find the pid, kill firestarter:

```
sudo kill <pid>
```

and check your firewall rules again.

---

### Post by handy on 2011-02-13
> **perspectoff said:**
> iptables is "off" by default. All ports are unblocked by default. The utility is there, but you have to configure it to block the ports. 

Ubuntu ships with NO open ports. [edit:] Public ports. /edit

> **perspectoff said:**
> 
The question is whether you trust the applications you run not to have spyware in them.

There is never a guarantee that one day you won't install some app that opens a backchannel to download data from your disk to some central location. That's the definition of spyware. 

One of the great benefits of OSS is that other people get to look at, learn from & use the code. If someone writes insecure code it would be found & it would be fixed fast. Apart from that, there are many extremely knowledgeable users both casual & professional who are extremely interested in network traffic; they monitor & evaluate.

> **perspectoff said:**
> 
Linux IS IN NO WAY PROTECTED FROM TROJANS AND SPYWARE!

If you happen to download and run an app that has the stuff coded into it, all the advice on these forums won't help you.

<snip>

You know, there are people who will tell you it's ok to have sex without condoms, too. Don't believe it. Be protected.

Please trot out the long list of security problems that are striking other users (& thankfully have managed to miss my machines over the last 5+ years)?

There is no talk of the distros being targeted with these problems except by people coming over from Windows who are used to being a target or trolls.

If the distros were genuinely being threatened then there would be lots of talk & stickies in forums such as this with a list of the non-OSS trojans & spyware that effect Linux distros & how to deal with them. 

These problems would have to be non-OSS as if they were open-source then they would not exist.


New Ubuntu users should read the link below, as this informative page (great site actually) will tell them all they need to know re. Desktop Ubuntu security. 

Take the page at its word as too many people talk about security & other things on the forum & don't really know what they are talking about, which makes it particularly difficult for new users who are trying to deal with the initial steep Linux learning curve:

[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

---

### Post by debd on 2011-02-14
> Ubuntu ships with NO open ports.
..dont get what you mean.

.. when you connect to the internet you gotta have appropriate ports open,right?

also I want to know , when I'm running a torrent client, my computer pretty much acts like a ftp server...isn't it? Especially when I seed?

---

### Post by handy on 2011-02-14
Read the page I linked to, that should settle things down in your mind. :)

& I edited that line & added "public ports" some time ago. ;)

---

### Post by debd on 2011-02-14
awryt....m gonna mark it solved now.

---

