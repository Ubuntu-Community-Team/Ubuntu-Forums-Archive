---
title: "An example of what I find frustrating about Ubuntu"
date: 2008-04-23
forum: Testimonials &amp; Experiences
---

### Post by Eric Weir on 2008-04-23
Consider this a rant. First, I've been using K/Ubuntu almost exclusively the last eight months until recently, and I've been amazed by and appreciative of the support that's always available on the Ubuntu forums. 

That said, the system I was using had only a 10GB HD, and it got VERY slow. I installed a 40GB drive and did a fresh install of Kubuntu 7.10. Even though I'm a semi-experienced user now, I'm finding the process of getting the new installation configured more than a little frustrating. I decided that maybe I'd gotten myself in over my head with Kubuntu after all and downloaded Ubuntu 7.10 thinking I'd give it another chance -- to see if maybe the solutions it provides aren't better than what I'm having a difficult time coming up with on Kubuntu.

After downloading Ubuntu I ran md5sum, and after getting a hash, went to the Ubuntu website to locate the hash I needed to compare it with. Since there was no obvious link to the hash page on the home page or the download page, I did a search for UbuntuHashes. No result. Went to Google, did a search for UbuntuHashes, and there it was, "https://help.ubuntu.com/community/UbuntuHashes."

Google can find it on Ubuntu, but Ubuntu can't find it on Ubuntu. So many things you have to know and do just to be able to do the simplest thing, like copying a folder from one drive to another. So difficult to get the help needed -- the forums aside! -- to find out what needs to be done and how to do it. I find the documentation, but things that are clear and taken for granted by the author are not at all clear for me. The result is more questions that have to be answered to get the answer I'm looking for. It is easy, at least for me, to become overwhelmed, usually pretty quickly. 

I don't want to have someone hold my hand every baby step of the way. I don't want to spend 80 percent of my time figuring out how to do things on Ubuntu. I want to use Ubuntu to do other things, to do my actual work.

As I say, forgive the rant. Obviously I am frustrated.

Sincerely,

---

### Post by bodhi.zazen on 2008-04-23
First I am sorry you are so frustrated, it gets better. It takes time to learn a new OS, 4-6 months.

