---
title: "Constructive Criticism of Indicator Applet (in 10.04)"
date: 2010-05-01
forum: Testimonials &amp; Experiences
---

### Post by pihbar on 2010-05-01
I don't like the indicator applet. Here are the reasons:

[LIST=1]
[*]Only works (at all) with a handful of applications. These don't even include the wireless monitor, for example. What this leads to is inconsistency in (a) spacing, and (b) icon behavior (with respect to right and left clicking) -- exactly what the indicator applet was made to remove. 

It would be nice if somehow the system tray could be replaced with indicator applet, so that at least all applications have the same spacing between them.

[*]It is hard to remove properly. I removed it *from the panel*, and (a) suddenly Rhythmbox wasn't showing ANYWHERE until I disabled the system tray plugin (I reported a bug on this), (b) and I needed to start gnome-volume-control-applet to have sound control in the tray (the icon was some ugly, default one -- clashing with the rest of my theme). However, removing indicator applet from the gnome panel still leaves something called indicator-application-session running. This leads me to my next point.

[*]The app is too buggy and incomplete to include in a distribution release and not include an easy way to disable it. This looks unprofessional.

[*]Lastly, and most importantly, it does a bad job at it's intended purpose. The majority of system tray icons don't integrate with it, so you still have to figure out which click does what on which icon, and furthermore, most icons open with a left click so turning indicator-applet off makes for a more consistent experience! Finally, it is horribly cumbersome to have to click twice (click, then select show Rhythmbox) to show an application. Euch![/LIST]

Istead of trying to create a custom tray icon for every application out there, and integrate indicator-applet with a ton of third party software, I think that the tray should be * re-imagined* to not be so (unnecessarily) all encompassing, and simply make the user's lives easier. What I have in mind, particularly, is the behavior Windows XP (gasp) implemented more than 10 years ago: have a little arrow in the corner that hides "unused" icons, and keep a list of icons that ever appeared in the system tray, so that the user can select which never to hide, and which always to hide. This solution sounds simple to program (although it seems like gnome programming is a mess), is already well understood, and is at least consistent across all apps. Better to have a weaker solution working properly, than an idea of an unreachable stronger solution.

Please add your thoughts, let's initiate communication with the devs. The most wonderful thing about linux is that you can do that! I submitted many bugs, for instance, that got solved quickly and were simply there because the right person didn't know about them. This principle is similar, even though we're not talking about one bug, per se, but a set of features.

---

### Post by pihbar on 2010-05-01
Here's somebody's unwitting contribution to this thread:

[https://bugs.launchpad.net/ubuntu/+source/indicator-applet/+bug/519553](https://bugs.launchpad.net/ubuntu/+source/indicator-applet/+bug/519553)

---

### Post by Mr. Picklesworth on 2010-05-01
Hehe, I was just about to pop in here and link you to my bug report, Pihbar :)

Unfortunately, try though I did, I have not succeeded at creating *any* serious discussion on my patch.

---

### Post by EtherBunny on 2010-05-01
[I completely agree with you]("http://ubuntuforums.org/showthread.php?t=1466061&highlight=indicator"), and [others]("http://ubuntuforums.org/showthread.php?t=1465522&highlight=indicator") [do]("http://ubuntuforums.org/showthread.php?t=1466561&highlight=indicator") [too]("http://ubuntuforums.org/showthread.php?t=1433134&highlight=indicator").

---

### Post by jpmaglutac on 2010-05-02
The Indicator Applet is the ONLY thing I HATE in Lucid, and yes, I agree that it should be changed with something more intuitive =/

---

### Post by autonomy on 2010-05-02
> **pihbar said:**
> it is horribly cumbersome to have to click twice (click, then select show Rhythmbox) to show an application.and the 2nd click is at the bottom of the menu!

---

### Post by iamnotthemessiah on 2010-05-02
my critisism isnt as constructive, i think its the worst thing since the nuclear bomb. it needs to die

---

### Post by pihbar on 2010-05-02
Would you still include the arrow for hiding some icons?

---

### Post by telefono on 2010-05-02
When i installed lucid, i really get disappointed with this feature.

Well, it is beauty (it integrates perfectly with the new Themes). But that's all.

The double click issue, is really irrational and tedious.

I hate the email ico (i really don't use it) because i never found a way to tray the evolution (i dont like alltray); 

however i love u, ubuntu : )

