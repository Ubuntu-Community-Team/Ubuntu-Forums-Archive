---
title: "Why aren't binary and decimal prefixes used properly?"
date: 2007-11-12
forum: The Cafe
---

### Post by NovaAesa on 2007-11-12
Why is it that binary prefixes and decimal prefixes are used incorrectly, even in Linux? From my understanding, the following prefixes mean the following things:

K = 10^3
M = 10^6
G = 10^9
Ki = 2^10
Mi = 2^20
Gi = 2^30

But Ubunutu doesn't seem to want to use the prefixes in the right places. Example, when I right click a file and go to properties, under size I get 298.1 KB (305262 bytes). This just doesn't seem to make sense. 305262 = 305.2 KB = 298.1KiB. So the prefix in the properties window should be KiB, or the number before the prefix (298.1) should really be calculated differently. And this same kind of problem appears in other kinds of places as well.

I know that Windows has the same kind of problem, but this is Linux we're talking about here, we should be able to get things right! This is an IEC standard, so shouldn't Linux use it?

Discuss.

---

### Post by rsambuca on 2007-11-12
You are getting your designations confused a bit.  In computing, a traditional kilobyte refers to 1024 (or 2^10).

---

### Post by LaRoza on 2007-11-12
[http://en.wikipedia.org/wiki/Binary_prefix](http://en.wikipedia.org/wiki/Binary_prefix)

This is a common confusion, look at the chart to see what the really mean. ([http://en.wikipedia.org/wiki/Binary_prefix#SI_prefixes_used_in_the_binary_sense](http://en.wikipedia.org/wiki/Binary_prefix#SI_prefixes_used_in_the_binary_sense))

---

### Post by reacocard on 2007-11-12
> **rsambuca said:**
> You are getting your designations confused a bit.  In computing, a traditional kilobyte refers to 1024 (or 2^10).

traditionally yes, however that is technically incorrect, kibibyte is correct. There was actually a discussion about this on ubuntu-devel some months ago, but I don't recall whether anything was actually decided.

---

### Post by NovaAesa on 2007-11-12
> **reacocard said:**
> traditionally yes, however that is technically incorrect, kibibyte is correct.

So traditionally 1KB = 1024 bytes, but as of today's standards 1KB = 1000 bytes and 1KiB = 1024? Shouldn't we be going off today's standards, not off something that is only true traditionally?

---

### Post by reacocard on 2007-11-13
> **NovaAesa said:**
> So traditionally 1KB = 1024 bytes, but as of today's standards 1KB = 1000 bytes and 1KiB = 1024? Shouldn't we be going off today's standards, not off something that is only true traditionally?

yes, but its become habit now to use kilobyte and the like, and people don't like changing habits. Note that not all applications are guilty of this misuse, the Deluge bittorrent client, for example, does use the correct prefixes.

Here's the wikipedia page on binary prefixes, lots of good info there: [http://en.wikipedia.org/wiki/Binary_prefix](http://en.wikipedia.org/wiki/Binary_prefix)

---

### Post by LaRoza on 2007-11-13
> **NovaAesa said:**
> Shouldn't we be going off today's standards, not off something that is only true traditionally?

What ever word is used, CPU's are understand two things, on/off. The names of 2^3 are just for humans. It is confusing, yes, but that is life.

---

### Post by samjh on 2007-11-13
> **NovaAesa said:**
> So traditionally 1KB = 1024 bytes, but as of today's standards 1KB = 1000 bytes and 1KiB = 1024? Shouldn't we be going off today's standards, not off something that is only true traditionally?

The problem with the IEC standard for those prefixes, is that it is only a standard written on paper, and agreed by some other standard bodies.

You don't have a real standard, unless it is used by the majority in the industry, academia, and end-users.  Use of the IEC prefixes are few and far between, nor was there any significant demand from industry or society for those standards when they were written.  At least most standards we take for granted were devised because of a need from the industry, or because they were conventions already widely used.  The IEC prefixes were never demanded in any significant way by anyone except standards organisations!  Talk about self-serving!

IMHO, they should just dump the IEC prefixes and go with the old IEEE standard of having context-dependant meanings for SI prefixes.

---

### Post by NovaAesa on 2007-11-13
> **reacocard said:**
> yes, but its become habit now to use kilobyte and the like, and people don't like changing habits.

That sounds like a pretty bad reason to be using the technically wrong notation. Sure, people don't like changing habits, but habits are going to have to be changed sooner or later (or at least I hope they do). I'm sure there are lots of people that have changed their OS 'habit' from Windows to Linux, but I'd bet most of them are thankful for that change in habit now. To me, using the wrong prefixes just seems unprofessional. It feels a bit like when you see someone write "your" instead of "you're". Sure you can still figure out what they really mean, but it would just be nicer if they would use the right term.

> **reacocard said:**
> Note that not all applications are guilty of this misuse, the Deluge bittorrent client, for example, does use the correct prefixes.


Yes I had noticed that. Yay for the Deluge team :) . I suppose in reality it's not a Ubuntu specific thing really. I would think that it would be the GNOME people that would have to fix it.

---

### Post by NovaAesa on 2007-11-13
> **samjh said:**
> IMHO, they should just dump the IEC prefixes and go with the old IEEE standard of having context-dependant meanings for SI prefixes.

IMO that's the exact problem - The meaning of the decimal prefixes changes depending on the context its used e.g. MB means 1048576 bytes when talking about RAM, but 1000000 bytes when talking about hard drive space. It just seems silly to have one set of symbols to mean two different things, when another set of symbols can easily be adopted.

---

### Post by rsambuca on 2007-11-13
I agree it is kinda silly, but does it really matter?

---

### Post by reacocard on 2007-11-13
> **NovaAesa said:**
> That sounds like a pretty bad reason to be using the technically wrong notation. Sure, people don't like changing habits, but habits are going to have to be changed sooner or later (or at least I hope they do). I'm sure there are lots of people that have changed their OS 'habit' from Windows to Linux, but I'd bet most of them are thankful for that change in habit now. To me, using the wrong prefixes just seems unprofessional. It feels a bit like when you see someone write "your" instead of "you're". Sure you can still figure out what they really mean, but it would just be nicer if they would use the right term.


I agree, but people are not rational beings and resist change. it's like inertia really, you need a big push to overcome the current motion. (or a lot of little pushes)

> Yes I had noticed that. Yay for the Deluge team :) . I suppose in reality it's not a Ubuntu specific thing really. I would think that it would be the GNOME people that would have to fix it.

Exactly, so perhaps the best thing to do if to file bugs against the offending applications. It's a simple change and it makes sense, so I see no reason why it wouldn't be implemented in most cases.

---

### Post by macogw on 2007-11-13
> **reacocard said:**
> traditionally yes, however that is technically incorrect, kibibyte is correct. There was actually a discussion about this on ubuntu-devel some months ago, but I don't recall whether anything was actually decided.
kibibyte is only correct because the hard drive manufacturers want to keep lying to people, and the IEEE decided they value them and letting them do whatever the hell they want more than they value The Way It Is Done.  So, instead of the hard drive manufacturers having to admit that there are NOT a full 20GB on that hard drive, just 18, they get to keep lying and everyone who actually knows about computers has to go start using new made-up words.  What they SHOULD have done was taken the hard drive manufacturers to task for lying about drive capacities and forced THEM to either start showing the proper capacities on the label or use some new, stupid, made-up word

---

### Post by samjh on 2007-11-13
> **macogw said:**
>  What they SHOULD have done was taken the hard drive manufacturers to task for lying about drive capacities and forced THEM to either start showing the proper capacities on the label

That's just it.

A kilobyte is 1024 bytes according to the old ANSI/IEEE standard.  Manufacturers can either be honest, or they can be screwed by false-advertising laws if they don't fall in line.  I just hope there are judges bold enough to put their hammer down on the issue: computer memory capacities are to be properly expressed.

On a related note, the fact that the IT industry is so keen to prefix "kilo" with a K is something that irks me; K is Kelvin, not kilo!  Kilo is k!.  Further, byte is B, bit is b.  Kilobyte should be kB, and kilobits should be kb!

I still say to get rid of pseudo-standards: standards that are written on paper but not significantly used. :)

