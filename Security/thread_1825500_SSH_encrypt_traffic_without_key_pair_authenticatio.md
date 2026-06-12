---
title: "SSH encrypt traffic without key pair authentication?"
date: 2011-08-15
forum: Security
---

### Post by fokuslee on 2011-08-15
{Sorry just realized should post under security}
does SSH encrypt network traffic automatically?
or do i need to put a setting somewhere? 
I am not using key pair authentication, does that mean my password is sent in plain text? 
I am currently using SSH to tunnel my web browsing,
so it would really help
Thanks a bunch

---

### Post by The Cog on 2011-08-15
Your password is not sent in plain text. If my memory is right, SSH uses Diffie Hellman Key Exchange to negotiate encryption keys before anything else.
[http://en.wikipedia.org/wiki/Diffie%E2%80%93Hellman_key_exchange](http://en.wikipedia.org/wiki/Diffie%E2%80%93Hellman_key_exchange)

P.S.
Moved to Security Discussions

---

### Post by Bachstelze on 2011-08-15
Simple: absolutely everything you do through SSH is encrypted. :)

---

### Post by fokuslee on 2011-08-15
Thanks for the replies, D-H key exchange turn out to be a very interesting read

---

