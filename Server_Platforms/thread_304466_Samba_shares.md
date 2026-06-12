---
title: "Samba shares"
date: 2006-11-21
forum: Server Platforms
---

### Post by 13ojo on 2006-11-21
Hello,

I've installed samba (got lost in the setup so im not sure if thats the problem).

I changed samba's workgroup to be workgroup (instead of mshome), and now i cant find it at all. Before i could find it but was always asked for a password.

I set it up as security=share, so ir permantly has geust as the user, but it still asks for a password!.

This is only when i view all shares at once, in windows xp.

Ive got SWAT up and running succesfully, and SSH, so i can change what ever i need to via terminals.

So my question is, how do i make samba accept null passwords, or even better quit asking for them, on the security=share option?

ps. im running 6.10 and the versions of samba etc i got from the

---

### Post by dantrevino on 2006-11-22
make sure you have 'guest ok = yes' in your share definition.  Also make sure your guest account has the correct privileges for the location you want to share.

---

### Post by 13ojo on 2006-11-23
i had all that :(.

i posted my smb.conf but it didnt appeaer it seems.

For good knows what reason, if the entry "geust" is blank it will give this error.

Typing in geust as nobody, fixes the error.

---

