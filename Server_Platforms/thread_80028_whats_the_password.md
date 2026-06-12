---
title: "whats the password??"
date: 2005-10-21
forum: Server Platforms
---

### Post by z3r0-c0d3r on 2005-10-21
I shared some folders on my network, when i try to acess them from my XP machine im asked for a password but i never added a password!!
i tried using my ubuntu login password but after that it asks for another password and the user is LAPTOP\imesh
can someone explain this to me??

---

### Post by Freddie.Ruddick on 2005-10-21
Not sure if this'll work for you, but I created a user called share, with minimal (zero) priviledges and a password. In Workgroup on WinXP, I double clicked the icon for the linux box, then typed the username and password into the dialogue.

HTH:KS

---

### Post by LordHunter317 on 2005-10-21
You need to setup your Samba password with:```
sudo smbpasswd -a mesh
```  Then use the password you entered there.  For a variety of reasons, SMB passwords are different from the rest of the world.

---

### Post by z3r0-c0d3r on 2005-10-21
thanks LordHunter works like a charm

---

