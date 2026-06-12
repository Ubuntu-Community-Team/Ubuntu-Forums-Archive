---
title: "accountability software"
date: 2007-04-01
forum: Ubuntu Christian Edition
---

### Post by xtheblack9x on 2007-04-01
Im going to be working on some accountability software for the ubuntu Christian edition (and other linux OS's). I'll post on this thread as i make progress to let everyone know how things are going. My prayer is that this will help others out in seeking to be more like Christ.

Unfortunately I'm no linux master I've been a windows guy. So it took me like a full day to figure out how to get my JDK Java Developerment Kit. Up and running. I spent all this time trying to do it the hard way and didn't realize there is a nice packaging system that installs everything for me :) . So ya my lack of linux knowledge my slow me down a bit but I'm hoping with a lot of focus i can get this thing out to you guys as soon as possible.



----------Plan's for the Program (may change)----------

This program will be working along side with DansGuardian :). Program will be writen in java. It will have a small GUI control panel with settings such as

* Sending DansGuardian Logs (to accountability partner)
* Sending All Websites Visited (to accountability partner)
* Enable
* Disable
* How often logs are e-mailed
* Add e-mail
* Remove e-mail
* Add Password
* Remove Password

any task that you do will require a password (most likely set by your accountability partner). You may how ever remove this password to change any options but removing password will be put in the logs that will be sent to your accountability partner along with any changes of settings (disable, enable, sending dansgardian logs, sending all websites visited).

------------------------------------------------------------------------------



thats at least what i think its going be be like. Im not sure what choices of how often to send the files though. I'm thinking of having 4 set lengths of time. If anyone has suggestions ill probably take the 4 most wanted duration's of time for the log sending.

---

### Post by mhancoc7 on 2007-04-01
This sounds great!

The one suggestion/comment that I have is about the password. I would prefer it if the program was setup to use the root user password (gksudo) by default. I know that this would make it easy for the root user to disable it, however you could simply set the program to notify the accountability partner when it is disabled. I just think this is more in keeping with how Linux is normally set up. The root user, in my opinion, should always have total control of their system.

Let me know what you think.

God Bless, Jereme

---

### Post by xtheblack9x on 2007-04-01
> **mhancoc7 said:**
> This sounds great!

The one suggestion/comment that I have is about the password. I would prefer it if the program was setup to use the root user password (gksudo) by default. I know that this would make it easy for the root user to disable it, however you could simply set the program to notify the accountability partner when it is disabled. I just think this is more in keeping with how Linux is normally set up. The root user, in my opinion, should always have total control of their system.

Let me know what you think.

God Bless, Jereme

ok we can do that :)

---

### Post by tonymccallie on 2007-04-03
Fantastic! This is exactly what I'm looking for. Here's a link that might be able to help you:
[http://www.safeeyes.com/faq2005/question.php?id=73](http://www.safeeyes.com/faq2005/question.php?id=73)

The document is for a similar idea, but could use the refinements you are talking about. I'm pretty decent with linux, but stink with java (I'm a php guy) so if I can help, let me know. Just PM me or email me. This is a roadblock I need to cross in getting my entire church staff moved over to linux.

Many blessings, Tony

p.s. I agree that your system should use the gksudo password. The important thing is logging the record for accountability partners. That's what Covenant Eyes does.

---

### Post by tonymccallie on 2007-04-03
Also, I just found this link you might be interested in:
[http://msmtp.sourceforge.net](http://msmtp.sourceforge.net)

In the other forum about accountability software, there was talk about setting up email that wouldn't get blocked. This might be an answer. Combine this little utility with anacron for users who don't leave their computers on all the time and we should be good to go. Maybe we could even figure out how to tap into the Evolution settings and use those??

Blessings, Tony

---

### Post by xtheblack9x on 2007-04-03
> **tonymccallie said:**
> Fantastic! This is exactly what I'm looking for. Here's a link that might be able to help you:
[http://www.safeeyes.com/faq2005/question.php?id=73](http://www.safeeyes.com/faq2005/question.php?id=73)

The document is for a similar idea, but could use the refinements you are talking about. I'm pretty decent with linux, but stink with java (I'm a php guy) so if I can help, let me know. Just PM me or email me. This is a roadblock I need to cross in getting my entire church staff moved over to linux.

Many blessings, Tony

p.s. I agree that your system should use the gksudo password. The important thing is logging the record for accountability partners. That's what Covenant Eyes does.

thank you so much for your offer i will let you know if theres anything i need help with. THANKS for all the info ill check it out sometime this weekend when i have some time.

---

### Post by xtheblack9x on 2007-04-04
wow tonymccallie your the best. I went over the first document you sent me and man. this takes most all the work out of it :). looks like most of it is going to be setting up the GUI and opening outside applications with arguments.

