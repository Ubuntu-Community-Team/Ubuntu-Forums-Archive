---
title: "oh... sigh.."
date: 2006-06-28
forum: Ubuntu Women
---

### Post by cara on 2006-06-28
Ok so my boyfriend threw me head first into Ubuntu a week ago.
I don't mind. Really.

All I use the computer for is world of warcraft, email, and some website browsing. I don't have much time to spend on the computer every day, and Ubuntu is fun. I like it. The problem I have is he keeps changing things. First, we ran warcraft with wine on its own separate hard drive. I guess he was mad that it was laggy and what not. I didnt care. I could raid, I could quest, it worked fine.
The next day, he had it dualbooted with winxp. 
Now I can't boot into win to play wow at all. 
He said he had to delete some windows files for something he had to put on that drive.
Now, he goes to bed when I'm gettin home from work, so when I come onto the machine, it's like a brand new thing every time. I have to waste time learning stupid things that I shouldn't need yet. I'm still new. I don't know how to do all the stuff he says will get warcraft running.

So I am at a loss for what to do. I don't want to reinstall windows, and I dont know how to find things that should be simple to do. all I need to do is move the warcraft folder from the ntfs drive to the fat32 one.. but I cant for a few reasons.  My knowledge is so limited and all he tells me is *read stuff, youll learn*
I've been reading for about 6 hours. This is supposed to be my day off where I can relax. But all it's turning into is a bitchfest.
I guess I'm just mad that he keeps changing thigs and doesnt fill me in on what he did. I'm frustrated that I cant play wow, and now he says that hes not even going to fix it anymore because hes done playing.

Yeah, I just needed to vent about this to other people that have [probably] been in my shoes.

---

### Post by aysiu on 2006-06-28
Tell your boyfriend, "Get me some basic functionality first. Then I'll read."

---

### Post by cara on 2006-06-28
[QUOTE=aysiu]Tell your boyfriend, "Get me some basic functionality first. Then I'll read."[/QUOTE]

i think i know most of the basic stuff. My problem is that I'm too paranoid to try things. Like I did attempt to move some files around so i could play  warcraft.. and it didn't work. i couldnt find the path for the file i was moving. i thought it would be under *properties* but i guess not.  :confused: 
but instead of moving his files, i'm just gonna delete em. theyre nothing special anyway.

delete - that IS one thing i know how to do ;D

---

### Post by aysiu on 2006-06-28
You can move files graphically with a little copy and paste action with your mouse.

If you need temporary root privileges, you can do that, too.

Something to read:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by cara on 2006-06-28
[QUOTE=aysiu]You can move files graphically with a little copy and paste action with your mouse.

If you need temporary root privileges, you can do that, too.

Something to read:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)[/QUOTE]

ooh! that nautilus thing in the link! i was looking for something like that.
so much easier to browse the computer.
you dont want to know how i was doing it before. rofl.

thanks.

---

### Post by cara on 2006-06-28
IT'S COPYING!!!!!!!!!!!


lol caps because i am happy. haha.

that was so much easier than doing the terminal cp -r thing.


woooohooo. 

thank you ;D

---

### Post by kingcharles1666 on 2006-06-28
cara, have you got your own profile set up or are you sharing one?
this way at least you can log on with your own profile and your boyfriend will not be able to change your personal settings, e-mail, chat, music library, etc, etc.
give yourself admin rights though.

---

### Post by cara on 2006-06-28
[QUOTE=kingcharles1666]cara, have you got your own profile set up or are you sharing one?
this way at least you can log on with your own profile and your boyfriend will not be able to change your personal settings, e-mail, chat, music library, etc, etc.
give yourself admin rights though.[/QUOTE]

hes not changing any of my settings. i really dont have anything to change! haha. all i do is play warcraft.. and thats broken :/


but i do have another question. 
how do i format a drive? i looked in system > admin but really didnt see anything.

---

### Post by aysiu on 2006-06-28
```
sudo aptitude update
sudo aptitude install gparted gksu ntfsprogs
gksudo gparted
```

