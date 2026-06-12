---
title: "Force ssh_config to always show local/remote fingerprint?"
date: 2016-06-13
forum: Security
---

### Post by mikey93898 on 2016-06-13
Hey all,

I'd like to heighten my SSH security a bit, as I'm connecting from outside locations.

I'd like to setup ssh_config such that any simple command like "ssh [email]blah@blabla.com[/email]" will *always* show both the remote server's fingerprint, and the local entry in known_hosts.

I realize known_hosts will already alert me if I happen to have a different entry stored, which is great... but .... I have a lot of servers I connect to, from multiple laptops and installs, and I'm not always the best at remembering to connect to each server initially from home (so my workstation has the correct fingerprint). Sometimes I'm out in the wild and get that warning prompt ("Bro you've never connected to this server before!") and a bead of sweat drips down my temple as I inevitably type y-e-s and hope I'm not the victim of a man in the middle attack.

I think I can just set each SSH server's MOTD to display it's own key... or something, such that I will always be seeing the server's real key after login... but ... how do I configure ssh_config to always show me both the last known fingerprint and the current fingerprint?

I'm trying to dummy-proof my security ... against myself.

Any ideas?

---

### Post by TheFu on 2016-06-14
Sorry. Don´t know how to do what you want and I definitely wouldn´t want any keys displayed in a MOTD.

1) Setup a ¨jump box¨ and always use that to go between all the other machines.  Don´t allow any others to be directly accessible from anywhere else.  That way, you only have 1 point to secure, reduction in attack vectors.

2) setup ssh-agent

3) setup ~/.ssh/config

4) NEVER, EVER, EVER, use passwords as credentials over the internet. NEVER.
[http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures](http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures)

---

### Post by mikey93898 on 2016-06-14
Hey Fu, Thanks for the reply.

Funny you should mention a jump box... I'm already doing that with my home LAN for just that reason. I have a virtual machine with no other services on it than SSHD and a firewall that blocks people who fail to login in the hopes that it'll be a less vulnerable than the other internal machines. My jump box is the only WAN accessible machine, and all my wan/lan SSH daemons on all machines I control are set to key authentication only.

I can't use a jump box for the other machines though, because I don't really trust them, and if I use my home LAN as a jump box I'll lose 90% of their speed (my home LAN is way slower than the normal internet boxes).

I should clarify though that when I say I would use MOTD to display keys, I mean the public key hashes, outputted with "ssh-keygen -l -f KEY_PATH". Since I last posted, I have all my machines displaying MOTD with MD5 and SHA256 sums of whatever key the server is using (rsa or that new ecdsa one, depending on the machine). This is great for a first time login, as I can now pretty quickly visually see if keys don't match.

I'm not really interested in using the ssh agent right now, because I use either full system encryption or home folder encryption with a pretty strong password, so there's no need for me to put a password on my keys inside my .ssh folder (I think, anyway).

But I still need to figure out how to configure my local ssh_config such that it always prints out the md5/sha256 sum of the remote host's public key (as saved in known_hosts) whenever it connects somewhere, even if it's previously connected. I feel like this will be the last step to satisfying my sense of security against MITM attacks.

---

### Post by TheFu on 2016-06-14
ssh thru a jump box doesn´t impact the performance between 2 other machines.  Plus, most things over interactive ssh just aren´t that bandwidth intensive.  Or am I missing something?

If you want something to happen with every connection, just put it at the end of the interactive ~/.bashrc.  I test for interactive sessions and return at the top for non-interactive connections (like rsync or some backup tools) since my full set of environment variables isn´t desired then.  Clearly, if the box is compromised, the war is lost.

---

### Post by mikey93898 on 2016-06-15
> **TheFu said:**
> ssh thru a jump box doesn´t impact the performance between 2 other machines.  Plus, most things over interactive ssh just aren´t that bandwidth intensive.  Or am I missing something?

If you want something to happen with every connection, just put it at the end of the interactive ~/.bashrc.  I test for interactive sessions and return at the top for non-interactive connections (like rsync or some backup tools) since my full set of environment variables isn´t desired then.  Clearly, if the box is compromised, the war is lost.

Ahhhh yes, sorry. In addition to normal terminal commands, I'm also often transferring files, or rarely fumbling around with X11 forwarding. One of my internet servers ends up being an SSH tunnel so I can surf with privacy wherever I am, as well.

The second part of what you wrote is a bit over my head. I'm assuming I would make my own custom script, and call it from within .bashrc, but how would I go about testing for an interactive session? And then, what command would I issue such that the remote server's public key hash was printed?

---

### Post by TheFu on 2016-06-15
X11 forwarding is next to useless over a WAN link, IMHO. There are much better solutions ... the one I prefer also works over ssh, x2go.
Transferring files doesn´t care if there are 50 intermediate machines before getting to the last 1.  The scp/rsync between the 2 machines will run at the speed of those 2 machines connection.  Of course, if those machines are on different networks, then ssh-keys between them will be necessary, but you can lock down the access using any firewall interface preferred.

I use ssh for all sorts of things: [http://blog.jdpfu.com/2014/09/23/you-don-t-know-ssh-about-ssh](http://blog.jdpfu.com/2014/09/23/you-don-t-know-ssh-about-ssh)
But for surfing anonymously, prefer openvpn. ssh is fine, but a little slower.

In the interest of teaching a man to fish .... the man page for bash will explain the start up for an interactive session and many, many, other things.  I always check the manpage when needing details.  Usually, I just check if $PS1 has been set or not.  [http://www.tldp.org/LDP/abs/html/intandnonint.html](http://www.tldp.org/LDP/abs/html/intandnonint.html)  

As for how to script it, what commands would you type?  Start there.

---

