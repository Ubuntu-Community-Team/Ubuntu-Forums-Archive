---
title: "Pangolin Value: No Display (Screen? Battery&gt;)"
date: 2009-02-10
forum: System76 Support
---

### Post by pacella on 2009-02-10
I bought a Pangolin Value in September 2006. It worked pretty well until about 6 months ago, aside from the battery life issues (which I realize could easily have been my fault), but about six months ago the screen went dark and I haven't been able to revive it, even when I run it off AC power and even when I plug in an external monitor. The battery light never varies from red, but the computer will definitely turn on and off, and the lights under the lightbulb icon and the WiFi icon display green.

I've been trying to figure this out on my own, but I have no idea what to try at this point. Any help would be great. Thank you.

---

### Post by pacella on 2009-02-15
I know it's lame, but I'm threadbumping in order to see if maybe this got overlooked. A lot of people have read this post, but no one has replied. Am I just missing something really obvious?

---

### Post by ctsdownloads on 2009-02-15
I think people need more information to be of much help. You have to be our eyes here. What was happening when it went dark?

1) Were you booting it then found for the first time it went dark?

2) Did it go dark during use in real time?

3) Did it go dark during a restart?

4) Has their been any physical trauma to the notebook itself? Lose lid, dropped, tripped on the cord, etc?

---

### Post by pacella on 2009-02-15
> **ctsdownloads said:**
> I think people need more information to be of much help. You have to be our eyes here. What was happening when it went dark?

Sorry. I'm far from an Ubuntu expert, and this is also the first laptop I've ever owned. It's hard to anticipate what's relevant.

> **ctsdownloads said:**
> 1) Were you booting it then found for the first time it went dark?

Yes.

> **ctsdownloads said:**
> 2) Did it go dark during use in real time?

No. I took it to a conference with me and nothing appeared on screen. That's the first time I noticed the problem. I assumed there as an issue with the battery.

> **ctsdownloads said:**
> 3) Did it go dark during a restart?

Perhaps. Not an intentional restart. It's possible that I hadn't shut it down correctly, but that would have been out of character for me. I'd had good luck with it during regular use for over a year before this problem started.

> **ctsdownloads said:**
> 4) Has their been any physical trauma to the notebook itself? Lose lid, dropped, tripped on the cord, etc?

Not that I'm aware of. The lid got scratched during shipping The keyboard wasn't connected properly when I first bought it, but the System76 folks were great about replacing for me. However, it got a bit nicked during transport either to or from. But it worked well since then for over a year.

---

### Post by jdb on 2009-02-15
> **pacella said:**
> Sorry. I'm far from an Ubuntu expert, and this is also the first laptop I've ever owned. It's hard to anticipate what's relevant.



Yes.



No. I took it to a conference with me and nothing appeared on screen. That's the first time I noticed the problem. I assumed there as an issue with the battery.



Perhaps. Not an intentional restart. It's possible that I hadn't shut it down correctly, but that would have been out of character for me. I'd had good luck with it during regular use for over a year before this problem started.



Not that I'm aware of. The lid got scratched during shipping The keyboard wasn't connected properly when I first bought it, but the System76 folks were great about replacing for me. However, it got a bit nicked during transport either to or from. But it worked well since then for over a year.

Have you tried running it from the charger without the battery??

jdb

---

### Post by ctsdownloads on 2009-02-15
> **pacella said:**
> Sorry. I'm far from an Ubuntu expert, and this is also the first laptop I've ever owned. It's hard to anticipate what's relevant.



Yes.



No. I took it to a conference with me and nothing appeared on screen. That's the first time I noticed the problem. I assumed there as an issue with the battery.



Perhaps. Not an intentional restart. It's possible that I hadn't shut it down correctly, but that would have been out of character for me. I'd had good luck with it during regular use for over a year before this problem started.



Not that I'm aware of. The lid got scratched during shipping The keyboard wasn't connected properly when I first bought it, but the System76 folks were great about replacing for me. However, it got a bit nicked during transport either to or from. But it worked well since then for over a year.

