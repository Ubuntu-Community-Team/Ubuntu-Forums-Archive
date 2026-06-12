---
title: "Will Linux Server Botnet be a threat to Linux Desktops?"
date: 2009-09-14
forum: Security
---

### Post by Brian_Newbie on 2009-09-14
I'm relatively new to linux (I use Ubuntu Jaunty) and especially to how best to secure my Ubuntu Desktop against malware threats.

While I understand that Linux is more resilient to intrusion and a much safer operating system than MS Windows - especially for those not running their computers as root - I do have one question about an article I read today at the following url:

[http://www.heise.de/english/newsticker/news/145292](http://www.heise.de/english/newsticker/news/145292)

Is this Linux server botnet a threat to Linux desktops as well as Windows PCs?

And if so, is there any actions Linux users can take to prevent being exposed to the malware in the above link?

Thanks Much

Brian

P.S. I hope I posted this in the right forum.

---

### Post by Agent ME on 2009-09-14
Most Unix-type servers are hacked by brute forcing the password to the FTP, telnet, or SSH services. As Desktop computers rarely have any of these services installed, they are not at risk at all to this type of attack.

Desktop users who have SSH or other server type services installed are just as vulnerable as webservers that have the same service installed. That is, if you have a weak password on an admin account (single dictionary word, same as username, etc), it is not unexpected to get hacked.
(If there's a weak password on a standard non-admin user account, then an attacker can get in and launch attacks onto other computers from the infected user account, but he won't have full access to the system, and it would be very easy to kick the hacker off.)

---

### Post by ApEkV2 on 2009-09-14
As long as you leave ports closed and keep your distribution updated, I couldn't see an attacker getting the upper hand. 
(unless like Agent ME said about bruteforcing the ssh password, but most ppl don't have ssh)


But this leaves a burning question, just how safe is linux?
I've been wanting to see how secure an insecure setup of linux is.  xD

To do this I'm going to setup an old comp with xubuntu, install and setup
apache, leave random ports open, set the default user to root, and finally put the computer in the router's DMZ.

And to top it off, I'll be torrenting 24/7, and IRC as well.

Monitoring the many different log files, if something significant doesn't happen within 72 hours I'll be impressed.
I'll probably start a thread once I get the setup going.

[color=red] EDIT: Got the computer up and running (10 year old hard drives suck): Fin [/color]

---

### Post by rookcifer on 2009-09-15
> **Brian_Newbie said:**
> I'm relatively new to linux (I use Ubuntu Jaunty) and especially to how best to secure my Ubuntu Desktop against malware threats.

While I understand that Linux is more resilient to intrusion and a much safer operating system than MS Windows - especially for those not running their computers as root - I do have one question about an article I read today at the following url:

[http://www.heise.de/english/newsticker/news/145292](http://www.heise.de/english/newsticker/news/145292)

Is this Linux server botnet a threat to Linux desktops as well as Windows PCs?

And if so, is there any actions Linux users can take to prevent being exposed to the malware in the above link?

Thanks Much

Brian

P.S. I hope I posted this in the right forum.

This story is misleading.  There is no Linux "botweb."  What you have here is one security researcher (from Russia nontheless) who has discovered a host of compromised Linux web servers.  What the news articles usually don't emphasize, however, is that these boxes were almost always cracked via weak passwords or poor settings.  This has **nothing** to do with any potential Linux malware.

[Here]("http://blogs.zdnet.com/hardware/?p=5457") is a quick explanation worth reading.

---

### Post by Brian_Newbie on 2009-09-15
Thanks everyone for your replies. It looks like I'm pretty safe as I don't run servers, ssh etc and have a strong password. I also don't run as root either.

It'll be interesting to see the results of your experiment ApEkV2. If anything significant happens, definitely post a new thread about it.

It definitely looks like I made a good decision switching from Windows to Linux rookcifer. The last time I had any type of malware was on that old Windows box.

---

### Post by __p1n__ on 2009-09-15
> **ApEkV2 said:**
> 
To do this I'm going to setup an old comp with xubuntu, install and setup
apache, leave random ports open, set the default user to root, and finally put the computer in the router's DMZ.

And to top it off, I'll be streaming ustream 24/7, and IRC as well.

Monitoring the many different log files, if something significant doesn't happen within 72 hours I'll be impressed.
I'll probably start a thread once I get the setup going.


Send me a pm with the external ip address of that server and I'll help you out with that.

---

### Post by Chayak on 2009-09-20
> **ApEkV2 said:**
> As long as you leave ports closed and keep your distribution updated, I couldn't see an attacker getting the upper hand. 
(unless like Agent ME said about bruteforcing the ssh password, but most ppl don't have ssh)


But this leaves a burning question, just how safe is linux?
I've been wanting to see how secure an insecure setup of linux is.  xD

To do this I'm going to setup an old comp with xubuntu, install and setup
apache, leave random ports open, set the default user to root, and finally put the computer in the router's DMZ.

And to top it off, I'll be torrenting 24/7, and IRC as well.

Monitoring the many different log files, if something significant doesn't happen within 72 hours I'll be impressed.
I'll probably start a thread once I get the setup going.

[color=red] EDIT: Got the computer up and running (10 year old hard drives suck): Am now setting it up

What your talking about doing is setting up what's called a honeypot.  I've used them a lot and set up training networks for red team/blue team events.

The biggest thing you need to do for that is set it up in a DMZ and have it dumping all of it's logs to a syslog server.  Though most attacks I've seen are on a script kiddie level or are automated bots.  There is occasionally someone who knows what they're doing and will clean out the log files and touch them back to match the last date entry in the log.  They'll also set up backdoors in a way that's very difficult to detect.

The standard way for honeypots is to set them up in virtual machines that have a snapshot taken of a known clean state.  That way when you're done you can reset it to a known clean state.

---

### Post by Haakon_KL on 2009-09-21
> **ApEkV2 said:**
> But this leaves a burning question, just how safe is linux?
Essentially as secure as it's dumbest admin.

Yeah, I know, that sounds a little condescending.

But it is not meant like that at all.

You see, if you're smart, then the linux box is safe.

Don't use root accounts unless necessary (when doing a fresh install, having root is rather nice, since you'll have a lot less password typing then you'd otherwise have, for instance. But if you just want to hack to line in the grub.lst file, just sudo it.) and use a strong password, and you'll be very much set.
Especially since you likely don't have SSH services running.

But, if you use a weak root password, and/or autologon as root :(, you're not any more secure than on Vista.

---