---

### Post by EtherBunny on 2010-05-03
Another gripe: The battery power icon doesn't show a percentage - not as a tooltip, and not even if you click on it. The best it does is estimate the "time remaining", which is always wrong.

---

### Post by Viva on 2010-05-03
I just removed the indicator applet completely.

---

### Post by Viva on 2010-05-03
> **autonomy said:**
> and the 2nd click is at the bottom of the menu!

and too close to quit for my liking.

---

### Post by autonomy on 2010-05-03
> **EtherBunny said:**
> Another gripe: The battery power icon ... best it does is estimate the "time remaining", which is always wrong.
sounds like the memory meter in the panel. It shows cached memory ... which has to do w/ the processor, so I make it blend in w/ the free memory. Otherwise, the system monitor would look like it's using 25% more RAM than it's using. I watch my memory b/c I barely have enough for VirtualBox.

---

### Post by juancarlospaco on 2010-05-03
1, 2, 3 = will be fixed on next release.

4 = Its not the purpose to include ALL apps on these menu, should stay small/medium size i think.

---

### Post by pihbar on 2010-05-03
> **juancarlospaco said:**
> 1, 2, 3 = will be fixed on next release.

4 = Its not the purpose to include ALL apps on these menu, should stay small/medium size i think.

How do you know this? 

Also, to some of the other people: 
- The battery not showing a percentage when you click or tooltip over is indeed a bad idea (even though i wasnt aware of this -- maybe becaus i use a different applet?
- Everybody wants to remove the mail icon from the applet it seems. This is actually achievable through removing some package.
- The problem with removing indicator-applet altogether is that some apps (in particular rhythmbox, wont work with it any more).

Nobody's talking about alternatives...

---

### Post by juancarlospaco on 2010-05-03
1) Battery Icon actually show percentage, and info, and graphs, and statistics, and tech info, and basic info, and estimated dis/charge and anything you should need.

2) sudo apt-get -y remove evolution-indicator

3) there are several replacements for notifications on official repos, you need to configure them, there are several apps actually using the default notification too.

---

### Post by pihbar on 2010-05-04
> **juancarlospaco said:**
> 1) Battery Icon actually show percentage, and info, and graphs, and statistics, and tech info, and basic info, and estimated dis/charge and anything you should need.

2) sudo apt-get -y remove evolution-indicator

3) there are several replacements for notifications on official repos, you need to configure them, there are several apps actually using the default notification too.

I'm not sure if these numbers are in correlation with my original post. I'll take them as points :) 



Perhaps there is a push for indicator-applet because of what's coming up: [http://www.markshuttleworth.com/archives/333](http://www.markshuttleworth.com/archives/333) 

I have mixed feelings on this, I wonder how it'll pan out. Then again, I have mixed feelings on Gnome Shell.

---

### Post by cgroza on 2010-05-04
> **pihbar said:**
> I don't like the indicator applet. Here are the reasons:

[LIST=1]
[*]Only works (at all) with a handful of applications. These don't even include the wireless monitor, for example. What this leads to is inconsistency in (a) spacing, and (b) icon behavior (with respect to right and left clicking) -- exactly what the indicator applet was made to remove. 

It would be nice if somehow the system tray could be replaced with indicator applet, so that at least all applications have the same spacing between them.
[*]It is hard to remove properly. I removed it *from the panel*, and (a) suddenly Rhythmbox wasn't showing ANYWHERE until I disabled the system tray plugin (I reported a bug on this), (b) and I needed to start gnome-volume-control-applet to have sound control in the tray (the icon was some ugly, default one -- clashing with the rest of my theme). However, removing indicator applet from the gnome panel still leaves something called indicator-application-session running. This leads me to my next point.
[*]The app is too buggy and incomplete to include in a distribution release and not include an easy way to disable it. This looks unprofessional.
[*]Lastly, and most importantly, it does a bad job at it's intended purpose. The majority of system tray icons don't integrate with it, so you still have to figure out which click does what on which icon, and furthermore, most icons open with a left click so turning indicator-applet off makes for a more consistent experience! Finally, it is horribly cumbersome to have to click twice (click, then select show Rhythmbox) to show an application. Euch!
[/LIST]