No worries :)

Speaking as a "retired" Windows PC repair tech, my "gut" says it might be hardware. But that is speculation without actually seeing it. I come to this speculation through age of the notebook, travel, previous hardware issues already.

Have you tried booting with a bootable CD? Are you seeing BIOS at all? Basically we need to determine if this is OS related or hardware. Failing bootable CDs and not seeing a BIOS would push into the faulty hardware category.

---

### Post by thomasaaron on 2009-02-16
Do you see the manufacturer splash page on the laptop's LCD when you turn on the computer? If not, it's probably hardware. If you do see the manufacturer splash page, your problem is likely a configuration issue.

Also, f you plug in an external monitor *first* and *then* turn on your computer, do you see the manufacturer splash page on the external monitor? If not, it's the graphics chip.

---

### Post by Jozza The Wick on 2010-04-26
Woah. I just had a very similar problem happen to me, on my Pangolin Performance.

I've had the laptop less than a year. No prior screen issues. Was using it on a flight when suddenly the screen 'scrambled' for a split second (random blocks of random colors) and then went black. I shut it down by holding the power key, tried taking out the battery, putting it back then restarting (tried this both on battery power, and since then on AC power). Screen stays back - no manufacturer logo, no BIOS, nothing.

However, at least once I've heard the Ubuntu drum sound, which means that it's booting properly - though it doesn't seem to do it consistently - I had to restart X (Ctrl-Backspace). I do have an external monitor at home but am away from home until next weekend. It does seem like a hardware issue, so my question is - if I'm able to confirm it as hardware once I get home, what's next? Can I ship it back to you for repairs?

Thanks!

---

### Post by thomasaaron on 2010-04-26
Does this occur in the System76 splash page? If so, contact me at support...at...system76...dot...com.

Also, you might try removing the ac adapter and battery and re-seating the memory cards. If it took a bump, and a memory card was jarred loose, you might get similar symptoms.

---

### Post by Jozza The Wick on 2010-04-26
Thomas,

Thanks for your response. I don't see the System 76 splash screen at all - the screen does not display anything at all when it's switched on. The only indication I get that the laptop is not completely dead (apart from the disk activity I can hear) is the Ubuntu drum sound.

I'll check the memory cards tonight and let you know what happens - thanks again.

---

### Post by Jozza The Wick on 2010-05-03
Quick update - my laptop works fine when plugged into my external monitor. I didn't see the Ubuntu splash screen or 'loading' animation (that orange bar) or the System 76 bios screen in fact, but saw my logon screen after a few moments. No problems using the laptop after logging in.

Haven't tried the memory cards yet - will let you know what (if any) difference that makes...

---

### Post by phyzome on 2010-05-03
Jozza The Wick,

Try shining a flashlight at an acute angle into the screen -- you might be able to see very faint graphics. If this is the case, your backlight is probably dead.

The fact that the first thing that shows up on the external monitor is the login screen indicates that your computer can see the built-in monitor -- it is switching to dual-monitor display at that point.

---

### Post by Jozza The Wick on 2010-05-03
Wow, phyzome, you're good :)

When I shine a flashlight on the monitor I can definitely see everything during bootup - the System76 logo, the GRUB menu and the loading animation.

At the login screen on my external monitor I can use Ctrl-Alt-F1 to switch to a terminal, and then see the text login prompt (with the help of the flashlight) on the laptop.

I noticed one of the hotkeys *should* turn the LED on and off, according to the manual (Fn-F2) but it doesn't seem to do anything.

So - what's the next step? How do I go about getting the backlight fixed?

Thomas - any suggestions?

Thanks again, Phyzome!

---

### Post by msrinath80 on 2010-05-04
If your backlight isn't broken chances are that the connection to the motherboard is flaky or loose. Either way, I suspect this is definitely a hardware problem. Wait for someone from System76 to confirm this.

---

### Post by isantop on 2010-05-04
Jozza The Wick:

email us at support...at...system76...dot...com

This definitely sounds like a broken backlight.

---

