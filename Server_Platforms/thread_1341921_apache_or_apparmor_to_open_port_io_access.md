---
title: "apache or apparmor to open port io access"
date: 2009-11-30
forum: Server Platforms
---

### Post by shred_eng on 2009-11-30
hi, im using ubuntu 9.04 server for a website and game server. i want to allow clients to use port 27977 so i guess that would be in and out access for the game server.

at the moment i have added Listen 27977 to the /etc/apache2/ports.conf file like this:

NameVirtualHost *:80

Listen 80
Listen 27977

but when i join the game server my connection disconnects after a minute or so, this is using my outside ip as seen to the world, but if i connect via local network using 192.168.1.64:27977 there is no connection problems.

there is apparmor installed as well so im thinking perhaps this is where i define access to port 27977 as i dont like the look of what i did by adding 27977 to the NameVirtualHost section of ports.conf, somehow it just seems like the wrong thing to do, at least where it is at the moment.

so how would i get this to work in the safest way?

thanks,

---

### Post by cdenley on 2009-11-30
Your "game server" runs through apache?
```

sudo lsof -ni :27977

```

---

### Post by shred_eng on 2009-11-30
good question cdenley, i assumed that it must but perhaps not.

this is what i got from ; sudo lsof -ni :27977

etded.x86 3396 etserver 35u ipv4 10021 udp *:27977 

then the rest starts with: apache2 then similar stuff to the line above but with www-data as the user apart from one entry with the owner root then ends with :   tcp *:27977 (Listen)

hope this is clear enough, i couldnt remember how to pipe the output to a file so that i could copy and paste it here.

so it doesnt really look like apache has anything to do with it or does it? :confused:

---

### Post by cdenley on 2009-11-30
> **shred_eng said:**
> 
so it doesnt really look like apache has anything to do with it or does it?

No. In fact, apache and your game server can't both listen on that port. One will fail. It sound like you have a routing (port forwarding) issue. Your server sounds like it is working properly.

---

### Post by shred_eng on 2009-11-30
yes, the server is running ok, i have the port forwarding on the router pointing at the computer with the server running on it but i dont think it is limited to only port 80, 

so im inclined to think that apparmor  needs a rule setting but im not too sure how to set one,  any ideas?

thanks,

---

### Post by cdenley on 2009-11-30
> **shred_eng said:**
> yes, the server is running ok, i have the port forwarding on the router pointing at the computer with the server running on it but i dont think it is limited to only port 80, 

so im inclined to think that apparmor  needs a rule setting but im not too sure how to set one,  any ideas?

thanks,

Apparmor doesn't restrict an application until you create or install a profile for it. Also, it doesn't restrict network access based on IP. Unless you configured the firewall (iptables) to filter traffic on port 27977 unless it is coming from your LAN network, you have a networking issue.

---

### Post by shred_eng on 2009-11-30
hmm, in that case, i'm stumped for the time being :)

thanks for the replys,

---

### Post by Sporkman on 2009-12-01
FYI, if you do in fact have an apparmor profile in effect for an application, and that application violates its profile constraints, the violation will be reported in /var/log/syslog .

---

