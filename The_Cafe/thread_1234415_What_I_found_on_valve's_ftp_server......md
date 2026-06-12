---
title: "What I found on valve's ftp server....."
date: 2009-08-07
forum: The Cafe
---

### Post by dragos240 on 2009-08-07
I was browsing their ftp server, (which the username and password are both 'hlserver') and saw a single file. They're latest version of the source engine. I looked inside to find LINUX LIBRARY FILES. AND a file that was named 'steamclient_i486.so'. I think they ARE indeed still working on a Linux native client.

---

### Post by doorknob60 on 2009-08-07
Didn't we hear about this a few months ago? Or is this something else.

---

### Post by dragos240 on 2009-08-07
I'm not sure. But this is just my find.

---

### Post by Muffinabus on 2009-08-07
What's the server address?

---

### Post by dragos240 on 2009-08-07
> **Muffinabus said:**
> What's the server address?
[ftp://ftp.valvesoftware.com/](ftp://ftp.valvesoftware.com/)

Use hlserver as username and password.

---

### Post by CharmyBee on 2009-08-07
That's probably only as a bootstrap to get a dedicated server running along with the Steam master server, for authorization of legal copies. Nothing about OMG!!! HL2 ON LINUX!!! or anything.

---

### Post by Bölvaður on 2009-08-07
hold your breath (for few seconds at least) this might only be server side of things (again)

**added**
**edit**
oh you need to use archive mounter for this -.-


*added for the last time*

THIS IS A SERVER!!!!
File list:

[SIZE=2]**/**[/SIZE]
srcds_i486

[SIZE=2]**/bin**[/SIZE]
datacache_i486.so
dedicated_i486.so
engine_i486.so
libsteamvalidateuseridtickets_i486.so
materialsystem_i486.so
scenefilecache_i486.so
shaderapiempty_i486.so
soundemittersystem_i486.so
steam_api_i486.so
steamclient_i486.so
studiorender_i486.so
tier0_i486.so
tier0_s_i486.so
unitlib_i486.so
vphysics_i486.so
vstdlib_i486.so
vstdlib_s_i486.so

**[SIZE=2]/tf/bin/[/SIZE]**
server_i486.so

---

### Post by forrestcupp on 2009-08-07
Is what you did legal?  I really doubt if they have a copy of the engine available for anyone to legally look at.

---

### Post by zekopeko on 2009-08-07
> **forrestcupp said:**
> Is what you did legal?  I really doubt if they have a copy of the engine available for anyone to legally look at.

Perhaps not in source code, but binary is fine.

---

### Post by chriskin on 2009-08-07
it seems that it just for the server side, as i can't see why someone would make a game that asks for payment for linux - as most of linux users want free (if possible even open source) apps, games included. but it would be really nice to have some games coming - the community's response to heroes of newerth has shown that linux users include some gamers as well

---

### Post by forrestcupp on 2009-08-07
> **zekopeko said:**
> Perhaps not in source code, but binary is fine.

That's true.  But I was wondering if it was legal to get onto their ftp like that and let everyone know their user name and password.

---

### Post by starcannon on 2009-08-07
> **chriskin said:**
> it seems that it just for the server side, as i can't see why someone would make a game that asks for payment for linux - as most of linux users want free (if possible even open source) apps, games included. but it would be really nice to have some games coming - the community's response to heroes of newerth has shown that linux users include some gamers as well

I buy Linux native games when a genre I enjoy is available. I think "free lunch" Linux users exist, but I don't think they are the dominate force; though I will say, it would be hard to sell me, just a photo hobbiest, Photoshop when I already have The Gimp; though I would bet professionals would be more than happy to pay for something like Photoshop. But I have bought Nero Linux Edition because I like it so much, even though there are great alternative free lunch burning utilities in the repositories. So it really I think boils down to what type and level of functionality in the software the user wants that will be deterministic of whether they would pay or not; free as in beer is a bonus, not the selling point. Just my .02.

---

### Post by Eviltechie on 2009-08-07
You do realize that they have a linux version of their dedicated server.

---

### Post by chriskin on 2009-08-07
> **starcannon said:**
> I buy Linux native games when a genre I enjoy is available. I think "free lunch" Linux users exist, but I don't think they are the dominate force; though I will say, it would be hard to sell me, just a photo hobbiest, Photoshop when I already have The Gimp; though I would bet professionals would be more than happy to pay for something like Photoshop. But I have bought Nero Linux Edition because I like it so much, even though there are great alternative free lunch burning utilities in the repositories. So it really I think boils down to what type and level of functionality in the software the user wants that will be deterministic of whether they would pay or not; free as in beer is a bonus, not the selling point. Just my .02.

consider this point :
*linux users are already so few
*half of them think that All apps Have to be open-source
*half of the rest want it to be at least free of charge
am i wrong until now?

then you have something like 0.5% of the marketshare consisting of linux users who would buy something good - yourself and myself included as it seems. if you owned a company, would you make the port for the game? i would only do it for personal reasons, if i wasn't a linux user, a seriously doubt that i would even think about it for more than a minute.

---

### Post by CharmyBee on 2009-08-07
> **Eviltechie said:**
> You do realize that they have a linux version of their dedicated server.

And they've been providing that for over 10 years.

Had Half-Life been released in this day and age, there would be "linux version!!!" rumors over the Tux icon for the server list.

---

### Post by Dark Aspect on 2009-08-07
Doesn't this belong in [Gaming & Leisure]("http://ubuntuforums.org/forumdisplay.php?f=93")?

---

### Post by chriskin on 2009-08-07
> **Dark Aspect said:**
> Doesn't this belong in [Gaming & Leisure]("http://ubuntuforums.org/forumdisplay.php?f=93")?

i would say "no" , as it is about the possibility of games coming to linux, not the experience of already existing games
i might be wrong though

---

### Post by starcannon on 2009-08-07
> **chriskin said:**
> consider this point :
*linux users are already so few
*half of them think that All apps Have to be open-source
*half of the rest want it to be at least free of charge
am i wrong until now?

then you have something like 0.5% of the marketshare consisting of linux users who would buy something good - yourself and myself included as it seems. if you owned a company, would you make the port for the game? i would only do it for personal reasons, if i wasn't a linux user, a seriously doubt that i would even think about it for more than a minute.

Evidently some game companies think there are enough of us to turn a profit on, which likely means that more than half of us do not require things to be open source; and also means that it is more than likely that more than half of us are willing to pay. Not saying your entirely wrong, just saying that a few companies have rolled the dice on Linux, and done okay with it. Something to consider.

---

### Post by CJ Master on 2009-08-07
> **chriskin said:**
> consider this point :
*linux users are already so few
*half of them think that All apps Have to be open-source
*half of the rest want it to be at least free of charge
am i wrong until now?

then you have something like 0.5% of the marketshare consisting of linux users who would buy something good - yourself and myself included as it seems. if you owned a company, would you make the port for the game? i would only do it for personal reasons, if i wasn't a linux user, a seriously doubt that i would even think about it for more than a minute.

When World of Goo was released to Linux it almost got as many sales as the Windows version (I contributed to that!) Something to consider.

---

### Post by Eviltechie on 2009-08-08
[http://www.slipgate.de/hltv/hltv_FAQ_admins.html](http://www.slipgate.de/hltv/hltv_FAQ_admins.html)

Looks like it might have something to do with HLTV.

---

### Post by swoll1980 on 2009-08-08
> **chriskin said:**
> it seems that it just for the server side, as i can't see why someone would make a game that asks for payment for linux - as most of linux users want free (if possible even open source) apps, games included.

I'm glad you know what we want, because I wasn't sure until now.

---

### Post by chriskin on 2009-08-08
> **CJ Master said:**
> When World of Goo was released to Linux it almost got as many sales as the Windows version (I contributed to that!) Something to consider.

me too :)

> **swoll1980 said:**
> I'm glad you know what we want, because I wasn't sure until now.

you keep on saying sarcastic comments about everyone , everywhere. if they were successfully funny ones, i would appreciate them, but i have been ignoring your posts from the beginning , as most are written without thinking :)