---

### Post by xtheblack9x on 2007-04-05
i attempted to run some of my old programs. and found out that the sun-java has some issues with displaying GUI based on the swing. I looked this up and found out that it conflicts with something. so I'm going to find a work around. Sounds like IBM java might be a solution or if i learn the old way of making GUI based on AWT it might work. I do some research into it later. but this week i have allot of java / math homework so not sure if ill get a chance.

---

### Post by mysticrider92 on 2007-04-06
> **xtheblack9x said:**
> i attempted to run some of my old programs. and found out that the sun-java has some issues with displaying GUI based on the swing. I looked this up and found out that it conflicts with something. so I'm going to find a work around. Sounds like IBM java might be a solution or if i learn the old way of making GUI based on AWT it might work. I do some research into it later. but this week i have allot of java / math homework so not sure if ill get a chance.

I noticed that the Linux Sun JDK/JRE doesn't seem to like awt or swing. You can compile the program with javac, but running java <program> creates an empty window. For me, it worked to use gcj and gij for Java programs (it's hard to beat GNU programming tools). 'gcj -C *.java' to compile seems to work pretty well and 'gij *' to run the program.

---

### Post by xtheblack9x on 2007-04-06
> **mysticrider92 said:**
> I noticed that the Linux Sun JDK/JRE doesn't seem to like awt or swing. You can compile the program with javac, but running java <program> creates an empty window. For me, it worked to use gcj and gij for Java programs (it's hard to beat GNU programming tools). 'gcj -C *.java' to compile seems to work pretty well and 'gij *' to run the program.

thank you so much this worked perfectly  :). you save me allot of trouble.

---

### Post by xtheblack9x on 2007-04-10
kinda doing this backwards but I made a GUI for the program before making the back end lol.

[[IMG]http://img213.imageshack.us/img213/9531/screenshotox1.png[/IMG]](http://imageshack.us)

---

### Post by mhancoc7 on 2007-04-10
> **xtheblack9x said:**
> kinda doing this backwards but I made a GUI for the program before making the back end lol.


Is there any other way to do it? ;)

Looks great! I am really excited about the possibility of getting this feature in Ubuntu CE.

God Bless, Jereme

---

### Post by dakotadare2b on 2007-04-10
I think this will be another great tool, to help us parents with supervising our children while on the internet.:)

---

### Post by accludetuner on 2007-04-12
I agree!  This will be an excellent tool to add to the arsenal of CE features.

Here's a related site my buddy told me about.  It's accountability software for XP/Vista but it might give you some ideas:
[http://xxxchurch.com/07/](http://xxxchurch.com/07/)  (<--- xxx church is not a porn link, I promise!!! lol)

If you want/need any help with this project, just say so ;)

---

### Post by jackelmatador on 2007-06-07
Not to be rude or pushy but I was just wondering if there was any progress on this?

---

### Post by runkidrun on 2007-06-07
I Was Looking For Something Just LIke This! GUI Looks Great! Please Keep Us Updated =D>


P.S.--Is It Possible To Add The Amount Of Time Someone Has Been On The Internet In The Email ?--

---

### Post by ElEdwards on 2007-06-27
I've been looking for this, too :)

In the meantime...... I'm a subscriber to Covenant Eyes.  Does anyone if this will work in Ubuntu through Wine?

Thanks! :)

---

### Post by xilix on 2007-09-04
Is there any progress with this piece of software?

I think it would be a very important part of a safe (in the christian meaning) operating system.

---

### Post by mssever on 2007-09-13
I've been working on something like this.
[http://ubuntuforums.org/showthread.php?t=550287](http://ubuntuforums.org/showthread.php?t=550287)

---

