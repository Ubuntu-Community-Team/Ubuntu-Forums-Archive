---
title: "ubuntu 9.04 6 days to release a quick review by me"
date: 2009-04-18
forum: Testimonials &amp; Experiences
---

### Post by stinger30au on 2009-04-18
Ubuntu 9.04 – a quickie review by an average user, thats me

 

 

 I have been a user of Ubuntu since 7.04 and consider myself an average ubuntu user
 

 if I get stuck, I go hunting via google and if I have no joy I ask for help at the ubuntu forums
 

 

 I decided today to d/l the 9.04 release candidate 6 days before the final hits the net and have ago and see whats changed and what works and what doesnt work
 

 

 my pc is nothing flash it is a pentium 4 3.4 Ghz with 1.5 gig ram and a few 40 gig ide hdd and a dvd burner and a nvidia 5500 256 meg agp video card

 

 I installed 9.04 to my external 80 gig usb hdd for a test run to make sure it would work ok before I ditched my current install on my internal hdd
 

 the installer is improved with a map of the world you can easily pick and chose your time zone from
 

 when I installed to usb hdd I did a custom install and told the s/w to use the usb hdd and install the boot to it and it runs fine. Install from cd took about 20 minutes I guess
 you can make it install faster if you burn the .iso file you download from the net to a dvd
 

 once installed I restarted the pc and removed the cd
 

 I noticed the ubuntu splash screen has changed a a little. Instead of a giant bar moving backwards and forwards there is now a thin line doing the same thing
 

 I was asked for my user name and password at the login screen.
 This is by far the most professional looking login screen by default yet
 it is black background and in lower right corner is a 3d ubuntu logo laying over and it looks ray-traced. Wow. Top work
 

 once logged In you can easily change the background on the desktop. It ships with a few desktops but the one I liked looks like a camera is pointed at the sun and there's a few spots around the place. I think its great so I used it
 

 my video card is a nvdia 5500 agp 256 meg. Nothing flash here either. I went to system – preferences – appearance and hit visual effects and clicked normal
 it said it was going to d/l new drivers off the net to make my nvdia card work with restricted drivers
 

 about now I left the pc for about 10 minutes and attended to other duties
 upon my return the pc was still scrolling a little line across the screen at 0% download of the required files
 

 I though, oh great, here we go again. Nvidia have done the same to us with no drivers like they did with 8.10
 

 so I restarted the pc  
 

 when I logged in again the restricted drivers icon popped up in the right corner and said it needed restricted drivers to run and I selected the drivers ubuntu suggested I used and let it install them
 

 I restarted the pc and presto, all is good and my nvidia card is working fine
 

 I also added compiz fuzion and emerald
 

 I put a normal dvd in the drive to see if it would auto download the drivers and play and movie player came up and said it needed to d/l codec's and it attempted to and said it could not find codec's required to play
 

 I was dissapointed that again another ubuntu release and this feature does not work
 not to worry. I dropped in to
 

  [www.medibuntu.org](www.medibuntu.org)
 

 and I followed the instructions  
 

 Ubuntu 9.04 "**Jaunty** Jackalope":  
 sudo wget [http://www.medibuntu.org/sources.list.d/jaunty.list](http://www.medibuntu.org/sources.list.d/jaunty.list) --output-document=/etc/apt/sources.list.d/medibuntu.list 

 

 and I did this too
 

 Then, add the **GPG** Key:  
 sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update and I did this
 

 sudo apt-get install libdvdcss2 and this
 

 For **i386**, the package is called **w32codecs**:  
 sudo apt-get install w32codecs and this
 

 sudo apt-get non-free-codecs
 

 and att the end of this I restarted my pc and TA DA!!!
 all is well I can play my dvds
 

 I had to add the compiz fusion icon to the startup sessions as well via preferences – startup applications
 

 so compiz runs fine too
 

 9.04 also has open office 3 built into it as well as a number of other upgraded applications as well
 

 on the whole im quite impressed it also seems to run faster then 8.10 as well
 

 tonight I will delete my 8.10 install and happily install 9.04
 it is the best working version yet I have used “out of the box” so to speak
 

 keep up the great work team Ubuntu!

---

### Post by stinger30au on 2009-04-18
i have ditched the external usb hdd and installed it on my internal hdd and its running smooth

very, very nice

have not hit any snags i could not resolve

loving it

install it NOW!!! :)

---

### Post by Joeb454 on 2009-04-18
Thread moved to  Testimonials & Experiences.

Glad to hear you like 9.04, I love it :D

---

### Post by longtom on 2009-04-18
Good report.  I had to think of Mary (or was it Martha) from Iowa installing it...we had that discussion somewhere else.

9.04 sounds really a good distro by most accounts and I'll get my hands on it as soon as you guys have sorted out the teething problems...;)

---

### Post by Ericyzfr1 on 2009-04-18
I have used it for the last couple of weeks and except a glitch with the updates (seems corrected now), the performance level is awesome.

---

### Post by wolfen69 on 2009-04-18
> **longtom said:**
> Good report.  I had to think of Mary (or was it Martha) from Iowa installing it...we had that discussion somewhere else.

9.04 sounds really a good distro by most accounts and I'll get my hands on it as soon as you guys have sorted out the teething problems...;)

i have used it since beta, and have to say i have not found any "teething" problems. awesome release.

---

### Post by Joeb454 on 2009-04-18
> **wolfen69 said:**
> i have used it since beta, and have to say i have not found any "teething" problems. awesome release.

I see your beta, and raise an Alpha 5 ;)

Still no problems for me either :) That's not to say there's **no** bugs, but you get the idea :)

---

### Post by Comhra on 2009-04-18
> **wolfen69 said:**
> i have used it since beta, and have to say i have not found any "teething" problems. awesome release.

