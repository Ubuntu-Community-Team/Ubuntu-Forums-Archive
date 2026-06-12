---
title: "How to attract more people to Ubuntu"
date: 2019-05-02
forum: Ubuntu, Linux and OS Chat
---

### Post by anyeos-3 on 2019-05-02
I want to make a constructive critism on Ubuntu, because I think we need to attract more users.

For the average user it is hard to start in Ubuntu (Linux Desktop in general).
 We need more easy to use features like a way to install apps only downloading it. AppImage can be included by default with the AppImageLauncher too.
I guess that we must avoid an X Server. Instead there will be a some more simple solution like Wayland but I think we need something new that flavors speed and simplicity over complexity and few used features like remote X sessions.
I think will be a good idea develop with the above a Desktop and Window Manager using new technologies like CSS and SVG to draw Window decorations and widgets (accelerated in OpenGL or Vulkan).
Including too a way of porting the current applications (the ones based on GTK, QT, etc) to the new widget and window system in a simple way (maybe creating a reeplacement for GTK with the equivalent function names).
So we can port an entire desktop environment like Gnome Shell with little effort.

I know there is Wayland, but the testing about speed vs classic XOrg are not showing differences. I suggest test against Windows 10 and overcome it. Because to be more attractive we need give to the user and the application developer such an environment. The speed is something that everyone are searching for. The simplicity too. And if we sucess in that we will finish having a lot of more users.

I am interested in doing such a labor because it will attract more users and more developers.
We need more Applications too. The free ones are not enought for the day a day.

I am actually not using any propietary software but NVIDIA. But if there are more programs like After Effects and so, we will have a more competitive and motivating environment to develop more free software too (more users to target too). 
So I think it is not a bad idea and does not hurt the freedom of the free software concept. It only will make Linux more convenient as a Desktop OS.

So, people, please, think about it and give more ideas on how we can achieve it. Remember: I suggest to create a new Window System with widgets included, like Wayland but with more simplicity and speed taking advantage of new hardware (where possible) and with full compatibility with the current widgets (GTK, QT, etc).

Thank you for reading.

---

### Post by TheFu on 2019-05-02
Everyone new to Unix systems gets excited and wants everyone else to know about these fantastic systems. But not everyone is interested in changing and not everyone can switch to new applications. When you need 100% compatibility with MS-Office on Windows, there is only 1 way to get that.

Anyone with 5+ yrs experience has tried converting people, probably lots of people.  Learning Linux/Unix is like learning a new language. It is hard, especially if you came from Windows.  

Trying to make Linux into Windows will fail. Linux isn't Windows and it never will be.  Linux isn't OSX either. Get over it. Managing Linux developers is like herding chipmunks.  You might be able to get 3-5 going in the same direction for a year, but not much longer.

Package management is THE KILLER APP for all the popular Linux systems.  By far, it is the main reason for using Linux.  In the early 1990s, we had to download files to install time and it was a mess. Package management provides automatic dependency resolution, which works almost always. It is really impressive.  I have ZERO interest in going back to 'download a file' solutions.

