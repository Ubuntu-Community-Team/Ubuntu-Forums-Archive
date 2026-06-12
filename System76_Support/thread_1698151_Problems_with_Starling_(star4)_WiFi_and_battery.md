---
title: "Problems with Starling (star4) WiFi and battery"
date: 2011-03-01
forum: System76 Support
---

### Post by pshmell on 2011-03-01
I just bought a star4 Netbook last month. I've been having a few problems that have continued to frustrate me lately...

My wifi periodically disconnects for no apparent reason. It seems that while a DHCP lease has been established, the network controller fails to route packets. I can confirm this by *ping*ing my router @ 192.168.1.1, which normally yields a 30-70% packet loss, depending on my distance from the router. Nobody else in the household (some of whom also run Ubuntu) have this problem. I have tried using wicd instead of NetworkManager to no avail. This is a *very* frustrating problem, to be in the middle of uploading photos, reading the news, or chatting with family and friends, and have my connection spontaneously drop. The strangest thing is that the issue occurs when the laptop is in a static location, just sitting on my table. Even when I am not even touching the machine, it will pop-up a notification that says "Connection lost..."

Another minor issue is that the battery will not report "Time until charge" or "Time until discharge". When I look at the battery monitor, it just reports "0 seconds" for both. Seems like it would be quite a simple calculation. It does read out a charge percentage, but no time...

Thanks!
Paul

---

### Post by pshmell on 2011-03-01
Sorry for the double post, but I'm so frustrated right now. I'm in my bedroom, no more than 20 meters from the router, and I can't get a damn connection. I had to come upstairs and stand next to the router in order to type this message.

This is unacceptable for a $400 purchase.

I don't blame Ubuntu, or System76, I blame myself for not doing enough research before making my purchase.

---

### Post by msrinath80 on 2011-03-02
I feel for your problems. And it's nice to see someone willing to step up and take the blame on themselves for a change. That said, come to think of it I've noticed that among System76's offerings, the Starling, Pangolin and Serval rank among the highest in reported issues. I own a first generation Lemur myself. I will admit, the build quality is a little shoddy. And I think there's little they can do about it given that the chassis comes from ODMs such as Clevo/Compal etc. However, the out of the box support for GNU/Linux is awesome. Clearly this is the main reason why I'm not completely regretting this purchase. Just my 0.02$

---

