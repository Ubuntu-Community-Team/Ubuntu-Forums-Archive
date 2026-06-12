---
title: "Remote server losing connections.  Need assistance on what to watch for."
date: 2014-03-21
forum: Server Platforms
---

### Post by Anaximander Thales on 2014-03-21
I have purchased a remote server that is running 13.10.  Twice I have had to have the tech people at the location reload the software for me.  The first time, I was given my root account information, I logged in, and started hardening the server.  I locked down SSH, set up hosts.allow and hosts.deny, and was looking into shutting down ports. I performed a reboot after getting a kernel update and I was no longer able to connect.  I contacted support and all they said was some how I closed off the connections.  Fair enough, I dinked around with things and messed something up.  Brand new installation, new root account information.  I do nothing except install LAMP packages, perform regular updates and perform a reboot after a kernel update.  Viola, lost connections again.  I ask for an explanation, and all I am told is that somehow I lost my connections.  So, they can't get to the server except physically, and I can not remote into.  Both times this occurred after having 20 or more days uptime.

So, how is it possible to lose 'connections?'  My assumption is that I'm either losing my IP address on the reboot, or I'm having all of my network locked down through some means.

So -- now that they are performing the second installation:
A)  Other than checking /etc/network/interfaces and making sure my IP is static, what else should I look at to ensure I'm not going to lose my IP address?
B)  What 'connections' should I be concerned with?  I know IP, I know ports (specifically ports I use for SSH), what else should I look for?
C)  I know there is hosts.allow and hosts.deny, I set it up the first time, but not the second time.  Are there other files I should look for/at?
D)  What monitoring tools should I look at setting up so that when anything that has to do with 'connections' changes I'm notified before I reboot?
E)  Once the monitoring is set up, what files should I monitor?

I honestly have no idea why this server is giving me headaches on a reboot.  I've never had a server lose 'connections' after I've gotten it set up.  The only difference is my servers were local to me, and this one is remote.

Thank you for your time.
@

---

### Post by TheFu on 2014-03-21
ssh is one of the things that isn't worth accidentally blocking. Instead of hosts.allow/deny, perhaps **denyhosts** or **fail2ban** would be a better choice? Also, only use key-based connections, not a password, to make it 1000x more secure.

From your description, it is hard to determine reality.  Often, we don't know what we don't know.  How many servers have you configured previously and how long have you been doping this?
So ... if you are modifying the firewall, it is likely a mistake is being made. Can you dump and post the settings?

---

### Post by Anaximander Thales on 2014-03-21
> **TheFu said:**
> ssh is one of the things that isn't worth accidentally blocking. Instead of hosts.allow/deny, perhaps **denyhosts** or **fail2ban** would be a better choice? Also, only use key-based connections, not a password, to make it 1000x more secure.  Yeah -- I'm quite paranoid about blocking that out, so I generally check about three times to make sure I don't block my SSH port.

> **TheFu said:**
> From your description, it is hard to determine reality.  Yes, I agree.  And it's unhelpful that what ever it is I do blocks the techs out as well.  All they know is that my connection is gone and I and they can not get to it.  It doesn't even ping, which really makes me believe that I'm losing my IP address.

> **TheFu said:**
> Often, we don't know what we don't know.  How many servers have you configured previously and how long have you been doping this?
So ... if you are modifying the firewall, it is likely a mistake is being made. Can you dump and post the settings?  Well, I've been playing with Linux for about 12 years.  I work as a system administrator and adminster about 10 linux servers and more windows server at work.  I've personally set up my own linux servers and servers for several friends, and host my own linux server at home as well as my work stations at home and work.  I'm the go to guy for my friends for linux on what they need to look at to fix issues.  But, I'm still quite a novice even though I'm quite knowledgable with Linux, but that's my opinion.  There's so many options that I may become really proficient, but I'll never an expert.

I hadn't even begun the firewall on this server.  I was intending on doing it the first time, but I had taken a break from hardening it to make sure things were working correctly and to get it doing what I needed so that I could test the firewall settings, once it was set up, to make sure there wasn't an issue.  I was following a blog post on what to do, but I don't have it here at work to quote it to show where I had left off.  I have a sript that I use to set the firewall up here at work, and I looked over it, so I have a copy of that and feel I could get it set up correctly when I need to.  However, that's a good thing that I should definitely look at.  Again I had never touched it, nor tried installing one either time, and it's possible that a firewall is installed by default in their installation script.  Hadn't thought of that.  Thank you.

---

### Post by tgalati4 on 2014-03-21
Was there anything in the log files (/var/log) that showed why the system "lost connection"?  Your helpful IT staff noted that you could not connect, but was that because the system crashed or because of a configuration change?  If it was a hardware/power issue, then you need to troubleshoot that first so that you are not constantly chasing mysterious lock-out issues.  I would also check the infrastructure--the wiring and switch connections.  Change them and see if that makes a difference.

---

### Post by TheFu on 2014-03-21
So the service provider doesn't have an out-of-band connection method for every server? Scary.
Guess they don't know about cobbler either. Redeploying a machine - especially a VM shouldn't be that hard.

My LUG had a server that died intermittently for about 4 months. Drove us crazy. We never figured out the issue - just swapped out the box and everything has been find since. That was about a yr ago. Remote troubleshooting is hard without DRAC/RIBLO/IPMI support.

---

