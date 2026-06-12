---
title: "Once again on Ctrl+Alt+BackSp in Jaunty"
date: 2009-06-05
forum: The Cafe
---

### Post by skotos on 2009-06-05
Every time I reinstall the OS from scratch I forget this *dontzap* utility and I remember I have not installed it when I am in troubles with Gnome.. _*GRRRRR*_

I think that _by default disabling the *Ctrl-Alt-BackSp* keyboard sequence is a pretty annoying, unuseful and unrequested change_: those who don't know of it, simply do not need and do not use it, but those who need it, know about it and have been using it **for years**.

It should be enabled by default and manually disabled by those who do not want it: simply just the opposite of what it is now!

And.. oh.. *[Ctrl]+Alt+SysReq[+K]* does not work in my case where the old *Ctrl+Alt+BackSp* always did... 
And!... the *Ctrl+Alt+F[1..6]* does not work well _anymore_ as it did instead in the past: some really bad guy might suggest that it is another long, annoying but awaited upgrade feature or simply something that is going to soon disappear like the dinosaurs...

To recap, when I install Ubuntu I have now to remember 1 more thing: -***dontzap-***
Otherwise, when I have a problem (and I generally cannot plan on **when**) I will have to remember:

[LIST=1]
[*]the *Ctrl+Alt+SysRreq[+K]* sequence (not so difficult if it worked the same)
[*]the short developers *Alt+PrintScreen+R+S+E+I+N+U+B* sequence (simply I-M-P-O-S-S-I-B-L-E)
[/LIST]
Luckily enough I trust ext3 and I have some Windows experience: _**a power loss always makes a computer restart.**_

---

### Post by Kingsley on 2009-06-05
I'm pretty sure it's a default setting in X.org 1.6.

Just add this to /etc/X11/xorg.conf under Section "ServerFlags."
```
        Option  "DontZap"       "false"
```

---

### Post by monsterstack on 2009-06-05
Zapping is one of my favourite things to do. It's not really that much trouble enabling it, although I would prefer to have it by default.

---

### Post by frodon on 2009-06-05
Yep i put it back right after updating because i like Ctrl+Alt+Backspace, not a big deal to put it back really. As it concerns mainly advanced users it is not difficult for them to put back the Ctrl+Alt+Backspace ability, so it is a rather armless change and if it can prevents new user from mistakenly kill xserver then why not.

---

### Post by t0p on 2009-06-05
> **frodon said:**
> Yep i put it back right after updating because i like Ctrl+Alt+Backspace, not a big deal to put it back really. As it concerns mainly advanced users it is not difficult for them to put back the Ctrl+Alt+Backspace ability, so it is a rather armless change and if it can prevents new user from mistakenly kill xserver then why not.

