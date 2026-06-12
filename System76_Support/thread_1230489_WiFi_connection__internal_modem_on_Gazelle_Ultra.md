---
title: "WiFi connection / internal modem on Gazelle Ultra"
date: 2009-08-03
forum: System76 Support
---

### Post by showgun22 on 2009-08-03
I bought my Gazelle ultra this spring and I have been en route for almost two months using hotels/motels.
Many places I could not connect due to no signal or very poor or loosing connection. I do understand that signal strength is everything, but now that I am back home I decided to test the Gazelle ultra side by side with my over 3 years old Dell both using the exact same Ubuntu version and connecting the same way.

Connection speed was always slower on the Gazelle Ultra by at least 10% and with much greater variation going up to almost 30% and this at different location in the house. Depending of location the variation were going to the point of loosing connection while this never happen on my old Dell.
I understand that the percentage might not be accurate but the end result are still real.

I would like to think that newer hardware are more advance tech. as well as better drivers, 
Personally I would like to see my Gazelle Ultra at least at par with my Old Dell if not a bit better.

I would like to assume the problem is drivers related.
I hope you can solve this WiFi strength and stability problem.

---

### Post by jml on 2009-08-03
It very well may be driver related.  Your Dell most likely has an older chipset for it's wireless card.  Sometimes older hardware has better Linux support.

I also notice that you list Feisty Fawn as your current distro.  Are you actually running Feisty on your new Gazelle?  If you are, you might want to boot up Jaunty, (9.04) as a live CD to see if your wireless improves.  I have noticed improvement compared to older versions.

Joe

---

### Post by showgun22 on 2009-08-03
They both have Jaunty with all the latest updates.
Since from what I understand System76 has it own drivers they should be
interested in this result and try to improve their drivers for this.
A very important thing to travelers.
Having to get out your hotel bedroom to get a connection most time is not very interesting.

---

### Post by thomasaaron on 2009-08-04
> Since from what I understand System76 has it own drivers they should be
interested in this result and try to improve their drivers for this.

We don't create wireless drivers. The wireless card is supported by default in Ubuntu.

While you have the two computers configured similarly, they are not exact (i.e. they are using two completely different wireless cards). 

We get calls and emails quite often about hotel wireless problems. For whatever reason, hotel networks are pretty consistently problematic for a lot of Ubuntu users.

But, as for your home router, I also find that some newer wireless cards don't work as well with certain brands of routers (particularly apple/airport routers and older linksys routers). I was having a similar problem at home and ordered a D-Link d-625(??) and it was like night and day.

---

### Post by showgun22 on 2009-08-04
Unless I am misunderstanding your reply which states
"hotel networks are pretty consistently problematic for a lot of Ubuntu users"

Seems like the Ubuntu teem has needs to improve their Wireless drivers?

Is there a teem working on this and should a bug be reported?

---

### Post by thomasaaron on 2009-08-04
Rick, I doubt is a driver issue. The driver for the Intel 5100 card is really quite good.

It more likely is either a networking issue with the hotel routers (which typically are older, poorly managed and poorly maintained), or it could be an issue with network manager. It's hard to say without digging deeply into a particular networking scenario. 

It's really a lot of conjecture at this point, since you aren't in a situation where you can provide us with diagnostic information about a particular hotel network.

However, if you want to try to figure out what is going on with your home network, please provide more information about it, and I'll be happy to assist you in any way that I can.

---

### Post by showgun22 on 2009-08-05
Because you specifically mention "hotel networks are pretty consistently problematic for a lot of Ubuntu users" you meant in comparisons with other OS on the same system.  But when I get the time later this year this is something I will try dual boot with windows and see what happen. Also cdysthe state that Linux Mint 7 is flawless Those might be some good test....

The card being the almost the same other than the N support I do not see why there would be a difference. 

In the starling post cdysthe mention tweaking is router I hope he will explain a bit what he did that might give us a hint for our routers if that is the case.

At this time I have two WRT54GL one original firmware the other with DD WRT

Thanks

---

### Post by thomasaaron on 2009-08-05
That's exactly the router I junked in favor of a D-link. I couldn't get decent speed out of it with an Intel 4965 card (which is the one just before the 5100).

That router is a wireless G. Meaning it has a max speed of 54MB per second. What kind of speed are you getting with it?

Your card (which supports "N" will get up to 400+ MB per second) if you have an n router.

---

