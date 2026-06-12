---
title: "What exactly do you do with your computer at home ?"
date: 2019-08-09
forum: The Cafe
---

### Post by linuxyogi on 2019-08-09
After I boot my PC I visit Facebook then I open my email and that's it.

I cant find anything interesting to do with my PC. 

What exactly do you do with your computer at home ?

---

### Post by sevendogs1337 on 2019-08-09
I have VMs as hack targets, I game (Linux only), I write, I surf, answer and ask tech questions on boards, I chat on IRC and Telegram, I do my banking, probably more, can't think of anything else at the moment.

---

### Post by rbmorse on 2019-08-09
I read every new message on Ubuntuforums.org and reply to some of them.

---

### Post by linuxyogi on 2019-08-09
> **sevendogs1337 said:**
> I have VMs as hack targets, I game (Linux only), I write, I surf, answer and ask tech questions on boards, I chat on IRC and Telegram, I do my banking, probably more, can't think of anything else at the moment.

I too have a VM (same Lubuntu 18.04) I use it mainly to browse porn. 

I want to try gaming on Linux but don't have the money to buy any games.

I visit IRC only when I have a problem and try to find an answer before posting 

here but most of the time I need this forum.

> **rbmorse said:**
> I read every new message on Ubuntuforums.org and reply to some of them.

I do the exact same thing but these days the number of replies to threads is very low.

The number of threads created is still high.

---

### Post by cruzer001 on 2019-08-09
First stop is eMail, then it depends on my mood :)

Everything gets tweaked software and hardware, thats my never ending task.  Latest project, turn half a laptop (no screen,keyboard,storage) into a docking station for my current laptop using some form of a cluster, beowulf I guess.  In theory I would end up with 16 core processing.

---

### Post by malspa on 2019-08-09
Web browsing; web searches; email; using Geany and LibreOffice Writer for text documents; using LibreOffice Calc for a few spreadsheets; viewing other documents (for example, pdf docs with qpdfview); listening to music using Audacious or YouTube; blogging; working with photos that I've taken; learning more about Linux; checking in at Linux forums; downloading isos; tweaking my desktops; paying some bills. That's all I can think of at the moment, but I'm probably leaving something out. No gaming.

---

