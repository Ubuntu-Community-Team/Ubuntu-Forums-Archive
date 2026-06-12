---
title: "Firewall problem"
date: 2008-08-15
forum: Security
---

### Post by donniezazen on 2008-08-15
I have read few post regarding firewall's futility in Ubuntu. As i am newbie can someone explain them to me in simple language.

What happens to firewall by default. If i run firestarter then do i have to start it every time i start my laptop.

Am i risking my laptop if i stop the firewall. I do this to get more speed in my torrent.

Thank you.

---

### Post by hyper_ch on 2008-08-15
(1) firestarter is no firewall
(2) firestarter just add stuff to iptables
(3) iptables is the "firewall"
(4) iptables runs all the time
(5) by installing and running firestarter you have already modified iptables so that all ports are blocked now

---

### Post by donniezazen on 2008-08-15
[QUOTE=hyper_ch;5593115
(5) by installing and running firestarter you have already modified iptables so that all ports are blocked now[/QUOTE]

iptables runs all the time but ports are open and now after installing firestarter ports are blocked. So what happens when i unistall firestarter. How to open all the ports.

---

### Post by Oldsoldier2003 on 2008-08-15
> **soham_1207 said:**
> iptables runs all the time but ports are open and now after installing firestarter ports are blocked. So what happens when i unistall firestarter. How to open all the ports.

You would need to modify your rules manually. 
see:
[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

---

### Post by Vivaldi Gloria on 2008-08-15
Stay away from firestarter. Use ufw. Read my posts here:

[http://ubuntuforums.org/showthread.php?t=889611](http://ubuntuforums.org/showthread.php?t=889611)

---

### Post by donniezazen on 2008-08-16
Thank You all of you

---

### Post by pedja_portugalac on 2008-08-18
> **Vivaldi Gloria said:**
> Stay away from firestarter. Use ufw. Read my posts here:

[http://ubuntuforums.org/showthread.php?t=889611](http://ubuntuforums.org/showthread.php?t=889611)

I use firestarter to configure my firewall from the first day I have installed Ubuntu and I never had a single problem. It is definitely the easiest way to configure firewall for both new and advanced users. Also, there's a lot more tutorials and howtos about firestarter. UFW is a new Ubuntu project and it already has some bugs, I saw it in security updates! That said, I suggest use of firestarter for the beginners and intermediate users! 

Ones firestarter installed and configured by default it will block all incoming traffic and allow all outgoing. If you are like me you'll want to change outgoing traffic into restricted by default and allow just minimum needed services and ports when you really need it. For example you'll need to allow HTTP (port 80) to surf on the internet. You'll also enable ICMP filtering and block traffic from reserved adrresses on public interfaces. Ones all that done, you don't need to open firestarter unless for troubleshooting. Its firewall (iptables) configuration will start every time you start Ubuntu. 
PS. As firestarter is iptables configuration GUI only for ipv4 protocol, learn how to completely disable ipv6 protocol, both from the kernel and from firefox, because currently you don't need that implementation.

---

