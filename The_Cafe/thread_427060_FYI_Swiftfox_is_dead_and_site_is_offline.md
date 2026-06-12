---
title: "FYI Swiftfox is dead and site is offline"
date: 2007-04-29
forum: The Cafe
---

### Post by inigmatus on 2007-04-29
Just a note to pass along to the community of Swiftfox fans, per a note from the old Swiftfox forums:

After checking to find out why one minute the swiftfox site was working, and the next it was all gone, I did a Google search for swiftfox and forum and came up with this:


per Google cache of the Swiftfox forum:
[http://72.14.253.104/search?q=cache:1tTmzB1WwLQJ:forums.getswiftfox.com/viewtopic.php%3Fp%3D637%26sid%3De62efeea9401e1f408513f0a3c67366a+swiftfox+forum&hl=en&ct=clnk&cd=2&gl=us](http://72.14.253.104/search?q=cache:1tTmzB1WwLQJ:forums.getswiftfox.com/viewtopic.php%3Fp%3D637%26sid%3De62efeea9401e1f408513f0a3c67366a+swiftfox+forum&hl=en&ct=clnk&cd=2&gl=us)

> The time now is Wed Apr 25, 2007 8:05 pm
View previous topic | View next topic
Reply to topic 	Page 1 of 1
Future of Swiftfox
Author 	Message
Jason
Site Admin
Joined: 20 Jul 2006
Posts: 178
Location: New York

	
Reply with quote
Post Future of Swiftfox 
First I want to say thanks to all the great people who have supported Swiftfox over the last 2 years. Recent events in my personal life have led me to conclude that I should be spending more time there than I have been. The forum will remain as it is pretty self-sustaining and Dreamhost is paid up for the next year. At this point I'm not planning on further updates of Swiftfox for the foreseeable future.

Mon Apr 23, 2007 7:41

I'm afraid the website didn't last longer than a week after this cached announcement by Jason, and I'm afraid Swiftfox is extinct. Anyone know how I can uninstall it off my comp?

---

### Post by hyperair on 2007-04-29
NO! How could it be?! Swiftfox was a great product! sigh. Looks like I'll have to deal with bloated ol Firefox again. I think I'll keep swiftfox until the next firefox update comes along though.

Anyway to uninstall it, run this in the terminal:
```

sudo rm -rf `ls /opt | grep swiftfox`
sudo rm /usr/bin/swiftfox
sudo rm ~/Desktop/Swiftfox.desktop
sudo rm /usr/share/applications/Swiftfox.desktop

```

---

### Post by inigmatus on 2007-04-29
Thanks for the uninstall info.

Yeah it's kind of a bummer. I really like the program.

---

### Post by hyperair on 2007-04-29
Yeah, I wonder if anyone will pick up after the author and come up with a new Swiftfox.. For one, the icon looked really cool compared to the original Firefox logo.

---

### Post by Sef on 2007-04-29
> Yeah, I wonder if anyone will pick up after the author and come up with a new Swiftfox.

Well since it is open sourced, someone could come and pick it up.

---

### Post by tehkain on 2007-04-29
Well this will soon give me a reason to move completely over to epiphany. I like firefox but its just a little too bloated. At least I am staying with a good ole gecko based browser.

---

### Post by mskadu on 2007-04-29
Its a shame. It would have been great for the author to release the code to open source. 


Anyway, I hope he finds what he's looking for.

---

### Post by dcstar on 2007-04-29
> **mskadu said:**
> Its a shame. It would have been great for the author to release the code to open source. 

Anyway, I hope he finds what he's looking for.

What "code"?, it is just the Firefox code compiled with the various switches for various CPUs.

He posted all compiler options with every release, everyone is free to use the exact same options to compile their own "Swiftfox" version for their CPU - basically all he did was all of that work and conveniently package it for all of us (which would be time-consuming given all of the different versions).

---

### Post by mskadu on 2007-04-29
Oh, is it? Where can i find this info, now that that the site is dead? I dont see why we cant start a sourceforgeproject using whatever's available. :guitar:


> **dcstar said:**
> What "code"?, it is just the Firefox code compiled with the various switches for various CPUs.

He posted all compiler options with every release, everyone is free to use the exact same options to compile their own "Swiftfox" version for their CPU - basically all he did was all of that work and conveniently package it for all of us (which would be time-consuming given all of the different versions).

---

### Post by cmost on 2007-04-29
Anyone know of an alternative mirror for debs?  I uninstalled mine via Automatix thinking I could upgrade from 2.0.0.1 to 2.0.0.3 by reinstalling.  Imagine my dismay when I find out the site is gone!!  Thanks for assistance.

---

### Post by Rhapsody on 2007-04-29
Who cares? Swiftfox was never that great anyway. The license agreement on the binaries was ludicrously restrictive (you weren't even allowed to redistribute unmodified binaries, so you could forget ever seeing it in the repos), most of the speed gain was had by removing pango (so it screwed up on some non-latin characters), and the speed gain could only really be seen in benchmarks.

You want a quick Firefox? Grab the sources, turn the compilation switches as high as you dare, and just compile your own! You don't need to be a rocket scientist!

---

### Post by hyperair on 2007-04-29
How about providing a step by step tutorial to the compilation switches, huh? You make it seem that simple, but truth be told not many of us know.

---

### Post by lingenfr on 2007-04-29
I am setting up my Libretto U100 and when I go to any of the servers at that domain, I get a directory listing. Anyone know what's up?

---

### Post by xpod on 2007-04-29
> How about providing a step by step tutorial to the compilation switches, huh? You make it seem that simple, but truth be told not many of us know.

It`s only easy when you know how eh:) 

I first tried swiftfox not long after first installing Ubuntu(dapper) but i didn`t really see any noticeable speed differences back then and so sacked the thing after a week or two.Tried it out again just prior to the fiesty release though and it was waaaaay faster than FF both on edgy and here on fiesty.

Of course that was just normal usage without all that benchmarking...i was too busy with the rocket science:)

---

### Post by qamelian on 2007-04-29
Check here for info: [http://en.wikipedia.org/wiki/Swiftfox](http://en.wikipedia.org/wiki/Swiftfox)

---

### Post by xpod on 2007-04-29
See the thread below this:)

EDIT: below this for now anyway

---

### Post by Anthem on 2007-04-29
Just use Mozilla's Firefox, instead of Ubuntu's one.

Ubuntu has been crippling firefox for a long time.

Although the problem seems to be less on Feisty.

---

### Post by lingenfr on 2007-04-29
> **qamelian said:**
> Check here for info: [http://en.wikipedia.org/wiki/Swiftfox](http://en.wikipedia.org/wiki/Swiftfox)

OK, thanks. I went to that site looking for download mirrors. Guess I should have read the article first. Too bad, I liked it.

---

### Post by bapoumba on 2007-04-29
@ lingenfr: merged your thread in here.

---

### Post by aysiu on 2007-04-29
This is sad news for people who have grown to love Swiftfox. I know a lot of people here swear by Swiftfox being *much* faster than Firefox.

I haven't found that to be the case on my Ubuntu installations, but I can't imagine other people are lying.

---

### Post by Rhapsody on 2007-04-29
> **aysiu said:**
> This is sad news for people who have grown to love Swiftfox. I know a lot of people here swear by Swiftfox being *much* faster than Firefox.

I haven't found that to be the case on my Ubuntu installations, but I can't imagine other people are lying.

They needn't be. There's a well-known phenomenon called the 'placebo effect', where the belief that something will have an effect actually causes a perception of that effect, regardless of whether it's actually happening. If people can feel less pain and get improved health from sugar pills, I think they can be convinced that pages are loading faster when there's actually no discernible difference.

---

### Post by K.Mandla on 2007-04-29
Ah well. I'm glad I held on to the Pentium III deb. 

It's kind of sad. I'm sure a lot of work went into that, and Jason drew a lot of flak for a while over licensing and whatnot. Faster or not, it had a following.

---

### Post by longfinkillie on 2007-04-29
Does anyone know where there are hidden debs for celeron?  I unfortunately deleted mine as well.  
Even though I never noticed  a noticeable difference, that was my browser of choice.  "First the Fat Boys break-up, now this."

---

### Post by longfinkillie on 2007-04-29
swiftfox is back?

[http://getswiftfox.com/debian.htm]("http://getswiftfox.com/debian.htm")

---

### Post by Lucifiel on 2007-04-29
Hmmm, perhaps the developer received some offers of help or something.

Nevertheless, Swiftfox is a good product. :)

---

### Post by kodoku on 2007-04-29
YAYYYY!! its back.

---

### Post by hyperair on 2007-04-30
Talk of a false alarm. 

EDIT: next time I'll quote the entire post. Perhaps it had been deleted, and maybe I typed the wrong name. Sorry, Lucifiel :)

---

### Post by cmost on 2007-04-30
Thank goodness!!  I love my Swiftfox.  Installing it with plugins via Automatix is almost trivial compared to the finagling required to get a comparable 32 bit Firefox with plugins installed on a 64 bit Ubuntu system.

---

### Post by Lucifiel on 2007-05-01
> **hyperair said:**
> Talk of a false alarm. 

@Lucifiel: While the placebo effect certainly exists and certainly functions as you say it does, this is not one of them. Benchmarks published online have shown that Swiftfox really is faster and more responsive than the original Mozilla Firefox. Even I did my own, shoddy benchmark. I opened a certain number of tabs, and in Swiftfox it was still working fine with no lag, but Firefox had its window completely stop responding. They were not run at the same time.

Huh??? I think you're talking to the wrong person?

---

### Post by Rhapsody on 2007-05-02
hyperair: You were probably talking to me.

But, to answer, I tried some benchmarks too and saw they indicated improved performance. But those are benchmarks, what about real-world improvement? There are a hell of a lot of variables, and I'd bet that in-between the usual shuffle of moving between tags, server speeds fluctuating, extensions bogging the browser down, and even other applications eating up resources, most of that improvement (which is pretty marginal compared to the difference between Firefox/Swiftfox and other browsers like Konqeuror, Epiphany, or Opera) will be lost.

The best way to properly test this would be with a double-blind study over a considerable period. I think if you did that, you'd find that the difference would only just manage to be statisically significant. Maybe someone should post this on the MythBusters message board?

---

### Post by hyperair on 2007-05-02
This Swiftfox vs Firefox battle could almost get to the size of the bittorrent clients battle in terms of download speed.

---

### Post by josephus on 2007-05-02
i don't think it would make for very interesting TV trying to bust this myth.  Not unless they somehow make the computer explode at the end.  Maybe they could bust the myth of the cpu that overheats and explodes.

---

### Post by PrimoTurbo on 2007-05-02
I used swiftfox in the past but later I did some personal tests and found no significant differences excpet that swiftfox for some reason seemed to mess up fonts more often.

---

