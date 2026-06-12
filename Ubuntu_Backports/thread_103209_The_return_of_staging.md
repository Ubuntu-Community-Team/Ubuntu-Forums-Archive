---
title: "The return of staging"
date: 2005-12-13
forum: Ubuntu Backports
---

### Post by jdong on 2005-12-13
Would just like to announce that breezy-backports-staging or some form of public package beta releases will be reintroduced shortly to aid in wider package testing.

Note that these would be experimental nature repositories only to be used by those who can cope with typical apt/deb breakages without nagging all the devs :)

---

### Post by matthew on 2005-12-13
[quote=jdong]Would just like to announce that breezy-backports-staging or some form of public package beta releases will be reintroduced shortly to aid in wider package testing.

Note that these would be experimental nature repositories only to be used by those who can cope with typical apt/deb breakages without nagging all the devs :)[/quote]Cool. When it's ready let me know the location and I'll put it in my sources.list immediately.

---

### Post by btdown on 2005-12-14
Sweet!

---

### Post by jdong on 2005-12-14
```

deb http://ubuntu-backports.mirrormax.net/ breezy-backports-staging main restricted universe multiverse

```

Add that for now :)

---

### Post by Knomefan on 2005-12-14
Great! :D 

Thanks a lot!

---

### Post by jdong on 2005-12-14
Staging may not get populated after all; I'm currently working with a few MOTU's to make an official backporting script that'll be in Universe, that'll allow people to assemble personal backports.

I think this is a much better solution than staging. I'll keep you posted, but keep an eye on the Backports mailing list.

---

### Post by Knomefan on 2005-12-14
[QUOTE=jdong]Staging may not get populated after all; I'm currently working with a few MOTU's to make an official backporting script that'll be in Universe, that'll allow people to assemble personal backports.

I think this is a much better solution than staging. I'll keep you posted, but keep an eye on the Backports mailing list.[/QUOTE]

That's even better.
Thanks again!

(If you keep going with this pace I won't be able to keep up with saying thanks. :D )

---

### Post by matthew on 2005-12-14
[quote=jdong]Staging may not get populated after all; I'm currently working with a few MOTU's to make an official backporting script that'll be in Universe, that'll allow people to assemble personal backports.

I think this is a much better solution than staging. I'll keep you posted, but keep an eye on the Backports mailing list.[/quote]Cool. Thanks for the hard work!

---

### Post by jdong on 2005-12-14
The reason for putting a plug on Staging for now is to make sure we don't run into the old problem with Mirrormax and people filing Ubuntu bugzilla tickets for Backports related issues, and support channels being flooded with such problems.

I have to agree with them. No matter how much you label "THIS IS EXPERIMENTAL -- DON'T CRY TO ANYONE IF YOU BREAK YOUR UBUNTU" on the repository, some still don't get it.

I believe an easier to use "personal backporting" system is going to be the best, because no matter how much I try I'll never make everyone happy.... Some are more bold and daring, while others are more conservative. This way, everyone is happy :)

---

### Post by ubuntu_demon on 2005-12-14
[QUOTE=jdong]The reason for putting a plug on Staging for now is to make sure we don't run into the old problem with Mirrormax and people filing Ubuntu bugzilla tickets for Backports related issues, and support channels being flooded with such problems.

I have to agree with them. No matter how much you label "THIS IS EXPERIMENTAL -- DON'T CRY TO ANYONE IF YOU BREAK YOUR UBUNTU" on the repository, some still don't get it.

I believe an easier to use "personal backporting" system is going to be the best, because no matter how much I try I'll never make everyone happy.... Some are more bold and daring, while others are more conservative. This way, everyone is happy :)[/QUOTE]
great!

What about the quality of the resulting deb. Will it be acceptable for official backports (after testing) ? If not it would be nice to have some "how to backport properly" so people can also learn how to do it "properly".

---

### Post by jdong on 2005-12-14
The scripts will use pbuilder to build Official Backports style Backports, so they'll be of official quality, minus any packaging bugs in Dapper (or wherever you're pulling your sources from)


Feedback from testers will be very very valuable for the Backports team.

---

### Post by ubuntu_demon on 2005-12-14
[QUOTE=jdong]The scripts will use pbuilder to build Official Backports style Backports, so they'll be of official quality, minus any packaging bugs in Dapper (or wherever you're pulling your sources from)


Feedback from testers will be very very valuable for the Backports team.[/QUOTE]
I've never backported anything. But it seems more fun than doing a request :)

---

### Post by ember on 2005-12-14
It is more fun ;) ... I did a personal backport of kino today and it is nicer to see how compiling messages run through and eventually you have your own package than just do a boring apt-get update ;)

---

### Post by carlosqueso on 2005-12-14
I'd have a couple concerns, and maybe these are silly.  First, wouldn't it be more helpful if users could test even for packaging bugs as well, since that is what is eventually going to be in the official repo?  Second, how will you ensure that the official backport supercedes the testing one?  I wouldn't mind building a custom backport, it sounds entertaining, but I just have those concerns.

---

