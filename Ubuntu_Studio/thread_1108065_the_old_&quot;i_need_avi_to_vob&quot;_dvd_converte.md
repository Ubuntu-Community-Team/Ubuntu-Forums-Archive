---
title: "the old &quot;i need avi to vob&quot; dvd converter question"
date: 2009-03-27
forum: Ubuntu Studio
---

### Post by Smiley Coyote on 2009-03-27
I have spent some time now looking through posts on this topic.  Months ago, I tried to switch to Ubuntu and switched right back because I could not get an answer that actually worked.  I see now that this is one of Linux's biggest shortcomings.  I for one am back to Ubuntu for good but I still have the same problem, the inability to make DVDs (NTSC) from AVI or other formats.  I have had nothing but negative experiences with Wine.  I always seemed to get a program that looked like it was going to work but all the text in the graphic interface was always missing, requiring that I blindly click here and there to see what happened.

So, does [this link]("http://ubuntuforums.org/archive/index.php/t-510207.html") indicate where the running wisdom on this matter still stands?

By the way, I NEED it to be a free program.

---

### Post by Stochastic on 2009-03-27
I've always used DeVeDe and had no problems with it.

---

### Post by binbash on 2009-03-29
+1 for devede

---

### Post by Smiley Coyote on 2009-03-30
I got DeVeDe and gave it another go.  Much is working for me that didn't before and I did have a somewhat archaic system the last time I tried to give Ubuntu and these items a try.

It seems to be working and the tutorial that I found, a video tutorial at Youtube, suggested that I leave the video rate the same as the original rate of the AVI that I am converting.

However, with ConvertXtoDVD, when I used Windows, I was taking six to nine hundred megabyte files and converting them to three to four GB and getting damned decent quality.  As I am doing it now, and I have a hunch that the video rate is the culprit, I am getting significantly lower quality and TS folders or ISO's that amount to the same size as what I am starting with or just a little higher.  In other words an 800 MB file is converting into around a 900 MB ISO instead of the 3 or 4 gigs I used to get with my old method.

If I just double the video rate, will I get a bigger and clearer file?  The DVD I just burned is actually a much lower quality than the original AVI that I started with.  

The Youtube tutorial strongly suggested I keep the values the same but something has to be done in order for this to be viable for me.

---

### Post by Smiley Coyote on 2009-03-30
Well well well.  What a difference having a relatively up to date system makes.  I have purveyed other similar threads to this and nearly every one ends up with some version of an expert saying it works for them with the inquirer complaining that it doesn't.

With four times the processing power that I had when I last tried Ubuntu and also Wine, and with four times the memory and significantly better graphics processing, it seems that Wine will actually work with my computer whereas it wouldn't with the Pentium 2 I WAS using last year.  Yeah, you heard me right - Pentium 2.

I have little doubt that some systems will not be able to simulate a Windows environment but since mine now can, I can now run ConvertXtoDVD with it to create an ISO about three times the size of the one I got with DeVeDe, created at about four times the bitrate, and lo and behold, THE QUALITY IS FAR SUPERIOR.

The evidence is in and it contradicts some "experts": DeVeDe needs further engineering AND there is some relationship between bitrate, size of ISO, and quality of playback.  A DVD created at a bitrate higher than the AVI was recorded at DOES NOT AUTOMATICALLY mean less quality and in this case, and I suspect that this will be repeated, meant higher quality.

I really hope some people stop claiming otherwise.

---

### Post by inobe on 2009-03-30
mandvd can take an avi and encode to dvd or iso

it will also handle subs and menus.. and create chapters automatically...

