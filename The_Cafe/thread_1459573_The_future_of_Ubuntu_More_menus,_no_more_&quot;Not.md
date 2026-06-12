---
title: "The future of Ubuntu: More menus, no more &quot;Notification Area&quot;"
date: 2010-04-21
forum: The Cafe
---

### Post by Starks on 2010-04-21
[http://design.canonical.com/2010/04/notification-area/](http://design.canonical.com/2010/04/notification-area/)
[http://www.markshuttleworth.com/archives/347](http://www.markshuttleworth.com/archives/347)

I hope Shell isn't the reason for this overhaul.

---

### Post by KlavKalashj on 2010-04-21
I kind of like this, I like already in 10.04 there is less clutter than before, it looks so much more polished. But I don't want to click just to see the time... I hope they will succeed in doing a good implementation of this idea.

---

### Post by x-shaney-x on 2010-04-21
I'm not sure what to make of all this.
I don't think it is anything to do with gnome shell at all, more it seems to be to do with ubuntu specifically (though many people see gnome and ubuntu as the same thing).

The trouble is, I can see it leading to even MORE inconsistencies, as ubuntu default apps take on the new system but other gnome apps and even more, other 3rd party apps take longer to make use of this new system (if ever).

So we may be left with all these "notification" menus, along with other apps still using the systray/notification area.
And if ubuntu decides to remove the notification area altogether as it says, what about other apps that still haven't adapted to this new system, which use the tray but there is no tray to use?

Aside from anything else, yes it's early days but look at the messaging menu as an example:
For that to be any use whatsoever, evolution has to be running.  What's the point?  if it's running we don't need a menu to control it and if it isn't running the menu doesn't control it anyway.
There will end up being all these menus everywhere taking up space that do nothing unless you happen to use those apps and those apps are running.

Nevermind, I'm just confusing myself more now.  Think I'm going to take a look at KDE.

---

### Post by Merk42 on 2010-04-21
I don't think it has to do with GNOME Shell. As the article states, this all started in 9.04 which is way before GNOME Shell was at its current state.

> **KlavKalashj said:**
> I kind of like this, I like already in 10.04 there is less clutter than before, it looks so much more polished. But I don't want to click just to see the time... I hope they will succeed in doing a good implementation of this idea.
You don't have to click to see your volume level, I doubt you'll have to click to see what time it is


The inconsistencies in the system tray is one of the big problems with Linux.  Any time someone comes along and wants to do some for the good of consistency, developers get all irritated and scream "MY FREEDOM". So we end up having many developers doing their own thing, reinventing the wheel and making Linux seem like a stitched together experience.

---

### Post by ankspo71 on 2010-04-21
If I include the space taken by MeMenu, the notification area was taking up a lot of space on the panel, especially with a non-widescreen monitor. I just bought a widescreen so it's not an issue for me anymore. This idea of theirs is probably thought of to help netbooks and other systems with smaller screens. I'm just guessing though. One of the very few drawbacks I found with Gnome was the notification area icons couldn't be hidden like in Windows XP and KDE4.

PowerMenu? I can't wait to test 10.10 now :P

---

### Post by zekopeko on 2010-04-21
> **x-shaney-x said:**
> I'm not sure what to make of all this.
I don't think it is anything to do with gnome shell at all, more it seems to be to do with ubuntu specifically (though many people see gnome and ubuntu as the same thing).

The trouble is, I can see it leading to even MORE inconsistencies, as ubuntu default apps take on the new system but other gnome apps and even more, other 3rd party apps take longer to make use of this new system (if ever).

You do understand developers can support both methods?

> So we may be left with all these "notification" menus, along with other apps still using the systray/notification area.
And if ubuntu decides to remove the notification area altogether as it says, what about other apps that still haven't adapted to this new system, which use the tray but there is no tray to use?

Then its the developers fault. They should have asked if there is a notification daemon at all. Assuming your application will have access to a notification area is sloppy coding.

> Aside from anything else, yes it's early days but look at the messaging menu as an example:
For that to be any use whatsoever, evolution has to be running.  What's the point?  if it's running we don't need a menu to control it and if it isn't running the menu doesn't control it anyway.
There will end up being all these menus everywhere taking up space that do nothing unless you happen to use those apps and those apps are running.

Nevermind, I'm just confusing myself more now.  Think I'm going to take a look at KDE.

Well that is a bug IMO. Evolution should have a backend that can run as a daemon (I think it does but have no idea why it isn't used as such).

---

### Post by Starks on 2010-04-21
Here's Mark chiming in...

[http://www.markshuttleworth.com/archives/347](http://www.markshuttleworth.com/archives/347)

---

### Post by castrojo on 2010-04-21
> **x-shaney-x said:**
> Nevermind, I'm just confusing myself more now.  Think I'm going to take a look at KDE.

KDE uses KStatusNotifierItem, which is basically application indicators, so there is no escape. :p

---

### Post by ronacc on 2010-04-21
> **whiprush said:**
> KDE uses KStatusNotifierItem, which is basically application indicators, so there is no escape. :p

Gnome and Kde are not the only desktops .

---

### Post by MacUntu on 2010-04-21
And Linux not the only OS. :P

> We will be working on ways for long-running applications to be less obtrusive when their windows are minimized.

I got an idea: place them in the panel as icons!

> That may make perfect sense to the developers of those individual applications.

Makes perfect sense to me too. :)

---

### Post by PcBoyGeorge on 2010-04-21
Aww... Don't like this. The Notification Area ruled. Hope when they remove it they keep things. I like seeing my battery status,volume etc from there. And I hate now that then I can't have stuff like VLC and Spotify (WINE) there... Good job 11.04/11.10 won't be for another year or so. 10.04/10.10 should do ok. And since I do prefer Win 7 anyway. I will have to learn to get used to it.

---

### Post by 23meg on 2010-04-21
> **PcBoyGeorge said:**
> Aww... Don't like this. The Notification Area ruled. Hope when they remove it they keep things. I like seeing my battery status,volume etc from there.

I guess you've been misled by the thread title into thinking that there will be "no more notifications", which is wrong. 

I've changed that part of the title to better reflect the content.

---

### Post by castrojo on 2010-04-21
> **ronacc said:**
> Gnome and Kde are not the only desktops .

Any desktop is free to implement libappindicator just like they did the old tray.

---

### Post by BwackNinja on 2010-04-21
Excuse my cynicism, but from reading that article I thought "Hmm... notification area is clearly bad." However, reaching the end it just sounded to me like "well, since it is so bad and so abused, we created/are creating this wonderful infrastructure that makes this area more consistant and groups a few things, but looks like it will be (ab)used in the same way as it was before."

I agree with it being better, but I can't say I agree with either needing to exist. As far as I see, no applications have a good reason to be there in the first place. What does rhythmbox do while there? Allow you to pause and play music? Without a keyboard with multimedia keys is it that horrible to go to rhythmbox and click "pause" while also allowing yourself the full interface? As bascially a replacement (in this case) for multimedia keys, there is an applet better suited for that.

System tray, although that's not what it is supposed to be called, that's what it should be. Volume, Battery, Network. Nothing else really needs to be there.

---

### Post by teachop on 2010-04-21
After following a few threads, I am wondering if my Lucid tray icons are actually not working.  One post said you can see volume without clicking on it.  How?  When I hover over the battery, nothing happen, no status.  When I hover over the volume, same thing, no volume percentage appears.  Is this correct for the new way, or does my system exhibit a bug?  I really miss having the hovers.

---

### Post by ronacc on 2010-04-21
One thing is very clear from Marks comments is that Ubuntu will be continuing the trend of less user choice  . Will this ultimately lead to less users choosing Ubuntu ?

---

### Post by xebian on 2010-04-21
> **x-shaney-x said:**
> <snip>

Nevermind, I'm just confusing myself more now.  Think I'm going to take a look at KDE.

You should because KDE notification settings/configuration is very easy and friendly.

---

### Post by xebian on 2010-04-21
> **whiprush said:**
> KDE uses KStatusNotifierItem, which is basically application indicators, so there is no escape. :p

But you can configure it easily to get the desired effect.

---

### Post by x-shaney-x on 2010-04-21
Hmm, installed kubuntu desktop and have been playing around with KDE a bit.
I still prefer the simpler feel of Gnome (at the moment) and with gnome I tend to be happier with the defaults.  I remember last time I used KDE i was endlessly fiddling and customizing things and I just can't help it.

But back to the notification are, I think the author of this post makes some good points: [http://ubuntuforums.org/showpost.php?p=9149522&postcount=7](http://ubuntuforums.org/showpost.php?p=9149522&postcount=7)

He is complaining that he doesn't use evolution or gwibber so the messaging menu is pointless for him but if he removes it he also loses volume and battery monitor because they are tied to the messaging menu.

As it is in it's current state I think the whole area is pointless (I mentioned in more detail in another thread).
Gwibber doesn't notify or even work properly (with facebook at least) the email part of the messaging menu is useless unless using evolution is running.
The chat bit works but once opened you have to show the empathy window OR move to another part of the menu to change status.

I just don't think it works at all in it's current state and might have been better left out completely for this release.

---

### Post by Merk42 on 2010-04-21
> **ronacc said:**
> One thing is very clear from Marks comments is that Ubuntu will be continuing the trend of less user choice  . Will this ultimately lead to less users choosing Ubuntu ?
Considering Windows and Mac have far more market share and far less ability to customize every little thing; I'm going to say 'no'.

---

### Post by ronacc on 2010-04-21
> **Merk42 said:**
> Considering Windows and Mac have far more market share and far less ability to customize every little thing; I'm going to say 'no'.

I did mot mention either Windows or Mac , nor would I suggest either of those as an alternative if choice is important to you . There are however more that 100 other linux distros that offer different levels of customization ranging from more to less than where Ubuntu seems to be headed .

---

### Post by Merk42 on 2010-04-21
> **ronacc said:**
> I did mot mention either Windows or Mac , nor would I suggest either of those as an alternative if choice is important to you . There are however more that 100 other linux distros that offer different levels of customization ranging from more to less than where Ubuntu seems to be headed .

Well perhaps the difference is you were referring to users of Linux and I was referring to users of any computer operating system.

I mentioned earlier in this thread how I feel about customizing in Linux (at least from a developer standpoint)

---

### Post by emarkay on 2010-04-21
Is this Apple? "Do it our way or no way".
Or is this Microsoft: "Do it this way because we have always done it this way, but now we are changing it because we can". 
Or is it Linux - "We do what the users want, because they make it so"?

Nope, sounds like Ubunutu "Let's try this because it sounds neat-o and makes us look cool".

Where's the logic; the proof of a legit enhancement to and for the end-user?  
Nothing more needs to be discussed.

---

### Post by Merk42 on 2010-04-21
> **emarkay said:**
> ...
Or is it Linux - "We do what the users want, because they make it so"?
...


Who says that's not what this is though?
Because **you** don't like it? Well I do, so our anecdotes cancel out.

Have you looked at how 'limiting' GNOME Shell plans to be?

---

### Post by andrewabc on 2010-04-21
So instead of battery icon that graphically shows how much battery left or hover over icon to get % etc, the user will have to click on something to bring up a menu that will show battery status?

Or will they have to click on a menu, then battery app listed among other apps to bring up relevant info?

---

### Post by dagrump on 2010-04-21
Never mind!

---

### Post by Queue29 on 2010-04-21
How is the end result any different than just having yet another "start" menu?

I say screw the taskbars, go with AWN and copy OSX all the way if we're just going to drop all the functional parts of gnome.

---

### Post by Longinus00 on 2010-04-22
> **Queue29 said:**
> How is the end result any different than just having yet another "start" menu?

I say screw the taskbars, go with AWN and copy OSX all the way if we're just going to drop all the functional parts of gnome.

Next time you use a mac, look at the top of the screen.

---

### Post by kansasnoob on 2010-04-22
My only concern is how usability will be effected for visually impaired old farts like me :)

The way notify-osd is now it's absolutely worthless to me. I need a longer duration so I can either focus or use the screen magnifier.

---

### Post by Saner on 2010-04-22
Meh, less clutter is GoooooooooooD

---

### Post by x-shaney-x on 2010-04-22
> **Saner said:**
> Meh, less clutter is GoooooooooooD

If I have empathy installed but only use it occasionally, the chat entry is still there in the messaging menu.
And the status changer is still always sitting there in the me-menu doing nothing.
Same with evolution, the useless menu entry is still there when it isn't running.
Gwibber?  Menu entry for broadcast still there when not running.

So from what I can see there is much MORE clutter.  With the regular "systray" or whatever you want to call it, there would be nothing up there at all unless the apps or running.

I'm still in two minds with it all.  I do like the whole me for messaging/social networking side of things because it keeps them all together but if you are also going to be launching more and more apps from these indicator menus it's going to be like having loads of menu everywhere.

---

### Post by zekopeko on 2010-04-22
> **x-shaney-x said:**
> If I have empathy installed but only use it occasionally, the chat entry is still there in the messaging menu.
And the status changer is still always sitting there in the me-menu doing nothing.
Same with evolution, the useless menu entry is still there when it isn't running.
Gwibber?  Menu entry for broadcast still there when not running.

So from what I can see there is much MORE clutter.  With the regular "systray" or whatever you want to call it, there would be nothing up there at all unless the apps or running.

I'm still in two minds with it all.  I do like the whole me for messaging/social networking side of things because it keeps them all together but if you are also going to be launching more and more apps from these indicator menus it's going to be like having loads of menu everywhere.

There is less clutter because all the relevant apps are grouped together. You don't have an icon for Empathy, Gwibber, Evolution and a dozen other things in the notification area.

What they aim to do is logically group things into a single menu entry so you know where your communication apps are, where your media apps are etc.

Even if you don't use Gwibber or Evolution at some point it is better to have them in the menu ready to setup. Why? Because disappearing, reappearing applications aren't cool from a usability perspective.

Have you noticed how menu entries in a normal menu simply have actions (that aren't context sensitive) greyed out if you can't use them? That is because you want to signal the user that they are there but simply not used at this time.

---

### Post by Lucretius on 2010-04-22
what about wine apps?

they still follow the windows way of doing things... will there need to be a separate "wine" menu?

---

### Post by robert shearer on 2010-04-22
> **zekopeko said:**
> There is less clutter because all the relevant apps are grouped together. 

What they aim to do is logically group things into a single menu entry so you know where your communication apps are, where your media apps are etc.

We already have this, 'Applications' top left  :).
Yes I know they don't have notifications etc etc  but the logic of having accessible groups of apps via **new** menus seems redundant.

Why not just upgrade the functionality of the existing menus or replace both ??
 Why this rampant mutiplicity of menus and layers of access ?.

---

### Post by zekopeko on 2010-04-22
> **Lucretius said:**
> what about wine apps?

they still follow the windows way of doing things... will there need to be a separate "wine" menu?

I don't know about the specifics of wine menus but they could allow a Windows applications menu for those apps. Or they could simply patch wine to use the Appindicators. I'm guessing wine reads somewhere the content of the wine notification icons menu and could translate that to the Appindicator way of doing things.

> **robert shearer said:**
> We already have this, 'Applications' top left  :).
Yes I know they don't have notifications etc etc  but the logic of having accessible groups of apps via **new** menus seems redundant.

Why not just upgrade the functionality of the existing menus or replace both ??
 Why this rampant mutiplicity of menus and layers of access ?.

Application menu is for launching apps only. The Appindicator area is for getting notified. The fact that you can launch some apps from the messaging menu is a good thing. 

Why? Well because it shows you all the communication options you have at your disposal. I think that the messaging menu does (or should) follow your "Preferred applications" choices.

---

### Post by x-shaney-x on 2010-04-22
If they want to reduce clutter:

Integrate MintMenu into gnome and do away with the menubar, turn the notification into just that, so only apps that give indications of events or status (chat, mail, gwibber, if it worked etc and things like wireless, battery monitor etc) can put icons there and come up with some guidelines to stop any app being able to put an icon there just for the sake of doing it or just to control something in that app.
That is basically what is being talked about by Mr S but it could be done with the existing systray without needing to create all these indicators.

---

### Post by zekopeko on 2010-04-22
> **x-shaney-x said:**
> If they want to reduce clutter:

Integrate MintMenu into gnome and do away with the menubar, turn the notification into just that, so only apps that give indications of events or status (chat, mail, gwibber, if it worked etc and things like wireless, battery monitor etc) can put icons there and come up with some guidelines to stop any app being able to put an icon there just for the sake of doing it or just to control something in that app.
That is basically what is being talked about by Mr S but it could be done with the existing systray without needing to create all these indicators.

There are a number of problems with the systray as you call it.

First of all its not native to Gnome or KDE. With Appindicators you simply pass a Dbus message and it creates the menu for you. Fully native looking since it uses either Qt or GTK+ to create it. That means that KDE apps would have a fully GTK+ notification menu in Gnome and vice versa. This also solves bugs that were plaguing the old "systray". Things such as non transparent icons etc.

Second of all the notification areas is highly abused. As was mentioned numerous times you really don't know what left or right click do until you click the icon in the old notification area. With the new one there is only one menu no matter right or left click.

All of this increases consistency. Limiting choice is sometimes the best option for usability and user design.

---

### Post by robert shearer on 2010-04-22
> **zekopeko said:**
> Application menu is for launching apps only. The Appindicator area is for getting notified.

Yes, as I said, I am aware of this.

However, why can the Application menu not be **upgraded** to allow notifications ?

If, say, "Applications' was pulsing a different colour and I could click on it to see that Sound & Video was pulsing and if I scrolled there I might find that Brasero was pulsing for my attention and when I checked Brasero I may find that "Burning was succesful" ( despite the disc activity having stopped and the tray being opened !!) 

 I could then go to "preferences" in Brasero and turn off it's damned notifications!!

A week or so after a new install I could have well turned off all the footling notifications I **don't** want and left only those that really concern Me.

Instead it seems we will end up with several more menus, some of which will launch apps just like the 'Application' menu.

Then what happens when some new functionality comes along?
Do we get yet another set of menus ??.

I have already uninstalled the me-menu package and if the multiplying menu mentality continues I will be looking for more to chuck.

---

### Post by ronacc on 2010-04-22
> **zekopeko said:**
> There are a number of problems with the systray as you call it.

All of this increases consistency. Limiting choice is sometimes the best option for usability and user design.  

1 ok lets do away with systray and its problems and introduce a whole new set of problems .

2 You assume that there is only one path to usability , or for that mater only one definition of usability . What you find pleasing and useable may well be annoying crap to someone else .

---

### Post by zekopeko on 2010-04-22
> **robert shearer said:**
> Yes, as I said, I am aware of this.

However, why can the Application menu not be **upgraded** to allow notifications ?

If, say, "Applications' was pulsing a different colour and I could click on it to see that Sound & Video was pulsing and if I scrolled there I might find that Brasero was pulsing for my attention and when I checked Brasero I may find that "Burning was succesful" ( despite the disc activity having stopped and the tray being opened !!) 

You do understand that the Application menu serves a different function then the Appindicator ones?

>  I could then go to "preferences" in Brasero and turn off it's damned notifications!!

You can disable notifications for most/all applications.

> A week or so after a new install I could have well turned off all the footling notifications I **don't** want and left only those that really concern Me.

Yet again, you can disable notifications. Both the notify-osd and Appindicator kind.

> Instead it seems we will end up with several more menus, some of which will launch apps just like the 'Application' menu.

Are you actually bitching because you will have a consistent way of receiving notifications? Really?

> Then what happens when some new functionality comes along?
Do we get yet another set of menus ??.

Instead of ifs perhaps you could give me a specific functionality? Mind you applications can implement custom menus. Another thing is that the API still isn't set so who knows what else could end up in those menus. For now you have text+icon menu entries and a volume slider.

> I have already uninstalled the me-menu package and if the multiplying menu mentality continues I will be looking for more to chuck.

So the me menu is horrible but having 3+ different icons, each for one app isn't?

---

### Post by zekopeko on 2010-04-22
> **ronacc said:**
> 1 ok lets do away with systray and its problems and introduce a whole new set of problems .

Perhaps you could enlighten me what those problems are.

> 2 You assume that there is only one path to usability , or for that mater only one definition of usability . What you find pleasing and useable may well be annoying crap to someone else .

So what is annoying crap to you?

---

### Post by ronacc on 2010-04-22
> **zekopeko said:**
> Perhaps you could enlighten me what those problems are.



So what is annoying crap to you?

1 jamming every possible notification need into a "one size fits all" solution with no flexibility ( choice )

2  transient floating messages that are unanswerable and bundled notifications for apps I don't want/use/have running . 

In my opinion the systray/notificaion area/whatever you want to call it should only be for apps that are actually running or messages that require action.

---

### Post by philinux on 2010-04-22
Thread moved to Community Cafe.

---

### Post by zekopeko on 2010-04-22
> **ronacc said:**
> 1 jamming every possible notification need into a "one size fits all" solution with no flexibility ( choice )

That was tried and sucked. Lets try something new.

> 2  transient floating messages that are unanswerable and bundled notifications for apps I don't want/use/have running .

The whole point of Notify-OSD is to notify you of some action that doesn't requires immediate action. I really don't understand what is with your obsession on having to act on something. Appears to me you are Pavlov's dog of old school notifications.

So you have this messaging menu that is the focal point of communication on your desktop. I would think that having "Set up your XXX app" is making a feature more discoverable.

> In my opinion the systray/notificaion area/whatever you want to call it should only be for apps that are actually running or messages that require action.

You do realize you just described the new Appindicator right?

---

### Post by null_pointer_us on 2010-04-22
The most amazing thing happened when I awoke and booted Linux. A powerful surge went through my body. Clairvoyance spontaneously developed in my mind, enabling me to see into the past and every possible future. Instantly, I knew everything.

To answer the question which is about to appear in your mind, I, with supernaturally enhanced infinite knowledge and wisdom, momentarily contemplated all possible uses of my time and decided the most efficacious use of my new abilities would be to review the user interface overhaul project of this Linux distribution.

I have determined that it is doomed to fail. The reasons have been seared into my mind:

1) As of right now, it is not finished. No, not even close. Some things have been converted and some have not. The result is even more inconsistent now! Half the icons are consistently inconsistent while the other half are inconsistently consistent. Moreover, I have foreseen that the project will never finish. So we shall be doomed to great inconsistency...forever!

2) Presently it does not function as a pure extension of my will. This is a major problem!! When I move my mouse over an icon, nothing happens. Right-clicking produces some weird panel menu. Some things are in different places than I expect. Whilst pondering the infinite complexities of software development, a conclusion has become readily apparent: This is a sign the project is doomed to fail.

