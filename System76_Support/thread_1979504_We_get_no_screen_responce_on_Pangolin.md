---
title: "We get no screen responce on Pangolin"
date: 2012-05-13
forum: System76 Support
---

### Post by ranch hand on 2012-05-13
We have a Pangolin that my wife just loves.  Got it just before 10.04 was released so it came with 9.10 installed.

Upgraded it to 10.04 in late summer of 2010 and have had no trouble with it since that time.

It is used most of the time right in the same place here at home.  It does make some trips with my wife on occasion.  We got the backpack bag with it and it is transported carefully.

I used it last night to look some things up for another laptop while the box I am on now was installing an OS on my external.  Worked fine.

Shut it down and there were no signs of trouble.

Wife tried to fire it up today and you can hear the thing running and feel the air coming out of it.

If plugged into AC you get two beeps during bootup.  If on battery I got 1 beep followed by 2 beeps.

The bios screen does not show up.  If it were and external monitor such as my desktop uses I would suspect it was turned off or some power problem.

What is the best thing for me to do at this point?

---

### Post by brdmn on 2012-05-13
Two beeps and no bios screen suggests that some type of pre-boot self-test must have failed.  You could try checking to see if any part has been jarred loose--RAM comes to mind, or maybe the ribbon cable that connects the screen to the mainboard--maybe take it out and put it back in?  Hard drive seems less likely, as you would have seen the BIOS boot screen and some type of error message.

---

### Post by ranch hand on 2012-05-13
> **brdmn said:**
> Two beeps and no bios screen suggests that some type of pre-boot self-test must have failed.  You could try checking to see if any part has been jarred loose--RAM comes to mind, or maybe the ribbon cable that connects the screen to the mainboard--maybe take it out and put it back in?  Hard drive seems less likely, as you would have seen the BIOS boot screen and some type of error message.
Thank you very much.

I know my way around the inside of a desktop very well.  Have never messed with the guts of a laptop.

Have been working on just cleaning  up a viao so that Vista may work on it better and found that Squeeze Xfce Live CD boots on it great but once again nothing inside the bugger.

Had not thought about ram.  Have thought about the connection to the screen.

The screen seem most likely but yes the ram would do it too.

Haven't had a chance and don't remember the details of what we left it set at but we did, a while back as an experiment in watching a movie, enable 2 monitors so we could watch on the TV.

Going to hook the bugger up and see if that does anything.  May be disabled.

If it works it shows anything it would have to be the monitor.

I may try to log into it blind too.  If I could do that I could ssh into it from here.  That might tell me something too.

Will have to get the thing open somehow and I don't have a clue.  The manual disappeared about a year ago so I will have to look into this.  May have to get another one somehow.

Thanks a bunch for the response.  I thought that was probably the case with the beeps.  And I sure never even thought about the ram.

---

### Post by isantop on 2012-05-14
> **ranch hand said:**
> Thank you very much.

I know my way around the inside of a desktop very well.  Have never messed with the guts of a laptop.

Have been working on just cleaning  up a viao so that Vista may work on it better and found that Squeeze Xfce Live CD boots on it great but once again nothing inside the bugger.

Had not thought about ram.  Have thought about the connection to the screen.

The screen seem most likely but yes the ram would do it too.

Haven't had a chance and don't remember the details of what we left it set at but we did, a while back as an experiment in watching a movie, enable 2 monitors so we could watch on the TV.

Going to hook the bugger up and see if that does anything.  May be disabled.

If it works it shows anything it would have to be the monitor.

I may try to log into it blind too.  If I could do that I could ssh into it from here.  That might tell me something too.

Will have to get the thing open somehow and I don't have a clue.  The manual disappeared about a year ago so I will have to look into this.  May have to get another one somehow.

Thanks a bunch for the response.  I thought that was probably the case with the beeps.  And I sure never even thought about the ram.

If you can't figure it out, go ahead and open a support case. We'll be able to help you there. This sounds like some kind of hardware issue.

---

