---
title: "Voyager I"
date: 2017-12-06
forum: The Cafe
---

### Post by KD5NRH on 2017-12-06
40 years, no replacement of the tape and it's still working.  Why, then, can I not get a HDD to last more than a year or two with Ubuntu on it?

---

### Post by ian-weisser on 2017-12-06
Perhaps you are not purchasing the same hardware that NASA is.

I have had over a decade of Ubuntu installs on many many machines, with no unusual disk problems.

---

### Post by mastablasta on 2017-12-06
try using a different file system.

---

### Post by ajgreeny on 2017-12-06
I have a disk that came from an old machine with IDE connection and that still is working fine in a caddy and has had one of the Ubuntu family on it since I first used Ubuntu in 2005.

I am sure there must be more to your problem than simply running Ubuntu on it, but without knowing all the detailed facts it's impossible to suggest much.

What type of problems do you see after such a short time; is it a hardware or software problem?

---

### Post by cariboo on 2017-12-06
Except for a certain model Seagate, I've never had any problems with hard drives dying. Here are a couple that I have in my server, results from smartctl -a

[LIST]
[*]9 Power_On_Hours 0x0032 052 052 000 Old_age Always - 42736
[*]9 Power_On_Hours 0x0032 030 030 000 Old_age Always - 61890
[/LIST]

---

### Post by mastablasta on 2017-12-07
unfortunately i don't have access to the site from work, to be able to post a link to it. but if you search "hard drive reviews reliability" you will get test results from Backblaze. you can see that even drives under major strain should last well over a year. 

as cariboo mentioned certain model of Seagate drives had an issue. a big issue and their failure rate was high within relatively short time. but they fixed it and the more recent version of same model or upgraded models perform fine.

---

### Post by gordintoronto on 2017-12-07
I swear by WD Black drives.

---

### Post by KD5NRH on 2017-12-10
> **ajgreeny said:**
> What type of problems do you see after such a short time; is it a hardware or software problem?

A couple of them fell victim to the SMART load cycle count trouble from forgetting to set hdparm [s]--stop_killing_my_drive[/s] -B 254 soon enough after install.  The rest suddenly started getting crazy bad sector counts way too soon.  It's been a mix of WD, Seagate and a Hitachi or two, over the course of several years.

---

### Post by litlesam on 2017-12-10
HDD more than 5 years old and is power on more than 12 hours a day.
SSD more than 3 years old and is power on more than 12 hours a day.

---

### Post by mastablasta on 2017-12-11
aside from the fact that space stuff is tested for 10 years before being installed, i can't help but wander what you do on the drives. care to share that info?

also what file system are you using? Are you heavy on swap?

WD Green can fail relatively fast, just now i had external WD elements fail on me without any warning and even more shockingly without much use. practically unused, less than 10% taken drive got busted.

---

### Post by KD5NRH on 2017-12-13
> **mastablasta said:**
> aside from the fact that space stuff is tested for 10 years before being installed, 

Sounds like a good standard for all hardware and software.  It would give the companies something to do besides dreaming up new and incompatible "standards."

> i can't help but wander what you do on the drives. care to share that info?

Mostly just daily personal use; web surfing, Gimp, LibreOffice, occasionally read a PDF ebook.

> also what file system are you using?

ext4

> Are you heavy on swap?

Current one is about 10G in a Dell E6400, partly because I was half asleep when partitioning and miscalculated while setting up the other partitions.

> WD Green can fail relatively fast, just now i had external WD elements fail on me without any warning and even more shockingly without much use. practically unused, less than 10% taken drive got busted.

Current one went south last night while watching a YouTube video.  WD 320GB, not sure which model as it's running badblocks right now so I can't pull it out to look.  It's been running Win7 in another laptop for years with no issues, though, and was about 95% full when I pulled it for this.  The errors were showing on the /home partition, /dev/sda3 this time though; most of the failures I've had before started in the first 1-2GB of the disk.

---

