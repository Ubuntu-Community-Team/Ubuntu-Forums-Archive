---
title: "understanding auth.log"
date: 2010-09-23
forum: Security
---

### Post by NertSkull on 2010-09-23
So its probably paranoia but I figure safe to just check with smarter people than I real quick.

I have this line in my auth.log that seems like it could be out of place to me.  

```
Sep 21 05:45:53 MY_MACHINE sshd[16245]: Connection from 76.127.218.159 port 41713
Sep 21 05:45:53 MY_MACHINE sshd[16245]: Invalid user pub from 76.127.218.159
Sep 21 05:45:53 MY_MACHINE sshd[16247]: Connection from 76.127.218.159 port 41772
Sep 21 05:45:54 MY_MACHINE sshd[16247]: Invalid user pub from 76.127.218.159
Sep 21 05:45:54 MY_MACHINE sshd[16249]: Connection from 76.127.218.159 port 41833
Sep 21 05:45:55 MY_MACHINE sshd[16249]: Invalid user thomas from 76.127.218.159
Sep 21 05:45:55 MY_MACHINE sshd[16251]: Connection from 76.127.218.159 port 41950
Sep 21 05:45:55 MY_MACHINE sshd[16251]: Invalid user thomas from 76.127.218.159
```


I get a LOT of these lines.  With lots of different IPs, different user names (i.e. thomas is not my username, it just goes through lots of names).

I get different Ports, and different number after the sshd , etc.

I'm reading about fail2ban (or potentially just iptables filtering) but before I set that up I'd like know more what those lines mean.

FIRST and FOREMOST, I'm assuming no one is actually getting into my machine (since I use ssh keys and no password authentication and they haven't even got the username right).  But I want to make sure thats a safe assumption.

SECOND, what is the number after the sshd?  Its different each time.  Is that just the process ID number?  or what is it?

THIRD, I have my ssh open on port 22 (only port I can use from school unfortunately).  But why all the connections to other ports?  Its like its trying the port but it just has a bad user.  I would think the fact those ports are closed it wouldn't even try to check the user, just immediately deny.  But instead it looks like it attempts on those ports.  Whats the deal with that?

FOURTH, is setting up fail2ban sufficient? (along with already set up ssh_keys and no password and no root login?)


The reason I ask is because I have had other lines in the past that look like this.

```
Sep 19 11:35:41 MY_MACHINE sshd[11261]: Invalid user arun from 111.93.132.233
Sep 19 11:35:42 MY_MACHINE sshd[11263]: Connection from 111.93.132.233 port 20814
Sep 19 11:35:46 MY_MACHINE sshd[11263]: reverse mapping checking getaddrinfo for static-233.132.93.111.tataidc.co.in [111.93.132.233] failed - POSSIBLE BREAK-IN ATTEMPT!
Sep 19 11:35:46 MY_MACHINE sshd[11263]: Invalid user arun from 111.93.132.233
Sep 19 11:35:50 MY_MACHINE sshd[11265]: Connection from 111.93.132.233 port 34406
Sep 19 11:35:51 MY_MACHINE sshd[11265]: reverse mapping checking getaddrinfo for static-233.132.93.111.tataidc.co.in [111.93.132.233] failed - POSSIBLE BREAK-IN ATTEMPT!
Sep 19 11:35:51 MY_MACHINE sshd[11265]: Invalid user admin from 111.93.132.233
Sep 19 11:35:52 MY_MACHINE sshd[11267]: Connection from 111.93.132.233 port 19144
Sep 19 11:35:54 MY_MACHINE sshd[11267]: reverse mapping checking getaddrinfo for static-233.132.93.111.tataidc.co.in [111.93.132.233] failed - POSSIBLE BREAK-IN ATTEMPT!
Sep 19 11:35:54 MY_MACHINE sshd[11267]: Invalid user admin from 111.93.132.233
Sep 19 11:35:54 MY_MACHINE sshd[11269]: Connection from 111.93.132.233 port 3331
Sep 19 11:35:56 MY_MACHINE sshd[11269]: reverse mapping checking getaddrinfo for static-233.132.93.111.tataidc.co.in
```

