---
title: "GNU/Linux user interface rant"
date: 2005-11-08
forum: The Cafe
---

### Post by Navyblue on 2005-11-08
I'm not sure if these has been brought up before. But I've not heard anyone complaining this.

Well these are not a huge problem, but a nuisance IMO. Details like these are what contributes to pleasant user experience

**Firefox**
I'm sure all firefox user has experience this. The mouse cursor has to be placed at the correct part of the frame in order for the page to scroll. While other browser like IE is way less fussy in term of cursor placement.

**KDE**
Sometimes clicking on an icon would invoke the busy cursor, but the not actual program that the icon is suppose to activate. It really makes me wonder what is happening underneath the GUI.

There are already many complains on this one below, but I'll just give my share. :p

**Hardware setup GUI**
I have yet to see a distribution that has a fully functional GUI on hardware setup. The best I've seen is YaST2 from SUSE but the last time I am trying to configure dual head through GUI it doesn't work yet. Well you might argue that Linux is not for everyone. But why is it so hard to make a script that generate a proper xorg.conf? Why can't we have a fully working GUI for "dpkg-reconfigure xserver-xorg" command? IMO this is the greatest stumbling block for new user to switch to Linux.

Hopefully this doesn't turn into a flame thread. ;)

Just my rant, you are welcome to share yours too. :)

---

### Post by kairu0 on 2005-11-08
[QUOTE=Navyblue]
**Firefox**
I'm sure all firefox user has experience this. The mouse cursor has to be placed at the correct part of the frame in order for the page to scroll. While other browser like IE is way less fussy in term of cursor placement.
[/QUOTE]

A small annoyance, but I hear ya.

---

### Post by GeneralZod on 2005-11-08
> **Navyblue]

**Firefox**
I'm sure all firefox user has experience this. The mouse cursor has to be placed at the correct part of the frame in order for the page to scroll. While other browser like IE is way less fussy in term of cursor placement.
[/QUOTE]

I'm not fully sure what you mean, here - can you give a sample page and steps to reproduce? Oh, and as a nitpick - Firefox is neither a GNU nor a Linux program, per se - complaining on the Ubuntu forums will have limited results as it is out of hands! :)

[QUOTE=Navyblue]
**KDE**
Sometimes clicking on an icon would invoke the busy cursor, but the not actual program that the icon is suppose to activate. It really makes me wonder what is happening underneath the GUI.

There are already many complains on this one below, but I'll just give my share. :p
[/QUOTE]

This usually means that app has crashed or failed to start.  Try running the app from the command line and see if any errors are reported.

> 
**Hardware setup GUI**
I have yet to see a distribution that has a fully functional GUI on hardware setup. The best I've seen is YaST2 from SUSE but the last time I am trying to configure dual head through GUI it doesn't work yet. Well you might argue that Linux is not for everyone. But why is it so hard to make a script that generate a proper xorg.conf? Why can't we have a fully working GUI for "dpkg-reconfigure xserver-xorg" command? IMO this is the greatest stumbling block for new user to switch to Linux.


Yes, this would be nice.  But in answer to the question "But why is it so hard to make a script that generate a proper xorg.conf?" - between crappy drivers and hardware that misreports its capabilities (monitors are especially guilty of this), the problem is a very hard one indeed. 
Hopefully this doesn't turn into a flame thread.  said:**
> 
Just my rant, you are welcome to share yours too. :)

Just in case you are unaware, ranting on the forums does nothing to effect a solution to the problems - except perhaps that it relieves some of your stress ;) Aysiu has a characteristically excellent article on this, but I can't find it right now :)

---

### Post by RawMustard on 2005-11-08
> 
Aysiu has a characteristically excellent article on this, but I can't find it right now


Frankly I find that thread insulting to new Ubuntu users and it should be removed. It's a classic troll in itself!  Nothing to be proud of that's for sure!

---

### Post by zenwhen on 2005-11-08
[QUOTE=RawMustard]Frankly I find that thread insulting to new Ubuntu users and it should be removed. It's a classic troll in itself!  Nothing to be proud of that's for sure![/QUOTE]

That thread points out that too many users come here with bad attitudes posting rants instead of requests for help. This thread is not one of those really. 

The original poster here has a point. I too would like to have configured dual head without editing xorg.conf manually, but now that I have edited it, I never have to do it again.

