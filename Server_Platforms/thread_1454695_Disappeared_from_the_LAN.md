---
title: "Disappeared from the LAN"
date: 2010-04-15
forum: Server Platforms
---

### Post by Vegan on 2010-04-15
The spare computer disappeared from the LAN, so what gives?

I had SAMBA running, then updates seem to have made it disappear.

What gives?

---

### Post by iponeverything on 2010-04-15
> **Vegan said:**
> The spare computer disappeared from the LAN, so what gives?

I had SAMBA running, then updates seem to have made it disappear.

What gives?

Sometime my wife will be thinking about something and when I walk into the room and she'll say something like "I'm petty sure that if we miss our connection, the Hyatt will have good coffee" -- And I will have no idea what she is talking about..

---

### Post by Vegan on 2010-04-15
I drink a lot of coffee myself, lots of it.

---

### Post by bab1 on 2010-04-15
> **Vegan said:**
> The spare computer disappeared from the LAN, so what gives?

I had SAMBA running, then updates seem to have made it disappear.

What gives?

Maybe it was stolen...

---

### Post by Vegan on 2010-04-15
The machine has a small disk, its a spare until I can get a new machine up. No big deal, I can use Microsoft's sky drive to move files around easy.

---

### Post by BobVila on 2010-04-15
Holy random thread, batman!

Check smb.conf - it sounds like you elected to overwrite your smb.conf file during the update and probably wiped out the pointers to the samba shares you had set up.

---

### Post by Vegan on 2010-12-10
I have changed my LAN settings completely and now that problem is fixed

Now I see some problems with web serving but I noticed my domain registrar was down for a bit.

I have not seen any problem since I changed from a class B subnet to a class A with 10.x.y.x to move the unit into a more nondescript spot.

I wonder if my old Linksys WRT54G is starting to die? I unplugged it for a bit and reset it.

It uses Linux too.

---

