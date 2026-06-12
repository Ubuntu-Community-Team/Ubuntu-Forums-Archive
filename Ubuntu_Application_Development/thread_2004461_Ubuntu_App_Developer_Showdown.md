---
title: "Ubuntu App Developer Showdown"
date: 2012-06-15
forum: Ubuntu Application Development
---

### Post by mhall119 on 2012-06-15
We have just launched the Ubuntu App Showdown contest at [http://developer.ubuntu.com/showdown/](http://developer.ubuntu.com/showdown/) with an opportunity to win awesome System76 laptops, Nokia N9 phones, and more! If you are not a programmer, share your app ideas and votes for inspiration for entrants at [http://www.reddit.com/r/ubuntuappshowdown/](http://www.reddit.com/r/ubuntuappshowdown/) - the contest kicks off on Monday, so be sure to check out [http://developer.ubuntu.com/showdown/](http://developer.ubuntu.com/showdown/) right now!

**Note:** The Quickly requirement was also dropped: [http://developer.ubuntu.com/2012/06/ubuntu-app-showdown-no-longer-requires-quickly/](http://developer.ubuntu.com/2012/06/ubuntu-app-showdown-no-longer-requires-quickly/)

---

### Post by jppiiroinen on 2012-06-18
Started to work on a Qt project for the showdown \\:D/

The application should be a cross-platform IRC client, which would have similar features as mIRC has on Windows.

The Name of the application as well as the open source license will be announced later :)

---

### Post by mhall119 on 2012-06-18
Be sure to post some early screenshots too!

---

### Post by jppiiroinen on 2012-06-19
> **mhall119 said:**
> Be sure to post some early screenshots too!

Here are some teaser images. ;)


20.6.2012:
[IMG]http://farm8.staticflickr.com/7243/7404500276_24c4e980c2_b.jpg[/IMG]
21.6.2012:
[IMG]http://farm9.staticflickr.com/8007/7413366508_40951fbdf9_c.jpg[/IMG]
23.6.2012:
[IMG]http://farm9.staticflickr.com/8154/7426917316_be1c805cea_c.jpg[/IMG]
[IMG]http://farm9.staticflickr.com/8027/7426918450_37a08297e3_c.jpg[/IMG]
24.6.2012:
[IMG]http://farm8.staticflickr.com/7134/7428175144_728fdf7259_b.jpg[/IMG]

The first Qt/C++ prototype application works already, so I can login to freenode using ssl \o/

Still a lot of things to be done and to be tested. The plan is that I would have the irc client library done from scratch in the next few days, then I would focus on the UI side and possibly implement some eye-candy with QML.

Todo:
 - research more about Unity and integration apis
 - add possibility to log messages
 - add pastebin support for coding
 - publish quick and dirty version for testing

Done in the current prototype:
 - created an Ubuntu theme for qtoolbar
 - is to create a better namelist for the channels, 
 - which would show the user modes and 
 - implement the channel control commands and modes.
 - some of the IRC commands
 - simple Qt/C++ ui
 - Unity quick list
 - Unity indicate

After that I should be able to produce first deb files for testing. As I try to collect first all the features what I want into the prototype, and then I will rewrite the stuff again with more not-so-quick-and-dirty way. :P

---

### Post by EyeOfRa on 2012-06-24
The App Showdown sounds like fun so I thought this would be a great opportunity to learn Python.  I am working on Una, a Pulse-like RSS reader.

Una is my acronym for Ubuntu News Aggregator.  I will utilize Ubuntu One to synchronize feed list and track which stories have been read.

Here is an early screenshot...

[IMG]http://i.imgur.com/P7PMP.png[/IMG]


:confused:*Ubuntu App Showdown subreddit hasn't been accepting my App Submission post...  Tried contacting the moderators with no luck.*

---

### Post by juhapekka on 2012-07-08
Entry has been posted :)
======================================
A Qt -based IRC Client.

 Features:
  - join/part channel
  - private messaging
  - support for ssl encryption
  - set channel topic
  - set user modes (op, deop, voice, devoice) on a channel
  - auto-join channel on connect

Screenshot:
[IMG]http://farm9.staticflickr.com/8152/7527903592_6aca8f8a23_z.jpg[/IMG]

Project Page:
[https://launchpad.net/jpiiirc](https://launchpad.net/jpiiirc)

PPA:
[https://launchpad.net/~juhapekka-piiroinen/+archive/jpiiirc](https://launchpad.net/~juhapekka-piiroinen/+archive/jpiiirc)

Support:
[https://answers.launchpad.net/jpiiirc](https://answers.launchpad.net/jpiiirc)

---

### Post by s.fox on 2012-07-09
> **EyeOfRa said:**
> The App Showdown sounds like fun so I thought this would be a great opportunity to learn Python. 

This is the same reason that I have entered.

**What does it do?**

 Basically it provides a quick and easy  method to launch my most commonly opened websites and applications from a  visually pleasing user interface.  The shortcuts include everything  from Planet Ubuntu to Rhythmbox.


 **What would I like it to do in future?**

 At the moment the website and  application shortcuts are fixed, it would be good if these could be  configured to use whatever shortcuts the user wants.


 **Why did I build it?**

 I am still learning the basics with  python and this is my very first steps into desktop application  development on Ubuntu.  I have had to learn how to build a user  interface, have it interact with my python scripts, sign PGP, packaging,  create a PPA and then get it into the Software Center.  That is a lot  of “new stuff” for me to learn, which is why I kept the application as  simple as possible.

**Screenshot**
[IMG]http://serial-coder.co.uk/blog/wp-content/uploads/2012/06/UI.png[/IMG]

[Project]("http://serial-coder.co.uk/blog/my-shortcuts/") website

---

