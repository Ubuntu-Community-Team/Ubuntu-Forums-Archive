---
title: "fish:// seems to be sending SYN floods"
date: 2010-04-13
forum: Security
---

### Post by VeggyDawson on 2010-04-13
Hi,
I've got a strange problem. I have a number of linux boxes - main running Gentoo, a couple of others running Mint and a new one running Kubuntu 9.10.

All, except the new one, connect to my hosted remote server through FTP, FISH or SSH without any problem.

However the new machine will connect to my remote server, via fish, but then gets immediately disconnected. I have discovered, via my hosting company, that it is flooding the connection and looking in my Router log I can see:

> 1. 2010.04.13 03:24:42 **SYN Flood to Host** 10.10.xxx.xxx, 38299->> 209.85.xxx.xxx, 80 (from ATM Outbound)

If I connect first through SSH on this machine it is fine and I can navigate through the remote filesystem. If I connect through FISH using either Konqueror or Dolphin, I get an initial file listing and then the remote firewall kicks in and blacklists my IP address for half an hour.

Does anyone have any ideas why this may be happening? Once I'm blacklisted I cannot make any connection, from any machine on my external IP address - whether it is HTTP, FTP, SSH or FISH until the remote firewall releases me. I'm stumped!!!! 
Thanks:(

---

### Post by OpSecShellshock on 2010-04-13
Just became aware of fish: five minutes ago when looking at this post to give you some kind of answer, so I might not provide much useful advice. However, it appears that the fish command will try to establish a connection over SSH, but the destination port on the server side is 80. Is your server listening for SSH connections on port 80?

Basically, it appears that what's happening is your client machine is attempting to initiate connections to the remote server, but isn't getting a response, so it just keeps trying. Since SSH connections are working without trouble, it seems to me that when you use fish directly it's attempting a regular http connection for whatever reason, or at least the server thinks it is. Have you tried specifying either the user name or the port when initiating a fish connection?

---

### Post by VeggyDawson on 2010-04-14
Thanks for the response. I wasn't aware that fish tried port 80 - I'll try specifying the SSH port - I assumed it went through on the standard SSH port.  Not sure if that is the problem though because I do get an initial file listing returned from the server but then nothing more as the server's firewall blacklists me. I will investigate the port issue.

I am using a username though:

e.g. fish://user@123.123.123.123

It seems that something has changed in this version of Ubuntu (9.10) as I have never experienced it before. My Gentoo and Mint boxes connect with no problem.

Thanks

---

