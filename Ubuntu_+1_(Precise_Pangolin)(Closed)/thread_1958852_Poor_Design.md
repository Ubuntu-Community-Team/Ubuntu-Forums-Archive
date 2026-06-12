---
title: "Poor Design"
date: 2012-04-15
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by longbeard on 2012-04-15
<snip>

Can I please have a Firefox with the command menues? Thank you!

---

### Post by zombifier25 on 2012-04-15
umm the application menu is on the very top panel of the screen (also called as the Global Menu, like the one from Mac OSX)
But you are right; the menus are too hideous for new users.

---

### Post by santosh83 on 2012-04-15
> **longbeard said:**
> 

Can I please have a Firefox with the command menues? Thank you!

Hi longbeard,

I think if you're using Firefox under the Unity desktop, you will find it's menu on the top panel.

---

### Post by alphacrucis2 on 2012-04-15
> **santosh83 said:**
> Hi longbeard,

I think if you're using Firefox under the Unity desktop, you will find it's menu on the top panel.

Maybe he hasn't realised that you have to move the mouse over it before the menu appears.

---

### Post by dcstar on 2012-04-15
> **alphacrucis2 said:**
> Maybe he hasn't realised that you have to move the mouse over it before the menu appears.

What!?!, something changes from the way its been done for almost 20 years and the users are supposed to know about it intuitively......

That's the trouble with most people, they just can't read the minds of the people who foist a new interface on them very well - I guess these backward people need an upgrade too.....

The answer is that you now have to move your mouse pointer way past where the actual active window is to the top of the screen to now access those menus that used to be in a logical and convenient position - all for the sake of saving a few pixels on the small touchscreens that Unity was designed for.

Welcome to the future where the mouse and keyboard desktop is now the second-class citizen compared to touchscreen features.

---

### Post by sgage on 2012-04-15
> **dcstar said:**
> What!?!, something changes from the way its been done for almost 20 years and the users are supposed to know about it intuitively......

That's the trouble with most people, they just can't read the minds of the people who foist a new interface on them very well - I guess these backward people need an upgrade too.....

The answer is that you now have to move your mouse pointer way past where the actual active window is to the top of the screen to now access those menus that used to be in a logical and convenient position - all for the sake of saving a few pixels on the small touchscreens that Unity was designed for.

Welcome to the future where the mouse and keyboard desktop is now the second-class citizen compared to touchscreen features.

It is possible to put the menus back where they belong (IMO):

sudo apt-get remove firefox-globalmenu

sudo apt-get remove thunderbird-globalmenu

Or, to get rid of global menus, um, globally:

sudo apt-get remove indicator-appmenu

---

### Post by craig10x on 2012-04-15
While making fun of the new "global menu" what you guys didn't point out (and he probably didn't notice) is that it's ADVANTAGE is you get extra "REAL ESTATE" space on your web browser by having it...Without it, you'd have an extra panel on top which takes up unnecessary space...

I happen to LOVE having the global menu myself...i think eventually they will offer the option of turning it off, but i hope they never remove it altogether as i would NOT like to NOT have it available to use...

---

### Post by kuvanito on 2012-04-15
the whole thing is designed with small screens in mind,perhaps ubuntu's tablet or Smartphones and it does serve it's purpose BUT i run Ubu on my main machine which happens to be my BIG desktop with a 26" screen and i do not like the Global Menus.I've never been a fun of the whole global menu thing but this makes me happy and so it should make every one esle happy too: 

sudo apt-get remove firefox-globalmenu
sudo apt-get remove thunderbird-globalmenu
sudo apt-get remove indicator-appmenu

---

### Post by Perryg on 2012-04-15
Simply disable the Global menu bar intergration extension in the FF preferences. Then you can bring it back if you like. Seems better than purging various packages.

---

### Post by cariboo on 2012-04-15
Instead of suggesting ways to disable parts of Unity, we should be working on a way to inform those users that don't keep up with computer news, and have no idea of how much a change the desktop has gone through since Lucid was released. The original post by longbeard that has since been edited, was pretty disrespectful to everyone.

We will be running into this type of post more often, when Precise is released, we need to come up with a better way to help users transition from Lucid to Precise, without having them remove packages, or pass on our own personal biases

In my opinion, Precise is going to be a darn good release, and we should speak positively about it. If someone transitioning from Lucid is willing to give Unity a try, why not point them to keithpeter's excellent but still in progress [poster]("http://ubuntuforums.org/showthread.php?t=1955365"), and if they want a more familiar desktop environment, point them to[ kansasnoob's  gnome-classic megathread]("http://ubuntuforums.org/showthread.php?t=1873765&highlight=gnome-classic"). You can also suggest to them the many other alternatives available to them.

It's is up to us to help LTS users make the transition as painless as possible, so let's keep the drama out of it, and actually help them.

---

### Post by buzzingrobot on 2012-04-15
Three gentle points:

1. The negative reactions to Unity and Gnome 3 are evidence of a lot of conservatism in the Linux community.  Given all the emphasis on 'choice', that's surprising. We should not consider that Gnome 2 solved the interface problem.  I'm liking Unity a lot more than I thought I would and I applaud the Ubuntu team for having the desire and the ability to innovate.