Have to agree, best Ubuntu yet, btw I'm still on the beta

---

### Post by Comhra on 2009-04-18
> **Joeb454 said:**
> I see your beta, and raise an Alpha 5 ;)

Still no problems for me either :) That's not to say there's **no** bugs, but you get the idea :)

Roflmho

---

### Post by rmayer32 on 2009-04-18
Installed clean with the Beta using ext4 and love every second of it here.

I haven't found any issues on my laptop as of yet.

---

### Post by wolfen69 on 2009-04-18
> **Comhra said:**
> Have to agree, best Ubuntu yet, btw I'm still on the beta

you're not doing updates?

btw, just in case someone someone does not know, you must do updates manually.

---

### Post by cariboo on 2009-04-19
> **Joeb454 said:**
> I see your beta, and raise an Alpha 5 ;)

Still no problems for me either :) That's not to say there's **no** bugs, but you get the idea :)

I see you Alpha 5 and raise a Tool Chain. There have been a couples of times that there where problems, but I've haven't had to do a reinstall. Jaunty Testing & Discussion has been the best resource.

Jim

---

### Post by stinger30au on 2009-04-19
oh man, oh man

i have his my pc running 9.04 for just over 24 hours now and man this is pure as silk

love it

sssssssoooooo smooth compared to 8.10

i have got this loaded up with all my apps i used to run in 8.10 and it makes 8.10 look like a snail

cool

saves me buying new hardware !!!

love it

---

### Post by jdrodrig on 2009-04-19
> **stinger30au said:**
> 

saves me buying new hardware !!!



Don't say it out loud...Ubuntu might get sued for destroying American Jobs in the hardware industry! 

This country needs your hardware purchases!! =)

---

### Post by Foxcow on 2009-04-19
> **rmayer32 said:**
> Installed clean with the Beta using ext4 and love every second of it here.

I haven't found any issues on my laptop as of yet.




How hard was it to install using ext4?

---

### Post by wolfen69 on 2009-04-19
> **Foxcow said:**
> How hard was it to install using ext4?

it's the same as installing ext3. maybe i'm not sure about your question.

---

### Post by cariboo on 2009-04-19
If you are doing a clean installation, there is nothing to it. In the partitioning section, you have to select manual partitioning, then after you have set up your partitions, select to format the partitions as ext4.

Jim

---

### Post by stinger30au on 2009-04-20
> **cariboo907 said:**
> If you are doing a clean installation, there is nothing to it. In the partitioning section, you have to select manual partitioning, then after you have set up your partitions, select to format the partitions as ext4.

Jim


hate to sound stupid, whats the difference between ext3 and ext4??? any main advantages to using it???

---

### Post by ukripper on 2009-04-20
9.04 is th ebest release out of the box so far for me too!!!Already on production machine after thorough testing!!:)

---

### Post by ukripper on 2009-04-20
> **stinger30au said:**
> hate to sound stupid, whats the difference between ext3 and ext4??? any main advantages to using it???

for benchmarks follow this link -
[http://www.phoronix.com/scan.php?page=article&item=ext4_benchmarks&num=1](http://www.phoronix.com/scan.php?page=article&item=ext4_benchmarks&num=1)

---

### Post by richaustin on 2009-04-20
Hi

I upgraded about 2 weeks ago. I figured that I had nothing much on the PC that mattered so what the hell if it went wrong? Nothing did. System is much faster than previously (unless I am deluding myself!) and it is, in my opinion, the best release so far that I have tried.

I'm not sure whether to wipe the system and re-install from scratch when the final release comes out. Any thoughts on that?

Rich

---

### Post by ukripper on 2009-04-20
> **richaustin said:**
> Hi

I upgraded about 2 weeks ago. I figured that I had nothing much on the PC that mattered so what the hell if it went wrong? Nothing did. System is much faster than previously (unless I am deluding myself!) and it is, in my opinion, the best release so far that I have tried.

I'm not sure whether to wipe the system and re-install from scratch when the final release comes out. Any thoughts on that?

Rich

Certainly i would opt-up for clean install of EXT4 Jaunty from scratch! Make sure you create backup of your valuable data first.

however, if you are already using Jaunty Daily build or RC, it will turn into final anyway on release via Update manager!

---

### Post by warjowuch on 2009-04-20
For watching encrypted dvd's, you should install the libdvdcss2 package too, it's also in the medibuntu-repos.
Good read and good to know you enjoy the stuff :)

---

### Post by Guitar John on 2009-04-20
I enjoyed the review.

I've used regular Ubuntu since 2006.

Even though our slowest computer is 1.4 GHz w/512 MB RAM, and runs fine with Gnome, I'm going with Xubuntu this time.  I don't have a practical reason other than that I just want to.

I downoaded the beta live cd just to give it a try.  Most things worked well.  The things that did not, I dismissed as "it's still beta."

If it doesn't work, I can always go back to Gnome.

---

### Post by Foxcow on 2009-04-21
> **cariboo907 said:**
> If you are doing a clean installation, there is nothing to it. In the partitioning section, you have to select manual partitioning, then after you have set up your partitions, select to format the partitions as ext4.

Jim



I will give it a whirl on my test drive when I get home.  Thanks!

---

### Post by SlickRick on 2009-04-21
> **cariboo907 said:**
> If you are doing a clean installation, there is nothing to it. In the partitioning section, you have to select manual partitioning, then after you have set up your partitions, select to format the partitions as ext4.

Jim

I figured I was gonna upgrade but with all the hype of ext4 I wanna try it out. Do I absolutely need to do a fresh install to reap in the benefits or is there another way?

EDIT:never mind, gonna fresh install

---