### Post by EJJ on 2011-03-02
For about a week I had no wifi on my Starling. The solution, strange as it was, turned out to be very simple. I deleted my router (Labeled 'Home") from the edit connections menu. I then reconnected it and set it to auto. No problems since. You might want to try that.

With open source software/OS/etc and small companies such as System 76, we need to give them as much info as we can on their products so they can continue to better it for everyone. So patience is a must with this stuff sometimes (especially if we want Ubuntu to be a more competing OS next to apple and microsoft...which I feel it already is.) So yes it is unacceptable for a $400 purchase--but there's always a solution.

Try booting from a live disc to verify whether the issue is software, or hardware related. If it's hardware, S76 will help you out. 

As far as the battery....

There has been a problem with the indicator as to how much life is left. There was a thread about this issue and I believe System 76 is looking into it.

System 76's customer service is way too good to be legal, so do get in touch with them on this issue.

---

### Post by isantop on 2011-03-02
I'm sorry you're having issues. Let's try and get those worked out for you. Try pressing Fn+F11 to turn the wireless card off, wait a few moments for it to disconnect. Then press it again to turn the card back on. That might help it out.

---

### Post by pshmell on 2011-03-02
At the risk of sounding like a pompous ***, I  consider myself a fairly seasoned Linux user. I built a server at 14 and configured and ran it on my own as a secured and encrypted HTTP, POP, and SMTP server for years. I ran Ubuntu as my primary operating system, too, starting back when Ubuntu was still a baby in 5.04.

I've tried all the things you would expect. I've tried downloading Windows drivers and making modules out of them with ndiswrapper. I have most certainly tried the soft-key networking controls. As far as I can tell, it seems to be a hardware issue, but when I get a chance I will try EJJ's recommendation of booting from a USB key or something.

---

### Post by PWill on 2011-03-02
Ah, I finally remembered my password for my old account.

This is the Ubuntuer formerly known as pshmell. I'll post from this account from now on.

---

### Post by pocklecod on 2011-03-03
I'm having an identical issue on my starling netbook.  Turning the wifi off and back on, along with deleting and restarting the connection have no impact.  I've been using Ubuntu for a couple of years, though I'm a pretty basic user.

I do have a couple more details that might be of help.  For me, the Starling has been working fine for several months, using a variety of different networks in my home, at the library, coffee shops and so forth.  I haven't noticed any issue until something changed.  My brother has installed a new Linksys e4200 router at his place.  The thing is super-fast and working great on all other machines...but not mine.  As the previous poster, I can hum along with no problem for a couple of minutes and then, complete stop for no reason.  Connection still established, signal still strong, machine not moving.  My brother's Macbook has absolutely no problem, and is blazing along, so it's definitely not the router or the ISP.

In addition, the new router sets up both a regular network and a 'guest' network that allows access via a web password.  If I switch back and forth between these two, I can get connectivity back temporarily.  So, basically, I get a few minutes on the first network, switch to the second, get a few more minutes, switch back and get a few more minutes etc.  That seems particularly odd, and doesn't seem consistent with a hardware problem to me since the thing does work very well and very fast for these brief periods.  Both networks are from the same router.

One last curious fact, I decided to install whatever Ubuntu updates were available to see if that might help, and during the download it seemed that each time I switched networks I would get around 10 megabytes of download before the complete stop.  This number wasn't completely consistent, but in the ballpark just about every time.  

So, it seems that there is a problem with this specific router for some reason, and my guess is there is something odd in the software on my machine that is causing it to refuse further packets from the network after a certain period.  Why that could possibly be, I don't know, and I'm not advanced enough to find out.   The other routers I use frequently don't give me any trouble.  I know my brother's new router is 'N,' where the older routers I usually use might not always be - so perhaps this has something to do with it?  The starling is advertised as N capable, but it's possible there is a glitch in that somewhere.  Or, maybe it's something else completely.

Help would be greatly appreciated.  As the last poster mentioned, this is very frustrating, especially since I've been talking up my System76 all-ubuntu choice for quite a while now, and this just makes the thing look crappy.

---

### Post by PWill on 2011-03-03
pocklecod, sounds like my problem exactly. People keep asking me, "How do you like your netbook?"

I want to say "I love it!" (because I do!) but it makes me feel so silly when I'm asked to look something up and I have to say, "Sorry, the WiFi isn't working right now..."

---

### Post by Roush 427r on 2011-03-03
> I also have the same problem, I haven't really noticed it since yesterday, but it usually always happens whenever I open up the star4 lid, and come out of screenlock. In example, I was browsing eBay for an HTC android phone to replace my dad's old phone, left it on the page and started watching Red. I got halfway through the movie, before I paused it and shut the laptop as I went to dinner. After coming back trying to show something to my grandfather on the news, I couldn't connect to my network which was really frustrating and pretty embarassing because he is the one who bought it for me and it appears to him that he spent .5k USD on something that 'doesn't' work. Hopefully S76 can work out this bug relatively soon! I haven't connected to wifi for a day now, and can't see any networks despite ubuntu saying that the Wiress card is turned on, networking is turned on, and wireless is active.

Scratch that, my mistake. I did the Fn + F11 trick to turn on my Wireless card and bam, I got on the internet.

---

### Post by isantop on 2011-03-04
Try making sure the router is set to either G/N Mixed mode, or G-only, and see if that helps the connection.

---

### Post by PWill on 2011-03-04
> **isantop said:**
> Try making sure the router is set to either G/N Mixed mode, or G-only, and see if that helps the connection.

Ah, I have not tried that. I'll give it a go when I get home.

---

### Post by Carleas on 2011-03-05
I have a similar problem, but it doesn't last for any real length of time.  For example, I play speed chess online, and the connection will drop for about 10 seconds during most games, but it usually comes back in time for me to be beaten fair and square.  It's not just that site though, it happens while streaming movies and downloading.  It doesn't seem to happen as often for me as the other posters have described, though many may simply being going unnoticed when I'm reading the news or posting.

I tried fn+f11, but wasn't able to turn it back on.  It disconnected me, but never reconnected me when I pressed it again.  I ended up restarting.  Which led me to wonder: if this were a problem that turning the wireless card on and off would solve, wouldn't a restart solve it as well?

---

### Post by PWill on 2011-03-07
So I've been experimenting. My home router doesn't have a b/g/n mixed mode--it's n-only. That shouldn't be a problem, though, since the 8191 supports 802.11n.

I tried changing some settings on my router (packet sizes, broadcast channels, etc.) but the problem persists, and my connection drops pretty regularly every 5 to 10 minutes. Before the connection actually drops, it first slows down. It will start dropping packets (losing about 10% of them) and working its way up to 100% packet loss over the course of about a minute. The only thing I can do to bring it back is running `sudo rmmod r8192se_pci && sleep 2 && sudo modprobe r8192se_pci', which works flawlessly every time, and gets me back online in a few seconds.

As I see it, I have three options:
* Write a new driver for the 8191 (or bug someone who knows C better than myself to do so)
* Return the netbook and buy from a different company
* Buy a new halfmini PCI express wireless card that is know to work with Ubuntu. I'm assuming this option would void my warranty, though. Currently, I'm looking at the Intel Ultimate N 5300 for about 30 bones.

---

### Post by PWill on 2011-03-07
After a night of hacking (reading through kernel logs and skimming through the source code of the rtl8192se_pci module) I think I finally isolated and solved the problem.

These are the interesting lines from kern.log
> Mar  7 09:10:05 Eden kernel: [ 5091.026150] ==============>rtllib_associate_procedure_wq():ieee->**current_network.qos_data.qos_mode is 0,ieee->qos_capability is 1**
Mar  7 09:10:08 Eden kernel: [ 5093.511877] ====>rx ADDBAREQ from :30:46:9a:12:e0:06
Mar  7 09:10:08 Eden kernel: [ 5093.511891] rtllib: Failed to reply on ADDBA_REQ as **some capability is not ready(0, 1)**

So, the card seems to be trying to communicate that while it has the capability for QoS enhancement, the wireless access point is not routing packets that way. When I realized this, I kinda freaked out since my router doesn't have QoS. I remembered something interesting, though: even while my HTTP connections were flaking out, some torrents I had running in the background were still downloading...because I had forwarded the ports for my IP address! So I went into my router settings page and forwarded port 80 for my IP, and now I'm browsing with super speed and no dropped connections.

Anyways, I'm going to file a bug at launchpad anyways with the Realtek drivers. It doesn't make sense that the card should drop strong connections just because packets aren't being prioritized.

---

### Post by pocklecod on 2011-03-08
PWill

  Thanks so much for this!!  It's clear from your second description that our problem is absolutely identical as my experience of 10% packet loss down to nothing is the same as well.

  I will try the port forwarding fix next time I visit my brother and hopefully it will work.  I'm content with this kind of solution since I'm pretty much just a joe-beercan end user type.  Hopefully System 76 or someone else can cook up a complete solution or at least make sure this problem doesn't persist into newer models.  It's pretty important for their machines to be able to run "N," since they are advertised that way, and I must say I rather resent the System 76 solution above which basically amounts to 'use G instead of N.'  That might get me online, but it doesn't give me the full functionality I was promised on this machine.

  Anyway, thanks again.  It sounds like this should work.

---

### Post by isantop on 2011-03-08
Trying G/N mixed mode instead of G- or N-only is more of a diagnostic step. If it works better there, then we know it's an issue with the card firmware, and where to fix the problem. It also provides a workaround for the interim while we get the issue resolved.

I can't remember if this is happening on several routers, or only one? If it's specific to one router, then my guess is that the issue may be with the router. If it happens with multiple routers, then it could be a bad card, which we can replace for you.

---

### Post by pocklecod on 2011-03-14
Thanks for the clarification on the G/N thing.

For me, the problem is with one specific router, which is a Linksys e4200.  Other routers I use frequently are not creating problems, and the e4200 is not creating problems for anyone else in my family.  So, I don't think it's hardware on my netbook, and it's not a faulty router.  It has to be something in the software on my Starling somewhere.

Does the code cited by pWill help with this problem?  Is there a permanent fix to what he observed?

---

### Post by pocklecod on 2011-04-09
So, just to update, port forwarding doesn't seem to do anything for me.  Same problem persists.

The Linksys e4200 I'm trying to connect with is N only, so no mixed mode or G mode is available.

---

### Post by pocklecod on 2011-04-09
Second update today - and some good news this time!

Looking a bit more closely at PWill's last post, I disabled QoS altogether in my router, and now my connection from the Starling is working great!  So - something is going wrong here with the way the starling is interacting with QoS settings.

This is progress, but not a complete solution.  We do use the router in question to stream netflix, and ideally I would like to be able to enable QoS settings to prioritize this streaming (the router came from the factory doing just that).  I poked around on the starling for a while, but I'm not expert enough to figure out how to change the setting that PWill referred to wherein the Starling doesn't think my router is using QoS.  From Pwill's post, my guess is that this might just be as simple as changing a 0 to a 1 somewhere in a settings file - but I don't have any idea which one or where to find it.

At least we're making headway, though...

---

### Post by tlroche on 2011-04-09
> **pocklecod said:**
> I disabled QoS altogether in my router, and now my connection from the Starling is working great[. But we] use the router in question to stream netflix, and ideally I would like to be able to enable QoS settings to prioritize this streaming

Presuming use in a home environment, and the router has a reasonably non-tedious UI (e.g., DD-WRT, Tomato), you could kludge-around this pretty easily. Just make a policy that

[LIST=1]
[*]allows only one MAC (the netflix box) on the network
[*]hardroutes all traffic (or just whatever port netflix uses) to the netflix box
[/LIST]

and toggle that policy on and off as needed. Admittedly suboptimal.

> **PWill said:**
> the card seems to be trying to communicate that while it has the capability for QoS enhancement, the wireless access point is not routing packets that way. When I realized this, I kinda freaked out since my router doesn't have QoS.

> **pocklecod said:**
> I'm not expert enough to figure out how to change the setting that PWill referred to wherein the Starling doesn't think my router is using QoS.  From Pwill's post, my guess is that this might just be as simple as changing a 0 to a 1 somewhere in a settings file

That's not the impression I get. Correct where wrong, but ISTM

[LIST=1]
[*]for pocklecod, routing fails when router has QoS enabled
[*]for pocklecod, routing works when router has QoS disabled
[*]for PWill, normal (soft) routing fails with a router that doesn't have QoS support
[*]for PWill, hard routing works with a router that doesn't have QoS support
[/LIST]

The impression I get is, bad routers. I Could Be Missing Something, though.

---

### Post by pocklecod on 2011-04-10
Right, so I'm already two steps ahead on the solution proposed here, at least for my situation.  Since I do have only one device that I want to prioritize, I set up QoS to favor the MAC address for my netflix Blu-ray player.  That's working well - so, in my particular case, this is an acceptable workaround.

Also, as the last post indicates, it does look like there are some differences between what's going on with me and what's going on with PWill.  That being said, though, both problems come down to issues with QoS, and the symptoms are basically identical.  So, they may be different forms of the same bug - a bug which is far too complex for me to understand, honestly.

I'm not sure, though, what is meant by a 'bad router.'  This simply isn't the case for me.  My brother's Macintosh was running blazing-fast on the router right out of the box, and the blu-ray player is working great.  The only problems have been on my machine - that means the problem is in my machine.

I'm hoping that I won't have to deal with problems in the future, but I'm a little worried that as N-only routers with QoS protocols become more ubiquitous, I will have issues again.  I'm particularly concerned that I will have problems with public routers, say at a coffee shop, where I don't have control of the router settings.  Basically, in my situation, the problem is in the software of my machine somewhere, and the fix was carried out by way of the router settings.  I may not be able to fix router settings for all the routers I deal with going forward.  It's possible that this simply won't ever actually manifest, but I'm hoping that System76 will keep looking into this problem.  The basic summary here is that the star4s are not as out-of-the-box compatible with N-routers as they should be.  I just want to make sure that this isn't written-off because, going forward, System76 will want to make sure these machines work right out of the box as much as possible.  I really think this is the tip of a bigger ice-berg which is starting to happen to people with very high-end new routers.  As those routers take over, this problem is likely to pop up more and more - just please keep an eye on it.

Thanks, everyone, for the help.  I'm glad I've got a workaround for me, at least.

---

### Post by isantop on 2011-04-11
I'm not very familiar with QoS, but can you add the Starling to the list of priority devices?

---

### Post by pocklecod on 2011-04-12
To isantop,

  For me, adding the Starling as a priority isn't really necessary.  What the QoS should do, as I understand it, is prioritize things like video streaming (like my netflix), or VOIP for telephone service - basically, things that you'd want to have first on the list for use of your bandwidth in the event that a lot of items tried to access that bandwidth at the same time.  Everything else is just treated 'normally.'  In my case, for the starling, and any other computer, it's fine to just have them duke it out for whatever bandwidth is available - I never do anything on my netbook that would really require first dibs on my bandwidth (like I would want my telephone to have, for example).  If I preferred, I could give the starling high priority using its MAC address - but there's no reason to do that for my situation.  It is worth noting, however, that that is possible with the Linksys e4200, just in case future users want to do that.

  Anyway, it may be worth doing some testing in the future regarding the starling machines and routers with QoS support.  Like I posted before, in my case I've got an acceptable workaround, but it's definitely something for you guys at System76 to keep an eye on going forward.  In the end, there's something not totally right about the starling4 and QoS systems which is causing packet loss and then loss of connectivity.  As I understand it, the goal is for these things to work right out of the box, and this is a case where it seems there could be some improvement.

  I hope that's helpful despite my very limited knowledge.  Frankly, the main reason I'm posting here at all is that I love what you guys do, I love running an all open-source system, and I want to see it keep getting better and better.  The fact that I'm just a jackass end-user with no programming knowledge is all the more reason for me to give some feedback since I'm basically the guy you're trying to win over.  So, I hope this can all make for better machines in the future.  Best luck.

---

### Post by macabrem on 2011-04-12
If I had to guess, I would say it is your wireless driver and not your router - based on your symptoms and past Starling history.

I didn't read the entire thread, but what wireless card is in the Star 4?  What has always worked for my Star 1, no matter what Linux OS I put on it, is by downloading compat wireless bleeding edge package, and then following the install directions to replace the prepackaged driver.  [http://wireless.kernel.org/en/users/Download](http://wireless.kernel.org/en/users/Download)

I think compat is in the Ubuntu repository too, but it is just as easy to download from above, extract, sudo make && sudo make install, etc.

---

### Post by TCWriter on 2011-04-13
I'm experiencing the same problem with my Star4 and my "Dlink Extreme" (why is everything "extreme" these days) router; the connection is constantly dumping, and getting anything done -- even when sitting literally 15 feet from the router -- is problematic.

Lacking a fix from System 76, I'll try turning off the router's QoS setting and see if that fixes things, though it's not a long-term fix. 

The Starling's a nice netbook, but too many little glitchy problems (like this) to recommend it to friends.

---

### Post by TCWriter on 2011-04-15
Just an update: I turned off the QoS on my router and my Starling hasn't dropped a connection so far today. That's not conclusively (talk to me again tomorrow), but it appears several prior posters have identified the problem.

Naturally, this isn't the greatest solution, but I hope System 76 is listening and looking for an answer.

---

### Post by TCWriter on 2011-04-26
I just completed a road trip with my Starling (Star 4); we stayed in two hotels and two houses, and in both the hotels - and one of the houses - my Starling's wi-fi largely failed. 

At the hotels, I could connect, but after a few minutes (to as much as twenty minutes), I'd lose all throughput -- even though the wireless network icon happily suggested I was still connected.

Re-connecting to the network bought me a few more minutes, but the only way to get anything done was to use my wife's Windows laptop, which never suffered an issue. 

Deleting the connection that that wi-fi network and creating a new one had no effect.

Given that I got my Starling to work at home by disabling the QoS on my home router -- and the problems I've experienced on the road -- it seems clear I can't trust this thing for travel, which is why I bought it. 

It seems like a kinda big issue; is there any hope of resolving it by upgrading to 10.10 or even 11.04?

---

### Post by pocklecod on 2011-06-10
TCWriter,

  This is my exact concern with the situation.  N routers are going to become more and more ubiquitous, and if we can't get this fixed at the level of the machine, our netbooks are going to be a disaster whenever we use a router we don't own.

  I've upgraded to 11.04 (which is working nicely on the whole)  I can try an experiment in the next couple of weeks to see if that fixes my problem with the E4200.  If so, then maybe the issue is resolved.  If not, this needs some much more serious attention than it seems to be getting.

---

### Post by isantop on 2011-06-10
I found a lead on a fedora forum that suggests this may be an issue with WPA supplicant, which is responsible for handling WPA encryption. It also suggests that it's linked to WPA supplicant version 0.6.8, which is current for Lucid. Natty has a newer version that may be much more stable with WPA and QoS.

---

### Post by TCWriter on 2011-06-10
> **pocklecod said:**
> TCWriter,

  This is my exact concern with the situation.  N routers are going to become more and more ubiquitous, and if we can't get this fixed at the level of the machine, our netbooks are going to be a disaster whenever we use a router we don't own.

  I've upgraded to 11.04 (which is working nicely on the whole)  I can try an experiment in the next couple of weeks to see if that fixes my problem with the E4200.  If so, then maybe the issue is resolved.  If not, this needs some much more serious attention than it seems to be getting.

I upgraded to 11.04, which didn't solve the problem for me; my Star4 frequently dropped the connection to my Dlink "Extreme" router, and in fact, it often exhibited a connection range of a measured 5 feet. 

I ditched the Dlink in favor of a Linksys E2000 (I think), and voila; everything works. 

Sadly, that's not the case around town; two of the four coffeehouse networks I exposed the Star4 to exhibited the same problems, and I'm reduced to carrying a USB dongle (the cheap TPLink seems to work the best) around in case the built-in Realtek wi-fi won't cut it. 

The USB dongle *always* works.

I'm not a particularly technical user of Linux so I can't troubleshoot it, but it seems clear the Star4's wi-fi has some issues, and while a USB dongle will solve them, it's not exactly elegant. 

Support has been relatively indifferent, and I'm not at all sure I'll be buying my next laptop from a Linux vendor.

---

### Post by zipmon on 2011-06-11
> **TCWriter said:**
>  I'm reduced to carrying a USB dongle (the cheap TPLink seems to work the best) around in case the built-in Realtek wi-fi won't cut it. 

The USB dongle *always* works.

Out of curiosity, which model of the TPLink dongle are you using, and did you have to do anything special to set it up in Ubuntu? I have similar problems with the WiFi on my Starling in hotels, coffee shops, etc. And while it works great at my house, I'm going on a research trip around the world in a month with the Starling as my only computer, so I really need a failsafe WiFi option - I'll definitely pick one of these up!

---

### Post by TCWriter on 2011-06-11
I have the [TP-Link TL-WN722N]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833704045&cm_re=tplink-_-33-704-045-_-Product") (which includes the "high gain" antenna, which can be a little awkward to carry). 

I believe the [WN727N]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833704041&cm_re=tplink-_-33-704-041-_-Product") is the same, but without the antenna (it's more compact, perhaps less range). 

(I included links to the products on Newegg.)

I just plugged it in (Ubuntu 10.10 and 11.04) and it worked immediately on both my Star 4, my old Dell Inspiron, and even my desktop machine (ZaReason). Amusingly, the more expensive Dlink USB connector didn't work very well, even with the Dlink router. 

Do have to manage the fact your internal is trying to connect too, so one extra step at startup (disconnecting).

---

### Post by zipmon on 2011-06-11
That sounds perfect, thank you so much!!

---

