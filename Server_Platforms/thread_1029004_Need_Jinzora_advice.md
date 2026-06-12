---
title: "Need Jinzora advice"
date: 2009-01-02
forum: Server Platforms
---

### Post by Lori700698 on 2009-01-02
I'm only a week into my first experience with a server, pretty impressed with Webmin, by the way!!!  Ok to my question I want to run my music server with Jinzora2 and MPD (shoutcast was ugly on Jinzora) I was having problems with the set up, no sound was ever achieved streaming to the MPD Jukebox, (the download play part worked fine)so what else do I need to install??? Jinzora3 is awful I was having huge errors with permissions, so I'm aborting that idea.  I changed so many settings and downloaded everything under the sun trying to get this to work that I've seriously messed something up, glad I'm only a week in I'm going to re-install the Intrepid Server.  So what exactly do I need to make this work? I want to stream music at home and work without downloading every song, so I really want the MPD to work.  I haven't seen any solid directions yet, (install this, install that, configure this, configure that and none of it's the same so I'm confused) so if anybody has this working or can point me to the simplest directions I would greatly appreciate it!

---

### Post by Lori700698 on 2009-01-04
Oh my gosh, nobody???  Everything is re-downloaded and is working beautifully , songs shuffle and load BUT I still have no sound and I have a sneaky suspicion that it's a sound card problem and I don't have a clue how to check it because my server is running with no OS or anything plugged into it to pull up and check.  I have icey, icecast2, and MPD all downloaded ~honestly don't know if my settings are even correct because I can't find one solid point for info and help.  Please help if you have anything like this working, I have to go back to work tomorrow (my vacation is over:() and I'm about to go nuts fiddling with it.

---

### Post by cmileto on 2009-12-18
Hopefully you will see this.

I have tried several times to install jinzora2 using the instructions provided with it to no avail on 9.10

Just go with ampache it works great and is in the repo.


sudo apt-get install ampache

though I have had luck with the alpha of jinzora3

---

### Post by Lori700698 on 2009-12-30
cmileto, Thank you for the reply..I REALLY like the look and feel of Jinzora, I'm just afraid nobody is no longer working on it.  I had to fix the playlist buttons my self, which took days to figure out.  The sound issue was so my fault I'm embarrassed to say.  The 3 music files I kept testing were .wmv and MPD doesn't play nice with .wmv at all.  I finally tested a different song and almost blew the windows out, every computer and my cell phone were all pointed to the Icecast streamer and it all took off at once.:lolflag:  I'm sure the neighbors were impressed!  If you ever want to try Jinzora again PM me and I will send you my modifed (working) copy.

Lori

---