### Post by showgun22 on 2009-08-06
My problem is not so much with speed as it is drop in the signal strength.
I do not have that type of drop with my old Dell and I just tested my son old E-machine Laptop side by side while I did not notice drop in the E-mach I did with the GU signal is strong but there is drop in strength by half at times. This is why in many hotels it is very hard to connects.

the old e-mach wifi
00:0b.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

My next testing I will try to setup windows on it and compare...

I never had problem with the router other than with the GU when compare with other laptop same distance the signal comes almost as strong but the GU has drops in signal strength.

---

### Post by thomasaaron on 2009-08-06
> Connection speed was always slower on the Gazelle Ultra by at least 10% and with much greater variation going up to almost 30% and this at different location in the house.

I thought speed was the issue.

As for signal strength, in *this* particular instance, it probably is related to how much surface area of foil is between the LCD and the back cover. Most laptops have the antenna wire connecting to sheets of foil. Some computers have little squares of foil, others plaster the whole back panel in foil. This plays somewhat into reception. The Gazelle probably has less foil than your older computer.

That's not really something that can be easily remedied.

---

### Post by showgun22 on 2009-08-06
This might account for strength of signal depending of amount foil on different laptops, but I do not believe it should account for continuous hi low/drops in signal strength while the other do not loose signal strength when tested side by side.

---

### Post by richard@laptop.org on 2009-08-06
> **showgun22 said:**
> My problem is not so much with speed as it is drop in the signal strength.


I 2nd this issue.  I carry my laptop around quite a lot and I _consistently_ see fewer AP's and lower signal strength than my peers.  I've been in hotels, businesses, coffee shops, etc.  The AP does not matter and its not "just a hotel" problem.  

Kernel version doesn't seem to matter nor does the firmware.  I'm currently running 2.6.31 rc5 but I've used .28 .29 .30 as well.  I'm currently running the latest firmware from the intelwireless.org site (version 8.24.2.12).  But when upgrading from the previous version I didn't see any change other than the driver stopped whining about old firmware.

The performance of the intel wireless in the Gazelle seems to be sub-standard.

---

### Post by thomasaaron on 2009-08-06
> This might account for strength of signal depending of amount foil on different laptops, but I do not believe it should account for continuous hi low/drops in signal strength while the other do not loose signal strength when tested side by side.

Hmmm... I can definitely see your point. 

However, I'm still thinking the culprit is antenna surface area. This is starting to get a little conceptual, but I think it works something like this...

Less surface area (i.e. a smaller target) may provide less reception at a greater distance. Whereas a huge surface area (a larger target) may still pick up enough of a signal at that same distance that it doesn't really register to the computer as a signal strength drop.

At any rate, I'm positive that what you're describing has to do more with the design of the machine than it does a problem with the card or driver.

---

### Post by showgun22 on 2009-08-06
It sure is weird

I have the two laptop side by side both laptop have strong signal but for some weird reason only the GU keep having drops in strength of signal while the other does not and with out moving the distance.

I will have to research this in my mind if this would be as you suggest "the culprit is antenna surface area" I could see this affecting signal strength as suggested and it does make sense. But when it come to spontaneous drop in signal going back up to normal and back down by almost 1/2 every drop it is just plain weird and can not see this being cause by antenna surface area.

---

### Post by jdb on 2009-08-06
> **showgun22 said:**
> It sure is weird

I have the two laptop side by side both laptop have strong signal but for some weird reason only the GU keep having drops in strength of signal while the other does not and with out moving the distance.

I will have to research this in my mind if this would be as you suggest "the culprit is antenna surface area" I could see this affecting signal strength as suggested and it does make sense. But when it come to spontaneous drop in signal going back up to normal and back down by almost 1/2 every drop it is just plain weird and can not see this being cause by antenna surface area.

I'm just speculating based on other things I have worked on in a similer frequency range.
I don't know what kind of antennas are in laptops.

Single antennas versus dual antennas (diversity recieve) can make a big difference in drop out.

Signals in this frequency range exhibit fade as reflections combine, somtimes reinforcing the signal & sometimes destructively.

Two recieve antennas seperated by a distance fade at different times so one of them usually has a good signal.

jdb

---

### Post by thomasaaron on 2009-08-06
> I have the two laptop side by side both laptop have strong signal but for some weird reason only the GU keep having drops in strength of signal while the other does not and with out moving the distance.

Does that mean you are *not* moving *at all* and the signal strength is lowering and then getting stronger?

