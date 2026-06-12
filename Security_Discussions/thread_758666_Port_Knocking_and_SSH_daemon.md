---
title: "Port Knocking and SSH daemon"
date: 2008-04-18
forum: Security Discussions
---

### Post by kevdog on 2008-04-18
Has anyone integrated port knocking along with an ssh server?  Just read about port knocking this morning:
[http://www.portknocking.org/view/](http://www.portknocking.org/view/)
however only the knock has been transmitted and accepted by the server, how does the knock program then open up the selected ssh port to allow tunneling?

Any ideas or implementations?

---

### Post by HermanAB on 2008-04-18
Xinetd is deprecated.

If you are bothered by script kiddies, add this rule to the end of /etc/rc.d/rc.local:

# General new connection rate limiting for DOS and Brute Force protection
iptables -I INPUT -p TCP -m state --state NEW -m limit --limit 30/minute --limit-burst 5 -j ACCEPT

You could also change /etc/ssh/sshd_config to run SSH on a non-standard port.

Cheers,

Herman

---

### Post by rustybronco on 2008-04-18
> **kevdog said:**
> 
however only the knock has been transmitted and accepted by the server, how does the knock program then open up the selected ssh port to allow tunneling?

Any ideas... It looks like the connection requests are intercepted and passed through to the firewall > step 3 | (A) server process (a port knocking daemon)** intercepts connection attempts** and interprets (decrypts and decodes) them as comprising an authentic "port knock"

---

### Post by kevdog on 2008-04-18
I'm not sure what xinetd was or is .. possibly an explanation.

I take it by you explanation that it had to be a dynamic daemon launcher.

Is port knocking deprecated?  It seems that the general theory is that the port knocking daemon monitors the tcp logs for attempted connections on various ports.  If the port "combination" and data being sent is correct, then the port knocking daemon simply makes a modification to the iptables to allow port 22 or whatever port you want open.  That's seems the basic theory at least.  

Im not a master at Iptables but the following:
iptables -I INPUT -p TCP -m state --state NEW -m limit --limit 30/minute --limit-burst 5 -j ACCEPT

What does this exactly do?  Seems to limit connection attemps.
I do run ssh on a non-standard port, however the concept of port knocking seems to offer even a greater security model.

Seems like this approach maybe abandoned since the last update to the port knocking site was 2004.  A lot of the programs implementing the theory were active between 2001-2004, with now a few number of active projects available.  Any history on port knocking?  Why it died?

---

### Post by kevdog on 2008-04-18
Seems like one implementation of port knocking -- the knockd client is available in the gutsy universe repository.  It looks fairly straight forward.  Can someone tell me the dfference however in this:

TCPFlags = fin|syn|rst|psh|ack|urg

      Only pay attention to packets that have this flag set. When using TCP flags, knockd will IGNORE tcp packets that don't match the flags. This is different than the normal behavior, where an incorrect packet would invalidate the entire knock, forcing the client to start over. Using "TCPFlags = syn" is useful if you are testing over an SSH connection, as the SSH traffic will usually interfere with (and thus invalidate) the knock.

      Separate multiple flags with commas (eg, "TCPFlags = syn,ack,urg"). Flags can be explicitly excluded by a "!" (eg, TCPFlags = syn,!ack). 

What exactly does fin, syn, rst, psh, ack, and urg refer to??  I'm not familiar with this notation?

---

### Post by kevdog on 2008-04-19
After more reading (or wasting more time), I think Im going to move toward using the fwknop Suite as my port knocker client and server, rather than knock and knockd.

[http://www.cipherdyne.org/fwknop/](http://www.cipherdyne.org/fwknop/)

This project seems to be in active development, and uses either a symmetrical or asymmetrical encryption technique.  Clients to allow for the port knocking are available on all platforms which is a big plus.

Hopefully I can figure out how to get this running.

---

### Post by HermanAB on 2008-04-19
There isn't much point in using port knocking.  Xinetd is a kind of port knocking super daemon and is deprecated because people finally realized that it isn't much use.

If you are bothered by script kiddies, use a non-standard port and protect SSH with iptables rate limiting.

If you are really interested in security, read this doc, it has a couple hundred pages of good suggestions and explanations: 
[http://www.nsa.gov/snac/os/redhat/rhel5-guide-i731.pdf](http://www.nsa.gov/snac/os/redhat/rhel5-guide-i731.pdf)

Cheers,

Herman

---

### Post by kevdog on 2008-04-19
I havent used port knockers before, however the ability to execute a command on a remote computer that how no active daemon listening (no listening ports) is really appealing.  Combine the port knock sequence with either Rijndael or GnuPG encryption (and then possibly route the sequence through Tor) -- it seems like an incredible piece of software from both a security point of view,  and convenient point of view.  

That nsa pdf site didn't work for me.  It just kept coming up a blank page
Thanks for the input HermanAB -- I appreciate your experience you bring to this subforum.

---

### Post by HermanAB on 2008-04-19
It has something listening - the port knocking daemon is listening.  So you are really just replacing one piece of software with another.

---

### Post by kevdog on 2008-04-19
Listening --- yes, but no open ports. I cant see how the addition of a port knocker in combination with standard ssh precautions, different port, changes to iptables, would be a bad thing?  It would seem this would be an extra layer of security, particularly if you are using an encrypted knock sequence.

---

### Post by HermanAB on 2008-04-19
Look at it this way:
Something is listening on that port.  Therefore you have n open port to that something.

SSH is secure and trusted by the CSE, DND, NSA, DoD and countless other spooky or dangerous XYZ organizations.  Instead of using SSH only, you introduce a new piece of immature software.  This reduces the security of the system!

Cheers,

Herman

---

### Post by kevdog on 2008-04-20
Not wanting to start an argument but port knocking either monitors the system logs, or monitors the tcp stream directly via libpcap.  No port is physically open in this process.  If the port knocking utility is compromised, at best it would simply open a port for the ssh daemon -- which it seem would be the default configuration anyway.  

But I do see your point about introducing another unproven program into the loop.

---

### Post by netlogic on 2008-04-20
Anyway, I don't want to get tied into this argument, but I find port knocking on ssh to be pointless. If you are that paranoid, use a ssh key with 16 characters passphrase. It will take about 9,500 years with the current technology your average corporation has an access to or they have to steal your key and point a gun to your head.

I really don't understand why people are so against using ssh keys. It is million times stronger than using passwords.

---

### Post by Oldsoldier2003 on 2008-04-20
> **netlogic said:**
> Anyway, I don't want to get tied into this argument, but I find port knocking on ssh to be pointless. If you are that paranoid, use a ssh key with 16 characters passphrase. It will take about 9,500 years with the current technology your average corporation has an access to or they have to steal your key and point a gun to your head.

I really don't understand why people are so against using ssh keys. It is million times stronger than using passwords.

personally I am all for ssh keys, in fact my machine doesn't accept password logins. however you have to admit that ssh keys ads a layer of support getting the users properly configured, and is no more secure than a strong password when physical security is lax at the user end.

---

### Post by netlogic on 2008-04-20
> **Oldsoldier2003 said:**
> personally I am all for ssh keys, in fact my machine doesn't accept password logins. however you have to admit that ssh keys ads a layer of support getting the users properly configured, and is no more secure than a strong password when physical security is lax at the user end.

I don't think you are thinking in the perspective of network design. Why would an average user need ssh access? Average LAN users only need NFS or Samba. Only the developers will need to interact with application servers. If a developer can't understand the simple concept of key access, I say fire him. 

It doesn't matter what protocol a person uses. If you have a physical access every protocols in this planet are comprised, so I don't really see your argument. Management stations should have /home encrypted. If it doesn't, I feel sorry for the company. The company's security is already probably comprised. It wouldn't matter it is xBSD, OSX, Linux, or Windows.  I know I annoying repeated myself for the last year, all management stations should have /home encrypted.

---

### Post by kevdog on 2008-04-20
Im not following your logic...average LAN users not needing ssh access.  Lets see...I run my own home network...have files at work (personal files, not company files)..backup nightly to home server using unison/ssh. Proxy connections tunneled through ssh when on the road using airport networks.

I guess I dont follow your logic about average network users not needing ssh access.

As far as /home being encrypted...What does this have to do with a port knocking utility?

---

### Post by netlogic on 2008-04-20
> **kevdog said:**
> Im not following your logic...average LAN users not needing ssh access.  Lets see...I run my own home network...have files at work (personal files, not company files)..backup nightly to home server using unison/ssh. Proxy connections tunneled through ssh when on the road using airport networks.

I guess I dont follow your logic about average network users not needing ssh access.

As far as /home being encrypted...What does this have to do with a port knocking utility?

I am speaking in a term of Enterprise solution. Most companies do follow some NSA guidelines for deploying Linux in their enterprise.  You also have not clearly defined this was for your home network. If this is your home server, go right ahead. You can use anything you want. It is your home network for experimenting, education, and enjoyment. I am saying, no corporations will even bother with this idea. It is adding a layer that will not produce better security outcome. Since this is your home network, go have fun. 

why /home? Where are you going to put your keys?

---

### Post by kevdog on 2008-04-21
I have whole disk LUKS encryption.  Not sure if this is what you mean.

Per the author, the sole purpose of the fwknop port knocker utility is to avoid zero-day and buggy patch exploits.  I'm sure these really don't happen but to an extremely minor degree, however if you are going to argue about the uselessness of this program -- at least argue against it on the merits it claims to provide the end user.

If it does deter from zero day and botched patch updates, then your statement "It is adding a layer that will not produce better security outcome" may not entirely be correct.

But yes, I agree with you that adding this in a corporate environment may not be the best thing to do.  Solutions involving security often take time-tested measures, and use of this port-knocking utility I don't believe is time testing -- except for use by black-hats who have used this exploit in the chrootkits for years -- except I guess that really wasn't for security but rather exploitation purposes.

---

### Post by netlogic on 2008-04-21
> **kevdog said:**
> 

Not necessary.  Remember attack doesn't always equal to hack. Sometimes, hack isn't even technology, so it becomes a bit pointless.

> I'm sure these really don't happen but to an extremely minor degree, however if you are going to argue about the uselessness of this program -- at least argue against it on the merits it claims to provide the end user.



Great point. It will not add anything to your protection. This concept has been around on few older routers in the past.

[QUOTE]
and use of this port-knocking utility I don't believe is time testing -- except for use by black-hats who have used this exploit in the chrootkits for years -- except I guess that really wasn't for security but rather exploitation purposes.

Why would you assume Blackhats are programmers? They will use floppy drive and do the dumpster dive if they have to.

---

### Post by netlogic on 2008-04-21
My strange vibe tells me you are going to attack back with an argument. Ok. I will spend 10 minutes why I am against it. I guess I do owe you an explanation. My response does come off very negative if it doesn't include the explanation. 

First of all, when you implement your port knocking, keep it a secret. These days, you can easily look for certain service users by using google to search for certain blogs. It is matter of time figuring out which domain name they use. Don't announce to everyone you have this feature. It defeats the entire purpose. Now, the attacker can focus his/her attack based around your information. 

If you aren't encrypting your port knocking method, it would be incredibly trivial to bypass it with a simple brute force knocking. Even you  use an encryption layer for it, it is obvious the strength is only equal to 40bits, which is also trivial. 

Also, you are letting port knocker start the challenge response, which makes it easier and vulnerable to man in the middle attack. It will be easier for someone to plan those steps of attack.

Anyway, you aren't the only one who looked into this. I am sorry for the short answers. This app isn't even written in C. It is simpler and stronger to just manipulate the firewall for ssh and use the key authentication.

---

### Post by HermanAB on 2008-04-21
I got to second Netlogic's logic.

Port knocking doesn't really buy you any security.  For home use - have fun though.

---

### Post by Oldsoldier2003 on 2008-04-21
> **netlogic said:**
> I don't think you are thinking in the perspective of network design. Why would an average user need ssh access? Average LAN users only need NFS or Samba. Only the developers will need to interact with application servers. If a developer can't understand the simple concept of key access, I say fire him. 

It doesn't matter what protocol a person uses. If you have a physical access every protocols in this planet are comprised, so I don't really see your argument. Management stations should have /home encrypted. If it doesn't, I feel sorry for the company. The company's security is already probably comprised. It wouldn't matter it is xBSD, OSX, Linux, or Windows.  I know I annoying repeated myself for the last year, all management stations should have /home encrypted.
To a certain extent I agree with you. I partly agree that the average user doesn't need ssh access, but I consider webmasters "average users" , note that I didn't say application developers :) 

In many companies there are cost cutting measures that often conflict with a tighter security model. I do agree that encryption of home directories is essential, but I also feel that proper user education is more important. Unfortunately security and IT guys often get shut down when security interferes with production.

 When I was talking about physical access some simple examples come to mind: for passwords, the old sticky note or slip of paper under the keyboard was my biggest nemesis when I was an administrator on a DoD network. As far as ssh keys, the guy that neglects to lock his workstation when he goes for a coffee or heads to lunch comes to mind. Though security folks are mostly considered to be the line  in the sand against the bad hacker dudes, realistically most breaches of security and theft of proprietary data come from within an organization.

I feel that complete physical security is something that is not practical in your average production environment.  The need for access often supersedes the need for complete security, IE elctro magnetic shielding, controlled single user access with case tampering detection, physical control of removable storage media and restriction of introduction of said storage media to the secure site and of course no internet access...


I guess in the end what I'm saying is simply that realistically speaking, security is only as good as management allows. There will always be the tradeoff between security and seamless usability. Security guys and management guys rarely see eye to eye because of the increased training overhead and productivity issues that high security impose on a business.

---

### Post by kevdog on 2008-04-21
> Even you use an encryption layer for it, it is obvious the strength is only equal to 40bits, which is also trivial. 


Not following this statement (although I get the rest of your arguments).  fwknop when implemented with gpg keys (the limit in this particular application is 2048 bit keys) for surpasses a 40 bit in terms of security.  In fact, to my knowledge 2048 bit RSA keys using a rijndael symmetric cipher have never been broken (at least not publically, within the nsa is another matter).

I contacted the author of the fwknop program.  Somethings in terms of implementation are definitley lacking in terms of the documentation.  Hopefully when I get this up and running I'll post a how-to for others to try in a "home networking" environment.

---

### Post by netlogic on 2008-04-21
> **kevdog said:**
> Not following this statement (although I get the rest of your arguments).  fwknop when implemented with gpg keys (the limit in this particular application is 2048 bit keys) for surpasses a 40 bit in terms of security.  In fact, to my knowledge 2048 bit RSA keys using a rijndael symmetric cipher have never been broken (at least not publically, within the nsa is another matter).

I contacted the author of the fwknop program.  Somethings in terms of implementation are definitley lacking in terms of the documentation.  Hopefully when I get this up and running I'll post a how-to for others to try in a "home networking" environment.

what?
8*5=40bits for port knocking encryption
when did i mentioned ssh was 40bit?
oh... it is possible to encrypt your knocks. 
Hmm...I know all about RSA keys. If you multiple by passphrase bit length, your technical  encryption is higher than 2048 for a ssh key.

---

### Post by kevdog on 2008-04-21
I would hate to memorize a passphrase that was equivalent to a 2048 bit key -- that would be quite difficult.  And again, with key use you bypass that whole keylogger threat.

---

### Post by netlogic on 2008-04-21
> **kevdog said:**
> I would hate to memorize a passphrase that was equivalent to a 2048 bit key -- that would be quite difficult.  And again, with key use you bypass that whole keylogger threat.

Right on Dog...
You will be more chilling with the higher bits.

---

