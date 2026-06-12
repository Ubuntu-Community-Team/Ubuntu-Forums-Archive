---
title: "A Rant"
date: 2009-11-04
forum: Testimonials &amp; Experiences
---

### Post by fredfelter on 2009-11-04
Microphone doesn't work!!!!

I have to date enjoyed using Ubuntu for the last couple of years or so for a majority of my computer needs and learning about Linux at the same time. I eagerly looked forward to the new version 9.10 Karmic which I installed yesterday. Now I find I cannot use the microphone on my Thinkpad T22, neither for Skype nor for the sound recorder. I believe I have made all the usual adjustments to sound preferences and AlsaMixer, to no avail. A web search reveals that this is an extremely common problem over a wide range of computers with literally hundreds of complaints and scores of "solutions" on various forums. I spent over 2 hours trying to solve it but cannot.

I consider this situation inexcusable and indicative of why Ubuntu has such a miniscule market share. Why was this new version released with such a major problem? And if such a deficiency exists why is there no centralized data base to explain how to fix it, or is there no fix? Why should hundreds like myself have to individually invest hours searching for a solution that should have a common answer? I don't use Ubuntu because I want to be challenged each time I perform a new install - I expect it to work at least as well as the one I changed from. 

Since I'm dependent on a workable mic I'm going to go back to Windows, and even though I would rather not, I do not have any more time to dedicate to such an elusive target.

---

### Post by yeats on 2009-11-04
> Now I find I cannot use the microphone on my Thinkpad T22, neither for Skype nor for the sound recorder. I believe I have made all the usual adjustments to sound preferences and AlsaMixer, to no avail. A web search reveals that this is an extremely common problem over a wide range of computers with literally hundreds of complaints and scores of "solutions" on various forums. I spent over 2 hours trying to solve it but cannot.

Are you asking for help on this issue?  It sounds like there are several sound-related (mainly Pulse Audio-related) problems with Karmic, and someone may be able to assist if you give them a chance (and more details).

Regarding your other comments, I understand your frustration - probably everyone on the forums has hit up against something similar at one time or another - I know I have.  I think it's just part of the trade-off of using free/open source software.  In your case, if you decide to stay with Ubuntu, you might want to put off upgrading until some of these sorts of issues are worked out, or are at least better documented.

---

### Post by fredfelter on 2009-11-05
Thanks for the measured reply Chris.
I guess I'm looking to vent frustration more than to ask for help. 

Firstly, I don't want to hear someone suggest that since this is a common problem already addressed many times in the forums that I should be using Search instead of posing the same question over again. 

Secondly I'd like to claim that Ubuntu has great potential as I see it but needs to have a much better mechanism for non-experts like myself to solve problems. There must be a better way to collate information such that real solutions to significant bugs are easy to find and easy to understand and apply. Having each of us deal with the mostly same microphone problem by having to sort through endless forum messages, most of which are not pertinent, is just not viable for lay people like me. I want badly to have Ubuntu work for me but I just don't have enuf time to invest in problem solving in the way it has to be done presently.

---

### Post by running_rabbit07 on 2009-11-05
> **fredfelter said:**
> Why was this new version released with such a major problem? And if such a deficiency exists why is there no centralized data base to explain how to fix it, or is there no fix? Why should hundreds like myself have to individually invest hours searching for a solution that should have a common answer?

Did you try the LiveCD before upgrading? 

How much money did you pay for this OS?

Good luck with which ever OS you end up using, though I'd hope when you cool off, you'll find the easy fix for your system.

---

### Post by kixome on 2009-11-05
> **fredfelter said:**
> Microphone doesn't work!!!!

I have to date enjoyed using Ubuntu for the last couple of years or so for a majority of my computer needs and learning about Linux at the same time. I eagerly looked forward to the new version 9.10 Karmic which I installed yesterday. Now I find I cannot use the microphone on my Thinkpad T22, neither for Skype nor for the sound recorder. I believe I have made all the usual adjustments to sound preferences and AlsaMixer, to no avail. A web search reveals that this is an extremely common problem over a wide range of computers with literally hundreds of complaints and scores of "solutions" on various forums. I spent over 2 hours trying to solve it but cannot.

I consider this situation inexcusable and indicative of why Ubuntu has such a miniscule market share. Why was this new version released with such a major problem? And if such a deficiency exists why is there no centralized data base to explain how to fix it, or is there no fix? Why should hundreds like myself have to individually invest hours searching for a solution that should have a common answer? I don't use Ubuntu because I want to be challenged each time I perform a new install - I expect it to work at least as well as the one I changed from. 

Since I'm dependent on a workable mic I'm going to go back to Windows, and even though I would rather not, I do not have any more time to dedicate to such an elusive target.

