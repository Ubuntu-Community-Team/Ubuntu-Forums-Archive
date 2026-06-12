---
title: "Pangolin - any noise and reliability issues?"
date: 2009-10-31
forum: System76 Support
---

### Post by brMichal on 2009-10-31
From what I have read so far I really like System76 offer. I am considering getting my first laptop from them, probably Pangolin (for the big screen, numeric keyboard and the silent mode button). I have two concerns, though. I hope someone could share their experience with me. 

First, I am looking for a quiet machine. Is Pangolin more quiet than other laptops? Does the silent mode button really makes it silent (does the fan still spin)? How does the button work exactly?

Second, does anyone have any recommendations regarding getting the extended 3-year warranty? How long can I hope to use Pangolin for without worrying about repairs? I made a big mistake by getting just one year warranty on my HP, but, then, everyone praises quality of System76 so much. Is worth to try saving on the extended warranty or not?   

Thanks,

---

### Post by samalex on 2009-10-31
> **brMichal said:**
> From what I have read so far I really like System76 offer. I am considering getting my first laptop from them, probably Pangolin (for the big screen, numeric keyboard and the silent mode button). I have two concerns, though. I hope someone could share their experience with me. 

First, I am looking for a quiet machine. Is Pangolin more quiet than other laptops? Does the silent mode button really makes it silent (does the fan still spin)? How does the button work exactly?

Second, does anyone have any recommendations regarding getting the extended 3-year warranty? How long can I hope to use Pangolin for without worrying about repairs? I made a big mistake by getting just one year warranty on my HP, but, then, everyone praises quality of System76 so much. Is worth to try saving on the extended warranty or not?   

Thanks,

Hi,

I've had my PanP5 for a couple of months now and love it.  Like most laptops it has a fan that you can hear, but it's nothing that'll cause distraction.  Unless the room is dead silent I never even notice it.  The silent button I believe turns of the fan and puts the CPU into a lower-power mode so it runs cooler but someone else might know more about what else it does.  I've never had a problem with the fan noise though, even in my office we're I'm in a cubicle in a room that's normally way too quiet.  You can't hear the fan outside of my cube.  Honestly I've never used the low power feature except for when I need to reserve battery life.

As for warranty I personally didn't go with the three year warrant, but only time will tell how wise of a decision that was.  I think though that it's a one year warranty outta the box though.  From what I've seen the PanP line of laptops are well built so hopefully if anything does go out it'll be within the first year.  I was also told that you can get the 3-year warranty up to thirty days after buying the laptop, but Thomas or someone can correct me if that's no longer true.  

All and all I'm glad I went with the System76 laptop, but if not the System76 I would've moved to a Mac since my last laptop was an iBook.  Personally I think Macs are the best built, but you pay a premium for it which I wasn't willing to do this go around.  

Take care -

Sam

---

### Post by brMichal on 2009-10-31
Thanks, Sam. That is helpful. 

Still, I wonder, what is the effect of the silent button on performance and noise level. While I do not need much horse power, I would really like to have the most quiet laptop possible. I do a lot of intense reading and writing in silence and find the fan noise destructing. 

I also wonder, if anyone had to send Pangolin back for repair in the first three years from purchase?

---

### Post by HotShotDJ on 2009-10-31
> **brMichal said:**
> Still, I wonder, what is the effect of the silent button on performance and noise level.As far as noise level, using "Silent Mode" does, in fact, make the laptop very quiet.  To make any laptop any quieter would require the use of the "off" switch. ;)