### Post by ranch hand on 2012-05-14
> **isantop said:**
> If you can't figure it out, go ahead and open a support case. We'll be able to help you there. This sounds like some kind of hardware issue.
Thank you, I am planning on doing just that.

When we bought this box I don't remember any account set up with a password at that time so I will need to call and straighten that out.

On my lunch break now and don't know if I will be able to do so today.  Same time zone as you and my hours today match yours.  Tomorrow will probably be different as we need to work with the right weather conditions.

I am sure this is a hardware problem and probably not to hard to straighten out.

I just want to be sure that my repairs are carried out in the proper manner so that the box does not suffer any ill effects.  Wife is very fond of this box.

Has been trouble free up to this point.  Small OS related problems are no trouble, I was in on 10.04-testing from the tool chain (2 days before it was announced even).  12.04-testing is the last testing cycle I plan on participating in but I now run Debian testing as my production OS and a near copy based on Sid for fun.

Have Fedora 17 on here too but am much more interested in Debian and Debian based OS's.  Just like the package management and grub versions better.

Thanks for the reply, will be in contact with you at the earliest possible time.

---

### Post by isantop on 2012-05-14
> **ranch hand said:**
> Thank you, I am planning on doing just that.

When we bought this box I don't remember any account set up with a password at that time so I will need to call and straighten that out.

On my lunch break now and don't know if I will be able to do so today.  Same time zone as you and my hours today match yours.  Tomorrow will probably be different as we need to work with the right weather conditions.

I am sure this is a hardware problem and probably not to hard to straighten out.

I just want to be sure that my repairs are carried out in the proper manner so that the box does not suffer any ill effects.  Wife is very fond of this box.

Has been trouble free up to this point.  Small OS related problems are no trouble, I was in on 10.04-testing from the tool chain (2 days before it was announced even).  12.04-testing is the last testing cycle I plan on participating in but I now run Debian testing as my production OS and a near copy based on Sid for fun.

Have Fedora 17 on here too but am much more interested in Debian and Debian based OS's.  Just like the package management and grub versions better.

Thanks for the reply, will be in contact with you at the earliest possible time.

Slightly off-topic, but Ubuntu betas and Debian testing are two very different animals (or toys, if you prefer ;) )

---

### Post by ranch hand on 2012-05-14
> **isantop said:**
> Slightly off-topic, but Ubuntu betas and Debian testing are two very different animals (or toys, if you prefer ;) )
Yes they are.

Debian testing with the package "apt-listbugs" and someone that does not install buggy packages or upgrade to buggy versions of packages has a system that is up to date with any Ubuntu release and more stable than those releases.

Sid is a little trickier but with care it can be very stable too, I am careful and use it as my backup (really) for my testing install.

I also use it for trying the really new packages in the experimental repo (apt -t experimental install <package> or aptitude install <package> -t experimental).

Also have the sid repo in my testing install in case a buggy package is fixed in sid but not in testing.  Same commands (sid instead of experimental of coarse) get those.

Have Squeeze on here for real secure purposes.  Set up pretty hardened.  A lot like 10.04 (based on Squeeze) but is a bit faster I think.

Can't, even with 10.04.4 boot 10.04 on this box (works fine on the Pang).  Plymouth and my hardware do not get along.  If I can boot it then it will not shut down (once in a while I try it by booting the Live Session off my HDD using grub).

Ubuntu still will not boot well in 12.04 but Xubuntu will.  Have to alt-SysRq-b to get out of it though.  Lubuntu works like Xubuntu.

Have never, in all these releases using Plymouth, with multiple installs, had one boot log written.  Just will not work on here at all well.

Start work at 6am tomorrow so will call in and get all this straight so I can communicate with you guys.  Really want to do a clean job with no cosmetic damage to the box.  Wife really loves it.  First couple months she did haul it around and used it at work.  Couldn't separate them.

You have, at least, on very happy customer.  Got it for her as a Mothers Day gift.  Pretty happy with that choice myself.

---