PS: Please refrain from calling something a troll from now on without providing proof or some form of reasoning in the post in which you do so.

---

### Post by Brunellus on 2005-11-08
1) read the stuff in the sig, if you haven't already.

2) "great stumbling blocks to new users" depends greatly on what the new user is.  If the new user is my mother, who checks her e-mail and surfs the web for maybe 10 hours a week, total, linux is already ready.  If the new user is curious about computers, or generally enjoys messing with them and finding out how stuff works--it's been ready for quite some time.  But if the new user has all kinds of non-standard hardware quirks that *must work* on linux, well...linux isn't ready, and frankly, neither is the user.

---

### Post by Navyblue on 2005-11-08
[QUOTE=GeneralZod]I'm not fully sure what you mean, here - can you give a sample page and steps to reproduce? Oh, and as a nitpick - Firefox is neither a GNU nor a Linux program, per se - complaining on the Ubuntu forums will have limited results as it is out of hands! :)
[/QUOTE]

I can't provide you a sample page off the hand I think it happen most often on heavily framed page with large frames. To be frank, I don't have high aspiration to make firefox a better web browser for the whole mankind. Just want someone to hear my opinion. :p

[QUOTE=GeneralZod]This usually means that app has crashed or failed to start.  Try running the app from the command line and see if any errors are reported.
[/QUOTE]

What you said is probably true, it's kinda hard to find out whats wrong as it doesn't happen that often and I don't really have the habit of typing "firefox" at the Konsole to surf the web. :)

[QUOTE=GeneralZod]Yes, this would be nice.  But in answer to the question "But why is it so hard to make a script that generate a proper xorg.conf?" - between crappy drivers and hardware that misreports its capabilities (monitors are especially guilty of this), the problem is a very hard one indeed. 
[/QUOTE]

Yea hardware detection is a problem even in windows, but to write a working xorg.conf for dual head has nothing to do with driver and hardware reporting, at least there need to be a default mode, and if it doesn't work, YaST2 already have the mechanism to revert back the the previous setting.

[QUOTE=GeneralZod]Just in case you are unaware, ranting on the forums does nothing to effect a solution to the problems - except perhaps that it relieves some of your stress ;) Aysiu has a characteristically excellent article on this, but I can't find it right now :)[/QUOTE]

Yea I am in the midst of some stress on the area of PC right now :p. On one of my box openoffice2 cease to work for some reason and no one can answer me why it happens let alone how to fix it. On another box following the howto on changing the default cursor on firefox made X unable to start. I did exactly the same thing on the other box but it works perfect. And again no one can answer me why it happens and how to fix it. So in the midst of frustration and a tinge of boredom I started a thread like this. :p

As said, I am just ranting, and not trying to change the world. :)

---

### Post by earobinson on 2005-11-08
The firefox scrole thing is due to frames within a page and it is in my mind a feature

---

### Post by 23meg on 2005-11-08
[QUOTE=Navyblue]and I don't really have the habit of typing "firefox" at the Konsole to surf the web. [/QUOTE]

When you're not taking the slightest effort to try to at least narrow down a problem when it's so easy to do (type "firefox" in a terminal once a session for example), and mislabeling the problem as a GNU/Linux problem, you're indeed changing the world; you're spreading FUD about software that isn't GNU/Linux specific (as well as Firefox, X and and KDE aren't specific to GNU/Linux either), and thus GNU/Linux itself, and that doesn't do anyone any good. 

I'm not calling this trolling (neither has GeneralZod) but you should be aware that in the open source world solving a problem for yourself most likely means solving it for everyone else. If you're disturbed by a problem, can't solve it yourself and want it solved, please consider being more constructive; ask around to learn if it's really a problem (I feel your complaint about scrolling isn't actually a problem) and why it's happening, file a bug report, if nothing works, contact the developers directly, so on. And if you don't want to contribute this slightest bit, keep in mind that ranting about problems when you're not informed well enough isn't harmless.

---

### Post by Navyblue on 2005-11-08
> **23meg]When you're not taking the slightest effort to try to at least narrow down a problem when it's so easy to do (type "firefox" in a terminal once a session for example), and mislabeling the problem as a GNU/Linux problem, you're indeed changing the world said:**
> 