To me, Snaps, Flatpaks and AppImage are currently DOA, not worth my time, until they fix the huge problems.  Today, it seems the architecture for snaps (I've only read about the others) can achieve their intended results, but the execution has failed by being overly restrictive.  By default, all snaps seem to prevent access to USB storage.  How is that a reasonable default?  Canonical has pushed snaps heavily for some packages where they just aren't needed.  Why does gnome need to be a snap?  Why does gnome-calculator?  If you understand the architecture, both of these are low risk systems and gnome is freakin' huge. I don't want/need 5 copies of the gtk libraries in RAM just because I'm running 5 different gnome programs.

Wayland has been missing key features, so I'm definitely in the X/Windows crowd still.  Most of my daily work is performed using a desktop that runs other applications on other systems on the LAN and displays the window back to the computer I'm sitting behind.  I've been working this way since the early 1990s.

The comments about Qt and GTK appear to be from a non-programmer. Yes?  

Ideas here don't go anywhere.  Nobody here works for Canonical and very few people here are active developers.

I've tried teaching CS and EE students Linux for years.  It took about 5 yrs before I became jaded. Initially, each fall, about 70 people show up for the first session, then 35, then 15, then 5 by the forth session. Usually, there are only about 3 students are truly interested each semester for a U with 20K+ students attending.  Creating and running 2-3 hr sessions on a weekend, for free, is a lot of work for just 3-5 people.  And there is only 1-2 extra who show up with no preparation for session 5 and expect to pick up the 12 hrs of already-covered material without any effort.

Now I only help people who take the effort to learn.  I'm a LUG organizer. Our club has over 1300 members. We have 10+ meetings most months, in different parts of town, at different times and DoW.  1 of those meetings is primarily for experts. All the others are for beginners. They are all free and we don't even ask for a name to attend. We go over different materials at each meeting, depending on who actually shows up.  The vast majority of new attendees want to learn for their jobs and they need to learn server management, not how to point-n-click on a desktop.  A few will attend about 5 sessions, but most show up once, we provide them with a list of "getting started" resources and they never return.  I am rather pleased that about 40% of the first-time attendees now are female.  For a long time it was 100% male.  It is good to see women taking control of their careers.

I'm 1 specific type of user.  In some ways I'm non-standard because I've been using a Unix X11 desktop for over 20 yrs now.  I know most of the power that is available in X11 and I know many of the issues.  The fact that it uses network layers for widget-to-widget communications is a blessing and a curse. Just depends on whether you use that facility or not.  It is THE killer app for X11 as far as I'm concerned.  Seamlessly running programs on different systems is amazing. On a fast network, I can't tell the difference between local and remote applications.  Actually, I can - the programs running remotely are faster.

"We need more applications."  Great, how do you suggest solving that?  You know, in the real world?

I wish you luck in getting more users.  Perhaps you will have more success than the 10M people before you did.

---

### Post by QIII on 2019-05-02
And, again, the mistake is in thinking that the desktop is all there is to computing.  It's only a sliver.

There are more users of Linux by an order or two of magnitude than there are users or anything from Microsoft or Apple.  They, and apparently you, simply do not realize they are using it every day in all manner of ways:  smart phones; cars; smart TVs; most of the internet backbone; the super-computers that meteorologists use to predict the weather (virtually all super-computers run Linux); home security systems; manufacturing controls, the New York Stock Exchange, many Fortune 500 companies ...

---

### Post by MartyBuntu on 2019-05-02
TheFu...I couldn't have said it better myself. You summed it up very well.

---

### Post by DuckHook on 2019-05-02
@OP

We know you mean well, but this is so much a recurring discussion that I am minded to move it there. Nonetheless, I'm also with TheFu and QIII on this. My take was already expressed in another recent thread. No point in repeating myself, so in case you are interested: [https://ubuntuforums.org/showthread.php?t=2414826&page=2&p=13849690#post13849690](https://ubuntuforums.org/showthread.php?t=2414826&page=2&p=13849690#post13849690)

---

### Post by yetimon_64 on 2019-05-02
> **DuckHook said:**
> ... [https://ubuntuforums.org/showthread.php?t=2414826&page=2&p=13849690#post13849690](https://ubuntuforums.org/showthread.php?t=2414826&page=2&p=13849690#post13849690)

On reading the opening post from the OP, I immediately thought of that post. So again here ... =d>... I thoroughly agree with the content of that post.

@OP, I most definitely recommend you have a read of the thread, and in particular that post, DuckHook links to above.

Regards, yeti.

---

### Post by TheFu on 2019-05-03
How much money does Microsoft spend on marketing? In 2018, they spend US$1.6B on marketing.
How much money does Apple spend on marketing? In 2015, they spend US$1.8B on marketing.

Linux is doing pretty freakin' great compared to those levels. 

For most end-users, they don't care about the OS.  It is 100% about the applications and using the applications they've already heard of.  They don't want to seek out "compatible" applications or "alternatives" - that's too hard.  The way to get people to consider moving to Linux is to get them using F/LOSS applications on their current OS.  I did this with my Mom years ago after she got hit with a batch of viruses from a spoofed "new baby" email.  
a) no grandma would ever NOT click on that email from a grand-daughter, right?
b) she didn't do anything unreasonable and immediately realized she'd been attacked. She powered down the system immediately and called me.

I'd been moving her over to F/LOSS for years.  She was using OpenOffice (libreoffice didn't exist yet), Thunderbird, Firefox for a few years already on Windows. A few months later, I visited and setup LXDE.  She was really scared, because she'd seen my highly custom use of Linux. I choose a GUI that looked much like she was used to using. After 1 day, she said that it wasn't hard at all. She happily used Linux until her death (long, good, life).  We upgraded her computer from a Pentium4 to a Core i7 - she didn't really notice much speed difference. The main thing to her was that everything was the same even though the entire computer, except the HDD, was new.  We literally pulled the HDD from the old system and put it into the new one. I forced the new NIC to use the old static IP so that I could remote in for maintenance and weekly remote backups.  That was it.