[http://www.getdeb.net/app/ManDVD](http://www.getdeb.net/app/ManDVD)

---

### Post by missbliss on 2009-03-30
I've got a DeVeDe question, hope you don't mind if I post it here!

Okay, so if I convert an .avi to PAL using DeVeDe and then I have an .iso file as a result, what do I do with that to make it something I burn to a DVD to play in my DVD player??

---

### Post by Smiley Coyote on 2009-03-30
> **missbliss said:**
> Okay, so if I convert an .avi to PAL using DeVeDe and then I have an .iso file as a result, what do I do with that to make it something I burn to a DVD to play in my DVD player??

Double click on the file and the option to burn it onto disc ought to automatically pop up.  I do recommend using the lowest burn speed possible.

---

### Post by Smiley Coyote on 2009-03-30
> **inobe said:**
> mandvd can take an avi and encode to dvd or iso

it will also handle subs and menus.. and create chapters automatically...

[http://www.getdeb.net/app/ManDVD](http://www.getdeb.net/app/ManDVD)

Thanks.  More tools.  Me likey.

---

### Post by missbliss on 2009-03-30
> **Smiley Coyote said:**
> Double click on the file and the option to burn it onto disc ought to automatically pop up.  I do recommend using the lowest burn speed possible.
So, an iso file will play on a dvd player??  I didn't realize that!



*edit* Nope, that doesn't play in my player.  Maybe I have so much trouble b/c my player simply doesn't play the files?

---

### Post by inobe on 2009-03-30
> **Smiley Coyote said:**
> Thanks.  More tools.  Me likey.

tweaking the menu' be selective on image backgrounds' fonts etc... when manually doing things, images with proper resolutions for example, you don't want a stretched menu !

if you have a 1080p monitor, the image resolution should be 1920x1080, you may need to experiment...

you will notice on playback devices the fonts flickering, you will eventually figure out why an prevent it..

never messed with animated backgrounds' i will assume it works great, of course mandvd allows you to cuts scenes for that' or you can manually put one together.

but overall i think its one of the best, over time you will be a master of all it's features glide rite threw it within minutes.

---

### Post by Stochastic on 2009-03-30
> **inobe said:**
> mandvd can take an avi and encode to dvd or iso

it will also handle subs and menus.. and create chapters automatically...

[http://www.getdeb.net/app/ManDVD](http://www.getdeb.net/app/ManDVD)

There is no reason to suggest people to getdeb.net for programs that are in the regular ubuntu repository - it only hurts ubuntu with inaccurate bug reports and wasted manpower during troubleshooting.

The proper way to install ManDVD is ```
sudo apt-get install mandvd
``` or by installing that package through add/remove programs (synaptic package manager).

Getdeb.net also does not provide any security updates for their packages - ubuntu does.

---

### Post by Stochastic on 2009-03-30
> **missbliss said:**
> So, an iso file will play on a dvd player??  I didn't realize that!



*edit* Nope, that doesn't play in my player.  Maybe I have so much trouble b/c my player simply doesn't play the files?

Your problem was that you chose PAL dvd, but your location specifies USA so you should have chosen NTSC.  Then all the rest should be the same.
[IMG]http://upload.wikimedia.org/wikipedia/commons/thumb/0/0d/PAL-NTSC-SECAM.svg/800px-PAL-NTSC-SECAM.svg.png[/IMG]

---

### Post by inobe on 2009-03-30
that's cool and all that' but i always check there first :wink:

---

### Post by Stochastic on 2009-03-31
> **inobe said:**
> that's cool and all that' but i always check there first :wink:

That's nice for you, but **please** don't ask for help or file bugs relating to any software you get from getdeb.net even if it's also in the repositories.

**AND PLEASE DON'T SUGGEST THAT SITE TO NEW USERS AS THEIR PRIMARY MEANS OF GETTING SOFTWARE.  IT COULD BE DAMAGING TO THEIR COMPUTER.**  

Ubuntu is rigorously testing the combination of packages that they have in their repositories and all the software you get from getdeb.net completely ignores this testing procedure.  It's equivalent to throwing a new user into a development release of ubuntu - breakages can and will occur which only looks bad for Ubuntu.

---

### Post by inobe on 2009-03-31
> **Stochastic said:**
> That's nice for you, but **please** don't ask for help or file bugs relating to any software you get from getdeb.net even if it's also in the repositories.

**AND PLEASE DON'T SUGGEST THAT SITE TO NEW USERS AS THEIR PRIMARY MEANS OF GETTING SOFTWARE.  IT COULD BE DAMAGING TO THEIR COMPUTER.**  

Ubuntu is rigorously testing the combination of packages that they have in their repositories and all the software you get from getdeb.net completely ignores this testing procedure.  It's equivalent to throwing a new user into a development release of ubuntu - breakages can and will occur which only looks bad for Ubuntu.

:)

---

### Post by uzzo2 on 2009-04-04
> 
The proper way to install ManDVD is
Code:

sudo apt-get install mandvd

or by installing that package through add/remove programs (synaptic package manager).

Getdeb.net also does not provide any security updates for their packages - ubuntu does.
I tried this and got this:

phil@phillip-desktop:~$ sudo apt-get install mandvd
[sudo] password for phil: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package mandvd is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package mandvd has no installation candidate
phil@phillip-desktop:~$ 

I have used DeVeDe a few times with success, just thought i would try mandvd because i read in another thread that it was a little faster converting avi files.

---

### Post by Stochastic on 2009-04-04
> **uzzo2 said:**
> I tried this and got this:

phil@phillip-desktop:~$ sudo apt-get install mandvd
[sudo] password for phil: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package mandvd is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package mandvd has no installation candidate
phil@phillip-desktop:~$ 

I have used DeVeDe a few times with success, just thought i would try mandvd because i read in another thread that it was a little faster converting avi files.

Ahh, whoops it looks like mandvd just got put into the repos for the Jaunty release: [http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=mandvd](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=mandvd)

So I was wrong (but will soon be right if that counts for anything).

getdeb.net is a good site to get software that isn't available in the repos, so yes, it's probably the best way to go if you're on a pre-jaunty machine.

---

### Post by uzzo2 on 2009-04-05
> Ahh, whoops it looks like mandvd just got put into the repos for the Jaunty release: [http://packages.ubuntu.com/search?su...eywords=mandvd](http://packages.ubuntu.com/search?su...eywords=mandvd)

Will that download work for Hardy? I downloaded the one from getdeb.net and couldn't get it to work. It wasn't able to see the the file i was trying to convert. Thanks for the advice, I am really starting to like this OS although i still have a lot to learn about it.

---

### Post by Stochastic on 2009-04-05
> **uzzo2 said:**
> Will that download work for Hardy? I downloaded the one from getdeb.net and couldn't get it to work. It wasn't able to see the the file i was trying to convert. Thanks for the advice, I am really starting to like this OS although i still have a lot to learn about it.

If memory serves correct getdeb.net will default to the latest release (intrepid) unless you change the settings up near the top of the page.  Read carefully.  Debs do need to be tailored for your exact OS.

---

