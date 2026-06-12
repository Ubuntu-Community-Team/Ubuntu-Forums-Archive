---
title: "Securing Linux beyond generic install"
date: 2008-03-08
forum: Security Discussions
---

### Post by Th3Professor on 2008-03-08
I've got a new set-up, recently installed Ubuntu (Studio), and am concerned about vulnerability to anyone or anything on the internet. My main goal is to 1st get an improved security going then I can learn how to tailor it for me. (I need a quick-fix, temporarily, until I get a grip on the subject.)

I'm using very strong passphrases - very long, very random, all kinds of crazy keys or characters in them - but I know that's not all it takes.

How do I use what they call "NAT"?

(Some have said that NAT's just for changing the published IP, or maybe preventing the private IP from getting out - but I definitely want that.)

What's the difference between NAT and proxy? (How do I use proxy?)

How do I make it so when I open an IRC program, say xchat, that when a user clicks on my "info" my actual IP address doesn't show? (It is currently showing information I don't want out there.)

How do I disable the daemons I don't want running?

(Like httpd, sshd, ftpd, telnetd... so they don't load at boot.)

If I'm going to look through /var/log/ syslog and messages, how do I know what to look for?

What I'd really like is to get some additional (post-install) generic security features working now, so I can feel safe as I gradually learn how to tweak security for me specifically.

Thanks!

---

### Post by pietjanjaap on 2008-03-08
You don't have to do anything, linux is secure.

But you can install guarddog, this is a firewall.
For the rest you have to read all the forum and how to's.


[http://www.debuntu.org/](http://www.debuntu.org/)
[http://www.ubuntu1501.com/](http://www.ubuntu1501.com/)
[http://www.cyberciti.biz/](http://www.cyberciti.biz/)
[http://www.tuxmachines.org/](http://www.tuxmachines.org/)
[http://polishlinux.org/](http://polishlinux.org/)
[http://www.debianadmin.com/](http://www.debianadmin.com/)
[http://www.ubuntugeek.com/](http://www.ubuntugeek.com/)
[http://ubuntu-tutorials.com/](http://ubuntu-tutorials.com/)
[http://www.ubuntux.org/](http://www.ubuntux.org/)
[http://www.howtoforge.com/howtos/linux/ubuntu](http://www.howtoforge.com/howtos/linux/ubuntu)
[http://cs-www.ncsl.nist.gov/tools/tools.htm](http://cs-www.ncsl.nist.gov/tools/tools.htm)
[http://www.ubuntu-nl.org/documentatie/veiligheid/apparmor/](http://www.ubuntu-nl.org/documentatie/veiligheid/apparmor/)
[http://www.ubuntu-nl.org/documentatie/veiligheid/knockd/](http://www.ubuntu-nl.org/documentatie/veiligheid/knockd/)
[http://www.grsecurity.net/](http://www.grsecurity.net/)
[http://ubuntulinuxhelp.com/are-you-keeping-your-ubuntu-linux-pc-secure/](http://ubuntulinuxhelp.com/are-you-keeping-your-ubuntu-linux-pc-secure/)

---

### Post by Th3Professor on 2008-03-08
Thank you for those links - that's a lot of stuff to go through.

Regarding:
> **Th3Professor said:**
> 
How do I use what they call "NAT"?

(Some have said that NAT's just for changing the published IP, or maybe preventing the private IP from getting out - but I definitely want that.)

What's the difference between NAT and proxy? (How do I use proxy?)


Is NAT usually automatically incorporated into (separate hardware) routers?

I have a wireless router, though in the past I have disabled the wireless features (I hear both WEP and WPA aren't as strong as they should be, though I think there are new/stronger options (on newer devices)). Anyway, the router auto reassigns IP, right? I'm guessing NAT is "network address translation", which a guess would say it literally does just that. So if I have a router my computer would be 192.168.x.x instead of the public address? Though, in that case, wouldn't the public address still show through the actual router or at the very least through the actual cable modem?

Before I put my separate router device back into the equation, is there a way I can incorporate NAT into just my computer (being plugged directly into the cable modem)?

Or, if not with NAT, should I use proxy settings to achieve that?

Is there an explanation of NAT and/or proxy on the Ubuntu forums?

The normal Ubuntu (Studio) install - does it actually come with those daemons automatically running? I'm hoping not. (Like httpd, sshd, ftpd, telnetd, etc.)

Thanks again!

---

### Post by p_quarles on 2008-03-08
NAT = Network address translation. If configured correctly, NAT can be used for security purposes for *inbound* connections, but has absolutely nothing to do with security for outbound connections. 

$ubuntu by default is not listening for any connections from foreign hosts. It has several daemons listening to localhost, but they are completely unaware of requests coming from outside of the computer on which they are running.

---

### Post by bruce2000 on 2008-03-08
> **Th3Professor said:**
> 
How do I make it so when I open an IRC program, say xchat, that when a user clicks on my "info" my actual IP address doesn't show? (It is currently showing information I don't want out there.)
Thanks!

To hide your whois info? The methods vary depending on your IRC network, and not all of them support it. I'm familiar with Undernet and logging into X to hide my IP address, but for other networks give their web page a try or a help channel.

---

### Post by Th3Professor on 2008-03-10
...probably going to use freenode irc - have they gotta work around for hidden or alternate IP?

---

### Post by Lysander10 on 2008-03-12
If you want to hide your identity online, use Tor. You should find everything you need at this address: [http://www.torproject.org/](http://www.torproject.org/)

---

### Post by Th3Professor on 2008-03-12
> **Lysander10 said:**
> If you want to hide your identity online, use Tor. You should find everything you need at this address: [http://www.torproject.org/](http://www.torproject.org/)

Ah yeah, thank you. I just installed tor from Ubuntu's package manager, it was already in a repo. It appears, though, to be a console-only app.

I'm familiar with tor for use with web browsers, though to use it for the entire internet connection, if possible, would be great.

---

### Post by Th3Professor on 2008-05-10
Okay, I'm only reviving this thread because for some ridiculous and inane reason I am unable to create a NEW thread... and that's only in this specific forum. I have no idea why.


Anyway...

Regarding "tor"...

It was mentioned that "to hide your identity online, use Tor", aka:
[http://www.torproject.org/](http://www.torproject.org/)

I've tried the tor in Ubuntu's repo, though it seems limited.

It also seems to be console only, which is okay, though some input on using the app in general would be helpful, and greatly appreciated, if possible.

I've only used tor via web browsers in the past - not for the *entire* internet connection. Is that possible (via entire internet connection)?

---

