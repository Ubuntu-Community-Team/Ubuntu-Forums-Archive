---
title: "apache not working on local network and other issues"
date: 2015-03-10
forum: Server Platforms
---

### Post by MissinasWorld on 2015-03-10
I use to host my site but then went away from it for a few years, now I'm trying to get it going again and having a world of issues that I do not remember having before, and I will admit that going away from linux for a few years and then coming back, I have forgotten most of what I use to know!

I installed Ubuntu 14.04 LTS and then installed lamp, php5, and apache2 with sudo get-apt install. there is no firewall blocking my server, its listening on port 80, the router is forwarding port 80 on my computer, I did have to add ServerName localhost to the apache2.conf file and restarted the server without error afterwards, I can access my website from OUTSIDE the local network but not On the local network. Some of my pages are not working but they are there and the links are not broken. my site is currently using: [http://missina.tk](http://missina.tk) 

I know it is probably something very simple that I am missing, if you need more info just tell me and I will post it. Im kind of missing the old vertions of ubuntu and apache right now. 

Thank you,

Missina

---

### Post by volkswagner on 2015-03-10
If you can access the server from outside but  not inside your LAN check router settings.

There may be some settings for NAT reflection.

---

### Post by SeijiSensei on 2015-03-10
Are you accessing the site locally with a URL like [http://www.example.com/](http://www.example.com/)?  Does [www.example.com](www.example.com) resolve correctly to the server's IP address from inside your network?  Is there a matching server configuration in /etc/apache2/sites-enabled that handles requests for [www.example.com?](www.example.com?)

If the IP address for [www.example.com](www.example.com) is on the Internet-facing side of your router, that can be a problem with many home routers.  Try adding an entry for [www.example.com](www.example.com) to /etc/hosts with the server's address on the local network.

---

### Post by fzaman2 on 2015-03-11
> **SeijiSensei said:**
> Are you accessing the site locally with a URL like [http://www.example.com/](http://www.example.com/)?  Does [www.example.com]("http://www.example.com") resolve correctly to the server's IP address from inside your network?  Is there a matching server configuration in /etc/apache2/sites-enabled that handles requests for [www.example.com?]("http://www.example.com?")

If the IP address for [www.example.com]("http://www.example.com") is on the Internet-facing side of your router, that can be a problem with many home routers.  Try adding an entry for [www.example.com]("http://www.example.com") to /etc/hosts with the server's address on the local network.

Hey, I'm having the same issue and have a thread [here]("http://ubuntuforums.org/showthread.php?t=2268218")

Could you explain what the entry for example.com and the IP address would look like in /etc/hosts?  I'm kind of in the same boat as the OP of this thread...haven't used linux in a few years and trying to get it working.  Mine also works from outside network but not inside.

Thanks for any help.

---

### Post by fzaman2 on 2015-03-11
So got mine working finally...added the server's IP address to the DMZ host and enabled it.  That made it start working right away.

Hope that helps

---

### Post by MissinasWorld on 2015-03-11
Sorry was working last night and slept today. My router settings are fine, I am using the same router that I use to use a few years ago when I use to run a server on apache from my home internet, I also have 2 security cameras running off the router open on port 8080 that are working fine. I played around with a few things before going to work last night and when I look up my site on localhost, it DOES work. but if I try to look it up with the IP address or the website address, it does not work. Also, when I can access my site on my tablet with another network, not all the pages work. I changed the permissions to allow others to read the files, but still some do not seem to work. The part that really drives me nuts is that this was ALL working fine right after I installed it, but then Ubuntu updated and now I can't seem to get away from these issues. I tried to reinstall and start over fresh but the issues are still there.

---

### Post by MissinasWorld on 2015-03-13
got it fixed this morning. it was a combination of router issues and needing to create the sites-avalible file. the issue with my router was that it needed to be opened under virtual server and not port forwarding (even though that is how it use to be set up and it worked fine for many many years that way). as far as I can tell, all is working well and I can finaly work on other things. Hopefully I relearn some of what i have forgotten over the past few years!

Thanks for all the help, you guys pointed me in the right directions :)


Missina

---

