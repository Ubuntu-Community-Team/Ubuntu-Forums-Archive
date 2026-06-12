---
title: "Akai MPD32"
date: 2008-06-20
forum: Ubuntu Studio
---

### Post by omgwtflol on 2008-06-20
Will it work with Ubuntu?  Because I would not like to use it in Windows.

[http://www.zzounds.com/item--AKAMPD32](http://www.zzounds.com/item--AKAMPD32)

---

### Post by Stochastic on 2008-06-21
If it's USB standards compliant, then it should work fine in Ubuntu.  Give it a shot at let us know.

---

### Post by deadgobby on 2008-06-22
> **omgwtflol said:**
> Will it work with Ubuntu?  Because I would not like to use it in Windows.

[http://www.zzounds.com/item--AKAMPD32](http://www.zzounds.com/item--AKAMPD32)

 OK my question is what you are want to do with this? Running midi to record via to lets say Rosegarden or Jokester? Do you want it to run as master to play Hydrogen? What do you want to do? Please be more in detail on what you want to accomplish with this cool instrument. If you are looking for pro tools like style. No! It is not going to happen yet. YET is the key word here. I do want to point out a very help full web site that can help you build up to you want to do. That is.
[http://www.vintagesynth.com/](http://www.vintagesynth.com/)
 Please be very down to the point on what you want do and what O/S you are using when you post. Being detailed on posting on the link I gave is very important. As to here to. I want to help but this is only what information you gave. 
Gobby

---

### Post by Sakrimo on 2008-06-23
i've looked at the akai32 so many times, and whilst i may be more into singer-songwriter recording and heavier music, i can't help but think that this is a very expensive tool for what it does.

Do you plan to use it live? I'm sure you could get similar results by using software. I know at least Virtual DJ gave me the results i was after from this when i looked at it, but i'm sure that there would be something out there that could do 'just' that job without eating up so much memory and giving more of a useable environment between that and your recording software (virtual dj takes over the entire screen, and LOTS of RAM.)

---

### Post by Stochastic on 2008-06-24
Deadgobby, that link you posted is of little help to getting the MPD32 running in Ubuntu.  Furthermore, your post seems to suggest that there isn't a pro-tools like software environment for Ubuntu, but newbies should know that Ardour is roughly equivalent to pro-tools.  If you were suggesting that Ardour doesn't accept general MIDI controllers just yet, you'd be wrong - as of Ardour 2 in the Options -> Control Surfaces  menu, there is the option for Generic MIDI controllers to be used (I haven't used this option yet, so I can't go into too much detail on it).  Lastly, your rant about which OS the poster is using seems out of place as they did specify Ubuntu.

---

### Post by prismatic7 on 2008-06-25
> **Stochastic said:**
> If you were suggesting that Ardour doesn't accept general MIDI controllers just yet, you'd be wrong - as of Ardour 2 in the Options -> Control Surfaces  menu, there is the option for Generic MIDI controllers to be used (I haven't used this option yet, so I can't go into too much detail on it).  

An aside: I *have* used this feature in Ardour (with an M-Audio Axiom 49 - which also has drum-pads) and it works brilliantly.

Returning to the MPD32, as far as I am able to work out it *is* class-compliant, which means that it should be able to work without a vendor-supplied driver. USB MIDI device support in Ubuntu has been pretty good for a year or two now, and so long as the software you use supports MIDI Learn (assigning controllers to parameters) you can have a LOT of fun :)

**Stochastic** - would it be worth putting together a 'known-to-work' hardware list, either here or on the wiki? Pro-Audio gear can be expensive, so maybe we need to share working configs with users..?

---

### Post by omgwtflol on 2008-06-26
> **prismatic7 said:**
> **Stochastic** - would it be worth putting together a 'known-to-work' hardware list, either here or on the wiki? Pro-Audio gear can be expensive, so maybe we need to share working configs with users..?
Yes, that would be awesome.

I new to Ubuntu so I haven really tried all the other audio apps.  However I tried LMMS because it was said to be somewhat of an equivalent to FL Studio.  And to my surprise, when I plugged in my MPD 32 and started LMMS up it worked.  I selected one channel to control with my MPD.  I havent found out how to control multiple samples yet though. :(

---

### Post by Stochastic on 2008-06-27
The troubles with a "known to work" list is that it quickly becomes a duplicate of the ALSA matrix and ffado listings (but with less information), and also runs the risk of being outdated quickly.

---

### Post by cerke on 2012-12-01
hi guys!
I know that I'm bringing an old topic up, but it is exactly what I need

just bought an mpd32 and now I'm trying to make it work with hydrogen or lmms.
didn't figure it out yet.
managed just to connect one drum sound to a channel, but it automatically puts it on every pad pitched by a half tone...
what to do? o.O

---

