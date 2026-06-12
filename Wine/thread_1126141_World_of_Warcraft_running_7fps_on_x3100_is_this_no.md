---
title: "World of Warcraft running 7fps on x3100 is this normal?"
date: 2009-04-15
forum: Wine
---

### Post by gackt on 2009-04-15
Hi guys i'm using lenovo y410 with 1 gig of ram, intel onboard x3100 (or 1300 I'm not sure but i believe it was intel mobile 965) and 1.8 gig dual core of processor. 
I'm playing WOW with average 7fps (I'm not using opengl since it was crashed with intel chip) is this normal?
How do I increase the fps? Sometime when i enter a building in the game the fps could jump to 20-24 but out side it always 7. 
I'm ready to sacrifice the quality even more (i already set the lowest for all graphic), so what can i do?
Thanks

---

### Post by khelben1979 on 2009-04-15
In what screen resolution are you running this game? If you can't use Wine with the -opengl extension the game will get very slow even if you had a graphics card for like 500$ inside that computer, so I think it's normal, unfortunately.

Let's see if someone else has something to say about this also.

If it were on a Windows machine you would get better performance. Look [here]("http://forum.notebookreview.com/showthread.php?t=133881"), unless there's a special fix for this.

---

### Post by binbash on 2009-04-15
If you do not use -opengl it is very normal to get 7 fps.

---

### Post by gackt on 2009-04-15
Thanks, so is there anyone manage to run WOW in opengl with x3100?

---

### Post by jenova_skill on 2009-04-15
I have a 1.9ghz x2 with radeon x1250
When i didn't have Opengl working properly *3d gfx* not working i was getting 7fps as well  
After  i got my card working properly I was getting 17-25fps average
in windows it was about the same be 4 i kicked it off the cpu *wink*

It is very tricky to get your grafix drivers and wine to run in sync with each other .. After you get it working tho it's worth it IMO

---

### Post by asdfoo on 2009-04-15
> **gackt said:**
> Thanks, so is there anyone manage to run WOW in opengl with x3100?

If you are talking of the Intel x3100, make sure you have compiz disabled, if it's still bad then blame the Linux drivers because currently they are not as good as the Windows counterpart.

---

### Post by gackt on 2009-04-16
> **jenova_skill said:**
> I have a 1.9ghz x2 with radeon x1250
When i didn't have Opengl working properly *3d gfx* not working i was getting 7fps as well  
After  i got my card working properly I was getting 17-25fps average
in windows it was about the same be 4 i kicked it off the cpu *wink*

It is very tricky to get your grafix drivers and wine to run in sync with each other .. After you get it working tho it's worth it IMO

Could you elaborate more on this?

@asdf00 yes it is intel x3100 the compiz is surely off but the performance still poor.

---

### Post by Monkey Brawler on 2009-07-13
X3100 is being pretty stubborn as far as linux goes. I cant even get a solid frame. My screen is all broke up and distorted and i cant even login. Its hittin me pretty hard, id love to find a fix. o and yea, i have tried the Opengl fix.

---

### Post by nandnor on 2009-07-14
you might want to use a light xp distro instead, like microxp or tinyxp, compact but good performance

---

### Post by ThisEndlessFall on 2009-07-14
You should switch back to Hardy Heron. Jaunty has broken Intel drivers.

---

### Post by Monkey Brawler on 2009-07-14
> **ThisEndlessFall said:**
> You should switch back to Hardy Heron. Jaunty has broken Intel drivers.
I wouldnt mind doing that but theres also another thread out there with the same issue and the guy did everything but backflips with his hands tied behind his back. However, theres no real need to swap to Hardy per say. Tonight im gonna try rolling back to intel 2.4 drivers, if that dont work i might try Hardy.

---