Edit: I'm having some difficulty understanding exactly what symptoms you are experiencing under what circumstances. I've read back through everything, and I am now pretty uncertain I ever understood your complaint.

---

### Post by jml on 2009-08-06
I think jdb may be on to something.  I had an old ThinkPad which had dual antennas mounted in the LCD housing.  That computer always had rock solid wireless performance, and very steady signal strength.  So Tom's suggestion that it might be due to the hardware may be right on if the laptop only has one antenna. 

The varying signal strength is very similar to a problem I had several years ago trying to get an Atheros based Wi-Fi card to work with Network Manager.  Back then there was a known bug that caused that combination of card and applet to list erroneous signal strength levels.  It did not always interfere with connections, but it was very weird.

Joe

---

### Post by showgun22 on 2009-08-06
English being a second language I sometimes try to explain things which seems clear to me but are not so clear to others <BG>

I have tested the GU side by side with two other laptop all running Jaunty with all the recent updates a....

Dell XPS  0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02

e-machine   00:0b.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

First at about 15 feet
the GU had a signal reception as strong as the other two but the GU was the only one receiving a signal that had drop in signal by half or very close to half for a few seconds + than spiking back up to the same signal strength for a while and droped again. While the other two laptop never showed sign of drop in the signal strength.

I than replicated the test at about 30 feet or so, while the signal showed a bit less strong for all of them maybe a bit more on the GU "meaning less strong" the drop this time for the GU were low enough to loose connection.

I hope I made this clear <G>

---

### Post by thomasaaron on 2009-08-06
Ah! I see. That makes more sense. Thank you for clarifying.

Please confirm these results with a different (preferably newer) router (other than a hotel router if possible). If it happens on more than one router, I'd be inclined to say you had a loose antenna wire or a defective wireless card. This is not something we're seeing across the board with Gazelles, so it is most likely either the card or the router.

