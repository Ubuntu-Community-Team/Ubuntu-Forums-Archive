---
title: "Thinking about flashing my router."
date: 2010-05-03
forum: The Cafe
---

### Post by Slug71 on 2010-05-03
So im thinking about flashing our router with DD-WRT. We have a WRT-54G2 V1 router and have been streaming netflix with no problems until yesterday when we had a few buffering interruptions. Probably about 10 actually. We do plan on getting a better router in a few months but figured id flash this one till then.
I've heard of some people having issue with DD-WRT though and say Tomato is better.?
So need some input regarding this and will DD-WRT/Tomato on its own make my router faster? 
We have cable internet.

Thanks in advance.

---

### Post by swoll1980 on 2010-05-03
Make sure you know 100% what your doing, and that the new firmware will work. You only get one shot at it. If you find out you were wrong the router will be a paper weight.

---

### Post by jetsam on 2010-05-03
I've only used Tomato.  Tomato is the Ubuntu to dd-wrt's Debian.  It takes care of 90% of the set up and installation decisions.  It works well, and has a great interface and an extremely good bandwidth monitoring setup...  There's also one small proprietary part to the firmware... I think it's the web interface or something.  That might make some people uncomfortable in a core security appliance, but it's still leagues better than using the stock firmware.

From my impressions, as I've never installed it, DD-WRT gives you more control over what you install and don't install, but that control comes with some added complexity.  There are more places you can stub your toe with dd-wrt.  There are also many more things you can do with it.  

Talking router?  If I wanted one, I'd start with dd-wrt.  A hybrid router/file-server is a bad idea, but one that a lot of people want, and dd-wrt would be a better place to start for that as well.  

I'm sure they both work fine out of the box for a reasonable stock install.  At some point, it becomes just a matter of personal preference.

---

### Post by Brent0 on 2010-05-03
I'm running DD-WRT on my Linksys WRT-160n and it's working perfectly. I honestly don't know much about the firmware but it lets me do a lot more than the standard Linksys junk. It even let's me increase my signal strength. If you want to install it, just make sure that it's compatible with your router and don't forget to do a "30,30,30" reset before you install. [URL="http://www.dd-wrt.com/wiki/index.php/Supported_Devices"]http://www.dd-wrt.com/wiki/index.php/Supported_Devices 
[/URL]

---

### Post by NCLI on 2010-05-03
DD-WRT is great. It's kind of like Debian. Slow development, but very stable, at least for me, not to mention that the interface is great.

You don't need to do any configuration, as it should work out of the box, but if you do go into custumizing it, I think you will be pleasantly surprised with the incredible power you suddenly have to make your Router do *exactly* what you want it to.

I run it on a WRT610N and a WRT54GL.

---

### Post by cariboo on 2010-05-03
I've had dd-wrt installed on a Linksys wrt-54gs, for about a year, about three months ago it crashed after a power bump, to the point where it took 3-4 hours to reboot. I got a little upset at that, and just went out and bought another router. After letting it sit for a week or two I decided to see if I could track down the problem, when I plugged it in it booted in the normal time, so I'm at a loss as to why it was behaving the way it did, it's now running as an access point 24/7 I had to reboot it last week as it wasn't being detected wirelessly by my laptop and netbook, but otherwise I haven't had any other problems.

Dd-wrt is wonderful software, but it almost has to many features for the normal user. 

If it stays reliable for the next six months, it'll go back to being my main router.

---

### Post by mobi on 2010-05-03
> **Brent0 said:**
> I'm running DD-WRT on my Linksys WRT-160n and it's working perfectly. I honestly don't know much about the firmware but it lets me do a lot more than the standard Linksys junk. It even let's me increase my signal strength. If you want to install it, just make sure that it's compatible with your router and don't forget to do a "30,30,30" reset before you install. [URL="http://www.dd-wrt.com/wiki/index.php/Supported_Devices"]http://www.dd-wrt.com/wiki/index.php/Supported_Devices 
[/URL]

Same here...no probs with ddwrt on my wrt54g

---

### Post by chriswyatt on 2010-05-03
Last week I flashed a Netgear DG834GT (With custom Sky Broadband firmware).  The official Sky firmware was basically rubbish and not fit for purpose, used to constantly have to restart it and it wouldn't share the bandwidth equally.  It was ridiculous how many times I had to reboot the bleddy thing.

Updated to the unofficial NGTeam firmware and it's made a massive difference in terms of both speed and stability.  Obviously risky trying unofficial firmware but I was getting so fed up with the crappy internet connection and it constantly saying "Waiting for ..." and then timing out.

Got one problem that if there are internet problems my housemates press the reset button at the back which resets to factory defaults (they don't realise it's a complete reset), wasn't such an issue with the Sky firmware as it reset to the default encryption and password which we were using anyway.  I left a note asking them not to do it but someone keeps doing it still and this wipes all the ADSL settings off, and I have to stick them on again which is a pain.

Anyway, it might not make such a big difference for you but sometimes firmware updates can make a night and day difference (either by improving performance or turning it into a brick) :)

---

### Post by jetsam on 2010-05-03
I've only had to restart Tomato a few times.  It's far more common for me to have power/cable problems than internal network troubles.  

The only bad thing about restarting Tomato is you lose the bandwidth usage history, but you can set it up so it backs that stuff up periodically.

All the freezing problems have gone I think anyways since I disabled wireless.  It's a real old router, so I could increase reliability by upgrading to a WRT 54GL (is that what the newish hacky one is called?)  I'm thinking of upgrading to higher speed (wireless non-draft n, 1000bps wired, so I keep delaying the purchase decision, waiting for a clearly supported hackable router to appear... and contemplating just making one in a shuttle box and switching to moonwall.)

Check the tomato forums if you wanna see something impressive.  One post in particular talked about an apartment building installation with lotsa unpredictable torrent using clients that was reliable through duct tape and the only rational expectation--> periodic failure and super fast recovery.  Maintanence required: find the frozen AP and reboot it.  If it smells smoky, throw it out and pull another one off the shelf...

---

