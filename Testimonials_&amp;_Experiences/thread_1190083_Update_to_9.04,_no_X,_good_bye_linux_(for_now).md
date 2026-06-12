---
title: "Update to 9.04, no X, good bye linux (for now)"
date: 2009-06-17
forum: Testimonials &amp; Experiences
---

### Post by xixor on 2009-06-17
Hello Ubuntu community, I just updated to 9.04 through the automatic update utility and now X doesn't start.  I just thought I'd mention it so you know, as I think that is how this "community" is supposed to work.

Some background: I've been a linux user since 1994 or so, where I used debian, slackware or redhat as my sole desktop OS and quite frankly, loved it.  I was in high school or my first years of university and had oodles of time to play with computers.  In the last 6 years or so I've been an on-again-off-again Linux user.  Once a year or so I will try out a new distro, check it out, fiddle with it, and see how it is.  Since I've always read the articles in Linux Gazette that state "199x is the year of the linux desktop!" I can't but help come back and see how things have improved.

Now, I am not asking for help on how to get X back up and running.  I am sure I could get to a console, ssh in, fiddle with xorg.conf, remove/install/fix some packages, and after an hour or two, would be back up.  It's just that I don't want to.  Every time I use linux, it is the same, and now, frankly, my time is just too valuable.  I just have absolutely zero desire to go through this same exercise that has been repeated for the last 15 years.

I do not mean to complain, or be a "linux hater".  I've got a project on sourceforge and I like the open source community for example, and Ubunutu/Debian/GNU Linux is one heck of an impressive suite of software.  I just felt the need to tell you in the community that my system doesn't work after the 9.04 upgrade.  I know from experience not to put any mission critical data on my linux partitions, that I probably just won't boot to it again, and will just reclaim the space when I need more room.

Keep up to good work. I will be back in 2010 or 2011 to see where the distro is at!

xixor

---

### Post by Mighty_Joe on 2009-06-17
> **xixor said:**
> I just thought I'd mention it so you know, as I think that is how this "community" is supposed to work.


If you want to help, you should file a report in [launchpad]("https://launchpad.net/ubuntu") with all relevant details (hardware, software, test case). The developers use launchpad to track, prioritize and assign bugs so they get fixed.  
Posting in the forums, especially with a "I'm not even going to try to figure out what's wrong, so good luck figuring it out" message is a pretty good way to get ignored.

---

### Post by Idefix82 on 2009-06-17
> **xixor said:**
> 
Now, I am not asking for help on how to get X back up and running.  I am sure I could get to a console, ssh in, fiddle with xorg.conf, remove/install/fix some packages, and after an hour or two, would be back up.  It's just that I don't want to...
I just felt the need to tell you in the community that my system doesn't work after the 9.04 upgrade.

Not sure, what anybody is supposed to do with this piece of information. Anyway, bye-bye and see you later.

---

### Post by Elfy on 2009-06-17
Possibly you have intel or ati as graphics - if so it was in the Release Notes. 

Anyway as you've stated that you don't actually want any help I've moved it to Testimonials and Experiences

---

### Post by Therion on 2009-06-17
[COLOR="White"].
.[/COLOR]

[IMG]http://blog.enterpriseitplanet.com/green/blog/blogpost_img/picard_facepalm.jpg[/IMG]

---

### Post by ngsupb on 2009-06-17
good luck :p

---

### Post by HappyFeet on 2009-06-17
Ever hear of a clean install? Or using a version that works on your hardware configuration? Guess not.

---

### Post by 3rdalbum on 2009-06-18
In theory this shouldn't happen - Ubuntu will usually be able to tell that something's wrong and put the graphics to "safe mode" (vesa).

Why can't you get to a text terminal by pressing Control-Alt-F2? You can modify Xorg.conf here; it'll take all of 60 seconds for someone who's been using Linux for years. Reboot. If that fails, delete Xorg.conf (yes, I'm serious) and X will try and work out everything for itself.

---

### Post by RoboNuggie on 2009-06-18
> **xixor said:**
> 
I just felt the need to tell you in the community that my system doesn't work after the 9.04 upgrade.
xixor

