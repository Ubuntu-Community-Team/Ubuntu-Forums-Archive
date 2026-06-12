---
title: "Security For The Aspiring Software Developer"
date: 2011-04-20
forum: Security
---

### Post by Stisfa on 2011-04-20
I'll try to be as concise as possible in this, so I apologize in advance if this is long-winded for an "Absolute Beginner Talk" post.  Also, [[COLOR="DarkOrange"]this is the only[/COLOR]]("http://ubuntuforums.org/showthread.php?t=645229") similar topic I found concerning this, but it doesn't really address what I have in mind, not specifically (that and I'm not in any position to be going "Independent", lol).  Despite alternation of keywords, I haven't had any relevant hits, so if my thread is a duplicate, I apologize in advance

I've been using Linux-based tools for roughly a year for various troubleshooting scenarios, as I'm coming from a Tech Support background.  I've had excellent experiences with ONTPRE, DBAN, Memtest86+ and many distros for whenever I needed to manipulate Windows according to my will :mrgreen:.  The thing is, despite all the power afforded to me by this Unix-inspired wonder, I've had trouble trying to integrate it into my regular, personal computing.  I realize why now: it's a **complete paradigm shift from Windows**.  That's why it's taken me several months to pour over the documentation before I could feel confident in approaching the community here concerning the topic at hand.

In trying to learn programming, for both the sake of personal satisfaction and secular application, I've discovered that everything makes more sense by using Linux (svn, Python, CLI, Vim, etc).  To illustrate, [[COLOR="DarkOrange"]Open Hatch's Training Missions[/COLOR]]("http://openhatch.org/missions/") are easier to work with when using Linux.  That's not to say it can't be done in Windows, it's just that the concept of "tar", "diff" and "patch" are quite native in Linux, unlike Windows.  Unfortunately, I have a penchant for exercising meticulous caution with new software, which prohibits me from making any productive use of it within the first few months of adoption.  That's why I wanted to ask about appropriate security measures for an aspiring programmer, this way I can accelerate my education.

My main goal is to have a localized development platform, not a full-blown server (the learning curve for becoming a Linux SysAdmin seems completely vertical from where I stand, lol).  I primarily need to have secure internet access for research, library lookup, the occasional Package download and svn interaction.  I also intend to use Ubuntu for general use, so that's another thing to take into consideration.  Below, I've compiled a list of what I currently understand to be appropriate for my security needs, if the community would be so kind to review it:

[LIST=1]
[*]**Acknowledgment That Perfect Security Doesn't Exist**
[*]**Common Sense & Practice** (For Combating Social Engineering & Associated/Similar Risks - For The Especially Worried, Exhibiting Paranoia And Suspicion, à la [[COLOR="DarkOrange"]Liar Game[/COLOR]]("http://en.wikipedia.org/wiki/Liar_Game"), Is Helpful)
[*]**Continued Education & Feedback** (bodhi.zazen's Posts Being A Good Place To Start & Respectful Use Of The Forums)
[*]Strong [s]Passwords[/s] Passphrases Coupled With File Encryption (Regularly Changed Too - KeePass Is Beautiful For This)
[*]Limited Use Of "sudo"
[*]Updates
[*]Backups (Onsite & Offsite)
[*]Leave Default Network Settings Alone (Unless You're A CCNA Security Tech - Only Halfway Joking)
[*]Protect The Hardware (Theft/Magnets/Water/Pets/Dust)
[*] Careful With Software!
[LIST]
[*]Use Trusted Repositories/Commands (If In Doubt, Verify)
[*]Avoid The Shiny, New, UNTESTED, UNSTRESSED, YET-TO-BE-ABUSED Things
[*]Server Software Demands Server-Type Security
[*]Employ Secure Browsing Practices & Tools
[*]Don't Bother With AV/RootKit Scanners (Possibility Of Increased Exposure To Threats & False Positives - Better To Spend Time Working With Encryption Technologies)
[/LIST]
[/LIST]

Please let me know if I'm missing anything that's vital to somebody in my circumstances.  I do understand that there are several esoteric means of securing a Linux distro, many of which are superbly effective, such as Kernel Hardening, but I'm not looking to pull all nighters for OpenBSD-quality security (overkill for my immediate needs, at least from my perspective).  To put it another way, Linux, and by extension, Ubuntu, can be secured to withstand all sorts of threats, but poor implementation and execution due to a thin spread of my mental resources would undermine the entire point, so I'd like to keep it focused towards a new user who has an inferiority complex laced with fear of the unknown ;).

I've got some specific questions that draw on the list above, but I'll reserve those for another thread or after I get some responses in this thread; let me know how you'd prefer to see the questions brought out.

---

### Post by HermanAB on 2011-04-20
Dude, relax and enjoy your Linux system.

---

### Post by Stisfa on 2011-04-20
> **HermanAB said:**
> Dude, relax and enjoy your Linux system.

I'm actually *more* worried since you've said that :P

Sorry, but I would like a little more elaboration, if you would, please?  Is the list overkill?  What specifically am I over-emphasizing?  Maybe I should be taking up my specific inquiries to the Security forum right about now?  Or should I head to IRC?

Unfortunately for me, I've unwittingly inherited a Python mentality (an implicit answer is difficult to work with, so an explicit and direct answer, with simplicity would be much appreciated).  Or maybe it's just refined my pre-existing affinity for worrying...;)