As far as performance, that will depend on which CPU you choose when you purchase it.  I bought my PanP5 with the P8700 processor, which has three step levels:  800 MHz, 1.6 GHz, & 2.53 GHz.  With "Silent Mode" activated, the CPU only uses the bottom two steps.  Quite frankly, for reading/writing (I'm assuming the use of a document reader and/or word processor here) I doubt that you would even notice a performance difference, since document reading and word processing are not CPU intensive tasks.

EDIT:  I just checked for any GPU performance hit when using "Silent Mode."  There seems to be no effect whatsoever on the NVidia graphics adapter.

I've only had my PanP5 a few weeks, so I can't speak to the question about repairs.  I recall Thomasaaron saying in a thread that only a tiny fraction of the computers they sell ever need to be sent back for service.
> **brMichal said:**
> ...and find the fan noise destructing.I'm hoping that you find fan noise distracting rather than destructing.    :lolflag:

---

### Post by brMichal on 2009-11-01
Thanks, HotShotDJ. Finally, the magic of silent mode button is revealed. I guess, I could force NVidia into a slower mode from the command line. That is what I used to do with my ATI card and it helped to bring down the heat and noise. I am considering getting P8700 processor too, because it should help my goal of keeping it quiet.  

Thanks for correcting my English, I am still working on it.

---

### Post by HotShotDJ on 2009-11-01
> **brMichal said:**
> Thanks for correcting my English, I am still working on it.Hi, Michal -- I didn't realize that English was a second language for you.  I just though you had made a very amusing typographical error. :)

If you want to lock your NVidia card into a lower GPU performance lever, it is easily accomplished via /etc/X11/xorg.conf using the "RegistryDwords" -- I've experimented with these options, but quite honestly, I think the default "PowerMizer" options seem to do the job by adaptively adjusting GPU performance levels.  The newer 190 series of the NVidia driver does it even better, from what I've heard, but I've not done any testing due to some other issues that I'm hoping to help debug, so I'm sticking with the Karmic defaults for now.

I'm very happy with my PanP5, so I'm sure you'd be happy with the new PanP6.  You might also want to look at the new Lemur UltraThin laptop.  Although the screen is a bit smaller (14"), based on the specs, it might be a good fit for your needs.  Also, based on the way that you plan on using your laptop (reading and writing), I wonder if the 16:9 aspect ratio of the PanP6 screen might be a problem for you.  I also do a lot of reading and writing as a university graduate student and researcher, and find the new wider screen format to be difficult to use, since reading and writing are vertically oriented tasks while the 16:9 screen is a horizontally oriented format (I actually went to a local "Best Buy" store and spent an hour in the laptop department to see if the 16:9 screens would make me crazy or not... they did).

A bit "off topic" -- have you looked at [Zotero]("http://www.zotero.org/")? It is an open source Bibliography manager and works with FireFox, OpenOffice, and MS Word for managing your research and bibliographies.  I use it for my research and it is AWSOME.  It has saved me hours of work.  As I browse the library database subscriptions (such as EBSCOhost, for example) in Firefox, I can save the citations AND the PDF documents with just a few clicks, and then cite them in the text of papers using any number of styles (such as APA, Chicago Manual of Style, AMA, etc.) and then auto-generate my endnotes/reference section.  I also love the sync features.  I can keep my bibliographies and source materials in sync with multiple computers -- home, office, research lab -- so no matter where I'm sitting, I have access to all my journal articles and citations.  It works flawlessly with Linux at home and on Windows at work.  The thing is really amazing.

---

### Post by brMichal on 2009-11-01
Thanks, HotShotDJ. 

> **HotShotDJ said:**
> quite honestly, I think the default "PowerMizer" options seem to do the job by adaptively adjusting GPU performance levels.

That is good to know- yet another proof Nvidia performs better than ATI under Linux. 

> **HotShotDJ said:**
> I wonder if the 16:9 aspect ratio of the PanP6 screen might be a problem for you.  I also do a lot of reading and writing as a university graduate student and researcher, and find the new wider screen format to be difficult to use, since reading and writing are vertically oriented tasks while the 16:9 screen is a horizontally oriented format.

Acctualy, 16:9 ratio works for me pretty well because I like to have two files open next to each other. Although, from my experience it requires 19" at optimum and 17" at minimum. As I think about it, the difference between 15.6" and 14" may be of small importance to me- I will probably need an external monitor anyway. Lemur has been under my consideration as well. But I am a little suspicious towards its Intel GPU and its robustness in general...

> **HotShotDJ said:**
> A bit "off topic" -- have you looked at [Zotero]("http://www.zotero.org/")? It is an open source Bibliography manager and works with FireFox, OpenOffice, and MS Word for managing your research and bibliographies.  I use it for my research and it is AWSOME.

I haven't seen Zotero before. I will definately check it out. The only reference manager I experimented with so far is EndNote, which I got for free from the university. I did not like it at all though, with the exceptions of "search" and "download full text" features. I am a GA as well, and, so far, the best tool I found for managing my refferences, notes, full text colection and my own research papers is MS OneNote.

---

### Post by HotShotDJ on 2009-11-01
> **brMichal said:**
> I am a GA as well, and, so far, the best tool I found for managing my refferences, notes, full text colection and my own research papers is MS OneNote.MS OneNote?  YUCK!  LOL.  To each his or her own.  I think you'll really like Zotero, though.

As far as being a GA -- Low pay, long hours, lots of hard work -- and the greatest experience of my life!  I wouldn't trade the experience for anything.

EDIT:  Regarding the Intel Graphics, it really is a very good general purpose graphics adapter.  My Dell 1505 has one and I've never had a problem with the hardware's performance, since I'm not a gamer and don't really care about gaming performance.  The 3D applications that I do use (simple games like "Planet Penguin Racer" or Google Earth) perform to my satisfaction, even with the older Intel 945GM adapter.  The major pain was in Jaunty, because of some major changes in the way the kernel handles graphics. This change required major changes in the Intel graphics drivers that were not ready in time for the release of Jaunty.  Ubuntu developers opted to go with a stable, but painfully slow, configuration for Intel cards in Jaunty.  The issue as been pretty much fixed for Karmic.  One advantage of the Intel integrated graphics is that they have significantly lower power usage -- and throw a lot less heat -- compared to NVidia or ATI cards, which is why you'll find them in laptops that are designed primarily for mobility and long battery life.  However, if you need the 3D performance, NVidia is certainly the way to go.

---

### Post by HotShotDJ on 2009-11-01
Just another interesting observation regarding the Pangolin.  I've noticed that occasionally the fan seems to get "stuck" on full blast, even though the temp readings (from Gkrellm) are quite low and my CPU is not under any load.  Pressing the "Silent Mode" button twice (once to enable it, a second time to disable it) puts things right.  Most of the time, the fans adjust up or down properly.

---