### Post by mastablasta on 2017-12-14
laptop drives are (usually) of much worse quality than "desktop" ones. also people often would move around with laptop on while disk is spinning. or put the laptop on uneven surface (such as bed, knees etc). all this can cause damage to drive. 

for reliability go with WD black (or similar), if you need even more reliable but are ok with slower ones go with WD Red (or similar). if you need server grade then HP will also do. Brands that are  also good are Seagate and Hitachi (even though they might be made in same factories).

with ext4 on it make sure there is always some disk space left free. but you could explore other file systems. still ext4 should be fine for the sue you described.

as with other things - "they don't make 'em like they used to". cheap components help bring down the price of the product. end result is that product doesn't last as long as it used to. a 10 Gb Hitachi drive went out after 16 years service and i am still not sure the drive is actually damaged (could be the motherboard is out but since drive was ide...). a later bought WD black drive kicked the bucked after 9 or 10 years. i still have a working IDE drive form arround 1999 or 2000. but i decided to replace it last year with a newer SATA drive. it just started to get errors and slowed down a bit. though it works quite well...

with normal use you should get 7-10 years out of "black" drives.

you can also investigate if there is any other issue that could be causing drives to be stressed.  power fluctuations, hard / cold shutdowns & reboots, also if you have them always on they should wear down less...

---

### Post by KD5NRH on 2017-12-14
> **mastablasta said:**
> you can also investigate if there is any other issue that could be causing drives to be stressed.  power fluctuations, hard / cold shutdowns & reboots, also if you have them always on they should wear down less...

