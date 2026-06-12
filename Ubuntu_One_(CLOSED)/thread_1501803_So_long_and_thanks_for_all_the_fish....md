---
title: "So long and thanks for all the fish..."
date: 2010-06-04
forum: Ubuntu One (CLOSED)
---

### Post by ade@work on 2010-06-04
I have the latest Kernel (fresh today), I have the latest version of Rhythmbox, I've even cleaned my screen, however, after twenty four hours of reading everything relevent on this forum, numerous re-starts of my lap top and frankly getting to the point that I'm losing the will to live I still cannot get my latest Music purchases to sync, for the last twenty four hours the music store has been stuck at "Transferring to your Ubuntu One storage"  

As I'm PAYING for this service, I feel I have the right to complain, however I understand your busy (aint we all), and I understand your all volunteers (well done that man).  So I'll take my complaints elsewhere, as well as my money.

Adios Amigo's I'm off to use a Music site that at least works.  I'll be back when you get your act together.

p.s. I'm really rather sad about this, cos I so much want to support the Linux and Ubuntu projects.

---

### Post by madverb on 2010-06-04
Glad to see you tried to get help before giving up!

---

### Post by ade@work on 2010-06-05
Hmmm...   Well, the most of the advice on here seems to be of the type 'try running u1sdtool...'  and 'file a bug report'.   For the record, u1sdtool reports that I'm connected, and that the queue manager is IDLE  (which it has been every time I've checked over the last three days now, regardless of any action on my part). Bug reports on my particular issue already exist, so what is the point of filing another one? That doesn't really help the situation.

Music store worked the other day (albeit slowly), and I've not changed anything (apart from downloading the latest version?).

I'm sure that the problem isn't my end, ergo...

Criticise me all you like for not asking for more help here,  See if I care, but the fact remains that the Music store is fundamentally broken and however much tweaking and filing of bug reports people do, it isn't going to make that go away.  Therefore, reluctantly, I'm giving this thing a miss (well once I finally get the files I paid for that is).

p.s I was using Computers, before half the people using these forums were born (30 years),  I am not a 'newbie', I have a BS degree in computing and was using Linux downloaded from BB's when it didn't have version numbering. I really dont need help along the lines of "have you tried re-booting?"  So please dont be flippant.

---

### Post by jimbo99 on 2010-06-06
Always follow these two rules before you make a change to your system.  If you can't adhere to these then don't make the change.

1)  Never keep your customers from purchasing your goods and services.

2)  Never keep your customers from their purchases once they own them.

If you can't make this happen don't make any changes once you have it working, even if you think you are the best ones to make the decision.

Yes, the online store is messed up right now.  I can't seem to purchase anything even though I was able to purchase music in the past.  I have ceased my purchases on iTunes because Apple is acting quite arrogant.  I'm not headed their direction with computing (closed, walled garden, user's loose their choice of what to run and how).  So, I've turned to Ubuntu One since it has such great potential. But they keep screwing it up.

Let's hope the get it worked out.

---

### Post by duanedesign on 2010-06-07
Hmm. I just purchased a song. It downloaded to my computer in seconds. It seems to be working fine. 

If you are having a problem with the music store a couple of things.

Is the song showing up in your cloud storage. Do you see the music at [http://one.ubuntu.com/files](http://one.ubuntu.com/files)  under Purchased Music.

If the song shows up there but not on your computer the issue is local. For that I would file a question on [Launchpad Answers]("https://answers.launchpad.net/ubuntuone-client/+addquestion"), or go to irc channel #ubuntuone on freenode and ask for rye. He is generally on weekdays between 13:00 - 21:00.


If the song is 'stuck' and not showing up in your online storage than I would recommend going to the #ubuntuone channel on freenode between 13:00 -- 21:00 on weekdays for help. Ask for alecu. Or you can file a [Launchpad Answer]("https://answers.launchpad.net/ubuntuone-client/+addquestion").

You might be asked to file a bug. This helps the devs see your logs so they can better understand your issue.

---

### Post by ade@work on 2010-06-08
> **duanedesign said:**
> Hmm. I just purchased a song. It downloaded to my computer in seconds. It seems to be working fine. 


Yes very good, but that doesn't really help anybody does it?  

The good news (I suppose) is that The music store has suddenly started  working for me again, I finally got my paid for music. 

[/QUOTE]
Is the song showing up in your cloud storage. Do you see the music at [http://one.ubuntu.com/files](http://one.ubuntu.com/files)  under Purchased Music.

If the song shows up there but not on your computer the issue is local. For that I would file a question on [Launchpad Answers]("https://answers.launchpad.net/ubuntuone-client/+addquestion"), or go to irc channel #ubuntuone on freenode and ask for rye. He is generally on weekdays between 13:00 - 21:00.


[/QUOTE]

This is incorrect.  The files showed up in my cloud storage (and I downloaded them from there, using the Web interface), however, without me making any changes from the other day, I fired up Rhythmbox this evening and guess what?  the files finally synced to my laptop!  proving beyond doubt, as far as I'm concerned, that the issue was not with my end.  ( I await someone to contradict that).

During my troubles, I set up and ran Music Store on my wife's machine (which has a hard wire internet connection) and it synchronised without a hitch, even a day later I was still able to purchase and download files with no issues. So I'm suspicious that the problem actually lies around the server being unable to tell if the client connection has been severed and re-applied (I'm on a laptop), and it sits there waiting for some token that no longer exists? Which, if true, is a very strange way of doing things a simple handshake would surely resolve?

I don't know, I don't write cloud software? this is pure speculation on my part and immaterial as I'm happy to have finally gotten my files, but I've still no wish to repeat what was quite a frustrating few days and my original post stands.

Oh, and if anybody uses 'u1sdtool -q'  to kill the syncdeamon, check its actually dead, because that command seems to work only sporadically, and then at only one end, I ended up re-booting more than once because of that, even restarting the wireless connection didn't seem to kill it. Does it actually send a kill request to the other end of the pipe? I have my doubts?

---

### Post by duanedesign on 2010-06-08
> Yes very good, but that doesn't really help anybody does it? 
I included that information to help in determining if the problem was with the music store and an issue that was affecting everyone, or a bug that was affecting just you. Perhaps you had given up trying to retrieve your music because you thought the music store was broken. I thought letting you know it was working for me might be beneficial in that you would try again to retrieve you music.

> This is incorrect. The files showed up in my cloud storage (and I downloaded them from there, using the Web interface), however, without me making any changes from the other day, I fired up Rhythmbox this evening and guess what? the files finally synced to my laptop! proving beyond doubt, as far as I'm concerned, that the issue was not with my end. ( I await someone to contradict that).

I apologise if you thought I was trying to say the issue was user error. What I meant by the error is 'local' is that the problem would not be fixed by someone at 7digital and that the issue was related to Ubuntu One. When there are errors in purchasing music the problems fall into two categories.

1. A bug with the music providers servers. This prevents the songs from even showing up in your cloud storage.

2. A problem with the syncdaemon/U1 not downloading the song from your cloud storage.

In attempting to help you with your issue I was speculating on the 2nd scenario. There were some server changes implemented over the weekend that increased the speed at which files were syncing. Due to a large increase in users associated with the release of Lucid the service performance was degraded during the time of your original purchase. This increase in sync speed was likely the reason your files finally showed up.

Glad to hear you finally got your music.

---