Advanced?!  I'm not an "advanced user", but I am a frequent user of the Ctrl-Alt-Backspace combo.  For various reasons (not least Ubuntu's tendency to seize up).  I installed Jaunty on another machine just recently (I'm on my Hardy box right now) and I'd wondered why it wasn't working.  Far from being an "advanced user", I just this minute discovered how to enable Ctrl-Alt-Backspace from Kingsley's post (thanks Kingsley) - Yeah I can fix it when I get to my other box, but I'd like to know *why* this was necessary.  How often do  new users mistakenly kill X?  I don't think I *ever* did that mistakenly when I was a new user (which wasn't that long ago..)

</rant>

---

### Post by SunnyRabbiera on 2009-06-05
For me disabling it was a stupid idea, mainly because now if the system freezes out too bad, hit the reset button...
Its another reason I dislike jaunty and I hope its re enabled in Karmic

---

### Post by frodon on 2009-06-05
To be honest i nerver did the combo mistakenly too but i accept the idea that some did and they got confused getting X to close.
What i meant is that the users knowing that this combo exists will easily find how enable it again, so except the few minutes spent to search on internet this is not a real pain.

As for the reason behind this it is sure questionable, i don't feel this necessary personaly but since i can enable it again easily it's ok for me.

> **SunnyRabbiera said:**
> For me disabling it was a stupid idea, mainly because now if the system freezes out too bad, hit the reset button...
without the combo just Ctrl+Alt+F1 to go on virtual terminal and type "sudo /etc/init.d/gdm restart" to restart X (it is longer to do but it does the same).

---

### Post by SunnyRabbiera on 2009-06-05
But still manually editing xorg can be dangerous, after all messing with xorg is what causes a good percent of the issues with Ubuntu.
Thats why we need frontends, no manual configs needed or google searches.
The new user would want the OS to be cooperative if they get a freeze out so telling them to manually edit xorg and search around on google is not the best way to get a first impression.

> 
without the combo just Ctrl+Alt+F1 to go on virtual terminal and type "sudo /etc/init.d/gdm restart" to restart X (it is longer to do but it does the same).

Oh yes that will work when I cant even get my mouse to work during a freeze out.
Again manual configs should be a thing of the past in the near future.

---

### Post by Johnsie on 2009-06-05
Control-ALT-fx and backspace needs to be brought back RIGHT NOW!!!!!!!

If people don't want to use it then don't press those three buttons.

---

### Post by frodon on 2009-06-05
The best is to have no freeze so you don't need it, i hope it is the real goal behind this :)
The beginner getting a freeze don't know this combo anyway so it doesn't really matter in such case. If you dont want to play manually with xorg.conf which is really wise you can just use the "dontzap --disable" command line to enable it.
[http://www.ubuntu.com/getubuntu/releasenotes/904#Ctrl-Alt-Backspace%20disabled%20by%20default%20in%20Xorg](http://www.ubuntu.com/getubuntu/releasenotes/904#Ctrl-Alt-Backspace%20disabled%20by%20default%20in%20Xorg)

---

### Post by SunnyRabbiera on 2009-06-05
> **frodon said:**
> The best is to have no freeze so you don't need it, i hope it is the real goal behind this :)
The beginner getting a freeze don't know this combo anyway so it doesn't really matter in such case. If you dont want to play manually with xorg.conf which is really wise you can just use the "dontzap --disable" command line to enable it.
[http://www.ubuntu.com/getubuntu/releasenotes/904#Ctrl-Alt-Backspace%20disabled%20by%20default%20in%20Xorg](http://www.ubuntu.com/getubuntu/releasenotes/904#Ctrl-Alt-Backspace%20disabled%20by%20default%20in%20Xorg)

Yes but in the future we wont even need a command, we should be able to turn off or on the feature with the click of a mouse.

---

### Post by frodon on 2009-06-05
You mean something like a "Xserver preferences" GUI which would act on xorg.conf ?

That would be sweet.

---

### Post by open_coder on 2009-06-05
> **SunnyRabbiera said:**
> For me disabling it was a stupid idea, mainly because now if the system freezes out too bad, hit the reset button...
Its another reason I dislike jaunty and I hope its re enabled in Karmic

if it locks up to the point where you cant do ctrl-alt-f1, login and execute "sudo /etc/init.d/[g/k]dm restart", then i doubt youd be able to use ctrl-alt-bkspc

---

### Post by SunnyRabbiera on 2009-06-05
> **open_coder said:**
> if it locks up to the point where you cant do ctrl-alt-f1, login and execute "sudo /etc/init.d/[g/k]dm restart", then i doubt youd be able to use ctrl-alt-bkspc

Yes but ctrl+alt+backspace did get me out of many a pickle...

---

### Post by open_coder on 2009-06-05
> **SunnyRabbiera said:**
> Yes but ctrl+alt+backspace did get me out of many a pickle...

Yeah, it is definitely useful, but i can see why Canonical would disable it by default. I mean the users that need it would be able to turn it back on. I think this is funny b/c there used to be a bug where just pressing backspace would restart kdm.

---

### Post by kuja on 2009-06-05
It's definitely nice to have there when you need it, for the sorts of freezes that it will still rescue 
you from. Sometimes ctrl-alt=bksp will work when ctrl+alt+f[1-6] won't. In those cases it's nice to have, so I don't have to resort to alt+sysrq+R,E,I,S,U,B when ctrl+alt+bksp might work. Y'know? Of course, I've turned it back on for just such an occasion.

---

### Post by monsterstack on 2009-06-05
> **open_coder said:**
> if it locks up to the point where you cant do ctrl-alt-f1, login and execute "sudo /etc/init.d/[g/k]dm restart", then i doubt youd be able to use ctrl-alt-bkspc

Not so. I used some of the early Songbird builds. One of them was full of memory holes and the damned thing ended up trying to use thousands of megabytes of RAM. Response was there, but it was all incredibly slow. My mouse pointer lagged in its movement to the tune of four or five seconds. Tried opening a terminal to kill the process, but that didn't work. Logging into a shell to manually tell gdm to stop, or to kill the process would have been slow as hell. Ctrl-alt-backspace was nearly instantaneous. You can't seriously argue that logging into a shell to kill the display manager is the superior way of nuking your X session.

---

### Post by 3rdalbum on 2009-06-05
They should bring back zapping. If they're worried about Windows users accidentally killing their X server when all they want to do is look at their system monitor, maybe they should set the keyboard combination to "Control-Alt-Shift-Super-Backspace".

Then again, Control-Alt-Shift-Super-Backspace is probably the default keyboard combination for clearing fire paint in Compiz. :-P

---

### Post by 3rdalbum on 2009-06-05
^ What he said +1

(sorry... accidental double-post)

---

### Post by sim-value on 2009-06-05
Yay add it to Ubuquity as a Question and make the question so complicated that a new user will need to go to the forums to ask what this is :D

---

### Post by Kareeser on 2009-06-05
I believe two of the reasons why zapping was disabled was to cater to the Windows and emacs audience.

On laptops, bksp is close to del, which might be accidentally triggered. I call bull on this one, since Windows users are not accustomed to pressing ctrl-alt-del in *normal computer usage*. If they pressed ctrl-alt-del to bring up the task manager to shut off a crashing program, and they restart X, then I suppose that might be a problem.

Emacs also uses ctrl-alt shortcuts, so that's another user case.

I personally believe zapping should be opt-out, instead of opt-in.

---

### Post by RiceMonster on 2009-06-05
> **open_coder said:**
> Yeah, it is definitely useful, but i can see why Canonical would disable it by default. I mean the users that need it would be able to turn it back on. I think this is funny b/c there used to be a bug where just pressing backspace would restart kdm.

Cranonical didn't disable it; The Xorg devs did.

---

### Post by binbash on 2009-06-05
> **RiceMonster said:**
> Cranonical didn't disable it; The Xorg devs did.

Maybe but it is easy to enable it at default installation

---

### Post by deep64blue on 2009-06-05
Ubuntu is a distro for new users and those who just want to get on with things. Disabling ctl-alt-backsp is totally sensible for Ubuntu (but not for Fedora / Debian / Gentoo etc).

---

### Post by RiceMonster on 2009-06-05
> **deep64blue said:**
> Ubuntu is a distro for new users and those who just want to get on with things. Disabling ctl-alt-backsp is totally sensible for Ubuntu (but not for Fedora / Debian / Gentoo etc).

I don't understand how disabling that helps them "get on with things".

> **binbash said:**
> Maybe but it is easy to enable it at default installation

Yes I know, I was just saying it's default in Xorg 1.6

---

### Post by earthpigg on 2009-06-05
from the 9.04 [release notes]("http://www.ubuntu.com/getubuntu/releasenotes/904#Ctrl-Alt-Backspace%20disabled%20by%20default%20in%20Xorg"):

> The Ctrl-Alt-Backspace key combination to force a restart of X is now disabled by default, to eliminate the problem of accidentally triggering the key combination. Users who do want this function can enable it in their xorg.conf, or by running the command dontzap --disable. 

```
dontzap --disable
```
returned
```
The program 'dontzap' is currently not installed.  You can install it by typing:
sudo apt-get install dontzap
bash: dontzap: command not found
```

on both my laptop and my dell mini 9 netbook. laptop has a clean install of vanilla 9.04, netbook is upgraded from vanilla 8.10.

manually editing xorg.conf worked fine for both.

---

### Post by cariboo on 2009-06-05
> **open_coder said:**
> Yeah, it is definitely useful, but i can see why Canonical would disable it by default. I mean the users that need it would be able to turn it back on. I think this is funny b/c there used to be a bug where just pressing backspace would restart kdm.

Canonical had nothing to do with deciding to disable Ctrl-Alt-Backspace. It was an upstream decision. tseliot came up with the dontzap script in response to the upstream decision.

---

### Post by ghindo on 2009-06-05
> **RiceMonster said:**
> Cranonical didn't disable it; The Xorg devs did.> **cariboo907 said:**
> Canonical had nothing to do with deciding to disable Ctrl-Alt-Backspace. It was an upstream decision. tseliot came up with the dontzap script in response to the upstream decision.This.  A thousand times this.  I keep seeing people complaining on the forums that Ctrl+Alt+Backspace doesn't work anymore in 9.04, but I think very few people realize that **it was an upstream decision**.  If you have an issue with it, take it up with the upstream developers, not the Ubuntu developers.

---

### Post by Skripka on 2009-06-05
> **ghindo said:**
> This.  A thousand times this.  I keep seeing people complaining on the forums that Ctrl+Alt+Backspace doesn't work anymore in 9.04, but I think very people realize that **it was an upstream decision**.  If you have issue with it, take it up with the upstream developers, not the Ubuntu developers.

Bingo.


That being said, the *buntu devs *could* simply re-enable Zap in the default Xorg.conf they ship in their packages.

---

### Post by ghindo on 2009-06-05
> **Skripka said:**
> Bingo.


That being said, the *buntu devs *could* simply re-enable Zap in the default Xorg.conf they ship in their packages.I just wonder how many people *need* that feature enabled.  There have been a few vocal advocates on the forums, but in the broader scheme of things, does the average user really need this feature enabled?

---

### Post by RiceMonster on 2009-06-05
> **ghindo said:**
> I just wonder how many people *need* that feature enabled.  There have been a few vocal advocates on the forums, but in the broader scheme of things, does the average user really need this feature enabled?

I agree with what you're saying, though I enabled that option myself, and I don't use Ubuntu either. The "average" user will not need it, as they'd probably just reset their computer and they'd be fine clicking logout themselves. However, it's not hard for people like me who want it enabled to enable it themselves.

---

### Post by earthpigg on 2009-06-05
i use ctrl+alt+backspace about once a week, and i am far from an advanced user.

---

### Post by Dimitriid on 2009-06-05
I first it was annoying. Now I just stop and start GDM as needed.

---

### Post by mocoloco on 2009-06-05
I used to show users how to Ctrl+Alt+Backspace, so yeah it's definitely annoying to have a shortcut that was once universal to all distros suddenly disabled.
Similarly I wish Gnome used Ctrl+Alt+Esc to bring up xkill like KDE and XFCE do, that's another handy tool that should be easy to get to no matter what DE or distro.

---

### Post by init1 on 2009-06-05
Not sure why they removed it. It's a very useful key sequence. There should be an option to enable/disable it somewhere in the system preferences menu.

---

### Post by jrusso2 on 2009-06-05
> **frodon said:**
> Yep i put it back right after updating because i like Ctrl+Alt+Backspace, not a big deal to put it back really. As it concerns mainly advanced users it is not difficult for them to put back the Ctrl+Alt+Backspace ability, so it is a rather armless change and if it can prevents new user from mistakenly kill xserver then why not.

I still wonder how you can press three keys by accident?

---

### Post by bailout on 2009-06-05
I found it never worked in previous releases when I had lock ups anyway. Whenever I have had freezes they have been total with no response from the keyboard or mouse and the only way of escape was a hard reboot. Hence I don't miss it :D

---

### Post by toupeiro on 2009-06-05
Frankly, I don't like it because its not standard behavior in any other UNIX or Linux variant out there, and rarely is it a problem on any other UNIX or linux variant out there.  In fact, the more I think about it, in over ten years of system administration and user support, its NEVER been an issue having that option...  BUT, as long as I get the option to turn it back on, I'm pacified.  Its not an ubuntu deal-breaker for me personally, but if I had to deploy ubuntu for as many people as I've deployed RHEL to professionally, I'd be pretty pissed off, because this "enhancement" was not disclosed well at all on release.  Doing things like that makes your release feel more hobbiest and less professional.  Thats not a reflection on how I feel about ubuntu as a distribution, but if too many undocumented changes like this start slipping out in releases, and are only clearly disclosed AFTER people complain about it, thats not good.

Personally, I think the devs should be more up front with giving the user the choice, rather than think its best for them to turn it off.

If I get a freeze that ctrl-alt-backspace doesn't fix, usually a ctrl-alt-F1 and a jump from init 3 and back to init 5 usually fixes things.  The times have been extremely rare where a cold reboot was **required.**

---

### Post by Skripka on 2009-06-05
> **jrusso2 said:**
> I still wonder how you can press three keys by accident?

Especially in lieu of the similarity of Zap's macro to that of the 3-fingered-salute.

---

### Post by Motorhead Kaze on 2009-09-19
I am a devote Hardy user, but installed Jaunty in Japanese yesterday on my laptop. Installing my new system there were several instances where I wanted to ctrl+alt+bksp and said words that sound like "schucks" and thought, "What did I do? I broke it and I only just installed...oh, maybe it is because it is a Japanese version?" So I went to the Japanese forum, and they were like, "Where have you been? That ain't us, that's Jaunty."

On the "advanced user" issue, I consider that to mean the folks who TEACH me the codes to type in the terminal. I am simply a copy+paste jockey. I am a VERY frequent "messer with things small and large" and like to try out stuff all the time...which means I make mistakes often and need to restart X real quick. So I am left with the question, "Why do long-term users need to find one day that the shortcut we have used since we began this Ubuntu journey is just not there anymore?" As others have said, it is usually when you need something that you find out it is gone. 

Originally Posted by jrusso2  ```

I still wonder how you can press three keys by accident?
```
Advice 1. Don't let the cat run up and down your keyboard. 2. While listening to Tocata and Fugue DO NOT try to play your keyboard like a pipe-organ.

Please, just bring ctrl+alt+bksp back by default and let people who despise it be the ones to shut it off.

PS I came here looking for the answer how to put ctrl+alt+bksp back...people have said "put it back by editing xorg.conf"...you have a link for the thread that says how to do that? Tried to put the keystrokes in my keyboard shortcut options, but the thing won't accept that combination...

---

### Post by Motorhead Kaze on 2009-09-19
I could really use a good tutorial.

I used the tutorial on this page: [http://www.ubuntugeek.com/howto-enable-ctrl-alt-backspace-in-ubuntu-jaunty.html/comment-page-1#comment-13187](http://www.ubuntugeek.com/howto-enable-ctrl-alt-backspace-in-ubuntu-jaunty.html/comment-page-1#comment-13187)
...and the first suggestion did not work, so I tried the second suggestion. Somehow an xorg.conf that only had the code for their fix in it opened up -- my usual xorg.conf was gone (so I foolishly believed that perhaps multiple files like this could exist) (doh) and when I saved it, it naturally replaced MY xorg.conf with theirs and my dual monitor setup was back to 2 clones...daaaaamn. I am so glad I backup my xorg.conf...

What I would like to know is, why did a new/different xorg.conf open that did not have my usual script included? Was it this redundant sudo gksudo command?
```
sudo gksudo gedit /etc/X11/xorg.conf
``` or am I just unlucky? So screwed. At any rate, I tried this route below first and it did nothing...
```
sudo apt-get install dontzap
```
```
sudo dontzap --disable
```
and like I said, the second route ate my xorg.conf.

Also, for some reason, I cannot make a keyboard shortcut for ctrl+alt+bksp either. The keys work otherwise, but I cannot press THOSE 3 keys and make a shortcut.

Ubuntu friends! Activate! ...form of...a tutorial! Shape of...an ice...well...no ice please.

---

### Post by Elfy on 2009-09-19
move your backup back to xorg.conf and add

> Section "ServerFlags"
	Option	"DontZap"	"False"
EndSection


Should be fine, it also should be all that installing dontzap does - at least that is all it did to mine

---

### Post by Motorhead Kaze on 2009-09-20
> **forestpixie said:**
> move your backup back to xorg.conf and add



Should be fine, it also should be all that installing dontzap does - at least that is all it did to mine

Yeah, it is just my luck that any of the aforementioned strangeness took place at all...because after all, I tried sudo dontzap --disable and sudo dontzap -d and they did nothing for me. ...which blows. It is such a common occurrence for me, but my computers aren't alien or anything. On top of it all, I looked at my xorg.conf and the "serverflags" section that you gave me is already there.

I am going to try messing with these quotes, maybe they are the wrong type...

---

### Post by Motorhead Kaze on 2009-09-20
Thank you for taking your time to help me out there. I appreciate it. 

It WAS the quotes. I am going to have to look up this "smart quote" concept, because I hear about it, just learned that I should consider it, but have no idea why some quotes are smarter than others (ahem). For that matter, yeah, sometimes quotes in Open office do appear differently. ...more basic information that never made it my way I see.

Anyway, the important thing is, after changing the quotes ctrl+alt+bksp kills X...as it should.

---

### Post by JillSwift on 2009-09-20
Under the new Xorg in Karmic, which doesn't seem to need a xorg.conf - can you have a partial xorg.conf, to include this? Or ... well, how to go about it under Karmic?

---

### Post by Paqman on 2009-09-20
Tbh, i've just got used to using Alt-SysRq-K.

---

### Post by Xbehave on 2009-09-20
> **Paqman said:**
> Tbh, i've just got used to using Alt-SysRq-K.
Thats a completely different shortcut, If you were ctrl+alt+bkspacing, the best thing to do is to learn what your doing and start:
ctl+alt+f1 -> login -> kill the problem app 

removing ctl+alt+bkspace was done by the xorg people because its a stupid shortcut that should only be needed when stuff goes **very** wrong (read xorg development) but gets abused by newbies who thing its a fast ctrl+alt+del!

---

### Post by lswb on 2009-09-20
> **Xbehave said:**
> Thats a completely different shortcut, If you were ctrl+alt+bkspacing, the best thing to do is to learn what your doing and start:
ctl+alt+f1 -> login -> kill the problem app 

removing ctl+alt+bkspace was done by the xorg people because its a stupid shortcut that should only be needed when stuff goes **very** wrong (read xorg development) but gets abused by newbies who thing its a fast ctrl+alt+del!

While dealing with the mods needed to get intel drivers working acceptably in 9.04 things often went **very** wrong, and occasionally still do. There have been many times when Ctrl-Alt-BS worked to restart X when I could not change to a VT and Alt-Sysrq-K wasn't working either. And there have been times when Alt-Sysrq-K worked but Ctrl-Alt-BS did not.

---

### Post by toupeiro on 2009-09-21
Thread brought back from the dead.  I thought it was a bad default idea then, and I still do now!

---

### Post by schauerlich on 2009-09-21
I installed Mint today and went to add DontZap to my xorg.conf, and was pleasantly surprised to find it was already there.

---

### Post by misfitpierce on 2009-09-21
I think it should be re-enabled by default just for security reasons of lockups of the system even though I have had 0 on Jaunty... But... If that day ever came which it does for every OS eventually for anyone... it would make t a lot easier than force powering down etc etc... I think it should be re-implemented just for the fact that its a good feature to have just incase and its not as though it is a key combonation that is easy to accidently hit lol!

---

### Post by sideaway on 2009-09-21
As a beginner I constantly broke gdm, ctrl+alt+backsp was one of the first shortcuts I learnt, first was alt+home. TBH, it was a godsend, now I don't break it as often as I (kind of) know what I'm doing. But I like to experiement. But I've enabled it anyway.

---

### Post by t0p on 2009-09-21
[quote=Xbehave;7982191 
removing ctl+alt+bkspace was done by the xorg people because its a stupid shortcut that should only be needed when stuff goes **very** wrong (read xorg development) but gets abused by newbies who thing its a fast ctrl+alt+del![/quote]

This is demonstrative of the utterly screwed-up thinking that goes on in the heads of those who disable useful tools like the Ctrl+Alt+Backspace, and of those who justify its removal!  Near the start of this thread, frodon said it was disabled because it was only needed or even known about by "advanced users".  Now Xbehave claims it's actually known about and "misused" by "newbies".

Try and get this straight:  I am not a newbie, nor am I an advanced user.  I am simply someone who likes being able to knock out X with a 3-key press when I decide I want to do it.  Yes, I know it's "easy" to enable.  I have enabled it.  That is irrelevant.  I don't use a certain proprietary OS, I use Linux.  And I want *my* Linux to act the way in which Linux is *supposed* to act!

One more thing: I'm sick of hearing how Ubuntu is "for users who just want a simple desktop machine on which to carry out simple desktop tasks etc".  Ubuntu is *for me* and for anyone else who wants to use it, for whatever purpose they want to use it.  So please let me use it in the way I want, withoutmaking me jump through stupid hoops.  The majority of voters in the poll want Ctrl+Alt+Backspace enabled by default.  Most of the posters in the thread have said enable Ctrl+Alt+Backspace by default.  So Do It!!!!  (And I'm not talking to Gnome devs - I'm talking to Ubuntu packagers.)

Thank you.

---

### Post by Motorhead Kaze on 2009-09-21
> **Xbehave said:**
> 
removing ctl+alt+bkspace was done by the xorg people because its a stupid shortcut that should only be needed when stuff goes **very** wrong (read xorg development) but gets abused by newbies who thing its a fast ctrl+alt+del!

You are so funny...but in an offensive kind of way. Because you don't like this shortcut makes it stupid huh. Well, it isn't just the people you label newbies who use this shortcut -- you Linux guru you -- I have used Ubuntu tutorials from Ubuntu documentation pages that will have a user "restart X" at a certain point in the process of installing a program, and the way to restart x has been ctrl+alt+bksp for quite a while. 

In recent times many changes take place "on the fly", because Ubuntu gets better with age, but not everything. They certainly didn't when many of us began using Ubuntu.

Although things go south less than they did a few years ago, sometimes things still go very wrong and system/quit/log out doesn't always work. That moment is not the opportune time to find out that the shortcut we were taught to use is gone.

---

### Post by Xbehave on 2009-09-21
> **Motorhead Kaze said:**
> You are so funny...but in an offensive kind of way. Because you don't like this shortcut makes it stupid huh.
I make no attempt to offend people, nor do i think people that use the shortcut are stupid, I just aim to inform people (in a much less offensive manner than your post). The shortcut is stupid because it gives users too much power without telling them what it really does. 
> Well, it isn't just the people you label newbies who use this shortcut -- you Linux guru you -- I have used Ubuntu tutorials from Ubuntu documentation pages that will have a user "restart X" at a certain point in the process of installing a program, and the way to restart x has been ctrl+alt+bksp for quite a while. 
And that is the wrong way to do it, the correct way to restart X is to logout (so applications don't lose data, corrupt their files, etc), then select restart X. I'm not some linux guru nor do i pretend to be, however doing an ***ugly*** (severs all connections and just hopes everything turns out ok) restart of xorg should not be done by anybody who doesn't understand what it is:
[LIST]
[*]It compromises security (ctl+alt+bkspace would remove a screensaver (this may not be true anymore))
[*]It compromises data integrity (apps may have thier files in a bad state when you run it)
[*]It offers no advantage over ctrl+alt+f2 (which short of bad driver bugs, will work whenever ctrl+alt+bkspace would)
[/LIST]

If **you** are doing stuff which will require you to restart X then **you** should enable it, that way newbies will not trigger it by mistake or mistake it for a quick ctrl+alt+del.
[LIST]
[*]newbies (don't know what c+a+b does) - should not be using it
[*]People who think they know what c+a+b does - can choose to enable it
[*]People who really know what c+a+b does - would rather kill/restart just the bad app
[*]Developers who actually need c+a+b - can enable it
[/LIST]

> That moment is not the opportune time to find out that the shortcut we were taught to use is gone.That is why ctrl+alt+bkspace should not be taught at all!

> I'm sick of hearing how Ubuntu is "for users who just want a simple desktop machine on which to carry out simple desktop tasks etc". Ubuntu is for me and for anyone else who wants to use it, I'm sick of people not understanding that they can customise ubuntu if **they** want to, but ubuntu is trying to spread linux to "users who just want a simple desktop machine on which to carry out simple desktop tasks etc". If you don't like the default configuration of ubuntu its a lot easier for you to make it more complicated than it is for a newbie to make it easier.

> Most of the posters in the thread have said enable Ctrl+Alt+Backspace by default. So Do It!!!!It is a good thing ubuntu isn't a democracy then, especially given that the people that answer this poll are hardly representative of all ubuntu users. The fact is the people that know what they are doing (at Xorg level, then ubuntu simply didn't overwrite the decision) have decided (and rightfully so IMO) that the shortcut should not be enabled by default in end-user desktops. 

> While dealing with the mods needed to get intel drivers working acceptably in 9.04 things often went very wrong, and occasionally still do.
Your dealing with xorg internals i think the enphasis should be on you to enable c+a+b
> There have been many times when Ctrl-Alt-BS worked to restart X when I could not change to a VT and Alt-Sysrq-K wasn't working either.
Ctrl+alt+f2 is handled by xorg, so it is strange that it would still respond to ctrl+alt+bkspace but not ctrl+alt+f2, however Alt+Sysrq+R will always (short of a kernel bug) get you keyboard control and allow c+a+f2.

> (And I'm not talking to Gnome devs - I'm talking to Ubuntu packagers.) This is the problem, and i don't mean to be harsh, but you don't understand what ctrl+alt+bkspace does if you think it has anything to do with gnome.

---

### Post by JugglinPhil on 2009-10-21
> **Kingsley said:**
> I'm pretty sure it's a default setting in X.org 1.6.

Just add this to /etc/X11/xorg.conf under Section "ServerFlags."
```
        Option  "DontZap"       "false"
```
Thanks a lot for that one, I was always wondering why it was not working. No wonder if it's disabled by default, definitely should be enabled.

---

### Post by Poyntz on 2009-11-06
> **frodon said:**
> The best is to have no freeze so you don't need it, i hope it is the real goal behind this :)
The beginner getting a freeze don't know this combo anyway so it doesn't really matter in such case. If you dont want to play manually with xorg.conf which is really wise you can just use the "dontzap --disable" command line to enable it.
[http://www.ubuntu.com/getubuntu/releasenotes/904#Ctrl-Alt-Backspace%20disabled%20by%20default%20in%20Xorg](http://www.ubuntu.com/getubuntu/releasenotes/904#Ctrl-Alt-Backspace%20disabled%20by%20default%20in%20Xorg)

Refresh metacity, compiz, when no other known means are available. If something is fiddle capable it will be fiddled with, when GUI things are fiddled with, Ctrl+Shift+Backsp provides a nice out. At least that's my outlook :/

---

### Post by hoppipolla on 2009-11-06
I said yeah... just because I guess it would kind of be possible for someone to hit it accidentally... maybe...

It's up for debate!

Incidentally I always enable it myself just in KDE 4 (I'm not sure if there's a similar setting in Gnome):

System Settings > Regional & Language > Keyboard Layouts > Key Combo to Kill the X Server - Ctrl+Alt+Backspace ... tick!

and that's it :)

---

### Post by 3rdalbum on 2009-11-06
The keyboard combination to kill X has NOT been removed. I repeat: NOBODY has removed the ability to kill X with a three-key combination.

The keyboard shortcut has merely MOVED to Alt-SysRq-K. (the SysRq key is sometimes labelled "PrintScreen".

That is the more appropriate place for it. Firstly, newbies won't hit it thinking it will bring up the system monitor. Secondly, all other recovery keyboard combinations involve Alt-SysRq (like Alt-SysRq-S for sync, Alt-SysRq-B for reboot etc). Thirdly, it works more reliably as a kernel keyboard combination than as a userspace keyboard combination.

It's changed. Get used to it.

EDIT: That's probably a bit harsh - I posted earlier on in the thread months ago, saying that it should be brought back in :-)  That was before I learnt of Alt-SysRq-K, though.

---

