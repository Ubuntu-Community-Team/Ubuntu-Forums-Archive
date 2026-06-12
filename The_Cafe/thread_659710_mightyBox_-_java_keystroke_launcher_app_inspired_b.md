---
title: "mightyBox - java keystroke launcher app inspired by Quicksilver - Devs needed!"
date: 2008-01-05
forum: The Cafe
---

### Post by sk8dork on 2008-01-05
**_[SIZE="3"]mightyBox[/SIZE]_**
[homepage]("http://www.eyalw.com/")
[@googlecode]("http://code.google.com/p/mighty-box/")
[@googlegroups]("http://groups.google.com/group/MightyBox")
[**see it in action**]("http://www.eyalw.com/drupal/node/43") [video]
[screenshots!]("http://www.eyalw.com/drupal/image/tid/2")

**_about:_**
**mightyBox** is a free and open source keystroke launching application inspired by, and very similar to, Quicksilver (OSX). It is developed using the Java language, and **targeted to run on both Linux and Windows platforms**. It allows users to use the keyboard to rapidly perform tasks such as launching applications, manipulating files and data, running scripts or sending e-mail. Although it is a complex application, it is centered around a very simple three-panel interface, called the "command window": the user performs complex tasks using simple, configurable key-combinations.

mightyBox is currently in alpha stages, but has only been in development for 2 months and has been coded from scratch in java by its primary developer. as you can easily see from the video and screenshots, even in its young state it has come a *very* long way.

**linux developers** are needed to code a native linux library to allow mightyBox to listen for a trigger keystroke (ctrl+space), and of course for any further linux specific development assistance. currently there is only a working alpha for windows (xp and vista). the source is available from the googlecode site.

*and now for some personal tidbits*: i've been using mightyBox in windows for the past couple weeks, and it's great! since i prefer to work in linux (ubuntu) i would very much like to see the development of mightybox progress into this platform. the primary dev of this app is mainly a windows programmer, but he has been a linux user for about 2 years. 

there are a handfull of similar apps out there for both windows and linux. why should you care about mightyBox? surely i hope you are not in that mindset, as we are all here for the freedom of choice!

reply to this thread or post to the google group with any ideas, suggestions, feedback. we can't wait to hear it!

(note: i am not a programmer and as such i am not the primary dev of this application.)

p.s.: this project was previously named "jquicksilver". we are currently replacing all occurrences of the old temporary name with the new name.

---

### Post by sk8dork on 2008-01-06
originally posted in the wrong place, now moved where it will hopefully get some views from the right people. what do you guys think? i know plenty of you guys have a windows installation you can test/work with this in. =)

---

### Post by IMYojimbo on 2008-01-07
Hi, 

I'm the main developer of MightyBox. It seems like there's no interest in this app? Maybe you could write what do you think about the idea, or any kind of feedback will be appreciated.

---

### Post by sk8dork on 2008-01-07
there's gotta be interest in this app, just looking at other new applications like GNOME Do, or launchy in windows. does anyone have any suggestions, comments?

---

### Post by tomauty on 2008-01-07
It looks really nice. The results of the searches have nice icons and it is fast and responsive. I hope a linux version will be ready soon. I'll be on the list of users.

A few bugs I have noticed are as follows:

It copies whatever is behind it, which I don't know if that is a technical limitation of java but it is not true transparency. 
This in turn causes strange borders filling in the rounded edges when mightybox is on a blank desktop

There is no ability to delete what is being typed, or it is not shown that it is deleting.

One suggestion I have is to provide a bit more of a view of what the user is typing. It is difficult to tell what I have typed in as I type, and can't tell if I have misspelled something.

Other than that I am enjoying using it.

---

### Post by sk8dork on 2008-01-07
> **tomauty said:**
> It looks really nice. The results of the searches have nice icons and it is fast and responsive. I hope a linux version will be ready soon. I'll be on the list of users.

A few bugs I have noticed are as follows:

It copies whatever is behind it, which I don't know if that is a technical limitation of java but it is not true transparency. 
This in turn causes strange borders filling in the rounded edges when mightybox is on a blank desktop

There is no ability to delete what is being typed, or it is not shown that it is deleting.

One suggestion I have is to provide a bit more of a view of what the user is typing. It is difficult to tell what I have typed in as I type, and can't tell if I have misspelled something.

Other than that I am enjoying using it.

thanks for the response! i agree with everything you said, and hopefully these things are in the works. the transparency issue is a tough one though, as supposedly java doesn't have real transparency support, so it is doing a psudo transparency by taking a picture of the background just before it brings up the command window, i think. mightybox currently assumes you know what you're typing and that you're fast, as it does not show you what you've typed unless you're in the browse/list/tree mode, after a few seconds what you have typed will reset when you start typing more, backspace one time will clear anything you entered, etc. 

we encourage you to post your issues at the google code site, no matter how big or small.

if anyone has any insight at all as to how to allow this java app to listen for hotkeys in linux, it would be a large step into linux functionality for mightybox! we need linux devs to help us out with this.

---

### Post by IMYojimbo on 2008-01-07
Actually the transparency thing can be fixed quite easily, both in Windows and in Linux. Again, it all comes down to native libraries. 

Basically, if some Linux devs will offer their help, MightyBox could be easily migrated to the Linux desktop. it has really few native dependencies so my guess is that it could run smoothly in all ditros and desktop environments , KDE or GNOME, it dosent matter. 

Since i have no knowledge of using Linux native libs. I can only wait until someone will offer his skills to help.

Thanks for the feedback

---