---

### Post by az on 2006-06-28
I made my wife very happy a few years ago when I bough a used computer for mucking around with.  Now her computer is always the same as the day before (and I typically run a slow computer).

---

### Post by cara on 2006-06-28
aahhh lucky you. i have no money for another computer, or else that is what i would do. have one machine for dedicated gaming and one for everything else.
hopefully in the future :)

---

### Post by cara on 2006-06-28
[QUOTE=aysiu]```
sudo aptitude update
sudo aptitude install gparted gksu ntfsprogs
gksudo gparted
```[/QUOTE]

ok great

my boyfriend is awake now, so ill make him reformat it.

thanks aysiu

---

### Post by az on 2006-06-28
[QUOTE=cara]aahhh lucky you. i have no money for another computer, or else that is what i would do. have one machine for dedicated gaming and one for everything else.
hopefully in the future :)[/QUOTE]
I mean old and used.  Twenty bucks......

---

### Post by skirkpatrick on 2006-06-28
First, you beat him senseless with the keyboard and when he comes to, tell him that if he doesn't leave your computer alone, you'll stick it somewhere where he cares if it's working or not!

---

### Post by cara on 2006-06-28
[QUOTE=skirkpatrick]First, you beat him senseless with the keyboard and when he comes to, tell him that if he doesn't leave your computer alone, you'll stick it somewhere where he cares if it's working or not![/QUOTE]

hahaha.

well we managed to fix it.. somewhat. now warcraft is being patched.. again... so ill have to fix it again anyway! haha. (patching wine for wow at the moment)

but things are working great.
got the drive formatted and warcraft is on its very own drive :)
it better stay that way!

---

### Post by MiKuS on 2006-06-29
good to hear you got it all going ;) 

after a while of playing around with linux using command line will become more and more natural to you. after about 6months you will look back at the progress you have made in using linux and think how you didn't feel confortable doing this sort off stuff and laugh :D 

also, don't be scared to try certain things, the more often you bork your install the more often you're forced to fix it (don't just opt to re install either, this isn't windows :P)

---

### Post by Biltong (Dee) on 2006-06-29
[QUOTE=skirkpatrick]First, you beat him senseless with the keyboard and when he comes to, tell him that if he doesn't leave your computer alone, you'll stick it somewhere where he cares if it's working or not![/QUOTE]

Things are twice as bad when you are an Ubuntu user in a Windows household. He's forever telling me I have strayed from the Microsoft path.:wink: 
Of course, when I get my shiny new Dapper CDs I know for a fact that he will want to try one out, so we will finally see for sure who strayed off what path...:lol:

---

### Post by cara on 2006-06-30
[QUOTE=MiKuS]good to hear you got it all going ;) 

after a while of playing around with linux using command line will become more and more natural to you. after about 6months you will look back at the progress you have made in using linux and think how you didn't feel confortable doing this sort off stuff and laugh :D 

also, don't be scared to try certain things, the more often you bork your install the more often you're forced to fix it (don't just opt to re install either, this isn't windows :P)[/QUOTE]

i broke the sound before.
he didnt like that :/

even tho i have no idea what i did! all i was doing was watching movies

---

### Post by skirkpatrick on 2006-06-30
Well, I'm the computer guru in my house.  It has always been Windows but my and my daughter's machines are Ubuntu.  But I do know that the machine needs to be setup for use by the person that uses it for the way they want to use it.  My son runs XP for all the games he plays and my wife uses Win98 because of the one game she really enjoys.

---

### Post by cara on 2006-06-30
[QUOTE=skirkpatrick]Well, I'm the computer guru in my house.  It has always been Windows but my and my daughter's machines are Ubuntu.  But I do know that the machine needs to be setup for use by the person that uses it for the way they want to use it.  My son runs XP for all the games he plays and my wife uses Win98 because of the one game she really enjoys.[/QUOTE]


yes, now we have winxp for games and ubuntu for internet.
it works, i like it.

---