Istead of trying to create a custom tray icon for every application out there, and integrate indicator-applet with a ton of third party software, I think that the tray should be * re-imagined* to not be so (unnecessarily) all encompassing, and simply make the user's lives easier. What I have in mind, particularly, is the behavior Windows XP (gasp) implemented more than 10 years ago: have a little arrow in the corner that hides "unused" icons, and keep a list of icons that ever appeared in the system tray, so that the user can select which never to hide, and which always to hide. This solution sounds simple to program (although it seems like gnome programming is a mess), is already well understood, and is at least consistent across all apps. Better to have a weaker solution working properly, than an idea of an unreachable stronger solution.

Please add your thoughts, let's initiate communication with the devs. The most wonderful thing about linux is that you can do that! I submitted many bugs, for instance, that got solved quickly and were simply there because the right person didn't know about them. This principle is similar, even though we're not talking about one bug, per se, but a set of features.
If you don't like it why you are not making a better replacement?

---

### Post by Tamlynmac on 2010-05-04
[> pihbar]("http://ubuntuforums.org/member.php?u=157659")

Thank you for sharing your testimonial. I will not comment on your opinions, as this is not a debating/discussion section of the forum. As defined by the T&E sectional guidelines.

Good Luck

---

### Post by pihbar on 2010-05-05
> **Tamlynmac said:**
> []("http://ubuntuforums.org/member.php?u=157659")

Thank you for sharing your testimonial. I will not comment on your opinions, as this is not a debating/discussion section of the forum. As defined by the T&E sectional guidelines.

Good Luck

Well, perhaps you can leave your opinion to be seen by others. I am not so invested in the indicator-applet that I will oppose people who don't agree with me. I may even change my mind -- maybe I'm missing something. Anyway, we don't have to debate.

---

### Post by pihbar on 2010-05-05
> **cgroza said:**
> If you don't like it why you are not making a better replacement?

You seem to be implying that I have a choice between exactly the following when I dislike something (a piece of software?):
1) Dislike something and work to make it better.
2) Don't say anything, therefore not providing input to people who are already working on the product.

I don't subscribe to this mode of thought, and see sharing my opinion as not only acceptable, but welcome. After all, sharing is caring, and posts are easily skipped on this forum.

---

### Post by cb_rex on 2010-05-06
> **autonomy said:**
> and the 2nd click is at the bottom of the menu!

I agree this Rythmbox icon issue is very annoying, and would like to see it fixed. Previously you could simply click to reveal Rythmbox. I also use several workspaces and if I had the Rythmbox window open on a different workspace than the one I was working on then I could double click on the icon and it would close it on the other workspace and show it on my current workspace, very handy indeed... but not any more.

As for the Indicator Applet, I have disabled it completely as it just doesn't seem to work right. My biggest issue with it is when it pops up I naturally mouse over it as I read it, causing it to fade out so I can't read it, this is very counter intuitive. 

It would also be good if I could click on the notification to make it disappear before it naturally times out. If these two things were incorporated into the applet and the other program syncing issues were ironed out then the Indicator Applet would be pretty cool.

Edit: On a different note now I'm thinking about it, I preferred the way the little Rythmbox icon used to have the circles around it when it was playing and no circles when it was stopped, now it always looks like its not playing. Can I have this back?

---

### Post by autonomy on 2010-05-06
> **cb_rex said:**
> As for the Indicator Applet, My biggest issue with it is when it pops up I naturally mouse over it as I read it, causing it to fade out so I can't read it, this is very counter intuitive. 

It would also be good if I could click on the notification to make it disappear before it naturally times out.I have appreciated the fade out because I usually want to click something underneath the notification when I put at it, but I think your ideas would make good optional check boxes if they are codable.

PS Rhythmbox still has little wavelengths coming out of the top.

---

### Post by cb_rex on 2010-05-06
> **autonomy said:**
> I have appreciated the fade out because I usually want to click something underneath the notification when I put at it, but I think your ideas would make good optional check boxes if they are codable.

PS Rhythmbox still has little wavelengths coming out of the top.

Yeah the option to customise the notifier would be best really as some people will like the fade as you do, but some will find it annoying like I do.

---

### Post by trayzz on 2010-05-07
agree with all the points. indicator applet is useless and notifications did the job perfectly well already.

---

### Post by Ms_Angel_D on 2010-05-08
pihbar, thanks for your feeback.

---

