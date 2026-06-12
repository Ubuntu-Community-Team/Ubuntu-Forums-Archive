---
title: "Am I going INSANE?!??!"
date: 2009-01-03
forum: Testimonials &amp; Experiences
---

### Post by i.dont.register on 2009-01-03
Alright this is my first post on these forums after very much enjoying Ubuntu since February 2008. The community here kick *** far beyond anything I have seen before. However there is one topic that I have not seen addressed on these forums no matter the search terms I use and this seemed like the most appropriate sub-forum.


Sometimes when I first start up my computer and hit Firefox + Pidgen I start to hear this song playing which would seem to be from the vietnam era. I have disabled all startup sounds, and looked at sessions for my account and whatever I can get my hands on. However it still *sometimes* plays when I start up my computer and load those apps. If i move my mouse it immediately kills the sound so it has been very difficult for me to reproduce as usually after I type in my login information I am trying to startup apps. Tonight it happened after *closed* Firefox after several hours of usage which was the first time it has ever happened in that manner.

Wow, this really confuses me. Why would some app decide to randomly play music in the background and stop when I move my mouse?????!?

---

### Post by Kevbert on 2009-01-03
If you open a terminal and then use
```
top
```
it may give you an idea as to where the sound is coming from as this will show all running tasks.

---

### Post by Martje_001 on 2009-01-03
Run this bash script:
```
while true; do
date >> processes
ps -e >> processes
echo "" >> processes
sleep 1
done
```
If you hear the sound, look at the clock and open the file 'processes' in your home-directory and look if the list differs from the second before you heard the sound.

Good luck! Sounds like someone is playing a bad joke on you, though ;)

Btw: Are you really sure it comes from your speakers? Did this happen with Windows?

---

### Post by sydbat on 2009-01-03
Short answer - YES!:lolflag:

Serious question - is it a song that you have on your computer already...like in your music folder? Also, when did this start? Was it as soon as you booted into Ubuntu the first time back in Feb? Or was it after installing something since then?

---

### Post by wolfen69 on 2009-01-03
> **i.dont.register said:**
> 
I start to hear this song playing which would seem to be from the vietnam era.

damn hippies and their long hair! :lolflag:

---

### Post by DforVendetta on 2009-01-03
Yeah and my computer always seems to play porn movies and goes to porn sites...

What's up with that :)

---

### Post by Tamlynmac on 2009-01-03
Insanity is only a state of mind.

Problem is - can't remember which state I left my sanity in...LOL

From one old hippie to another.

On a serious note, have you checked preferences/sound/sounds to see if someones turned on a audio file?

---

### Post by i.dont.register on 2009-01-03
I checked all the files in /usr/share/sounds/ and did not find any with the particular sound I am hearing.

> 
If you open a terminal and then use
Code:

top

it may give you an idea as to where the sound is coming from as this will show all running tasks.



I've seen the GUI version of this in System>Administration>System Monitor but that also seems useful thanks I'll be watching that.


> 
Run this bash script:
Code:

while true; do
date >> processes
ps -e >> processes
echo "" >> processes
sleep 1
done

If you hear the sound, look at the clock and open the file 'processes' in your home-directory and look if the list differs from the second before you heard the sound.

Good luck! Sounds like someone is playing a bad joke on you, though

Btw: Are you really sure it comes from your speakers? Did this happen with Windows?


Ill check this out too. Yes this is really coming from my speakers and it never happened in windows. I'm the only person using this computer (bachelor in NYC) so its not possible for it to be a joke unless someone has rooted my machine.


> 
Short answer - YES!

Serious question - is it a song that you have on your computer already...like in your music folder? Also, when did this start? Was it as soon as you booted into Ubuntu the first time back in Feb? Or was it after installing something since then?


This started happening about a month or so ago. I don't recall if it started after having installed any particular software. No it is not a file I already have on my computer (I only stream Pandora.)


> 
Insanity is only a state of mind.

Problem is - can't remember which state I left my sanity in...LOL

From one old hippie to another.

On a serious note, have you checked preferences/sound/sounds to see if someones turned on a audio file?


I checked the utility you mentioned and can see there are several system events which have sound events associated with them. However they are all set to either Default or Disabled. 



STRANGE!

---

### Post by stalkingwolf on 2009-01-04
> damn hippies and their long hair

I resemble that remark!!!!!

---

### Post by Tamlynmac on 2009-01-04
> stalkingwolf 	 		**Re: Am I going INSANE?!??!**
 		 	Quote:
 	 	 		 			 				damn hippies and their long hair 			 		 	 	 