---

### Post by conehead77 on 2007-11-13
> **NovaAesa said:**
> IMO that's the exact problem - The meaning of the decimal prefixes changes depending on the context its used e.g. MB means 1048576 bytes when talking about RAM, but 1000000 bytes when talking about hard drive space. It just seems silly to have one set of symbols to mean two different things, when another set of symbols can easily be adopted.

So i have not 1MB of RAM but 1MiB? Like Migabyte...? Why didnt they say MeB? Seems like the standardization made a mistake here :)

---

### Post by NovaAesa on 2007-11-14
> **samjh said:**
> 
On a related note, the fact that the IT industry is so keen to prefix "kilo" with a K is something that irks me; K is Kelvin, not kilo!  Kilo is k!.


Yes, I've noticed that as well. It goes along with the same idea that the same symbol shouldn't be used to mean two different things depending on their context. Even if an uppercase K is used in computing, we all know that it implies kilo (and not Kelvin) because of the context. Even though people still get the same message, it's the improper way of doing things. It should be a lowercase k. It's the same thing with binary and decimal prefixes. When a hard drive manufacturer markets their drive as being 80 GB, they mean that it can hold 80 billion bytes of data because G is the symbol for giga and giga means billion. The inconsistency lies at the software end (such as when an OS reports the 80GB hard drive as about 76GB). G means billion in every field of life except for in computers, so why don't we just agree with the rest of the world to make things consistent?

