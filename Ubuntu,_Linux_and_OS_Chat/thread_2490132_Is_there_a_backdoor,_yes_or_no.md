---
title: "Is there a backdoor, yes or no"
date: 2023-08-23
forum: Ubuntu, Linux and OS Chat
---

### Post by bjngchn on 2023-08-23
Are there backdoors in *ubuntu's ? and other linux distributions?

Why ask such a strange question, ..because people can't say yes or no so far,
plus a few other reasons.

(Maybe it exists but because it has to exist for some deep reason 
which can't be remotely discussed anywhere without taking some risk.)

---

### Post by yaminb on 2023-08-23
Unless you review every line of code yourself including the tools used to build the software, you cannot say 100% that there are no backdoors. 
It just depends on how much trust you give the ecosystem and people. 

There's no guarantee the water you drink isn't laced with chemicals meant to impact you in a certain way...

As a regular user, I trust the ecosystem to a reasonable extent. I rely on basic network monitoring / firewalls to give me some assurances, but anything is possible.

---

### Post by deadflowr on 2023-08-23
Not a support request so
*Thread moved to **Ubuntu, Linux, and OS Chat***

---

### Post by crip720 on 2023-08-23
The answer is yes.  If by backdoor someone can get into your Ubuntu/Linux system.  If your system is only protected by the password, it only takes someone a few minutes to change the password and get in if they have access to the system/PC.  Encryption of the harddrive will defeat this.

---

### Post by TheFu on 2023-08-23
Yes.  There are lots of back doors.  Usually, end-users like them because they do things like patching the system without asking.  Do you use snaps?  They have back doors.  Do you use automatic APT updates?  More back doors.  Did you sign up for Ubuntu PRO support?  More back doors.  These are known and reasonably documented, but they aren't called "back doors".  They are generally doing what the admin for the system requests.

If you setup inbound and outbound firewall rules, will they be bypassed?  Nope.  There was a competitor who specifically did allow their OS programs to bypass user-created firewall rules on the operating system. I'll give you 1 guess for which company that was. They turned this capability into a "feature" - look up "bypass rules".  This is why we have different firewalls outside the OS enabled and why UPnP on firewalls must be disabled everywhere.

Remember when Canonical inserted Amazon queries for all queries?  Those could have opened back doors, according to some.

There are also hundreds of bugs that can be remotely accessed when a system is on the network.  I can say this based on history with much higher quality software projects with 100x less code.
Almost all software has bugs. These bugs can be abused.  They can be made into "back doors", with sufficient effort.

Does Canonical have super secret back doors that only they know about and strive to keep hidden?  Impossible to say but I doubt it.  It isn't that hard to gain access to an OS if you have physical access, provided the OS isn't on strong encrypted storage.


> (Maybe it exists but because it has to exist for some deep reason
which can't be remotely discussed anywhere without taking some risk.) 
Whether it is a risk to discuss or not depends on which country you are in and if your work is under any national security acts or NDAs in the commercial world.  I'm free to discuss nearly anything I didn't work on myself and haven't signed a legal agreement called an NDA. 

People are constantly trying to insert nefarious software into every F/LOSS project.  Sometimes they've been successful.  There was an FTP server that had a back door for over a year before someone noticed it. That was long ago.  I see reports of code modules from different languages having undesirable code added when someone on the trusted team has their credentials stolen.  Most recently, node.js and other javascript libraries seem to be a popular target.  I'm much more worried about that than I am Canonical.

---

### Post by bjngchn on 2023-08-28
Thanks for great answers. 

Actually I have the same question about hardware, for example
are there hidden cameras on TVs, monitors, smartphones, and even refrigeratos, washing machines,
and if so they would come with an excuse like remote controlling/ monitoring by users if needed,
or support purposes. (and if something is provably leaked, they would just say: hacked,.. ok but why is it even possible)

...
A strange thing that happens with ultra fresh  kubuntu (on ultra fresh computer)
I maximize security/health by disabling wireless, blutooth, chat, sharing . etc.. and now I can't  connect 
WIRED internet. or can connect just for 10 minutes; and when I logout I get error "Blutooth malformedd, TRACEPC"
So someone (hardware or software) is very unhappy that I don't want my computers to be used  by others without my consent.

---

### Post by TheFu on 2023-08-28
> **bjngchn said:**
> Thanks for great answers. 

Actually I have the same question about hardware, for example
are there hidden cameras on TVs, monitors, smartphones, and even refrigeratos, washing machines,
and if so they would come with an excuse like remote controlling/ monitoring by users if needed,
or support purposes. (and if something is provably leaked, they would just say: hacked,.. ok but why is it even possible)

Hidden?  not in general, but if you are a specific target, then the supply chain can be intercepted and almost anything is possible.  At least 2 counties spy agencies have been caught doing this.  The mitigation is to randomly buy these things from stores without providing any hint that you will.  Don't "order" a new laptop online. Walk into a store, perhaps not the normal one that you would visit, and pull the laptop randomly off the shelf, buy it and walk out without letting them "set up" the system.  That's nearly impossible for a "state actor" to intercept.

And avoid smart devices. That's been known for a long time, regardless of what those industries do.  We haven't had a TV in the house since 2010 (or so).  We have lots of screens larger than 24 inches, but none are TVs and none have built-in networking.

When it comes to carrying around a personal tracking device (cell phone), that's a personal choice.  It is a trade-off between convenience and privacy.  Only you can make that choice.  I'm different than everyone I know and stubborn.  I have a cell phone, but no cellular data plan.  It is a wifi-only device, unless I'm traveling to a new city.  Then I'll get a 10-day SIM card in the new city.  When traveling, we are more vulnerable, so in my mind, a little tracking is a good thing.  When I'm traveling, I generally enable the GPS on the phone and have it ping back locations every 5 minutes to my Nextcloud server ... leaving tracks.  I enjoy looking at those tracks.  They are locally stored about every 10 seconds too.  This is how I can add GPS coordinates to photos taken on the trip.  I just ensure the camera time is correct within a few seconds to actual time.  There are tools that will take a directory of photos with EXIF timestamps and a GPS trk file, mux that data together to place GPS information into the photos by matching the times.  Of course, I don't do this for local photos, since GPS coordinates also show both were you are AND where you are NOT.  That can be very dangerous.  Thieves are known to monitor social media for when people say they are going on a trip, figure out where that person lives and break into their home when they are gone.  
At least one guy was talking about a business trip to a foreign country on twitter.  When he arrived there was a sign with his twitter handle waiting to take him.  He was kidnapped and his company ended up paying $250K to get him home.  When he got home, his house had been robbed.

All these smart devices that send data outside your home are a huge liability.  A number of very well-known "security cams" have been cracked and remote people watch the cam. Sometimes they are pretty crazy and have conversations with young kids.  The parents learn about it, usually thinking it is an imaginary friend, until the parents are also spoken with over the webcam.  Maybe, only buy webcams that hook into your infrastructure?  If there's an "app" to control the webcam - run away.  Normal IP cameras cost a bunch more, because the company isn't selling your data to subsidize their business.  That's why smart TVs are so cheap.  Your viewing is being sold. Any smart device that does work disconnected from the internet, should be returned.  YOU ARE THE PRODUCT BEING SOLD.  I have a webcam in my attic. Had some critter issues. It never had any video/photos of any humans on it.  These days, neighbors might have cams pointed from inside their door to the street.  Perhaps the video capture also gets the front of your house?  Someone could use image tracking to build a timetable of your habits leaving and returning home.  I've been temped to setup a SDR to capture RF signals on the street.  I live close to the entrance for the housing area here. I could probably figure out the habits for 50% of the neighborhood in just a few weeks simply by capturing wifi and bluetooth MACs which are broadcast in the clear.  Add in a LPR to snap a photo, and it would be easy to track the vehicles passing.  [https://github.com/openalpr/openalpr](https://github.com/openalpr/openalpr)

> **bjngchn said:**
> 
...
A strange thing that happens with ultra fresh  kubuntu (on ultra fresh computer)
I maximize security/health by disabling wireless, blutooth, chat, sharing . etc.. and now I can't  connect 
WIRED internet. or can connect just for 10 minutes; and when I logout I get error "Blutooth malformedd, TRACEPC"
So someone (hardware or software) is very unhappy that I don't want my computers to be used  by others without my consent.

I used a laptop without wifi or bt for years. Both were internal to that laptop.  Instead, I used a USB3-to-GigE adapter with 4 USB3 ports.  It was completely plug and use and routinely tested to 920Mbps using iperf3.  I have no idea how to disable chat or sharing. I never set those up.  The BT and wifi was disabled in the BIOS and at boot, I unloaded the kernel drivers, just to be certain.  At a security conference, a laptop I had was hacked.  Because I'd never enabled wifi or let the laptop out of my touch, it took me a little time to figure out how they'd gotten in.  In preparation for attending the conference, I'd wiped the storage and did a fresh install of Ubuntu the day before. Completely patched it.  Bingo!  That fresh install had enabled bluetooth without my knowledge.  Because I never use bluetooth, I wasn't used to looking for it in the settings.  After that weekend, I disabled BT in the BIOS.  Live and learn.  When I got home, I wiped the storage completely and did a fresh install, then restored my backup data, settings, and programs. ... then triple checked that bluetooth couldn't be enabled accidentally.

Whenever someone claims that other people are using their system and they have wifi, bluetooth and networking disabled and they live alone, I know they are overly paranoid or not telling the facts.  A few people have made those claims in these forums.  I might post 1 time to their thread, but by that point, they are usually spinning in paranoia and lack of knowledge for how things work.  There's no convincing them otherwise.

---

### Post by bjngchn on 2023-08-29
TheFU is a lot like me, except that he knows a lot more.
Also when buying electronics, don't give your info (or better give fake ones), pay in cash, wear and behave differently than you normally do 
(for example wear a mask and say, I'm sensitive to cowid).

Being careful is one thing, 
and while trying to be careful, 
experiencing unexpected consequences is another thing,
for example not  being able connect to wired internet, whatever the reason is 
very abnormal. I disable BT and use airplane mode (I don't trust airplane mode either,
it is like saying, I can't use wireless, but wireless may be working outside my control)
why is Wired internet disabled also.

New kubuntu's internet management is poor in my opinion. 
I don't have much control over it. I don't see much. There is airplane mode, blutooth,
it is not very clear which setting enables//disables whatm
and whether I'm connected to anything or not. For example, why is there
no option to turn off wireless, and instead I'm being shown airplane mode.
Who knows what unknown things turning on airplane mode does besides
making blutooth and wireless unusable by user. Maybe it enables a different comminication
between machine and the cloud, outside user control.

---

### Post by TheFu on 2023-08-29
> **TheFu said:**
>  And avoid smart devices. That's been known for a long time, regardless of what those industries do.  We haven't had a TV in the house since 2010 (or so).  We have lots of screens larger than 24 inches, but none are TVs and none have built-in networking. 

If a "smart device" works without any connection to the LAN, fine.  There's little risk in using it.  Just be certain that firmware updates can be performed using a local USB device and don't require internet connectivity.  

Where it gets fuzzy and either may or may not work is whether those devices can be on your LAN, but not have internet.  My first experience with this was with a Google Chromecast.  For me, it was effectively only useful for youtube. It couldn't play any of my media on my LAN even with internet connectivity.  Without internet, it wouldn't boot.  Plus, it was extremely limited for the video/audio codecs supported.  At the time, it didn't support about 95% of the codecs I'd been using. Useless, at least to me.  Plus, you needed an android phone to control it, also connected to the internet.  All of this was less about showing you media than it was gaining access to your habits.

Why do people think Google created Android?  I have a theory.  Before Android, Google had lots of data, but none of it was tied to a real person.  Nobody used their real names and nobody connected their google account with any form a payment (i.e., a real name).  With Android phones, we all needed a cellular voice/data plan.  And since Google owned the OS, they had access to that sensitive data.  Stupidly, we all signed up (well, other people did, not me I was avoiding social networks and anything with Google already at that point).  Then my job demanded I carry a smart phone - they bought it, not me.  I'd had jobs that required Blackberry devices for about a decade at the time, but Blackberry wasn't known for selling out their customers.  Anyway, the company bought and gave me a Nexus 4 phone.  How's that for putting off getting a smart device?

Today, my phone is generally in airplane mode.  Otherwise, the LTE modem will connect to towers so that E911 calls are possible.  I suspect that dialing 911 would automatically enabled the radio.  Telecom companies thing about stuff like that. Plus, in the USA, any cell phone that has power is required by law to be able to make 911 calls. Their might be an exception for technology changes, so I don't expect a cell phone from 2005 using GSMv1 to work that way, but it will try.  I trust airplane mode to work correctly in my country.  What other countries do is a completely different question.

BTW, airplane mode turns off all the radios, but they can be individually re-enabled.  So, choosing airplane mode, then choosing to enable wifi should (that's a big should), only enable the wifi radio.  It is possible that there is only 1 radio in these tiny devices, so the different frequencies may not be enabled, even if the circuit is powered.  Hard to know without specifically testing your device with your firmware on your installed OS.  An OS upgrade could change that completely.

And if you have a Faraday pouch, those definitely work. They are cheap, provided you use it and understand the limitations.

---

### Post by whysohard2 on 2023-10-08
anyone aware or syncing or mirroring code (passively backdooring certain processes)? for productivity add easy to use terminal search commands to discover any potential discrepancies. 

some commands to start with are : 

sudo chkrootkit 
sudo rkhunter -c

---

