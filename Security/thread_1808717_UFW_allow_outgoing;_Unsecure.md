---
title: "UFW allow outgoing; Unsecure?"
date: 2011-07-20
forum: Security
---

### Post by Hatsune Miku on 2011-07-20
Hey everyone, quick question. I have a minecraft server running on a P4 box running Ubuntu server 11.04 64bit. Now would it be secure, if i allowed ufw to allow outgoing? Or would this be a huge flaw someone could exploit? Thanks!

---

### Post by Dangertux on 2011-07-20
Allowing outgoing traffic isn't a huge vulnerability per se. 

However if the services you are running have a vulnerability that could be exploited to yield code execution you would have no protective measure against a reverse shell being spawned on your system. Since by your system would be initiating the connection to a remote server the resulting incoming traffic would be considered RELATED by iptables. So the attacker would in fact gain the shell. 

So in terms of server hardening limiting outgoing traffic in a production environment is wise albeit in terms of a gameserver sometimes difficult.

---

### Post by Hatsune Miku on 2011-07-20
> **Dangertux said:**
> Allowing outgoing traffic isn't a huge vulnerability per se. 

However if the services you are running have a vulnerability that could be exploited to yield code execution you would have no protective measure against a reverse shell being spawned on your system. Since by your system would be initiating the connection to a remote server the resulting incoming traffic would be considered RELATED by iptables. So the attacker would in fact gain the shell. 

So in terms of server hardening limiting outgoing traffic in a production environment is wise albeit in terms of a gameserver sometimes difficult.


I Thought as much, do you know what ports i need to open for java to verify minecraft characters?

---

### Post by Dangertux on 2011-07-20
Not off the top of my head I am not particularly familiar with the Minecraft server. I am sure the documentation or google could give you that info better than I.

---

### Post by The Cog on 2011-07-21
I don't see much harm in allowing outgoing connections. If you can't trust the apps that are running on your machine, then it's probably game over anyway.

Try port 25565. My son runs a minecraft server, and that's the only port that's allowed inbound.

---

### Post by deesto on 2011-07-22
> **vvk125 said:**
> Hai  i want the details of how many time and which type of usb stick used into the pc.  Because i went to audit the cyber security.  so pl how deduct the details, help me
Uhm, what?  And what does this have to do with UFW?

---

### Post by Hatsune Miku on 2011-07-24
> **The Cog said:**
> I don't see much harm in allowing outgoing connections. If you can't trust the apps that are running on your machine, then it's probably game over anyway.

Try port 25565. My son runs a minecraft server, and that's the only port that's allowed inbound.

Already opened

Thanks everyone for help, did some more research and i should be fine.

---