---

### Post by tehet on 2007-11-14
> **NovaAesa said:**
> G means billion in every field of life except for in computers, so why don't we just agree with the rest of the world to make things consistent?
Because a computer is a binary environment. The decimal system isn't relevant in a technical sense.

---

### Post by BDNiner on 2007-11-14
With Hard Disks an 80GB HD does hold 80GB of data. You lose the extra space when the disk is formatted and a file system put on it. That is what takes up the other 4 GB or so. If you wanted 80 GB of useable space then the HD would have to be around 85 GB large. If the end user was given access to that extra space then there would be a lot of other issues with data loss.

---

### Post by Endolith on 2008-04-13
These units are already used correctly in many Ubuntu applications (either IEC prefixes for powers of 2 or SI prefixes for powers of 10).

Look in Network Tools or Partition Manager, for instance.  Or type about:cache in Firefox.  There are just a few hold outs who think it's "not necessary" to switch over, despite the massive user confusion it causes:

[http://ubuntuforums.org/showthread.php?t=101855#10](http://ubuntuforums.org/showthread.php?t=101855#10)
[https://bugs.launchpad.net/ubuntu/+source/nautilus-cd-burner/+bug/14422](https://bugs.launchpad.net/ubuntu/+source/nautilus-cd-burner/+bug/14422)
[http://ubuntuforums.org/showthread.php?t=300184](http://ubuntuforums.org/showthread.php?t=300184)
[http://ubuntuforums.org/showthread.php?t=49698](http://ubuntuforums.org/showthread.php?t=49698)
[http://ubuntuforums.org/showthread.php?t=322529#2](http://ubuntuforums.org/showthread.php?t=322529#2)
[http://ubuntuforums.org/showthread.php?t=420126](http://ubuntuforums.org/showthread.php?t=420126)

Using the standard units is the right way to go.  The only thing in computers that is naturally powers of 2 is the memory, and there are proper units for that now.  Everything else has always been measured in powers of 10, like disk space, bandwidth, or DVD size.  Use the right units for the job, devs.  It's about time we cleaned up this mess.

[[IMG]http://brainstorm.ubuntu.com/idea/4114/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/4114/)

---

### Post by p_quarles on 2008-04-13
Hmm. Thread necromancy to drum up support for your brainstorm poll? Seems like a slight breach of netiquette to me. Thread closed. 

In any case, here's the real deal:
[img]http://imgs.xkcd.com/comics/kilobyte.png[/img]

---