thats why I stayed with hardy, my **** with intel 915 graphics, and microphone working flys! also sound recorder doesn't format wavs properly, use gnusound instead.

---

### Post by kixome on 2009-11-05
oh, have you tried unmuting the mic?

---

### Post by KIAaze on 2009-11-05
Audio problems in Ubuntu 9.10:
[http://ubuntuforums.org/showthread.php?t=1307019](http://ubuntuforums.org/showthread.php?t=1307019)
[http://drowninginbugs.blogspot.com/2009/10/caveats-for-audio-in-910.html](http://drowninginbugs.blogspot.com/2009/10/caveats-for-audio-in-910.html)

This seems to be the most likely solution:
> Install linux-backports-modules-alsa-karmic (then reboot) if you have a very new computer, because that package enables audio on quite a few very new laptop models and contains much improved support for microphone auto-switching.
```
sudo apt-get install linux-backports-modules-alsa-karmic
```

> Secondly I'd like to claim that Ubuntu has great potential as I see it but needs to have a much better mechanism for non-experts like myself to solve problems. There must be a better way to collate information such that real solutions to significant bugs are easy to find and easy to understand and apply. Having each of us deal with the mostly same microphone problem by having to sort through endless forum messages, most of which are not pertinent, is just not viable for lay people like me. I want badly to have Ubuntu work for me but I just don't have enuf time to invest in problem solving in the way it has to be done presently.

Ubuntu 9.10 known issues and their solutions:
[http://www.ubuntu.com/getubuntu/releasenotes/910](http://www.ubuntu.com/getubuntu/releasenotes/910)

You could try the official Ubuntu support for which you have to pay, but I don't know how efficient it is.

Otherwise, this forum, the [wiki]("https://wiki.ubuntu.com/") and [launchpad]("https://launchpad.net/") are usually very efficient for finding help (especially with the help of google).

You can also [report your problem as a bug]("http://www.ubuntu.com/community/ReportProblem").

And never forget that you can dual-boot if you don't have time to deal with this problem at the moment!

---

### Post by wxnker on 2009-11-05
> Since I'm dependent on a workable mic I'm going to go back to Windows, and even though I would rather not, I do not have any more time to dedicate to such an elusive target.
If that's what is needed to vent your frustrations then do so, but it's not like you don't have choice...

- Solve the issue with the help of the excellent Ubuntu community.
- Use 9.04 if it works better for you
- Use another Linux distro. It's not like Ubuntu is the only easy to use Linux choice out there.

---

### Post by sliketymo on 2009-11-05
Actually,there are mechanisms in place.Forum? Bug-Reports?
You appear to be so easily frustrated,that you may in fact not be a good fit with the particular version that is causing you problems.I find it rather hard to beleive that in two years use,you have not discovered the multitude of resources that are available,not just through Canonical.How about your local library?

---

### Post by running_rabbit07 on 2009-11-05
> **sliketymo said:**
> How about your local library?

Yup, I have seen quite a few Linux books at the public library.

---

### Post by GodLikeCreature on 2009-11-05
I swear to God I thought the OP was being sarcastic and this was all a joke on the typical "I hate Ubuntu <enter new release name here> because my <enter random external device here> does not work now!!!!"

I honestly find it a bit ridiculous that anybody would rant on an operating system because their mic stopped working.  I don´t know, sounds funny to me.

To be honest, if something is working Ok, why risk it by upgrading right after release date?  Why not sticking to the working version?  Why not upgrading after the smoke clears and there are fixes to bugs?...  

In my opinion, it is great that non expert users are trying Ubuntu, but they should be conscious of their limitations and take the safe route, instead of jumping into cold waters.

For future reference, I would recommend the OP to upgrade into a release only if necessary, and if it is, upgrade several weeks after release date.  That should save lots of headaches.

---

### Post by solwic on 2009-11-05
> **GodLikeCreature said:**
> I swear to God I thought the OP was being sarcastic and this was all a joke on the typical "I hate Ubuntu <enter new release name here> because my <enter random external device here> does not work now!!!!"

I honestly find it a bit ridiculous that anybody would rant on an operating system because their mic stopped working.  I don´t know, sounds funny to me.

To be honest, if something is working Ok, why risk it by upgrading right after release date?  Why not sticking to the working version?  Why not upgrading after the smoke clears and there are fixes to bugs?...  

In my opinion, it is great that non expert users are trying Ubuntu, but they should be conscious of their limitations and take the safe route, instead of jumping into cold waters.

For future reference, I would recommend the OP to upgrade into a release only if necessary, and if it is, upgrade several weeks after release date.  That should save lots of headaches.

+1 to all of that.  :)

---

