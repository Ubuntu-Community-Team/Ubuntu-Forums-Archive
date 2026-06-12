---
title: "Sharing some Ubuntu Server &quot;Server Management&quot; Projects"
date: 2013-04-06
forum: Server Platforms
---

### Post by MAFoElffen on 2013-04-06
Okay... Ubuntu Server (12.04 LTS and newer) on my various test servers. Things have been a bit slow in +1 dev tests and the job market, so...

I was wondering if i could get various vendor server management app's that were meant originally meant for RHEL and hardware dependent ... running on current Ubuntu (12.04LTS, 12.10 and 13.04). Most of my servers are true server hardware but old iron. I have an assortment of HP, GW and IBM Servers. Getting text reports from them was easy- just a few scripts and email alerts. But I got nostalgic and missed my days of graphical dials and gauges monitoring things from a graphical management terminal (25+ years ago). So I started something to challenge my mind and make things interesting.

IBM XSeries 346 server: Get IBM ServeRAID RAID Manager working remotely. Server running Ubuntu Server current editions, managed remotely from Ubuntu Desktop current editions. Got it converted from rhel rpm's. Minimum installed instance of X11 that facilitates the remote ssh connection to run the graphical app locally from the management PC's desktop. (Only loads enough to facilitate the app instance... See attached photo.

HP DL380 G3: HP Server Management Homepage: Integrated HP Health to monitor all health stats of the server, set thresholds, send alerts, etc. Integrated health and ILO logs, ILO management, Files system and storage reports. RAID config and Array diagnostics. In-depth Reports and reporting. Some was converting RHEL RPM's; converting scripts. Converting some RPM source packages to Debian source packages and converting their scripts and C Source to update them for 3.x kernels to create kmods. Others, where finding some HP Debian packages and mixing them in. Configuring a mix of SNMP agents to work together... See attached.

What do you think?  Any more ideas? I'm looking for stuff to keep my idle hands busy and engage my mind... I have a few more servers and was wondering if I should add other management app's for them- HP Netserver, 2 GW960's, GW930, GW7400, 4 ASUS server boards, 3 other assorted GW's. Some with LSI hardware Raid and some with mdadm...

Actually, I had this idea I was playing with to remotely manage and report SMART stats, mdadm stats, etc. from a management console from a GUI app... But then I started playing with Zental and got sidetracted. I thought if anything, this is just something to add to my portfolio/resume. LOL.

---

### Post by cariboo on 2013-04-07
I'd like to see something similar to the gnome disk utility in 12.04, with the ability to check smart remotely. The gnome devs have decided that us normal users don't need to have this ability in the latest version.

---

### Post by offerlam on 2013-04-07
NICE!! 

From what you are showing in the screenshots it looks like you thinking the HP smartstart combined with some HP insight manager (I mainly work with HP, as you know :) )

Correct me if om wrong but isn't there allready a Linux version of those two types of software?

When in stall this in windows i just go to hp website, look up the server i got choose my operating system and install the software. I would assume that i would just have to pick linux instead of windows in that regard? Or perhaps im missing something here?

I have never used linux with smartstart before so I am assuming ALLOT :)

/Casper

---

### Post by MAFoElffen on 2013-04-07
Casper-

For your Gen8, yes. The link for their SDR is "[HP Software Delivery Repository]("http://downloads.linux.hp.com/")". (PM me for directions on making that simpler for you.) But you have to remember hardware that I did this on is an old Gen3 with SCSI ultra 320's instead of SATA. Last Utils they made in any Linux code for that controller was about the time of Ubuntu Server 9.04, which was before CCISS went opensource. Seems with the SmartRAID 5i and ILO (before ILO2)... well as they included new versions of hardware, they then dropped support for older versions out. When that server came out, the only supported Linux by then was RHEL and SEL (+ Win 2000 server and Novell). They didn't use to support Debian or it's branches. As we found out with your new HP hardware, when HP said it was certified for Debian and Ubuntu, those cert's were with "technical exceptions" that excluded specific hardware functionality...

Then the newer versions of the HP-SMH manager didn't want to work with the older utils that supported my controller, because the older utils were looking for dependencies and resources that got renamed somewhere over the last 8-9 years and between different branches of Linux, sometimes being just in different directory structures...

As I just said, HP does have a nice Proliant Software Delivery Repo (SDR) that includes most distro's including recent Debian and Ubuntu through 12.04LTS... But it they say it only supports the G6 and newer servers. I actually had the newest versions of the Homepage running, but all the info was blank because it could not recognize the older hardware. 

