---
title: "Cogent Co and Level 3"
date: 2005-10-06
forum: The Cafe
---

### Post by lyam_kaskade on 2005-10-06
Article on Slashdot
[Internet Partitioning]("http://ask.slashdot.org/article.pl?sid=05/10/05/2247207&tid=95&tid=187&tid=4")

I haven't seen people calling much attention to this, but it seems pretty important to me.
Basically, it means that for an indefinite period of time, I cannot access ubuntulinux.org, or update synaptic. 
I can't even download the Breezy Release Candidate.
And I'm certain I'm not the only one that can be having this problem. 
This troubles me greatly...

---

### Post by DJ_Max on 2005-10-06
This could mean the downfall of Level3 and/or Cogent. Level3 has sent notification of depeering to Cogent, Saavis, Wiltel, XO and a few others. So far, Level3 is only planning on keeping Tier1 bandwidth providers (MCI, AT&T, Sprint, Level(3), Qwest, TWTC and GBLX).  Level 3 terminated its peering with Cogent without cause (as permitted under its peering agreement with Cogent).

Now, from a business standpoint, I really don't see why Level3 decided to do this. Any BGP speaking host simply will not receive routes VIA Cogent for Level3. But, *many Level 3 customers can still exchange traffic with Cogent customers IF the Level 3 customer is multi-homed, (i.e. it also has a connection to Cogent or to one of the many other networks with which Cogent has a peering relationship).*  This is hurting a lot of people. Many internet providers now have to contact their line providers and ask for different connections. But right now Cogent is sore, and trying to make bank of of this fiasco buy making deals with Level3 customers to switch to them.

Just to add, Cogent buys transit from Verio, who in turn deals with Level3. In theory, if Cogent wanted to restore service, they could pay Verio to give them transit to L3.

And you are right, this is very important. The internet has bee greatly effected, as the same in your case.

---

### Post by drogoh on 2005-10-06
But isn't the Internet designed to work around these type problems?  Sure, it affects the single-homed people but I'm pretty sure none of these tier 1 providers actually charge each other money...

I could be wrong, but that's just what a little bird told me.

p.s. Slashdot is evil.

---

### Post by DJ_Max on 2005-10-06
[QUOTE=drogoh]But isn't the Internet designed to work around these type problems?  Sure, it affects the single-homed people but I'm pretty sure none of these tier 1 providers actually charge each other money...

I could be wrong, but that's just what a little bird told me.

p.s. Slashdot is evil.[/QUOTE]
Yes, hence one of the points of a BGP'd network. But you will still see problems connecting to certain sites, mainly single-homed Cogent sites. RoadRunner DSL users have been hit the hardest.

Read a bit more into it
[http://www.webhostingtalk.com/showthread.php?s=&threadid=449728](http://www.webhostingtalk.com/showthread.php?s=&threadid=449728)
[http://www.theregister.co.uk/2005/10/06/level3_cogent](http://www.theregister.co.uk/2005/10/06/level3_cogent)

---

### Post by snarkout on 2005-10-06
The internet needs a LERG.

---

### Post by smedstadc on 2005-10-07
I'm also affected by this... I can no longer update Ubuntu or use apt. Can anyone suggest a fix for my sources.lst? As I can't access any of the us repos. :(

---

### Post by DJ_Max on 2005-10-07
You didn't try all of the US repo's, did you? There are a lot of mirrors.
[https://wiki.ubuntu.com/Archive](https://wiki.ubuntu.com/Archive)

You want the 'Package Archive'

---

### Post by lyam_kaskade on 2005-10-07
[QUOTE="DJ_MAX"]You didn't try all of the US repo's, did you? There are a lot of mirrors.
[https://wiki.ubuntu.com/Archive](https://wiki.ubuntu.com/Archive)

You want the 'Package Archive'[/QUOTE]

Heh...the wiki was another site I couldn't access.
But fortunately, the issue seems to have been resolved for the moment, Level 3 caved.

---

### Post by DJ_Max on 2005-10-08
Thats because I'm an idiot, if the wiki in the same DC as the Ubuntu archives, why did I think you can access thw wiki. :confused:

---