3) My clairvoyance has granted me the ability to see the exact reasons why all past software projects have succeeded or failed. Furthermore, I can see elaborate connections between Ubuntu and some other nameless projects. I would explain these connections, but to you, with your normal mind, would conclude they were superficial, vague, tenuous, and/or completely insane. Regardless, they, too, were doomed to fail, from the start, for the very same reasons. Plus, I didn't really like them either.

4) Looming on the distant horizon, like the dark stormclouds of a terrible storm, is a monstrousity called Gnome Shell. It dares to provide me with new and different ways to organize and interact with my desktop. This, in itself, is truly horrifying. But what's even worse is the possibility that all Gnome and Ubuntu developers might suddenly come together, lose their minds in a collective creative orgy, and in one magnificent gesture end all hope of desktop productivity in Ubuntu.

The end is coming. When Gnome Shell arrives, Ubuntu's credibility as a distro will plummet. At this time, following a massive cash infusion from undisclosed sources, SCO will suddenly revive, subsume Ubuntu, and promote it to irrevocably ruin public perception of Linux. I have foreseen this; do not question it.

Strangely, as soon as I finished writing this, my powers of clairvoyance faded along with any hope of understanding what I just wrote. However, one thing remains clear in my mind: unless this project is run the way I wish, it is doomed to fail.