This has been a continuous pattern over several years, (As in, first time was with Slackware installed via FTP back when torrents weren't yet a thing.) three houses, two cities, and at least four different laptops.  I rarely shut down unless I know I'm going to be unplugged long enough for the battery to run down in standby.  I'm seeing drives fail in 3-4 years pretty regularly.  The current one went from no problems during install last week to so many bad blocks I'm not sure I could have made one that bad by sandblasting the platters.

---

### Post by QIII on 2017-12-14
Yours is an anecdotal experience as is mine:  since the 80's I've had exactly one drive fail -- one of the Seagates that had the firmware bug that stuck them on "busy".  With a gerry-rigged USB cable, some crimped on terminals and a few commands in the terminal I got it working long enough to recover my data.  Other than that, the only time I have replaced drives is when I get bigger ones.

I've been using Ubuntu since Warty and have encountered no such issues.

That does not mean you haven't, but it does indicate that Ubuntu is not the death of hard drives.  Something is definitely going on and that is beyond frustrating I am sure!

---

### Post by KD5NRH on 2018-06-20
And since I last posted, I got a brand new Seagate 2TB, and today, 
COMRESET failed (errno=16)

---

### Post by poorguy on 2018-06-20
hard drive reviews reliability


[https://www.backblaze.com/blog/hard-drive-reliability-q4-2015/](https://www.backblaze.com/blog/hard-drive-reliability-q4-2015/)

[https://www.backblaze.com/blog/hard-drive-reliability-stats-q1-2016/](https://www.backblaze.com/blog/hard-drive-reliability-stats-q1-2016/)

[https://www.backblaze.com/blog/hard-drive-stats-for-2017/](https://www.backblaze.com/blog/hard-drive-stats-for-2017/)

[https://www.digitaltrends.com/computing/backblaze-reliability-report-2018-hgst/](https://www.digitaltrends.com/computing/backblaze-reliability-report-2018-hgst/)



I'm still using old hard drives from the days of ***Windows XP ***(***40 GB 5400 RPM***) and (***40 GB 7200 RPM***) and larger without any problems and all brands.

Modern electronics manufactured today is mostly garbage and does seem to have a high failure rate check the roadside curb out on the morning drive to work and you will see evidence
of that.

Now that being the case doesn't mean that good quality manufactured electronics can't be purchased today although one will have to be willing to research and then be willing to spend the extra money for better quality electronics.

I also wouldn't recommend buying refurbished hard drives to much chance of failure imo.

---

### Post by KD5NRH on 2018-06-20
> **poorguy said:**
> hard drive reviews reliability

[https://www.backblaze.com/blog/hard-drive-reliability-q4-2015/](https://www.backblaze.com/blog/hard-drive-reliability-q4-2015/)

[https://www.backblaze.com/blog/hard-drive-reliability-stats-q1-2016/](https://www.backblaze.com/blog/hard-drive-reliability-stats-q1-2016/)

[https://www.backblaze.com/blog/hard-drive-stats-for-2017/](https://www.backblaze.com/blog/hard-drive-stats-for-2017/)

[https://www.digitaltrends.com/computing/backblaze-reliability-report-2018-hgst/](https://www.digitaltrends.com/computing/backblaze-reliability-report-2018-hgst/)

Got a link for the magic adapter to fit any of those drives into a laptop?  My machines may be a little outdated, but they're not LTE 5200s with 3.5" bays.  Should I just toss some drives in the dryer and hope they shrink, or try to build the first quad core Osborne?

---

### Post by poorguy on 2018-06-20
The purpose of the links was to show which drive manufactures produce reliable drives.

I would think that a 2.5" drive could be found with it's results also posted for comparison although have no idea as I don't use Laptops.

I use a lot of 2.5" hard drives removed from Laptops and use them in desktops and have zero problems or issues with any of them.

If mechanical hard drives are always failing than you might consider an ***SSD*** 
[LEFT][COLOR=#000000][FONT=Ubuntubeta]
[/FONT][/COLOR][/LEFT]

---

### Post by 1clue on 2018-06-20
> **KD5NRH said:**
> 40 years, no replacement of the tape and it's still working.  Why, then, can I not get a HDD to last more than a year or two with Ubuntu on it?

Let me guess:  You're using a Western Digital "green" drive?

I ordered a dozen of those at one time, and all but one died a horrible death way before I would have expected. The last one died, but in what I would call a reasonably early failure rather than infant mortality like the others.

It has to do with settings on the green drive, there to use less energy. The drive sleeps much faster than other drives. There are supposedly 2 methods to tweak it, but they didn't work for me.

---

### Post by uRock on 2018-06-22
I've never had an HDD failure, either. Knocking on wood. I have a cheap Asus netbook that has been running as a Motion server, which is constantly writing to the drive, and it is still running like a champ. My current tower has the HDDs from my previous two desktops in them as secondary drives and have had no problems with them. I also have some second hand laptops that are pretty old and still kicking.

---

### Post by jeremy31 on 2018-06-22
I lost a couple hard drives 20 years ago but the last one was just a couple years ago after this Lenovo was over a year old.  I also saw one fail on a production machine at work with no backup as somehow the backup that was only a few months old disappeared from the server.  This Lenovo had a Seagate SSHD but the replacement has worked well

---

### Post by galacticstone on 2018-06-22
Back in early 2008, I purchased an Acer Aspire One netbook which was manufactured in Taiwan. I used it for 8 years - heavy daily use. Eventually, the LCD screen had dead pixels on it. One of the USB ports failed. The power adapter jack failed. The keyboard started acting up and then eventually failed. That little netbook became an experiment - I wanted to see how long I could use it before it failed completely. Eventually, it was the power jack that was the deal breaker - buying new power adapters didn't matter because the juice wasn't getting to the machine. So, after several months of using an external USB keyboard, I had to quit using it. The battery wouldn't charge any more and it would not run off A/C. But, the HDD never failed. 

Using that good experience as motivation, I bought another Acer netbook. The new one was made in mainland China - everything on it started failing in under a year and it went into the trash heap shortly after it's first birthday. 

Quality means everything. There is an old saying in China that roughly translates to "For every penny, you get a penny's worth of quality." In other words, you get what you pay for. Although, the OP's experience sounds more like a rash of bad luck as much as quality control issues or quality of components.

---