Those lines clearly look different from the ones above.  Why the difference?  Obviously seeing something that says possible break-in attempt kind of made me worried.  But I gotta admit I've felt relatively secure saying, let them try, I'm using ssh_keys and should be good.

Still, I'd like to understand as much as I can to keep me as safe as possible.

Thanks all for the help.

---

### Post by CharlesA on 2010-09-23
> **NertSkull said:**
> So its probably paranoia but I figure safe to just check with smarter people than I real quick.

I have this line in my auth.log that seems like it could be out of place to me.  

```
Sep 21 05:45:53 MY_MACHINE sshd[16245]: Connection from 76.127.218.159 port 41713
Sep 21 05:45:53 MY_MACHINE sshd[16245]: Invalid user pub from 76.127.218.159
Sep 21 05:45:53 MY_MACHINE sshd[16247]: Connection from 76.127.218.159 port 41772
Sep 21 05:45:54 MY_MACHINE sshd[16247]: Invalid user pub from 76.127.218.159
Sep 21 05:45:54 MY_MACHINE sshd[16249]: Connection from 76.127.218.159 port 41833
Sep 21 05:45:55 MY_MACHINE sshd[16249]: Invalid user thomas from 76.127.218.159
Sep 21 05:45:55 MY_MACHINE sshd[16251]: Connection from 76.127.218.159 port 41950
Sep 21 05:45:55 MY_MACHINE sshd[16251]: Invalid user thomas from 76.127.218.159
```

It's just bots trying to brute force your password to get SSH access.

> I get different Ports, and different number after the sshd , etc.

The port listed in auth.log is the source port, which is a random port between 1024 and 65535.. something.

> I'm reading about fail2ban (or potentially just iptables filtering) but before I set that up I'd like know more what those lines mean.

fail2ban is decent, but I just use two SSH rules to help slow down bots. I use keys and well so there is no password to crack.

> FIRST and FOREMOST, I'm assuming no one is actually getting into my machine (since I use ssh keys and no password authentication and they haven't even got the username right).  But I want to make sure thats a safe assumption.

That's a pretty good assumption. Unless someone got a hold of yer private key, knew your passphrase and know what you need to connect to, it's highly unlikely.

> SECOND, what is the number after the sshd?  Its different each time.  Is that just the process ID number?  or what is it?

I think it's the PID of SSH, but I am not 100% sure.

> THIRD, I have my ssh open on port 22 (only port I can use from school unfortunately).  But why all the connections to other ports?  Its like its trying the port but it just has a bad user.  I would think the fact those ports are closed it wouldn't even try to check the user, just immediately deny.  But instead it looks like it attempts on those ports.  Whats the deal with that?

It's logging the source port, not the destination port. The destination port never changes.

> FOURTH, is setting up fail2ban sufficient? (along with already set up ssh_keys and no password and no root login?)

It depends on what you want to do tbh. I don't care able logging ip addresses so I just drop any attempts to connect that hit more then 4 times a minute.

I use this in an iptables-save file. I use iptables-restore at boot to apply it.

```
# 10 minute lockout if trying to bruteforce
-A INPUT -p tcp --dport 22 -m state --state NEW -m recent --set --name  SSH --rsource
-A INPUT -m recent --update --seconds 600 --hitcount 8 --rttl --name SSH  --rsource -j DROP
```

> The reason I ask is because I have had other lines in the past that look like this.

