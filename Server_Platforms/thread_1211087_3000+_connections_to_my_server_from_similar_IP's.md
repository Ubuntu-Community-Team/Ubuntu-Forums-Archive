---
title: "3000+ connections to my server from similar IP's"
date: 2009-07-12
forum: Server Platforms
---

### Post by gobbledigook on 2009-07-12
Hi!

I run a small file server at home with which i host a few webpages, mainly just for messing about with, and noticed yesterday that i was getting time-outs occasionally when i was using my main machine to browse the web. At first I thought it was someone using my wireless, but on investigation i found that my router reported over 3700 connections to my server! 

I checked to make sure my utorrent was turned off on the server.  I was wondering if anyone could help me find out why i have so many connections and if they pose a security risk? is someone trying to hack my server? Its not a big deal to get rid of them i just do a reboot of my modem to get a different IP. However i am very curious to know what its all about:)

I have run trace's on a few of the IP's and they all seem to be coming from the same host, you can see for yourselves [**here**]("http://network-tools.com/default.asp?prog=express&host=217.154.97.119").

I have also got the logs from iptraf and netstat for inspection, in the attached .zip file.

any help greatly appreciated:)

Dan

---

### Post by jasonbrisbane on 2009-07-13
Hi,

I use network-tools.com for checking IP's.

I checked one of those:
[http://network-tools.com/default.asp?prog=network&host=217.156.225.180](http://network-tools.com/default.asp?prog=network&host=217.156.225.180)

It contains the details to contact the admins regarding spamming your connection.
Send them a very nicely worded email asking why their connections should be trying to make so many connections to your server "before you take action to prevent any further misuse". Send the logs for EVERYTHIGN to prove and backup your claim of misuse.

See what they say.

I got a nice letter saying they had cancelled the users accounts and would be taking legal action (not those guys, but still it was an OS company!


Since the activity appears to be someone trying to SSH into your machine, you could:

A) Disable port 22 on your firewall.
B) if you use port 22, then Disable all incoming packets (ALL) form 217.x.x.x.

Hope that helps!

---

### Post by grantemsley on 2009-07-13
> **gobbledigook said:**
> Hi!

I run a small file server at home with which i host a few webpages, mainly just for messing about with, and noticed yesterday that i was getting time-outs occasionally when i was using my main machine to browse the web. At first I thought it was someone using my wireless, but on investigation i found that my router reported over 3700 connections to my server! 

I checked to make sure my utorrent was turned off on the server.  I was wondering if anyone could help me find out why i have so many connections and if they pose a security risk? is someone trying to hack my server? Its not a big deal to get rid of them i just do a reboot of my modem to get a different IP. However i am very curious to know what its all about:)

I have run trace's on a few of the IP's and they all seem to be coming from the same host, you can see for yourselves [**here**]("http://network-tools.com/default.asp?prog=express&host=217.154.97.119").

I have also got the logs from iptraf and netstat for inspection, in the attached .zip file.

any help greatly appreciated:)

Dan


Actually it looks like the connections are coming FROM your server.  The netstat looks like your server is performing a scan for SSH servers on 217.156.0.0/16.

There are also connections to an IRC server - your computer is almost certainly part of a botnet now.

Most likely, your server is compromised. It's happened to me as well in the past.  Probably someone guessed a password and logged in via SSH.

Make sure nobody else is logged in (who command). Also, check /var/log/auth.log for people logging in via SSH.

Look in every user's home directory for hidden folders (start with a dot, do ls -la).  That's usually where they keep their files.

It's also possible that they have installed rootkits or other software to hide their activities.  I'm not an expert on removing or detecting such things - usually its safer to just reinstall the OS from scratch.

---

