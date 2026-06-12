---
title: "Advanced Samba Config Tool?"
date: 2009-11-14
forum: Server Platforms
---

### Post by Roasted on 2009-11-14
I'm trying to find a decent, easy to use, but feature packed Samba gui tool. Currently I use system-config-samba and it's nice, but I can't adjust things like create mask and directory mask from within the gui, so I just add it to the smb.conf.

This is easy to do, but I'm just trying to find tools that'll handle more features like this.

I've considered webmin, but haven't gotten home yet to install it. Would webmin do what I need or am I just stuck with editing the smb.conf manually?

---

### Post by Vegan on 2009-11-14
I have not noticed any special tool, too many options to be considered. Its not that bad to open nano and edit the file manually and restart SAMBA.

I have run it manually for so long it's second nature.

---

### Post by capscrew on 2009-11-15
> **Roasted said:**
> I'm trying to find a decent, easy to use, but feature packed Samba gui tool. Currently I use system-config-samba and it's nice, but I can't adjust things like create mask and directory mask from within the gui, so I just add it to the smb.conf.

This is easy to do, but I'm just trying to find tools that'll handle more features like this.

I've considered webmin, but haven't gotten home yet to install it. Would webmin do what I need or am I just stuck with editing the smb.conf manually?

How about [**_[COLOR="Blue"]SWAT[/COLOR]_**?]("http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/SWAT.html")

---

### Post by Roasted on 2009-11-15
> **capscrew said:**
> How about [**_[COLOR="Blue"]SWAT[/COLOR]_**?]("http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/SWAT.html")

I heard about SWAT, but I heard rumors that their support was sub-par or that they didn't update anymore or something like that. I don't know the details but I remember hearing something that wasn't overly promising about them. Can anybody confirm this?

I checked out webmin, and I'm very impressed with it. I could do a lot more in webmin than I expected, so I think I'll continue using this.

---

### Post by CharlesA on 2009-11-15
Heh, I use webmin and it works fine for me. :-)

I've heard good things about another program, but I cannot recall its name atm. I think it can be used to configure Dan's Guardian, Squid as well as Samba and whatnot.

EDIT: The other one was called "[eBox]("http://www.ebox-platform.com/")"

---

### Post by Roasted on 2009-11-15
> **CharlesA said:**
> Heh, I use webmin and it works fine for me. :-)

I've heard good things about another program, but I cannot recall its name atm. I think it can be used to configure Dan's Guardian, Squid as well as Samba and whatnot.

EDIT: The other one was called "[eBox]("http://www.ebox-platform.com/")"

Yeah, I liked ebox, but I decided to stick with webmin. It seems a lot more expandable and straight forward.

---

