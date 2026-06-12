---
title: "Making &quot;extras&quot; official..."
date: 2005-08-26
forum: The Cafe
---

### Post by c0rderr0y on 2005-08-26
I would like to see extras made official so it can be maintained properly because there are MANY programs that I use on it, the extras currently arent working and there a lot of things on it that I need and it is keeping me from using this great distro.  I am sure there are many others who are in the same boat. This is a good distro which is why it is the more popular one right now on distro watch. Please people hear my voice~! I want it to be made official so bad I would donate cash.... anyone with me on this?

---

### Post by tommy04 on 2005-08-26
What are these "extras" you speak of?

---

### Post by c0rderr0y on 2005-08-26
the extra backports which lets you install gaim gimp and A LOT more others, currently the extras are broken and many people are having problems atm.  I really love this distro but if extras isnt going to be maintained properly I might as well go back to slackware for my lappy.  (Which I deffinatly DO NOT want to do)

---

### Post by tommy04 on 2005-08-26
[QUOTE=c0rderr0y]the extra backports which lets you install gaim gimp and A LOT more others, currently the extras are broken and many people are having problems atm.  I really love this distro but if extras isnt going to be maintained properly I might as well go back to slackware for my lappy.  (Which I deffinatly DO NOT want to do)[/QUOTE]
 Gaim and Gimp come with Ubuntu...
Backports is a 100% community-driven project. Right now the lead guy there (only?) is doing... something else that I forgot.
I would like to see a new backports-like project though.

---

### Post by c0rderr0y on 2005-08-26
I use Kubuntu =T and they arent in the basic install.... plus it seems back ports are all screwy right now which makes me cry.

---

### Post by KingBahamut on 2005-08-26
I got yer back.

---

### Post by Wolki on 2005-08-26
[QUOTE=c0rderr0y]I use Kubuntu =T and they arent in the basic install.... plus it seems back ports are all screwy right now which makes me cry.[/QUOTE]

They aren't in Kubuntu because they're gtk apps and it's Qt based. You can install them from the standard Ubuntu repositories though, like a Ubuntu user can install Kopete.

Money is one of the problems of the extra repositories (and it's a big one, just look at the licensing fees of mp3 and think of how many more formats there are...), but it's not the only one. The people behind Ubuntu have strong feelings towards Free software (with all it's meanings), and though i feel some non-Free stuff might be currently necessary for many users, i think we should respect their decision as far as standart repos are concerned.

Backports usually work great, though there might be difficulties with single apps. If a repo is down, try another mirror or just wait a little until the server works again.

---

### Post by drizek on 2005-08-26
Just go into your mp3 directory and open a terminal and do

apt-get install mp32ogg (need to enable universe)
mp32ogg *
rm *.mp3

and youll find that you can play all the files in that folder on a default ubuntu install. its like magic.

Edit: in case you didnt figure it out, this will replace your mp3's with ogg's. ;)

---

### Post by ow50 on 2005-08-26
People, remember the difference between backports, which is these days an official Ubuntu project with proper hosting and extras which will never be official due to legal issues. But I agree that extras could use more reliable and faster hosting. I doubt any cash would make a difference, you just need careful management for reliability and kind souls to provide fast mirrors.

---

### Post by SGC on 2005-08-26
[QUOTE=drizek]Just go into your mp3 directory and open a terminal and do

apt-get install mp32ogg (need to enable universe)
mp32ogg *
rm *.mp3

and youll find that you can play all the files in that folder on a default ubuntu install. its like magic.[/QUOTE]
 At least warn the people before you tell them to remove thier entire MP3 collection.

---

### Post by c0rderr0y on 2005-08-26
well okay not official but officially supported and this is to help persuade the devs to make it atleast supported by their servers...... and i know many people would like it if it was more officially supported.... i also think this would help out the community more by donating money and giving  the developers an incentive to make an awsome distro out of already great one.

---

### Post by Burgundavia on 2005-08-27
Most of the things in extras cannot legally be distributed by Ubuntu and thus cannot be supported. There has been an effort in Breezy to get some of the redistributable stuff (but not neccessarily DFSG-free) into multiverse.

Things that will never be on Ubuntu servers are:
-w32codecs (this violates copyrights as well as patents)
-j2re (the sun one. Blackdown java 1.4 is now in multiverse and free java is shipped by default)

Corey

---

### Post by c0rderr0y on 2005-08-27
hmm never thought of that... but as long as we have a "good" extras server i bet it will keep everyone happy....

---

### Post by Kvark on 2005-08-27
The backports are made official right?

So the only things that won't be official are the ones with legal issues, thats very few packages right?

It's only a small annoying problem and not a major showstopper if thats the case.



But it'd be nice with one official version without the patented stuff for the parts of the world where you can patent software algorithms and another official version with patented stuff for the rest of the world.

I'm pretty sure you can't patent a software algorithm where I live so I'd like to have an mp3 codec and that other stuff out of the box and I don't care if it's illegal somewhere else. Just like I have a bible and don't care that it's probably illegal somewhere else too.

---

