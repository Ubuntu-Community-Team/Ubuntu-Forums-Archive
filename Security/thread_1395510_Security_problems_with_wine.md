---
title: "Security problems with wine?"
date: 2010-01-31
forum: Security
---

### Post by houseworkshy on 2010-01-31
I started a thread elsewhere, Desktop Enviroments, and have been advised to post a link here pointing to it.  Neither I nor the person trying to help me with it are sure what it all means and would welcome advice.  The security stuff comes up later in the thread.

Here it is

[http://ubuntuforums.org/showthread.php?t=1391683](http://ubuntuforums.org/showthread.php?t=1391683)

---

### Post by bodhi.zazen on 2010-02-01
That is a long thread. I understand your password was changed, but I find it hard to believe that a game written for Microsoft running in wine would change you linux log in password.

First the game would have to call a linux command, passwd, and ask you current password then enter a new one. Extremely difficult as I doubt you entered your password when your started the game. So now you would have to invoke some kind of key logger or who knows what.

The other option, the game changed your password by editing system files. In theory this is not possible if wine is running without root powers. Again, you are claiming the windows program somehow had a Trojan the rooted you linux box via wine ?

I am sorry, but neither of these two seem very plausible. I would be curious to see if you can replicate this behavior.

---

### Post by houseworkshy on 2010-02-01
When I have time, not soon as I'm out of play time for a while, I'll ask my friend to bring the disc around and see if it can be done again.  It did seem very odd to me which is why I posted.  I think it may have been because the game was installed immediately after wine was installed, instantantly.  So the guess was that the sudo used to install wine gave those rights to the game during it's install, less than sudo default fifteen minuets, or when it ran.  

I know that if one uses sudo in the terminal or for an administer task such as synaptic the password is not asked for again until the timer runs out.  It is only a guess.  Whilst I've used Ubuntu since 7.10 I have been primarily an application user so I am out of my depth here and though the tiger report looks bad to me I don't really know what it all means.  This is why I posted.  

The other less serious problem which happens with the other game, needing three logins to get to the gnome GUI, I have replicated three time now, including twice on freshly installed main systems.  It is this which leads me to the other guess.  If the game is installed immediately after wine it happens.  If one waits more than a quarter of an hour after installing wine in it doesn't.  

I have promoted learning the terminal to top of the things to learn list, should have done that in the first place instead of the office, graphics and pythons stuff perhaps.  Is this one pertinent to  the Ubuntu terminal  BTW [http://linuxcommand.org](http://linuxcommand.org).  Currently I'm reading up on the sudo man pages trying to find a command which is effectively "for this command and that which depends on it only".

Thankyou for looking it over.

I've sent you a pm

---

### Post by bodhi.zazen on 2010-02-01
After installing wine (or using sudo) use 

sudo -k

Again, you would need to either install the game by running wine as root

sudo wine ....

or the game would have to have linux commands, ie sudo, built in.

Very very odd behavior.

---

### Post by houseworkshy on 2010-02-01
Thanks for that.  So what I'll do is try to get the mystery game disc again, and play around with installing wine and it, using the sudo -k after the wine install then not using it and see if the behavior can be replicated/prevented.  I have a duel boot so as long as nothing hits the loader or the disc I work on I can use the other for experiments.  I'm not sure when this will be, I have time at the weekend but don't know when I can get hold of the cd as it is not mine and the owner is not always easy to contact.  It is of course quite likely that something utterly differant happened as I hadn't configured my firewall.  I'll post here again when I know more.

Thanks again

---

### Post by mkvnmtr on 2010-02-01
I have read both your threads and have a couple of points that might help you figure out the problem. I run wine with a couple of rather simple games. Your tiger report looks like it found much more wrong than on my system. I did have a lot of checksum errors but I think most of them were in a virtual box install. But as unscholed as I am in security I would be afraid there is a problem after seeing that repost. 
  The other thing is on the password. Are you sure that the change was not to the keyboard. I ask because the other day I installed localepurge. That is a script that deletes any language files that it thinks you do not need. A couple of days later when I tried to put in a password I discovered a to me strande font. It was another language , font and keyboard. It is posible that you had the game change your keyboard and thus the letters were different when you tried to put in your password. My fix was to uninstall localepurge and reinstall all of the language files. I watched them install and they were for many apps. I am thinking that was your problem, not that the password changed.

---

### Post by houseworkshy on 2010-02-01
As I reinstalled because I couldn't get in I don't know so it could have been that.  When I test it I'll take a look at the keymapping too.  Thanks.

---

### Post by houseworkshy on 2010-02-02
I've just reinstalled 9.04 prior to beating it up at the weekend.  Because I wanted to be absolutely sure I did everything correctly I followed the guide in the documentation part of the Ubuntu site.  I saw something I hadn't seen before; apt-links, for want of a better name.  This page has some [https://help.ubuntu.com/9.04/musicvideophotos/C/video-dvd.html](https://help.ubuntu.com/9.04/musicvideophotos/C/video-dvd.html)  It looks like a nice way of helping new people set up things like restricted extras and so on.  The thing is when I clicked on them I got a pop up box asking if I wanted to install then when I clicked "yes" it just went ahead and did it.  I was not asked for a password.  Is this normal?

---

### Post by bodhi.zazen on 2010-02-02
Yep, apt-url is new, people are just learning to use it:

[https://wiki.ubuntu.com/AptUrl](https://wiki.ubuntu.com/AptUrl)

[http://manpages.ubuntu.com/manpages/jaunty/en/man8/apturl.8.html](http://manpages.ubuntu.com/manpages/jaunty/en/man8/apturl.8.html)

If it did not ask a password my guess is that you recently entered it, there is a 15 minute grace period.

Try it again, if does not ask a password, I would file a bug report.

---

### Post by houseworkshy on 2010-02-02
You're right.  I must have had more perceptions per moment of consciousness than usual and misjudged time. When I waited  for a clock, much better at relative measurements of change  than me, to say fifteen minuets had elapsed then used the link from the wiki to [http://appnr.com](http://appnr.com) all was well.  Put in one and was asked for my password, then put in another one quickly and wasn't.  I understand it now.  With respect to the technical side of things I really am a novice and appreciate your patience.
Because it may be valid later.  If I were to shorten the default fifteen minuets in sudo to something smaller, say 15 seconds, then initiated an administration action such as an installation which took longer, say 30 seconds, would the action finish it's task or stop uncompleted when the timer ran out?

P.S  Just a thought.  The only apt-urls I've seen are benign.  There may come a time when vandals use them to trick people who may still be in sudo after doing something, that pop up box could say anything I imagine.  Is there an icon or applet one can download for the toolbar as a reminder.  "Caution sudo active" sort of thing, perhaps showing time remaining too.

---

### Post by bodhi.zazen on 2010-02-02
> **houseworkshy said:**
> You're right.  I must have had more perceptions per moment of consciousness than usual and misjudged time. When I waited  for a clock, much better at relative measurements of change  than me, to say fifteen minuets had elapsed then used the link from the wiki to [http://appnr.com](http://appnr.com) all was well.  Put in one and was asked for my password, then put in another one quickly and wasn't.  I understand it now.  With respect to the technical side of things I really am a novice and appreciate your patience.
Because it may be valid later.  If I were to shorten the default fifteen minuets in sudo to something smaller, say 15 seconds, then initiated an administration action such as an installation which took longer, say 30 seconds, would the action finish it's task or stop uncompleted when the timer ran out?[/code]

If you shorten the time out or grace period it only affects how long before you need to enter your password again.

Any tasks that are running will continue to run and function normally even though the time out expires.

[quote]P.S  Just a thought.  The only apt-urls I've seen are benign.  There may come a time when vandals use them to trick people who may still be in sudo after doing something, that pop up box could say anything I imagine.  Is there an icon or applet one can download for the toolbar as a reminder.  "Caution sudo active" sort of thing, perhaps showing time remaining too.

Yes, such things are tools , and as such the are good and bad and potentially abused.

Obviously apt-url + a malignant stie + browsing within the 15 minute grace period == big problems.

IMO apt-url should ALWAYS ask for a password and display informational text explaining the package to be installed.

One more example of convenience at the expense of security =)

---

### Post by houseworkshy on 2010-02-03
Thank you, I was beginning to worry about sudo but initiated commands complete, that's perfect!  So what I'll do when I get the problem disc is repeat the wine>game> bit with the sudo default timer settings, and if the problem repeats try to get some data.  Then, after another clean start, try it again with at least a  fifteen minuet wait after installing wine and see what happens then.

In fact I have frequently used the terminal and Administration at the same time the browser is open, using guides, installing things and double checking something in my system before posting somewhere.  It it probable that wine just happened to be what was running when unsafe practices caught up with me and has nothing to do with it.  Though I haven't *knowingly* encountered apt urls before, browsing all over the place while sudo was effective seems a far more likely culprit.  I hope so but will still look into it as part of the learning process if nothing else.  

As a touch typist putting in the password frequently is no problem at all.  From what you have said about browsing in the sudo grace period, which I must have spent days doing if one adds it up, I'd like to set the sudo timer to have very short duration after password entry.   If possible an effective &#8220;for this only then lock&#8221;.  I'd like this to be the system default as, most of the time, sudo actions are one off's and I could simply change it back to suit more intensive tasks anyway.  Please could you point me at a good guide aimed at novices which shows me how to set this up.

True about the convenience security balance, sadly.  My pen hasn't had a virus yet but the packet transefer rate is dreadful and rather expensive, especially first class.

---

### Post by bodhi.zazen on 2010-02-03
FYI, you can also use ```
sudo -k
```

see man sudo =)

---

### Post by houseworkshy on 2010-02-07
The sudo -k has been very useful to me.  I've found that it works on the apt:urls too which is good as along with the request for a password one also gets a list of what is intended.  Currently trying to work out a way to automate it after each sudo command, it would make a nice add-on which kicks in with the browser I think, though it'd be a long time before I was up to writing something like that if ever.
Still haven't managed to get hold of the disk but a few installs down the line am fairly sure that I was wrong to blame wine.  I tried tiger on a system which had nothing but the hardware drivers, updates, and ufw enabled with default deny and got a very similar looking log.  Could be in my loader, tiger itself or, more probably that I'm just too far out of my depth.  I'm learning a lot though.

---

### Post by houseworkshy on 2010-02-16
I still haven't had the time and the nessesaries to play with this yet.  However, thoughts arising from this thread have led me to post an idea for kicking around here [http://brainstorm.ubuntu.com/idea/23600/](http://brainstorm.ubuntu.com/idea/23600/).

---

