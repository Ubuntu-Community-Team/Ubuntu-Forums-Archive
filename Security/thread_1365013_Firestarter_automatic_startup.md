---
title: "Firestarter automatic startup"
date: 2009-12-26
forum: Security
---

### Post by gameguy on 2009-12-26
I need to get firestarter working, but before that, I need to get it working automatically on bootup, so I need to:

1. Have it as an icon in a tray without the program showing up on the panel like normal programs do.

2. I need to get it working on startup. I am using 9.10's startup programs. I tried as command "sudo /usr/sbin/firestarter" and it comes up with an error because the network connection isn't initialised, before starting, and I tried "sleep 10; sudo /usr/sbin/firestarter", and then it never starts at all. How do I set priorities, not necessarily in that program, though.

---

### Post by lovinglinux on 2009-12-26
You don't need to start Firestarter on boot to be protected. It is just a firewall manager, which basically allows you to create rules for the real firewall, which is loaded on boot and runs all the time. So once you create the rules, just close Firestarter and forget about it.

Firestarter is not even recommended anymore and running it all the time could be a security risk, due to administrative privileges required to run it. Most recent Windows converts like Firestarter because you can monitor blocked connections, but that is just a waste of time. Besides, running a firewall on your machine is probably not even necessary if you don't have a server running and want to limit the server traffic to specific machines.

You don't need a firewall if:

[list][*] you have a router with firewall capabilities
[*] you don't have any server installed and running[/list]


Anyway, the recommended firewall manager these days is ufw, which is installed by default. If you want a graphical interface, then install gufw.

You need to purge Firestarter before running gufw.

```
sudo apt-get purge firestarter
sudo iptables -F
sudo iptables -X
sudo apt-get install gufw
```

Also see [Ubuntu Security](http://ubuntuforums.org/showthread.php?t=765421).

---

### Post by gameguy on 2009-12-26
> **lovinglinux said:**
> Also see [Ubuntu Security]("http://ubuntuforums.org/showthread.php?t=765421").
Looked at it earlier today.
I have a modem with a hardware firewall at dad's house, but at mum's nothing.
And do you know of a free antivirus that updates itself, scans files as you open them, and doesn't take much speed off your system. And before you ask, I need an antivirus, especially since the computer is running windows in dual boot.
BTW is the firewall (or the antivirus if you can think of one) available on windows 7?

---

### Post by lovinglinux on 2009-12-26
> **gameguy said:**
> And do you know of a free antivirus that updates itself, scans files as you open them, and doesn't take much speed off your system. And before you ask, I need an antivirus, especially since the computer is running windows in dual boot.

I like BitDefender. It has nautilus integration and a drop box.

> **gameguy said:**
> ABTW is the firewall (or the antivirus if you can think of one) available on windows 7?

For Windows 7 I highly recommend Comodo Firewall. The latest versions also comes with an anti-virus. It also has HIPS. Is a full featured free security application.

---

### Post by gameguy on 2009-12-26
Sorry, the keyword was "free". I know there's a trial, but I'll go with ESET otherwise.

---

### Post by lovinglinux on 2009-12-26
> **gameguy said:**
> Sorry, the keyword was "free". I know there's a trial, but I'll go with ESET otherwise.

They are both free.

---

### Post by gameguy on 2009-12-27
Sorry, my mistake. I didn't see the free version thing. I just saw the boxed product and the bit about money so didn't look any further.

---

