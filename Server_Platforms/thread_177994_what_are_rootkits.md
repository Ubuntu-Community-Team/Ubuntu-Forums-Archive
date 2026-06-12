---
title: "what are rootkits?"
date: 2006-05-17
forum: Server Platforms
---

### Post by lonelypauly on 2006-05-17
how secure is ubuntu really?  ive read some things about rootkits and it kind of freaked me out.  i grabbed some root kit finder app from synaptic but i dont know how to use it.  any recommendations if i want to do a periodic scan of my system?

---

### Post by Sef on 2006-05-17
> how secure is ubuntu really?

It is very secure.  Think of the difference between GNU/Linux and Microsoft Windows this way:  

GNU/Linux:  You walk into a house, and you can use the shower, the computer, the tv, and all the other things in the house.  You do not like how things are done; however, you can't change a thing for the basement where all changes that are needed to be done is locked.   Only if the owner lets you in can you make any changes.

Microsoft Windows: You walk into a house, and you can use the shower, the computer, the tv, and all the other things in the house.  You do not like how things are done; however, you walk into the basement and make all the changes that you want.  The owner does not need to let you in cause you are in already.  

That is essentially the difference between the two systems.  In GNU/Linux, unless you (the owner) allow something to get into root (the basement) it is locked out.  It can affect the the applications (the shower, tv, computer, etc.), but it can't change your system.  In Microsoft Windows, once you are in, you can go anywhere.  You can change anything and everything.  You (the owner) may not even realize things have been changed.  

> ive read some things about rootkits

A root kit cannot affect a GNU/Linux system unless you allow it too.  If something come up that you don't recognize, then do not allow it.  It is that simple to keep rootkits off of your system.  In Microsoft Windows, a rootkit can infect your system without you even realizing it.  Read this article from The Register.

[http://www.theregister.co.uk/2006/05/16/poker_site_trojan/]("http://www.theregister.co.uk/2006/05/16/poker_site_trojan/")

Here's a definition of a rootkit from webopedia:

>  A rootkit is a type of malicious software that is activated each time your system boots up. Rootkits are difficult to detect because they are activated before your system's Operating System has completely booted up. A rootkit often allows the installation of hidden files, processes, hidden user accounts, and more in the systems OS. Rootkits are able to intercept data from terminals, network connections, and the keyboard.

[http://www.webopedia.com/TERM/r/rootkit.html]("http://www.webopedia.com/TERM/r/rootkit.html")

The only protection that you really need is to have a firewall.  That is download through Synaptic.  (System > Administration > Synaptic)

So if you run GNU/Linux, relax and enjoy using your computer without of rootkits and other malware.

---

### Post by glotz on 2006-05-17
Basically any OS is just as secure as the person using it. The threat within the firewall as it's called... I'd be more concerned about never getting a rootkit than detecting or removing one... Might be of interest [http://en.wikipedia.org/wiki/Rootkits](http://en.wikipedia.org/wiki/Rootkits)

---

### Post by Azrael on 2006-05-17
[quote=glotz]Basically any OS is just as secure as the person using it.[/quote]
This old saying is lame and inaccurate. An OS which has a high level of security by default (i.e. out of the box) is more secure for an ignorant user than an OS with little default security is for that same user. The potential for damage may be similar, but the *chance* definitely is not. Statisically, the chance of an OS being in an insecure state is not 1:1 dependant on the knowledge/wisdom of the user, because the chance of a user accidentally causing an insecure situation is also dependant on the OS.

---

### Post by glotz on 2006-05-17
Your critique is warranted, I should point out that what I meant of course was, you can screw every system by doing silly things. No amount of built in security will help a clueless and promiscuous user.

I never intended to say that I can use windows 95 safely if I want... :)

---

### Post by lonelypauly on 2006-05-17
ive read on these forums that i don't need a firewall or antivirus on ubuntu.  now, i understand why i wouldn't need antivirus, as 99% of viruses/malware are written for windows.  as far as a firewall is concerned...if i am already behind a router with a hardware firewall, do i need a software firewall as well?  if so, which app should i look for in synaptic?

also, which apps are available for ubuntu that i can use to periodically scan my computer for rootkits, etc?  i installed a rootkit hunter from synaptic, but i have no idea how to use it.  

thanks for the info.

---

