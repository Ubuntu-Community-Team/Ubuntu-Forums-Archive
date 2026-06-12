---
title: "panickedthumb is panicked!"
date: 2005-04-04
forum: The Cafe
---

### Post by TravisNewman on 2005-04-04
Oh crap! What the heck!

The power went off today, and though I have a UPS, I havne't figured out how to get Ubuntu to cooperate with it, so when the UPS ran out, the computer shut down hard.

When I got home from work, I turned it on, and I got
DISK BOOT FAILURE. INSERT SYSTEM DISK AND PRESS ENTER

which came right after
Updating ESCD...........................Success
Verifying DMI Pool Data...............Update Success

These messages come up when I've installed new hardware ONLY.
It usually says only "Verfying DMI Pool Data... Success" not "Update Success" and the ESCD message doesn't come up at all, unless I install new hardware.

Now, here's the thing, I usually get two messages where it's trying to boot from cd, then it boots my hard drive. But those messages don't come up at all. I can't boot from floppy, I can't boot from cd, I can't boot from hard drive. 
I've tried changing the boot settings to set the first boot device to all the possibilities. I've reset the defaults. Nothing.
HELP!

---

### Post by Whiffle on 2005-04-04
Does your motherboard have the little trouble lights on the back?  Mine has a set of 4 lights that light up red or green, and theres a table in my manual that tells what code means what, its been useful a number of times.  

What kind of computer is it btw?

---

### Post by TravisNewman on 2005-04-04
It's a panickedthumb computer ;) Built it myself. It's an AOpen motherboard, about three years old. Athlon XP 1800+, Maxtor hard drive

No, no lights. But it's not a POST issue, so I'm not sure they'd help anyway.

---

### Post by Gandalf on 2005-04-04
hmmmmm that's so weird that you cannot boot from devices, when the computer start booting, it detects primary and secondary IDE as it suppose to do it, or not?

---

### Post by bored2k on 2005-04-04
[QUOTE=Gandalf]hmmmmm that's so weird that you cannot boot from devices, when the computer start booting, it detects primary and secondary IDE as it suppose to do it, or not?[/QUOTE]
 Following wise man's post, are you 100% the system is saving your Bios Settings -boot settings- ? Maybe reset the lil' battery by removing it for a while and retry?

Whatever it is, something's for sure: after you're able to boot from disc, you'll need  HDD Regenerator/Hiren's Boot v6..

---

### Post by Gandalf on 2005-04-04
[QUOTE=bored2k]Following wise man's post,
[/QUOTE] lol :D :lol:

---

### Post by TravisNewman on 2005-04-04
I'm not sure the hard drives are bad.

And yes, the devices are getting detected properly.

And again, yes, the settings are being saved. I think. I'll check that in a few ;)

---

### Post by Gandalf on 2005-04-04
[QUOTE=panickedthumb]I'm not sure the hard drives are bad.

And yes, the devices are getting detected properly.

And again, yes, the settings are being saved. I think. I'll check that in a few ;)[/QUOTE]
 ok i had this one once, (don't remember exaclty, i'm talking a 5 years story), and i tried (if i remember well) to switch some drives on the IDE which will force CMOS recheck/update, try it maybe !!!! but i doubt that

---

### Post by bored2k on 2005-04-04
[QUOTE=panickedthumb]I'm not sure the hard drives are bad.[/QUOTE]

Dude.. Hello? 3rd world country here, meaning I "have" experienced several power failures with my *noir* working full speed.  Even if you are able to boot back to Linux, I suggest you run what I call a "Hiren's check" on your drive, as sometimes HDD take some jabs but are too shy to just "stop working". Boy I remember the day my UPS betrayed me.. while installing AuroX Linux 10Beta.. that HDD was never the same :-#.

---

### Post by Gandalf on 2005-04-04
[QUOTE=bored2k]Dude.. Hello? 3rd world country here, meaning I "have" experienced several power failures with my *noir* working full speed.  Even if you are able to boot back to Linux, I suggest you run what I call a "Hiren's check" on your drive, as sometimes HDD take some jabs but are too shy to just "stop working". Boy I remember the day my UPS betrayed me.. while installing AuroX Linux 10Beta.. that HDD was never the same :-#.[/QUOTE]
 you mean sudo badblocks /dev/hda???

---

### Post by TravisNewman on 2005-04-04
ok, it just took some rest ;) Letting it sit with no power, no battery, nothing for a few minutes cleared everything up.

I'll give it a hiren's check, though I probably won't gheck for bad blocks unless I notice some stress or corruption. That's a lot of strain on a hard drive (and the user's patience ;))

---

### Post by Gandalf on 2005-04-04
[QUOTE=panickedthumb]ok, it just took some rest ;) Letting it sit with no power, no battery, nothing for a few minutes cleared everything up.

I'll give it a hiren's check, though I probably won't gheck for bad blocks unless I notice some stress or corruption. That's a lot of strain on a hard drive (and the user's patience ;))[/QUOTE]
 BTW just to tell a weird story that happended to me last week (in the occusion of mentioning badblocks ;) )lol sorry for the off-topic

in case if you don't know, i ran my own server for my website (better than paying hosting) and everything was working fine, the HDD was working like a charm, a week ago, the cron job that make a backup of files/sql has been executed and  for some reason, every single file that have been touched by the backup task, it was a badsector i just woke up the morning found my site givin an error that he can't access the databse, turn on the screen and see the charm, errors messaged running like if someone behind them wants to kill them lol, so i just changed sessions and begin to get back some of the files since the backup was 8 days older, i succeded to get 75% of mysql databses (most important ones) that's all, ok backup them ran badblocks /dev/hdb waited 6 hours and finaly stuck with 4 gb out of 80 without bad blocks and really that's weird to happen in one night!!!!! the HDD is working for another task now, holding my cigaretes :D lol

---

### Post by bored2k on 2005-04-04
That sucks, specially when a website depends on it. Did a lot of members noticed it [while it was happening]?

BTW, by cigarette you mean your pipe right ? ;)

---

### Post by poofyhairguy on 2005-04-04
[QUOTE=panickedthumb]ok, it just took some rest ;) Letting it sit with no power, no battery, nothing for a few minutes cleared everything up.

[/QUOTE]

Put it in the fridge. Sounds stupid, but I've saved a PS1, a wireless access point, a gameboy, and a satillite receiver by letting it sit in the fridge overnight...

---

### Post by bored2k on 2005-04-04
[QUOTE=poofyhairguy]Put it in the fridge. Sounds stupid, but I've saved a PS1, a wireless access point, a gameboy, and a satillite receiver by letting it sit in the fridge overnight...[/QUOTE]
 Are you serious lol. This would get it all wet = not good. Duracell batteries seem to receive a FF Phoenix Down when put on a fridge though..

---

### Post by poofyhairguy on 2005-04-04
[QUOTE=bored2k]Are you serious lol. This would get it all wet = not good. [/QUOTE]

The fridge not the freezer!

[QUOTE=bored2k]Duracell batteries seem to receive a FF Phoenix Down when put on a fridge though..[/QUOTE]

LOL!!!! Good reference.

---

### Post by bored2k on 2005-04-04
The fridge not the freezer![/quote]
That's my english knowledge betraying me right there *grr*. My bad.
[QUOTE=poofyhairguy]LOL!!!! Good reference.[/QUOTE]
Gamer @ Heart ;) .

---