/satire, specifically NOT directed at anyone in this thread

---

### Post by Directive 4 on 2010-04-22
> **ronacc said:**
> 

2 You assume that there is only one path to usability , or for that mater only one definition of usability . What you find pleasing and useable may well be annoying crap to someone else .


+1000

usability is about using it the way you want, 

not the way someone else wants you to.

---

### Post by ronacc on 2010-04-22
> **zekopeko said:**
> That was tried and sucked. Lets try something new.



The whole point of Notify-OSD is to notify you of some action that doesn't requires immediate action. I really don't understand what is with your obsession on having to act on something. Appears to me you are Pavlov's dog of old school notifications.

You do realize you just described the new Appindicator right?

1 If it does not require immediate action do not pop up a meaningless messagebox that I can't get rid of and have to wait for to disappear on its own . (note if I cant do anything about the message it IS meaningless .)

2 remains to be seen .

---

### Post by zekopeko on 2010-04-22
> **ronacc said:**
> 1 If it does not require immediate action do not pop up a meaningless messagebox that I can't get rid of and have to wait for to disappear on its own . (note if I cant do anything about the message it IS meaningless .)

How is the message meaningless? For the majority of your day you are receive such transient messages IRL and you don't act on them. You make a mental note and go on. Why should computer interaction be any different?

