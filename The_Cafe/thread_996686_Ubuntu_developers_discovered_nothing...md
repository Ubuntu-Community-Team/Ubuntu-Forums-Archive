---
title: "Ubuntu developers discovered nothing.."
date: 2008-11-29
forum: The Cafe
---

### Post by picturefreedom on 2008-11-29
and so lets discuss some controversial topic,


[http://beranger.org/index.php?page=diary&2008/11/28/20/34/04-ubuntu-developers-discovered-exa]("http://beranger.org/index.php?page=diary&2008/11/28/20/34/04-ubuntu-developers-discovered-exa")

do you agree with the blog?  or this just really an overblown press by softpedia with ubuntu no control over it?

in addition , the USN haven't disclosed why it took them a month before the update? if what the blog said is true.

---

### Post by bobbocanfly on 2008-11-29
The author of that post obviously does not understand how Ubuntu development works. We inherit 99% of things from Debian, which means that we often wait for them to fix bugs, then we pull the new packages down into our repos. This means that work isnt being duplicated and the time overhead is normally less than a week. 

True, in some of the examples in the blog post, Ubuntu gets the fixes in as much as a month after. This could be down to any number of reasons. Firstly, when a bug is not reported against a package on Launchpad, we wont be able to fix it as we wont know it exists. As you can imagine, it is difficult to fix bugs you have not been told about. 

Instead of writing that post, the Author could have actually helped out, gone to the latest CVE list and filed some bugs in Ubuntu. If they already exist, add a comment to the bug saying "This also affects me, running Ubuntu $VERSION_NAME".

Also, it looks like what we did was lump together a whole pile of patches from the last couple of months then release them in one big go. This makes quite a lot of sense right now (from the developers perspective): At the start of the release cycle, the build servers are under 100% use. The kernel builds take *ages*, which means that development work on Jaunty slows down. If the kernel was released with every patch in that blog post, it would have to be built 5 times, tieing up more build machines over more time. Not really great for Jaunty development. Releasing 5 new kernel updates would mean testing would need to be done for each one and, tbh, we just dont have enough testers to make that feasible right now. 

Final point. Kernel updates are about the biggest (Megabytes wise) you get with Ubuntu. If one came out every few days, poor person x on their dialup connection is going to be pretty annoyed.

---

### Post by mihai.ile on 2008-11-29
oh my this again... ubuntu devs don't have to contribute to kernel, they don't send many patches so what? Kernel is not everything you know...
For example if it wasn't for Ubuntu the HAL team wouldn't get my 2 patches for new sony mp3 players devices. This is a great help to the HAL, but who counts it? Nobody. All they care is measure how many bugs got found/fixed in kernel...

Ridiculous...

---

### Post by fatality_uk on 2008-11-29
"THE WORLD IS GOING TO END AND ALL LIFE WIPED OUT"
No wait, that might just be an opinio and so I need to treat it with a little self discipline!

---

### Post by Polygon on 2008-11-29
hey bobbo, apparently you have a friend over at that blog: (from the blog again)

> 
 «The author of that post obviously does not understand how Ubuntu development works. We inherit 99% of things from Debian, which means that we often wait for them to fix bugs, then we pull the new packages down into our repos. This means that work isn't being duplicated and the time overhead is normally less than a week.» &#8212; This guy is completely idiot. Ubuntu releases twice a year, Debian releases very rarely, hence the kernel versions between the two distros don't match! Then, Ubuntu's kernel is very different from Debian's (it usually has a lot of ugly patches). Thirdly, Ubuntu's LTS editions are supposed to be used on servers, therefore the updates need to be provided in a timely manner.

 «Firstly, when a bug is not reported against a package on Launchpad, we won't be able to fix it as we won't know it exists. As you can imagine, it is difficult to fix bugs you have not been told about.» &#8212; Wow. All the other distros knew... Ubuntu didn't!

 «At the start of the release cycle, the build servers are under 100% use. The kernel builds take *ages*, which means that development work on Jaunty slows down. If the kernel was released with every patch in that blog post, it would have to be built 5 times, tieing up more build machines over more time. Not really great for Jaunty development.» &#8212; Screw the &#8220;Jaunty development&#8221;, you ********s! All you can think of is &#8220;let's build the next collection of bugs, no matter what else should we do&#8221;. Oh, and if &#8220;the kernel builds take ages&#8221;, then they really need better hardware (Mark, don't be such a cheap guy).

Ubuntu is making me puke. 


dont we pull from debian sid anyway? (unstable)....so the packages there get updated more then just once every blue moon when debian whatever gets released?

and im sure there is some nice rebuttal to all of this but i dont know much about it, im sure an ubuntu dev could set all of this straight

---

### Post by SqdnGuns on 2008-11-30
> **picturefreedom said:**
> and so lets discuss some controversial topic,


[http://beranger.org/index.php?page=diary&2008/11/28/20/34/04-ubuntu-developers-discovered-exa](http://beranger.org/index.php?page=diary&2008/11/28/20/34/04-ubuntu-developers-discovered-exa)

do you agree with the blog?  or this just really an overblown press by softpedia with ubuntu no control over it?

in addition , the USN haven't disclosed why it took them a month before the update? if what the blog said is true.

He does do a lot of bitching and complaining, I read his blog all the time for entertainment but in matters like this, he is pretty right on.

---

### Post by baruch60610 on 2008-11-30
This article seems excessively harsh.  He criticizes Ubuntu developers for things they never claimed they do, nor are they reasonably expected to do them.

In a comment, someone claimed that the Ubuntu folks declared themselves "Masters of the Universe".  I haven't seen any such thing.  What I *have* seen are many grateful Ubuntu users who perhaps put the developers on a pedestal - but that's not the developers' fault.

I don't think this article deserves more attention.

Update: Thanks to mentallaxative for setting me straight.  They do claim to be MOTU, after all...

Even so, I don't feel the article is meritorious.

---

### Post by mentallaxative on 2008-11-30
> **baruch60610 said:**
> 
In a comment, someone claimed that the Ubuntu folks declared themselves "Masters of the Universe".  I haven't seen any such thing.  What I *have* seen are many grateful Ubuntu users who perhaps put the developers on a pedestal - but that's not the developers' fault.


You're not aware of what the term means: [https://wiki.kubuntu.org/MOTU](https://wiki.kubuntu.org/MOTU)

---

### Post by wirepuller134 on 2008-11-30
I wrote out a long winded reply for a comment on their blog, But in the end decided it wasn't worth it. The 5 minutes spent reading the blog is 5 minutes I will never get back of my life, what a waste of my time.  I don't remember anyone twisting my arm and claiming Ubuntu was the best at anything.

---

### Post by quinnten83 on 2008-11-30
I don't get all this hate for Ubuntu.
Sure we are not perfect, but we are one of the larger distros.
That is why we get so much attention. And for the end user we are one of the easiest Linux distros to install. Sure we didn't get the patches in a timely fashion, but really how many crackers used the vulnerability anyway?
The author seems overly spiteful of Ubuntu anyway, so you have to wonder how seriously you are supposed to take this.

---

### Post by Closed_Port on 2008-11-30
I don't know how you could really argue with this blog post. The author is simply right. The facts support what he says. 

While you may disagree with the author, I don't think being critical about Ubuntu taking a long time to fix these vulnerabilities is something that should be discouraged. On the contrary, I think that really is the kind of valid criticism that every distro needs.

And his other points about the stupid softpedia article are also valid. It's simply a fact that Ubuntu devs did not discover these vulnerabilities and it's a fact that they took more than a day to fix them. 

Now you might of course claim that the article is irrelevant, however go over to digg ([http://digg.com/linux_unix/Newly_Discovered_Kernel_Vulnerabilities_Affect_All_Ubuntu_Us](http://digg.com/linux_unix/Newly_Discovered_Kernel_Vulnerabilities_Affect_All_Ubuntu_Us)) and see ubuntuusers virtually highfiving each other for finding the vulnerabilities and fixing them in a day. Simply embarrassing.

And don't even get me started about the answer provided here by an ubuntu member. Ouch...

---

### Post by wirepuller134 on 2008-11-30
Unless I am paying for it, I am not going to openly blame them for not fixing the vulnerability.  I appreciate the fact they take their time and effort to produce this project. Bottom line, anyone whom cared enough could learn and find and fix the bugs/holes themselves.  If someone doesn't like the way they update the kernel/apps nothing is stopping them from using a different distribution.  I won't wast my time reading any more of his blogs, He can be as "controversial has he wishes".
    If it becomes an issue to me, Fedora is just a hard drive swap away.  Yes we actually keep hard drives loaded and updated ready to install, if we do have a hard drive failure.  All data and user profiles are stored on a remote server.

---

### Post by bobbocanfly on 2008-11-30
That guy has to be taking the piss, surely.

> «The author of that post obviously does not understand how Ubuntu development works. We inherit 99% of things from Debian, which means that we often wait for them to fix bugs, then we pull the new packages down into our repos. This means that work isn't being duplicated and the time overhead is normally less than a week.» &#8212; This guy is completely idiot. Ubuntu releases twice a year, Debian releases very rarely, hence the kernel versions between the two distros don't match! Then, Ubuntu's kernel is very different from Debian's (it usually has a lot of ugly patches). Thirdly, Ubuntu's LTS editions are supposed to be used on servers, therefore the updates need to be provided in a timely manner.

We marge/sync every six months with Debian sid and backport security fixes whenever we deem it necessary. If you do not like this, use another distro.

> «Firstly, when a bug is not reported against a package on Launchpad, we won't be able to fix it as we won't know it exists. As you can imagine, it is difficult to fix bugs you have not been told about.» &#8212; Wow. All the other distros knew... Ubuntu didn't!

Exactly my point, from what I can find on Launchpad, we didn't know. If you think we should regularly be taking bugs off other distros bug trackers, you are welcome to setup a team that does this. 

> «At the start of the release cycle, the build servers are under 100% use. The kernel builds take *ages*, which means that development work on Jaunty slows down. If the kernel was released with every patch in that blog post, it would have to be built 5 times, tieing up more build machines over more time. Not really great for Jaunty development.» &#8212; Screw the &#8220;Jaunty development&#8221;, you ********s! All you can think of is &#8220;let's build the next collection of bugs, no matter what else should we do&#8221;. Oh, and if &#8220;the kernel builds take ages&#8221;, then they really need better hardware (Mark, don't be such a cheap guy).

So if we just stagnate, do absolutely nothing even vaguely innovative and just spend the next 50 years fixing all the bugs on Launchpad, that is your idea of a good distro? Ubuntu is not for you.

> Ubuntu is making me puke.

[http://fedoraproject.org/](http://fedoraproject.org/)
[http://www.debian.org/](http://www.debian.org/)
[http://en.opensuse.org/Welcome_to_openSUSE.org](http://en.opensuse.org/Welcome_to_openSUSE.org)
[http://www.openbsd.org/](http://www.openbsd.org/) (You'll like openBSD, just 2 security holes in 10 years)

Good luck with your new distro.

I'm now going to stop posting in this thread, because it is just going to piss me off even further and the author is obviously showing no intent to try to help "fix" these problems, and would prefer to just moan about it.

---

### Post by Closed_Port on 2008-11-30
Oh yes, finally, the use an other distro excuse...

Especially funny as it seems quite obvious that the author of the blog is not using ubuntu.

Needless to add that not one of the points of the blog author has been invalidated by telling him not to run a distro he's probably not running in the first place.

Don't get me wrong, I really like ubuntu, otherwise I wouldn't use it, but the inability of many ubuntu users to take any kind of criticism of their beloved distro never ceases to amaze me.

Edit:
One finally note, as this kind of aggressive ignorance simply can't be ingnored:
> Exactly my point, from what I can find on Launchpad, we didn't know. If you think we should regularly be taking bugs off other distros bug trackers, you are welcome to setup a team that does this. 
For God's sake, there are upstream lists that developers of distros should and do subscribe to and the vulnerabilities that were fixed were publicly know, not burried in some bugzilla of an other distro. How do you think the ubuntu devs knew about these problems?
Do you even have the slightest clue about what you are talking?

And about the bugs not being on launchpad: How about you use the CVE tracker on launchpad that was designed to, gosh, track CVEs so that all thos nasty kernel bugs are automatically reported on launchpad.
[https://bugs.launchpad.net/bugs/cve/](https://bugs.launchpad.net/bugs/cve/)
> Launchpad includes full support for the CVE framework. We update the Launchpad CVE database daily to ensure it includes details of all known vulnerabilities.

---

### Post by Polygon on 2008-11-30
yeah, the ubuntu devs should subscribe to every upstream mailing list for every single program in the repos. That is just not manageable.

and i would trust bobbo, a contributor to universe, over someone who just registered and has 3 posts

---

### Post by Closed_Port on 2008-11-30
> **Polygon said:**
> yeah, the ubuntu devs should subscribe to every upstream mailing list for every single program in the repos. That is just not manageable.

As we all know, the kernel is just a program like any other, isn't it...
But to answer your question, yes, a maintainer of a program should very well subscribe to the bug mailinglist of this program. Imagine that.

And btw. as I already posted, they even automated getting kernel bugs delivered to launchpad. Do you have an issue with that? Do you think ubuntu devs who maintain the kernel should not know if there are any security vulnerabilites? What exactly are you trying to tell us?

> **Polygon said:**
> 
and i would trust bobbo, a contributor to universe, over someone who just registered and has 3 posts
You don't have to trust me, you can check out the facts yourself. Were the kernel vulnerablities public? Just look the CVE numbers up on the ubuntu mailing list advisory and see for yourself.
And while you are at it, simply use google to see how kernel vulnerabilities are handled, how distros cooperate, etc.

Are CVEs autmatically delivered to launchpad? Just follow the link I posted and see for yourself.

So again, what exactly is your point?

---

### Post by Delever on 2008-11-30
Someone throwing **should**s around in their blag. Imagine that.

---

### Post by picturefreedom on 2008-11-30
boy! we have a bit of some lively discussion here have we..

upon reflection..

some points..

1. ubuntu could not be blamed for what others have said, sofpedia sure put the wrong credit to ubuntu devs. 

2. I must agree, need to put more effiecincy on the whole bug management.

---

### Post by saulgoode on 2008-11-30
> **picturefreedom said:**
> 1. ubuntu could not be blamed for what others have said, sofpedia sure put the wrong credit to ubuntu devs. 

FWIW, Softpedia has updated the wording to "the Ubuntu developers **announced** the availability of a major security update ..."

---

### Post by bruce89 on 2008-11-30
I would be very annoyed if someone else took the credit for work that I had done, so I can understand the annoyance. In the eyes of too many, Linux distro == Ubuntu.

Also, Ubuntu does relatively little upstream work (note the use of the word relatively) compared to similarly-sized distributions. Of course, a lot of this is down to the small number of developers. Also, a lot of work that Ubuntu does directly is only for Ubuntu.

---