Ok guys, I mislabeled it, "GNU/Linux" is not an appropriate word to use, I can't think of a word to sum all these things up, and that was the closest I could think of. I stand corrected.

Hey, that is your assumption. I said I do not have the habit of typing "firefox" on Konsole does not mean that I have never done so. And I did.

Also, it does not confine to a single program. And it does not happen all the time. I have a life to live and do not have the time to start each program that I use for 100 times and just to look for an error message that happens only one in a blue moon.

[QUOTE=23meg]I'm not calling this trolling (neither has GeneralZod) but you should be aware that in the open source world solving a problem for yourself most likely means solving it for everyone else. If you're disturbed by a problem, can't solve it yourself and want it solved, please consider being more constructive; ask around to learn if it's really a problem (I feel your complaint about scrolling isn't actually a problem) and why it's happening, file a bug report, if nothing works, contact the developers directly, so on. And if you don't want to contribute this slightest bit, keep in mind that ranting about problems when you're not informed well enough isn't harmless.

As mentioned, I have a life to live. This is way too small for me to do so much (invoking every single program that you use in console for a gazillion times). And since I have not heard any complaint on this I guess it does not affect anyone much at all. Filing a bug report, contacting the developers and etc are noble acts, and I respect those who has done so.

What's up with you guys? You guys need to relax a bit. Next time I guess I need to hire a bunch of editors to audit my writing before posting anything. :confused:

Editted: I wish I get such amount and speed of reply on my problem thread. :p

---

### Post by 23meg on 2005-11-08
> What's up with you guys? You guys need to relax a bit.
As I said in my former post, I totally respect your wanting to just use the software and not debug it, all I'm saying is that it takes very little effort to help spot bugs, and if you don't even want to spare that little effort, you could still help by being careful as to where you point your finger. You could for example post your KDE problem in the appropriate forum section as a problem rather than rant about it in the community chat section; it would take the same amount of effort, and maybe your problem would have been solved by now.

> Editted: I wish I get such amount and speed of reply on my problem thread. 
If you already started a problem thread, why not give us the link so that we can take a look? Some threads do go unanswered at times even though they may be about widely known / easily solvable problems.

---

### Post by Navyblue on 2005-11-08
Cool... I'd really appreciate if anyone can help me with these :)

[http://www.ubuntuforums.org/showthread.php?p=473415](http://www.ubuntuforums.org/showthread.php?p=473415)

[http://www.ubuntuforums.org/showthread.php?t=80295&page=4](http://www.ubuntuforums.org/showthread.php?t=80295&page=4)

[http://ubuntuforums.org/showthread.php?p=472434](http://ubuntuforums.org/showthread.php?p=472434)

[http://ubuntuforums.org/showthread.php?t=80635](http://ubuntuforums.org/showthread.php?t=80635)

---

### Post by Navyblue on 2005-11-23
2 weeks has passed and only the author of Automatix replied. Thank you Arnieboy. Well, it seems clear to me now that certain topic are just more popular. ;)

---

### Post by 23meg on 2005-11-23
Just to let you know that I took a look at all your threads and did a few searches and some asking around as well, but unfortunately they were beyond my knowledge.

---

### Post by Navyblue on 2005-11-23
Thanks for the try and effort.  I'm glad that there is someone is reading them. :)

However, with Breezy I do think that I have two weird systems, They work alright with Hoary though.

---

### Post by joflow on 2005-11-23
In the windows version of Firefox, if you click in the url field...it will highlight the current url making it easy to type over or delete it.

Doesn't work in the linux version firefox.  You have to manually highlight the url or delete the url one character at a time.  Very annoying if you're used to the windows way like I am.

---

### Post by poptones on 2005-11-23
double-click...

---

### Post by GeneralZod on 2005-11-23
[QUOTE=poptones]double-click...[/QUOTE]

...or CTRL+L! :)

---

### Post by poptones on 2005-11-23
*I totally respect your wanting to just use the software and not debug it, all I'm saying is that it takes very little effort to help spot bugs*

You know why I don't submit bug reports? because the ubuntu bugzilla site is A PAIN IN THE ASS! This is also why I stopped working on the wiki - they are both encrypted AND they use voluminous chunks of text to do the simplest damn functions which makes them pretty much UNUSABLE VIA DIALUP. I just came from the ubuntu bugzilla site where I was going to contribute to the bug report on initrd not working with encrypted swaps - I think I may have a solution - but guess what? I gave up after like two minutes of waiting for the stupid damned page to load.

Why is the wiki encrypted? Why do I have to spend minutes waiting for ENCRYPTED pages to load simply to check on a bug in bugzilla? 

AAAGH! It's worse than trying to submit a listing to damn EBAY!

---

### Post by 23meg on 2005-11-23
[QUOTE=joflow]In the windows version of Firefox, if you click in the url field...it will highlight the current url making it easy to type over or delete it.

Doesn't work in the linux version firefox.  You have to manually highlight the url or delete the url one character at a time.  Very annoying if you're used to the windows way like I am.[/QUOTE]
It's tweakable; type about:config in the adress bar and change this value to true: browser.urlbar.clickSelectsAll.

---

### Post by 23meg on 2005-11-23
[QUOTE=poptones]*I totally respect your wanting to just use the software and not debug it, all I'm saying is that it takes very little effort to help spot bugs*

You know why I don't submit bug reports? because the ubuntu bugzilla site is A PAIN IN THE ASS! This is also why I stopped working on the wiki - they are both encrypted AND they use voluminous chunks of text to do the simplest damn functions which makes them pretty much UNUSABLE VIA DIALUP. I just came from the ubuntu bugzilla site where I was going to contribute to the bug report on initrd not working with encrypted swaps - I think I may have a solution - but guess what? I gave up after like two minutes of waiting for the stupid damned page to load.

Why is the wiki encrypted? Why do I have to spend minutes waiting for ENCRYPTED pages to load simply to check on a bug in bugzilla? 

AAAGH! It's worse than trying to submit a listing to damn EBAY![/QUOTE]I agree that it's sometimes a pain to wait for the pages to load, but it's got nothing to do with encryption. What's being loaded is the list of package names that you can type in in the "package" box. The list is preloaded so that you can be shown a list of similar package names as you type, and cannot enter an incorrect package name, which makes sense, but is slow.

This should be no excuse not to report bugs. You can for example pass your bugs to someone else with a faster connection for them to submit, or create a wikipage (maybe there already is one, do a search) where you dump your bugs to be submitted by others (under your name perhaps). On this page you can elaborate on why you created it, how slow it is to submit bugs on dialup, etc.

---

### Post by poptones on 2005-11-23
What about the wiki? Why is it also so slow? I am certain it is downloading voluminous text as I am on dialup and the traffic is quite easy to see.

And why does it HAVE to download that "package names" just for me to request a search? Making excuses about why it is how it is doesn't solve the problem - I am actually MOTIVATED to do this stuff, imagine how motivated a casual user is going to be to try a second time to "contribute."

This needs to be fixed, not excused. at the very least provide two user interfaces to the database.

---

### Post by 23meg on 2005-11-23
The wiki isn't slower than any other wiki in my experience.

The reason the package list is shown is that there are many packages with similar names, and you get suggestions as you type so that you will not accidentally enter an incorrect package name, thus removing the chance of developer time being wasted on errors in package names. Consider it as something like the bash auto complete feature. I'm not making excuses; I didn't choose and install this system, I'm merely explaining the idea behind it. 

I say a truly motivated user who truly wants to contribute *will* contribute anyhow.

---

### Post by poptones on 2005-11-23
OK fine then.. consider me no longer motivated.

---

### Post by Navyblue on 2005-11-23
[QUOTE=23meg]It's tweakable; type about:config in the adress bar and change this value to true: browser.urlbar.clickSelectsAll.[/QUOTE]

This one is cool, thanks for sharing. :)

---

### Post by 23meg on 2005-11-23
I'm sad to have taken away all your motivation with two posts. 

We've strayed way off topic in this already mislabeled thread.

---

### Post by joflow on 2005-11-23
[QUOTE=23meg]It's tweakable; type about:config in the adress bar and change this value to true: browser.urlbar.clickSelectsAll.[/QUOTE]

thanks

---

### Post by aysiu on 2005-11-23
Someone was alluding earlier to my "troll" thread, but I think this one is far more appropriate: [What's better than whining on the forums? Making a difference.](http://www.ubuntuforums.org/showthread.php?t=78741)

---

### Post by Navyblue on 2005-11-23
I see 4 options under the thread tools but none sounds like closing this thread. Yes I am logged in.

---