> 2 remains to be seen .

Well you said it not me. Not my fault the Appindicator works falls almost perfectly into that definition.

---

### Post by Directive 4 on 2010-04-22
> **zekopeko said:**
> How is the message meaningless? For the majority of your day you are receive such transient messages IRL and you don't act on them. You make a mental note and go on. Why should computer interaction be any different?
.

i don't like such transient messages coming from my computer for the same reason

 i don't like my dishwasher beeping at me.

---

### Post by zekopeko on 2010-04-22
> **Directive 4 said:**
> i don't like such transient messages coming from my computer for the same reason

So you are saying that the old bubbles that are there forever or until clicked were awesome?

> i don't like my dishwasher beeping at me.

From my experience dishwashers beep only when imminent doom is upon them.

---

### Post by Directive 4 on 2010-04-22
> **zekopeko said:**
> So you are saying that the old bubbles that are there forever or until clicked were awesome?



From my experience dishwashers beep only when imminent doom is upon them.



i don't know what old bubbles you speak of, 

if i want to find something out i do,

my computer don't do 'bubbles'

machines work for me, i don't work for machines

---

### Post by ronacc on 2010-04-22
> **zekopeko said:**
> How is the message meaningless? For the majority of your day you are receive such transient messages IRL and you don't act on them. You make a mental note and go on. Why should computer interaction be any different?



