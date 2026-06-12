---
title: "SSH Warning: &quot;Remote host identification has changed&quot;"
date: 2005-05-10
forum: Server Platforms
---

### Post by mwnovak on 2005-05-10
I'm running Ubuntu 5.04-ppc as a web/file server on a "headless" G4 Cube.  I use OpenSSH 3.9p1 for all remote administration tasks.  And, lest I forget, I am a newbie at all things *nix.

This afternoon, while working on an iptables script, I had three or four open SSH connections into the server.  When I attempted to open an additional connection, I received the following message:

> 
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@ WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!  @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
f2:92:1d:da:81:2a:d7:16:0a:48:f0:43:20:1c:f4:b5.
Please contact your system administrator.
Add correct host key in /home/novak/.ssh/known_hosts to get rid of this message.
Offending key in /home/novak/.ssh/known_hosts:1


My initial--and hasty--reaction was to delete the local ~/.ssh/known_hosts and try opening the connection again.  While this restored me to a l/p situation, I was unable to actually login: the system took my l/p, but immediately dropped the connection with a note about "not having permission" (or some such).  Attempting yet another login brought me back to the "Warning: Remote Host Identification Has Changed" message quoted above.

Eventually, I restarted the server and dropped all my open connections, cleared the local ~/.ssh/known_hosts, and tried again.  And, guess what?  Everything now seems back to normal.

I'm hoping that someone can explain to me what might have happened here.  A cursory Google search on the SSH warning suggests that a) it's a non-trivial warning, and b) it's a common occurance when system administrators update RSA certs. for an SSH daemon.  But I _didn't_ update RSA certs. on the server.  So, I'm wondering... well, honestly, I wondering if my SSH daemon didn't get attacked.  Is there an sure way to tell?  And, if it didn't get attacked, how can I figure out what caused this?

Any help is appreciated,

--MW

---

### Post by JonahRowley on 2005-05-10
What do the modification times on the **/etc/ssh_host_*_key*** files say?  I know, these times can be forged, but it's a start.

Are you *sure* that you were connecting to the correct host?  It wasn't just some DNS mixup?  Because something like this really shouldn't happen.  Check your logs, anything suspicious?  If there was an attacker, they might not have cleanup up after themselves.

I make a backup of my host keys after I install, this is a good thing to have.  Perhaps you should start this as well?

---

### Post by LordHunter317 on 2005-05-10
It sounds to me like you connect to the host form itself or some other such nonsense to get a key mismatch when you didn't have one.

Without knowing what shells you were running, how you connected them, etc.  there's no way to discern what actually happened.

---

### Post by mwnovak on 2005-05-10
Okay...

JonahRowley:

All the /etc/ssh/known_host_*_key files are dated 2005-04-26.  Which at least looks good: that was my install date for the machine.

I poked around in /var/log/syslog and /var/log/auth.log and didn't find anything particularly out of the ordinary (no failed login attempts, no unaccounted-for logins, no heavy port scanning logged by my firewall, etc).  That said, I'm not sure what all I should be looking for. ;^)

Interestingly, while I expected to find unusual sshd entries for the date/time all of this happened, there wasn't a single note about the warning in question ("Remote Host Identification Has Changed").  In fact, all sshd entries for May 9 16:00:00-19:00:00 (inclusive times for all of this happened) were more-or-less identical to entries on preceding and subsequent days.

The one exception is that all the sshd login enteries in /var/log/auth.log before May 9 13:48:58 include a note about "reverse mapping checking getaddrinfo for ... ."  I've received that note/warning upon ssh login since I installed Ubuntu.  However, the message doesn't appear in auth.log for any ssh login afer the above-noted timestamp.  I dunno if that means anything, but...

I'm not sure what you mean about a DNS mixup.  Are you asking whether I ssh'd to the wrong address?  Or whether something went awry with the dns pointers to my machine?  The former option isn't likely: I usually use the same command from my shell history, and I certainly double-checked everything when I started getting the "Host Id. Has Changed" message. 

One thing that might shed some light on this is that, somewhere in the midst of getting that warning message and not being able to login to the server, I received a message to the effect of, "Connection terminated by 206.x.x.x".  My external client ip is 67.x.x.x, and the external server ip is 63.x.x.x.  I have no idea where that 206.x.x.x ip was pointing (it didn't resolve with DNS, though). 


LordHunter317:

I'm not connecting "to the host from itself" or any such.  As noted, the server is Ubuntu 5.04 running OpenSSH 3.9p1 built against OpenSSL 0.9.7e; my client machine is a PowerBook running OS 10.4 with OpenSSH 3.8.1p1 built against OpenSSL 0.9.7b. 

When I connect to the server, I issue the following command from the client machine:

```
ssh [username]@www.[serverdomain].org
```

If I happen to be inside the LAN with the server, I use the same command but may change [serverdomain] to the server's local ip address.  RSA keys were established on my first connection to the server (it may have generated unique keys for both my first connections from outside and inside the LAN, but I don't recall).  

