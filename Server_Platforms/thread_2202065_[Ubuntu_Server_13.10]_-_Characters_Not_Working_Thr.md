---
title: "[Ubuntu Server 13.10] - Characters Not Working Through SSH"
date: 2014-01-27
forum: Server Platforms
---

### Post by Dorian_Sokolowski on 2014-01-27
Hey guys!
I'm having a problem with Characters on my Ubuntu Dedicated Server, here is what is wrong:

So, whenever I make a screen using JVM (Java) and try to type § for example or *öäå*, it turns into >ï¿½ .
However all characters are working outside the screen.
I will try to explain this better if needed.

Thank you for reading!
**- Additional Info:**
**OS: **Ubuntu Server 13.10 "Saucy Salamander" (64bits)[COLOR=#34393C][FONT=OpenSans]
[/FONT][/COLOR]**$ locale** - Output:[COLOR=#34393C][FONT=OpenSans]
[/FONT][/COLOR]*LANG=en_GB.iso88591*
*LANGUAGE=*
*LC_CTYPE="en_GB.iso88591"*
*LC_NUMERIC="en_GB.iso88591"*
*LC_TIME="en_GB.iso88591"*
*LC_COLLATE="en_GB.iso88591"*
*LC_MONETARY="en_GB.iso88591"*
*LC_MESSAGES=POSIX*
*LC_PAPER="en_GB.iso88591"*
*LC_NAME="en_GB.iso88591"*
*LC_ADDRESS="en_GB.iso88591"*
*LC_TELEPHONE="en_GB.iso88591"*
*LC_MEASUREMENT="en_GB.iso88591"*
*LC_IDENTIFICATION="en_GB.iso88591"*
*LC_ALL=*

[B]Java Version:
[/B]*java version "1.7.0_51"*
*Java(TM) SE Runtime Environment (build 1.7.0_51-b13)*
[I]Java HotSpot(TM) 64-Bit Server VM (build 24.51-b03, mixed mode)

- I'm using SSH for connecting to my server (I'm using Putty for SSH).[/I]

---

### Post by steeldriver on 2014-01-27
I don't really understand what you're doing (a screen using JVM?) but you may find that it helps to change the PuTTY 'Remote Character Set' (Change Settings --> Window --> Translation). Try UTF-8 instead of the default Latin-xxx set.

---

### Post by Dorian_Sokolowski on 2014-01-27
> **steeldriver said:**
> I don't really understand what you're doing (a screen using JVM?) but you may find that it helps to change the PuTTY 'Remote Character Set' (Change Settings --> Window --> Translation). Try UTF-8 instead of the default Latin-xxx set.
Hey there.
Basically I'm running a Minecraft Server which uses Java 7, not sure if this is a problem with Java's encoding or if this is associated to Ubuntu's encoding.
Anyway, I have a batch file which turns on the Minecraft server and I view the console by using a screen.
§ Is format used for colors in Minecraft, whenever I type "say §aHello" (§a is light green color) it turns into "<?>Hello" in game chat.
Thank you.
**EDIT:// I changed my Putty's character set to UTF-8 and saved (I forgot to save last time) and all characters are working but they are appearing as <?> in game chat, perhaps Java 7's encoding is set to wrong?**

---

