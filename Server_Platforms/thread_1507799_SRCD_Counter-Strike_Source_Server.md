---
title: "SRCD Counter-Strike Source Server"
date: 2010-06-12
forum: Server Platforms
---

### Post by dyvid on 2010-06-12
Hi guys, I am using Ubuntu, Hardy 8.04
I am using an i5 2.66ghz, 4 gb of 1333 mhz ram and a 7200rpm 500gb sata hdd.

uname -a
```
Linux 216-55-143-27.phx.dedicated.codero.com 2.6.24-23-server #1 SMP Wed Apr 1 22:22:14 UTC 2009 i686 GNU/Linux

```I was running 64 bit but it was giving me grief so I switched to 32bit.

Everytime I try to run
```
./srcds_run -console -game "cstrike" +maxplayers 24 +map gg_aim_shotty

```It holds on this line.  It tends to hold for about 7 minutes.
```
Auto detecting CPU
Using SSE2 Optimised binary.
Server will auto-restart if there is a crash.

Console initialized.
Game.dll loaded for "Counter-Strike: Source"
maxplayers set to 32
maxplayers set to 24
Network: IP 255.255.255.255, mode MP, dedicated Yes, ports 27015 SV / 27005 CL
**Executing dedicated server config file**
```I have search the internet and google and I can't find anything that resolves this.  I've tried not using the autoupdate option, I just can't get it to load properly (swiftly). This also continues whenever the server changes maps.

Any and all suggestions are appreciated.  I know we're all busy, but I would like to resolve this by Monday (I have a virtual private server that was windows that expires on Monday), so the transition for the players/users will be easier.

I also wouldn't mind possibly upgrading release if we think it will help.

Thanks for reading and hopefully helping!

~ Dave

P.S.  I love you guys, I use Intrepid, my favorite so far, though I haven't tried Linx.  You guys (Ubunutforums) have always had my issues resolved in other post.  I can give you guys feedback/help with Ncomputing if anyone wants to pm me a question or something.

---

### Post by Schuby007 on 2011-03-10
Hey,

Did you figure this out. I'm in the process of building a Counter Strike: Source server and trying to gather as much information as I can to avoid any obstacles. I plan on using Ubuntu Server 10.04 64bit.

I'm kinda surprised no one got back to you, however I've found that for specific, technical questions, the community can be pretty silent.

---

### Post by arrrghhh on 2011-03-10
> **Schuby007 said:**
> I'm kinda surprised no one got back to you, however I've found that for specific, technical questions, the community can be pretty silent.

Well this is a specific, technical question about something that is NOT ubuntu related, but rather CS related.

Not really the best place to ask those kinds of questions.  If it was a technical specific question about ubuntu, it probably would've been answered by now.

---

### Post by dyvid on 2011-03-10
Nope, I know it happened on every other os we tried using, Cent and redhat.

I think it was a broken update when css redid/upgraded their engine.  Or it could have broken sourcemod/metamod which in turn could have caused Ubuntu (Linux) to not recognize the commands and take forever to run.

I would just simply try it and see how it works now.

(On one of the two game servers we ran, we ran a zombiemod, which had updated signatures to make it work in Linux as of Jan. 11)

P.S.  No one ever answers my direct questions, they just are ignored until someone asks me for advice or bumps it.  But when I search for a preexisting question there is typically an answer I need.

So I blame you ;) if only you had posted before I did.

---

### Post by CharlesA on 2011-03-10
You could post here: [http://forums.steampowered.com/forums/forumdisplay.php?f=45](http://forums.steampowered.com/forums/forumdisplay.php?f=45)

---

### Post by dyvid on 2011-03-10
The one difference, I told Ubuntuforums to contact me when a new post was made...steam, I waited and waited until I gave up the project.

So it might be answered somewhere.

---

