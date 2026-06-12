---
title: "Specs - For a small business server"
date: 2008-04-14
forum: Server Platforms
---

### Post by Shiva-Shinken on 2008-04-14
I have read many posts that say server specs do not have to be high... but at the same time I do not know what is too low.  So here goes my question:

I am building a home and small business server (no GUI) to serve some files, stream some media, game server (for Steam).

Is a 1 GHz + 1 GB Ram + 7200 hard-drive too low?  I am also using a Gigabit NIC and switch for the location.

CC

(I am still a noob on these matters, so hope I am not asking the obvious)

---

### Post by hyper_ch on 2008-04-14
as server, that should do fine... but better specs never hurt ;) streaming media will probably put most pressure onto the server...

---

### Post by Shiva-Shinken on 2008-04-14
What component is most affected by the streaming media?  CPU, RAM, hard-drive?  Or all of them?  :KS

CC

---

### Post by refdoc on 2008-04-14
FWIW I had an old P3 with 512 MB and some old SCSI drive doing thsi kind of work for me.

It was too loud (fan) and now I am using a Buffalo Linkstation Live which i reflashed to Debian.

It is working as backup, file and mailserver and is just as repsponsive as the old one was.

The Linkstation's particulars are:

Arm9 with 266 MHz
128 MB Ram
500 GB harddrive

---

### Post by Deathrend on 2008-04-14
That processor could hurt.

What game are you planning on using with Steam? An older CS server might do soso, however you will be hurting, if it runs at all, with a more modern HL2DS.

I remember running Natural-Selection servers on HT 3Ghz Zeons with give or take 2 GB's of ram.. You could squeeze one server onto each side of the processor, but if it hits more than 18-22 users, it would eat the memory like there's no tomorrow.  Old TFC servers loaded on about what you're looking at, with 22-26 people.  But if you're looking to load an HL2 game (Any Source/TF2 game) you're going to need a harder hitting server.

I currently run a TF2 server on an oldish DL580 server, before that however it was run on an old P4 Gaming PC/Convert.  You can get a 3Ghz P4 for 60 bucks, motherboard for about that easily.  If you get DDR2, you're looking at 60-70$ for 2Gb, which is ntohing these days (And it's cheaper than normal DDR)

Just my thoughts, hope it helps.

---

### Post by hyper_ch on 2008-04-14
death: the server doesn't have to do as much computing as the game computer... mainly it's reference stuff...

I run a WoW server on my server and there is hardly any impact on perforamce...

---

### Post by Deathrend on 2008-04-14
WoW servers are went to support several thousand people on cheap hardware, Steam is a memory hungry beast.  I've ran both, there's really no compairing.

My first Business was selling old HLDS servers, on dule T1's lonngg ago.  I had a wall covered in Dell PowerEdge servers, all of which ran ~1.26Ghz PIII processors with 512 RAM (Predating steam, the real HLDS).  These could run three, maybe four HLDS servers at a time, depending on size, The Source gaming engine however is much much larger, and very nasty, and by no means as server friendly.

I can't do the reserch now or I would, (Gogo WebSence) but you can find posts all over about recomended hardware, just for Dedicated HL2 Servers.

I Can tell you that I couldn't get it to run on a Dule 1.4ghz PIII, HP ML370, which iis a beast compaired to most.

{quote]death: the server doesn't have to do as much computing as the game computer... mainly it's reference stuff...[/quote]

When you load HLDS, it downloads the full game to the PC you're installing it on (Thus is how people get early coppies of Multi-player games for Steam).Game servers for FPS games like this do much much more in the way of computing, than a private wow server with Two-Six people on them.  But Yes, HLDS does PHYSICALY load the game onto the server, it doesn't run the actual game, but it is there.  

With WoW, most of the Math is done on the player's PC, as well as most of the MAP's are saved to the PC (Just for fun, look up OverRated, a friend of mine figured out how to remove walls for his guild, making short work of AQ40/Naxx pre BC).  Half-Life uses the server for all of this (Hence why people can only see through walls when cheating, and not shoot through them).  I've played WoW from day one, Half-Life from the DOS days.  on top of that, I'm a Systems Administrator, so not only do I know the games in question like the back of my hand, I know servers.

Take my word for it or not, but I would do the reserch before spending the money, this is something that will hurt your server however.  HLDS is not a production friendly server, by any means.

---

### Post by StarMonkee on 2008-04-14
> **Deathrend said:**
> WoW servers are went to support several thousand people on cheap hardware, Steam is a memory hungry beast.  I've ran both, there's really no compairing.

My first Business was selling old HLDS servers, on dule T1's lonngg ago.  I had a wall covered in Dell PowerEdge servers, all of which ran ~1.26Ghz PIII processors with 512 RAM (Predating steam, the real HLDS).  These could run three, maybe four HLDS servers at a time, depending on size, The Source gaming engine however is much much larger, and very nasty, and by no means as server friendly.

I can't do the reserch now or I would, (Gogo WebSence) but you can find posts all over about recomended hardware, just for Dedicated HL2 Servers.

I Can tell you that I couldn't get it to run on a Dule 1.4ghz PIII, HP ML370, which iis a beast compaired to most.

> death: the server doesn't have to do as much computing as the game computer... mainly it's reference stuff...

When you load HLDS, it downloads the full game to the PC you're installing it on (Thus is how people get early coppies of Multi-player games for Steam).Game servers for FPS games like this do much much more in the way of computing, than a private wow server with Two-Six people on them.  But Yes, HLDS does PHYSICALY load the game onto the server, it doesn't run the actual game, but it is there.  

With WoW, most of the Math is done on the player's PC, as well as most of the MAP's are saved to the PC (Just for fun, look up OverRated, a friend of mine figured out how to remove walls for his guild, making short work of AQ40/Naxx pre BC).  Half-Life uses the server for all of this (Hence why people can only see through walls when cheating, and not shoot through them).  I've played WoW from day one, Half-Life from the DOS days.  on top of that, I'm a Systems Administrator, so not only do I know the games in question like the back of my hand, I know servers.

Take my word for it or not, but I would do the reserch before spending the money, this is something that will hurt your server however.  HLDS is not a production friendly server, by any means.

Agreed. I haven't got any wow server experience, but those specs would struggle with an old HLDS server, and I doubt a source server would run.

For all the other things you mentioned, the machine will perform fine, but running a steam based server will probably be more than it can cope with.

1gb RAM should be ok, but you'll probably need to at least double the processor for game servers.

---