2. Apple has put all application menus in the menu bar for years, before OS X and long before phones and tablets were even a notion.  Moving them there is not solely a response to small screens.  (Remember, too, that the first Macs had 9-inch screens with considerably fewer pixels than an iPhone or iPad.)

3. When Apple released Lion, they included in the install routine an explanation of the things that had changed from Snow Leopard.  Perhaps, if there is time before the release, a similar display might be included at the end of the 12.04 install.  Putting something on the web and then calling the user's attention to it immediately after the first post-install reboot might work.

---

### Post by sgage on 2012-04-15
> **cariboo907 said:**
> Instead of suggesting ways to disable parts of Unity, we should be working on a way to inform those users that don't keep up with computer news, and have no idea of how much a change the desktop has gone through since Lucid was released. The original post by longbeard that has since been edited, was pretty disrespectful to everyone.

We will be running into this type of post more often, when Precise is released, we need to come up with a better way to help users transition from Lucid to Precise, without having them remove packages, or pass on our own personal biases

In my opinion, Precise is going to be a darn good release, and we should speak positively about it. If someone transitioning from Lucid is willing to give Unity a try, why not point them to keithpeter's excellent but still in progress [poster]("http://ubuntuforums.org/showthread.php?t=1955365"), and if they want a more familiar desktop environment, point them to[ kansasnoob's  gnome-classic megathread]("http://ubuntuforums.org/showthread.php?t=1873765&highlight=gnome-classic"). You can also suggest to them the many other alternatives available to them.

It's is up to us to help LTS users make the transition as painless as possible, so let's keep the drama out of it, and actually help them.

No drama here, just practicality. I see nothing wrong with disabling global menus, or showing someone else how to. It might keep people in the Ubuntu fold who would otherwise jump ship. 

There are people who have tried hard and in good faith to work with and get used to the new features, and decided it just doesn't work for them. This probably especially true for desktop users. I'm one of those people, and I don't like the issue being framed as one of being behind the times or pushing my biases or, my favorite (NOT): being afraid of change. This is what is truly insulting, IMO.

For my applications and way of working, global menus are absurd. Especially ones that disappear when you aren't mousing over them. But we've been all over this and some other issues, and I don't want to bring it up again. I just want to point out that there are legitimate reasons for wanting to disable some of these things.

---

### Post by 3rdalbum on 2012-04-15
Yes, a part of the user interface that requires a "hover over" is designed solely for use with touchscreens.

Wait...

Let's have a look at a maximised window on Gnome 2. You've got the top panel, then the window's titlebar, then the window's menu, then the window content. Then at the bottom you have another panel.

On a widescreen monitor you've lost a significant portion of the available vertical space.

With Unity, you have one top panel which also doubles as the menubar. I don't care if you've got a 32-inch computer monitor, it's still convenient to be able to see more of your content.

I use Unity on a 10 inch netbook and a 22 inch desktop monitor, and I **prefer** it on the 22 inch monitor. Although, it works well on the 10 inch netbook screen. The difference in usability isn't as big as it was in Gnome 2.

I'd agree with an earlier poster that we should educate users on the differences, not on "here's how to remove things".

---

### Post by sgage on 2012-04-15
> **buzzingrobot said:**
> Three gentle points:

1. The negative reactions to Unity and Gnome 3 are evidence of a lot of conservatism in the Linux community.  Given all the emphasis on 'choice', that's surprising. We should not consider that Gnome 2 solved the interface problem.  I'm liking Unity a lot more than I thought I would and I applaud the Ubuntu team for having the desire and the ability to innovate.

2. Apple has put all application menus in the menu bar for years, before OS X and long before phones and tablets were even a notion.  Moving them there is not solely a response to small screens.  (Remember, too, that the first Macs had 9-inch screens with considerably fewer pixels than an iPhone or iPad.)

3. When Apple released Lion, they included in the install routine an explanation of the things that had changed from Snow Leopard.  Perhaps, if there is time, a similar display might be included at the end of the 12.04 install.  Putting something on the web and then calling the user's attention to it immediately after the first post-install reboot might work.

1. Not conservatism, but rather concern with usability.

2. That Apple has had global menus for a long time is no justification for them.

3. I am extremely aware of where everything is and how it works in Unity. I've been testing it for a long time all through its development. It's not that it's new and different, it's that I can't work efficiently with it. That's all.

---

### Post by Perryg on 2012-04-15
Wow.  I can appreciate the LTS users wanting to retain some similarity to what they were used to. What is the point of not sharing information on configuration preferences? After all it is there for a purpose, or are you suggesting that the only way to use Ubuntu is out of the box and no other way? That doesn't sound like the Ubuntu I have come to know and use.

---

### Post by sgage on 2012-04-15
> **3rdalbum said:**
> I use Unity on a 10 inch netbook and a 22 inch desktop monitor, and I **prefer** it on the 22 inch monitor.

And I **don't** prefer it, by a wide margin. If you are running a small display with maximized windows, it makes some sort of sense (though having it disappear is bizarre and anti-ergonomic).

---

### Post by craig10x on 2012-04-15
sgage...my desktop is toshiba 17 inch (widescreen) desktop (bought about 6 months ago) with 900x1600 resolution and I think the global menu is great...i love having the extra space when i am web browsing...to me, an extra panel on top is just a waste of space and doesn't even look as nice...I'd still prefer it, even if i was running a 20 or 22 inch monitor...as far as i am concerned, the more web page space..the BETTER...

