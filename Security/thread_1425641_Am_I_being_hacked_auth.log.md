---
title: "Am I being hacked? auth.log"
date: 2010-03-09
forum: Security
---

### Post by Neezer on 2010-03-09
Hi,

I have something in my auth.log on my server at home that bothers me. 

```

Mar  7 16:04:46 server sshd[2916]: Address 192.168.1.102 maps to lappy.local, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!

```

I have no idea what this means, but it worries me. Could it have something to do with my signing on through ssh with my wired connection and logging out after unplugging my laptop and using wireless?

---

### Post by CharlesA on 2010-03-09
How are you authenticating?

It looks like it's doing a reverse DNS lookup to see if that machine is really what it says it is.

---

### Post by Neezer on 2010-03-09
I am connecting with an RSA key...

Is that what you meant?

I also recently added 
```

server     192.168.1.105


```

I added that to /etc/hosts or something like that so now I can just do ssh server

---

### Post by CharlesA on 2010-03-09
Yeah, that's what I meant. It does sound like it's doing a reverse dns lookup.

Check [here]("http://www.electrictoolbox.com/reverse-mapping-possible-break-in-ssh/").

---

### Post by Neezer on 2010-03-09
So you're saying it is fine? I think it is....because the time stamps on it are matching the approximate times that I did this...On another note, I have no idea how someone could get in anyways, the only port I forward is my 2222 for ssh, and it has a 4096 bit rsa key...

---

### Post by CharlesA on 2010-03-09
As long as you locked everything down, you should be fine. If the timestamps match a known connection attempt that you made, then you should be good to go.

---

### Post by doas777 on 2010-03-09
I think that it is getting lappy.local from your hosts file (which would return a loopback like 127.0.0.1) and since it doesn't resolve as 192.168.1.102 it logs the warning.

---

### Post by noway2 on 2010-03-10
Also keep in mind that your 192.168.1.X address range is local to your LAN, which means that the login was from your LAN.  If it were a crack attempt, the address would most likely be external.  That is unless you are using wireless and they were able to establish a connection, but then you would likely get a host name that you didn't recognize.

---

### Post by moody_mark on 2010-03-10
I would second the theory its trying to do a reverse lookup. We have some Linux boxes at my work who send out a "logwatch" report daily and I often see messages like this (IPs and domains changed of course for the example);

```
--------------------- SSHD Begin ------------------------ 

 Users logging in through sshd:
    oracle:
       1.2.3.4 (dhcp-somewhere.blab.blab.com): 1 time
       2.3.4.5 (dhcp-emea-uk-blah-blah.vpn.here.com): 1 time
 
 **Unmatched Entries**
 reverse mapping checking getaddrinfo for dhcp-emea-uk-blah-blah.vpn.here.com failed - POSSIBLE BREAK-IN ATTEMPT! : 1 time(s)

 ---------------------- SSHD End ------------------------- 

```

The user using the above on 2.3.4.5 connected via a vpn, I knwo that because it was me, and the reverse IP is one that is allocated by the vpn box and as such doesnt map to the vpn box at least not in the /etc/hosts file of this machine.

Someone correct me here, but I guess if I added an entry into the hosts file then this message could be avoided.

---