### Post by crip720 on 2019-08-09
Question got me thinking, very bad idea.  So did a google search on something did not think would be there, but there is.  [https://www.google.com/search?client=opera&q=video+of+watching+paint+dry&sourceid=opera&ie=UTF-8&oe=UTF-8](https://www.google.com/search?client=opera&q=video+of+watching+paint+dry&sourceid=opera&ie=UTF-8&oe=UTF-8)

---

### Post by irv on 2019-08-09
The main thing I do is make videos. I have over 2000 videos on youtube. I also watch videos: news, how-to's, and anything else I find interesting. (No porn).
I write and have published books on Amazon and Google Play Books. I have a couple of thousand out there, and every month I get about 6 to 8 royalty checks sent to my bank.
Then I sell stuff on eBay, Amazon, and a local market place in my area through facebook.
I also do webpages, run a server, operate a sound system at a church, which encludes editing sound files. 
I do so much I don't know how I find time to get it all done and still write and answer posts out here.

---

### Post by lammert-nijhof on 2019-08-10
I use it for YouTube and Facebook when I'm bored or tired. 
My main usage of my PC is related to getting the max performance from my stuff for almost no money. My PCs are interesting; 7 to 16 years old, except my Ryzen 3:
- 2019 Ryzen 3 2200G (New, except the disks; 1x  SSD 128 GB and HDDs 500 + 1000 GB and 320 GB laptop HDD)
- 2008 HP dc5850 with a Phenom II X4 B97 (1x laptop HDD 160 GB and 1x 80 GB HDD)
- 2012 HP Elitebook with an i5-2520M and 1 TB SSHD
- 2003 Pentium 4 HT (from parts I had lying around) with 2 IDE HDDs (320+ 250 GB) and 1 SATA-1 laptop HDD (320GB).

All PCs run Ubuntu or Ubuntu Mate, only the Pentium runs FreeBSD-12. All systems boot and use ZFS, with memory caching and if possible SSD caching.
I'm constantly looking how to improve the performance, some improvements are:
- Boot from striped HDDs (P4 and Phenom) and use striped HDDs in the Ryzen for the Virtual Machines (VMs).
- Dual boot the Ryzen from a LZ4 compressed ZFS datapool with 2 datasets (folders) on the SSD.
- Use LZ4 compression for all OSes, it improved usability for the SSHD.
- Memory caching results in  instantaneous response times in my VMs and Linux reboot times are 6 to 10 seconds.
- SSD caching improved VM boot times; from striped HDDs it takes 40-60 seconds and from SSD cache it takes 15-25 seconds.

The laptop SSHD and P4 HDDs are used as backup for the Ryzen, so i use the ZFS send/receive over ssh to backup my VMs. On a 1 Gbps link the backup is sent from 64-bits Ubuntu 19.04 to 32-bits FreeBSD-12 (the miracle of well designed software).

The performance issues for the coming period are;
- The Phenom II; those two HDDs are extremely slow with a throughput of 60MB/s or less, rearrange some disks or spend $50 - $100 in the future for a Ryzen NVME and rearrange afterwards?
- The P4 transfer speed is only 250 Mbps, because the P4 CPU load is ~90%. 
        --- So do I need 1 or 3 cheap Chinese 1 GB 400MHz DDR sticks; to enable hyper-threading and to increase the cache size. Expected CPU performance increase 20-30%. 
--- How to avoid LZ4 re-compression in the P4 during transfer, that should increase the throughput to physically 300 Mbps. Those 300 Mbps would be 37 MBytes/s of compressed bytes so uncompressed it would equal to ~67 MByte/s (1.8 compression ratio).
--- Maybe switch off LZ4 compression in the P4, it would only influence the new snapshots send.

---

### Post by Artim on 2019-08-10
I always go to email first thing, then check my calendar, then social media and a few favorite forums, including Ubuntu Forums.  I write a blog, do school work (LibreOffice mostly), and listen to music.  That's pretty much it.

---

### Post by Richard_Romick on 2019-08-12
Web and email of course.  In my spare time, my hobbies are programming (iOS/Android development and python) as well as other projects like working on my NAS.

---

### Post by mastablasta on 2019-08-13
i just want to say that i don't believe no one watches pr0n on their home PC :)

anyway i mostly use it for checking email, reading news, playing games and paying bills (i know paying via android is easier, but it just seems a bit more secure via PC). i also process photos and occasionally (though not so much lately) edit some videos. this is all light editing, a cut here and there. the PC is very old.

the desktop is mostly occupied anyway by kids watchign you tube or playing games. also i am not home so much and since i work at a deskjob behind a PC i am often too tired (eyes) to also touch it at home.

---

### Post by PJs Ronin on 2019-08-14
I think I've mentioned this somewhere b4, but over in the corner is my TV set that I have watched for a total of about 4 hours over the past 4-5 years, and they were all David Rabbitburough shows.   Between my computers/tablet/phone my connectivity needs are well and truly met.   I do everything now on the computer that I have always done, except I no longer cut code nor push hardware envelopes.   Everything from finance to entertainment, from news to sports, from social media (blurgh) to pondering the meaning of life, is all done on  computers in various forms.   Surprisingly, emails have become an insignificant role for my computers even to the point where I only get 3-5 spam emails a week.   Couple of years ago this would have been approx 30-50 spam emails a day. 

A new endeavor for me is in the garden.   I've always had a passion for a particular flower species and now I find I can maintain a online database of my plants that all my electronic devices can link to.   My phone/tablet cameras have even supplanted my DSLR camera as image taker of choice.

---

### Post by uRock on 2019-08-16
I run a Motion server, so the first thing I do while drinking coffee is merge all the vids together, then open with VLC and take the speed to 4x and look for any clips worth saving, which is usually 5 out of 30 clips recorded daily per camera. 

Next, I go to Facebook to see what non-sense my friends are posting and match their rhetoric with more rhetoric.

Check my email and delete all of the emails from recruiters who's names I cannot pronounce.

Rip disks that are getting scratched to MP4, then create a new ISO and burn it to a new DVD.

Search for tech jobs relative to my education and end up applying for call center support positions, because I can't afford the $10k worth of certs needed to get a real tech job.

Search for new wine making recipes, since I have almost 200 pounds of peaches I just finished processing and tossing in the freezer and have yet another peach tree about to start ripening.

Order more seeds and supplies for the veggies and microgreens I have growing.

Pay bills, thanks to my wife picking of a more lucrative profession, which honors a degree as an investment in knowledge.

Check the forums for anything that I can help with or learn from others' mistakes.

Play with VMs

Boot Kali to see if any of the updated script kiddie softwares can crack my WiFi.

Search Google for information on whatever project I currently have going and try to find ideas for a small business, as I didn't have the funding I needed to start the roofing company I had planned to start when moving to where we live now.

Clicking refresh on Facebook in hopes of something stupid to reply to.

---

### Post by cruzer001 on 2019-08-16
> **uRock said:**
> I run a Motion server, so the first thing I do while drinking coffee is merge all the vids together, then open with VLC and take the speed to 4x and look for any clips worth saving, which is usually 5 out of 30 clips recorded daily per camera. 
I can (kind of) relate to that.  I can look at the lake conditions without leaving the living room.

[https://www.insecam.org/en/byrating/](https://www.insecam.org/en/byrating/)

---

### Post by freemedia2018 on 2019-08-16
I write, read, and just for fun load two different windows with invidio.us so I can watch the video of one synced with the sound of the other:

"I would do anything for love (but I won't do that)" vs. "Easy Lover" by Genesis

"All About that Bass" vs. "Dancing in the Moonlight" by King Harvest, etc.

---

### Post by uRock on 2019-08-16
> **cruzer001 said:**
> I can (kind of) relate to that.  I can look at the lake conditions without leaving the living room.

[https://www.insecam.org/en/byrating/](https://www.insecam.org/en/byrating/)

Wow, the exact reason I built my own server. No IP cams.

---

### Post by pteryges on 2019-08-18
Three machines.

My macOS machine pays my bills with InDesign, Illustrator and Photoshop. It's my main machine: email, web surfing, calendar, etc. I spend at least an hour a day doing emails, if not more.

My Windows machine is for gaming. It's pretty much a toy.

My Linux machine is for tinkering and curiosity. I have a couple VMs set up with older OSes (OpenStep, Mac OS 9, OS X 10.0) and for general messing around.

---

### Post by sdsurfer on 2019-08-20
- Yes, those, plus . . . 
- Accounting - Gnu Cash is the most awesome accounting software ever, and it's free. When I moved over I exported IIF files from <cough> Quickbooks and brought everything in, it just . . . works.
- Coding - I code all day (web stuff, PHP, perl, JS/jQuery etc.) but love to constantly improve OOP design pattern skills, I go through books and write out the code examples. At home I run Netbeans, at work, PHP Storm. Nothing beats Storm, I just haven't bought my own license yet.
- Graphics - Gimp falls short of Photoshop in only one aspect: the color lookup tables, being open source, have a lot to be desired. Adobe's color lookup tables are far superior. But for web display, GIMP rocks, I do a lot of that and use it to comp out designs for my watercolor paintings.
- Documents - Use the Libre Office suite a lot.
- Duke Nukem - go ahead, laugh. :-) This is the **only** video game I play, it's violent, sexist, non-PC and I love it. I built eduke32 a few years back and there are hundreds and hundreds of user created add-on maps, many of them are true genius. I "get me some" once or twice a week. I just wished it had a network port for deathmatch maps.

> The main thing I do is make videos.
What are your software recommendations? I haven't found a video editor that works just right for me, this is the **only** reason I go over to Windoze on my dual boot machine, to use PowerDirector. Free is not required, I will pay for a decent Linux video editor.

---

### Post by sdsurfer on 2019-08-20
> **uRock said:**
> Clicking refresh on Facebook in hopes of something stupid to reply to.

LOL . . . Facebook is like a refrigerator, you open it, find nothing interesting to eat, close it and walk away, then ten minutes later you open it again . . . nope, same stuff. Nothing to see here.

---

### Post by uRock on 2019-08-20
> **sdsurfer said:**
> 
What are your software recommendations? I haven't found a video editor that works just right for me, this is the **only** reason I go over to Windoze on my dual boot machine, to use PowerDirector. Free is not required, I will pay for a decent Linux video editor.I use Openshot.

> **sdsurfer said:**
> LOL . . . Facebook is like a refrigerator, you open it, find nothing interesting to eat, close it and walk away, then ten minutes later you open it again . . . nope, same stuff. Nothing to see here.
Too true.

---

### Post by sulton on 2019-08-24
watch latest world news
check traffic stats
programming
earn money
watch youtube, movie, clips
read books
play game
listen to music and so on

---

