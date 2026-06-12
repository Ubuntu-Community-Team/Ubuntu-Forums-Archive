---
title: "Chrome Browser dep issue"
date: 2013-04-19
forum: Ubuntu Development Version
---

### Post by carl4926 on 2013-04-19
Chrome will not install in +1 ATM
libudev0 not satisfiable

---

### Post by zika on 2013-04-19
> **carl4926 said:**
> Chrome will not install in +1 ATM
libudev0 not satisfiable
[URL="http://ubuntuforums.org/showthread.php?t=2136669"]http://ubuntuforums.org/showthread.php?t=2136669
[/URL][http://ubuntuforums.org/showthread.php?t=2132483&highlight=libudev0](http://ubuntuforums.org/showthread.php?t=2132483&highlight=libudev0)
[http://ubuntuforums.org/showthread.php?t=2133603&highlight=libudev0](http://ubuntuforums.org/showthread.php?t=2133603&highlight=libudev0)

---

### Post by craig10x on 2013-04-19
Carl, this was posted on several other threads here...here is the article with the simple solution...install the dependency first, then install chrome...
This is because of the change, and Google will be correcting it on their end (fix is in Chrome Development so should filter down to beta and stable versions soon)...
Meanwhile, follow the instructions to install it right now:
[http://www.webupd8.org/2013/04/fix-google-chrome-cant-be-installed-in.html#more](http://www.webupd8.org/2013/04/fix-google-chrome-cant-be-installed-in.html#more)

PS: i see Zika just gave you a few links, but go right to my article link for this...it explains what happened and gives you the links you need right there...

---

### Post by carl4926 on 2013-04-19
Thanks
Sorry I missed all those :oops:

---

### Post by craig10x on 2013-04-19
No problem, buddy..we were glad to be of help ;)

---

### Post by tdockery97 on 2013-04-19
I know it's not "mission critical" since it involves the installation of a package from an outside source, but it would be a nice gesture if the devs could put that dependency back in the 13.04 repositories.

---

### Post by vasa1 on 2013-04-19
> **craig10x said:**
> No problem, buddy..we were glad to be of help ;)

@craig10x, do you have a link to follow the progress of Google fixing the issue? I searched crbug.com for a bug but didn't find anything relevant :(

---

### Post by carl4926 on 2013-04-20
> **vasa1 said:**
>  follow the progress of Google fixing the issue?  
That was my thought too

---

### Post by craig10x on 2013-04-20
In that article that i linked him to, they mention about it being fix in the Chrome developer channel...seems that one of those that commented below the article (Ray) mentioned to the guy that wrote the article about the fix...i don't have the actual link for that...:redface:

But if that be the case (have no reason to doubt it) i would think they would get it down fairly quickly...just like when there was a recent problem with pepperflash, they got it corrected quickly in development and then moved it down to stable pretty fast...so i would not be too surprised if it appears in the next stable version you receive...

---

### Post by vasa1 on 2013-04-20
@craig10x, I found something and "starred" it: [Google Chrome can not install in Ubuntu 13.04]("https://code.google.com/p/chromium/issues/detail?id=226002")

---

### Post by craig10x on 2013-04-20
Excellent, vasa1....that appears to be the actual bug report to chromium project...he reported that it is now fixed in development, gives the version, and mentions it should filter down to beta and stable soon... :)

---

### Post by vasa1 on 2013-04-22
> **craig10x said:**
> Excellent, vasa1....that appears to be the actual bug report to chromium project...he reported that it is now fixed in development, gives the version, and mentions it should filter down to beta and stable soon... :)

Yes, this is the currently [last comment]("https://code.google.com/p/chromium/issues/detail?id=226002#c27"): 
> Hmm, we still need to merge the fix back to Chrome 26.x and 27.x.

---

### Post by carl4926 on 2013-04-27
Has anyone had any luck with Chrome yet?

---

### Post by VMC on 2013-05-09
I just found this thread after finding the "fix" as stated in post#3. This is for Ubuntu sauce 13.10.

So you need to get [LIBUDEV0]("http://www.webupd8.org/2013/04/fix-google-chrome-cant-be-installed-in.html") , then chrome-stable will install correctly on saucy.

---

### Post by craig10x on 2013-05-09
Yes, that dependency works for 13.10 now...just out of curiousity, i ran a daily build of 13.04 today and tried installing Chrome that way and it worked fine...
I'm not with you guys now in development (just running a 13.04 final as my system right now) but i just wanted to see how 13.10 was coming along and checked it out...

Eventually, the actual fix, which i understand is in Google Chrome development version, should filter down to the stable channel, and then this fix won't be needed anymore...
But that could be a while yet...

---

### Post by vasa1 on 2013-05-09
@craig10x, it has reached beta (v27) as well. I was hoping stable (v26) would get it but according to [this]("https://code.google.com/p/chromium/issues/detail?id=226002#c52") it won't. I'm holding out for stable because I have a lot riding on my profile (GDrive stuff).

---

### Post by craig10x on 2013-05-09
Yes, vasa1...thanks for the link, and i see you are quite right...what will happen is that when Chrome 27 (currently in beta) reaches stable channel, it will have the fix in it...they just won't be sending an update for our current stable 26...And the developer mentioned that they will keep an eye on new versions of ubuntu from now on, to ensure that they maintain compatibility...

I added my own comment of thanks to that bug thread, including a comment to some dope who was knocking ubuntu (of course)....i just thought i would include it here for everyone's amusement ;) 
Here it is:


@marcelo: You seem a bit confused...what you do not realize is that Mint 14, which is based on ubuntu that you love so much, is running on ubuntu 12.10 NOT ubuntu 13.04, so therefore it doesn't have the problem...once Mint 15 comes out you going to have the SAME PROBLEM as we are experiencing in Ubuntu 13.04 (which is not "crap" as you say...you are using mint and that is based on it...wake up!)...    Anyway, even though the fix won't be filtering down to Chrome Stable, i am glad to hear that once Chrome 27 hits the stable channel, the fix will be there and we won't have to take the extra step of adding the dependency...   Also, glad to hear that the Chrome developers will check for compatibility for new versions of Ubuntu from now on...which will help ubuntu and all the distros based on it (like marcelo's "precious Linux Mint")....thanks for the update!

---

