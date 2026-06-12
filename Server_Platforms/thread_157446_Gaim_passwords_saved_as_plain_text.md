---
title: "Gaim passwords saved as plain text"
date: 2006-04-09
forum: Server Platforms
---

### Post by Laterix on 2006-04-09
I'd like to know is there a way to save account passwords in hash or crypted form in Gaim. KDE has this kwallet program which is very nice application. Is there anything similar to Gnome? It really bugs me that my passwords are saved as plain text in config file. For more, because Ubuntu gives 755 permissions to user folders as default, I think that this is really an issue!

I hope I'm missing something here. This just can't be the way things are.

PS. Yes, I don't HAVE TO save my passwords, but I'm too lazy to type them everytime again.

---

### Post by LordHunter317 on 2006-04-09
[QUOTE=Laterix]I'd like to know is there a way to save account passwords in hash or crypted form in Gaim.[/quote]Hashing them would be impossible.  Encrypting them is of questionable gain, as a rule.  It has to be reversible, meaning the attacker can trivally (very trivally) crack the password given the encrypted password.

The same applies to unsalted hashed passwords too.

More importantly, your AIM account has no value whatsoever.  If it does, you have other fundamental issues in whatever business you're doing.

---

### Post by trent dillman on 2006-04-10
Don't save passwords? Bad practice...

---

### Post by Kresten Kjaer on 2006-04-10
If the cracker wants your aim password, he would use a packet sniffer or similar. Easier than breaking into your machine.

---

### Post by Azrael on 2006-04-10
[quote=Kresten Kjaer]Easier than breaking into your machine.[/quote]
If the cracker can only access his machine through the internet (the most common scenario I'd think), then sniffing is usually not any easier. To sniff the traffic you'd need root access to a machine along the route between his computer and the AIM servers (including subnets). The weakest link would mostly turn out to be his computer anyway.

Nonetheless, it's very retarded for any network service to send passwords in plaintext. If AIM really does this, then my advise would be to stop using it already.  Make the futile attempt to persuade your friends to use a superior alternative.](*,)

---

### Post by LordHunter317 on 2006-04-11
[QUOTE=Azrael]If the cracker can only access his machine through the internet (the most common scenario I'd think), then sniffing is usually not any easier. To sniff the traffic you'd need root access to a machine along the route between his computer and the AIM servers (including subnets).[/quote]You won't need root access, you may not need any access.  You may just need access to a machine at limited privilege levels, depending on the physical network mediums used between point A and point B.


> Nonetheless, it's very retarded for any network service to send passwords in plaintext.No, it's utter nonesnse to believe most data 
is of enough value to justify sending it encrypted.

> If AIM really does this, then my advise would be to stop using it already.  Make the futile attempt to persuade your friends to use a superior alternative.](*,)There aren't any.  No major IM network uses SSL for authentication, except maybe MSN under certain circumstances.

---

### Post by honeydew on 2006-04-19
maybe dont save the password? enter it every time you login ;)

edit:
------------
oh didnt read about the laziness.. seems your in between a rock and a hard place :D

---

### Post by RavenOfOdin on 2006-04-19
EDIT: Never mind.

---

