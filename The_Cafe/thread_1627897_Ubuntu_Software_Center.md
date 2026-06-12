---
title: "Ubuntu Software Center"
date: 2010-11-21
forum: The Cafe
---

### Post by racie on 2010-11-21
So... is the Ubuntu team ever going to implement a rating system to the Software Center (similar to Linux Mint)?  

I could have sworn that there used to be something like this a while ago, but I could be making that up.  It's really a useful and I don't see why there isn't one already.

---

### Post by ubuntu27 on 2010-11-22
We used to have a rating system long ago before we had Ubuntu Software Center. Back then, it was another application called "Add/Remove Applications."

On Add/Remove Applications, it showed yellow stars representing popularity of a given package.

---

### Post by ikt on 2010-11-22
Android and the iphone have a software rating/comment system as does download.com for windows software, I see no reason why we shouldn't have one as well.

---

### Post by earthpigg on 2010-11-22
I'm strongly in favor.

---

### Post by racie on 2010-11-22
> **ubuntu27 said:**
> We used to have a rating system long ago before we had Ubuntu Software Center. Back then, it was another application called "Add/Remove Applications."

On Add/Remove Applications, it showed yellow stars representing popularity of a given package.
Ah ha!  I knew I wasn't crazy!  I wonder why it was removed when it got switched to the Ubuntu Software Center.

---

### Post by czr114 on 2010-11-22
Yes, provided it can be done entirely using methods of opt-in data collection or existing counts on hits in the repo logs, and not by collecting or incorporating any software statistics from a client machine. (some popularity algos need a bit too much)

I like what Mozilla has done with their add-ons portal. Sorting by download count calls attention to what is most broadly used (not that with the most loyal userbase), and a rating and selection of comments gives a general idea of whether the software delivers as promised, and if not, what problems users are actually complaining about.

---

### Post by simpleblue on 2010-11-22
Many newbies will download apps from the Software Center that might not be up to par. With the rating system they can see the best of the apps by simply clicking 'highest rated.' The result is a much better first impression.

---

### Post by Paqman on 2010-11-22
> **czr114 said:**
> Yes, provided it can be done entirely using methods of opt-in data collection or existing counts on hits in the repo logs, and not by collecting or incorporating any software statistics from a client machine. (some popularity algos need a bit too much)


The old system was to use popularity-contest, which is opt-in. I've always thought making it opt-in pretty much invalidated the data, but that's just me.

Popcon tracks what is installed and how much it actually gets used, and is completely automated.

---

### Post by Johnsie on 2010-11-22
It needs to have user comments so that users can post a short summary of what they think of the app (if it works etc). Similar to Android marketplace or amazon. 

That will also help developers get some feedback on what they need to improve.

---

### Post by Naiki Muliaina on 2010-11-22
Aye, used to like the old star system back in the old add / remove. I dont know what Mints one looks like.

---

### Post by Lucradia on 2010-11-22
Yes, but I can't wait for trolls to rate random software to just have it have a low rating.

---

### Post by wkhasintha on 2010-11-22
Yes, but it must be a weighted rating system (like in imdb). to overcome the issue [Lucradia]("http://ubuntuforums.org/member.php?u=1094376") bro stated in the above post..

---

### Post by czr114 on 2010-11-22
> **Paqman said:**
> The old system was to use popularity-contest, which is opt-in. I've always thought making it opt-in pretty much invalidated the data, but that's just me.

Popcon tracks what is installed and how much it actually gets used, and is completely automated.

It has to be either opt-in or limited solely to server statistics and submitted reviews.

Profiling peoples' software usage without informed consent is a hideous privacy practice. There's a lot of interesting things that can be done in the way of popularity ranking, usage ranking, similar recommendations, etc., all built off of how people interact with software, how often, how long it stays installed, and what else they use, but it has to be done in a way which respects user privacy and transmits no data except in cases where people make an informed decision to be part of the monitoring.

Some people consider that a feature; others consider it spyware. We can please both camps with opt-in, and avoid going down the road of those commercial devs to whom a privacy policy is a document written by lawyers, for lawyers, and never used in the real world.

Opt-in will skew the statistics a little bit, but that's the best that can be done short of taking an anti-privacy panoptic view of every Ubuntu desktop.

---

### Post by bash on 2010-11-22
> **racie said:**
> So... is the Ubuntu team ever going to implement a rating system to the Software Center (similar to Linux Mint)? 

Yea for the next version of Ubuntu. Two minutes of searching would have answered your question:

[http://www.omgubuntu.co.uk/2010/10/ubuntu-software-center-ratings-and-reviews-to-come-by-christmas/](http://www.omgubuntu.co.uk/2010/10/ubuntu-software-center-ratings-and-reviews-to-come-by-christmas/)
[https://wiki.ubuntu.com/SoftwareCenter/RatingsAndReviews](https://wiki.ubuntu.com/SoftwareCenter/RatingsAndReviews)
[https://blueprints.launchpad.net/ubuntu/+spec/packageselection-foundations-n-ratings-and-reviews-in-software-center](https://blueprints.launchpad.net/ubuntu/+spec/packageselection-foundations-n-ratings-and-reviews-in-software-center)

---

### Post by Dustin2128 on 2010-11-22
> **ubuntu27 said:**
> We used to have a rating system long ago before we had Ubuntu Software Center. Back then, it was another application called "Add/Remove Applications."

On Add/Remove Applications, it showed yellow stars representing popularity of a given package.
I thought I remembered something like that too. Anyway, I think it would make software packages vulnerable to groupthink, but I wouldn't mind... say.. a comment system.

---

### Post by ubuntu27 on 2010-11-22
The "Add/Remove Applications" rating system was based on statistics gathered by which packages the users downloaded the most. These statistics were only gathered from the users who opt-in or agreed to submit those data.

You can opt-in by 

If you are using Ubuntu (Gnome):
opening Synaptic Package Manager---> Software Sources--->Statistics  ---> Check "Submit Statistical Information"

If you are using Kubuntu (KDE):
KPackageKit-------> Settings------>Edit Origins------->Statistics----> Check "Submit Statistical information"


I am have it enabled since I consider this statics to be benevolent, and I want to be useful.

---

### Post by Paqman on 2010-11-22
> **ubuntu27 said:**
> The "Add/Remove Applications" rating system was based on statistics gathered by which packages the users downloaded the most.

Popcon actually goes a little bit further. From the man page:

> The  popularity-contest  command  gathers information about Debian packages installed on the system, and prints the name of the most recently used executable program in that package as well as its  last-accessed  time  (atime)  and last-attribute-changed time (ctime) to stdout.

So it actually tracks how much a package is used, as well as how many people have it installed. You can see the data at [http://popcon.debian.org/](http://popcon.debian.org/)

---

