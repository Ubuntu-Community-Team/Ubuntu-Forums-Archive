---
title: "Desktop sharing vnc upnp .xsession-errors.old full drive"
date: 2013-10-16
forum: Security
---

### Post by SirWeazel on 2013-10-16
Thanks in advance for any help. Here was/is my issue.  I wanted to access my computer from work so i enabled the default desktop sharing preferences from withing ubuntu. I chose a difficult password (as difficult as i could manage because it appears to be limited to specific amount of characters) and for simplicity i quickly used UPnP to configure and forward ports. Then after a couple days, the hidden .xsession-errors.old file ballooned and completely filled up my 480GB SSD. The file grew to over 300GB in size and my system became unusable. It took me a day to track down the hidden file.  I needed a usable workstation again, so i deleted the file and couldn't dive into the log too much. What i could gather was i was being attacked/brute forced from some various IP addresses.
Now for some questions?

1. What happens after so many attempts? What's the default behavior and does ubuntu just ignore/deny an ip after so many attempts or could someone just keep brute forcing there way in?
2. Why would this log not have a size limit?
3. Do you think someone grabbed my ip from somewhere (ie visited website logs) or was i just unlucky and someone was randomly scanning and came across my system?
4. What should i do to prevent this from happening in the future?
5. Any other thoughts/comments/recommendations?

Thanks in advance for any help provided.  The forums are usually helpful, and i hope that in the future i can return any help and learn from my experiences.

---

### Post by TheFu on 2013-10-16
Scans for commonly used, poorly secured, ports happens all the time.  It takes less than a week to scan **every** IP on the IPv4 internet for common ports.

VNC is not secure.  Using it means you need a VPN or tunnel too.  That means either OpenVPN or ssh.  VNC is designed for LAN remote desktop use, NOT over-the-internet use.

For over the internet use, 
a) use ssh-only when possible. No GUI.
b) if a GUI is needed, use either an SSH tunnel or OpenVPN ... do not use PPTP.

For WAN-based remote desktops, I've found FreeNX and nx-client to be the best and easiest way to get something working that is secure and efficient.  [https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX) should help.  To me, NX feels 2-3x more responsive/efficient than any RDP or VNC tool.  Since FreeNX uses ssh, only the normal ssh port needs to be opened and secured in the default way.  Fail2ban or DenyHosts are the usual ways to handle that plus using key-based connections - NEVER passwords.

---

### Post by SirWeazel on 2013-10-18
Looks like i'm going to have to dive into this a little more and give it some thought. You have some good links in your signature that i'll have to read over. Now only if i could download all the info i needed directly into my head (which is already overloaded).
Can you give me your thoughts on why not to use PPTP? Also, do you think by default ubuntu kept allowing connection attempts?
So once i have FreeNX or similar setup, you recommend Fail2ban or DenyHosts to monitor my ports and prevent other login attempts? I already have a random port opened up and forwarded for my media (via plex) so i can access my media from anywhere. Thoughts?

As always, i appreciate the time you've taken to answer my questions.

---

### Post by TheFu on 2013-10-18
> **SirWeazel said:**
> Looks like i'm going to have to dive into this a little more and give it some thought. You have some good links in your signature that i'll have to read over. Now only if i could download all the info i needed directly into my head (which is already overloaded).
Can you give me your thoughts on why not to use PPTP? Also, do you think by default ubuntu kept allowing connection attempts?
So once i have FreeNX or similar setup, you recommend Fail2ban or DenyHosts to monitor my ports and prevent other login attempts? I already have a random port opened up and forwarded for my media (via plex) so i can access my media from anywhere. Thoughts?

As always, i appreciate the time you've taken to answer my questions.

PPTP has been hacked ... er ... more than once. It is weak.

Why did ubuntu allow connection attempts?  Did you tell it to stop? With great power, comes great responsibility. Running a server means you KNOW what you are doing and accept the risks.

fail2ban should be installed on any machine with an ssh-server.  IMHO, every machine should be running ssh-server, so .... 

Can't talk about plex, besides that making it available over unencrypted connections outside the LAN is ... er ... foolish, IMHO. It is really worth risking any level of security for every system on your LAN to watch a video? That is really what is happening.

---