(You don't have to compare computers on another router, just confirm that the wireless signal on your Gazelle is flaky on a different, known-good router.)

Also, it is *entirely* possible to have a good signal with one computer connected to a flaky router and have problems with another computer connected simultaneously to that router. We've seen that on several occasions. It happens.

I can send a new wireless card to you if necessary.

---

### Post by showgun22 on 2009-08-06
I will try to get to a few different places that offers wifi and see what happen I will ask what brand of router they have.
This might take a couple of weeks but I will try to do this.

I'll let you know what happen
THanks

---

### Post by showgun22 on 2009-08-22
I finally got some time and got around to go to a couple other place to test.

First place was a Hotel lobby they had a small Netgear router and I was at less than 10 feet away from the router. The connection signal strength kept going up and down from as low as 15%  and up to 72% strength.

The second place I went was inside Staples I asked the guy at the computer counter if he mind if I'd test my laptop connectivity as well as what brand of router they were using.
They had a D-link I was at about 20 to 25 feet away from their router my signal strength was not as good as theirs on their laptops, and again my signal reception was again going up and down from as low as 12% and up to 47% and I did lost signal once in a minute or two of testing or simply being connected to their network.

So end result the signal strength is still as bad of a problem with other router and my Linksys is just as good as the other 2 brands I tested with.

Hope that we can do something to improve this. My guess is that having such fluctuation might have been the cause why I could not connect to some hotel while on my summer trip.

---

### Post by thomasaaron on 2009-08-24
Thanks for running those tests.

I think the next order of business is getting you a new wireless card. What you are experiencing is certainly not typical for a Gazelle. Please email me at support--at--system76--dot--com.

---

### Post by showgun22 on 2009-09-03
I have received the replacement wifi card.
Before I replace it I did my updates and I had to reboot which I did but I believe the after rebooting "Not positive" I had no wifi connection which I realized after the fact and recalled after shutting down and replacing the WIFI card.

Anyway to make a short story I replace the card rebooted had no wifi connection. did lspci in the terminal and the card is there and detected.
iwconfig

 iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan1     IEEE 802.11abgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B
          Encryption Key:off   
          Power Management:off
          Link Quality=0  Signal level:0  Noise level=0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.


I am not sure what is going on I tried turning on/off wifi
At this stage is there a way to see if the wifi is on or off?
any suggestion what I should do next?
I have setup my router to unsecured wireless just in case....
I also tried the old wifi card back and got the same thing
Thanks
Other than a clean install <G>

---

### Post by thomasaaron on 2009-09-03
When you say the old wifi card gave you "the same thing," do you mean it shows no wireless, or do you mean it gives you the previous symptoms?

First...

> To fix your /etc/network/interfaces file, go to a terminal
(Application > Accessories > Terminal) and enter the following command:

sudo gedit /etc/network/interfaces

This will launch a text editor with the interfaces file opened in it.

In this file, put a comment (#) in front of EVERY line of the file
EXCEPT for these two lines:

auto lo
iface lo inet loopback

Click SAVE on the text editor and reboot your computer.
It should now boot faster and connect to networks more easily.

NOTE:
Unless you are dealing with static IP addresses (which is pretty rare for the
general end-user) you should NOT establish a network connection by going to
System > Administration > Network.

Instead, you should connect to the Internet using the Network Manager icon
in the upper right corner of your screen (the one that looks like a little
computer monitor).   

Second, reset your access point and verify you have networking on it with other computers (if you have another machine to test with).

Third, did you remove the ac and battery before replacing the card?

---

### Post by showgun22 on 2009-09-03
AP can connect to other wireless no problem

What I meant is that 
I relace the old WIFI card with the new one and had no wireless
I put the old one back in and the same no wireless
put the new one back in and still have the same no wireless.

I did not remove the ac battery 
I just made sure it was turned off and no static.
The replacement part did not come with any instruction or mise en garde to remove the battery first I hope i did not fry the cards...

Thanks

---

### Post by thomasaaron on 2009-09-03
Please fill out this brief online form. It goes straight to my inbox and will provide me with the information necessary to process warranty requests and repair estimates...

[http://system76.com/article_info.php?articles_id=39](http://system76.com/article_info.php?articles_id=39)

Let's bring it in.

---

### Post by showgun22 on 2009-10-20
Can some one tell me if there was any improvement done in the wireless drivers?

I just installed Karmic 9.10 beta 64 and unless I am having wild dreams my wifi connection seems stronger and better very close to my old Dell.

Does any one else with a GU running Karmic see this?
Thanks

---

### Post by thomasaaron on 2009-10-20
It's possible, but we've not tested Gazelles here in the shop yet.

---

### Post by showgun22 on 2009-10-20
When you start doing so please add some comments
But in my opinion the wifi has improve.
I will keep watching for comments
Thanks

---

### Post by eddietours on 2009-10-21
sorry to jump in my Gazelle has the similar range problem anything more then 20 feet drops, l have a Belkin N+ router but l usually use the wired

---

### Post by thomasaaron on 2009-10-21
Does it do that with other access points?

---

### Post by showgun22 on 2009-10-21
Similar problem with mine even after replacing wifi card.
But I believe upgrading to Karmic has improved it.
If you do upgrade to Karmic can you please post your result 
if it does improve or even if you believe it did not.
thanks

---

### Post by eddietours on 2009-10-21
let me try with the live cd of Karmic

---

### Post by ShowMeGrrl on 2009-10-23
This is just a general comment. I watch the System76 Support wiki and find that there are a fair number of people who report less than robust wireless range with Gazelles and Starlings. 

I do not know whether this is a problem with System76 machine design, antenna design, the wireless cards being used, the firmware, the routers or access points, the Ubuntu OS, the drivers or what. 

But I would like to urge Ubuntu and System76 to work hard on this problem, because wireless connectivity is an extremely high priority for most laptop and netbook users. It is the one thing that gives me pause about System76 machines. 

As I said above, I don't know the origin of the problem or problems, but it seems critical to me that it be addressed. System76 machines should connect equally robustly to wireless networks in libraries, cafes, hotels and homes as do other computers. It is not comforting to be told that it is the hotel's fault, etc. etc. etc.

---

### Post by jmwink on 2009-10-26
Just to chime in: though it's a bit too early to say definitively, the replacement wireless card in my Gazelle is performing with 150% more consistency, reliability, and signal strength. For what it's worth.

---

### Post by thomasaaron on 2009-10-27
> This is just a general comment. I watch the System76 Support wiki and find that there are a fair number of people who report less than robust wireless range with Gazelles and Starlings.


First, it's important to realize that the any problems with the Gazelle and Starling are completely unrelated.

The next thing to realize is that the Starling problem was fixed. And we have many hundreds of Gazelles out there that are reporting *no* problems. The two or three that appear on the forums definitely seem to be somewhat isolated.

> I do not know whether this is a problem with System76 machine design, antenna design, the wireless cards being used, the firmware, the routers or access points, the Ubuntu OS, the drivers or what.

As far as the Gazelles go, it's hard to say. Since it isn't an across-the-board problem, though, we tend to take these on a case by case basis.

> But I would like to urge Ubuntu and System76 to work hard on this problem, because wireless connectivity is an extremely high priority for most laptop and netbook users. It is the one thing that gives me pause about System76 machines.

Of course that is understandable. But again, people tend to post on forums when there is a problem. From a tech support perspective, though we look at how many machines we have out there vs. how many report problems via phones/email/forums in analyzing these sorts of things.

> As I said above, I don't know the origin of the problem or problems, but it seems critical to me that it be addressed. System76 machines should connect equally robustly to wireless networks in libraries, cafes, hotels and homes as do other computers. It is not comforting to be told that it is the hotel's fault, etc. etc. etc.

Good points, and typically they do.

---

### Post by ShowMeGrrl on 2009-10-28
Yes, you have a good point that forums attract posts from people who are having problems rather than from the thousands who are not having problems.

And I do agree that the System76 driver fix definitely improved the wireless performance of the Starling.

But as much as I love my Starling, I still find that it does not connect as well to wireless networks as does my Lenovo R60 laptop. I would call the Starling wireless "adequate," but I think it could be improved. 

I don't want to chide anybody. I think System76 does a great job. Ubuntu also is wonderful.:)

I am trying to express that wireless performance should be a very high priority for any portable computer. And when other computers are connecting to wireless networks without difficulty and a System76 computer is not, that is a problem that needs to be addressed. 

What originally stirred me to post was this statement:

"We get calls and emails quite often about hotel wireless problems. For whatever reason, hotel networks are pretty consistently problematic for a lot of Ubuntu users."

If hotel networks are "pretty consistently problematic for a lot of Ubuntu users," that is something that I want to see Ubuntu address very urgently. That is the essential point of my post.

---

### Post by jmwink on 2009-10-28
I have a week of use on the replacement card, and things are working gangbusters here, and even did on a conference trip I took this past weekend. Didn't try any hotel wireless spots, but I was on a couple different networks. Smooth like gelato.

---

### Post by thomasaaron on 2009-10-29
ShowMeGrrl,
> 
But as much as I love my Starling, I still find that it does not connect as well to wireless networks as does my Lenovo R60 laptop.

Correct. And that somewhat to be expected, at least if the problem can be traced to the distance from the access point. When you compare wireless performance between computers, it's important to compare apples to apples. I believe one of our forum members (JML?) did a study for us in which he compared the Starling (with the wireless fix in place) to another netbook (...and I don't remember which one off hand) and found them to be very comparable in wireless performance.

There are physical design differences between laptops and netbooks that seem to effect wireless range (antenna area, etc...).

That said, I would definitely like for that *NOT* to be the case. Netbooks are primarily meant for Internet usage. So hopefully this is something that will improve in the future... sooner rather than later.

As for the hotel wireless issue, I'm not exactly sure what the problem is. I can only really address it from an anecdotal perspective as 1) I don't stay in hotels very often, and 2) I've only had maybe a dozen requests for hotel networking issues in almost 3 years.

These problems are particularly difficult to analyze, as it is difficult to gather accurate information about what equipment a hotel has and how they have it set up. (I've always suspected though that many hotels probably don't have a highly-trained / active IT staff to maintain things and troubleshoot issues. And who knows how old their equipment is? (Access points wear out, get intermittent and fail. I *do* see that all the time.)

To go straight to the heart of your comment, though, I don't really know how Ubuntu could work on hotel wireless issues. I'm pretty sure it's not something they are very concerned with.

The best I can do on it is try to help folks out on a case-by-case basis.

---

### Post by ShowMeGrrl on 2009-10-29
Thanks for the response, Thomas. Thank you for explaining that it's to be expected that laptops would have better wireless range than netbooks.

Also pleased to that you do place a priority on wireless performance:

"Netbooks are primarily meant for Internet usage. So hopefully this is something that will improve in the future... sooner rather than later."

I still believe, however, that if hotel networks are "pretty consistently problematic for a lot of Ubuntu users," that's something that Ubuntu SHOULD be concerned with. 

People travel with computers these days and when they travel they usually stay in hotels and motels. If Ubuntu users can't get connectivity in these situations, why would people want to have Ubuntu as their OS? Why wouldn't they want an OS that would not have that problem?

---

