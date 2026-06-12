---
title: "Web apps"
date: 2012-10-19
forum: Ubuntu Development Version
---

### Post by ELD on 2012-10-19
So do you think it is possible for this cycle we can have web apps that don't require the browser to be open on the websites?

So facebook, g+ and gmail for example would give you new message notifications when you are not on the website?

This would make them much more useful!

---

### Post by offgridguy on 2012-10-19
Curious, how would this be possible?

---

### Post by MG&amp;TL on 2012-10-19
> **offgridguy said:**
> Curious, how would this be possible?

Web service asks to install webapp through firefox modification, firefox installs application + configuration to appropriate place in home directory, daemon running on startup starts the webapps when necessary.

It could be engineered, is the point. :)

---

### Post by offgridguy on 2012-10-19
Thanks for the info, since it could be engineered the question would be is it likely to
happen?:)

---

### Post by MG&amp;TL on 2012-10-19
> **offgridguy said:**
> Thanks for the info, since it could be engineered the question would be is it likely to
happen?:)

I don't know. Is the answer. I'd suggest taking it up with the Unity webapps team people. :)

---

### Post by chrismine on 2012-10-19
Don't know how but it's being done in Android - get notifications for Facebook when no app or web page open, technically feasible...

---

### Post by cariboo on 2012-10-19
> **chrismine said:**
> Don't know how but it's being done in Android - get notifications for Facebook when no app or web page open, technically feasible...

On my android phone, there is always a facebook app running. I haven't been able to completely remove it. On my Android tablet, I've removed the facebook app, as I don't use it.

---

### Post by scradock on 2012-10-19
As it is, the last few weeks of QQ severely curtailed the usefulness of Ubuntu for me. aMSN was removed some months back, now Emesene is gone - there seems to be no available program to monitor and report new mail on live.com, gmail, etc. The webapps seem to offer the ability to have that, but only when FF is running.

For ***'s sake - we all laugh about the pre-historic AOL "You've got mail" message, but that's what being connected is all about! I feel I'm back in the Stone Age without notifications, under my control, of whether I have unread email messages.

And please don't say I need to get a cell-phone - I read email on a computer, thank you very much! Not on a 2 inch (or 4 inch - or even (gasp!) 5 inch screen).

Ready to head to a distro that keeps useful services going instead of eliminating them in favor of marketing ploys....

---

### Post by mc4man on 2012-10-20
>  there seems to be no available program to monitor and report new mail on live.com, gmail, etc. 
As far as gmail I get notification on screen & thru the messaging indicator for gmail, (turns blue, lists mails),  so "no..." isn't quite true

---

### Post by cariboo on 2012-10-20
I use Thunderbird, I get the blue envelope, and a pop sound whenever a new email is received. I have 2 gmail accounts, 3 with my ISP, and an ubuntu.com email address.

---

### Post by jbicha on 2012-10-20
> **scradock said:**
> As it is, the last few weeks of QQ severely curtailed the usefulness of Ubuntu for me. aMSN was removed some months back, now Emesene is gone - there seems to be no available program to monitor and report new mail on live.com, gmail, etc. The webapps seem to offer the ability to have that, but only when FF is running.



It's back... [https://launchpad.net/ubuntu/+source/amsn](https://launchpad.net/ubuntu/+source/amsn)

And Emesene never left...

Why don't you just use Evolution, Thunderbird, or similar if you want to see new email without a web browser?

---

### Post by ELD on 2012-10-20
I use gmail in the browser so why would i want to use thunderbird? Don't you need to have that open too or even when close does it have something running?

The web apps working without the browser is just the ideal solution no having to use an email client or install some third party gmail indicator.

---

### Post by scradock on 2012-10-20
> **jbicha said:**
> It's back... [https://launchpad.net/ubuntu/+source/amsn](https://launchpad.net/ubuntu/+source/amsn)

And Emesene never left...

Why don't you just use Evolution, Thunderbird, or similar if you want to see new email without a web browser?

Thanks for the news about aMSN, Jeremy. That's a relief.

I'm not sure why you say emesene never left - it was missing from the repos for a while, apparently because of a toolkit conflict. Maybe it came back and I didn't know to set it up again. I'll try it and see.

Hmmm - tried to launch it and got a Segmentation Fault. No helpful error messages in the terminal I launched it from - I'll send in the apport report to Launchpad.

As ELD says, why would I want to have a huge program like Thunderbird, Evolution or Firefox running all the time - it just needs a simple little beast that watches, notifies and connects when clicked.

---

### Post by converted on 2012-10-20
I have to admit that as they currently stand I don't really see the point of the webapps.

I was wondering why I couldn't find much online about them until I experienced them.  Then I understood once I installed 12.10 -- at this time they seem to me to be nothing but glorified bookmarks that want a spot on my launcher.

I understand the argument some of you have made that these things belong in a browser -- but then what is the point?  I could get a gmail notifier for the tray (yes, it's not really called the tray, yadda yadda) years ago.  And Ubuntu could certainly provide one now that doesn't require installation of a "webapp".  
 
I'd love to see webapps be something awesome, but at the moment they seem only to be confusingly pointless.

Take the HUD as a counter-example --

With webapps I was excited about them until I tried them.

With the HUD, I didn't really get it until I tried it -- and now I love it!  I don't use it all the time, but when I do I'm *really* happy that it's there.

---

### Post by scradock on 2012-10-20
Checked into the emesene problem - it's in the repos, but it has been unusable since early September. It started crashing with a SEGFAULT on startup, and it hasn't been fixed as far as I can see. LP bug #1050358.

---

### Post by buzzingrobot on 2012-10-21
Dunno if this is the intended direction for Ubuntu webapps, but OS X has had an app for several years called [Fluid (http://fluidapp.com).]("http://fluidapp.com")

It encapsulates a site as an independent app that can be executed without opening a browser. 
[]("http://fluidapp.com")

---

### Post by serdotlinecho on 2012-10-22
Hmmm, how about fogger webapps in Ubuntu? It does the same thing like fluidapp, right?

---

### Post by serdotlinecho on 2012-10-22
buzzingrobot, thanks for sharing.
Damn, fluidapp looks good. 
[https://www.youtube.com/watch?v=LsgQFOWMFgo](https://www.youtube.com/watch?v=LsgQFOWMFgo)

---

### Post by dpjg on 2012-10-22
> **serdotlinecho said:**
> Hmmm, how about fogger webapps in Ubuntu? It does the same thing like fluidapp, right?

I asked this question already [in another thread]("http://ubuntuforums.org/showthread.php?t=2073647"): I cannot find fogger in the Ubuntu 12.10 repos nor in the original ppa. Any idea, what happened?

---

### Post by serdotlinecho on 2012-10-22
try adding this ppa:

```
sudo add-apt-repository ppa:loneowais/ppa
sudo apt-get update && sudo apt-get install fogger
```

---

### Post by mr john on 2012-10-26
Isn't this what gwibber was for? Back in the day I used to have everything hooked into Trillian Pro. It had rss feeds, email checker and all my ims.

---

### Post by ELD on 2012-10-26
> **mr john said:**
> Isn't this what gwibber was for? Back in the day I used to have everything hooked into Trillian Pro. It had rss feeds, email checker and all my ims.

Gwibber is a social media client aimed at mainly things like twitter and identica, not for facebook, g+, emails etc.

---

