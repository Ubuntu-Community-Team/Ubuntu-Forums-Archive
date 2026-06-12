---
title: "Most important security vulnerabilities"
date: 2009-06-05
forum: Security
---

### Post by wiso2010 on 2009-06-05
[COLOR=black]**I have question what are the most important security vulnerabilities in Linux that could be disabled, this way it can [COLOR=black]become[/COLOR] safer.**[/COLOR]

---

### Post by cdenley on 2009-06-05
> **wiso2010 said:**
> [COLOR=black]**I have question what are the most important security vulnerabilities in Linux that could be disabled, this way it can [COLOR=black]become[/COLOR] safer.**[/COLOR]

What's with the bold? Did you read the security sticky?
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by yaroto98 on 2009-06-05
If you don't like the tone of the security sticky, I suggest downloading DVL as the most secure linux distribution out there. In fact, suggest it to your boss too.

---

### Post by pauna on 2009-06-05
> **wiso2010 said:**
> I have question what are the most important security vulnerabilities in Linux that could be disabled, this way it can becomesafer.

Ubuntu installations are pretty much secure by default from the network point of view, there are not that many services open to the world. Besides, the security team will make sure important security updates fixing known vulnerabilities will become available as soon as possible.

To keep that good situation during use, key issues are:
[LIST]
[*]Keep packages up to date by regulardly updating them from the Ubuntu repositories (either by Update manager or manually).
[*]Install only applications you know how to use and configure. Quite many security problems are caused by wrong configuration.
[*]Disable/remove applications when you don't want or need them anymore. This is especially important for all internet-facing services (such as web servers etc).
[*]Use strong passwords for your accounts (if you have ssh open to the world, you will be bombarded with brute force guessing).
[/LIST]

---

### Post by wiso2010 on 2009-06-05
Well I was asked if there anything on Linux that could be disabled in order to make more secure. I'm not sure what I suggest to them

---

### Post by cdenley on 2009-06-05
> **wiso2010 said:**
> Well I was asked if there anything on Linux that could be disabled in order to make more secure. I'm not sure what I suggest to them

It sounds like someone has a windows mindset. Unlike previous versions of windows, linux does not come pre-installed with a file server which allows remote users to authenticate and gain access to your system.

---

### Post by wiso2010 on 2009-06-05
[COLOR=black][FONT=Verdana]This is the exact words he used. He is asked if there was one way to increase system security and to eliminate unnecessary system services. He wanted for me to look at and consider the services that run by default in Linux, And if there a way to just disable them to make the system more secure. I'm still getting some knowledge on linux, this guy is thinking with a windows mindset.[/FONT][/COLOR]

---

### Post by cdenley on 2009-06-05
> **wiso2010 said:**
> [COLOR=black][FONT=Verdana]This is the exact words he used. He is asked if there was one way to increase system security and to eliminate unnecessary system services. He wanted for me to look at and consider the services that run by default in Linux, And if there a way to just disable them to make the system more secure. I'm still getting some knowledge on linux, this guy is thinking with a windows mindset.[/FONT][/COLOR]

There aren't really any unnecessary network services running by default, especially on a server install. On a desktop install, [avahi]("http://en.wikipedia.org/wiki/Avahi_(software)") is running by default, but it isn't really a security risk. Depending on your network configuration, you might have a dhcp client running, but that is sort of necessary.

This command shows all processes running on your system which are listening for TCP or UDP connections.
```

sudo netstat -tulnp

```

---

### Post by bodhi.zazen on 2009-06-05
Wow, lets not be so hostile :)

The biggest security risk on a linux system is the users.

In terms of learning security, please read the security sticky, it is a sticky for a reason.

As with any OS, Linux can always be hardened, but to be honest you really should have a solid understanding of how the system works before you go making changes.

When you are ready, consider :

1. configure apparmor

2. [http://www.debian.org/doc/manuals/securing-debian-howto/](http://www.debian.org/doc/manuals/securing-debian-howto/)

3. [http://www.debian.org/doc/manuals/securing-debian-howto/ap-harden-step.en.html](http://www.debian.org/doc/manuals/securing-debian-howto/ap-harden-step.en.html)

I think, once you understand the basics, the question then becomes how do you wish to harden the system and to what end ?

To answer the question, what needs to be done to increase the security of Ubuntu - Nothing.

---

### Post by HermanAB on 2009-06-05
Hmm, Ubuntu is secure out of the box.  However, the biggest reason users get hacked is because they install VNC and FTP or think that four letter passwords are uber cool.

---

### Post by soltanis on 2009-06-07
From the sounds of this boss guy, it's more likely that his password is going to be the point of failure rather than any program.

If you're looking for security from a network perspective, it's really simple; don't run services you don't need. If you never ssh into your computer, don't run sshd. If you don't serve web-pages, there's no point in having an HTTP server, and if you don't plan on sharing files, for the love of God don't install an FTP server.

Ubuntu doesn't have any of these activated by default (although ssh is pretty easy to turn on; by the way, ssh isn't really a vulnerable program, it just allows you to run remote sessions, which like I said, if this guy is dumb enough to have a weak password, will definitely be a point of entry).

If you are being more hard core (i.e. paranoid) about your security, and are worried about people stealing data off your hard disks (by physically stealing them, by the way), then set up the computer with LUKS and encrypted partitions with a strong passphrase.

Computer security is never 100% perfect, but with Linux, you start off much better than Windows, and the more paranoid layers you apply, the better off you get. Don't get complacent; vulnerabilities do exist in open source software, so update as often as they occur.

---

### Post by Soul-Sing on 2009-06-08
IMO the biggest security risk is to abandon/leave/or take not serious the off. ubuntu software sources. These are the achilles heel of the "security system" provided by Ubuntu.

---

