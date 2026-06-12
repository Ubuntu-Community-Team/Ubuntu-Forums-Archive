---
title: "Help understanding Firestarter event log"
date: 2005-04-13
forum: Server Platforms
---

### Post by shakin on 2005-04-13
I'm on a network and Windows computers on the LAN are often hitting my Ubuntu box with SMB requests. Is this a normal part of Windows' operation (maybe part of a netbios scan) or is it likely that something is wrong with those Windows boxes?

The SMB traffic is on UDP ports 137 and 138. I'm normally being hit 3 or 4 times every minute and the incoming hits are spread out evenly between all 10 or so Windows computers on the network.

Thanks.

---

### Post by idn on 2005-04-13
Yeah this is happening on my network as well, any ideas?

---

### Post by underworld on 2005-04-13
[QUOTE=idn]Yeah this is happening on my network as well, any ideas?[/QUOTE]

Windows does like to broadcast  ;-)

Nothing to worry about.


Greetings,
Daniel

---

### Post by shakin on 2005-04-13
[QUOTE=underworld]Windows does like to broadcast  ;-)

Nothing to worry about.


Greetings,
Daniel[/QUOTE]

Thanks. I'm glad this network isn't overrun by trojans :)

What I also find weird is that while my workstation (10.53.25.154) is showing the logs above, my dev server (10.53.25.155) is not. My last Firestarter event on the dev server was on April 6. Weird.

---

### Post by youlikeicecream on 2005-10-21
as the other members have said, it's nothing to worry about ... basically every windows machine on the network have a delegation process for electing a 'Master Browser'. The master browser maintains information about all the machines on the network and when queried will give out the list of workgroups and shares. Thats why every couple of minutes the master browser (usually a domain controller) will talk to every machine on the network .. also any machine can become a Master Browser at any time .. thus pissing off Linux users who have no permission to contact windows machines that become master browsers (This happens on Domain and workgroup networks).

hope this info sheds light on the subject

Mike :)

---

