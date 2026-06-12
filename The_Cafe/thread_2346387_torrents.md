---
title: "torrents"
date: 2016-12-14
forum: The Cafe
---

### Post by pete1977x on 2016-12-14
if you use Transmission in Ubuntu on a semi regular basis...  what do you think is a reasonable setting for uploading????

---

### Post by Bucky Ball on 2016-12-14
A reasonable setting is what suits your ISP's speeds and your hardware. Depends on a number of factors. What is the maximum upload speed your ISP provides? Run a speed test (there are a heap available, try [Ookla]("http://www.speedtest.net/")) and see what upload speed you're actually getting.

Best to diddle around with it and see what works for you. There is no 'standard'. Experiment.

Possibly more relevant is how many peers you have set Transmission for. If you have the gate open for 200 cattle to get through and you have 5 cattle ... (in other words, if you have 5 peers, drop the setting in 'options' to 7 or 8 as you don't need to leave space for 200 possible peers).

---

### Post by shantiq on 2016-12-14
personally i use this on a 75M/s Broadband
[ATTACH=CONFIG]272704[/ATTACH]

---

### Post by Bucky Ball on 2016-12-14
> **shantiq said:**
> personally i use this on a 75M/s Broadband
[ATTACH=CONFIG]272704[/ATTACH]

Presuming that's download speed, not your upload speed. Try that speed test I linked to and see what it shows. It will do an upload then a download test. ;)

You've been around awhile so sure you've checked it, but I would never take an ISP's word about the speeds you are getting. They only ever tell you what is possible, not actual. :)

---

### Post by shantiq on 2016-12-14
yes  bucky that is my broadband connection no one in the UK has 75M upload  do they anywhere?   ...  download is the figure mentioned i took this as read : )  upload is 4M about

details >>


speedtest-cli
Retrieving speedtest.net configuration...
Retrieving speedtest.net server list...
Testing from Virgin Media (xxxxxxxxxxx)...
Selecting best server based on latency...
Hosted by InTouch Systems (Norwich) [0.93 km]: 39.804 ms
Testing download speed........................................
Download: 73.92 Mbit/s
Testing upload speed..................................................
Upload: 4.61 Mbit/s


PS    i must add this what my settings are when i use the net in the daytime; it does not interfere with my surfing

---

### Post by SeijiSensei on 2016-12-14
I'm not clear about the question.  There are many settings that can affect uploading.  For instance, I have Transmission configured to upload twice the size of the download.  What settings are you asking about specifically?

---

### Post by mastablasta on 2016-12-15
i think they are interested in up, down and max number of connections. 

i have limited it all otherwise everoyne attaches to my network. i have 50M/50M optical cable. but i limit download to 5M and upload to 2M and do it only during night time. the reason is because server is also receiveing data during night and that data has priority. i also limited the max number of connections. i do not care if torrents download slow.

i used to be on 512kb/256kb connection when i lived at my grandfathers house. i had to limit it even further then, and torrents too a really long time but eventually they arrived. :-)

so to the OP, what you want is for you to decide. if oyu want it fast open it all up. if you do not mind a slower download then close it down a bit. i would say to max about a 3rd of your network speed.

---

### Post by TheFu on 2016-12-15
There are places with residential 1 GigE/1 GigE connections.  The fastest I could get are very different from what I have.  I can buy 250Mbps/75Mbps ($300/month), but have 16/3Mbps for $110/month. This is not a residential connection, since they don't offer multiple static IPs or better support options.  

Older consumer routers had issues with lots and lots of connections. Newer GigE routers shouldn't have an issue supporting 10K connections, if the bandwidth is available. On my connection, I'd never allow more than 25 connections and never more than 50% of the tested, available, bandwidth and only overnight.  During the day, the bandwidth has more important uses here.

---

