---
title: "Securing a Server (noob)"
date: 2007-11-21
forum: Server Platforms
---

### Post by ctlw83 on 2007-11-21
I'm no security expert but, being in a field where I get calls regarding stolen passwords and hacking all the time, I think security would be very important to have on my server.

I'm going to be running 3 or more sites, and possibly a mail client as well.  I figured I should probably configure the security now, while the server isn't fully working (see thread: [http://ubuntuforums.org/showthread.php?t=618566](http://ubuntuforums.org/showthread.php?t=618566)) rather than wait and then get hacked.

I do use separate MySQL accounts for each site and also have a good password scheme, it is secures, and easy to remember.

But, other than that I am pretty clueless.  I want to make it so I can access the computer through its local router IP and also so that people can access the sites themselves (when they are working).

Thanks
God Bless,
Chris

---

### Post by mellowd on 2007-11-21
Is this a corporate server or a home server? Also, with either of the two, what kind of network devices will you have in front of it?

---

### Post by ctlw83 on 2007-11-21
Home server but done with server version of ubuntu.  I do have a router in front of it and currentl;y have DMZ open for that machine.  I can change that though so port 80, 110 and 25 requests get routed to that computer.  I also have the DSL modem which was a pain but, I've since fixed that...

---

### Post by ctlw83 on 2007-11-21
I just turned off DMZ and have port forwarding set up just for ports 80, 110, 25, and the SQL port (forgot which one but, it was already in there)

---

### Post by mellowd on 2007-11-21
I would keep the server in the DMZ. That way you can lock the DMZ zone with different policies as opposed to your regular lan

---

### Post by ctlw83 on 2007-11-21
Not sure if I have that option in my router.  Plus, that would, in theory, leave everything open on the server, wouldn't it?

---

### Post by mellowd on 2007-11-21
No, you can use the DMZ as a seperate part on your network and have different security policies on the dmz as opposed to your regular lan. It depends on your router/firewall though

---

### Post by ctlw83 on 2007-11-21
Yeah, I think my router isn't quite that sophisticated.  However, it is working the way that I want it to with the port forwarding, so I have a nice solid firewall against outside intruders.

---

