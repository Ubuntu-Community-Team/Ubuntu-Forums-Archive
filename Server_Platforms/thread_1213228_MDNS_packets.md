---
title: "MDNS packets?"
date: 2009-07-14
forum: Server Platforms
---

### Post by afowler on 2009-07-14
Hello,

I just installed Ubuntu Server with the defaults.

Looking at a wireshark trace, i see the server sending out "MDNS" packets.

What are these, and why would I want them. (I intend the server to be a basic public facing web and mysql server)


If they are not needed, how do i turn them off?

Thank you,
:)

---

### Post by capscrew on 2009-07-14
See [_here_]("http://www.multicastdns.org/") for more information.  This is part of the Avahi (Zero Conf).

If indeed you have Avahi running, Then I'll bet you installed the gnome desktop too.  It is part of that package.  Avahi is not part of an Ubuntu server install that I know of.

---

### Post by Vegan on 2009-07-14
Is that program console friendly?

---

### Post by capscrew on 2009-07-14
> **Vegan said:**
> Is that program console friendly?

What program are you referring to?  What does *console friendly* mean?

---

### Post by spynappels on 2009-07-15
I guess *console friendly* means does it need a GUI to run or will it work ok in CLI?

---

### Post by capscrew on 2009-07-15
> **spynappels said:**
> I guess *console friendly* means does it need a GUI to run or will it work ok in CLI?

Avahi is a daemon and runs in the background.  The user does not directly interact with it at all.

---

### Post by afowler on 2009-07-17
> **capscrew said:**
> See [_here_]("http://www.multicastdns.org/") for more information.  This is part of the Avahi (Zero Conf).

If indeed you have Avahi running, Then I'll bet you installed the gnome desktop too.  It is part of that package.  Avahi is not part of an Ubuntu server install that I know of.

Thank you for the help.   I certainly did **not** install Gnome.    I used all the defaults during the server installation.

I then installed apache2 and ebox.  I then removed ebox.

Can I remove "Avahi", and if so how?

Thank you,
:)

---

### Post by capscrew on 2009-07-17
I would check my hypothesis first.  Try this from the terminal:```
ps -ef|grep avahi
```

If the daemon is running it will look like this```
>ps -ef |grep avahi
avahi     4601     1  0 08:17 ?        00:00:00 avahi-daemon: running [malibu.local]
avahi     4602  4601  0 08:17 ?        00:00:00 avahi-daemon: chroot helper

```

To remove it you can run this from the command line:```
sudo apt-get remove avahi-daemon
```

I tried it on my desktop (test only (using the -s switch)) and it showed this:```
>sudo apt-get -s remove avahi-daemon
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  avahi-daemon libnss-mdns ubuntu-desktop
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
Remv ubuntu-desktop [1.102]
Remv libnss-mdns [0.10-3ubuntu2]
Remv avahi-daemon [0.6.22-2ubuntu4.1]

```

Notice that it removes the ubuntu-desktop also.  If you wish you can use *purge* instead of *remove* in the above command.

I wonder if eBox added it?

---

### Post by afowler on 2009-07-17
Yep, it's running....

```

avahi     2348     1  0 Jul14 ?        00:00:00 avahi-daemon: running [UbuntuServer.local]
avahi     2349  2348  0 Jul14 ?        00:00:00 avahi-daemon: chroot helper

```


Here is the output from apt-get -s:
```

$ sudo apt-get -s remove avahi-daemon
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  avahi-daemon avahi-utils libnss-mdns
0 upgraded, 0 newly installed, 3 to remove and 2 not upgraded.
Remv libnss-mdns [0.10-3ubuntu2]
Remv avahi-utils [0.6.23-4ubuntu4]
Remv avahi-daemon [0.6.23-4ubuntu4]


```


Before I remove it, are there any logs to figure out how this got installed?

---

### Post by capscrew on 2009-07-17
> **afowler said:**
> Yep, it's running....

Before I remove it, are there any logs to figure out how this got installed?

Just the usual logs i.e.  They are located at /var/log/  I would look at messages and syslog.

This [_[COLOR="DarkSlateGray"]forum thread[/COLOR]_]("https://lists.ubuntu.com/archives/ubuntu-server/2007-November/001000.html") might be helpful to you.

It brings up something I never thought of; CUPS.  I don't print from my server.  I wonder if eBox may set up anticipating a need for printing.  I do see that there is no reference to Gnome or ubuntu-desktop.  :-)

---

### Post by afowler on 2009-07-17
> **capscrew said:**
> Just the usual logs i.e.  They are located at /var/log/  I would look at messages and syslog.

This [_[COLOR="DarkSlateGray"]forum thread[/COLOR]_]("https://lists.ubuntu.com/archives/ubuntu-server/2007-November/001000.html") might be helpful to you.


Ok, i will take a look.. Thank you,  :)

---