```
Sep 19 11:35:41 MY_MACHINE sshd[11261]: Invalid user arun from 111.93.132.233
Sep 19 11:35:42 MY_MACHINE sshd[11263]: Connection from 111.93.132.233 port 20814
Sep 19 11:35:46 MY_MACHINE sshd[11263]: reverse mapping checking getaddrinfo for static-233.132.93.111.tataidc.co.in [111.93.132.233] failed - POSSIBLE BREAK-IN ATTEMPT!
Sep 19 11:35:46 MY_MACHINE sshd[11263]: Invalid user arun from 111.93.132.233
Sep 19 11:35:50 MY_MACHINE sshd[11265]: Connection from 111.93.132.233 port 34406
Sep 19 11:35:51 MY_MACHINE sshd[11265]: reverse mapping checking getaddrinfo for static-233.132.93.111.tataidc.co.in [111.93.132.233] failed - POSSIBLE BREAK-IN ATTEMPT!
Sep 19 11:35:51 MY_MACHINE sshd[11265]: Invalid user admin from 111.93.132.233
Sep 19 11:35:52 MY_MACHINE sshd[11267]: Connection from 111.93.132.233 port 19144
Sep 19 11:35:54 MY_MACHINE sshd[11267]: reverse mapping checking getaddrinfo for static-233.132.93.111.tataidc.co.in [111.93.132.233] failed - POSSIBLE BREAK-IN ATTEMPT!
Sep 19 11:35:54 MY_MACHINE sshd[11267]: Invalid user admin from 111.93.132.233
Sep 19 11:35:54 MY_MACHINE sshd[11269]: Connection from 111.93.132.233 port 3331
Sep 19 11:35:56 MY_MACHINE sshd[11269]: reverse mapping checking getaddrinfo for static-233.132.93.111.tataidc.co.in
```

Those lines clearly look different from the ones above.  Why the difference?  Obviously seeing something that says possible break-in attempt kind of made me worried.  But I gotta admit I've felt relatively secure saying, let them try, I'm using ssh_keys and should be good.

This chunk has dns lookups enabled, so it is trying to do a reverse dns lookup to verify the ip address. If it cannot verify it, it spits up a warning.

---

### Post by NertSkull on 2010-09-24
Thats one of the most useful replies I've ever had to a post and I seriously appreciate it.

I think I'm slowly getting the hang of security and logs.

One final question about this stuff.

Right now my SSH keys are passwordless.  Is that a big deal?  Should I add a password.

I kind of was under the impression that as long as the key is never compromised then a password doesn't do anything.

That the password really is just to slow down the use of a key that may be stolen?

Is that right? Or is there a security risk by having a passwordless key that I missed while reading things?

thanks again!!

---

### Post by CharlesA on 2010-09-24
> **NertSkull said:**
> 
Right now my SSH keys are passwordless.  Is that a big deal?  Should I add a password.

The problem with passphrase-less keys, is that if someone gets a hold of your key, whoever has it will not be prompted for a password when connecting.

> I kind of was under the impression that as long as the key is never compromised then a password doesn't do anything.

That the password really is just to slow down the use of a key that may be stolen?

It really depends. Like I said above, if the key doesn't have a passphrase on it, and someone gets a hold of it, they will have access to your machine.

> Is that right? Or is there a security risk by having a passwordless key that I missed while reading things?


See above. I always add a passphrase to any ssh keys I create. Just make sure that the passphrase isn't a dictionary word and is fairly long - 15 to 20 characters.

Just to note: I'm not taking into account that they won't have your username, but it's still a security risk imo.

---

### Post by bodhi.zazen on 2010-09-24
You can use ssh agent to add you ssh keys to memory so you do not need to enter a password each time.

See man ssh-add

```
ssh-add -i ~/.ssh/your_key
```

---

### Post by CharlesA on 2010-09-24
Thanks! I didn't know about that.

---

### Post by bodhi.zazen on 2010-09-24
You might like ssh-add -x =)

---

### Post by bodhi.zazen on 2010-09-24
FYI: Just put this page up :

[http://bodhizazen.net/Tutorials/ssh_keys/](http://bodhizazen.net/Tutorials/ssh_keys/)

---

### Post by CharlesA on 2010-09-24
> **bodhi.zazen said:**
> FYI: Just put this page up :

[http://bodhizazen.net/Tutorials/ssh_keys/](http://bodhizazen.net/Tutorials/ssh_keys/)

Nice write up. =D>

---

### Post by bodhi.zazen on 2010-09-24
> **CharlesA said:**
> Nice write up. =D>

Thank you for reviewing that page. Hoping to show some people how to use keys =)

---

### Post by CharlesA on 2010-09-24
> **bodhi.zazen said:**
> Thank you for reviewing that page. Hoping to show some people how to use keys =)

I was more interested in trying to figure out why ssh-agent was spitting back errors and that was on there too. :)

---

