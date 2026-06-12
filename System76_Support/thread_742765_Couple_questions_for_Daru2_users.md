---
title: "Couple questions for Daru2 users"
date: 2008-04-02
forum: System76 Support
---

### Post by LibertyShadow on 2008-04-02
I am considering buying a new portable laptop, and I am torn between the XPS M1330N, a Macbook, and the Darter Ultra.  I know If I purchase the M1330N or the Darter, I will probably wait until they are available with Hardy.

I have been searching the net religiously for feedback on the daru2, but I haven't had much luck... so I guess I will throw out random questions with the hopes that someone might answer!

-How is the battery life with wireless on? 
-Is it portable enough to be carried 1/2 mile from my (future)  apartment house to the Computer Science academic building daily?
-Do desktop effects work out of the box? (I have read about issues with Intel's GMA)  How is the GLX performance? Good?
-Does the N-wireless work (well)?
-Is it sturdy?
-How is the 12.1 inch screen?  Dell classifies its screens as Anti-Glare or Glossy... what is the Daru2 closer to?

Thanks in advance :)

---

### Post by reh4c on 2008-04-02
Hi,
Overall, I am happy with the Daru2 and ubuntu, except for flaky power management.  Based on my experience, here are some answers to your questions:
How is the battery life with wireless on?
Very good...well over 2 hrs.
-Is it portable enough to be carried 1/2 mile from my (future) apartment house to the Computer Science academic building daily?
Yes...reasonably portable.
-Do desktop effects work out of the box? (I have read about issues with Intel's GMA) How is the GLX performance? Good?
With Hardy...Yes.  Approx 1100 fps.  Not sure how that stacks up.
-Does the N-wireless work (well)?
Mine just has Intel A-B-G...not problems.
-Is it sturdy?
Yes..pretty solid.
-How is the 12.1 inch screen? Dell classifies its screens as Anti-Glare or Glossy... what is the Daru2 closer to?
Anti-glare I'd say.

I'm running Hardy Beta.  It runs well overall with some minor bugs.  Hope this helps!

---

### Post by Peneus on 2008-04-02
I have Daru2 too. I like to add one thing to reh4c's post. 
When I was searching for a laptop i thought 12'' is too small for me. But after using it for 5-6 months I think the screen size is fine. Overall I really like Daru2 too with one exception. The right and left clicks on the touchpad are too stiff for my taste. Other then that and the power management I think it is really a good machine.

---

### Post by theologian aaron on 2008-04-02
I have had my Darter since september, am a student, and can relate to all of your concerns.


> -How is the battery life with wireless on?

   I get over 3 hours mostly with moderate power management settings (I can use it for an entire 3 hour lecture without pluggin in).  If you turn everything down even more you can get 4 hours + (with wireless off, as you should not be checking facebook in class anyhow!)

> -Is it portable enough to be carried 1/2 mile from my (future) apartment house to the Computer Science academic building daily?

   I take mine to school with me every day on the bus or on my bike (about 7km each way).  It is a little smaller than the macbook and weighs a little less.  I bought it for its portability and have not been let down.

> -Do desktop effects work out of the box? (I have read about issues with Intel's GMA) How is the GLX performance? Good?

    In hardy they do, but even in gutsy it is very easy to get them to work with the directions listed here in the forums.

> -Does the N-wireless work (well)?

    I have a/b/g and have had exactly no problems, but cannot say for n.

> -Is it sturdy?

     Compared to other laptops, I would say the build quality is excellent.  Like I said, I take this thing everywhere and am not gentle with it.  It has had some drops and has survived my carelessness with nothing more than a few scatches.

> -How is the 12.1 inch screen? Dell classifies its screens as Anti-Glare or Glossy... what is the Daru2 closer to?


      It is a glossy screen that you can see your reflection in, and while  I was adverse to it at first, I am now used to it.  It is a good screen if you can live with the small size.


A few notes that may or may not help:

- The keyboard is wonderful.  I write many many papers, and find this more comfortable than any other small laptop I have ever used (the mac keyboard is HORRIBLE!!)
- The battery monitor has been an issue, but has been largely resolved though is still not perfect.
- This thing is not for games.  The screen is too small, the video card too weak, and the sound is not great out of the built in speakers.  If you want to do any gaming, even moderately, you will need to have something else to do it on.
- Finally, if you are serious about using ubuntu, and you should be because it's the best OS around, system76 is about the best company you could deal with.  The support is great, the people are helpful, and you are putting your money toward a company that is dedicated to the open-source revolution.  

Cheers, and welcome to the club!

---

### Post by pavel_987 on 2008-04-02
I have a Daru2 as well. I'm a student too, the laptop is so light that I carry it to class everyday, even though I don't really need it there.
I love the battery life, I easily squeeze out 3 hours out of it.
The laptop is pretty sturdy, I bought a nice carrying bag for it....then didn't use it. So I wind up just putting the laptop into my backpack. Which isn't the best idea. The paint around the edges started to rub off a little. Doesn't bother me because I kind of like the "good 'ol worn out' look.
Don't have an N card, don't know the screen specifics.

Unlike others, I seem to have a lot of beef with the laptop hardware integration. Here are my complaints:

- Power management !!!
- Sound = this one needs an explanation. The sounds works, there's nothing wrong with it in the fact that it exists and functions. I wouldn't say it functions correctly though. Using a default install the soundcard is detected and all the channels are set up properly. But the headphone jack doesn't work in the sense that the jack and internal speakers always output something (regardless if you have your headphones plugged in or not). System76 uses an alsa parameter to fix the jack thing. So when you plug in your headphone jack then the internal speakers mute. But with this setting, the alsa mixer reports extra channels, it doesn't report the internal microphone (effectively getting rid of that feature). Also, when having your headphone plugged in, there's a chance that you might unmute the internal speakers while adjusting the sound. e.g. if you have your headphones plugged in, then mute and unmute the master channel...then both the headphones and internal speaker will be unmuted.

Hardware that's built in but doesn't work with linux:
HDMI port
Finger print reader
Can't really blame System76 for this one. It's not listed in the specs so I never expected it to work.

I also can't seem to get S3 suspend to work. But I haven't monkeyed around with it in Ubuntu too much. So I can't say that it's a problem.

All in all it's not a bad laptop, I just wished the hardware worked in linux better.
What I find disappointing when a friend of mine started to tell me about his dell 13" xps. He tells me you can get everything to work, suspend, hdmi, fingerprint reader. But I can't confirm that. You should ask around yourself.

---

### Post by thomasaaron on 2008-04-02
pavel_987,

The Power Management issues is solved. Please follow these instructions (they work on either Gutsy x32 or Gutsy x64.

Make sure you're connected to the Internet.

From a command line, enter:
sudo wget [http://planet76.com/repositories/system76-driver-2.1.7.deb](http://planet76.com/repositories/system76-driver-2.1.7.deb)
sudo dpkg -i system76-driver-2.1.7.deb

Then go to System > Administration > System 76 Driver
Click the restore tab and restore button.

Reboot your computer.

---

### Post by ackey on 2008-04-02
I really must attest to the laptops portability.  I drag it between campus, home, and my lab (a few miles up a hill), all by bike.  It is so light I must open my bag to make sure it is really in there!  The shape is a little strange, so I ended up getting a ridiculously large laptop case for it, but that doesn't need to be true for you.

I needed some help getting the wireless to work out of the box, but it was my first time ever using Ubuntu or wireless with linux.  Otherwise, I found it incredibly user friendly (and I had no clue what I was doing!).

It was frustrating when the power management didn't work, but now I have no problems with it.  I find that the ALSA-fix is fine.  Usually when I plug in headphones it does what I expect, though sometimes I fiddle with the volume in the wrong way and unmute the main speakers.  On the whole it isn't that bad - I listen to loud, angry music in a quiet workplace environment and trust it to work.

The speakers are fine for ambient music (or bug-your-neighbors music), but they are too quiet for watching movies.  The screen is fine for movies.  I am happy with the screen for the coding that I do, though I tend to plug into a ginormous CRT at work.

Perhaps the biggest testament to how great this laptop (and System76!) is: even after seeing the problems with the power management and  the "limitations" of the system, my boyfriend got the identical laptop about 6 months after I did.  We had to put stickers on the top to tell them apart.

---

### Post by LibertyShadow on 2008-04-02
Thank you everyone for the great and honest feedback :) I just love the community.

---

### Post by hackmeister on 2008-04-07
The Darter looks sweet. Does it have a firewire port?

---

### Post by pavel_987 on 2008-04-07
no

---

### Post by abuakel on 2008-04-23
I've also been looking at the DarU2 and have liked everything about it. I've read multiple reviews think it's a really good one.
But I've got one question about the display. I currently own an Acer TravelMate 4010 and after a year of use, the screen started wobbling. Now, three years later, I sometimes have to prop up the screen. By biggest worry about the DarU2 is the stability of the display screen.. how is it?

---

### Post by thomasaaron on 2008-04-23
It is pretty solid.
And it only goes back about 45 degrees past vertical.

But I'm a tech support guy, so some customer input would be nice.

---

### Post by jdb on 2008-04-23
> **abuakel said:**
> I've also been looking at the DarU2 and have liked everything about it. I've read multiple reviews think it's a really good one.
But I've got one question about the display. I currently own an Acer TravelMate 4010 and after a year of use, the screen started wobbling. Now, three years later, I sometimes have to prop up the screen. By biggest worry about the DarU2 is the stability of the display screen.. how is it?
I've only had mine a little over 3 months so it's hard to say long term.
So far the screen hinges have not loosened any and seem to be very rugged.
It appears to be very well built, better than many laptops I have seen.

jdb

---

### Post by abuakel on 2008-04-23
Thanks for the feed back! It seems like the perfect laptop! :)

---

### Post by dtrask on 2008-04-26
I'm a teacher and I have a Daru2 and LOVE it!  I bought it for the portability and size.  I travel quite a bit to speak at conferences and so forth about Open Source in Education ([http://fossed.blogspot.com](http://fossed.blogspot.com)) ([http://dtrask.wordpress.com](http://dtrask.wordpress.com))  In any case, the Daru2 has great battery life and runs nice a quiet.  I can get about 3 hours or more of battery life under normal usage.  The wireless is nice a strong.  The laptop is very durable in my opinion.  I recently had a nice wipeout on a patch of ice...my laptop lives in a Tom Bihn "Buzz" bag [http://tinyurl.com/5bjoz3]("http://tinyurl.com/5bjoz3")  and it broke my fall...and not only survived, but without a scratch!  With the right bag, the laptop is EXTREMELY portable (a good bag can make ALL the difference).  It's nice, small, and very easy to work with.  I have a MacBook Pro, an iBook G4, an HP zv5000 (behemoth), and an older Dell Latitude 610...the Daru2 (Darter Ultra 2) is by far my favorite laptop and the one I use on a daily basis (in fact I'm using it right now).  :-)  The System76 tech support is great!  I had a minor hardware issue several months ago...the System76 guys treated me like the geek I am instead of assuming I was the average computer user (although they make no assumptions...so even average computer users should feel perfectly comfortable)...I helped diagnose my own issue and they fixed me up right!  Go for it...you will NOT be disappointed.  Oh...the power issues are solved...the HDMI port doesn't work (who cares?)...and the fingerprint scanner doesn't work, but I never expected it to...the nice thing is that since it's an Open Source OS...it just might work someday (won't that be a cool surprise!)  They also keep up with the Ubuntu releases...so you get an upgrade every 6 months!  That in itself is just plain fun!  Essentially a new OS with new surprises!  :)  Order one!  And Enjoy!  ):P

---

### Post by abuakel on 2008-04-27
> **dtrask said:**
> I'm a teacher and I have a Daru2 and LOVE it!  I bought it for the portability and size.  I travel quite a bit to speak at conferences and so forth about Open Source in Education ([http://fossed.blogspot.com](http://fossed.blogspot.com)) ([http://dtrask.wordpress.com](http://dtrask.wordpress.com))  In any case, the Daru2 has great battery life and runs nice a quiet.  I can get about 3 hours or more of battery life under normal usage.  The wireless is nice a strong.  The laptop is very durable in my opinion.  I recently had a nice wipeout on a patch of ice...my laptop lives in a Tom Bihn "Buzz" bag [http://tinyurl.com/5bjoz3]("http://tinyurl.com/5bjoz3")  and it broke my fall...and not only survived, but without a scratch!  With the right bag, the laptop is EXTREMELY portable (a good bag can make ALL the difference).  It's nice, small, and very easy to work with.  I have a MacBook Pro, an iBook G4, an HP zv5000 (behemoth), and an older Dell Latitude 610...the Daru2 (Darter Ultra 2) is by far my favorite laptop and the one I use on a daily basis (in fact I'm using it right now).  :-)  The System76 tech support is great!  I had a minor hardware issue several months ago...the System76 guys treated me like the geek I am instead of assuming I was the average computer user (although they make no assumptions...so even average computer users should feel perfectly comfortable)...I helped diagnose my own issue and they fixed me up right!  Go for it...you will NOT be disappointed.  Oh...the power issues are solved...the HDMI port doesn't work (who cares?)...and the fingerprint scanner doesn't work, but I never expected it to...the nice thing is that since it's an Open Source OS...it just might work someday (won't that be a cool surprise!)  They also keep up with the Ubuntu releases...so you get an upgrade every 6 months!  That in itself is just plain fun!  Essentially a new OS with new surprises!  :)  Order one!  And Enjoy!  ):P

You're a pretty good salesperson! haha.. 
Now my only problem is saving up for it ;-)

---

