---
title: "Procmail and Exchange mailboxes"
date: 2008-04-24
forum: Server Platforms
---

### Post by SirLouen on 2008-04-24
I have installed in my Ubuntu server, a Procmail server and in another machine, a Windows 2003 server with an Exchange server with multiple mailboxes.

I would like to know if I could use my Ubuntu server as a connector, receiving the e-mails and through fetchmail, and processing them to the Exchange server mailbox, and how may I do it.

Regards

---

### Post by SirLouen on 2008-05-08
Any ideas? I read sometime something about this, but I can't remember anything.

Thanks in advance

---

### Post by SirLouen on 2008-05-12
When I said Procmail,  is not strict to do this with this software, I'm open to any other alternatives to obtain the same function,

Any ideas?

---

### Post by SirLouen on 2008-05-14
Finally I found something, instead with procmail with postfix.

Thanks for the help :P :guitar:

[http://www.edadfutura.com/en/mail-gateway-linux-con-filtro-antispam-para-microsoft-exchange-server/](http://www.edadfutura.com/en/mail-gateway-linux-con-filtro-antispam-para-microsoft-exchange-server/)

---

### Post by zhuqing789 on 2008-05-14
The fourth [wow power leveling](http://www.wow-powerleveling.org) latest game in [wow power leveling](http://www.xowow.com) Warcraft series is ‘[wow power leveling](http://www.powerlevelingweb.com)’. Also known as [wow power leveling](http://www.igsstar.com), it represents a [wow power leveling](http://www.wowgoldweb.com) multiplayer online [wow power leveling](http://www.powerleveling-wow.com/siteMap.asp) game, the best of [wow power leveling](http://www.powerleveling-wow.com) kind. Initially, it was [wow gold](http://www.wow-powerleveling.org) it be released in 2001, but [wow powerleveling](http://www.powerleveling-wow.com) was delayed [wow powerleveling](http://www.powerlevelingweb.com) 2004, thus [wow powerleveling](http://www.xowow.com) the 10 years of[wow powerleveling](http://www.wow-powerleveling.org) franchise of this[wow gold](http://www.xowow.com) series. The [world of warcraft power leveling](http://www.powerlevelingweb.com) was not [world of warcraft power leveling](http://www.wow-powerleveling.org/wow+power+leveling.html)fulfilling, because [wow power level](http://www.powerleveling-wow.com/siteMap.asp)problems with [wow power level](http://www.powerlevelingweb.com) server’s stability [power leveling wow](http://www.powerleveling-wow.com/siteMap.asp) performance occurred, but [power leveling wow](http://www.xowow.com) game still [power leveling wow](http://www.powerlevelingweb.com) a financial success [powerleveling wow](http://www.powerleveling-wow.com/siteMap.asp) the most [powerleveling wow](http://www.xowow.com) game of its kind. The number [cheap wow power leveling ](http://www.powerlevelingweb.com) users that play [Maple Story mesos](http://www.igsstar.com/Maple-Story-mesos-us/), exceeds 8.5 [MapleStory mesos](http://www.igsstar.com/Maple-Story-mesos-us/), worldwide.As a form [ms mesos](http://www.igsstar.com/Maple-Story-mesos-us/),recognition for [mesos](http://www.igsstar.com/Maple-Story-mesos-us/),outstanding popularity, the game [SilkRoad Gold](http://www.igsstar.com/Silkroad-Online-Gold/), received a[SRO Gold](http://www.igsstar.com/Silkroad-Online-Gold/), of awards. Now the question [eq2 plat](http://www.igsstar.com/EverQuest-2-gold-plat/), why is [eq2 gold](http://www.igsstar.com/EverQuest-2-gold-plat/), game [eq2 Platinum](http://www.igsstar.com/EverQuest-2-gold-plat/), popular? For anyone[EverQuest 2 Platinum](http://www.igsstar.com/EverQuest-2-gold-plat/), played the previous [EverQuest 2 gold](http://www.igsstar.com/EverQuest-2-gold-plat/), and [EverQuest 2 plat](http://www.igsstar.com/EverQuest-2-gold-plat/), already initiated [lotro gold](http://www.igsstar.com/Lord-of-The-Ring-online-gold/), the mysterious world [lotr gold](http://www.igsstar.com/Lord-of-The-Ring-online-gold/), the breathtaking [Lord of the Rings online Gold](http://www.igsstar.com/Lord-of-The-Ring-online-gold/), this [Rolex Replica](http://www.watchreplicashop.com/) nothing but an [Replica Rolex](http://www.watchreplicashop.com/) adventure that continues the story of ‘Warcraft III: Frozen Throne’, four years after conclusion, in the world of Azeroth. The game is online role-playing, the previous versions being online and offline strategy games. The major thrills and unique features are present as in every Blizzard game.

---

### Post by sunstriker on 2008-05-14
Indeed, I think you should install postfix and relay the mails to your exchange server.

---

### Post by promodus on 2008-05-14
[I have done something similar.]("http://www.promodus.net/postfixmailrelaysmarthostforexchange")

All email would go through postfix before reaching exchange.
All email leaving exchange would go through postfix.

A mail relay & smarthost.

---