Well you said it not me. Not my fault the Appindicator works falls almost perfectly into that definition.

1 the computer is not my "larger life" it is a tool I use for a focused task , therefore a message that does not apply to that focused context and furthermore cannot be acted upon in any case ,is an unwelcome annoyance and contextually meaningless .

2 as the new notification has so far appeared it certainly does not fit my description of how I believe the notification area should work .

---

### Post by Merk42 on 2010-04-22
> **Directive 4 said:**
> machines work for me, i don't work for machines

and yet you'd prefer to do the active work of finding out a status of something (and maybe also actively closing it), rather than the computer working for you and telling you

and this whole thing of OH NO the indicator applet is horrible because it's not how **I** want it to work is hilarious.
what if program foo's "systray" icon doesn't work they way I want? Is it exempt from criticism?

---

### Post by ronacc on 2010-04-22
> **zekopeko said:**
> 
From my experience dishwashers beep only when imminent doom is upon them.

they also beep to tell you the wash cycle has finished which information can , if important to you , be obtained in other ways .

---

### Post by zekopeko on 2010-04-22
> **ronacc said:**
> 1 the computer is not my "larger life" it is a tool I use for a focused task , therefore a message that does not apply to that focused context and furthermore cannot be acted upon in any case ,is an unwelcome annoyance and contextually meaningless .

Then disable the notifications for that/those app(s).

> 2 as the new notification has so far appeared it certainly does not fit my description of how I believe the notification area should work .

What are you now talking about? You already said how the area should work and that is exactly how the Appindicator area works. Do I need to re-quote you?

---

### Post by ronacc on 2010-04-22
> **Merk42 said:**
> and yet you'd prefer to do the active work of finding out a status of something (and maybe also actively closing it), rather than the computer working for you and telling you

and this whole thing of OH NO the indicator applet is horrible because it's not how **I** want it to work is hilarious.
what if program foo's "systray" icon doesn't work they way I want? Is it exempt from criticism?