---

### Post by samalex on 2011-04-20
As someone also who's getting more into programming I can tell you Linux is the best platform for it as you have a wide variety of languages and IDE's at your disposal with little to zero financial overhead.  Plus most of the code you write is portable and will work on other platforms, unlike code written in Apple XCode or Microsoft Visual Studio.  As for having an all in one development box you can do that on pretty much any OS, but it is MUCH easier on Linux, IMO anyway.

As for security, you need to focus on learning the language(s) first and security and best practices will come in time.  You can read all the security notices you want about a particular language, but if you don't have a concrete understanding on how that language works and is used it's not helping you much.  

But given security seems to be your focus, I suggest checking out SELinux which is a security package for Linux that can help secure most items on the box.  FLOSS Weekly interviewed the author of SELinux on their Podcast a month or so ago - [http://twit.tv/floss156](http://twit.tv/floss156) - so check this out as well.

You mentioned OpenBSD which is known for its security, but securing an operating system, application, and even a website are each quite different beasts.  This goes back to what I said about learning a language, inside and out, then picking up the security best practices after the fact.

Hope this helps --

Sam

---

### Post by rookcifer on 2011-04-20
OP, there should be no extra security requirements just because you plan on developing on the machine.  Now, secure coding practices is another issue.

---

### Post by Stisfa on 2011-04-20
Thanks for the replies samalex & rookcifer!

> **rookcifer said:**
> OP, there should be no extra security requirements just because you plan on developing on the machine.  Now, secure coding practices is another issue.

Ah yes, "avoid spaghetti code because it opens up security holes the size of a barn"; I completely agree.  Don't worry, I won't be harassing you about *developing* security protocols/measures, not until I finish  reading _Programming Pearls_, _Code Complete_, _The Pragmatic Programmer_ and _Structure and Interpretation of Computer Programs_.  In line with those, I guess it would be appropriate for me to review _The Art of Computer Programming_ series by our good friend Mr. Knuth; I know this isn't directly related to security, but if I'm ever in the need to ask questions about secure programming, at least I won't be speaking a different language and thus avoid this face: :confused:

So don't worry, I'll keep the "secure coding practice" questions away from here; besides, I've got StackOverflow for those type of questions.

---

### Post by HermanAB on 2011-04-21
Howdy

You only need to get really concerned about security once you run a server that is actually listening on the net.  So if you are developing web sites, make sure that you understand Apache security and so on.

For general use, don't worry too much about security, just ensure that you always use proper looooooong passwords of 9 or more characters and you will be OK, since the default configuration of Ubuntu is pretty strong.

Please stay away from SELinux on Ubuntu, since it is mainly a RedHat thing.  Ubuntu uses App Armor.  If you deploy SELinux on Ubuntu, *nothing* will work and you will be in for a world of hurt to get it to work again.  However, even App Armor is best left till later when you know more about Ubuntu and you have nothing better to do for a few days.

---

### Post by Stisfa on 2011-04-21
> **HermanAB said:**
> Howdy

You only need to get really concerned about security once you run a server that is actually listening on the net.  So if you are developing web sites, make sure that you understand Apache security and so on.

For general use, don't worry too much about security, just ensure that you always use proper looooooong passwords of 9 or more characters and you will be OK, since the default configuration of Ubuntu is pretty strong.

Please stay away from SELinux on Ubuntu, since it is mainly a RedHat thing.  Ubuntu uses App Armor.  If you deploy SELinux on Ubuntu, *nothing* will work and you will be in for a world of hurt to get it to work again.  However, even App Armor is best left till later when you know more about Ubuntu and you have nothing better to do for a few days.

Thanks for the reply HermanAB!

Also, thanks for addressing Apache, since I was intending to develop PHP on my laptop.  I'll post my questions about the LAMP stack in the appropriate forum, but you basically covered my main concern: would the LAMP setup open up the ports that Ubuntu closes by default?  At least now I know that I need to learn how to configure it to route only to the local host.

I did review some of the material on AppArmor and Hosts files, so I will eventually get to those; thanks for keeping me away from SELinux, since I would have accidentally followed it that way.

By the by, I disagree with you on long passwords; I prefer "looooooong" **passphrases** to properly defend against Dictionary Attacks and Rainbow Tables (I know, it's semantics, but I couldn't help it, now that I'm finally relaxing, lol ;-))

---