Attempts to make Windows software "just work" under Linux have been ongoing over 20 yrs.  Even with all that effort, perhaps 20% does work under WINE.  Want more software supported?  Buy a commercial WINE license.  Every $30-$50 helps, but it is best when millions do it.  But we can't expect MSFT to slow down their multi-BILLION $$$ software changes, many of which break WINE.  I think the last time WINE worked well with MS-Office was 2007.  I have Office 2003 installed in a WinXP VM somewhere here. Haven't used it in over 10 yrs now.
 
But end users are all a little different.

In a corporate environment, setting up a few Windows terminal servers for every 50 Linux clients is a way to help the migrations. Have each desktop only use F/LOSS tools, so licenses don't need to be tracked outside the professionally managed systems. We did that at my last company.  1 TS for 5 people. 

I think gamers are stuck. Linux just doesn't have large enough market for any finance person to agree to support Linux games, unless the CEO/President is a hard-core Linux user.  When it comes to making money, we Linux types tend to be cheap.  I buy 1 piece of software a year and it isn't for Linux.  Everyone has to figure out how they wish to give back to the Linux/GNU communities.  I volunteer my time, here (trying to help workaround issues), at my LUG and I give talks at conferences.  Others give $10/month to the EFF.  Some people get their companies to sponsor different project teams.  We each need to do what we feel comfortable doing, but something is better than nothing.

---

### Post by him610 on 2019-05-03
Totally agree with everything TheFu said in both of his posts.
I converted my spouse from Windows to Ubuntu. I convinced my daughter to take a series of online courses that included several labs using Ubuntu. I began using Linux (ubuntu) because I wanted to learn something about Unix, and Linux was the most economical way to do it.

Power to the Penguin!

---

### Post by QIII on 2019-05-03
"... converted ..."?

Part of the reason people are disinterested in Linux is just that sort of thing:  a religious-feeling expectation that one must leave one world behind and cleave only to the other as the true and righteous path.

We should not be wearing hair-shirts, growing neck-beards and eating organic, non-GMO locusts.  It is absolutely acceptable for people to use whatever number and type of OSes they choose.  There is no reason whatsoever to break from Windows and never send it holiday greeting card again.  Last I checked, using Linux is neither a religious undertaking nor a marriage.  Playing the field is allowed.

Why do we assume otherwise?

---

### Post by DuckHook on 2019-05-03
I get QIII's point, but, to be fair, "converted" could simply be used in a descriptive sense as in "I converted my Euros to Dollars".

I too "converted" my wife to Ubuntu, but in the purely descriptive sense.

---

### Post by Shibblet on 2019-05-03
I am a firm believer that you NEVER try to attract people toward something that you enjoy.  You find others that enjoy the same thing, and harmony ensues.  When you try to attract someone toward something you are interested in, they tend to see it from their perspective, and do not always see the same values within it that you do.

This works in all life situations.  Restaurants, Hobbies, Activities, Political, Religious, right down to Operating Systems.

If they're interested, they'll ask.

---

### Post by #&amp;thj^% on 2019-05-03
> **Shibblet said:**
> You find others that enjoy the same thing, and harmony ensues. 

Well said, plain and simple. ;)
However I'm not opposed to **learn** why others enjoy different.

---

### Post by DuckHook on 2019-05-03
> **Shibblet said:**
> I am a firm believer that you NEVER try to attract people toward something that you enjoy.  You find others that enjoy the same thing, and harmony ensues.  When you try to attract someone toward something you are interested in, they tend to see it from their perspective, and do not always see the same values within it that you do.

This works in all life situations.  Restaurants, Hobbies, Activities, Political, Religious, right down to Operating Systems.

If they're interested, they'll ask.
&#8593;&#8593;&#8593;Advice to live by.&#8593;&#8593;&#8593;

Mrs DuckHook couldn't care less about OSes&#8212;which I am passionate about. By the same token, I couldn't care less about watching royalty&#8212;which tickles her fancy.

We celebrate those qualities we share in common, but also those things that make us different, because it's the differences that keep life interesting.

---

### Post by VMC on 2019-05-03
> **DuckHook said:**
> I get QIII's point, but, to be fair, "converted" could simply be used in a descriptive sense as in "I converted my Euros to Dollars".

I too "converted" my wife to Ubuntu, but in the purely descriptive sense.

This was my take on his comment.

---

### Post by bluemagoo on 2019-05-03
Why would I want Ubuntu to be like Windows???  I never get the point of these threads.  Also, as far as installing software, whats easier than 'sudo apt install...'?

---