Second, the md5sum is not *that* hard to find. First it is listed on [Distrowatch](http://distrowatch.com/index.php?dataspan=4), right next to the iso ...

Second it is on the download page :

[http://releases.ubuntu.com/releases/8.04/](http://releases.ubuntu.com/releases/8.04/)

See the file entitled "MD5SUMS" and  if you are inclined, "MD5SUMS.gpg"

Put the text file MD5SUMS in the same directory as your iso and :

```
md5sum -c MD5SUMS
```

See also : [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Last, when you boot the CD there is a self test function that checks the integrity of the download / burn.

---

### Post by Eric Weir on 2008-04-23
> **bodhi.zazen said:**
> First I am sorry you are so frustrated, it gets better. It takes time to learn a new OS, 4-6 months.

Second, the md5sum is not *that* hard to find.
md5sum was installed on my system. I'd already run md5sum and needed to locate the UbuntuHashes page so I could compare the hash listed for what I downloaded with what md5sum had calculated.

After posting my rant, I went on to run md5sum on the CD that I'd burned. Another instance of instructions that are transparent to an experienced user and opaque to the novice, which I guess is what I am, given the difficulties I'm experience. Only took me a couple hours to do it.

At the moment I've got the CD in my CDROM drive. When I put it in, the system put an icon on the desktop. Right clicking on the icon gave me the option of mounting the drive. After I figured out how to get md5sum to run on the CD, which took me a long time, I right clicked on the icon again assuming could use the eject option.  

No such luck. Rather, I get a "KDE media manager is not running" messsage. So I can't eject that way. Pushing the eject button on the drive does nothing. I've rebooted the system, and still can't find anyway to get the CD out of the drive.

No doubt very simple -- if and when you know how, which is *absolutely* opaque to this apparently stupid user at this time. 

A few simple tasks -- backing up a couple of folders to the second HD, downloading, burning, and verifying Ubuntu 7.10 -- have taken me from 9:30 AM to till 4:00 PM. I haven't gotten any of my real work done. Ridiculous.

**Why **couldn't ubuntu.org just tell me where UbuntuHashes is?

**Why **did KDE Media Mannager stop running?
[B]
Why? Why? Why?[/B]

Again, forgive my ranting, but I am extremely frustrated.

---

### Post by xyverz on 2008-04-23
I do the following to verify the MD5SUMS and get an error:

```
$> gpg --verify MD5SUMS.gpg MD5SUMS
gpg: Signature made Fri 18 Apr 2008 04:21:34 AM PDT using DSA key ID FBB75451
gpg: Can't check signature: public key not found
```

My buddy tells me I need to import the signature file, which I cannot find.  This is extremely frustrating to me.

Any pointers?

---

### Post by jdrodrig on 2008-04-23
> **Eric Weir said:**
> 
Google can find it on Ubuntu, but Ubuntu can't find it on Ubuntu.

Well...after all google is famous for something...

I guess that something to be said is the importance of trying first LiveCD before upgrading or installing, specially if under tight work deadlines...

---

### Post by bodhi.zazen on 2008-04-23
Why did you have to run a md5sum on the CD ?

Your CD burning software should check this for you when it burns. I use K3b ...

Furthermore, boot the CD and chose the option to check the installation media.

Don't know about your eject issue. close any applications which are accessing the CD, including terminals, right click the CD icon and select eject ...

---

### Post by aimpau on 2008-04-24
Try unmounting the CD first rather than ejecting it.

---

### Post by Eric Weir on 2008-04-24
> **bodhi.zazen said:**
> Why did you have to run a md5sum on the CD?
Just following instructions on HowToDoMD5SUM, obtained from a link on the download page.

> Your CD burning software should check this for you when it burns. I use K3b ...You know that. I don't. Remember, I'm a relative novice. 

> Furthermore, boot the CD and chose the option to check the installation media.Yes, you reminded me that that was an option -- but, I wasn't planning/ready to do the installation immediately after the burn. [I suppose I could've waited till I was ready.] And per above, I was under the impression that it was something I ought to do.

> Don't know about your eject issue. close any applications which are accessing the CD, including terminals, right click the CD icon and select eject ...I finally managed to get the disk out by shutting down, rebooting, and pushing the eject button on the drive before the system started to boot.

I'm feeling a little less frustrated today. I get a little bent out of shape though when I don't get any work done because I've spent a day trying to do some simple thing on [K]Ubuntu.

I've decided I have to do my work first, then give a couple hours at the end of the day to Kubuntu. Take it one thing at a time. Can't get caught up in trying to get the system completely configured the way I want it all at once. Make do till I get there.

I do appreciate your suggestions.

Sincerely,

---

### Post by Eric Weir on 2008-04-24
> **aimpau said:**
> Try unmounting the CD first rather than ejecting it.
Thanks, I'll keep that in mind. But at the time I went to do the eject I was informed that "KDE Media Manager is not running." Unmounting was also not an option then.

Any idea why KDE Media Manager stopped running. I doesn't seem to be something you can restart easily. It's not on the menu. I may be misremembering, but I don't believe I was able to find it in Add/Remove programs, either. 

I don't know, of course, but it seems to be a system package that's not visible to the user, at least the ordinary user. So why would something like that stop running when you're in the middle of a task that requires it?


Thanks for the suggestion, and unmount will be the first action in the future.

Sincerely,

---

### Post by FastZ on 2008-04-25
Eric,
  I suggest you start doing some reading.

This is a good book.  I bought a copy for my ex-girlfriend. I doubt she's read it though.
[http://www.amazon.com/Ubuntu-Unleashed-2nd-Paul-Hudson/dp/0672329514/ref=pd_sim_b_title_4](http://www.amazon.com/Ubuntu-Unleashed-2nd-Paul-Hudson/dp/0672329514/ref=pd_sim_b_title_4)

And if the second edition of this book was as decent as the 1st, then I recommend this one as well.
[http://www.amazon.com/Official-Ubuntu-Book-2nd/dp/0132354136/ref=pd_sim_dbs_b_img_4](http://www.amazon.com/Official-Ubuntu-Book-2nd/dp/0132354136/ref=pd_sim_dbs_b_img_4)

---

### Post by Eric Weir on 2008-04-26
> **FastZ said:**
> Eric,
  I suggest you start doing some reading.

I was kinda expecting this. Even coming to that realization on my own. I guess I am learning. Fortunately I have an IBM ultralight that I bought to put Xubuntu on that I love and that is available while take my time getting the kinks worked out in my attempts at Ubuntu installations. Latest iteration is that I think I'm gonna give Xubuntu a try on the desktop.

About the books, I have the "official" one but not the other. I do have Ubuntu Hacks from O'Reilly that I dabble in for help with specific issues. Recently I came across this,
[http://www.linux.org/lessons/beginner/index.html](http://www.linux.org/lessons/beginner/index.html)  It seems pretty clear and pretty comprehensive. There's an intermediate version, too.

I appreciate the suggestions.

Sincerely,

---

### Post by altonbr on 2008-05-16
I feel if you're running MD5sums that you're more of an advanced user and should know that MD5s will not be on the front page.

I've been running Ubuntu for 2.5 years and I've still never ran MD5sums.

I do agree, however, that Ubuntu's website needs a usability upgrade (and so does its search engine) and needs to focus on documentation much much more.

---

### Post by armitage1337 on 2008-05-25
I'm not really sure why Ubuntu's search needs to be that good anyway. As a Linux user, you should have come to realize by now that Google is **the** place to go if you want information on any topic online. Rather than depending on individual sites to develop working search algorithms (which probably isn't at the top of their priorities list) you should just append your search with "site:<site name>", allowing you to search that site without using their built-in search.

---

### Post by 3rdalbum on 2008-05-26
If you use a mirror to download Ubuntu disc images, the hashes are in the same file listing as the disc images. Obviously though, the hashes should be easier to get to from the main Ubuntu download sites.

---

### Post by Cap'n Skyler on 2008-05-26
i think your frustration is in the inherant geekiness that is built into linux in general.and i say that and mean it needs to be pared down and made easier.
so if your butt gets chapped--sound off!!
then lets hunt down what is bothering you and get a real solution going for you!:guitar:

---