### Post by jdong on 2005-12-14
[QUOTE=carlosqueso]I'd have a couple concerns, and maybe these are silly.  First, wouldn't it be more helpful if users could test even for packaging bugs as well, since that is what is eventually going to be in the official repo?
[/quote]
Well, in the process of making and using the backport, packaging bugs will indeed be exposed.

> 
 Second, how will you ensure that the official backport supercedes the testing one? 

Version numbers. Official backports are named ~breezy1, ~breezy2, and so on, while unofficial backports are named ~breezy**0.**1, etc.

---

### Post by ubuntu_demon on 2005-12-14
[QUOTE=ember]It is more fun ;) ... I did a personal backport of kino today and it is nicer to see how compiling messages run through and eventually you have your own package than just do a boring apt-get update ;)[/QUOTE]
So I'm looking forward to having a bit of fun :)

---

### Post by Confuse on 2005-12-15
So help me understand. If this goes through, backporting will be personalized? Meaning all will have the ability to easily backport a package? How do you guys go about choosing what goes into backports when you have multiple people submitting their own? Will the admins be in charge of officially backporting whatever is requested and this script just to keep the masses happy? From what I understand it'll just create a lot of multiplebackports, but its nice that we'll have the power to backport what we want whenever we want for sure. 

Also, there are many features sometimes the backporter doesn't include which we can enable ourselves that do not limit functionality. I just "backported" xchat-gnome 0.7 thanks to the instructions on one member and SSL was disabled on the backported one but now ssl works, so this could be a nice thing! Good job, I hope it works out! =]

---

### Post by jdong on 2005-12-15
There will be a one-command method of backporting (i.e. "backport xchat") for users, so that they can track upstream easily.

Official backports will be provided for convenience, picking conservative updates and saving you compile time.

---

### Post by btdown on 2005-12-15
stop teasing...roll that bitch out!~

---

### Post by ubuntu_demon on 2006-04-04
jdong what happened to this ? Will this get released together with Dapper ?

---

### Post by jdong on 2006-04-04
We are bring everything onto Launchpad for better integration... A staging branch is still being considered, though there is a maintenance factor involved. I'd actually like to see a "Bleeding Edge Ubuntu Team" type of thing formed that did what old Backports did, and Backports is a stabilized version of that tree. I'm sure we have users around here that would like to go a bit more bleeding-edge than Backports but not go all out development version.

If we do any kind of unofficial tree like this, it needs to be well integrated with Ubuntu efforts, otherwise support will be a headache to everyone, like Warty Backports.

---

### Post by ubuntu_demon on 2006-04-05
[QUOTE=jdong]We are bring everything onto Launchpad for better integration... A staging branch is still being considered, though there is a maintenance factor involved. 
[/QUOTE]

thnx for the fast answer 

[QUOTE=jdong]
I'd actually like to see a "Bleeding Edge Ubuntu Team" type of thing formed that did what old Backports did, and Backports is a stabilized version of that tree. I'm sure we have users around here that would like to go a bit more bleeding-edge than Backports but not go all out development version.
[/QUOTE]

Okay cool

[QUOTE=jdong]
If we do any kind of unofficial tree like this, it needs to be well integrated with Ubuntu efforts, otherwise support will be a headache to everyone, like Warty Backports.[/QUOTE]

agreed

And what about the pbuilder scripts to backport packages easily yourself?

---

### Post by jdong on 2006-04-05
[QUOTE=ubuntu_demon]
And what about the pbuilder scripts to backport packages easily yourself?[/QUOTE]

The idea still remains, though not much work is going into it at this point. I anticipate it'll be something we put into Dapper+1 and backport to Dapper.

---

### Post by jdong on 2006-04-05
[QUOTE=ubuntu_demon]
And what about the pbuilder scripts to backport packages easily yourself?[/QUOTE]

The idea still remains, though not much work is going into it at this point. I anticipate it'll be something we put into Dapper+1 and backport to Dapper.

---

### Post by jdong1337 on 2006-04-05
Ok....this is kinda of topic but jdong....how did u get ur name cuase i use jdong as my name all the time and i was just browsing and i found jdong lol
oh and i am a newmember of the ubuntu forums i have ordered lots of free ubuntu disks ... i have not tried it out my self quite yet but ......well never try to give it out to peeps at school lol yeah ok just like its kinda cool to have some one with the same name as me on the internet;) 
--------------------------------------------------------------------------
PS I am most likely using tor for when ppl post stupid stuff i get mad 
(ur sql server < then my sql server):D

---

### Post by ubuntu_demon on 2006-04-06
[QUOTE=jdong]The idea still remains, though not much work is going into it at this point. I anticipate it'll be something we put into Dapper+1 and backport to Dapper.[/QUOTE]

okay thnx for the info!

---

### Post by byteshack on 2006-05-20
This looks very promising.  I was directed to this post after posting about scripts to generate current packages in the repositories.  The reason why I wanted a script that would generate any given package in the current repositories was so that I could modify the script and generate myself some backports.  IMHO this would not only allow people who aren't afraid of playing around under the hood to get newer versions of packages into their systems, but could maybe even speed the process of getting newer version to the repos for the simple reason that more people can try to generate them.

---

