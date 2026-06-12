---
title: "Is Synaptic Reliable? I Don't Think So."
date: 2006-03-21
forum: The Cafe
---

### Post by Swiss on 2006-03-21
Is Synaptic Reliable? I Don't Think So! Nearly all of my problems in Ubuntu has stemmed from Synaptic, It stops working after about 1-2 weeks, then I post on this forum, get no (or not helpful at all) replies! Then I usally end up reinstalling!
That's the reason why I am back to using Windows more.... :confused:  :(

---

### Post by AndrewB on 2006-03-21
I've run into problems like that before. My ultimate solution, was to be sure to disable all non-official Ubuntu repositories after use. That way all updates are official\\:D/ 

just my 2 dineros,
Andrew

---

### Post by Buffalo Soldier on 2006-03-21
Perhaps it's your sources.list files? Synaptic has been kind to me all this while. Sorry for not noticing your other post/threads.

---

### Post by htinn on 2006-03-21
Actually, I've had my connection die on me during Synaptic sessions and it was able to deal with it. I could save my marks if necessary, and Synaptic could install around whatever failed to download.

Honestly, it does everything perfectly except for partial downloads, and I think that's being worked on.

---

### Post by localzuk on 2006-03-21
I would say it is not synaptic but something you have done - it looks like you have used automatix (which is sometimes unstable, there are plenty of people who have complained about it...).

What is the specific problem you are having? (Rather than trawl through all your prior posts to find the issues).

---

### Post by CompShrink on 2006-03-21
Please explain your problems and we'll try to help you. I'm sorry you didn't have luck on the forums before.

Personally, I have had no issues with synaptic, other than from the use of unofficial packages, and those have been minor issues as well.

---

### Post by Brunellus on 2006-03-21
[QUOTE=Swiss]Is Synaptic Reliable? I Don't Think So! Nearly all of my problems in Ubuntu has stemmed from Synaptic, It stops working after about 1-2 weeks, then I post on this forum, get no (or not helpful at all) replies! Then I usally end up reinstalling!
That's the reason why I am back to using Windows more.... :confused:  :([/QUOTE]
perhaps you were using it with that revolutionary no-click interface?

In seriousness.  apt/synaptic itself isn't that much of a problem for me.  Things will break, however, if you mix repositories willy-nilly.  If you stay within the ubuntu main, universe, and multiverse repos, you should be in good shape.  

Adding debian unstable repos to your sources.list would be a good and quick road to breakage if you don't know what you're doing.

HOWEVER.  If you're still having a problem, open a terminal and

sudo apt-get -f install

apt will then try to fix your broken packages.

If you're having trouble with connections timing out, try pointing your sources.list to a different mirror, preferrably (but not necessarily...) the one closest to your location, geographically.

---

### Post by Swiss on 2006-03-21
> 
HOWEVER. If you're still having a problem, open a terminal and

sudo apt-get -f install

apt will then try to fix your broken packages.

Actually, one of the times SYN wasn't working, (the last one I think) apt was not working at all, I did "apropos apt" and tried all likely commands, but none worked. 
> 
I would say it is not synaptic but something you have done - it looks like you have used automatix (which is sometimes unstable, there are plenty of people who have complained about it...).

Yes, I did use Automatix, but the problems didn't start until a few days after. 


> 
What is the specific problem you are having? (Rather than trawl through all your prior posts to find the issues).

At the moment I'm not having problems (I booted haven't into Ubuntu in a while) But you can see for some of my other posts what the problem was.

---

### Post by Brunellus on 2006-03-21
I think this post points to a possible solution to your problem:

[http://www.ubuntuforums.org/showpost.php?p=816553&postcount=5](http://www.ubuntuforums.org/showpost.php?p=816553&postcount=5)

I'm guessing you were a bit overzealous in terms of host/port blocking on iptables.

---

### Post by Swiss on 2006-03-21
I don't remember ever changing my IP tables... I did have (as you can see) a firewall runing.

---

### Post by Brunellus on 2006-03-21
[QUOTE=Swiss]I don't remember ever changing my IP tables... I did have (as you can see) a firewall runing.[/QUOTE]
the firewall merely a frontend to IPtables.

---

