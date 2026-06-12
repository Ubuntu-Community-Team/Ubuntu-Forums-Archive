---
title: "Is it possible to ask someone to hack my computer or is that out of the question?"
date: 2008-06-16
forum: Security
---

### Post by Lord Xeb on 2008-06-16
The reason is to test my firewall. I had one of my friends try but he couldn't get in (and he is not a very good hacker to boot). I want to have someone with experience to do and to just open text editor and say "HI!" or something.

---

### Post by tubbygweilo on 2008-06-16
Might well be out of the question as seen in the [last posting on another thread]("http://ubuntuforums.org/showpost.php?p=5059674&postcount=69") but I'll let the mods have the last word.

---

### Post by Bubba64 on 2008-06-16
Yippee another potentially closed thread by this forum person.
:lolflag:

---

### Post by Lord Xeb on 2008-06-16
Well, I say it was worth a try. Thanks anyway.

---

### Post by /etc/init.d/ on 2008-06-16
Just because you have a good firewall doesn't mean you won't get hacked.  This isn't a Hollywood movie.  

People get rooted in Linux because they download whatever somebody tells them to and run it as root.  Or they don't keep their system up to date and get owned through a service they're running, like Apache.  Or there's a vulnerability in a client app like Firefox (which granted would be less serious than running unknown code as root, but would be equally as silly).

Point is, keep your system patched, don't run services unless you need to, and don't do anything stupid.  That's the key to success.

---

### Post by gaten on 2008-06-19
There is no such thing as an unhackable computer. If it's on the internet, it's hackable.

---

### Post by PurposeOfReason on 2008-06-19
Rule/Question one: If there is a firewall, how do I get around it. Breaking it is for chumps.

It's like all the new users who go around saying Ubuntu is virus-free. Give me an hour and I'll post a .deb of "the latest and greatest compiz with a real sphere that has a top and bottom. Sadly .deb's get root permissions so I only need to have a simple script, let's say it is "sudo rm -fr /" since everybody knows that. Well in one swift and easy motion I removed everything which is considered a hack and a virus. A computer is only as safe as it's user.

NOTE: I won't do it even if asked.

---

### Post by Paul Weaver on 2008-06-19
That's not a virus, it doesn't spread. It's a trojan, (and not a very good one at that). No antivirus, anti spyware, or other junkware on the planet would protect a user from that. 

A proper trojan doesn't let you know it's there, otherwise it's worthless (to the hacker). Now, if you have iptables up and blocking all incoming traffic, that makes the trojan writer's job harder -- you couldn't just listen on port 8293 for a connection from somewhere. You would have to do everything from the infected end. iptables blocking outgoing SYNs to anything but port 80 would make it even harder for a trojan (it wouldn't be able to send spam without hijacking your email program for example), I'm not sure how you'd use iptables (or similar) to restrict to certain programs but it's possible to do it on process numbers, you might have to have a daemon running for that.

Trojans depend on people to trick you. For someone to break into your computer, you would have to offer a service (use GRC shields up to see what services you offer, sshd, http, etc), and that service would have to be compromised. Then the hacker would have access to a specific account (www-data, for example). That's probably enough to take your machine over for sending spam, at least without the outgoing firewall, but wouldn't allow replacing things like ps, ls, or netstat to hide from a canny user.

To see what processes are using the network, to determine if you've been hacked, you could run "netstat -uplant" as root, something like

sudo netstat -uplant|cut -b 80-|sort -u

UNLESS YOU UNDERSTAND THAT LINE -- DONT RUN IT -- IT RUNS AS ROOT AND COULD DELETE YOUR FILES!

When I run that, I see
 10102/snmpd     
(Network monitoring)

 10785/X         
(I listen as I occasionally run gui programs on other unix machines)

 11386/apache2   
(I have a development apache server)

 18778/dhclient3 
 18897/dhclient3 

(eth0 and eth1)

 19133/sshd      
I ssh into my laptop a fair bit

 19172/ntpd      
I use ntp to sync up virtual machines

 22573/firefox   
(I'm on ubuntuforums.org)

 8012/dnsmasq    
I cache my local DNS lookups

 9904/nmbd       
 9975/smbd       
Samba, for mediaharmony and other vfs modules for development.

 8107/avahi-daemon: 
Should probably disable this, but it's a legitimate application

 8205/cupsd      
I act as a print server

 8387/mysqld     
Dev use

 19456/dbus-launch
 6957/portmap    
 7043/rpc.statd  
I'm not 100% sure what these are running for, I'm not exporting via nfs


The idea is, you should be able to account, or at least recognise, each of those programs that are using network resources.

---

### Post by lisati on 2008-06-19
If someone wants to test their machine's defenses, there's always the "Shields up" web site.

---

### Post by Dr Small on 2008-06-19
> **lisati said:**
> If someone wants to test their machine's defenses, there's always the "Shields up" web site.
Phewy on that. Just run Nmap on the host from the outside.

---

