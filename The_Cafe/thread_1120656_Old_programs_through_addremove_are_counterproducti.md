---
title: "Old programs through add/remove are counterproductive"
date: 2009-04-09
forum: The Cafe
---

### Post by pointyblufish on 2009-04-09
It's great to be able to get new programs for Ubuntu through the add/remove menu, but why are the programs in there so old? I'm not asking this from a tech support standpoint, just from a conceptual standpoint. The way I see it, I'd rather not find what I'm looking for under add/remove and have to search for it online than to find an old and really awful version there. 

Let me explain with an example. I was looking for a torrent client this morning. Deluge came up in the first thread I came to so I got it. What an awful experience! The program claimed to have support for partial downloads through a plugin, but I found no way to access a screen that would let me configure that. The interface in general was pretty awful. Even Transmission was better than this. 

I got rid of it and went to look for more suggestions, but Deluge kept coming up. I thought to myself, "Either all of these folks are complete idiots or I'm doing something wrong. And Linux folks are generally pretty smart, so..." Of course, a few of the suggestions mentioned getting Deluge from the repo or from the official website. So I eventually figured out that the official website had a version much newer than the one available through the add/remove menu, got it, played around with it, and have been satisfied with it so far. 

Conclusion (or tl;dr): If something is easily accessible to a new user it should be polished. Why do you suppose car dealerships keep the old clunkers hidden in a field out back and leave all the nicest looking, latest model cars at the roadside? If they kept the clunkers out front nobody would even set foot there. Same deal with Linux. If I'm Average Joe User switching over from Windows and absolutely must have program X and I get an awful version from the first source I find, my impression of Linux as a whole just went down. And if I wasn't persistent enough to find out that the good stuff is hidden in the lot out back I'd very likely go right back to Windows. So why does Linux hide the good stuff and show off the clunkers?

---

### Post by 23meg on 2009-04-09
[https://wiki.ubuntu.com/StableReleaseUpdates](https://wiki.ubuntu.com/StableReleaseUpdates)
[https://wiki.ubuntu.com/TimeBasedReleases](https://wiki.ubuntu.com/TimeBasedReleases)

---

### Post by forrestcupp on 2009-04-09
You make some good points.  Maybe they need to work on some kind of rating system that works better.

---

### Post by snowpine on 2009-04-09
Your question is kind of like "why does my 1969 Chevy use 40-year-old parts? :)

The version of applications available in the Ubuntu repository is determined by which Ubuntu release you're using. If you're using 8.10, you get whatever the stable version of the application was as of Oct. 2008. If you're runnning 8.04, you get the April 2008 version, and so on. If you want newer versions of applications, upgrade to 9.04, which includes the stable-as-of-April-2009 versions. Not rocket science. :)

If you go into Synaptic and enable the "backports repository", you will get newer (though not necessarily the newest) versions of selected applications.

If you really need the latest version of an application (which has not been tested as stable with your release by the Ubuntu team), download it from their website and hope it works.

---

### Post by pointyblufish on 2009-04-09
> **snowpine said:**
> Your question is kind of like "why does my 1969 Chevy use 40-year-old parts? :)

Very true! But also, I'm wondering why that 1969 Chevy is prominently displayed on the lot in the first place. ;) 

I think forrestcupp got what I was trying to say. In the case of my example, Deluge was pretty clearly unpolished when 8.10 was released, yet there it is with 4 stars waiting to be installed by the unwary Ubuntu newbie. *If I didn't know better*, I'd imagine that Ubuntu must be a real junker if something like that gets rated at 4 stars. 

I thought I'd bring this issue up because it's probably something that veteran users would be likely to miss. You all have your favorite places to get programs from and you've streamlined Ubuntu to work the way you like it, but if the default Ubuntu settings lead new users astray then those new users are likely to get turned off from Ubuntu and you'd be left scratching your heads wondering why they left when the system works so well for you.

---

### Post by snowpine on 2009-04-09
The bottom line is that Ubuntu assumes the "average user" will upgrade to the new release every six months, and that is where they spend most of their development efforts, not necessarily backporting new applications into old releases.

It sounds to me like that version of Deluge works okay (4 stars) for the average user, but the new version has a new feature that you want. To continue the automotive analogy, people hot rod their cars all the time, but they don't go to the dealership to do it. Think of Add/Remove Programs (the Ubuntu repository) as the factory-authorized warranty program; they are going to try and sell you the exact replacement part, because their #1 priority is to keep your car running reliably. 

Now, there is another type of Linux distro called "rolling release" where you don't have distinct releases. All applications/packages are constantly being upgraded as new versions become available. Examples of this kind of distro include Arch and Debian Sid (the distro from which Ubuntu is derived). This is something you might consider if you ever want to branch out from Ubuntu. :)

---

### Post by forrestcupp on 2009-04-09
Well, I'm thinking of it from a different point of view than the version number thing.  

What if there are a few different software packages that do the same thing, and some are obviously better quality than others?  When a user is trying to find that type of software in Add/Remove Programs, it shouldn't be the crappy program that dominates the screen; it should be the one that's the better choice.  That's why a good rating system that works would be useful.

---

### Post by mkendall on 2009-04-09
Please correct me if I'm mistaken, but I thought the star rating in Add/Remove was a measure of how many people use that particular program, not how good it is. (Granted, there is a tendancy for people to think that because something is popular it must be good, despite all evidence to the contrary.)

---

### Post by Mokoma on 2009-04-09
yeah but if you use a lts like hardy your left with rapidly aging software. which forces you to go to outside sources. which 

a) exposes you to malicious code

b) means that it may force you to install some dated dependency which breaks something else in the system

so yeah, they should update more

---

### Post by cariboo on 2009-04-09
You can always check [getdeb]("http:///www.getdeb.net/") for a newer version of a program you are looking for.

Jim

---

### Post by Mehall on 2009-04-09
Using an LTS is counterproductive to asking for new software.

Ask Debian stable.

---

### Post by 3rdalbum on 2009-04-09
If you'd like to package and test new versions of software for Ubuntu Hardy and Intrepid users, and then run a repository with all those packages, then don't let me stop you. It's a lot of work, and with versions of Ubuntu that are a year old you'd also find yourself packaging up newer versions of libraries and coming across more conflicts with the older programs that assume the older libraries.

Linux is very much a moving target, by choice. Keeping all software up-to-date with new versions would be a full-time job for a large team of people.

---

### Post by forrestcupp on 2009-04-10
> **mkendall said:**
> Please correct me if I'm mistaken, but I thought the star rating in Add/Remove was a measure of how many people use that particular program, not how good it is. (Granted, there is a tendancy for people to think that because something is popular it must be good, despite all evidence to the contrary.)

Exactly.  That's why I said we need a "good rating system that works."

When you have a star rating system based only on the number of people using it, it's like a snowball effect.  More people use it, so it shows up with more stars, so more people see the stars and download it, so it just adds to the rating.  It just keeps getting bigger and bigger, and you might have a really crappy program that is only popular because that's what people use.

It's the same concept as the whole argument of free music vs. mainstream music.  Popular music is only popular because that's what we're fed and that's what everyone listens to, not because it's good music.

The current star system is useful, but we need to add at least one more where software is rated by how good it is.  Kind of like how for Windows, Download.com has several different types of ratings that you can filter the software with.  They have ratings for "Most Popular", "New Releases", "Editor's Picks", "User Favorites", and "Top Freeware".  

Why couldn't Add/Remove and even Synaptic come up with a model like that?  It might take time for the ratings to build up, but I think it would be worth it.

---