so, while you may prefer no global menu...many of us do appreciate it...they should have the option of switching it off...but i sure wouldn't want them to eliminate it...

when i had a short run with Macs (after leaving windows and before discovering linux) i really appreciated the idea of the global menu and was glad to see ubuntu carry it over into unity (along with the doc style launcher)....of course, this should be explained to newbies to unity as they may not be familiar with it...i like the suggestion of having a default webpage when you install with a guide to unity's features that make it different from what they are probably use to...

only thing i would like to see is the option (from ubuntu) of placing the unity bar on bottom (with a smaller width because it would be too wide on the wide screen which many of us have these days)...

but i don't really mind too much having it on the left...though that particular option would be nice if they would offer it... ;)

---

### Post by Gregory Lee on 2012-04-15
> **cariboo907 said:**
> You can also suggest to them the many other alternatives available to them.

You mean like the alternative shells/logins Gnome 3, Gnome Classic, XFCE, KDE, Windowmaker, which don't have global menus?  Good idea.  I posted about the KDE interface a few days ago, but my post was just moved away.  Can we really talk about alternatives to Unity?

---

### Post by sgage on 2012-04-15
> **craig10x said:**
> sgage...my desktop is toshiba 17 inch (widescreen) desktop (bought about 6 months ago) with 900x1600 resolution and I think the global menu is great...i love having the extra space when i am web browsing...to me, an extra panel on top is just a waste of space and doesn't even look as nice...I'd still prefer it, even if i was running a 20 or 22 inch monitor...as far as i am concerned, the more web page space..the BETTER...

so, while you may prefer no global menu...many of us do appreciate it...they should have the option of switching it off...but i sure wouldn't want them to eliminate it...

when i had a short run with Macs (after leaving windows and before discovering linux) i really appreciated the idea of the global menu and was glad to see ubuntu carry it over into unity (along with the doc style launcher)....of course, this should be explained to newbies to unity as they may not be familiar with it...i like the suggestion of having a defaault webpage when you install with a guide to unity's features that make it different from what they are probably use to...

only thing i would like to see is the option (from ubuntu) of placing the unity bar on bottom (with a smaller width because it would be too wide on the wide screen which many of us have these days)...

but i don't really mind too much having it on the left...though that particular option would be nice if they would offer it... ;)

Well, we have different preferences is all I can say. I don't like global menus - for that matter, I don't much like Macs :KS

And that's the point. One size does not fit all. 

But its moot, really. Even with the global menus turned off and the overlay scrollbars disabled and some tweaks to Unity behavior, I just can't warm up to it. At least Gnome Shell I can work with.

---

### Post by Simian Man on 2012-04-15
Am I the only one who thinks that regular programmers who just casually make things the way they want come up with significantly better interfaces than "design experts" who spend all their time coming up with things like this?

---

### Post by Morbius1 on 2012-04-15
> 2. Apple has put all application menus in the menu bar for years, before  OS X and long before phones and tablets were even a notion.  Moving  them there is not solely a response to small screens.  (Remember, too,  that the first Macs had 9-inch screens with considerably fewer pixels  than an iPhone or iPad.)Please don't compare the global menu in OSX to the global menu in Ubuntu. 

There is in fact a global menu on OSX and it is always visible changing whenever a different application gains focus. The global menu in Ubuntu is not seen until someone hovers over it with a mouse. 

It would I suspect confuse even an Apple user.

---

### Post by JHCKX on 2012-04-15
> **buzzingrobot said:**
> Three gentle points:

1. The negative reactions to Unity and Gnome 3 are evidence of a lot of conservatism in the Linux community.  Given all the emphasis on 'choice', that's surprising. We should not consider that Gnome 2 solved the interface problem.  I'm liking Unity a lot more than I thought I would and I applaud the Ubuntu team for having the desire and the ability to innovate.
I don't think anyone willing to give any flavour of Linux can be called "conservative", surely you're joking? What people are concerned about is usablity. I'm willing to give something new a shot but there has to be an advantage for me, the pros have to outweigh the cons. So far Unity just doesn't fit the bill, at least for me. 

But at least to me Unity doesn't seem innovative. It reminds me an awful lot of the Microsoft Office 97 shortcut bar. That was a fairly decent program launcher, used autohide but better and smoother than Unity. It was easier to configure too, you could add a program group, then place shortcuts in appropriate folders.

@sgage thanks for the tip on how to disable the global menus, they bugged me too, bad idea. I'm giving Unity another shot but I'm still not liking the experience. Autohide doesn't work reliably and I can't figure out how to turn it off. I thought you could just right-click the dash and select properties but that's not working (maybe because I'm using Unity 2D). I did like the original netbook remix and still use it with 10.04 on an acer one. Ironically, I'll probably replace it with 12.04 and gnome-fallback.

---

### Post by VeeDubb on 2012-04-15
> **buzzingrobot said:**
> Three gentle points:

1. The negative reactions to Unity and Gnome 3 are evidence of a lot of conservatism in the Linux community.  Given all the emphasis on 'choice', that's surprising. We should not consider that Gnome 2 solved the interface problem.  I'm liking Unity a lot more than I thought I would and I applaud the Ubuntu team for having the desire and the ability to innovate.

