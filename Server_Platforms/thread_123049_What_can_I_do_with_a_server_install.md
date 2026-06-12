---
title: "What can I do with a server install?"
date: 2006-01-29
forum: Server Platforms
---

### Post by mohapi on 2006-01-29
I'm sorry for such a foolish newbie question, but I install Ubuntu in two steps -- first server, then (x)ubuntu-desktop -- and when I finish the server install, I always wonder this.

It seems quite sparse. Can I do anything with it, or should I just keep chugging along, setting up a GUI?

---

### Post by dotmil on 2006-01-29
A server install is just that by design, sparse. This allows the admin to install only what is needed/wanted and nothing that is not.

---

### Post by mohapi on 2006-01-29
I see. So what kind of things could be installed? 

I'm sorry, I know this is a god-awful newbie question to ask. I think my ignorance stems from a long-suppressed fear and loathing of DOS, and remembering how little I ever got done with it.

---

### Post by stream303 on 2006-01-29
Don't fear the command line!

I came from the dos world myself, and the hardest thing for me to do was to get my psyche around the fact that you don't need a gui, or in the case of dos, a CUI.

Don't try to remember all the commands at once, and don't fret over not remembering all the optional flags.  That's what aliases and shell scripts are for.

Anyway, right off the top of my head, I'd install a few programs:

nano - easy to used editor  (although I've come to love vi over the years)
lynx - easy text-based web browser and file manager, ie
**lynx .**     (lynx - space - dot)

mailx  - or perhaps mutt for mail
slrn - newsreader

It all depends on what you want to do.  Learn some bash commands
cal
top
ifconfig

man - manual pages for commands (sometimes too terse for beginners)
apropos - find out what commands relate to your subject, such as

apropos clock
apropos calendar
apropos file

You get the idea.  Maybe move on to shell scripting and learn about file redirection < > and the power of pipes |

The simplicity and raw power of the command line is great, once you forget the notion that you need a pretty user-interface to get results.

---

### Post by Iowan on 2006-01-29
[QUOTE=mohapi]I see. So what kind of things could be installed? [/QUOTE]I suppose the traditional answer would be "That depends on what you want the server to do." My server install included most of the basic tools I needed, but I want the box to be a  Samba server, so I had to install that.  If #1 son decides he wants to use it as a jukebox, I suppose I'll have to find some software to do that, too.  I currently have a Linux-based router/firewall between the server and internet that also acts as DNS server and DHCP server, but these jobs may get moved to the Ubuntu server - so as to let the router work less (it's a '486).

---

### Post by sco01 on 2006-01-30
I would recommend you to set up a home server just to learn more about GNU/Linux. I use mine for HTTP (Apache + PHP), SSH (OpenSSH), SMS (Gnokii) and as a File & Print Server (CUPS + Samba). I started my GNU/Linux experience two months ago and there are two websites (besides this one) that helped me alot from day one:

[http://www.ubuntuguide.org/](http://www.ubuntuguide.org/) (Somewhat outdated, but still very helpful).
[http://www.ss64.com/bash/](http://www.ss64.com/bash/) (Linux commands)

Regards,
Stefan

---

### Post by alamba on 2006-01-30
I run the following on my server install: Apache for my website, Postfix for my mail, nessus (rather not say what for!), jabber server (chatting), webmin (just incase I need to admin it from office where ssh ports are blocked), ssh (remote shell access), samba(file sharing with XP), iptables(firewalls) & ftp(mainly for uploading website pages).

Akshay

---

### Post by mohapi on 2006-02-01
I think I get the idea. I can see myself playing with that ... after I get some more basics nailed down. Thanks.

---

