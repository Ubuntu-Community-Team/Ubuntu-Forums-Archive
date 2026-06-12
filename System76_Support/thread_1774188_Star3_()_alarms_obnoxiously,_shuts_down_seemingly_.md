---
title: "Star3 (?) alarms obnoxiously, shuts down seemingly spontaneously"
date: 2011-06-03
forum: System76 Support
---

### Post by Ms.N on 2011-06-03
Hi there,

I bought my Starling in early September of 2010 (so I believe it's a Star3, but if that's not what sys76 was shipping then, please correct me). In probably January, it started this odd behavior: within a few minutes of waking from a suspend, it will start blaring the alarm tones that it only ever also emits when the battery has gotten to a critically low level. However, during the periods it engages in this quirk, it will do it regardless of how much charge the battery actually has left. And, just as if the battery attached indeed had almost no charge, it will subsequently shut itself off. 

If I simply turn it back on, it will, within a few minutes (usually just enough for me to log in as one of the users), start the alarm sound again and shut down. By the way, plugging it in once this behavior starts is not helpful; shutdown will still happen. 

I think that what may kick it off each time is the netbook getting jostled, usually by being put in and taken out of a computer bag for travel, whether around town or by air. It never happens whenever the machine's just been sitting around my desk or even carried to another room in my home, only when it's been taken out and about, in a bag. 

I have never been able to figure out well at all what stops the behavior.  It seems to just...go away somewhat by itself, each time. On my end, I usually will have swapped out the battery (I bought an additional 6-cell with the machine), sometimes swapping from one to another a couple times, and done several reboots to try and get it to behave, with several instances of the machine doing the very same thing and shutting itself off again, including the audible fanfare. Then eventually, it starts normally and stays booted, with no evidence of wanting to blare the battery alarm...that is, until its next bout (maybe 3 weeks later?) of bad behavior. So, I have always had some assumption that it may be a problem with the battery seating properly.

Today, it started the behavior again. But this time, several reboots and battery swaps haven't fixed the issue. In fact, although it usually waits until I've logged onto one of the accounts (and it doesn't matter whether it's a primary or secondary user) to start the blaring noise and shutdown, now it starts all that by the time the login screen is pulled up. I've even pulled out the battery entirely and am still getting the same behavior running it only on AC power, with no battery at all.

Since I'm writing, I'll mention that I have enjoyed the Star overall. Maybe that just makes me very patient, but truly, it feels sturdy, and I like its form factor. The fan sometimes runs a little loud, but I'm willing to put up with that. I haven't gotten heavily into learning the capacities of Ubuntu, but the system does everything that I need it to, particularly since I still have a couple machines running Windows and so don't find it crucial to find Linux workarounds if one is not immediately obvious. Also, besides potentially this odd power-down issue, I have not had problems with battery life; although the charging/charge remaining icon is not consistently accurate, that's not a dealbreaker for me, either, and the batteries I have get the life I expect them to, regardless of what the charge icon says.

However, it is a dealbreaker that my machine can't be counted on now to work consistently or without disturbing others around me due to its unpredictable and uncontrollable alarming.  So I'd love not only for it to stop having the spontaneous shutdown problem but also would like to figure out how to turn that low-battery alarm off for good (or at least change to a different tone for it that would be less piercing). When that alarm is sounding as a "normal" function (the battery actually is low), a popup occurs to show me anyway...and when it's sounding because of this malfunction, it's still not really helpful, since the problem isn't actually that the battery is low.

I believe I am still on 10.04 UNR, as the netbook shipped. I've allowed Upgrade Manager to update the machine as needed but don't recall changing Ubuntu versions.

I have noticed no prior mention on this forum of my issue. I'd love some help, so thanks in advance!

---

### Post by isantop on 2011-06-03
I think you're having heat issues. Can you try blowing the fan vent out with compressed air?

---

### Post by Ms.N on 2011-06-07
Hello!

Many thanks for your response. :)

I did as you suggested, and I'm amazed (and embarrassed) that that seems to have solved the problem for now. I have been running it for a few days that have included taking it out and about quite a bit...and there's been no repeat of the blaring-alarm-and-shutdown issue.

Is it still going to need the kind of service where the casing gets taken apart, though, and if so, would system76 do that? Also, I'd still love to turn that alarm off, or at least down by quite a bit. Would it be possible for you to tell me how to achieve this?

---

### Post by isantop on 2011-06-08
As long as the problem has gone away, there isn't any need to take the case apart. As for muting the alarm, I don't think that is possible, as it is a fairly critical system function.

---

### Post by Ms.N on 2011-06-08
Hi there,

Great---so if I understand correctly, what I need to do is blow compressed air into the fan vent regularly...and my problem was just that I needed to maintain the hardware better. Is that right?

And also, if you don't mind my asking, what critical system function is the alarm signaling: "imminent shutdown"? I'm really only curious at this point. It's just so remarkably loud, and nothing that (as an also-Windows user) I'm used to experiencing.

Thanks again!

---

### Post by isantop on 2011-06-09
The Alarm is the critical system function. It signals that there is a problem with the computer at a physical level; in this case that it was too hot. It's roughly equivalent to the check engine light in your car.

---

### Post by Ms.N on 2011-06-10
I think I'm clear now.:) Thanks for your time, and I'm marking this solved!

---

### Post by Mr.DNA on 2011-12-16
I understand an obnoxiously loud alarm sounding when the computer becomes too hot.  That seems like a legitimately critical system function.  But is the alarm really necessary when the battery is critically low?  I think that is ridiculous, and am surprised no else has mentioned it on the board.  I love my wife's Star3 with this one major exception.  I no longer bring this starling to any professional environment for fear of the battery running too low.  Normally, with any other netbook/laptop/tablet/phone, I should only need to be worried that if the battery runs out in the middle of a class or meeting, then I will simply be unable to continue using said device for the duration of the meeting; instead I have to worry that I will create a major disruption.  

Is there really no fix for this?

---

### Post by isantop on 2011-12-19
In most cases, the system will hibernate before it starts beeping. In the event that it doesn't, the beeping provides a warning alarm that the battery will die within one minute, so you can save your work and shut down safely.

Make sure that the system isn't set to hibernate too late. Adjusting this setting should alleviate the beeping.

---

### Post by Mr.DNA on 2011-12-26
Thanks for the reply.  This sounds like a solution, however I cannot seem to find the setting you describe.  In the power management settings, I can set to either "shutdown" or "suspend" when battery power is critically low.  Critical level is not adjustable and whatever it is preset to is lower than that which triggers the alarm.  

This is my first battery-powered ubuntu system, so maybe I am missing something somewhere else in the system settings?  Currently running 11.04.

---

### Post by isantop on 2011-12-27
Go ahead and open the power dialog box, then take a screen shot with the PrtSc Key. Post that here, and I'll see if you have the settings required.

---

### Post by Mr.DNA on 2011-12-27
Done.

---

### Post by isantop on 2011-12-27
You should be able to disable the alarm on low battery from within the BIOS configuration. It's located under Advanced.

To get to the BIOS configuration, reboot the computer. During the System76 Splash page, press F2 repeatedly. This will load the BIOS configuration.

---

### Post by Mr.DNA on 2011-12-27
Here is a noodle-scratcher:  the alarm was already set to [disabled] in the BIOS...

---

### Post by isantop on 2011-12-28
That is strange. That tells me that the battery isn't actually low. 

This sounds like a calibration issue. Let the laptop charge fully, wait an addition hour or so to ensure a complete charge, then let the laptop run down completely until it shuts off. Do this a few times, and the problem should correct itself (assuming this isn't actually a heat issue).

---