2. Apple has put all application menus in the menu bar for years, before OS X and long before phones and tablets were even a notion.  Moving them there is not solely a response to small screens.  (Remember, too, that the first Macs had 9-inch screens with considerably fewer pixels than an iPhone or iPad.)

3. When Apple released Lion, they included in the install routine an explanation of the things that had changed from Snow Leopard.  Perhaps, if there is time before the release, a similar display might be included at the end of the 12.04 install.  Putting something on the web and then calling the user's attention to it immediately after the first post-install reboot might work.

> **sgage said:**
> 1. Not conservatism, but rather concern with usability.

2. That Apple has had global menus for a long time is no justification for them.

3. I am extremely aware of where everything is and how it works in Unity. I've been testing it for a long time all through its development. It's not that it's new and different, it's that I can't work efficiently with it. That's all.

1. I think it's more a matter of human nature.  People want choice, but what they want more than choice is consistency and that 'their choice' remain immediately accessible while they have the illusion of other options they don't really care about.  People just want their computer to work the way they expect it to.  That's why mac is slowly gaining ground and linux has become so much more UI centric over the last decade.

2. I agree that Mac doing or not doing something is almost entirely irrelevant, but the simple fact of the matter is that it saves vertical screen real estate, which is a big plus for almost everyone in the days of widescreen monitors and high resolution applications.  When an application is maximized, the menus are in the exact same place relative to the content of the application that they were always in.  You just don't have wasted pixels sitting in another bar above or below the application.

3.  I agree completely with BR on this one.  If such a screen was correctly designed and included in the install process, it would help a great deal.  The usability of Unity is at least as great as gnome-panels, but it is such a major departure that many people won't be able to work efficiently with it until they relearn the interface.  Given that Ubuntu (and every other major distro today) is so heavily UI centric, such a massive UI overhaul is equivalent to switching from Windows to Mac.  Obviously, this is especially true for LTS-LTS users.  Anything that can be done to get even a few people started on the right track would be a big help.

---

### Post by Gregory Lee on 2012-04-15
Yes, people want choice, uniformity, ease of use, tradition, and all sorts of things.  But an important thing that a fair number of people want is the freedom to express their opinions, even when they are not totally in sync with the group think that some want to impose on them.  All these get-with-the-program calls for suppressing dissent are things we can very well do without, in my opinion.  I'm sure it's irritating to have people express disagreement, but you should just learn to put up with it.

---

### Post by sgage on 2012-04-15
Is it my imagination, or have several posts disappeared from this thread?

---

### Post by keithpeter on 2012-04-15
> **sgage said:**
> Is it my imagination, or have several posts disappeared from this thread?