> **starcannon said:**
> Evidently some game companies think there are enough of us to turn a profit on, which likely means that more than half of us do not require things to be open source; and also means that it is more than likely that more than half of us are willing to pay. Not saying your entirely wrong, just saying that a few companies have rolled the dice on Linux, and done okay with it. Something to consider.

let me correct this for you though "that a few companies"... should be "that few companies" :) i can't name more than 10 modern looking games that have been ported to linux :S

most of the "numbers" i mentioned might be a little too much, but by searching about closed source vs open source polls in these forums, that's the answer that you will get (two polls i found had a majority of people voting on "i would use free software unless it is a real need" or something like that)


anyway, i sure hope that games start coming this way, i keep a dual boot these days for anno 1404 and it is starting to become a little too boring having to reboot each time

---

### Post by forrestcupp on 2009-08-08
> **starcannon said:**
> Evidently some game companies think there are enough of us to turn a profit on, which likely means that more than half of us do not require things to be open source; and also means that it is more than likely that more than half of us are willing to pay. Not saying your entirely wrong, just saying that a few companies have rolled the dice on Linux, and done okay with it. Something to consider.

I'd say that it's more likely that there was a Linux fanatic involved in the game production than it is that they thought they could turn a profit on it.

---

### Post by RATM_Owns on 2009-08-08
Upon execution of srcds_i486:
> Warning: falling back to auto detection of vproject directory.
Unable to find gameinfo.txt. Solutions:

1. Read [http://www.valve-erc.com/srcsdk/faq.html#NoGameDir](http://www.valve-erc.com/srcsdk/faq.html#NoGameDir)
2. Run vconfig to specify which game you're working on.
3. Add -game <path> on the command line where <path> is the directory that gameinfo.txt is in.

Unable to find gameinfo.txt. Solutions:

1. Read [http://www.valve-erc.com/srcsdk/faq.html#NoGameDir](http://www.valve-erc.com/srcsdk/faq.html#NoGameDir)
2. Run vconfig to specify which game you're working on.
3. Add -game <path> on the command line where <path> is the directory that gameinfo.txt is in.Read the #2. "To specify which game you're working on."

EDIT: Oh, and also, it's from over a year ago.

---

### Post by CharmyBee on 2009-08-08
srcds = Source Dedicated Server. #2 does not show it's a development tool. This is just an error that it's executed without a game set or a data folder missing.

I hate false rumors.

---

### Post by RATM_Owns on 2009-08-08
I didn't say it was a development tool...

I was saying that to point out that it wasn't a Steam Linux Client.

---

