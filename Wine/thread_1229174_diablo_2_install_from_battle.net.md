---
title: "diablo 2 install from battle.net?"
date: 2009-08-01
forum: Wine
---

### Post by Rumbl3 on 2009-08-01
I just came back to xubuntu after being away for a while. Anyway i was playing diablo 2 on xp. Just curious if someone can point me in the direction of how to get it to work on ubuntu.

I don't have the cd's but on battle.net you can download the game files. I tried to download them but the downloader failed. I could just download them at work and burn them two cds. Just curious i did some searching but info seems a bit scrambled.

thx in adv.

update my thread got closed due to someone else's post (no hard feelings tho lol). Anyway I'm curious haven't been able to find anything about downloading d2 off bnet and installing it? Is there anyway to in linux when i go to download my copy of the game from bnet it says it can't authenticate me.

Just curious if anyone has any tips for installing and downloading from bnet site.

---

### Post by NightMKoder on 2009-08-02
Can you post your terminal output from trying?

---

### Post by ridetheteapot on 2009-08-02
i never heard of downloading your copy from bnet. where do you get that installer? cause i searched after reading this and saw nothing on battle net.
i can guess why your other threadgot closed and the advise that caused it --- all i can say it diable2 is old. single player is so lame that if you dont have a key to play on battle.net it would suck anyway. so if you have a key but not the discs; follow the previous recommendation.

---

### Post by Rumbl3 on 2009-08-03
> **ridetheteapot said:**
> i never heard of downloading your copy from bnet. where do you get that installer? cause i searched after reading this and saw nothing on battle net.
i can guess why your other threadgot closed and the advise that caused it --- all i can say it diable2 is old. single player is so lame that if you dont have a key to play on battle.net it would suck anyway. so if you have a key but not the discs; follow the previous recommendation.

ROFL umm maybe you should go to battlenet yourself make a login put in your cd keys for say diablo 2 and try it yourself its new beta program out that uses the same downloader type program wow uses for patches etc. People lay to much on google for answers to everything. As for my other threading getting closed it was due to someone suggesting something illegal not because of me. I play on battlenet on windows. I have a valid key. 

Anyway to the second poster i'll get back with ya on what shows up for errors etc. See if we can make some progress instead of useless progress of people advising illegal things and making post that point nowhere. No i'm not trying to bash either but before you kinda start hinting to piracy go to battlenet and check for yourself.

[http://us.battle.net/?rhtml=y](http://us.battle.net/?rhtml=y) heres the link for you also. Make a account and see for yourself.....

I just figured hmmm if the downloader looks to use the same type of thing wow uses probably should be a way to get it to work. So i can download my games on there ( i tend to stick to digital downloads cause cds always get destroyed) and also it would be helpful to others that might have lost or damaged cds but have keys and now you can get your copy of the game the legit way from battle.net itself.

---

### Post by ridetheteapot on 2009-08-03
> ROFL umm maybe you should go to battlenet yourself make a login put in your cd keys for say diablo 2 and try it yourself its new beta program out that uses the same downloader type program wow uses for patches etc. People lay to much on google for answers to everything. As for my other threading getting closed it was due to someone suggesting something illegal not because of me. I play on battlenet on windows. I have a valid key.
sorry checked bnet and didnt see it. i thought i had access to your browsing history, but i guess operas broken and i can't see it.

i play battlenet on linux - i have valid key for d2 and LOD --- i lost my lod disc. but still got it installed somehow. its about 6 this way and half a dozen that way.

anyway i signed up and am using the downloader to get the client.
so far its working fine and ill post some screenshots - but i'm not gonna use the client to install, cause its already installed on this pc.

---

### Post by ridetheteapot on 2009-08-03
ok i went through the whole downloader without errors on my machine. after it finished the launcher popped up and i could start the game (i'd guess normally it would install between these steps, but it must have seen my original installation.)
there are a few screenshots here just for confirmation.

---

### Post by Rumbl3 on 2009-08-03
sry for being a little rude yesterday. Eh i tried to download it and i keep getting can't authenticate download. No clue why it won't allow me to download it.

---

### Post by ridetheteapot on 2009-08-03
you can register the game on battlenet and get the installer/downloader, but then the downloader fails telling you that?
can't authenticate download.
no further information; i would post on battle.net forums and ask --- dont even tell them you running xubuntu though, they might leave to out to dry.

btw im running wine version 1.1.26 from the wine repo. set to windows xp with directx9 installed.

-----------
i searched around the forums and ppl running windows where having this problem as well. their solution was to run downloader as administrator.
i didnt have to sudo the install and you shouldnt have to either (and its a silly idea); but maybe check the permissions on .wine and everything in drive_c including the tmp directory.

---

### Post by Rumbl3 on 2009-08-04
when i do wine in terminal and put that in this is what i get. Then it says it can not autheticate me.

maybe someone can make something of this?

(yeah i am on mint now was on xubuntu having the same exact issues with both same stuff in terminal etc.)

---

### Post by Rumbl3 on 2009-08-04
updated wine to 1.1.26 and this is what it's doing now kinda same thing.btw i've read on b.net people having to run the downloader as administrator in windows. no clue doesn't wine automaticly do that?


well i guess at work tomorrow ill try downloading it there and burning it to cds. Then try installing it lol geez what a pain.

---

### Post by iosif on 2009-08-09
I have a similar problem.  Most of the time the Diablo 2 installer will start downloading, but stops after a few minutes.  Steam does this too when downloading.  To continue I usually have to reboot the computer to resume downloading.

Diablo 2 has never finished downloading, and has thrown a few errors about authentication.

Wine 1.1.26

---