That particular project was actually educational, challenging and fun. I learned a lot about HP resources when I helped you with your G8 that gave me ideas about my older Proliants. I started it because the fans on my HP DL380 G3 sound like they are taking off. Research said that without the ILO agents and HP Health, the fan control was all on the hardware PAL. If those software pieces where if place, then the PAL handed it off to software control, where you could monitor it and set thresholds. That is what got me started and interested in it. I now know my temperatures are low and my redundant variable speed fans are actually running on "low" and that they are just very loud on that model!!! (ROTFLMAO!!!)

The version I used of the IBM ServeRAID app is also old iron ServeRAID 7e, which was also SCSI Ultra 320's and just one app, that was written for RHEL. That was a lot easier to convert. Both App's can manage other "alike" servers with "alike" hardware, just like HP-SMH and HP-SIM can.

That got me thinking about something "more" open for managing different servers with differing hardware. I know working with bigger businesses, we standardized on hardware to simplify management, control and support. But we still ended up with a few that swayed from that, because of time between purchases, different contract bids or because of differing requirements. Even with the same vendor we ended up with "different" hardware... With my personal server "farm," I just got deals on hardware people were thinking were outdated and needed to upgrade from. Both the above app's got me thinking. They are pretty specialized. HP SIM is a little more open, just in that it allows other servers with other hardware to report limited info from their non-alike hardware...

Then I got looking at Zental, which is a Ubuntu Server branch targeted at small businesses. From a server management perspective, it has a lot of modules that can cover a lot of things, but each comes at the cost of a lot of overhead. I think each also costs a lot of time to keep up on. And it is all displayed graphically on the local server... even though "that server" could be a virtual host instance.

I'm finding with helping others, consulting, setting up my own test boxes for dev +1 again and again... there are things I do repeatedly (severe understatement), that I started writing pre-seeds and scripts for. I'm starting to look at tools the same way. There are things that I want to keep track of or I wish were easier to administer. Now, if I do something 5-10 times the same way, there's got to be a way to spend my time more effectively. TEXT is okay for reports, but from a management standpoint, I type maybe 120 WPM... There are some things I could be doing rather than typing the same repeatedly. And "something" that grabs the eye visually if there is a problem, like XMessage alerts to the remote console, is more timely responded to than an email alert message or some text report I haven't gone through yet. I've been playing with bash scripts tickled by cron jobs sending XMessage alert message popups to the remote console instead of emails. They are handy... Keeps me from having to weed through alert emails and finding something that should have been taken care of "then." Reminds me of alerts we used to setup to dial and message pagers with... "Feed Me Now!" Now with playing again with SNMP alerts... old and sometimes vulnerable (if used public), but not much overhead...
 
With a combo of the above, my ideas came to either a homepage type visual webapp for managing servers that included smart tools, mdadm, storage, swap, memory, host health type monitoring and some javascript scripts to tie it all together... or a GUI app that could be executed over ssh and displayed on the remote console. Either way. then it's easier to do, and security is local/private.. then extending services from other servers to tie it into one console. It would just make things more open and "easier"... yet easy to secure and lock down.

---

### Post by MAFoElffen on 2013-04-07
> **cariboo907 said:**
> I'd like to see something similar to the gnome disk utility in 12.04, with the ability to check smart remotely. The gnome devs have decided that us normal users don't need to have this ability in the latest version.
Dustin-

gnome-disk-utility stepped away from that, but the functionality/calls are still in udisks right? Thinking that even in the gnome's gnome-disk development scope, they say they didn't want to touch LVM and RAID... I think along with SMART statuses, those are things we "normal folk" look at as part of normal server health indicators. So an easy to use front-end for utils that already have hooks into dbus and are already universally tied into Linux distro's, that can be accessed remotely without bringing a server down to do it... might make things interesting. 

Not wanting to re-invent something like Nagios.... just something light and portable.

Weird concept eh? Server apps to make server setup, administration, maintenance and recovery easier and less effort- Just some thoughts...

---

### Post by offerlam on 2013-04-10
Hey Mike,

Sorry for the late response but after your helped me burst the bubble i have been busy playing with the IDS.. :)

So just to know if i understand you right.. you want to make your OWN webinterface or what ever to show these thing like temperature, fan speed, disc health and so on?? ofcause that would be SO NICE! :)

As i hoped got through my post earlier i have NEVER played with Linux in anyway combined with smartstart - i was just assuming allot of things.. so consider me asking innocently :)

/Casper

---