Oh.

Umm..

Thanks!

:confused:  :^o  :roll:

---

### Post by masux594 on 2009-06-18
Maybe uninstalling graphic drivers or reconf xorg configuration file? Everybody know this kind of "issue"..

---

### Post by caravel on 2009-06-18
> **xixor said:**
> Hello Ubuntu community, I just updated to 9.04 through the automatic update utility and now X doesn't start.
The problem is caused by the update of xorg.  I think from checking your old posts that you have a ATI 4870x2?  If so then there was a simple solution for this - but I do see your point.  The dist upgrade from 8.10 to 9.04 cocked up a lot of peoples' systems.

The simple solution is to either clean install or purge the fglrx proprietary drivers *before* the upgrade.  This would have saved you a lot of headache.  You would then enable the new driver that is compatible with the version of xorg in 9.04.  The old driver running on the latest xorg causes the system to hang.

Anyway you didn't want help, so goodbye and good luck with whichever OS you're moving on to/going back to.

---

### Post by ukripper on 2009-06-18
Good bye

---

### Post by solwic on 2009-06-20
> **xixor said:**
> Hello Ubuntu community, I just updated to 9.04 through the automatic update utility and now X doesn't start.  I just thought I'd mention it so you know, as I think that is how this "community" is supposed to work.

Some background: I've been a linux user since 1994 or so, where I used debian, slackware or redhat as my sole desktop OS and quite frankly, loved it.  I was in high school or my first years of university and had oodles of time to play with computers.  In the last 6 years or so I've been an on-again-off-again Linux user.  Once a year or so I will try out a new distro, check it out, fiddle with it, and see how it is.  Since I've always read the articles in Linux Gazette that state "199x is the year of the linux desktop!" I can't but help come back and see how things have improved.

Now, I am not asking for help on how to get X back up and running.  I am sure I could get to a console, ssh in, fiddle with xorg.conf, remove/install/fix some packages, and after an hour or two, would be back up.  It's just that I don't want to.  Every time I use linux, it is the same, and now, frankly, my time is just too valuable.  I just have absolutely zero desire to go through this same exercise that has been repeated for the last 15 years.

I do not mean to complain, or be a "linux hater".  I've got a project on sourceforge and I like the open source community for example, and Ubunutu/Debian/GNU Linux is one heck of an impressive suite of software.  I just felt the need to tell you in the community that my system doesn't work after the 9.04 upgrade.  I know from experience not to put any mission critical data on my linux partitions, that I probably just won't boot to it again, and will just reclaim the space when I need more room.

Keep up to good work. I will be back in 2010 or 2011 to see where the distro is at!

xixor

I don't even have to read through all of the replies to know that somebody has already suggested a clean install as opposed to the horribly broken "update" system.  Wipe it all out, reinstall, and your problems ought to be fixed.  

Otherwise...well, see you in a year or two.  :)

---

### Post by Tamlynmac on 2009-06-20
[> ]("http://ubuntuforums.org/member.php?u=233497")[xixor]("http://ubuntuforums.org/member.php?u=233497")
I just felt the need to tell you in the community that my system doesn't work after the 9.04 upgrade.

Why?

Why the "**need to tell**" anyone? Over the last three years I've had some minor issues and didn't feel the need to tell. Either got help to fix it or figured it out on my own. Of course that assumes one wants assistance or has the desire to resolve the issue(s).

The OP has been provided numerous ideas in this thread and based on no response, one must assume they left. Hence, the OP really didn't tell the community anything, other than the fact that they've given up and will return in the future. My suspicion is rather than seek assistance, the OP will give up then too.

I find it extremely odd that the OP's final words included "KEEP UP THE GOOD WORK", having not been able to try 9.04. Exactly how did the OP come to the conclusion that it's "GOOD WORK"?

If the OP is reading the responses: Should you return in the future, perhaps the solution lies in expanding your horizons by accepting some support/assistance. Instead of simply complaining about and relying upon an online upgrade process.

---

