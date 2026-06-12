---
title: "I have finally ditched Windows"
date: 2007-02-23
forum: The Cafe
---

### Post by floke on 2007-02-23
My fellow forum-ers,

I have been using Ubuntu since October 2006 and can now announce that I have finally taken the plunge and deleted my Windows partition.

No more dual booting (not that there was any dual booting ever going on :) ) (well I am still dual booting between Edgy and Feisty, but no more Windows in my life as of now).

This feels very good!

:guitar:

---

### Post by rolando2424 on 2007-02-23
That's good :D

I also haven't booted to Windows in a few months, I only keep it around because I'm just too lazy to remove the partition :D

---

### Post by PartisanEntity on 2007-02-23
Great news! :)

I too ditched windows not too long ago. I think I also started using Ubuntu and Linux for the very first time around October 2006 and deleted the windows partition about a month or so later, never looked back.

---

### Post by maniacmusician on 2007-02-23
Great, welcome to the club!

---

### Post by Minyaliel on 2007-02-23
*shrug* Good for you, I guess.

---

### Post by PurplePenguin on 2007-02-23
I kept my windows partition without even touching it for about six months, just in case I wanted to play Ghost Recon. :)  Which I did maybe twice.  Good game! :)  But now Windows is gone, Sabayon is in its place, and I've even got some PCLinuxOS action going on in another partiton.

---

### Post by RedSquirrel on 2007-02-23
Good for you. :) I used to dual boot windoze and another linux distro on this box, but I wiped them both out with Ubuntu. No regrets.

---

### Post by ~LoKe on 2007-02-23
Ditched Windows cold-turkey over a year ago.  Never had any regrets, or any reason to go back.

---

### Post by steven8 on 2007-02-23
> **Minyaliel said:**
> *shrug* Good for you, I guess.

Try to keep it down to a dull roar please.  :) 

That is very exciting, and meshes with my announcement of the same.  My wife tonight had me transport her bookmarks into Firefox from the demon AOL, and she is ready to make the big switch!!  As she said tonight, she found she could do everything she needed to do in Open Office, and just needed to make sure the internet would work for her.  She says I can dump windows!!

Yahoooo!!!:guitar:

---

### Post by tgalati4 on 2007-02-23
That's great news.  Now you get to carry the radio.  Don't forget the beret and the bandolier.  Oh, and watch your head on the way out.  We must continue the struggle against oppression.  Remember, we're doing this for the children.   Viva la Ubuntu!

---

### Post by Bloch on 2007-02-23
When I first started using linux (it was Libranet, 2004) I joined the forum and announced myself.

Someone called Morgoth replied within seconds:
"Welcome over from the Dark Side."

Those were the days.

---

### Post by floke on 2007-02-24
[QUOTE=steven8;2202525]

That is very exciting, and meshes with my announcement of the same.  My wife tonight had me transport her bookmarks into Firefox from the demon AOL, and she is ready to make the big switch!!  As she said tonight, she found she could do everything she needed to do in Open Office, and just needed to make sure the internet would work for her.  She says I can dump windows!!

Congrats back to you!

---

### Post by steven8 on 2007-02-24
> **Steve.K said:**
> [QUOTE=steven8;2202525]

That is very exciting, and meshes with my announcement of the same.  My wife tonight had me transport her bookmarks into Firefox from the demon AOL, and she is ready to make the big switch!!  As she said tonight, she found she could do everything she needed to do in Open Office, and just needed to make sure the internet would work for her.  She says I can dump windows!!

Congrats back to you!

Thanks!  It is so good to be free!  :)

A question.  Did you just delete your windows partition and everything just worked at boot?

---

### Post by X-626 on 2007-02-24
To those who have ditched Windows, you're lucky...I wish I could get rid of Windows.  However, my dad and step mom still use it (though, with how it's been acting lately, they *may* allow me to remove it...I hope). I just wish I was good at persuading people..so I can get rid of it.

---

### Post by floke on 2007-02-24
Yep - just deleted it (the whole thing was over too quickly, I wanted a bit of a 'I'm killing you' moment, but GParted is just too damned efficient!); then made it into ext3; then rebooted as usual and then edited my grub file to remove the entry for XP.

The new partition is called 'dead windows' on my Desktop until I figure out what I want to do with it.

---

### Post by steven8 on 2007-02-24
> **Steve.K said:**
> Yep - just deleted it (the whole thing was over too quickly, I wanted a bit of a 'I'm killing you' moment, but GParted is just too damned efficient!); then made it into ext3; then rebooted as usual and then edited my grub file to remove the entry for XP.

The new partition is called 'dead windows' on my Desktop until I figure out what I want to do with it.

I like the title. :)

> edited my grub file to remove the entry for XP.

That was the info I was looking for.  I figured I'd have to do something so GRUB wouldn't look for xp anymore.

Thanks.

---

### Post by pirothezero on 2007-02-24
> **X-626 said:**
> To those who have ditched Windows, you're lucky...I wish I could get rid of Windows.  However, my dad and step mom still use it (though, with how it's been acting lately, they *may* allow me to remove it...I hope). I just wish I was good at persuading people..so I can get rid of it.



What do they use the computer for? If its simple stuff that can be done on xubuntu you should live cd it for them.

---

### Post by X-626 on 2007-02-24
> **pirothezero said:**
> What do they use the computer for? If its simple stuff that can be done on xubuntu you should live cd it for them.

Mostly just for the Internet, but the reason I can't ditch Windows is a little more complicated than that.  I'd probably need an entire topic (although, I've talked about it before in IRC, so I know a little of what I could do).

---

### Post by floke on 2007-02-24
to edit grub first make backup:) 

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup

then

sudo nano /boot/grub/menu.lst

remove that Windows POS forever

enjoy!

:popcorn: 

PS: You must be v. persuasive - I have another PC that I wanted to scrub clean of XP but my wife won't let me do it - show me your methods!

---

### Post by steven8 on 2007-02-24
> **Steve.K said:**
> to edit grub first make backup:) 

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup

then

sudo nano /boot/grub/menu.lst

remove that Windows POS forever

enjoy!

:popcorn: 

PS: You must be v. persuasive - I have another PC that I wanted to scrub clean of XP but my wife won't let me do it - show me your methods!

Backup.  Got it.  I use gedit, but otherwise it looks the same.

As to my persuasiveness, I didn't really have to do anything.  Microsoft did it all for me.  I explained the direction Microsoft was going with their new operating system and a few informational speeches about DRM.  That's all it took.  My wife is very idealistic, and doesn't like monoplistic, unfair business practices.  So here we are in Ubuntuland!  :guitar:

---

### Post by floke on 2007-02-24
'tis a pleasure to live here with you sir!

Regards to your wife, she has the right idea (mine still prefers the land of the 'doze for some inexplicable and never understandable reason - although she is a convert to Firefox, so at least that's a start).

---

### Post by steven8 on 2007-02-24
> **Steve.K said:**
> 'tis a pleasure to live here with you sir!

Regards to your wife, she has the right idea (mine still prefers the land of the 'doze for some inexplicable and never understandable reason - although she is a convert to Firefox, so at least that's a start).

Your wife will come through.  Mine was afraid the way Microsoft wants us all to be afraid.  Like we can't get along without them.  She just had to see that we can.

---

