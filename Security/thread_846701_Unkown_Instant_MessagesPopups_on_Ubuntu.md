---
title: "Unkown Instant Messages/Popups on Ubuntu"
date: 2008-07-01
forum: Security
---

### Post by Gaming4JC on 2008-07-01
Hello,
Whenever I use an eDonkey variant such as eMule on WINE, aMule, or whatever I get these popups. I have a full firewall and I've no idea how they get through but they do. Here's a pic:
[IMG]http://img503.imageshack.us/img503/8653/screenshotar3.png[/IMG]

See the thing in the bottom right corner of the screen? What is that?!! :confused: Help, I hope I didn't infect my Ubuntu box.

---

### Post by dominiquec on 2008-07-01
That's most likely just a DHTML component that's part of the web site you're looking at.

---

### Post by Gaming4JC on 2008-07-01
Thank you for saying that!
Found it:
```

<script src='lyad.com/popdiv.asp?id=20638' type='text/javascript'></script><img src='lyad.com/tracking_id_20638A1O144468A1O50.gif' width='1' height='1' border='0'>

```
In my haste and paranoia I had thought some how it was a real application. For an ad it is most nasty, the thing sits on top of other tabs and pops up so well it could fool you. I had to clean out my FF cache to make the thing stop (Ctrl+Shift+Del).

And the way it says "souhaite chatter" and "Accepter la Discussion", I thought the french had gotten me. lol :P

Sorry for being n00bish, thanks.

---

