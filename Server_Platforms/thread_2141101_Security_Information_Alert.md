---
title: "Security Information Alert"
date: 2013-05-01
forum: Server Platforms
---

### Post by schnabea on 2013-05-01
*** SECURITY information for HOSTNAME ***
HOSTNAME : May  1 10:20:50 : USERNAME : 1 incorrect password attempt ; TTY=unknown ; PWD=/tmp/ubuntu-release-upgrader-d4oqik ; USER=root ; COMMAND=/tmp/ubuntu-release-upgrader-d4oqik/raring

Hey All,

I've been running Ubuntu (and Ubuntu Server) for a long time, slowly building up my knowledge. I finally added sendmail to my server so I could get email alerts of various things and I've been pretty happy with it. Today I got the alert pasted above and I'm just wondering... is this something I need to be worrying about? How do I investigate this? What logs should I be looking at to see if my system has been compromised?

I was not doing anything on the server at the time in the email so I'm a little worried that something's going on...

---

### Post by TheFu on 2013-05-01
Congratulations.

a) sendmail is for extreme professionals who do sendmail and only sendmail for a living. I've been running email servers 20+ yrs and never needed to deploy sendmail. Postfix is a drop in replacement with hugely greater security out of the box.  Don't get me wrong, if you need sendmail, then you need it, but it is also one of the 2 most hacked programs in the history of UNIX servers. Best to avoid, IMHO.  Also, on really busy servers, email services are not run when utilization is above 90%.  That applies to Sendmail, postfix and probably all the other MTAs.  Is sendmail available on your public IP?  If so, I hope you are running it chroot'd?

b) do you allow remote root logins?  If so, why?  Best practice is to block root access from any network connection and only allow root from sudo on the local machine.  Only allow non-LAN access to systems using ssh-keys, not passwords.

c) Is "username" you or someone you know?  Should they be trying to access root?  Is it a daemon account, if so, perhaps you've been hacked?

d) Did you want to "upgrade" a server to Raring?  Hopefully this is a test server, not production. I'm a 10.04 and 12.04 LTS guy. My next planned upgrade path is 14.04 LTS for servers.  I'll be skipping all the intermediate releases, thank you very much.  Stability is more important than "new" to me and my clients.

At this time I'd usually point you to a few of my Linux Security Blog posts, but recently saw that Ubuntu has a Basic Security page that covers much more.
[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)  If you work your way through that page, you are well on the way to a secure single server. Networked server security is more complex as we add trust relationships and need remote authentication, centralized user management, centralized performance stats, alarming, logging, etc....

---

### Post by schnabea on 2013-05-01
Thanks for the link to the basic security page, I'll work through it later tonight or this week. I misspoke earlier... I looked at sendmail but decided it was too much for what I wanted, so I ended up installing SSMTP as all I needed was to send mail.

The USERNAME was my normal user account, which should have root access (via sudo) but I definitely didn't kick off an upgrade cycle at 10:20am. This is my server at home which I use as a file server and media server and I host two separate private wordpress sites on it.

Based on your first question I checked and disabled root login via SSH. Where can I disable all remote access to root? I'd still like to be able to sudo from an external connection via ssh if possible... Let me know what other information I can provide and thanks for the help :)

---

### Post by TheFu on 2013-05-02
I don't understand your last paragraph.  If you disable root from ssh, what other remote access is there?  I can't think of any on my systems.  ssh is it.
To gain root from a remote machine, you need to ssh in as a normal user using keys, then sudo.  This is the best practice and the machine only knows that you are not remote asking for a root connection. After all, your ID is local to the box.

If I were running wordpress and saw stuff like this, I'd assume that my wordpress setup had been hacked and would start looking their.  You are aware of the recent Apache hacks in the last week?  Seems that anyone using cPanel was a target, but it could be anyone using any admin-gui tool.  This crack is especially bad, since it uses shared memory and doesn't write files to any storage for discovery.  I don't use apache and I don't use cPanel, so, in theory, my systems are not targets.

My professional IT security friends will not let any web server running PHP directly on the internet. They prefer to avoid php programs completely, but that isn't always possible, so a reverse proxy is used to actively filter undesirable inputs.  I've used pound previously, but switched to nginx about 3 yrs ago. It works as more than just a reverse proxy very nicely.  Using MicroCache on it does wonders!

If you are running a server on the internet, start watching the security forums for your specific distro.  [http://www.zerodayinitiative.com/advisories/upcoming/](http://www.zerodayinitiative.com/advisories/upcoming/) is a good start, but there are many others to help you monitor.  I skim RSS feeds in the morning and in the afternoon for this stuff and plan specific patches for maintenance periods.

If I believed I were hacked, I'd start looking back through the differences between every backup made looking for things that don't make sense.

---