If I want to know the status of something I am willing to take reasonable steps to determine said status . If I am not in the least interested it that status , dont slap me in the face with floating bubbles .

You are quite welcome to criticize foo's systray icon if you feel it to be behaving badly .

---

### Post by BwackNinja on 2010-04-22
> **Merk42 said:**
> and yet you'd prefer to do the active work of finding out a status of something (and maybe also actively closing it), rather than the computer working for you and telling you

and this whole thing of OH NO the indicator applet is horrible because it's not how **I** want it to work is hilarious.
what if program foo's "systray" icon doesn't work they way I want? Is it exempt from criticism?

Looking allows you to see the status when **you** want to. Otherwise it just tells you when it changes, and without being able to look, if you miss the bubble, you miss the info. For example, a new IM in pidgin or empathy occurs, you are distracted and don't see the lovely bubble in the corner. Without any other indication that you received a message, at best you find out late just checking randomly or when another message comes.

Notifications are nice, and persistence certainly doesn't belong there, so there has to be something else you can glance at to give you this info.

---

### Post by Directive 4 on 2010-04-22
> **Merk42 said:**
> and yet you'd prefer to do the active work of finding out a status of something (and maybe also actively closing it), rather than the computer working for you and telling you

and this whole thing of OH NO the indicator applet is horrible because it's not how **I** want it to work is hilarious.
what if program foo's "systray" icon doesn't work they way I want? Is it exempt from criticism?

if i wanted the computer to do it for me, i'd tell it to.

i still don't get it, status of what, why do we need to get messages from the system. 

i put the dishes in the dishwasher, when i want i come back and it's finished, don't need it to beep and go, oh, finished now, still have to take the stuff out beep or none so no extra active work there.

and just what are you on about with program foo systray criticism, 

do you  even know what those words mean

---

### Post by ronacc on 2010-04-22
> **zekopeko said:**
> Then disable the notifications for that/those app(s).



What are you now talking about? You already said how the area should work and that is exactly how the Appindicator area works. Do I need to re-quote you?

I can't give a screenshot to illustrate my point , because I did disable the thing .

---

### Post by DoktorSeven on 2010-04-22
This is, of course, about personal choice, whether someone wants to have messages or not.  Personally I don't like the idea of messages popping up on screen for everything, nor do I like notification icon overload.  

The idea is that we want to get rid of the overuse of notification icons, so let's concentrate on that -- applications that use them as little more than an alternative for being minimized should be changed.  Gnome should also lessen the amount of things in the taskbar -- why do I need a pseudo-messenger application in my taskbar when I can run a messenger app alone?  Why do I need a shutdown app when it could go into the menu?  Why do I need three menus (Applications, Places, System) when they could all be integrated into 1?  And if you actually WANT those things, someone could make an app or have an option to make it do this.  It comes back to the almost fear of choice many have with computers -- it baffles me that people have a huge number of choices everywhere else in their lives but when it comes to computing, they want one single, safe choice.

I believe the whole messaging/notification system is basically a useless idea that does nothing but add a huge layer of unnecessary complexity to the system.  Let each application notify me in its own way.  If I don't like how it notifies me, let me choose another application.  It's that simple.  Stacking it all into a single system removes choice, increases complexity, and makes applications too dependent on the environment; if you change to another environment, say, fluxbox, it's going to be out of place and annoying.  

I believe GNU/Linux in general has been going way too fast towards the idea of unnecessary complexity lately in many ways (dbus, for example, a system which can easily be replaced as it was in the past by directly passing messages between applications/named pipes, rather than a complex system) for the sake of new users, when the very essense of GNU/Linux is supposed to be *simplicity*.  You can still make a distro easy to use for new users without adding all sorts of complex architecture hanging all over the place by creating simple yet effective helper scripts and programs that do all the heavy lifting.  

I moved to GNU/Linux many, many years ago for this idea of simplicity and elegance, among other reasons, and now I find that it's getting more and more difficult to do.  Even other distros that are much less "user-friendly" and lighter than Ubuntu embrace this idea of complexity by using things like dbus, and it worries me that many have lost what it really means to have a system that works on simple yet powerful elements, as it did in the past.  I believe that regardless of the need for user-friendliness and modern requirements that it still can do this if we would try and let go of this illusion that complexity is somehow necessary with modern GNU/Linux.

---

### Post by gangstafoo! on 2010-04-22
there should be a petition for not changing it! i despise the popups on windows, thats one of the reasons i left.. lol but a small one... why are they copying a horible design, aka windows 7? and where will all the apps be? like msn ( or emesene ) and all that crap.

---

### Post by whiskeylover on 2010-04-22
Ubuntu's notification - moving complexity from the systray to the notification area... and making it more complex.

My two cents.

---

### Post by Merk42 on 2010-04-22
> **Directive 4 said:**
> if i wanted the computer to do it for me, i'd tell it to.

i still don't get it, status of what, why do we need to get messages from the system. 

i put the dishes in the dishwasher, when i want i come back and it's finished, don't need it to beep and go, oh, finished now, still have to take the stuff out beep or none so no extra active work there
My point was that the way you'd rather use a computer (which is all well and good) seems contrary to your comment "machines work for me, i don't work for machines"

> **Directive 4 said:**
> and just what are you on about with program foo systray criticism, 

do you  even know what those words mean
Foo is used as a variable when whatever Foo stands for (in this case a specific application) isn't important.

What I was saying was you and others are upset that the indicator applet doesn't work they way you want.  What of those users who are upset (and now relieved) that the current Notification Area (systray) didn't work they way they want (ie lack of consistancy)

---

### Post by bash on 2010-04-22
To all the people complaining that this is taking away users freedom and limiting choice:

Ubuntu is not about making everything the way you personally want it to be or even about giving you the option to do it. Ubuntu is about doing things the way the Ubuntu developers and "leaders" want. 

