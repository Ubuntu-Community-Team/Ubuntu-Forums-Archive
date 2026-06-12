---
title: "Multiple attempted logins from same IP"
date: 2018-09-18
forum: Security
---

### Post by jeanathon2 on 2018-09-18
So I have a few IP address that seem to be running a script trying to login via ssh, imap, etc. filling up my log files.  It is mildly annoying so the most insistent ones I have /sbin/route add -host IP address -reject, but being slightly vindictive I was thinking it would be nice to route their attempted logins back to them.  So that they can fill up their own logs.  
I know iptables has a forward command that I was thinking of using, but I'm not sure that would be the best way to go.  Any thoughts on doing this?

---

### Post by TheFu on 2018-09-18
Hacking back is illegal in some countries.

I just drop the packets at the router.  I block entire countries which have no business accessing my systems. If you can, use a whitelist for network access.  Not everyone can if you don't know where your people might be trying to connect from.  We simplified the IMAP stuff - it is only available via VPN, so there aren't any external attempts on that anymore.

For ssh, if you move the listener to a non-default port, almost 100% of the unwanted attempts will be gone.  Also, install **fail2ban** and only allow key-based authentication over the internet for any ssh-based connection. That would be ssh, scp, sftp,rsync, and most network backup tools like duplicity, rdiff-backup and the 50 others.  fail2ban is preconfigured for ssh on 22/tcp, so if you have the router do port-translation from WAN:62022 --> LAN:22 you can use the defaults.   Tweak your client ~/.ssh/config file to have 2 configs - the public and the LAN so you need not to know which port the WAN is listening on for day-to-day use.  Every ssh-based tool that I know honors that setting.

You can setup fail2ban for imap connections too, if you like.

---

### Post by QIII on 2018-09-18
I believe TheFu and I were recently in a similar thread.

I want to echo his advice to use "drop".  "Reject" is throwing down a gauntlet and can end up with the hacker saying "Challenge accepted".

---

### Post by jeanathon2 on 2018-09-19
Good advice both of you.  Interestingly I already use a nonstandard port for ssh.  These are the more persistent ones.
I will definitely implement a VPN for imap.
As far as the legality of hacking back I would think just mirroring back their attempts would not constitute hacking on my part since any attempts successful or not would be initiated by them.  I am concerned about the overhead of such a scenario, would not want to accidentally set up a loop.

---

