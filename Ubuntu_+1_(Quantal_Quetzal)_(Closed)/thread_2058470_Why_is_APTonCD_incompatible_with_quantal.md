---
title: "Why is APTonCD incompatible with quantal?"
date: 2012-09-15
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by epikvision on 2012-09-15
I recently found out about the app [APTonCD]("http://aptoncd.sourceforge.net/") and became hugely excited!  It could take the packages of my choice in my precise desktop and pack them all in one cd, like my "essentials" installation media. I installed this app and placed my favorite packages into a cd.  

Next, I wanted to insert the cd on my laptop running Ubuntu quantal daily build. I navigated to the APTonCd page on the software center, and to my dismay, I realized that it was incompatible with quantal. 

Why can some apps, like this one, be incompatible in quantal? Thanks.

---

### Post by oldos2er on 2012-09-15
Moved to Ubuntu +1 (Quantal Quetzal).

---

### Post by cariboo on 2012-09-15
I haven't play with aptoncd for years, but it looks like it is essentially broken, from the terminal output it looks like it depends on HAL, which is no longer used.

The way it is supposed to work is, that once you've made the iso, and burned it to CD/DVD, the restore function is supposed to extract the packages from the CD and copy them to /var/cache/archives, where you can then use synaptic, or gdebi to install the packages. 

Seeing as the application is broken, you could still manually extract the packages from the CD and copy them to the archive directory, then use the terminal or gebi to isntall them.

It looks to me that aptoncd isn't compatible with the software center, more than it isn't compatible with Quantal.

I'd also suggest you create a bug report for aptoncd. To do so, press Alt-F2 and type:

```
ubuntu-bug aptoncd
```

**Note**: You need a [Launchpad]("https://launchpad.net/") account to report bugs.

---

### Post by epikvision on 2012-09-15
Alright, it's good that I have an account.  

I report bugs on quite a normal basis, but this brings up another issue.  

Whenever I report bugs, I don't really get much activity around developers.  How can I get developers' attention?  Or more specifically, how can I determine what lists to merge or subscribe?

---

### Post by tienlbhoc on 2012-09-15
because quantal is 12.10 but package in aptoncd is for 12.04. I think that ;)

---

### Post by cariboo on 2012-09-16
> **epikvision said:**
> Alright, it's good that I have an account.  

I report bugs on quite a normal basis, but this brings up another issue.  

Whenever I report bugs, I don't really get much activity around developers.  How can I get developers' attention?  Or more specifically, how can I determine what lists to merge or subscribe?

Make sure you supply as much relevant information as possible. It also depends on a bit of luck sometimes :-D, 

The last bug I reported, was picked up right away, and a fix has been released, it took about 10 days, but I have to admit I did a bit of pushing here and there to get things done.

---

### Post by Pinoy Tux on 2012-09-16
> **tienlbhoc said:**
> because quantal is 12.10 but package in aptoncd is for 12.04.
+1 on this.  AFAIK, you use AptOnCD to transfer your apt cache to another machine running the same version of Ubuntu.  The purpose of this is so you don't have to download the same packages anymore, especially if you're deploying updates to a lot of computers and your connectivity resource is limited.

So, it's not a matter of AptOnCD being incompatible, it's more like you're trying to transfer packages that are not meant for QQ.

---

### Post by cariboo on 2012-09-16
For the two of you that said the aptoncd package is for Precise, have a look [here]("http://packages.ubuntu.com/search?keywords=aptoncd&searchon=names&suite=all&section=all"). The package is the same for both versions.

---

### Post by stinkeye on 2012-09-16
> **cariboo907 said:**
> For the two of you that said the aptoncd package is for Precise, have a look [here]("http://packages.ubuntu.com/search?keywords=aptoncd&searchon=names&suite=all&section=all"). The package is the same for both versions.
Yes, but isn't he using aptoncd to try and install Precise packages in Quantal?

---

### Post by Pinoy Tux on 2012-09-16
> **cariboo907 said:**
> For the two of you that said the aptoncd package is for Precise, have a look here. The package is the same for both versions.

By packages, I meant the .deb files in the OP's PP apt cache folder, not AptOnCD *itself*.  I re-read the original post and this caught my attention:

> **epikvision said:**
> I navigated to the **APTonCd page on the software center**, and to my dismay, I realized that **it was incompatible with quantal**.
The way I understood from reading the above, it's telling me that the OP wasn't able to install AptOnCD on his/her QQ and Software Center is saying that it's incompatible.  But looking again at the attached screen shot, it seems to be an error message from AptOnCD itself and not Software Center?  If the screen shot is indeed from AptOnCD then AptOnCD *is* installed on the OP's QQ.

As stinkeye said (and I mentioned this in my previous post),

> **stinkeye said:**
> ...but isn't he using aptoncd to try and **install Precise packages in Quantal**?

which is a no-no AFAIK.  I may be wrong, but is this even safe/recommended in the first place?   Maybe the OP could clarify this further.

---

