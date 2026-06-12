---
title: "I need help with Wine deficiencies for Linksys wireless N router..."
date: 2011-03-07
forum: Wine
---

### Post by rainbowagent7 on 2011-03-07
Hi all. I just purchased a Linksys E3500 wireless N router and am having problems running setup.exe from the disc in Wine. The file is marked as an executable and I can get Wine to open it, but immediately I get an error message saying: "the program setup.exe has encountered a serious problem and needs to close. we are sorry for the inconvenience.". I'm sure it is due to missing libraries because at this point my Wine program only includes itself and Winetricks, I have added nothing else. I looked on [http://appdb.winehq.org/](http://appdb.winehq.org/)  and Google for any info on this device and wireless N in Wine in general, but the results were very disappointing. I'm fairly proficient in Ubuntu and can keep up when being instructed, but have not used Wine much and at this point am asking for someone to either point me in the right direction or walk me through the steps necessary to avoid damaging this very nice router.Thanks in advance. Also, this just feels like a good time to thank everyone who has helped me here in the past, keep rockin' !



                                                                                                                                                        :guitar:

---

### Post by Tweak42 on 2011-03-07
Are you sure you need to use the utility off the disc?  I could not find reference to a E3500 Linksys router on their website, but I have never heard of any router tied to a outside utility to get it setup, hence the lack of entries in the winehq appdb.

It is likely the included disc is for absolute beginner level picture walk through tutorials, troubleshooting and printed manuals.  All configuration should be able to be done via the routers web interface.  

Out of the box, connect using a wired line instead of wireless; navigate to the web admin interface; then configure the wireless (enable security) and then test.

Regarding damage, it is possible to lock yourself out of the router by losing the password, but there is a wipe/reset-to-factory procedure for that.  I would not be concerned about software damaging the router, but more accidentally burning one out by mixing up the power adapters with another device.

---

### Post by rainbowagent7 on 2011-03-07
Thanks Tweak. Actually, I should have mentioned that this is my first "real" encounter with setting up a router, aside from my Sonicwall which has never been up and running due to firmware issues. Now that I think about it, I remember accessing the console via web browser. Anyway, I officially feel like an artard now, thanks for pointing out what should have been obvious to me. I'll just give this a whirly-go and see what happens now, and in the meantime I hope no one reads this post, ever:-]

---

### Post by rainbowagent7 on 2011-03-08
p { margin-bottom: 0.08in; }  Alright I'm back with success. Thanks for your time Tweak. I was able to configure the router by booting into Windows and running the set-up disc there, also creating a USB flash key to set-up any other computer on the network. I then re-booted into Ubuntu and it fired right up. At first I tried to access the router through the web browser, but it required a password??? So I tried the generic "admin" and "password" as the username and password respectively, but to no avail. After realizing it was inevitable, I booted into windows and let it have it's way with my computer as I stood by watching helplessly, writhing in agony over the endless pop-ups and gut turning flashiness. After that was over I took my computer into the shower with me and after about an hour or so I got out, toweled off and hooked back up (okay maybe I exaggerated a little) Everything seems to be running very well now, much better than before actually. I'll make a note of the settings Windows applied because all in all I don't know that much about networking yet, but am quickly learning. Truth be told I'm pretty noobish in a lot of areas, and self taught too which doesn't help much. It's amazing how any hardware can be utilized with enough time applied to researching things, sorry I'm still a fairly new Windows convert (loyal though!) so this is a new concept to me. 

Anyway, before I turn this into some endless string of babbling I'll end with a [COLOR=#ff0000]noob note[/COLOR] (for struggling noobs): if you have made it this far reading my post, that means you really want to figure out a solution to your problem and that's all it takes in Ubuntu. You can have all the amenities of Windows and it feels a zillion times better knowing what's going on "behind the curtain" of your machine, but you have to get in and figure out what's what by researching these forums and Googling things. So just hang in there. Also, if you're having trouble opening the router interface via web browser try connecting an ethernet cable from your computer to the router, I left mine off after pulling the existing one to put into the router and didn't realize it for a while. Anyway, it might save someone some time:-]

[COLOR=#ff0000]Final note:[/COLOR] sorry to all if this post contains inane babbling and unexplained time gaps or other phenomenon, I'm running off of about 5 hours sleep in three days and to be honest am feeling a bit funny. I don't recommend to anyone that you do that.


:guitar::lolflag:

---