Quite a few users don't seem to want realize or understand this. Reminds me a lot of this post on the Fedora Devel Mailing List:

[https://www.redhat.com/archives/fedora-devel-list/2008-January/msg00861.html](https://www.redhat.com/archives/fedora-devel-list/2008-January/msg00861.html)

---

### Post by Directive 4 on 2010-04-22
> **Merk42 said:**
> My point was that the way you'd rather use a computer (which is all well and good) seems contrary to your comment "machines work for me, i don't work for machines"


no, i think it's the way you would rather me use a computer that's seems contrary.

---

### Post by toupeiro on 2010-04-22
If Ubuntu's going to continuously start "phasing out" pieces of standard gnome and standard linux OSes, IMO ubuntu just needs to stop using gnome and focus on a WM that works more like they want.  Ubuntu seems to throw standards to the wind lately and do radical graphical changes every point release.  This makes it harder to promote and support.

If they want to stop using notifications for themselves and their own in-house apps, fine.  If they want to phase out the system tray, get real....

---

### Post by MaxIBoy on 2010-04-22
I like what they're doing with all the new menus, but they seem to be threatening to get rid of the systray altogether and break thousands of working, useful applications! This is a very heavy-handed, Apple-like move and I had honestly come to expect better from them. I certainly hope I'm not understanding them correctly. It's true that if anyone comes up with an alternative to the systray, I will be the first in line. But any solution *must* have some kind of legacy support for old programs and protocols. 

This is not like system software, such as X servers, drivers, and kernels. When you are dealing with non-system software, i.e. applications, compatibility becomes important. I know that the systray is visually offensive and could probably use some depreciation, but you need to be realistic. For example, I hate the Tk look-and-feel as much as the next guy, but I still keep it installed because I use programs that need it. And I still write code for it because it is *the* cross-platform toolkit for Python.

As far as notifications go, Notify-OSD was a good effort but it's really not an improvement. It really is just as annoying as it looks at first. I've never really learned to like it. One of my programming projects in the future will be a dummy daemon which implements the freedesktop notification protocol but, by default, sends everything to the bit-bucket. It will also be configurable so you can have totally customized actions and methods of display, via shell scripts. Personally, I think this is going to be the best way to do this kind of thing.

Finally, I hope Notify-OSD and these new menus will be developed separately from Ubuntu itself, and effort should be made to reach out to packagers for other distros.

---

### Post by powder on 2010-04-22
I like the idea and I'm totally on board with it.  The only complaint I have at this point is that it's only been half-implemented so far.

---

### Post by Glucklich on 2010-04-22
I believe this discussion might be very important since it might lead to the beginning of the construction of a Ubuntu desktop identity, in terms of the way it feels when you use it. And I really hope that it can flourish. That being said, I must admit that my personal path on Linux has been focused on performance, so I have a couple of things to say about this. It's obvious that this might suck for legacy computers, but since lower than PII are not supported for a while and there's nothing to accommodate them comfortably, I guess it was a predictable move. Pretty good job on ending with the African schools and environmental gimmicks, wouldn't you say? So, the first practical thing I have to say is that, those pop-up balloons do a pretty good job of making themselves annoying and therefore, noticeable. So, I actually told them to sod off. The second point is, as far as I remember, programs like Pidgin, Transmission and others came with the systray option unchecked. And checking it might be interpreted as a loud and clear: "I want those suckers there". Out of my way (that is, out of the tasklist) but not too hidden (especially among other apps/windows, the reason why groups suck hard) because I might feel like checking it at any time. Now, don't get me wrong, I don't care about why it started. I just want it to continue, for the reasons I stated in the beginning. And I really think it is on everybody's best interest that this search gets successful because the more diversity you have, the easier it is for everyone to choose what pleases them the most. For users like me, we'll always have Pari... other distros, I mean :P

---

### Post by ronacc on 2010-04-22
> **bash said:**
> To all the people complaining that this is taking away users freedom and limiting choice:

Ubuntu is not about making everything the way you personally want it to be or even about giving you the option to do it.

****** Ubuntu is about doing things the way the Ubuntu developers and "leaders" want. *********

Quite a few users don't seem to want realize or understand this. Reminds me a lot of this post on the Fedora Devel Mailing List:

[https://www.redhat.com/archives/fedora-devel-list/2008-January/msg00861.html](https://www.redhat.com/archives/fedora-devel-list/2008-January/msg00861.html)

and the developers and "leaders" who feel that they can ignore the users need to visit this site [http://distrowatch.com/](http://distrowatch.com/) and contemplate the fact that they are not the "only game in town" .

---

### Post by zekopeko on 2010-04-22
> **ronacc said:**
> and the developers and "leaders" who feel that they can ignore the users need to visit this site [http://distrowatch.com/](http://distrowatch.com/) and contemplate the fact that they are not the "only game in town" .

Why yes I would say they can. As Shuttleworth aptly put it: this isn't a democracy. And you are a minority. Loud one but a minority.

---

### Post by toupeiro on 2010-04-22
> **zekopeko said:**
> Why yes I would say they can. As Shuttleworth aptly put it: this isn't a democracy. And you are a minority. Loud one but a minority.


That's quite the slippery slope considering Ubuntu touts itself as "being for human beings" if it continues to take the stance that the opinions of the human beings using Ubuntu are a minority and don't matter.  Just rename the slogan to "Ubuntu: Mark Shuttleworth's baby, eat it and shut up." and quite frankly, I'll be much happier.  At least we'll know, very plainly, where we stand.  Don't sell software freedom with a side of shut the hell up, because that is not what FOSS is all about.  If I wanted that, I'd buy a RHEL subscription.

---

### Post by ProNux on 2010-04-22
I won't be surprised anyway if they will bring back the 'notification area" after 7-10 years.  It's just like the colored TV sets housing.  Black was the norm, then after 3 years, it's silver / white.  Then 3 more years then it's black again.

---

### Post by antenna on 2010-04-22
I agree with the goals of this, the systray was always one of the worst parts of Windows and I would never wish for that again.  [This article]("http://ploum.frimouvy.org/?219#rev-pnote-219-5") describes the problems well.  There are going to be those that complain and insist their IRC client and such need to be in there, but it makes for inconsistency when some applications close and go there and some don't, some have a right click menu and some don't, etc... nightmare.
It also doesn't really make much sense when the taskbar/window list is available, and if it's something you want to keep out of sight just move it to another workspace.

---

### Post by zekopeko on 2010-04-22
> **toupeiro said:**
> That's quite the slippery slope considering Ubuntu touts itself as "being for human beings" if it continues to take the stance that the opinions of the human beings using Ubuntu are a minority and don't matter.  Just rename the slogan to "Ubuntu: Mark Shuttleworth's baby, eat it and shut up." and quite frankly, I'll be much happier.  At least we'll know, very plainly, where we stand.  Don't sell software freedom with a side of shut the hell up, because that is not what FOSS is all about.  If I wanted that, I'd buy a RHEL subscription.

Ok then.Lets do it your way. What is FOSS about?

---

### Post by BrokenKingpin on 2010-04-22
I do not like the idea with the permanent notification menus. I personally like how it is done now, as long the the application in question gives you the option of displaying it in the notification area or not.

---

### Post by 23meg on 2010-04-22
> **BrokenKingpin said:**
> I do not like the idea with the permanent notification menus. I personally like how it is done now, as long the the application in question gives you the option of displaying it in the notification area or not.

And believe it or not, all applications using application indicators let you choose whether or not to display their indicators in their preferences, just like they (used to) do with notification area icons. 

Opposed to how the "They're taking away my choice!!1111" people will have you believe, it's not Mark Shuttleworth dictating how your beloved application should behave in the indicator applet; it's still ultimately up to application developers, who are simply provided [a set of guidelines]("https://wiki.ubuntu.com/CustomStatusMenuDesignGuidelines") as to how to make best use of the functionality, and [the specification]("https://wiki.ubuntu.com/DesktopExperienceTeam/ApplicationIndicators") explicitly [states]("https://wiki.ubuntu.com/CustomStatusMenuDesignGuidelines#How%20should%20people%20hide%20the%20menu?") that the user should be able to toggle the indicator in the preferences dialog of each application. You know, exactly like they could with notification area icons.

---

### Post by Luke has no name on 2010-04-22
> **emarkay said:**
> Is this Apple? "Do it our way or no way".
Or is this Microsoft: "Do it this way because we have always done it this way, but now we are changing it because we can". 
Or is it Linux - "We do what the users want, because they make it so"?

Nope, sounds like Ubunutu "Let's try this because it sounds neat-o and makes us look cool".

Where's the logic; the proof of a legit enhancement to and for the end-user?  
Nothing more needs to be discussed.

This is Ubuntu: "Do it our way, or join the community and rationally discuss it, or go to another compatible distribution".

I like the idea. It's really just a clean-up of the notification area implementation.

---

### Post by gashcr on 2010-04-22
> **MacUntu said:**
> And Linux not the only OS. :P



I got an idea: place them in the panel as icons!



Makes perfect sense to me too. :)

And I have a perfect solution for that ;) I just posted it in the OP linked blog

Why not add a right click action to the “close” button, just like the maximize button has now, to have a different behavior when pressed. This way, if you want to “tray” your app, right click on the close button, and it will go at the beggining of the taskbar as an icon only. This way, you can have apps with different level of visibility. When you need apps in the taskbar to be fast and easily visible, minimize it, with the normal behavior and representation we have now. If you just want it to be there for a long while, but don’t really need to click it a lot, “right-close” it, to “iconify” it. 

I wanted to add that, this is pretty similar to sending the app to the tray, so they could even have a different right-click menu, as in the tray, when closed this mode ;)

---

### Post by NCLI on 2010-04-22
To all you guys discussing this passionately: [COLOR="Red"]**JOIN THE AYATANA MAILING-LIST AND MAKE YOURSELF HEARD!!**[/COLOR]

The developers and designers won't hear you here.

---

### Post by x-shaney-x on 2010-04-24
I'm now wondering where this is going to leave other distributions and gnome itself?
If gnome decides to take gnome shell/gnome 3 in a completely different direction  and come up with their own new notification system that is incompatible  with ubuntu, what happens then?

Apps are going to be forced (by ubuntu) to adopt this new system or even support both systems, unless gnome follows ubuntu's lead (which I suspect will happen anyway).
And if gnome do follow then gnome based distros have no option but to follow as well.

Or maybe different distros will all adopt different systems?

The way I see it, with moves like this, whether it turns out well or not) ubuntu are basically making decisions which other distros are forced to follow.
It's not like it's a simple decision of which app to use as default email or chat app, this is something that directly affects ALL distros in the long term.

It may even lead to distros all coming up with their own independent window managers/desktop environments (it has been done before).

---

### Post by 3rdalbum on 2010-04-24
I'm fully in support of this. Having specialised menus for battery, network, communication and audio is a real improvement on the current situation with applications. And it helps immensely with giving an impressive, integrated feel to the system.

Just as the notification area is still available to be added to your panel in Ubuntu 10.04, I'm sure it will continue to be an option in 11.04.

---

### Post by mayanasri on 2010-04-24
I just bought a widescreen so it's not an issue for me anymore. This  idea of theirs is probably thought of to help netbooks and other systems  with smaller screens. I'm just guessing though. One of the very few  drawbacks I found with Gnome was the notification area icons couldn't be  hidden like in Windows XP and KDE4.

[MP3 Music Search Engine](http://www.hunt4tunes.com)

---