[http://ubuntuforums.org/showthread.php?t=1959174](http://ubuntuforums.org/showthread.php?t=1959174)

Yes, I was a bit suprised about that. Must be the moderators but they usually say.

---

### Post by BwackNinja on 2012-04-15
> **buzzingrobot said:**
> Three gentle points:

1. The negative reactions to Unity and Gnome 3 are evidence of a lot of conservatism in the Linux community.  Given all the emphasis on 'choice', that's surprising. We should not consider that Gnome 2 solved the interface problem.  I'm liking Unity a lot more than I thought I would and I applaud the Ubuntu team for having the desire and the ability to innovate.

2. Apple has put all application menus in the menu bar for years, before OS X and long before phones and tablets were even a notion.  Moving them there is not solely a response to small screens.  (Remember, too, that the first Macs had 9-inch screens with considerably fewer pixels than an iPhone or iPad.)

3. When Apple released Lion, they included in the install routine an explanation of the things that had changed from Snow Leopard.  Perhaps, if there is time before the release, a similar display might be included at the end of the 12.04 install.  Putting something on the web and then calling the user's attention to it immediately after the first post-install reboot might work.

1. I agree, but that is reason for another interface to emerge, not a reason that everyone should use it. Unity (or Gnome-shell for that matter) isn't *bad*, its just that I personally don't care to use it.

2. You are missing the whole point of Apple putting the application menus on the top of the screen. The point is the difference between a window-based and an application-based system. The menus on OSX are *application* menu's, while in unity they are *window* menus. The separation only makes sense in an application-based environment like Apple has created because they are actions for the current application, not the current selected window.

3. Sounds good, but short of also telling them how to make the environment familiar again by running away from Unity, you're still making people who've become accustomed to the regular Gnome2 interface uncomfortable without giving them an escape, saying politely "this is the future, and this is how best to deal with it."


All this said, my gripes with Unity don't amount to a "Unity is bad," but the core aspects of the design are contrary to how I use my computer.

- Docks: I like to see the text of a window, and especially when I have a lot of windows of the same type open, I can easily go to it by remembering where it was on my taskbar or finding its name if I can't remember that. I don't like having to go two layers down instead of one to get to a window.

- Dash: Its cool, but despite my large amount of files, I have a well organized system and in the odd situation where I need to find something, the "locate" command can always back me up if the file isn't already in my recently used. I use a desktop right-click menu to access my programs and a hotkey for the terminal.

- Minimalism: Not talking about a lightweight set of applications (though I go for that too) but rather a lightweight look. I'm not a fan of large icons everywhere, I find them to be a poorer way of displaying information, especially because text is usually either absent or truncated.

- Compiz: While I can understand some of the technical advantages of Unity being a Compiz plugin, especially with its monolithic nature, it limits the style of desktop you have to all of Unity or none and the fact that Compiz has lost a lot of support outside of Unity is a rather sad situation. It is still my favorite window manager and the only one of its kind.



I say that new users might like or even love Unity, but coming from running Linux distros for as long as I have, I can't agree that people will see it and want to migrate to it, and the trend of Window Manager + Shell that's cropped up limits the classic "Linux way" of doing things where every piece is easily interchangeable and you configure it right, your system represents you, rather than some developers or designers visions.

---

### Post by sgage on 2012-04-15
> **keithpeter said:**
> [http://ubuntuforums.org/showthread.php?t=1959174](http://ubuntuforums.org/showthread.php?t=1959174)

Yes, I was a bit suprised about that. Must be the moderators but they usually say.

It's strange, because the posts that were removed were moving in quite a productive and useful direction, IMO. Oh well!

---

### Post by keithpeter on 2012-04-15
> **sgage said:**
> It's strange, because the posts that were removed were moving in quite a productive and useful direction, IMO. Oh well!

They have not been deleted, just split off in a new thread.

Keep thinking about the howto!

---

### Post by sgage on 2012-04-15
> **keithpeter said:**
> They have not been deleted, just split off in a new thread.

Keep thinking about the howto!

I see it now... I like the thread title. If I were to undertake writing a howto, where do you think my efforts would be best directed?

[edit: actually, I'll post this question over in the new thread.]

---

### Post by neu5eeCh on 2012-04-15
> **craig10x said:**
> While making fun of the new "global menu" what you guys didn't point out (and he probably didn't notice) is that it's ADVANTAGE is you get extra "REAL ESTATE" space on your web browser by having it...Without it, you'd have an extra panel on top which takes up unnecessary space...

That's not true. In the case of FF, a menu button substitutes for the menu. Using XFCE and the "maximize without borders" option (as opposed to F11), I get more real estate than with Unity. Unity does better than Gnome Shell or Cinnamon, but not XFCE or KDE.

---

### Post by keithpeter on 2012-04-15
> **sgage said:**
> I see it now... I like the thread title. If I were to undertake writing a howto, where do you think my efforts would be best directed?

Well effenberg0x0 put his list up at

[http://ubuntuforums.org/showpost.php?p=11846141&postcount=4](http://ubuntuforums.org/showpost.php?p=11846141&postcount=4)

and you have already posted the basic steps for removing the global menu at

[http://ubuntuforums.org/showpost.php?p=11845514&postcount=6](http://ubuntuforums.org/showpost.php?p=11845514&postcount=6)

I think that might be popular for people with very large displays. You might want to work up the steps a bit, have a look at

[http://ubuntuforums.org/showthread.php?t=677396](http://ubuntuforums.org/showthread.php?t=677396)

I think you might not need all of those steps, but a sentence or two at the beginning saying what skills are needed would help people decide if it was for them. 

effenberg0x0 is suggesting we forward stuff to him for incorporation in a wiki page.

Basically just have a bash.

---

### Post by rg4w on 2012-04-15
> **cariboo907 said:**
> Instead of suggesting ways to disable parts of Unity, we should be working on a way to inform those users that don't keep up with computer news..
Respectfully, we should not be dissuaded from calling out design mistakes as such.

Concealing the primary means of accessing an application's features runs so counter to the sum of usability research for the last 30 years - including some done at Canonical - that there appears to be no rationale for it other than that a key team member wanted it that way.

If that's how decisions are made, fine, but we need to be honest and willing to discuss that openly.

If instead there is an earnest desire to make Ubuntu the best OS possible, we will all want to employ rigorous research methods, and be willing to change the OS when the results may differ from where we thought we wanted to go.

Removing auto-hide behavior was an excellent example of such discipline, but it remains a mystery why the same principles that led to that removal were not also heeded with regard to the confusion which inevitably arises from hiding commands from the user.

---

### Post by sgage on 2012-04-15
> **keithpeter said:**
> Well effenberg0x0 put his list up at

[http://ubuntuforums.org/showpost.php?p=11846141&postcount=4](http://ubuntuforums.org/showpost.php?p=11846141&postcount=4)

and you have already posted the basic steps for removing the global menu at

[http://ubuntuforums.org/showpost.php?p=11845514&postcount=6](http://ubuntuforums.org/showpost.php?p=11845514&postcount=6)

I think that might be popular for people with very large displays. You might want to work up the steps a bit, have a look at

[http://ubuntuforums.org/showthread.php?t=677396](http://ubuntuforums.org/showthread.php?t=677396)

I think you might not need all of those steps, but a sentence or two at the beginning saying what skills are needed would help people decide if it was for them. 

effenberg0x0 is suggesting we forward stuff to him for incorporation in a wiki page.

Basically just have a bash.

I will have a go at it...

---

### Post by craig10x on 2012-04-15
@VtPoet:  but you see i don't use firefox...i am a Google Chrome guy ;)
Chrome doesn't have that option...so no global menu then extra panel would be on top (taking up unnecessary space)...

---

### Post by longbeard on 2012-04-16
> The original post by longbeard that has since been edited, was pretty disrespectful to everyone.I don't think my post was disrespectful, and certainly not to everyone. I tried to communicate my frustration with the new surface. Perhaps the content wasn't apt for this forum, which I understand, but it also were respectful of people not to invent defamatory stories in the absence of evidence.

> ..and I don't like the issue being framed as one of being behind the times or pushing my biases or, my favorite (NOT): being afraid of change. This is what is truly insulting, IMO.The surface issue is a true and I'm happy there is discussion about it. Since some time I observe the tendency towards reduced surfaces in the IT world. My summary there is that the attempt is good but the extension is often harmful. I believe user surfaces have "political" implications also. Democratic and liberal systems go well with and perhaps are tied to explicity. A reduced surface has the risk of screening out groups of people, or to be more precise, screening out their access to competence. So a reduced surface is always also an inexplicit surface in my eyes.

I see the pressure coming from small hardware, but there is no need to extend the consequences to a broad desktop environment. I prefer to have a clearly ordered access to functions instead of making guesswork about grafical symbols in all corners around the screen. Perhaps it is even respectless to offer something like that, I don't know .. I also understand elder people (who are always less flexible) when they give the box a kick finally because they don't understand it any more.

Dealing with Ubunto 12.04, up today I have no idea how to access the set of programs that come along with it. The top bar, now functional to programs, is not available any more for a system command menu. Where are the programs? I have to open installation vallet in order to understand what might be available on the system (but still can't access it). You may call me stupid, but this is the type of work someone has to undergo when confronted with this surface. What is the benefit?

I don't believe, or at least hope, that the reduced surfaces will survive on the desktop. It should be quite easy to implement an option for "traditional" users who enjoy a clear sight on things. I see no reason other than pressure group vanity, or perhaps lack of sensitivity, to press such a development onto users.

---

### Post by nothingspecial on 2012-04-16
> **keithpeter said:**
> [http://ubuntuforums.org/showthread.php?t=1959174](http://ubuntuforums.org/showthread.php?t=1959174)

Yes, I was a bit suprised about that. Must be the moderators but they usually say.

Sorry, that was me. And yes we are supposed to say.

I moved the posts to a new thread because they were indeed productive and worthy of a thread of their own rather than being buried in the middle of this one.

---

### Post by ikt on 2012-04-16
> **Simian Man said:**
> Am I the only one who thinks that regular programmers who just casually make things the way they want come up with significantly better interfaces than "design experts" who spend all their time coming up with things like this?

You'd be wrong, Apple is considered to have the best UI's in the world, and programmers most certainly don't design the UI for Apple.

---

### Post by rg4w on 2012-04-16
> **ikt said:**
> You'd be wrong, Apple is considered to have the best UI's in the world, and programmers most certainly don't design the UI for Apple.
The key difference between Apple's menu bar and Unity's is the subject of the OP:  Apple doesn't hide an app's commands from the user.

---

### Post by sgage on 2012-04-16
> **VTPoet said:**
> That's not true. In the case of FF, a menu button substitutes for the menu. Using XFCE and the "maximize without borders" option (as opposed to F11), I get more real estate than with Unity. Unity does better than Gnome Shell or Cinnamon, but not XFCE or KDE.

Besides which, many (most?) of us have plenty of screen "real estate". Again, for a small netbook or tablet, it makes sense. For a desktop with decent sized display, not so much.

---

### Post by buzzingrobot on 2012-04-16
> **sgage said:**
> 1. Not conservatism, but rather concern with usability.

2. That Apple has had global menus for a long time is no justification for them.

3. I am extremely aware of where everything is and how it works in Unity. I've been testing it for a long time all through its development. It's not that it's new and different, it's that I can't work efficiently with it. That's all.

1. Gnome 2 is an old design framed in a Win95 world, with the addition of what I think was an amateurish top panel. If it had solved the desktop problem once and for all, everyone would be using it.  Insistence on using it seems to me the essence of conservatism.  Questions about Unity's appeal aside, I like that Canonical is being innovative, rather than simply riffing on something Microsoft did, as was done in Gnome 2.

2.  Arguing with Ubuntu about the demise of Gnome 2 seems pointless.  The Gnome team killed it. It's unreasonable to expect Ubuntu, or anyone else, to continue to deploy and support a someone else's dead project.

3. The argument was made that Unity uses global menus to support tablets.  I pointed out that they've been around for decades.

4. With respect, I suspect that if people had used Unity for several years that when confronted by something like Gnome 2 they would be making the same complaints about lost efficiency.

5. Linux is all about choice, right?  Alternatives to Unity exist that mimic Gnome 2 on a modern base.  You can also run real Gnome 2 on Centos or Debian Stable if you're willing to use old software. Why not opt for those rather than argue that Canonical should let die-hard Gnome 2 users determine Ubuntu's path?

---

### Post by zolero on 2012-04-16
Well **buzzingrobot**...

although I agree that Linux is all about choices, these should be done with a sense of respect regarding usability, much more than being only eyecandy-addicted. As an example, just look at Nautilus' aspect in Lucid's Gnome2 and compare it for functionality with same apps' aspect in Precise.
Where is the toolbar with its useful buttons (hiding many necessary functions)? The "Up" button, "Copy", "Paste", Search box...? Instead we have two misplaced "Back" and "Forward" buttons. Is this useability would you mean...? Because I understand and agree with "all about choice" concept, but totally reject the loss of utilitarism and usefulness. In other words, I'd look to what sacrificing for what reason and results. Usability is and stays above the choices, man...!

---

### Post by cariboo on 2012-04-17
I don't understand why people have a hard time understanding what the issue is here. Ubuntu is a Gnome based distribution, for better or worse. Gnome no longer develops Gnome 2, so we are using the current version of Gnome, just like all the previous releases. Any complaints should be directed at the Gnome developers. The Ubuntu developers have added back quite a bit of functionality that isn't available when running Gnome-shell.

---

### Post by VeeDubb on 2012-04-17
> **buzzingrobot said:**
> 4. With respect, I suspect that if people had used Unity for several years that when confronted by something like Gnome 2 they would be making the same complaints about lost efficiency.


Very well put, and almost certainly true.

---

### Post by exploder on 2012-04-17
buzzingrobot, I really like what you wrote and completely agree with you. At this point in time Unity is very good and from what I have seen as far as what is in store for future releases things are only going to get better.

---

### Post by xzero1 on 2012-04-17
> **sgage said:**
> Besides which, many (most?) of us have plenty of screen "real estate". Again, for a small netbook or tablet, it makes sense. For a desktop with decent sized display, not so much.

If it makes sense on smaller displays and is at least workable on the desktop, then isn't that the point. That is why they call it  "Unity".

---

### Post by xzero1 on 2012-04-17
When using the unity side bar, when I open an app say a new terminal, by *default* instead of a new window I am re-directed to a previously opened window (terminal) even if that requires changing my current desktop. Is this by design? It seems to break the desktop metaphor. What is the reason for this design choice?

---

### Post by scaine on 2012-04-17
> **xzero1 said:**
> When using the unity side bar, when I open an app say a new terminal, by *default* instead of a new window I am re-directed to a previously opened window (terminal) even if that requires changing my current desktop. Is this by design? It seems to break the desktop metaphor. What is the reason for this design choice?

Yes, very much by design. If you want a new terminal, you have to right-click and choose "New Terminal". This doesn't bother me much - you get used it really, really quickly. What is nice about this behaviour is that if you have several terminals open, then your left-click will launch an Expose/Scale function for just those terminals. Probably a bad example, since they'll all likely look the same, but it's handy for multiple nautilus/firefox windows (although since they're both tabbed apps, the benefit is reduced anyway).

It does annoy me that there's no keyboard modifier to let you launch a new instance though. I'd like to be able to CTRL-leftclick on terminal to launch a new one.

---

### Post by scaine on 2012-04-17
Actually, I've just noticed that the Expose/scale effect is horribly broken if you have multiple windows on multiple workspaces. It just chooses one at random and flips you to that terminal. The ones on the other workspace are ignored.

Worse, clicking the button again only shows you the terminals on that workspace, implying that you don't have other terminals in other workspaces.

I'll check to see if there's a bug about this, but since the Ayatana (Unity-Design it's called now, I think) team seem to be trying to abandon workspaces in favour of a single-workspace controlled by Unity, perhaps this decision is by design too.

Best not jump to conclusions though. I'll check launchpad.

---

### Post by keithpeter on 2012-04-17
> **scaine said:**
> 
It does annoy me that there's no keyboard modifier to let you launch a new instance though. I'd like to be able to CTRL-leftclick on terminal to launch a new one.

I may have misunderstood the issue here, but I just use Ctrl-Alt-T to launch new terminals.

---

### Post by sgage on 2012-04-17
> **xzero1 said:**
> If it makes sense on smaller displays and is at least workable on the desktop, then isn't that the point. That is why they call it  "Unity".

I am not content with "at least workable". Whatever.

---

### Post by 3rdalbum on 2012-04-17
> **sgage said:**
> I am not content with "at least workable". Whatever.

1. Global Menus are a stop-gap measure until they work out how to implement menus better (than everyone else)

2. I don't have any trouble with them. It took me a couple of days to adapt. You flick your finger, the menus are shown - it becomes second nature.

3. On a widescreen monitor you have very little vertical space, which is only "workable" and not ideal. Unity makes the most of the space so you can actually see more of the document you are working with.

---

### Post by NHclimber on 2012-04-18
> **scaine said:**
> Yes, very much by design. If you want a new terminal, you have to right-click and choose "New Terminal". This doesn't bother me much - you get used it really, really quickly. What is nice about this behaviour is that if you have several terminals open, then your left-click will launch an Expose/Scale function for just those terminals. Probably a bad example, since they'll all likely look the same, but it's handy for multiple nautilus/firefox windows (although since they're both tabbed apps, the benefit is reduced anyway).

It does annoy me that there's no keyboard modifier to let you launch a new instance though. I'd like to be able to CTRL-leftclick on terminal to launch a new one.
My main gripe with Unity's interpretation of taskbar functionality (what you refer to as Expose/Scale) is that it brings to the foreground *all* of the (toplevel) windows of every instance -- there's no way to pick a particular toplevel window directly from the sidebar.

So when doing real work -- not just messing around with a single app -- where I might have 3~4 emacs windows (one of which is full-screen because it has the debugger in it), several terminal windows, a browser referencing multiple sites, switching to a different emacs window is really just painful. I am repeatedly manually restacking the window order. That's just poor.

---

### Post by wgarcia on 2012-04-18
@NHclimber, for the working flow you demand (similar to mine) i find Alt-tab, and arrow-down, a good way to access the window that I want.

---

### Post by NHclimber on 2012-04-18
> **wgarcia said:**
> @NHclimber, for the working flow you demand (similar to mine) i find Alt-tab, and arrow-down, a good way to access the window that I want.
Thanks for the pointer.

---

### Post by Krause on 2012-04-18
1 thing I didn't like about the global menu is how the middle mouse button doesn't work to open a folder of bookmarks like it does inside of Firefox's own bookmarks menu.

---

### Post by buzzingrobot on 2012-04-18
> **zolero said:**
> Well **buzzingrobot**...

although I agree that Linux is all about choices, these should be done with a sense of respect regarding usability, much more than being only eyecandy-addicted. As an example, just look at Nautilus' aspect in Lucid's Gnome2 and compare it for functionality with same apps' aspect in Precise.
Where is the toolbar with its useful buttons (hiding many necessary functions)? The "Up" button, "Copy", "Paste", Search box...? Instead we have two misplaced "Back" and "Forward" buttons. Is this useability would you mean...? Because I understand and agree with "all about choice" concept, but totally reject the loss of utilitarism and usefulness. In other words, I'd look to what sacrificing for what reason and results. Usability is and stays above the choices, man...!

It's time to stop throwing the eye-candy word at every UI change we don't like. To me, eye candy is extraneous art work thrown about in an amateurish attempt to pretty things up.  By that definition, I don't see eye candy in Unity or OS X.  (KDE, however, is a different matter.)

When I right click a file or directory name in Unity's Nautilus, I see at least 15 options. I can move around my file system and search with ease. 

Why are the arrows misplaced?  They're on top of a directory listing.  You can go back and you can go forward. The other location choices available for the arrows are bottom, left side, or right side.  How are those better?

But, to reiterate, Gnome 2 is dead and buried.  It's OK if someone thinks Gnome 2 solved every desktop UI problem for all time. I don't think it did, so I'm OK with people trying something new. I have to say, though, as someone who has been using Macs and Linux, together, at home for 15 years, and Windows at work, I've never had the problem of becoming so habituated to one way of doing things that I can't handle a little change.

---

### Post by mcellius on 2012-04-18
> But, to reiterate, Gnome 2 is dead and buried.  It's OK if someone  thinks Gnome 2 solved every desktop UI problem for all time. I don't  think it did, so I'm OK with people trying something new. I have to say,  though, as someone who has been using Macs and Linux, together, at home  for 15 years, and Windows at work, I've never had the problem of  becoming so habituated to one way of doing things that I can't handle a  little change.

I'm the same, and this has been the source of some of my confusion (as a relative n00b to Linux and Ubuntu) regarding the furor that arose with the introduction of Unity.  (The first version of Linux I used was Ubuntu 11.04.)

I used OS/2 back in the day, and used Stardock products (Object Desktop) to modify the desktop.  When I moved to Windows (sad day) I kept using Stardock products and made lots and lots of changes to the desktop.  I moved buttons, changed backgrounds and themes, created and deleted and moved taskbars and launchers and everything else, and really just learned to be comfortable with all of them.  Change desktops?  No big deal.  After all, the desktop is just a way to interact with the underlying OS: if things are moved or changed in appearance, I still know what's there and that I can still reach it.

But I do understand, too.  If one has devised an efficient way to work, moving things around can affect that efficiency, at least for awhile.  I enjoy the change, but can understand that not everyone does.  But I still don't understand all the heat surrounding the issue.

---

### Post by keithpeter on 2012-04-18
> **mcellius said:**
> If one has devised an efficient way to work, moving things around can affect that efficiency, at least for awhile.  I enjoy the change, but can understand that not everyone does.  But I still don't understand all the heat surrounding the issue.

Hello All

My computer day:

[LIST]
[*]Train on way to work: Make slides, export slides, suspend netbook.
[*]At work: E-mail, Intranet, Interactive Whiteboard software. Import slides, teach, export slides to Intranet. Word stuff. Swear at ribbon and the formula editor.
[*]Train on way home: Wake up netbook, do a handout for tomorrow's extra lesson. Suspend netbook.
[*]Home: Wake up netbook, Firefox to write this while cooking the pasta (it is my turn apparently). Dropbox syncs the documents.
[/LIST]
Total time interacting with the Desktop Graphical User Interface itself: Something like 5%?

---

### Post by mcellius on 2012-04-18
> Total time interacting with the Desktop Graphical User Interface itself: Something like 5%?

Yeah, that sounds about right for me, too.  No big whoop.

---

### Post by scaine on 2012-04-18
> **scaine said:**
> Actually, I've just noticed that the Expose/scale effect is horribly broken if you have multiple windows on multiple workspaces. It just chooses one at random and flips you to that terminal. The ones on the other workspace are ignored.

Worse, clicking the button again only shows you the terminals on that workspace, implying that you don't have other terminals in other workspaces.

I'll check to see if there's a bug about this, but since the Ayatana (Unity-Design it's called now, I think) team seem to be trying to abandon workspaces in favour of a single-workspace controlled by Unity, perhaps this decision is by design too.

Best not jump to conclusions though. I'll check launchpad.

Here's the bug - seems that Super-W behaviour is broken, which affects the behaviour when you click on the launcher button for multiple windows.

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/933776](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/933776)

---

