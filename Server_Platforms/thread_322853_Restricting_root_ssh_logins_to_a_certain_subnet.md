---
title: "Restricting root ssh logins to a certain subnet"
date: 2006-12-21
forum: Server Platforms
---

### Post by Tyler_Durden on 2006-12-21
Hi,
I have been search the web for hours no to find out how to do the following thing. I simply want to restrict ssh root logins to our firm's subnet. I would like to write something like this in /etc/ssh/sshd_config:

DenyUsers root@!(192.168.123.*)

However, this does not work, as the sshd_config only allows the pattern ? and *. Now way to specify something like "user that does not connect from a certain host".

Does anybody know how to handle that?

Many thanks in advance.

So long,
CU Tyler

---

### Post by Sir_Yaro on 2006-12-21
try to ban this user on the firewall

---

### Post by Tyler_Durden on 2006-12-22
Hi,

> **Sir_Yaro said:**
> try to ban this user on the firewall

hmm... I'm not sure if that works. Where does the firewall know that the incoming ssh connection is someone who wants to connect as root on a machine?

Is there no way to do this in the sshd.conf?

So long,
CU Tyler

---

### Post by jexxie on 2006-12-22
Hi there,

Sorry to say, there's no way to do this -- only just restricting root access globally, or not.

Probably not what you're looking for, but you can always add user accounts that can have passwordless sudo access, or even add a 'sudo su -' into the user's .bash_login so he's su'd to root.

---

### Post by chrisfay on 2006-12-22
What about using /etc/hosts.allow and /etc/hosts.deny via TCP wrappers?

---

### Post by MJN on 2006-12-22
I could be wrong but I would've thought that any attempts to restrict/customise access on a per-user basis would **have** to be done by SSHD itself as to any other protocol at a lower level the connection is encrypted and hence nothing else has the opportunity would know which user is trying to login.
 
Hence that leaves the SSHD config... and as far as I am aware there is nothing that provides what you want to do (that I've seen anyway - it might be worth you reading through the man page thoroughly).
 
Perhaps you need to think out of the box and decide what it is you're trying to do, or rather how much security you 'need'. Do you really need remote root login, from anywhere? If so, is it to perform general jobs (if so why not login in as a normal user and use sudo) or particular tasks (e.g. remote backups) - if the latter then you could use the 'forced commands only' function. Furthermore, if you use certificate-based authentication then you can safely ignore dictionary attacks.... Do you need any more security than all of this?
 
Mathew

---

### Post by chrisfay on 2006-12-22
> I would've thought that any attempts to restrict/customise access on a per-user basis would have to be done by SSHD itself 

But isn't the initial request made by the client before sending any data non-encrypted? I would think it would be possible to limit based on an IP or subnet apart from ssh in a similar format to [DenyHosts]("http://denyhosts.sourceforge.net/")....Only preempting the connection 'before' a failed attempt rather than afterwards.

---

### Post by MJN on 2006-12-22
I believe the tunnel is established before any username (and of course password) credentials are transferred. If you run ssh with the -v option you'll see this is the case (or indeed run a packet sniffer and you won't ever see the usename on the wire).
 
I'm not at my PC right now so can't check for certain... if I was then I'd see one way or another and then could make my assumptions sound a bit more like authoritive facts! ;)
 
Mathew

---

### Post by chrisfay on 2006-12-22
> I believe the tunnel is established before any username (and of course password) credentials are transferred. If you run ssh with the -v option you'll see this is the case (or indeed run a packet sniffer and you won't ever see the usename on the wire).

I think in that respect we're saying the same thing.  I'm referring to blocking the tcp connection prior to even allowing comunication with the ssh daemon in the first place. I'm not positive if this would be something integrated within ssh via libwrap or via tcpd but, I'm pretty sure its doable one way or the other.

---

### Post by MJN on 2006-12-22
I see what you mean now. However, I don't think it would be possible to restrict access based on IP address **for root only** as there is no knowledge outside of SSH of who is logging in hence any IP restrictions would have to apply to all users.
 
Mathew

---

### Post by chrisfay on 2006-12-22
Ahhh....I see. 

In that case, check this out:
[http://www.cyberciti.biz/tips/openssh-root-user-account-restriction-revisited.html](http://www.cyberciti.biz/tips/openssh-root-user-account-restriction-revisited.html)

---

### Post by Tyler_Durden on 2006-12-22
Hi,

> **chrisfay said:**
> Ahhh....I see. 

In that case, check this out:
[http://www.cyberciti.biz/tips/openssh-root-user-account-restriction-revisited.html](http://www.cyberciti.biz/tips/openssh-root-user-account-restriction-revisited.html)

this sounds promising! Many thanks.

So long,
CU Tyler

---

### Post by MJN on 2006-12-22
Good find!
 
Maybe we ought to all remove our posts and make it look like the answer was known all along! ;)
 
Mathew

---

### Post by Tyler_Durden on 2006-12-22
Hi,
this works perfect. The following line does exactly what I want: restrict root logins to localhost and all other machines of my network only.

-: root : ALL EXCEPT LOCAL 192.168.123.

Hm... I consider this is pretty handy stuff for all those sysadmins out there.

So long,
CU Tyler

---

### Post by chrisfay on 2006-12-22
> Maybe we ought to all remove our posts and make it look like the answer was known all along! 

Good call...:p 

> this works perfect. The following line does exactly what I want:
Glad it helped...

---