I resemble that remark!!!!! 	


[COLOR=#2D4038][COLOR=#2D4038]"He[/COLOR][/COLOR]'[COLOR=#2D4038]s[/COLOR] [COLOR=#2D4038]an[/COLOR] [COLOR=#2D4038]old[/COLOR] [COLOR=#2D4038]hippie[/COLOR] [COLOR=#2D4038]and[/COLOR] [COLOR=#2D4038][COLOR=#2D4038]he[/COLOR][/COLOR] [COLOR=#2D4038]don[/COLOR]'[COLOR=#2D4038]t[/COLOR] [COLOR=#2D4038]know[/COLOR] [COLOR=#2D4038]what[/COLOR] [COLOR=#2D4038]to[/COLOR] [COLOR=#2D4038]do[/COLOR] Should [COLOR=#2D4038][COLOR=#2D4038]he[/COLOR][/COLOR] hang on [COLOR=#2D4038]to[/COLOR] the [COLOR=#2D4038]old[/COLOR] Should [COLOR=#2D4038][COLOR=#2D4038]he[/COLOR][/COLOR] grab on [COLOR=#2D4038]to[/COLOR] the new". I think there's a song in that.
:lolflag:

I also resemble that remark. +1

---

### Post by stalkingwolf on 2009-01-04
Insanity is hereditary.  You get it from your kids.


Insanity is relative.  You get it from your relatives.



:P:D

---

### Post by DarkReaper79 on 2009-01-04
Well, everyone is insane, it just depends on how you make it work for you:P

Also, could it be the login sound? I get it too, sometimes it get it, and others it dont play. system>preferences>sound, then the sound tab, login and click the little play button to the right of it. Is it the same sound??

---

### Post by olskar on 2009-01-04
Sometimes I get some kind of finnish waltzmusic in my speakers but I think that is am-radio or something, I get it in my guitaramp to :)

---

### Post by ubuntu27 on 2009-01-04
Check if the music that comes from the speaker is a song that it is stored on your computer.

I had a similar experience with my desktop computer.
From the speaker I could hear some radio talk show regardless of the operating system that I was using.

It seems that the speaker was capturing the signal from AM or FM radio.

---

### Post by 3rdalbum on 2009-01-05
My first thought was that you were hovering your mouse over a sound file on the desktop, causing Gnome to start playing it. I've done that several times accidentally and it has startled me :-)  Moving your mouse will stop the sound.

If it's not a sound file on your PC, then something weird is happening. Are you sure it's not on your computer? Are you sure it's not coming from next door? :-P

---

### Post by i.dont.register on 2009-02-12
> **3rdalbum said:**
> My first thought was that you were hovering your mouse over a sound file on the desktop, causing Gnome to start playing it. I've done that several times accidentally and it has startled me :-)  Moving your mouse will stop the sound.

If it's not a sound file on your PC, then something weird is happening. Are you sure it's not on your computer? Are you sure it's not coming from next door? :-P


You were correct! It turns out that a friend had sent me an MP3 over MSN and I let it rot within the disaster that is my desktop organization without ever even realizing it was there. I found the MP3 while doing some cleanup 2 days ago and had half the mystery solved. After reading your post it would appear that it was indeed the case that my mouse would be hovering over the icon and the music would play.

/look of disbelief/

I don't see how that could possibly be a useful feature is there a way to turn that off?

Edit: Also I cannot figure out how to mark a thread as solved. I modified the title for the original post but it doesn't show up in the main forum view.

---

### Post by wolfen69 on 2009-02-12
> **i.dont.register said:**
> 

Edit: Also I cannot figure out how to mark a thread as solved. I modified the title for the original post but it doesn't show up in the main forum view.

you can't mark it as solved right now. they are working on fixing the issue.

---

### Post by solwic on 2009-02-12
> **i.dont.register said:**
> You were correct! It turns out that a friend had sent me an MP3 over MSN and I let it rot within the disaster that is my desktop organization without ever even realizing it was there. I found the MP3 while doing some cleanup 2 days ago and had half the mystery solved. After reading your post it would appear that it was indeed the case that my mouse would be hovering over the icon and the music would play.

/look of disbelief/

I don't see how that could possibly be a useful feature is there a way to turn that off?

Edit: Also I cannot figure out how to mark a thread as solved. I modified the title for the original post but it doesn't show up in the main forum view.

Glad you got it fixed, and thanks for letting us know.  That was a strange issue you had, and I was anxious to hear what was causing it.  

As for that feature...I love it, though it can get annoying when you don't want it there.  :P

Cheers!

---