Until yesterday, I have never had the slightest hiccup ssh'ing into the server from my client machine regardless of my location.

Shells?  Like bash, tsh, etc?  My server account runs the bash shell; my client/PowerBook account also runs the bash shell.  Does that make a difference regarding the present discussion?


Anyway, does any of this shed and additional light?  If I'm not answering questions appropriately, not giving enough/the right kind of information, or generally being confusing... let me know and I'll see if I can't clarify things.  

In the mean time, I'm still wondering what the heck happened yesterday.

Thanks again,

--MW

---

### Post by Beernut on 2005-05-13
I guess it might be possible that there was some IP/DNS spoofing going on but maybe not.  Unless I am mistaken the key from the server should not change unless you change it somehow it shouldn't matter where you login from.  You might want to change your configuration to only use keyed authentication.  You will need to copy your key to your second computer.  There is a link in my signature for a HowTo.

---

### Post by mwnovak on 2005-05-17
Beernut--

Yeah, I get that authenticating through RSA keys is more secure and probably worth doing, but I still don't understand why the sshd behaved like the server key had changed...   I hadn't regenerated keys since installing OpenSSH, so I shouldn't have received that message.  Right?

Regarding the local keys (~/.ssh/known_hosts on my client machine), I just meant that client keys are stored for both [www.[domain].org](www.[domain].org) and 192.168.x.x (pointing to the same machine)... which makes sense because, if I'm on the LAN and ssh to the server's non-public IP, there's no way for my ssh client to resolve that non-public IP to the server's public domain name.  The actual keys stored on the client machine should be/are the same in both cases, I think.

I dunno...  

--MW

---

### Post by Beernut on 2005-05-17
[QUOTE=mwnovak]Beernut--

Yeah, I get that authenticating through RSA keys is more secure and probably worth doing, but I still don't understand why the sshd behaved like the server key had changed...   I hadn't regenerated keys since installing OpenSSH, so I shouldn't have received that message.  Right?  [/QUOTE]


Right the you shouldn't have recieved the message unless you did something on the server to change the key.  I would have been curious to see if the it went away trying to login at another time before you deleted the offending key.  [Here is a good overview of how a MITM attack works.](http://www.vandyke.com/solutions/ssh_overview/ssh_overview_threats.html) It's basic but explains it pretty clearly.  There are a few programs which can accomplish this sshmitm package for DSNIFF and ettercap are a couple.  I would switch to keyed authentication after making sure there aren't any machines on you network acting as a MITM.

---

### Post by mwnovak on 2005-05-18
> I would switch to keyed authentication after making sure there aren't any machines on you network acting as a MITM.

Fair enough (your tutorial at tsb.blogdns is _very_ nice, btw).  I have one more question, though...

If I understood the cited explanation of mitm attacks, the attacking machine would have to be on the same subnet as either my client machine or my server (I'm not 100% clear as to which).  Okay, so...

There are no publicly-accessible, "always on" machines residing on the LAN with my server.  That should rule out 192.168.0.0 as a concern, right? 

The server itself lives at 63.199.0.0 with a dynamically assigned ip through SBC's residential dsl service.

My client machine is usually running from 67.161.0.0 with a dynamically assigned ip from Comcast's residential cable modem service.

To make sure there isn't a mitm machine residing on my subnet, doesn't that mean I'm looking at either SBC's or Comcast's networks?  Is it even possible to determine whether there's a mitm running from somewhere in 63.199.0.0 or 67.161.0.0? 

Thanks again for your help.

--MW

---

### Post by LordHunter317 on 2005-05-18
[QUOTE=mwnovak]Fair enough (your tutorial at tsb.blogdns is _very_ nice, btw).  I have one more question, though...

> If I understood the cited explanation of mitm attacks, the attacking machine would have to be on the same subnet as either my client machine or my server (I'm not 100% clear as to which). Okay, so...Nope.  A machine performing a MITM can be anywhere on the Internet.  IT's just likely it will be.

> There are no publicly-accessible, "always on" machines residing on the LAN with my server. That should rule out 192.168.0.0 as a concern, right? Nope.  But the odds of a MITM having occured here are zero.

The issue at hand is still likely PEBKAC, or potentially an dynamic IP reassignment.  But there's no way to tell without complete session logs.

> Is it even possible to determine whether there's a mitm running from somewhere in 63.199.0.0 or 67.161.0.0?No real way for you do to it, really.

---

### Post by mwnovak on 2005-05-18
> The issue at hand is still likely PEBKAC ...

Hmm... I don't think that's particularly appropriate, but thanks anyway.

As I've said, if I'm not providing enough information to "help people help me," just let me know what's needed.

--MW

---

### Post by enzyme on 2008-05-15
ssh-keygen -R ip_addressInConflict

---

