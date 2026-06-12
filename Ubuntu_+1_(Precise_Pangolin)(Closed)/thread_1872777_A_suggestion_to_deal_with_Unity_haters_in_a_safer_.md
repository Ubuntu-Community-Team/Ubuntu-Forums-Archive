---
title: "A suggestion to deal with Unity haters in a safer way"
date: 2011-10-31
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by effenberg0x0 on 2011-10-31
Reading threads in the General Help and other forums I have noticed that users are unaware that Unity is a Compiz Plugin, which can be disabled. It's so obvious, I never thought that people generally don't know that.

So, instead of having unskilled users destroying their systems in suicidal attempts to reinstall older DEs or install lighter DEs, wouldn't it be easier to just let these people know of the one-liner they can cut/paste to disable Unity Plugin (while keeping essential compiz plugins, like the ability to alt+tab, etc) and install the wonderful mac-like Cairo/Docky or whatever people are into instead of the Unity Launcher? 

It certainly would be much safer for the standard end-users. I've been seeing people installing (n)Ubuntu over Ubuntu, removing Compiz, xorg, etc in non-sense attempts to get rid of what, in fact, is simply a Compiz Plugin. It's funny: Some of these attempts even uninstall/reinstall Plymouth, etc.... People get desperate.

We can add to the "one-liner" the gconf setting to move min,max,close to the right of application windows, maybe wget and set an old desktop background back (whatever was the default on Maverick - can't remember) and the only real visual difference between that desktop and what Ubuntu has been for previous releases would be the global panel - which doesn't seem to be the main gripe for most users anyway (majority seems to be working with small screens, notebooks, maximized apps, etc).

Maybe putting a thing like that, in very simple terms, in the stickies in General Help would avoid the ridiculous reports of Unity destroying entire families, burning VGAs, etc. 

Something like "Press CTRL+ALT+T and Paste this command into the terminal to Disable Unity and use Cairo".

At least the users keep the possibility of reactivating Unity at any time. It tends to be less destructive.

Regards,
Effenberg

---

### Post by castrojo on 2011-10-31
I talked to DBO about this last week, as I'm seeing a bunch of people accidentally disabling the plugin and ending up with a broken desktop so it's likely that in 12.04 we'll make it so that checkbox can't be unchecked.

(Also making unity --reset fix compiz as well instead of just unity)

---

### Post by effenberg0x0 on 2011-10-31
> **castrojo said:**
> I talked to DBO about this last week, as I'm seeing a bunch of people accidentally disabling the plugin and ending up with a broken desktop so it's likely that in 12.04 we'll make it so that checkbox can't be unchecked.

(Also making unity --reset fix compiz as well instead of just unity)

That would be great. I do believe (strongly) that people will feel the need to revert to Unity, as they see other people happily using it. A simple checkbox to enable/disable would be the way to go. It will definitely help avoid users from doing crazy things. I've been seeing people removing Ubuntu critical packages and ending up with non functional PCs.

Thanks,
Effenberg

---

### Post by Merk42 on 2011-10-31
Unfortunately a lot of people that want to remove Unity:
A) Want to use GNOME 2's panels
B) Think Canonical are the ones that discontinued the panels in the first place.

---

### Post by teachop on 2011-10-31
I think the term "Unity haters" is unfortunate.

---

### Post by effenberg0x0 on 2011-10-31
> **Merk42 said:**
> Unfortunately a lot of people that want to remove Unity:
A) Want to use GNOME 2's panels
B) Think Canonical are the ones that discontinued the panels in the first place.

Exactly...

I've been defending the idea that most people didn't had a working accelerated desktop enabled in previous versions. Not being aware of what it is or of their own hardware capabilities, they got used to having it customized in a certain way, which became their view of what Ubuntu was in past releases. These users were unaware that, in parallel, other users with working VGA, enough RAM and working setups were already having a totally different experience (Compiz enabled).  

Then these guys upgrade, Compiz is ON, but their PC has not enough RAM, a bag VGA, or simply bad settings (tearing, blocky transition effects, etc). They can't experience a fluid Unity experience. And I doubt they can see that as something that can be worked / fixed / improved in their setup. They're used to Windows: What you see after install is the default experience - Nothing can be changed / improved.

But hardware on stores in the last two years supports Compiz/Unity fluid experiences. I can't find a desktop/notebook on sale right now that has a VGA that won't be able to support Compiz decently. PCs with 1GB of RAM or less are not common anymore too.

So I think it's just a temporary thing. As people get to see other users running accelerated desktops, with different features and ways of doing things, they may want to try again. My main concern is that, in the middle of all that, they are destroying their setups with non-sense uninstalls of unrelated packages, etc.

Regards,
Effenberg

---

### Post by effenberg0x0 on 2011-10-31
> **teachop said:**
> I think the term "Unity haters" is unfortunate.

Lol, sorry if it offends you, seriously. But really, that's what it is. There's a mail-list in my country with this exact name (translated to my language of course). Most forums have Homeric fights between Unity-Likers and Unity-Haters and things get surprisingly emotional. The reports are the funniest things you'll ever see: "Canonical betrayed us", "Let's all move to Mint", "Let's fork Ubuntu", "Unity burned my VGA", "Destroyed my HDD", "Wrote to my BIOS", "Made me loose data", etc. While there's a lot of acceptable ignorance in IT and Linux, there's a large portion of that that are purely fake reports created by users that want to create havoc... out of pure hate.

---

### Post by philinux on 2011-10-31
> **effenberg0x0 said:**
> Lol, sorry if it offends you, seriously. But really, that's what it is. There's a mail-list in my country with this exact name (translated to my language of course). Most forums have Homeric fights between Unity-Likers and Unity-Haters and things get surprisingly emotional. The reports are the funniest things you'll ever see: "Canonical betrayed us", "Let's all move to Mint", "Let's fork Ubuntu", "Unity burned my VGA", "Destroyed my HDD", "Wrote to my BIOS", "Made me loose data", etc. While there's a lot of acceptable ignorance in IT and Linux, there's a large portion of that that are purely fake reports created by users that want to create havoc... out of pure hate.

I've seen some outlandish comments out there too.
Unity seems to have managed to split people into two camps.

Bit like marmite does. Some love it and some dislike it with a venom.

Once Unity matures I think more people will come to like it.

Now enough of that back on topic please all.

---

### Post by lucazade on 2011-10-31
@effenberg0x0
Having an accelerated desktop doesn't change the way you use the pc, doesn't help making anything smoother or achiving any task in a faster way.
It only add bling and kill you video driver performance.. just take a look at scrolling speed with gtkperf or flash video playback when in 1080p and fullscreen.
It doesn't matter if it is a low end atom or a 6 core and SLI gfx setup.. it only kill performance just for the sake of a sparkling desktop. I don't need it.. my pc, as a tool, has only to complete tasks in the fastest possible way.

---

### Post by mc4man on 2011-10-31
> **castrojo said:**
> I talked to DBO about this last week, as I'm seeing a bunch of people accidentally disabling the plugin and ending up with a broken desktop so it's likely that in 12.04 we'll make it so that checkbox can't be unchecked.


It would then be interesting to see how that change  extends to the 'default' profile where by default the unity plugin is not enabled.
Ie. - will an ubuntu session require the unity plugin be enabled, or only if/when the user is using the unity profile?

---

### Post by rg4w on 2011-10-31
> **teachop said:**
> I think the term "Unity haters" is unfortunate.
Interestingly, when posters use similarly dismissive and disparaging terms for those who think Unity is fine as it is, their posts are often penalized.

Can we ask for a more egalitarian application of the Code of Conduct?

And really, enforcement should be the least concern for a community.  Shouldn't we all make an effort to weigh varying opinions on their own merit without being dismissive or disparaging?

Unity is an interesting experiment, but it's benefits are not unquestionable.  It seems natural, and indeed healthy, that there are a wide variety of opinions about it.  Dismissing those that don't follow one particular view risks missing what may be significant opportunities for improvement.

---

### Post by cariboo on 2011-10-31
This thread is starting to drift off topic, please don't.

---

### Post by effenberg0x0 on 2011-10-31
> **lucazade said:**
> @effenberg0x0
Having an accelerated desktop doesn't change the way you use the pc, doesn't help making anything smoother or achiving any task in a faster way.
It only add bling and kill you video driver performance.. just take a look at scrolling speed with gtkperf or flash video playback when in 1080p and fullscreen.
It doesn't matter if it is a low end atom or a 6 core and SLI gfx setup.. it only kill performance just for the sake of a sparkling desktop. I don't need it.. my pc, as a tool, has only to complete tasks in the fastest possible way.

Hi Lucazade :)

I totally agree with you! But what changes is the overall experience. Go into a large IT retail shop, those that keep a lot of desktops, laptops, tablets, smartphones, etc turned on in glassy tables for people to test them. No one cares about Windows 7 black laptops. But there are lines to see how amazing Macs taskbar icons behave as you hover them :) Another example: Until last year, maybe two years ago, people were so mesmerized by the Ubuntu Compiz "Cube", they were recording / posting their cube demo in youtube!

On the other hand, it sure is hard to sell the "bling" desktop idea to corporate PCs, professional use: Devs, government, large companies: In these segments, no one wants to waste performance. CIOs also hate the idea of having Music, Photos, etc in the dash when they should have ERP, CRM, etc...

But again, considering the standard user, a guy that has no idea what RAM, VGA is, but looks for a beautiful experience, aesthetics, effects, like in a mac. If he can't have that immediately after install, whose fault is that in his opinion? Canonical, Ubuntu, me and you (testers), etc. He doesn't know his hardware may not be adequate, or that things can be improved, that there are workarounds, that he can keep same Ubuntu version but disable some things, even Unity, etc. They hate it, they feel betrayed, they feel the update broke their PC. **And they don't know what to do next.**

Which is why I'm proposing that, instead of trying to deal with so many problems that arise from that, we change and align the communication to a new line: "Look, your PC is OK, if you don't like Unity, that's OK too, run this small command to disable it, install another launcher, etc, and you got your desktop working very similarly to what you got used to - while still using Ubuntu. There's no need to uninstall Ubuntu or install XUbuntu over Ubuntu, and break everything, etc...". And if he evers feel like trying Unity again, the system will still be capable of easily activating it, etc. It sounds to me like a more manageable way to deal with the situation of average non-technical users than ask the guy to install another DE, remove compiz, etc.

---

### Post by lucazade on 2011-10-31
Ok.. this sounds reasonable.. first impact is important, especially for new adopters that will judge the entire os from its interface. But we have to find a compromise between beauty and performance, on linux we usually have poor written video drivers compared to windows so compiz/nux/unity usually kills 2D rendering. Let's hope wayland will bring a better platform for this kind of things.

---

### Post by demosthene1 on 2011-10-31
It is so easy to ditch unity. Install xubuntu. Actually, I do hate unity. I've tried to like it but I can't. I don't understand the point of unity. Why make your programs a mystery? What was so bad with having categorized list of your programs? Why lock the user out of personalizing their desktop? Why didn't the developers at least make the menu bar work right, like a Mac's?

So yes, I do hate unity. It is the most poorly conceived desktop design I've ever encountered.

---

### Post by effenberg0x0 on 2011-10-31
> **lucazade said:**
> Ok.. this sounds reasonable.. first impact is important, especially for new adopters that will judge the entire os from its interface. But we have to find a compromise between beauty and performance, on linux we usually have poor written video drivers compared to windows so compiz/nux/unity usually kills 2D rendering. Let's hope wayland will bring a better platform for this kind of things.

You know how Windows has some sort of an "Experience Index"? I think it would be great if something like that was available for Ubuntu. What if, during install, the user had the opportunity to see that he would get a low experience index in his current hardware and had, right there, the opportunity to enable or disable some things? Maybe he would make a more educated decision, he would know whats going on, and even consider if he needs new hardware or accepts to trade visuals for performance, etc.

---

### Post by ronacc on 2011-10-31
I freely admit to being a unity hater but to all of us who don't like it take a look at the launcer in the windows 8 dev prev and you will see that they could have made unity even worse .

---

### Post by tekstr1der on 2011-10-31
> **ronacc said:**
> I freely admit to being a unity hater but to all of us who don't like it take a look at the launcer in the windows 8 dev prev and you will see that they could have made unity even worse .

Likewise, take a look at the launcher in Windows 7 and see that they could have made unity even better.

---

### Post by NTL2009 on 2011-10-31
> **effenberg0x0 said:**
> 
So, instead of having unskilled users destroying their systems in suicidal attempts to reinstall older DEs or install lighter DEs, wouldn't it be easier to just let these people know of the one-liner they can cut/paste to disable Unity Plugin (while keeping essential compiz plugins, like the ability to alt+tab, etc) and install the wonderful mac-like Cairo/Docky or whatever people are into instead of the Unity Launcher? 

....

Something like "Press CTRL+ALT+T and** Paste this command** into the terminal to Disable Unity and use Cairo".

At least the users keep the possibility of reactivating Unity at any time. It tends to be less destructive.

Regards,
Effenberg

Are you saying that such a command exists (please excuse my ignorance)? If so - please tell us!

I've loaded 11.10 on an external drive to try it out, and ended up installing Kubuntu (kde-desktop), but that is extra effort and a learning curve also. I'd love to get my old customized panel set ups back from my 10.04 Ubuntu install, and update to the latest greatest from 11.10.

Nothing against Unity, if others like it that's great. But I have a set up that's very efficient for the way I work, and it depends on the drop-down application and places menu, and the work-space switcher (which isn't bad in 11.10) and some other panels. I just want this capability back (I've got my Kubuntu pretty close).

-NTL2009

---

### Post by effenberg0x0 on 2011-10-31
> **NTL2009 said:**
> Are you saying that such a command exists (please excuse my ignorance)? If so - please tell us!

I've loaded 11.10 on an external drive to try it out, and ended up installing Kubuntu (kde-desktop), but that is extra effort and a learning curve also. I'd love to get my old customized panel set ups back from my 10.04 Ubuntu install, and update to the latest greatest from 11.10.

Nothing against Unity, if others like it that's great. But I have a set up that's very efficient for the way I work, and it depends on the drop-down application and places menu, and the work-space switcher (which isn't bad in 11.10) and some other panels. I just want this capability back (I've got my Kubuntu pretty close).

-NTL2009
Yes, of course there is. My question is: Should we help users in such a way? The alternative seems to be unhelpful (use Unity anyway) or too hard / risky (install another DE, etc). 

Without putting too much thought in it, but something like this will probably get users to a more familiar desktop?

With Cairo:
```
PLUGINS=$(gconftool-2 --get /apps/compiz-1/general/screen0/options/active_plugins | sed 's/,unityshell//') && sudo apt-get install cairo-dock && gconftool-2 --set --type=string /apps/metacity/general/button_layout "menu:minimize,maximize,close" && gconftool-2 --type=list --list-type=string --set /apps/compiz-1/general/screen0/options/active_plugins $PLUGINS ; cairo-dock &
```Or maybe the user wants his gnome-panel back:
```
PLUGINS=$(gconftool-2 --get /apps/compiz-1/general/screen0/options/active_plugins | sed 's/,unityshell//') && sudo apt-get install gnome-panel && gconftool-2 --set --type=string /apps/metacity/general/button_layout "menu:minimize,maximize,close" && gconftool-2 --type=list --list-type=string --set /apps/compiz-1/general/screen0/options/active_plugins $PLUGINS ; gnome-panel &
```Or both, who knows.

Does anyone has a Unity desktop there to test? I'm on ssh to Linux machine from Windows, no $DISPLAY to test...  But anyway, one can add a background change to this one-liner, change minimal stuff you know... disable / enable Compiz plugins in a more intelligent way, etc. A one-liner like that can avoid users from installing / unistalling heavy stuff. That's my point. 


Thanks,
Effenberg


**EDIT**: Forgot to provide a way for users to revert above stuff:

[B]Revert Cairo test:
[/B]```
PLUGINS2=$(gconftool-2 --get /apps/compiz-1/general/screen0/options/active_plugins | sed 's/]/,unityshell]/') && killall -s KILL cairo-dock && sudo apt-get remove --purge cairo-dock && gconftool-2 --set --type=string /apps/metacity/general/button_layout "close,maximize,minimize" && gconftool-2 --type=list --list-type=string --set /apps/compiz-1/general/screen0/options/active_plugins $PLUGINS2
```[B]Revert gnome-panel test:
[/B]```
PLUGINS2=$(gconftool-2 --get /apps/compiz-1/general/screen0/options/active_plugins | sed 's/]/,unityshell]/') && killall -s KILL gnome-panel && sudo apt-get remove --purge gnome-panel && gconftool-2 --set --type=string /apps/metacity/general/button_layout "close,maximize,minimize" && gconftool-2 --type=list --list-type=string --set /apps/compiz-1/general/screen0/options/active_plugins $PLUGINS2
```**EDIT2:** Tested. Works ok... If I were to recommend such a thing I would just edit the above code to set small things, like background, put / remove stuff from startup applications, etc... It's not about the "code" itself, but the safest policy to take with those that will not accept Unity and demand their old looks back...

---

### Post by Atamisk on 2011-10-31
I'd be interested to see how disabling the checkbox would affect other installed sessions using compiz. Please consider this before making it un-uncheckable! I'd really rather not have my XFCE session break =/

OT: Then again, Xfce's CCSM profile is flat-file, and Unity still uses gconf, so i don't know what would happen....

---

### Post by tekstr1der on 2011-10-31
> **effenberg0x0 said:**
> ...I'm on ssh to Linux machine from Windows, no $DISPLAY to test...

If you're on a machine at work where you aren't allowed to install software, Xming has a portable version that can be configured to run without any installer/registry access necessary.
[http://www.straightrunning.com/XmingNotes/portableputty.php](http://www.straightrunning.com/XmingNotes/portableputty.php)

Very handy for forwarding X sessions while at work or when visiting someone when Windows is the only option. Just need a USB flash drive and good to go.

---

### Post by effenberg0x0 on 2011-10-31
> **tekstr1der said:**
> If you're on a machine at work where you aren't allowed to install software, Xming has a portable version that can be configured to run without any installer/registry access necessary.
[http://www.straightrunning.com/XmingNotes/portableputty.php](http://www.straightrunning.com/XmingNotes/portableputty.php)

Very handy for forwarding X sessions while at work or when visiting someone when Windows is the only option. Just need a USB flash drive and good to go.

Thanks, good tip. I normally do remote GUI via NX on my windows laptop but I was at a conf call room posting from a tablet, which actually is unusable. Anyway, I tested the thing here on pp, works ok. No unity, gnome-panels activated, etc.

---

### Post by gsmanners on 2011-10-31
> **effenberg0x0 said:**
> Yes, of course there is ...

How about we package these scripts into one convenient zenity script that you can easily install/use? Doesn't seem too unreasonable. Then, when you see a "hater" thread, you can simply link them to that download.

---

### Post by effenberg0x0 on 2011-10-31
> **gsmanners said:**
> How about we package these scripts into one convenient zenity script that you can easily install/use? Doesn't seem too unreasonable. Then, when you see a "hater" thread, you can simply link them to that download.

Sure, easy to do. We can improve it a little, of course...Add some more compiz settings to disable the heavy stuff, deal with some unnecessary startup apps, then host it, put it on ppa, etc, not a prob. I was just wondering if it's the right thing to do strategically. Maybe Ubuntu people prefer people to attempt installs of xubuntu, lubuntu, or want them to stay with Unity anyway, etc? I really wouldn't know. Which is why it's just a suggestion to see if people align with. It just sounds safer to me because no DE is installed/removed.

---

### Post by gsmanners on 2011-10-31
Why not give people every option? Alt. desktops and fixer scripts? Sounds like the way to go to me.

---

### Post by MacUntu on 2011-10-31
It's not that difficult to deal with it:
[LIST][*]If people are asking for help, answer their questions.[*]If people are misinformed, clear things up.[*]If people want to leave constructive criticism, send them to the right places (brainstorm/Ayatana mailing list/Launchpad).[*]If people hate/troll, ignore them.
[/LIST]
I don't waste a second on haters or trolls.

---

### Post by kansasnoob on 2011-10-31
> **teachop said:**
> I think the term "Unity haters" is unfortunate.

+OneMillion!

---

### Post by vasa1 on 2011-10-31
> **MacUntu said:**
> It's not that difficult to deal with it:
[LIST][*]If people are asking for help, answer their questions.[*]If people are misinformed, clear things up.[*]If people want to leave constructive criticism, send them to the right places (brainstorm/Ayatana mailing list/Launchpad).[*]If people hate/troll, ignore them.
[/LIST]
I don't waste a second on haters or trolls.

The problem comes with those posts that have a genuine need tucked away under layers of unnecessary commentary peppered with, "I simply hate this" or, "I just despise that", or, "I've been using Linux since I was in nappies but this is just ... ".

---

### Post by pommie on 2011-10-31
Just an idea, would it be possible to release a live iso that contains all the officially supported flavours of Ubuntu, with an opening page describing each desktop, then the end user can try them all before installing their choice.
I realize that it would be to big for a cd, but dvd's are cheap and the different flavours contain largely the same coding for each, so what 1.5gig ?? <--<< pure guesswork :)
That would eliminate any "hate" posts as they would have no excuse for not trying another flavour.
Personally I am now on Xubnutu, not because I dislike Unity but because I prefer a classic menu system and have no need to be 'seen to be cool', been there, done that, first DE was GEOS on the Commadore64 :lolflag:

Cheers David

---

### Post by PRC09 on 2011-10-31
I personally dont believe you will get any official permission or such to implement any of your proposed solutions.The Unity interface is designed to be used across all platforms,be it desktop,netbook ,notebook,tablet or phone.This in my mind is the major reason for the lack of customization as well.This would also fit with the ability to offer support to OEM distributions.One desktop as default with very little you could muck with....



> Shuttleworth explained, “Unity has a strong design vision and part of that is to provide coherent screens across platforms. While it’s not one size fit all a common design is vital to it.” Still, “Nothing is cast in stone. Still, since Unity on the desktop is part of a greater whole, we look at the experience as a whole.” So, “We want a consistent platform with a tightly structured user experience.”

[http://m.zdnet.com/blog/open-source/ubuntu-linux-heads-to-smartphones-tablets-and-smart-tvs/9834](http://m.zdnet.com/blog/open-source/ubuntu-linux-heads-to-smartphones-tablets-and-smart-tvs/9834)

---

### Post by gsmanners on 2011-10-31
> **PRC09 said:**
> The Unity interface is designed to be ...

I highly doubt anyone actually using "Ubuntu" Linux cares what it was designed to do. I think what people want to know is what it CAN do. This is probably how we can best solve their frustrations.

To my mind, it makes sense to make Unity more flexible in whatever way we can. We need to really listen to what people are telling us are their technical problems, figure out a way to solve them, and then just do it. Otherwise, what's the point?

---

### Post by cariboo on 2011-10-31
> **PRC09 said:**
> I personally dont believe you will get any official permission or such to implement any of your proposed solutions.The Unity interface is designed to be used across all platforms,be it desktop,netbook ,notebook,tablet or phone.This in my mind is the major reason for the lack of customization as well.This would also fit with the ability to offer support to OEM distributions.One desktop as default with very little you could muck with....





[http://m.zdnet.com/blog/open-source/ubuntu-linux-heads-to-smartphones-tablets-and-smart-tvs/9834](http://m.zdnet.com/blog/open-source/ubuntu-linux-heads-to-smartphones-tablets-and-smart-tvs/9834)

This planned for 14.04, lets not jump the gun, it may not even be useful yet in the next 2 years. 

In that time, there will be third parties that will have stepped in to create utilities to modify the Unity desktop, witness the ability to move the launcher to the bottom, as posted here:

[http://www.webupd8.org/2011/10/how-to-move-unity-launcher-to-bottom-of.html](http://www.webupd8.org/2011/10/how-to-move-unity-launcher-to-bottom-of.html)

I doubt if there was any official permission given for this hack, but its there none the less.

---

### Post by MacUntu on 2011-11-01
> **vasa1 said:**
> The problem comes with those posts that have a genuine need tucked away under layers of unnecessary commentary peppered with, "I simply hate this" or, "I just despise that", or, "I've been using Linux since I was in nappies but this is just ... ".

Ignore the commentary or ignore the post. :-)

---

### Post by tkoco on 2011-11-01
As a long time user of Linux, I have seen many changes to the desktop over the years. Hate/Like Unity? Nether! If I wanted a locked desktop, I would buy MS Windows. NO, it is about choices. I want a choice between installing (or activating Unity) vs plain old fashion desktop.

Everyone saw the same thing happen when pulseaudio first came out. Pulseaudio was too raw. I waited 2 releases before allowing pulseaudio to manage the audio on my system. It just needed better integration and more mature coding.

IMHO, unity is in the same situation.The other thing which needs to happen on these forums is a "mega" help thread to assist those of us who desire to tweak the unity desktop.

---

### Post by NTL2009 on 2011-11-01
> **tkoco said:**
>  .... Hate/Like Unity? Nether!  ... it is about choices. I want a choice between installing (or activating Unity) vs plain old fashion desktop.

... The other thing which needs to happen on these forums is a "mega" help thread to assist those of us who desire to tweak the unity desktop.

Agree totally. A positive thread about how to customize it to an individual's preference would be great. A wiki would make a good reference for the current 'best practices' summary - long threads are great for troubleshooting and throwing around ideas, but get unwieldy for actually finding summary info.

I've been using Lucid as my everyday system for over a year, and I really like it. I won't 'upgrade' until I the features I use everyday are available.

Right now, I'm trying out Kubuntu, Xubuntu, and XFCE on an external drive. But I'm just not that 'up' on all this stuff, know only a little of the 'under the hood' stuff, so it's a lot of time consuming trial-and-error and googling. Many people would just not bother. I think a good way to grow the user base would be to have a nice concise summary of the customization options, with examples and pros/cons/limits of each.

I'll try out some of the ideas in this thread later.

-NTL2009

---

### Post by keithpeter on 2011-11-01
> **effenberg0x0 said:**
> You know how Windows has some sort of an "Experience Index"? I think it would be great if something like that was available for Ubuntu. What if, during install, the user had the opportunity to see that he would get a low experience index in his current hardware and had, right there, the opportunity to enable or disable some things? Maybe he would make a more educated decision, he would know whats going on, and even consider if he needs new hardware or accepts to trade visuals for performance, etc.

I think this would be an excellent idea, however I can see that it would be difficult to implement given the on/off nature of 3d acceleration.

---

### Post by effenberg0x0 on 2011-11-01
> **keithpeter said:**
> I think this would be an excellent idea, however I can see that it would be difficult to implement given the on/off nature of 3d acceleration.

I was thinking to evaluate a couple aspects, give them different weights. I'm going simple, using things that already exist, like unity_support_test, gtkperf, etc. Don't have it clear in my mind yet, but maybe:


[LIST=1]
[*]**CPU:** 1GHz (easy to check)
[*]**RAM:** Minimum 1GB (easy to check)
[*]**Video**
[/LIST]

[LIST]
[*]**VGA must not be blacklisted** (easy to check)
[*]**Minimum OpenGL version**: 1.4 (easy to check)
[*] **Unity Reqs**: fbconfig, texture from pixmap, npot or rect textures, vertex program, fragment program, vertex buffer object, framebuffer object (easy to check, using unity_support_test output)
[*]**GTKPerf:** Minimum Performance (easy to check, using gtkperf output): I would have to evaluate how a very fast / very slow PC performs. No idea on the numbers. Mine are below, but it's a fast PC/CPU/GPU.
[/LIST]
> 
GtkEntry - time:  0,02GtkComboBox - time:  1,01
GtkComboBoxEntry - time:  0,61
GtkSpinButton - time:  0,03
GtkProgressBar - time:  0,01
GtkToggleButton - time:  0,04
GtkCheckButton - time:  0,04
GtkRadioButton - time:  0,07
GtkTextView - Add text - time:  0,53
GtkTextView - Scroll - time:  0,05
GtkDrawingArea - Lines - time:  0,26
GtkDrawingArea - Circles - time:  0,61
GtkDrawingArea - Text - time:  0,15
GtkDrawingArea - Pixbufs - time:  0,09
 --- 
Total time:  3,53


Then once this numbers are somehow balanced, we *should* be able to say if, by proceeding with login, user will or will not have a fluid Unity experience, considering his current hardware performance. Maybe the whole if item 3, with all its subitems, will be responsible for more than 50% of the evaluation. 

I still have to think a lot.

---

### Post by keithpeter on 2011-11-01
> **effenberg0x0 said:**
> I was thinking to evaluate a couple aspects, give them different weights. I'm going simple, using things that already exist, like unity_support_test, gtkperf, etc. Don't have it clear in my mind yet, but maybe:


[LIST=1]
[*]**CPU:** 1GHz (easy to check)
[*]**RAM:** Minimum 1GB (easy to check)
[*]**Video**
[/LIST]

[LIST]
[*]**VGA must not be blacklisted** (easy to check)
[*]**Minimum OpenGL version**: 1.4 (easy to check)
[*] **Unity Reqs**: fbconfig, texture from pixmap, npot or rect textures, vertex program, fragment program, vertex buffer object, framebuffer object (easy to check, using unity_support_test output)
[*]**GTKPerf:** Minimum Performance (easy to check, using gtkperf output): I would have to evaluate how a very fast / very slow PC performs. No idea on the numbers. Mine are below, but it's a fast PC/CPU/GPU.
[/LIST]


Then once this numbers are somehow balanced, we *should* be able to say if, by proceeding with login, user will or will not have a fluid Unity experience, considering his current hardware performance. Maybe the whole if item 3, with all its subitems, will be responsible for more than 50% of the evaluation. 

I still have to think a lot.

OK, how would your script classify this system?

T60-1952 thinkpad, 1Gb ram, dual core 1.83GHz, GMA950 (reported as 'driver unknown' by system information). I've logged in as Unity 2d but not that much more responsive than 3d. Both better than Win7!

```
GtkPerf 0.40 - Starting testing: Tue Nov  1 22:10:45 2011

GtkEntry - time:  0.04
GtkComboBox - time:  1.82
GtkComboBoxEntry - time:  1.44
GtkSpinButton - time:  0.14
GtkProgressBar - time:  0.14
GtkToggleButton - time:  1.16
GtkCheckButton - time:  0.17
GtkRadioButton - time:  0.28
GtkTextView - Add text - time:  1.12
GtkTextView - Scroll - time:  0.16
GtkDrawingArea - Lines - time:  2.22
GtkDrawingArea - Circles - time:  4.24
GtkDrawingArea - Text - time:  0.68
GtkDrawingArea - Pixbufs - time:  0.22
 --- 
Total time: 13.84
```

---

### Post by effenberg0x0 on 2011-11-01
> **keithpeter said:**
> OK, how would your script classify this system?

T60-1952 thinkpad, 1Gb ram, dual core 1.83GHz, GMA950 (reported as 'driver unknown' by system information). I've logged in as Unity 2d but not that much more responsive than 3d. Both better than Win7!

```
GtkPerf 0.40 - Starting testing: Tue Nov  1 22:10:45 2011

GtkEntry - time:  0.04
GtkComboBox - time:  1.82
GtkComboBoxEntry - time:  1.44
GtkSpinButton - time:  0.14
GtkProgressBar - time:  0.14
GtkToggleButton - time:  1.16
GtkCheckButton - time:  0.17
GtkRadioButton - time:  0.28
GtkTextView - Add text - time:  1.12
GtkTextView - Scroll - time:  0.16
GtkDrawingArea - Lines - time:  2.22
GtkDrawingArea - Circles - time:  4.24
GtkDrawingArea - Text - time:  0.68
GtkDrawingArea - Pixbufs - time:  0.22
 --- 
Total time: 13.84
```

Doing the code in whatever language is easy, the classification is the issue, because we don't have all possible VGAs, to see what they output as result. In fact an hour ago I was thinking of somethings: 


Idea 1) What if I underclock a VGA until the use of the session becomes unbearable, even with all the Compiz plugins unloaded? I know it's not precise, but I'd probably get a very high result number in gtpperf for example. Then I could start to raise it's clock little by little, until I reach a usable performance. This number would be a starting point.

Idea 2) Use a xml or something very open for the calculation of the index, but leave it disabled. That way, as people eventually use and get results (10, 100, 100.000), I could get a more precise idea of min, max and average results. Then, at this point, having a sample, it would be easier to code the math to transform them into a 0-10 index.

Idea 3) I want to put it into LightDM. That way, the user will have the option to choose between sessions while seeing his hardware capability / experience index. There's a lot of free space in lightdm. 

Idea 4) In lightdm, as user selects an existing session in the current dropbox, he will see a picture of the session in the right, the name of it, the explanation of what that session is (accelerated, non-accelerated, etc) and the requirements, as well as a button to "test my hardware".

lightdm can be as it is, I just have to mess with the greeter. The greeter is vasa, which is easy because it's like more or less like C, but can also (and even more easily) be messed with using the webkit, which would be even faster in terms of rad.

I'm gonna see if i can find some time to do an alpha of it next week.

---

### Post by cariboo on 2011-11-01
I find it saddening that people don't use the information that is already available via the Ubuntu wiki. There are several pages available concerning hardware requirements for Unity.

Check this page published by the desktop experience team:

[https://wiki.ubuntu.com/DesktopExperienceTeam/UnityHardwareRequirements](https://wiki.ubuntu.com/DesktopExperienceTeam/UnityHardwareRequirements)

---

### Post by madjr on 2011-11-01
> **cariboo907 said:**
> I find it saddening that people don't use the information that is already available via the Ubuntu wiki. There are several pages available concerning hardware requirements for Unity.

Check this page published by the desktop experience team:

[https://wiki.ubuntu.com/DesktopExperienceTeam/UnityHardwareRequirements](https://wiki.ubuntu.com/DesktopExperienceTeam/UnityHardwareRequirements)

umm but "some" people only "read stuff" when things go really bad.

so if people wont do it, is better if the computer/os was **smarter** and did it for them (check the requirements are met, not read for them lol), because in the end a computer is suppose to be *"an **artificial brain** created by humans to make their life easier and delegate tasks for it to handle"*(normal user)... and we many times **forget** that and think is the other way around: delegate more tasks to humans to make the machines life easier (hobbyist)...

---

### Post by effenberg0x0 on 2011-11-01
@cariboo I agree, but, people are people... I gave up writing tutorials, wiki, etc some time ago becaause of this frustration. But if somehow we can put it right on the user screen, before login, an experience index with and advise that things might go wrong if he chooses session X, but will be OK if he uses session Y, it probably would be more effective for a group of people. Others will try it anyway, who knows.

---

### Post by effenberg0x0 on 2011-11-01
Look at this thread: [http://ubuntuforums.org/showthread.php?t=1871442](http://ubuntuforums.org/showthread.php?t=1871442)
Then see the advice the guy got. And then what happened as he did the commands.

It's sad....And that was light. I've seen people breaking the system in heavier ways.

But anyway, that's what I was considering in this thread. Shouldn't they know that it is just a damn plugin? :)

---

### Post by PayPaul on 2011-11-01
> **effenberg0x0 said:**
> Reading threads in the General Help and other forums I have noticed that users are unaware that Unity is a Compiz Plugin, which can be disabled. It's so obvious, I never thought that people generally don't know that.

So, instead of having unskilled users destroying their systems in suicidal attempts to reinstall older DEs or install lighter DEs, wouldn't it be easier to just let these people know of the one-liner they can cut/paste to disable Unity Plugin (while keeping essential compiz plugins, like the ability to alt+tab, etc) and install the wonderful mac-like Cairo/Docky or whatever people are into instead of the Unity Launcher? 

It certainly would be much safer for the standard end-users. I've been seeing people installing (n)Ubuntu over Ubuntu, removing Compiz, xorg, etc in non-sense attempts to get rid of what, in fact, is simply a Compiz Plugin. It's funny: Some of these attempts even uninstall/reinstall Plymouth, etc.... People get desperate.

We can add to the "one-liner" the gconf setting to move min,max,close to the right of application windows, maybe wget and set an old desktop background back (whatever was the default on Maverick - can't remember) and the only real visual difference between that desktop and what Ubuntu has been for previous releases would be the global panel - which doesn't seem to be the main gripe for most users anyway (majority seems to be working with small screens, notebooks, maximized apps, etc).

Maybe putting a thing like that, in very simple terms, in the stickies in General Help would avoid the ridiculous reports of Unity destroying entire families, burning VGAs, etc. 

Something like "Press CTRL+ALT+T and Paste this command into the terminal to Disable Unity and use Cairo".

At least the users keep the possibility of reactivating Unity at any time. It tends to be less destructive.

Regards,
Effenberg

I'm not sure if I understand this correctly. Is there already a way of disabling Unity and also going back to basic gnome in compiz without having a destroyed desktop.? This post seems more like a suggestion than pointing to an actual command or function within compiz. Please clarify if possible. 

I, for one, am not too sure just yet whether I like or dislike Unity. It seems to attempt to mimic Windows behavior in a kind of lopsided way that I'm getting used to. I have seen the much simpler gnome interface which has all the access to things like "applications" on a menu bar at the top. It only took getting used to because Windows puts all that on the bottom of the screen. It's no big deal but it would be nice to have the option of having all that on the bottom if I really wanted to emulate a Windows desktop. But then why did I switch to Ubuntu in the first place? 

I switched to get away from Windows and learn a new OS so this is all part and parcel of it.

---

### Post by effenberg0x0 on 2011-11-01
> **PayPaul said:**
> I'm not sure if I understand this correctly. Is there already a way of disabling Unity and also going back to basic gnome in compiz without having a destroyed desktop.? This post seems more like a suggestion than pointing to an actual command or function within compiz. Please clarify if possible. 

I, for one, am not too sure just yet whether I like or dislike Unity. It seems to attempt to mimic Windows behavior in a kind of lopsided way that I'm getting used to. I have seen the much simpler gnome interface which has all the access to things like "applications" on a menu bar at the top. It only took getting used to because Windows puts all that on the bottom of the screen. It's no big deal but it would be nice to have the option of having all that on the bottom if I really wanted to emulate a Windows desktop. But then why did I switch to Ubuntu in the first place? 

I switched to get away from Windows and learn a new OS so this is all part and parcel of it.

Hi Paul, 

Yes, there is. It's not a hidden system feature or anything, just standard commands. Unity runs as a plugin to Compiz in the Ubuntu session. I have posted a small one-liner, in post #20, that in one simple cut/paste to the terminal uses gconf to disable this plugin, moves min,max,close buttons to the right of the application windows and does some other stuff to download and reactivate traditional gnome-panels (top/bottom, launcher/taskbar)... It's not beautiful code, just a proof of concept, but it woks and proves my point: Users can do something like that and not destroy their systems, while still being able to restore to Unity also with a one-liner. No harm done.

---

### Post by cariboo on 2011-11-02
> **PayPaul said:**
> I'm not sure if I understand this correctly. Is there already a way of disabling Unity and also going back to basic gnome in compiz without having a destroyed desktop.? This post seems more like a suggestion than pointing to an actual command or function within compiz. Please clarify if possible. 

I, for one, am not too sure just yet whether I like or dislike Unity. It seems to attempt to mimic Windows behavior in a kind of lopsided way that I'm getting used to. I have seen the much simpler gnome interface which has all the access to things like "applications" on a menu bar at the top. It only took getting used to because Windows puts all that on the bottom of the screen. It's no big deal but it would be nice to have the option of having all that on the bottom if I really wanted to emulate a Windows desktop. But then why did I switch to Ubuntu in the first place? 

I switched to get away from Windows and learn a new OS so this is all part and parcel of it.

The problem is that there are too many ways, as effenberg0x0 says  pasting a command in a terminal would be the easy way, but for many users, that is something they've never tried, and many are afraid to.

The other easy way is to install gnome-session-fallback, but it also installs gnome-shell as a dependency. Once you install it, select Gnome Classic from the login menu and you'll have what looks like the classic two panel interface. I'd show you a screenshot, but at the moment I'm upgrading my server via ssh, and if I logout and start a different desktop my upgrade will stop.

**Note:** If any one wants to comment on my remote upgrade, I forgot to run screen before starting it, so I'm stuck waiting for it to finish. :)

**Note 2:** I did this in a couple of minutes, check the screenshot

---

### Post by keithpeter on 2011-11-02
> **cariboo907 said:**
> I find it saddening that people don't use the information that is already available via the Ubuntu wiki. There are several pages available concerning hardware requirements for Unity.

Check this page published by the desktop experience team:

[https://wiki.ubuntu.com/DesktopExperienceTeam/UnityHardwareRequirements](https://wiki.ubuntu.com/DesktopExperienceTeam/UnityHardwareRequirements)

Hello cariboo907 and all

We understand that the plan is to have a simple to use desktop that is standardised so that it will be attractive to large numbers of people who currently do not use Linux. As anyone who has any experience at all of end user support in volume, pointing someone at that page is not going to achieve *anything* at all.

I suspect that if Canonical want to be populist, they will have to programme in suggestions. Yes, it's paper-clip time :twisted: Just look forward to the feedback from hard bitten Linux users then :twisted::twisted:

Mac OS X is often referred to in these threads, remember Apple only support a very limited range of hardware that they design themselves.

---

### Post by Hylas de Niall on 2011-11-02
Appeasement?

[http://www.omgubuntu.co.uk/2011/11/ubuntu-desktop-designers-clarify-on-configurability/](http://www.omgubuntu.co.uk/2011/11/ubuntu-desktop-designers-clarify-on-configurability/)

Sorry if this link has been posted elsewhere, but there's news of lots of impending ways to customise Unity, which might just win around some of those 'haters'.

:)

---

### Post by grahammechanical on 2011-11-02
Hi

I know that I have been eavesdropping on a conversation between the big guys (and girls - before someone says that "guys" was an unfortunate remark) but I have come to the opinion that a user should be forced to pass a knowledge test or better still an IQ test before being allowed to seriously modify their system. And I am only half joking.

It seems that we have reached the point where we need a true alternative install ISO where the user gets to choose the User Interface and takes responsibility for the choices he/she makes.

Download 1 = easy install, not too much input from you. Like what you get or lump it.

Download 2 = More complicated install, more decisions by you. If you don't like what you get. Don't complain . It was your choice.

It was well known that 11.10 would be like 11.04 + Unity only more so. So, why upgrade to it if you did not like 11.04 + Unity? I have also noticed since joining this forum that given enough time clever people will work out ways to do things. So, why not wait and let the clever people work out how to change things to the way you like? Why demand that what you want right now? It is this that I do not like.

Regards.

---

### Post by effenberg0x0 on 2011-11-02
Here are two screenshots of what the desktop looks like when the first command I posted is ran. As you can see, there's no unity and the user gets back his top/bottom panels, which act as the Apps & Places launcher and bottom Taskbar. 

See that I'm not an artist like Vin or Lucazade, but you get the idea :)

What @cariboo says is totally true. There are many ways and some may lead to risk of making things worse to the users. You know from what I've been posting that I really can't understand why Unity is so bad for some - I can't get it. And I do question myself all the time how to help users get the best of Ubuntu without going through not only risky procedures but how does teaching them to avoid Unity would align with supporting Ubuntu strategy, which I respect, understand and don't feel like putting myself against. That's what is on my mind and unfortunately I can't find an answer. It's not trivial.

[ATTACH]206138[/ATTACH]

[ATTACH]206139[/ATTACH]

---

### Post by reduz on 2011-11-02
> **pommie said:**
> Just an idea, would it be possible to release a live iso that contains all the officially supported flavours of Ubuntu, with an opening page describing each desktop, then the end user can try them all before installing their choice.


How about working a little on offering users more customization options on the default one (Unity), so most users are pleased with a consistent experience instead of having to maintain 5 separate desktops?

I mean, it obviously seems more reasonable to go that way for Canonical, instead of going the "Don't like the unconfigurable Unity? go use KDE!" route with the "Unity Haters",then ensuring all those alternative Desktops work properly..

I mean, think about it a little..

---

### Post by ventrical on 2011-11-02
> **cariboo907 said:**
> The problem is that there are too many ways, as effenberg0x0 says  pasting a command in a terminal would be the easy way, but for many users, that is something they've never tried, and many are afraid to.

The other easy way is to install gnome-session-fallback, but it also installs gnome-shell as a dependency. Once you install it, select Gnome Classic from the login menu and you'll have what looks like the classic two panel interface. I'd show you a screenshot, but at the moment I'm upgrading my server via ssh, and if I logout and start a different desktop my upgrade will stop.

**Note:** If any one wants to comment on my remote upgrade, I forgot to run screen before starting it, so I'm stuck waiting for it to finish. :)

**Note 2:** I did this in a couple of minutes, check the screenshot


 Linux Mint has an option called 'Compatibility mode' at CD Live start up .. but I think no matter which way we cut the cake , end_users are going to 'go for the gusto' and try to drive their systems to the (n)th degree. That goes for kids and adults alike.!  I think it is redundant to put in memos and paperclips because the 'release-notes' reference is already there and if people are not going to read that then what makes any conceptualist think that they are going to read some pre-reformed revision warmed over from some archaic help file ?

  I think the install system is fine the way it is. I mean , part of the challange is to build ones own preferential system.  The forums, the help and the KB are very exhaustive if anyone chooses to read them. I mean to say .. Canonical has to draw a line somwhere ... certainly  Ubuntu is for all people  but it certainly is not for all computers.

---

### Post by ventrical on 2011-11-02
> **effenberg0x0 said:**
> Here are two screenshots of what the desktop looks like when the first command I posted is ran. As you can see, there's no unity and the user gets back his top/bottom panels, which act as the Apps & Places launcher and bottom Taskbar. 

See that I'm not an artist like Vin or Lucazade, but you get the idea :)

What @cariboo says is totally true. There are many ways and some may lead to risk of making things worse to the users. You know from what I've been posting that I really can't understand why Unity is so bad for some - I can't get it. And I do question myself all the time how to help users get the best of Ubuntu without going through not only risky procedures but how does teaching them to avoid Unity would align with supporting Ubuntu strategy, which I respect, understand and don't feel like putting myself against. That's what is on my mind and unfortunately I can't find an answer. It's not trivial.

[ATTACH]206138[/ATTACH]

[ATTACH]206139[/ATTACH]


 So far I have had several successful rollbacks to Unity 2D on systems who's graphics cards do not support the Unity 3D option - so an older system can still be at pace with the rest of the bleeding edge crowd in the sense that they can still have a functioning PP in a reduced but working mode.


 So if Canonical decides to , say, for instance, put in a start up script "Ubuntu has detected that your computer does not meet hardware specifications to run Unity 3D. Would you like to install in LegacyMode?"  How many people do you think would actually choose this mode on a first run?

---

### Post by PayPaul on 2011-11-02
I suspect I might seriously screw up my installation going into compiz right now and changing things. I'm on a Wubi install now...still.. and have to get up the courage and the willingness to put up with the time consumption to do my reinstall of everything including Windows 7. My PC needs a serious cleaning out. 

BTW, and maybe a little off topic, this morning I had to reboot due to a lockup of the machine and I noticed a number of changes including that my Title Bars are now all gray and the also the icons for the calculator are marketedly different I seem to be using the same version of Ubuntu but things are slightly skewed. It's as if Ubuntu entered another timeline or something sci-fi like that.

Overall I'm not, as I've said, unhappy with Unity but good points have been made here about being able to customize it a little more than is currently possible.

---

### Post by ventrical on 2011-11-02
> **PayPaul said:**
> I suspect I might seriously screw up my installation going into compiz right now and changing things. I'm on a Wubi install now...still.. and have to get up the courage and the willingness to put up with the time consumption to do my reinstall of everything including Windows 7. My PC needs a serious cleaning out. 

BTW, and maybe a little off topic, this morning I had to reboot due to a lockup of the machine and I noticed a number of changes including that my Title Bars are now all gray and the also the icons for the calculator are marketedly different I seem to be using the same version of Ubuntu but things are slightly skewed. It's as if Ubuntu entered another timeline or something sci-fi like that.

Overall I'm not, as I've said, unhappy with Unity but good points have been made here about being able to customize it a little more than is currently possible.


Thanks PayPaul,

  Yes .. it is all about  'courage and willingness' , virtues that a dumb terminal does not have.

  I don't think  I had any problems with Unity  and it's concepts. It some ways it does have a refreshsing quality when it is working properly.

---

### Post by PayPaul on 2011-11-02
> **ventrical said:**
> Thanks PayPaul,

  Yes .. it is all about  'courage and willingness' , virtues that a dumb terminal does not have.

  I don't think  I had any problems with Unity  and it's concepts. It some ways it does have a refreshsing quality when it is working properly.


:lolflag:  
Perhaps I'm feeling like a "dumb terminal" now. Considering the fact that "Terminal" is much more than dumb in Ubuntu I can only say that my *command structure* is a bit faulty at the moment. I'll get around to it sooner or later. I'm also beginning to see that Wubi isn't all it's cracked up to be. If it ***is*** the Wubi installation that is presenting with these mouse and graphics issues that is.

---

### Post by cariboo on 2011-11-02
> **PayPaul said:**
> :lolflag:  
Perhaps I'm feeling like a "dumb terminal" now. Considering the fact that "Terminal" is much more than dumb in Ubuntu I can only say that my *command structure* is a bit faulty at the moment. I'll get around to it sooner or later. I'm also beginning to see that Wubi isn't all it's cracked up to be. If it ***is*** the Wubi installation that is presenting with these mouse and graphics issues that is.

Your problem has nothing to do with wubi, I've had the same thing happen after a couple of updates. Seeing as my Precise install is just for playing around with at the moment, I just deleted the ~/.config directory and logged out, then logged back in again, I lost all the icons I placed in the launcher, and a few other things were missing, but it was a matter of 5 minutes to get everything back the way it was.

---

### Post by gsmanners on 2011-11-02
> **effenberg0x0 said:**
> There are many ways and some may lead to risk of making things worse to the users. You know from what I've been posting that I really can't understand why Unity is so bad for some - I can't get it. And I do question myself all the time how to help users get the best of Ubuntu without going through not only risky procedures but how does teaching them to avoid Unity would align with supporting Ubuntu strategy, which I respect, understand and don't feel like putting myself against. That's what is on my mind and unfortunately I can't find an answer. It's not trivial.

It's not trivial. That's true. In fact, this is a very serious issue that needs to be addressed by the top PR guys. Or at least some official "community manager" or something like that.

In the absence of any official direction, I think the way to go is to simply level with everyone. Tell people what you most seriously believe is what is truly going on and ALL their options. Don't assume people are stupid or they will prove you right.

---

### Post by jerrylamos on 2011-11-04
Unity has been out for two releases now.

Any hint about Unity acceptance?

Only thing I've seen so far is on Planet Ubuntu which was very unfavorable.

Of course, Mark Shuttleworth (who pays the bills) is solidly behind Unity in spite of the continuing theme that Ubuntu should be user configurable (except for Unity).

Me, I test whatever Ubuntu throws over the wall as their main offering.  Exception is I prefer Unity-2D vs. -3D.  Compiz has got to be one of the biggest source of bugs on Launchpad as well as soaking up pc cycles even when I'm running full screen applications and anything Commpiz is doing is worthless.

Jerry

---

### Post by kurt18947 on 2011-11-04
> **grahammechanical said:**
> Hi

I know that I have been eavesdropping on a conversation between the big guys (and girls - before someone says that "guys" was an unfortunate remark) but I have come to the opinion that a user should be forced to pass a knowledge test or better still an IQ test before being allowed to seriously modify their system. And I am only half joking.

It seems that we have reached the point where we need a true alternative install ISO where the user gets to choose the User Interface and takes responsibility for the choices he/she makes.

Download 1 = easy install, not too much input from you. Like what you get or lump it.

Download 2 = More complicated install, more decisions by you. If you don't like what you get. Don't complain . It was your choice.

It was well known that 11.10 would be like 11.04 + Unity only more so. So, why upgrade to it if you did not like 11.04 + Unity? I have also noticed since joining this forum that given enough time clever people will work out ways to do things. So, why not wait and let the clever people work out how to change things to the way you like? Why demand that what you want right now? It is this that I do not like.

Regards.

Well said.  If there is any thought of offering telephone support in the future, there HAS to be a known desktop/package configuration (download 1).  If a user chooses to make it fit his/her desires, that user is on their own if there are conflicts or failures due to untested configurations.

---

### Post by lehjr on 2011-11-04
If you want to figure out how to deal with the Unity hate, you have to realize that much of that hate is a result of a negative user experience. I personally don't like it because it takes more time to find the things and the performance isn't as good as the classic Gnome interface that Ubuntu users generally associate with the "face" of Ubuntu. 

Sure my system may be a bit dated (Asus A8V Deluxe, Athlon 64 4000+, 2GB Dual Channel DDR, Ati Radeon 3400 HD (AGP), 500GB 7200 RPM SATA HDD), but it runs Windows 7 just fine. But with Unity, no, not so much, even with the fglrx drivers. Then you get into the user experience between finding the program you're trying to launch, to switching between running programs and instances of them. Then when I go to do anything on the far left of the screen the Unity pops up. I'm running a desktop PC, not a tablet.

Also consider this, if the ultimate goal is to target portable devices, then don't you think that you're going to have to scale back the requirements a bit? I mean after all, my current phone doesn't even meet the requirements to run Unity, and that's an Atrix 4G. However, the built in webtop interface does run Jaunty, and Motorola now has other devices running Maverick, and apparently they plan to have the webtop in all of their high end phones. I can't say what their view of Unity is, but I imagine they'll never use it given the requirements on top of Android. And yes, I know that webtop implementation isn't quite the implementation in mind, but look the specs for even the most advanced tablet or smart phone available and see if ANY of them can run Unity. 

Anyway, mine is only an example of the negative user experience, but I'm hoping that it at least gives you some insight as to why those that don't like Unity really don't like it, and hopefully you can improve the user experience for those people as well. Maybe Wayland can improve the performance issues, but how do you fix the interface itself?  The only fix I could find for my user experience was to follow those who already switched to Mint.

---

### Post by effenberg0x0 on 2011-11-04
> **lehjr said:**
> If you want to figure out how to deal with the Unity hate, you have to realize that much of that hate is a result of a negative user experience. I personally don't like it because it takes more time to find the things and the performance isn't as good as the classic Gnome interface that Ubuntu users generally associate with the "face" of Ubuntu. 

Define performance. I am running Eclipse CDT, Code Blocks, 4 Gedits, 2 terminals, 2 Firefox Browsers, each with more than 10 opened tabs, Banshee is playing 320Kbps audio, LibreOffice Writter is opened in a document with more than 100 pages of images and text, two putty ssh sessions, VmWare player is running a Windows 7 Enterprise VM with Internet Explorer and proprietary apps running and I have Thunderbird opened, managing 6 e-mail accounts with more than 5.000 messages considering all folders. I have many Compiz plugins activated, including a lot of bling stuff, and I'm using less than 2.5GB of RAM. My CPU cores are in "OnDemand" mode, clocked most of the time at 800MHz and it makes no change in speed if I set them to "performance" governor (3.9GHz). I have 14GB of unused RAM and my swap is turned off. I can't even dream of doing all that in Windows 7 as host/native OS. And I have tried.

> **lehjr said:**
> 
Sure my system may be a bit dated (Asus A8V Deluxe, Athlon 64 4000+, 2GB Dual Channel DDR, Ati Radeon 3400 HD (AGP), 500GB 7200 RPM SATA HDD), but it runs Windows 7 just fine. But with Unity, no, not so much, even with the fglrx drivers.
It's a good enough machine, but ATI is known to need some parameters and customizations to really perform in Linux, Unity or not. You might wanna check it.

> **lehjr said:**
> 
Then you get into the user experience between finding the program you're trying to launch, to switching between running programs and instances of them. Then when I go to do anything on the far left of the screen the Unity pops up. I'm running a desktop PC, not a tablet.
You can disable and adjust this behavior.

> **lehjr said:**
> 
Also consider this, if the ultimate goal is to target portable devices, then don't you think that you're going to have to scale back the requirements a bit? I mean after all, my current phone doesn't even meet the requirements to run Unity, and that's an Atrix 4G. However, the built in webtop interface does run Jaunty, and Motorola now has other devices running Maverick, and apparently they plan to have the webtop in all of their high end phones. I can't say what their view of Unity is, but I imagine they'll never use it given the requirements on top of Android. And yes, I know that webtop implementation isn't quite the implementation in mind, but look the specs for even the most advanced tablet or smart phone available and see if ANY of them can run Unity. 

I'm unaware of any official plans to take Unity as it is to Phones. I have a Galaxy SII with a 1.2GHz dual-core CPU running Android, and I seriously doubt someone that is running Android, an alternate Android ROM (like MIUI, etc) will want to switch to Ubuntu in its current state. There's no alternative to do that yet. It probably wouldn't be done with current code.

> **lehjr said:**
> 
 Anyway, mine is only an example of the negative user experience, but I'm hoping that it at least gives you some insight as to why those that don't like Unity really don't like it, and hopefully you can improve the user experience for those people as well. Maybe Wayland can improve the performance issues, but how do you fix the interface itself?  The only fix I could find for my user experience was to follow those who already switched to Mint.
This should all be taken to the people that make decisions regarding Unity look and feel experience. I doubt any of them reads what is posted here.

> **lehjr said:**
> 
  ...Mint...
Ubuntu is more than Unity. You can disable Unity. Why would someone migrate to another distro when a 5 minute search in this forum would reveal a couple ways to use the latest Ubuntu while not having to use Unity? It makes no sense as an argument.

---

### Post by ventrical on 2011-11-04
> **jerrylamos said:**
> Unity has been out for two releases now.

Any hint about Unity acceptance?

Only thing I've seen so far is on Planet Ubuntu which was very unfavorable.

Of course, Mark Shuttleworth (who pays the bills) is solidly behind Unity in spite of the continuing theme that Ubuntu should be user configurable (except for Unity).

Me, I test whatever Ubuntu throws over the wall as their main offering.  Exception is I prefer Unity-2D vs. -3D.  Compiz has got to be one of the biggest source of bugs on Launchpad as well as soaking up pc cycles even when I'm running full screen applications and anything Commpiz is doing is worthless.

Jerry


  I watched  some video of Mr. Shuttleworth launching Natty Narwhal and discussing the future of Ubuntu. He struck up a lot of cords about his personal passion for Unity. Quite obviously the guy is a genius. He reaches out to end_users of all stripes. He is an open clean slate for feedback and thrives off the fumes of launchpad_bug reports. Yes .. he is a bug_junkie and those are the best  kind of white hatted hackers that the internet buisness structure needs more of.

  His goal is to span out to 200 million users and with a refined legacy GNOME GUI -he will succeed (I would assume) because he  certainly does not to appear unbuisness-savy enough as to let go of his core base which  obviously is GNOME.. But Unity will prevail and successfully so.  I would also assume he is about, lurking , reading , gathering .. :)

---

### Post by gsmanners on 2011-11-04
> **ventrical said:**
> But Unity will prevail and successfully so.  I would also assume he is about, lurking , reading , gathering .. :)

I love all the unjustified optimism. It really warms the heart. Now give me some reasons for it. :D

Is sabdfl lurking moar? That's a comforting thought but I doubt it.

---

### Post by lehjr on 2011-11-04
> **effenberg0x0 said:**
> Define performance. I am running Eclipse CDT, Code Blocks, 4 Gedits, 2 terminals, 2 Firefox Browsers, each with more than 10 opened tabs, Banshee is playing 320Kbps audio, LibreOffice Writter is opened in a document with more than 100 pages of images and text, two putty ssh sessions, VmWare player is running a Windows 7 Enterprise VM with Internet Explorer and proprietary apps running and I have Thunderbird opened, managing 6 e-mail accounts with more than 5.000 messages considering all folders. I have many Compiz plugins activated, including a lot of bling stuff, and I'm using less than 2.5GB of RAM. My CPU cores are in "OnDemand" mode, clocked most of the time at 800MHz and it makes no change in speed if I set them to "performance" governor (3.9GHz). I have 14GB of unused RAM and my swap is turned off. I can't even dream of doing all that in Windows 7 as host/native OS. And I have tried.


It's a good enough machine, but ATI is known to need some parameters and customizations to really perform in Linux, Unity or not. You might wanna check it.


You can disable and adjust this behavior.


I'm unaware of any official plans to take Unity as it is to Phones. I have a Galaxy SII with a 1.2GHz dual-core CPU running Android, and I seriously doubt someone that is running Android, an alternate Android ROM (like MIUI, etc) will want to switch to Ubuntu in its current state. There's no alternative to do that yet. It probably wouldn't be done with current code.


This should all be taken to the people that make decisions regarding Unity look and feel experience. I doubt any of them reads what is posted here.


Ubuntu is more than Unity. You can disable Unity. Why would someone migrate to another distro when a 5 minute search in this forum would reveal a couple ways to use the latest Ubuntu while not having to use Unity? It makes no sense as an argument.

First off, I'd like to point out that my own views may/may not be in line with what other "Unity haters" feel, but everyone that I've encountered so far has had a similar experience with it. Of course you can read comments just as easily as I can, so likely aside from my own detailed personal experience, I'm probably not really helping much. I'm just trying to give you an idea as to what you'll be up against.

Say I'm typing on Facebook. With Unity, with no more than 3 tabs open, there are times where I have to wait several seconds for the words to actually appear in the text entry box. The same happens with Chrome, so it's not really a FF issue. And EVERYTHING is just laggy, which is pretty much the same as every other performance issue reported. But in Mint, I can have 80 tabs open and still be able to type without having the browser or the entire system hang. Unity's 2D interface was met with it's own obstacles, including garbled text and garbled parts of the screen. Maybe the issue is that I still have a single core CPU, I dunno, but I've never had to jump through any hoops beyond installing the fglrx drivers before.

Gnome 3's shell is actually worse ("unholy mess"), and even the classic DE (no effects) runs miserably. I suffered with that for a couple days, but after finding a Fedora specific dependency (FirewallD) for adding a printer through Gnome's control panel, I decided I wasn't going wait to discover even worse unpleasant surprises. 

There's also a sound issue, where the sounds stutters even just logging in. Yes, the sound can be improved with some magical setting to Pluseaudio (AC97 related), but it isn't entirely fixed. 

As for Unity not being Ubuntu, no, it's not the underlying OS, but the method provided for the user to interact with it, for better or worse. For the most part Mint is Ubuntu (unless you're using the LMDE version), with a few tweaks, but these tweaks can make all the difference in the world. 

Searching the forums isn't always as fruitful as you might think, especially when you consider that a user searching the forums for helpful information when the person's system is already running in "limp mode" and he/she doesn't know what exactly to search for. Even then, you'd be amazed at the speed at which information becomes outdated.

As for why I, and many others actually switched, either they simply don't like the interface, or the performance, or both. Furthermore, we don't like the other alternative DE's and for some, some Unity is more than a interface, it represents a sign of change and an intended direction, where once Ubuntu took Debian and made it usable for even the most casual user, it now has taken a page from the Gnome devs and sacrificed that functionality. I understand that Gnome 2 is an unsupported dead end and that change had to happen, but Unity was not the change I needed. But as I said before, maybe Wayland will fix the performance issues. At least that would be a step back in the right direction.

---

### Post by sgage on 2011-11-04
[QUOTE=NTL2009;11412500]Are you saying that such a command exists (please excuse my ignorance)? If so - please tell us!

/QUOTE]

in a terminal:

sudo apt-get install gnome-shell

Works for me! :KS

I also think the term "Unity hater" is not helpful, at least not if one is trying to promote any kind of community. It sounds like you're characterizing people who don't like Unity as somehow irrational and blinded by hatred. Ever since it came out, I have tried and tried to understand the thought process behind Unity, and I don't get it. I dislike (you could say strongly dislike) Unity - it simply does not work for me. I do not use small screen gadgets with my apps maximized all the time. I am beginning to think that I am no longer in the Ubuntu target demographic.

---

### Post by effenberg0x0 on 2011-11-04
> **lehjr said:**
> I doubt that everyone is having such a hard time with Unity. The online forums concentrate the users that are looking for solutions or for a place to vent, so it's a sample that can't possible represent the universe.

> **lehjr said:**
> 
Say I'm typing on Facebook. With Unity, with no more than 3 tabs open, there are times where I have to wait several seconds for the words to actually appear in the text entry box. The same happens with Chrome, so it's not really a FF issue. And EVERYTHING is just laggy, which is pretty much the same as every other performance issue reported. But in Mint, I can have 80 tabs open and still be able to type without having the browser or the entire system hang. Unity's 2D interface was met with it's own obstacles, including garbled text and garbled parts of the screen. Maybe the issue is that I still have a single core CPU, I dunno, but I've never had to jump through any hoops beyond installing the fglrx drivers before.
Go check your GL setup. ATI is known to have some issues and needed switches in order to run OpenGL with a decent performance. You never had such problems because you were not using an accelerated desktop. This is not PP or Unity related.

> **lehjr said:**
> 
Gnome 3's shell is actually worse ("unholy mess"), and even the classic DE (no effects) runs miserably. I suffered with that for a couple days, but after finding a Fedora specific dependency (FirewallD) for adding a printer through Gnome's control panel, I decided I wasn't going wait to discover even worse unpleasant surprises. 
Go check your GL setup. ATI is known to have some issues and needed  switches in order to run OpenGL with a decent performance. You never had  such problems because you were not using an accelerated desktop. This is not PP or Unity related.

> **lehjr said:**
> 
 There's also a sound issue, where the sounds stutters even just logging in. Yes, the sound can be improved with some magical setting to Pluseaudio (AC97 related), but it isn't entirely fixed. 
This is not PP or Unity related.
 
> **lehjr said:**
> 
  As for Unity not being Ubuntu, no, it's not the underlying OS, but the method provided for the user to interact with it, for better or worse. For the most part Mint is Ubuntu (unless you're using the LMDE version), with a few tweaks, but these tweaks can make all the difference in the world. 
 
I wouldn't know, I use Ubuntu.

> **lehjr said:**
> 
   Searching the forums isn't always as fruitful as you might think, especially when you consider that a user searching the forums for helpful information when the person's system is already running in "limp mode" and he/she doesn't know what exactly to search for. Even then, you'd be amazed at the speed at which information becomes outdated.
 
You can easily fiond a solution to improve your video performance by searching for the keywords "ati" "fglrx" "opengl"

> **lehjr said:**
> 
    As for why I, and many others actually switched, either they simply don't like the interface, or the performance, or both. Furthermore, we don't like the other alternative DE's and for some, some Unity is more than a interface, it represents a sign of change and an intended direction, where once Ubuntu took Debian and made it usable for even the most casual user, it now has taken a page from the Gnome devs and sacrificed that functionality. I understand that Gnome 2 is an unsupported dead end and that change had to happen, but Unity was not the change I needed. But as I said before, maybe Wayland will fix the performance issues. At least that would be a step back in the right direction.
It has a good performance right now, which will certainly be improved in upcoming releases and fixes. Check your hw+sw setup. Something's not right there.

> **sgage said:**
> 
[QUOTE=NTL2009;11412500]Are you saying that such a command exists (please excuse my ignorance)? If so - please tell us!


in a terminal:
sudo apt-get install gnome-shell

Works for me! :KS

I also think the term "Unity hater" is not helpful, at least not if one is trying to promote any kind of community. It sounds like you're characterizing people who don't like Unity as somehow irrational and blinded by hatred. Ever since it came out, I have tried and tried to understand the thought process behind Unity, and I don't get it. I dislike (you could say strongly dislike) Unity - it simply does not work for me. I do not use small screen gadgets with my apps maximized all the time. I am beginning to think that I am no longer in the Ubuntu target demographic.[/QUOTE]

You're an exception. People do believe that their slow rendering of OpenGL, network lag, slow disk access, sound and printer issues, etc can somehow relate to Unity - it's insane. 

I use large monitors with non-maximized apps too, therefore I have chosen to deactivate the global panel and now it suits me. You should give it a try, it may become more comfortable for you (it did for me).

---

### Post by ventrical on 2011-11-04
> **effenberg0x0 said:**
> Go check your GL setup. ATI is known to have some issues and needed switches in order to run OpenGL with a decent performance. You never had such problems because you were not using an accelerated desktop. This is not PP or Unity related.

 
Go check your GL setup. ATI is known to have some issues and needed  switches in order to run OpenGL with a decent performance. You never had  such problems because you were not using an accelerated desktop. This is not PP or Unity related.

 
This is not PP or Unity related.
 
 
I wouldn't know, I use Ubuntu.

 
You can easily fiond a solution to improve your video performance by searching for the keywords "ati" "fglrx" "opengl"


It has a good performance right now, which will certainly be improved in upcoming releases and fixes. Check your hw+sw setup. Something's not right there.



You're an exception. People do believe that their slow rendering of OpenGL, network lag, slow disk access, sound and printer issues, etc can somehow relate to Unity - it's insane. 

I use large monitors with non-maximized apps too, therefore I have chosen to deactivate the global panel and now it suits me. You should give it a try, it may become more comfortable for you (it did for me).


 I talked to my brother last night on just this issue ..about ATI ,disabling  antialiasing .. GL  ..etc.. but , however , I have all the Ubuntus working just fine  on my ATi Radeon1250.

---

### Post by effenberg0x0 on 2011-11-04
> **ventrical said:**
> I talked to my brother last night on just this issue ..about ATI ,disabling  antialiasing .. GL  ..etc.. but , however , I have all the Ubuntus working just fine  on my ATi Radeon1250.

It seems to affect some models and not others. I've helped many users on General Help and here in my country who really couldn't use OpenGL at all when CCSM/OpenGL/Sync to VBlank and /or Catalyst "Tear Free" setting were enabled. There seem to be other improvements one can do to make it work faster (they're spread in general help) but I'm not familiar with ATI at all and don't have the hardware to test it. 

However, when a user says he has to wait for the letter he type to show in screen when using Unity, it becomes obvious that there is something wrong in his GL setup.

---

### Post by lehjr on 2011-11-04
> **effenberg0x0 said:**
> Define performance. I am running Eclipse CDT, Code Blocks, 4 Gedits, 2 terminals, 2 Firefox Browsers, each with more than 10 opened tabs, Banshee is playing 320Kbps audio, LibreOffice Writter is opened in a document with more than 100 pages of images and text, two putty ssh sessions, VmWare player is running a Windows 7 Enterprise VM with Internet Explorer and proprietary apps running and I have Thunderbird opened, managing 6 e-mail accounts with more than 5.000 messages considering all folders. I have many Compiz plugins activated, including a lot of bling stuff, and I'm using less than 2.5GB of RAM. My CPU cores are in "OnDemand" mode, clocked most of the time at 800MHz and it makes no change in speed if I set them to "performance" governor (3.9GHz). I have 14GB of unused RAM and my swap is turned off. I can't even dream of doing all that in Windows 7 as host/native OS. And I have tried.


It's a good enough machine, but ATI is known to need some parameters and customizations to really perform in Linux, Unity or not. You might wanna check it.


You can disable and adjust this behavior.


I'm unaware of any official plans to take Unity as it is to Phones. I have a Galaxy SII with a 1.2GHz dual-core CPU running Android, and I seriously doubt someone that is running Android, an alternate Android ROM (like MIUI, etc) will want to switch to Ubuntu in its current state. There's no alternative to do that yet. It probably wouldn't be done with current code.


This should all be taken to the people that make decisions regarding Unity look and feel experience. I doubt any of them reads what is posted here.


Ubuntu is more than Unity. You can disable Unity. Why would someone migrate to another distro when a 5 minute search in this forum would reveal a couple ways to use the latest Ubuntu while not having to use Unity? It makes no sense as an argument.

> **effenberg0x0 said:**
> Go check your GL setup. ATI is known to have some issues and needed switches in order to run OpenGL with a decent performance. You never had such problems because you were not using an accelerated desktop. This is not PP or Unity related.

 
Go check your GL setup. ATI is known to have some issues and needed  switches in order to run OpenGL with a decent performance. You never had  such problems because you were not using an accelerated desktop. This is not PP or Unity related.

 
This is not PP or Unity related.
 
 
I wouldn't know, I use Ubuntu.

 
You can easily fiond a solution to improve your video performance by searching for the keywords "ati" "fglrx" "opengl"


It has a good performance right now, which will certainly be improved in upcoming releases and fixes. Check your hw+sw setup. Something's not right there.



You're an exception. People do believe that their slow rendering of OpenGL, network lag, slow disk access, sound and printer issues, etc can somehow relate to Unity - it's insane. 

I use large monitors with non-maximized apps too, therefore I have chosen to deactivate the global panel and now it suits me. You should give it a try, it may become more comfortable for you (it did for me).

I never had the problem until Unity so I fail to see how it isn't related to Unity. And my poor experience with it was why I switched to Mint. As for my opengl settings:
```
$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 3450 
OpenGL version string: 3.3.10665 Compatibility Profile Context

$ glxgears
12247 frames in 5.0 seconds = 2447.858 FPS

$ fgl_glxgears
Using GLX_SGIX_pbuffer
3218 frames in 5.0 seconds = 643.600 FPS

```
Unity was a problem for me the moment I installed Ubuntu, and that wasn't even an upgrade but a clean install. Unless my hardware configuration is the same as yours, my actual user experience will be different than yours. And I don't mean that I installed it and after 15 minutes I decided I didn't like it. Even during the installation I experienced graphics corruption. I mean how do you even begin to search for help if you can't even get the OS that you're trying to get help with to a usable state where you can actually type into a text control on a web page in a usable fashion without waiting 5 seconds between words or having the browser freeze up halfway through a post?

But even hardware issues aside, there's still the issue of the usability of the interface itself. Sure users can tweak their desktop, but only if they know what they're doing, and some are really just to afraid of breaking things or they don't want to put time into customizations they may lose in the next release or if they have to reinstall. Not everyone wants to install an OS for the sake of spending the time to tweak it to the point of bringing back functionality that was updated out of it.

The bottom line is while you simply can't fix hardware related issues for those having problems, those with usability issues not related to hardware issues you can help, and I can only assume those are the people that this thread was about. However, to say that that I'm the exception to the rule for those having hardware/performance related issues isn't supported by the use of this forum's search feature, nor that of your browser. There just doesn't seem to be an abundance of answers to fix either problem yet.

---

### Post by cariboo on 2011-11-04
@lehjr, do you also have performance issues when running the 2D interface? How about the gnome classic interface?

Keep in mind that this is the Precise testing and discussion sub-forum, so you should be running Precise in order to get help here.

---

### Post by ARooster on 2011-11-04
> **effenberg0x0 said:**
> Define performance. I am running Eclipse CDT, Code Blocks, 4 Gedits, 2 terminals, 2 Firefox Browsers, each with more than 10 opened tabs, Banshee is playing 320Kbps audio, LibreOffice Writter is opened in a document with more than 100 pages of images and text, two putty ssh sessions, VmWare player is running a Windows 7 Enterprise VM with Internet Explorer and proprietary apps running and I have Thunderbird opened, managing 6 e-mail accounts with more than 5.000 messages considering all folders. I have many Compiz plugins activated, including a lot of bling stuff, and I'm using less than 2.5GB of RAM. My CPU cores are in "OnDemand" mode, clocked most of the time at 800MHz and it makes no change in speed if I set them to "performance" governor (3.9GHz). I have 14GB of unused RAM and my swap is turned off. I can't even dream of doing all that in Windows 7 as host/native OS. And I have tried.


Really, it wouldn't run on the same system on Windows? I have to say I really enjoyed Gnome 2 desktop and preferred it over the Windows one, Unity however, as someone who also usually runs 10+ applications as a standard, is simply discouraging me from doing so. I run what I need on Ubuntu now and when I am done I switch back to the more manageable Windows environment. I'm still running Ubuntu with Unity DE, though I remain hopeful that Canonical will stop trying to build an Apple clone with it and add some actual functional way to keep track of open applications without having to move the mouse or even scroll through a smartphone sidebar.

---

### Post by lehjr on 2011-11-04
> **cariboo907 said:**
> @lehjr, do you also have performance issues when running the 2D interface? How about the gnome classic interface?

Keep in mind that this is the Precise testing and discussion sub-forum, so you should be running Precise in order to get help here.

I have graphics corruption issues in 2D, some of the text is garbled, some of the graphics are garbled which was made worse if I moved anything, almost like the screen doesn't refresh at all at times. During installation, there were times I had to restart from the beginning because I couldn't even make out the options in the installation. The classic Gnome interface runs sluggish as well in Oneiric, but in Natty it was great but that's still Gnome 2 vs Gnome 3. As far as fgl_rxgears, and glrxgears frame rates, the numbers for Natty were better than Oneiric, and similar to what I have now on Mint.  

If I had more time I'd try to get the issues worked out on the proper thread, but at this stage I'm not even trying to get help anymore, as I already switched to Mint which currently has Natty (yeah, still Gnome 2 this version) under the hood but runs as fast as Maverick. I'm just trying to give some feedback to let those that thread this thread know that there may be more to fixing the user experience than a couple shell scripts and UI tweaks. Maybe there should be some hardware checks in place. In the near future when my time isn't so limited I'll try and help collect enough useful information to get the issues fixed.

---

### Post by NTL2009 on 2011-11-05
> **effenberg0x0 said:**
> Yes, of course there is. ...

Without putting too much thought in it, but something like this will probably get users to a more familiar desktop?

Or maybe the user wants his gnome-panel back:
```
PLUGINS=$(gconftool-2 --get /apps/compiz-1/general/screen0/options/active_plugins | sed 's/,unityshell//') && sudo apt-get install gnome-panel && gconftool-2 --set --type=string /apps/metacity/general/button_layout "menu:minimize,maximize,close" && gconftool-2 --type=list --list-type=string --set /apps/compiz-1/general/screen0/options/active_plugins $PLUGINS ; gnome-panel &
```Or both, who knows.

Does anyone has a Unity desktop there to test? 

Thanks, Effenberg

Thanks for the code examples. I did a fresh install of 11.10 Ubuntu on an ext USB to test this out. I got results like your screen-shots.  A few things I noticed:

A) No SYSTEM menu alongside the Application, Places menus. 
B) I could not add/delete anything from the panels, or change their size. I could configure the applets that were there OK.


It did kick off a few errors that might be related (Greek to me):

```
(gnome-panel:4581): Gtk-CRITICAL **: gtk_orientable_get_orientation: assertion `GTK_IS_ORIENTABLE (orientable)' failed

(gnome-panel:4581): Gtk-CRITICAL **: gtk_orientable_get_orientation: assertion `GTK_IS_ORIENTABLE (orientable)' failed

(gnome-panel:4581): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.30.0/./gobject/gsignal.c:2295: signal `size_request' is invalid for instance `0x922bce0'
```

What I thought was GREAT - this gave me the CHOICE of Unity (2D/3D) and Classic Gnome (w/wo effects) at login. A quick log out & back in let me try the different configs. I think this is the answer to your earlier concern:

> **effenberg0x0 said:**
>  ... how to help users get the best of Ubuntu without going through not only risky procedures but how does teaching them to avoid Unity would align with supporting Ubuntu strategy, which I respect, understand and don't feel like putting myself against. That's what is on my mind and unfortunately I can't find an answer. It's not trivial.


This way, it isn't a conflict between two ways of working, it is a choice. And if the installer was set up this way, it would not be confusing - just install and then try different ways of working w/o much effort and no install/re-install/delete-this/delete-that.

Two further thoughts - 1) can that code be tweaked (or my errors resolved) so that I can configure the panels and their applets, and get my SYSTEM menu back? and 2) Will these ideas work in the future, or is development for classic Gnome on a dead-end?


> **grahammechanical said:**
>  ...

It was well known that 11.10 would be like 11.04 + Unity only more so. So, why upgrade to it if you did not like 11.04 + Unity?   

Well, if you are new and trying it out, you probably would load the 'latest & greatest' release. So that is all you would know. ANd many will not like it. I almost gave up on Linux as my first real experience was what was shipped on the eeePC901 (Xandros). It had an icon system that I found far too limiting. Fortunately, I worked up the nerve to wipe it and install Ubuntu, and I eventually moved to Ubuntu (10.04/Lucid) for my everyday machine. I'm afraid that w/o readily available options for a DE with menus and panels/applets/widgets, many people will try it and decide it isn't for them and never get to the point of learning about the options. That's unfortunate I think,


-NTL2009

---

### Post by cariboo on 2011-11-05
In gnome classic, use Alt-right-click to modify/add applets to the panel.

Also check this thread for making gnome classic better:

[http://ubuntuforums.org/showthread.php?t=1873765](http://ubuntuforums.org/showthread.php?t=1873765)

---

### Post by NTL2009 on 2011-11-05
> **cariboo907 said:**
> In gnome classic, **use Alt-right-click to modify/add applets to the panel.**

Also check this thread for making gnome classic better:

[http://ubuntuforums.org/showthread.php?t=1873765](http://ubuntuforums.org/showthread.php?t=1873765)

Well, that made a world of difference - THANKS! I now have everything just about the way I like it!

Interesting, I now get a "Gnome" entry at login, that was a dock kind of thing, so I went back to "Gnome Classic". I loaded gnome-tweak-tool, added the MegaGrip theme I had been using (has easier to grab borders, not sure that was fixed along the way, but it drove me nuts).

Should I be concerned about those errors I got earlier? It all seems to work fine with the exception of no SYSTEM menu. Can that be added? I guess I could rebuild those entries in the APPLICATIONS menus.

```
(gnome-panel:4581): Gtk-CRITICAL **: gtk_orientable_get_orientation: assertion `GTK_IS_ORIENTABLE (orientable)' failed

(gnome-panel:4581): Gtk-CRITICAL **: gtk_orientable_get_orientation: assertion `GTK_IS_ORIENTABLE (orientable)' failed

(gnome-panel:4581): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.30.0/./gobject/gsignal.c:2295: signal `size_request' is invalid for instance `0x922bce0'
```

It's looking good, I'm getting very tempted to update my main system. Am a bit concerned about maintaining this though - will things 'break' with other updates?

Thanks so much for this info, this is much better (for me) than trying to make the switch to K/Xubuntu (those are nice, but just more of a change from my current system).

-NTL2009

---

### Post by keithpeter on 2011-11-05
> **NTL2009 said:**
> 
It's looking good, I'm getting very tempted to update my main system. Am a bit concerned about maintaining this though - will things 'break' with other updates?
-NTL2009

Yup, this is the testing phase for Ubuntu 12.04, so there should be plenty of changes and things will break. I use an old netbook for testing, and then I start just before the Alphas come out. I'll have a go with Unity 2D so bug reports are useful.

NOT advised for main system.

---

### Post by NTL2009 on 2011-11-05
> **keithpeter said:**
> Yup, this is the testing phase for Ubuntu 12.04, so there should be plenty of changes and things will break. I use an old netbook for testing, and then I start just before the Alphas come out. I'll have a go with Unity 2D so bug reports are useful.

NOT advised for main system.

I clicked on this thread w/o realizing it was 12.04 specific. I ran that script (from post #20) on a fresh 11.10 install (on an ext drive to experiment with). Should I move future comments over to that "Gnome Classic Mega-thread"? I guess that is what these scripts are setting (edit- whoops, I just noticed that thread is in the 'precise' forum also - is there a better place to post questions on Gnome Classic for 11.10?) 

So what I meant to ask, was would updates to 11.10 be likely to  break what these scripts set up?

-NTL2009

---

### Post by ranch hand on 2011-11-05
Having kind of followed this thread I really wonder what the point of it is.

Ubuntu puts out Gnome, KDE, Xfce and Lxde flavors of its OS.  It is kind of hard to imagine that "handling" Unity "haters" is any harder than suggesting trying one of the other three flavors.

Unless they want to go to Open Box or some other DE their choices are kind of stuck with those in any distro.

I only mention this because, while somewhat interesting, this seems a long thread on such a shallow subject.

---

### Post by gsmanners on 2011-11-05
I think it's the sheer volume of threads. There's been a lot of threads started and continuing about coping with Unity. It's frankly a huge pain, and having a convenient place to point to when the topic of technical solutions come up would be nice.

---

### Post by effenberg0x0 on 2011-11-05
> **ranch hand said:**
> Having kind of followed this thread I really wonder what the point of it is.

Ubuntu puts out Gnome, KDE, Xfce and Lxde flavors of its OS.  It is kind of hard to imagine that "handling" Unity "haters" is any harder than suggesting trying one of the other three flavors.

Unless they want to go to Open Box or some other DE their choices are kind of stuck with those in any distro.

I only mention this because, while somewhat interesting, this seems a long thread on such a shallow subject.

When I created it, I wanted to gather some thoughts of experienced users / helpers on how to deal with them in terms of advise in the safest possible way, as in trying to avoid them from ending up with a broken setup. If we were gonna end up creating and providing a unified set of instructions / guide to using some other DE, and if it was OK to do that, and with which DE. Some people were (and some still are) removing important things from their systems, driven by the simple desire to not use Unity. In my limited experience, I have learned that a large portion of users can't install and setup a lighter DE on their own. This are the factors that drove me to creating this thread back then.

But, since then, other threads and guides (some 100% correct, some partially correct, etc) on how to use lighter DEs have been made, and they deal with these situations in most cases. 

It has became useless and, at most, only a place for some people to eventually vent their frustrations regarding current Ubuntu strategy.  Arguments are poor and discussions lead to nowhere. 

I have come to the conclusion that the only way to properly handle newbies and alike is to have more complete and refined interfaces embedded in the OS, which presents the users with better information and allow for educated choices. This is what I am pursuing.

So I have no restriction whatsoever for locking this thread now. Nothing will come out of it.

---

### Post by lesterness on 2011-11-05
> **effenberg0x0 said:**
> That would be great. I do believe (strongly) that people will feel the need to revert to Unity, as they see other people happily using it. A simple checkbox to enable/disable would be the way to go. It will definitely help avoid users from doing crazy things. I've been seeing people removing Ubuntu critical packages and ending up with non functional PCs.

Thanks,
Effenberg

Two ways to deal with us Unity haters: 1) avoid a patronizing tone ("You'll love brussels sprouts boiled in dog urine if you only give it a chance!!"); 2) avoid an authoritarian tone ("Ubuntu has decreed Unity! Tremble and obey!")

I'm not a computer professional but an historian and archaeologist. I use Ubuntu to write on those subjects. I don't want to fuss with irrelevant technical details anymore than you want to fuss with the Early Bronze Age/Middle Bronze Age interface, or the details of potsherds. So far, Ubuntu has been an improvement on Windows. If it stops being better, why should I get used to worse?

---

### Post by effenberg0x0 on 2011-11-06
> **lesterness said:**
> Two ways to deal with us Unity haters: 1) avoid a patronizing tone ("You'll love brussels sprouts boiled in dog urine if you only give it a chance!!"); 2) avoid an authoritarian tone ("Ubuntu has decreed Unity! Tremble and obey!")

I'm not a computer professional but an historian and archaeologist. I use Ubuntu to write on those subjects. I don't want to fuss with irrelevant technical details anymore than you want to fuss with the Early Bronze Age/Middle Bronze Age interface, or the details of potsherds. So far, Ubuntu has been an improvement on Windows. If it stops being better, why should I get used to worse?

You're probably right but I don't care anymore. I gave up understanding. For me it's like a car. Toyota or Honda or whatever brand releases a new model that has a different interior design for the panel. Either you buy it and use it or you don't. If you really like the car, but just hates the panel, there are methods for getting your panel replaced. If you know what you're doing (which most people don't), you can safely buy a new panel and replace it yourself. If you don't, you should look for guidance of specialists on how to replace the panel. And if it all seems too complicated, you can use another car brand/model. 

I can't get all these emotional aspects of "Ubuntu is forcing us to use Unity", "we've been betrayed", etc because it just shows how technically ignorant users are, how unskilled they are to not event try to perform simple Google search and copy/paste procedures. I find it silly. People are lazy and it makes me sick. How hard is it to Google for something like "disable Unit", read something, copy/paste the steps, done. Google + 5 minutes is all it takes to have a desktop customized. And it's not necessary to even understand what an operating system is.

Now, I do believe the currently existing and safe options to disable the Unity plugin should be built into the OS in a wizard-like interface. And that central-help places like this one should organize to provide unified instructions on how to do those things. But I gave up on #2 and decided I waste my time better working on #1.

---

### Post by cariboo on 2011-11-06
Moved an off topic post to the jail.

---

### Post by PRC09 on 2011-11-06
> I can't get all these emotional aspects of "Ubuntu is forcing us to use Unity", "we've been betrayed", etc because it just shows how technically ignorant users are, how unskilled they are to not event try to perform simple Google search and copy/paste procedures. I find it silly. People are lazy and it makes me sick. How hard is it to Google for something like "disable Unit", read something, copy/paste the steps, done. Google + 5 minutes is all it takes to have a desktop customized. And it's not necessary to even understand what an operating system is.

I am afraid you might as well get used to this level of user.This is exactly the type of user that Ubuntu wants as its user base not the hobbyist that can tinker and put up with things not quite right.It is trying to target the Average user and this is the result.Most average users are lucky to be able to tell you the brand name of whatever they are using let alone configure an interface to run on it.....

---

### Post by ventrical on 2011-11-06
> **effenberg0x0 said:**
> You're probably right but I don't care anymore. I gave up understanding. For me it's like a car. Toyota or Honda or whatever brand releases a new model that has a different interior design for the panel. Either you buy it and use it or you don't. If you really like the car, but just hates the panel, there are methods for getting your panel replaced. If you know what you're doing (which most people don't), you can safely buy a new panel and replace it yourself. If you don't, you should look for guidance of specialists on how to replace the panel. And if it all seems too complicated, you can use another car brand/model. 

I can't get all these emotional aspects of "Ubuntu is forcing us to use Unity", "we've been betrayed", etc because it just shows how technically ignorant users are, how unskilled they are to not event try to perform simple Google search and copy/paste procedures. I find it silly. People are lazy and it makes me sick. How hard is it to Google for something like "disable Unit", read something, copy/paste the steps, done. Google + 5 minutes is all it takes to have a desktop customized. And it's not necessary to even understand what an operating system is.

Now, I do believe the currently existing and safe options to disable the Unity plugin should be built into the OS in a wizard-like interface. And that central-help places like this one should organize to provide unified instructions on how to do those things. But I gave up on #2 and decided I waste my time better working on #1.


But Toyotas and Hondas have  computers also  that are pre-set and cannot be adjusted while travelling down the hi-way. They are expected to 'just work'. Also , I think 'lazy' is a rather strong term.

  I don't think  newer end_users 'hate' Unity, I think they are just frustrated and perplexed at how the first run can be so dysfunctional. This is not an end_user problem, it's a program presentation problem. 

 I remember back in 1986 while working with a Packard Bell PC Reflex Database. I was performing a proceedure called a 'partial retrieve'.  The database crashed and my boss started yelling at  me and cursing .. etc. He finally called  the techshop where he bought the PC. Luckily for me the proprietor admitted that it was some obscure buffer setting in a batch file that was the culprit. We fixed the problem.

  Getting mad at my boss or Reflex DB would have done me no good. But I was frustrated because I worked so  long & hard on the database. Even for advanced user , it is sometimes a little tiresome to download .iso files. Some people are on 'usage' plans from their IPs and may have slower connections.  so they spend some personal time, burn their CD expecting  to see the bewonderment of Unity in action and all they get are headaches.? Hatred ? no. Honest frustration? Yes.

  One good thing .. I would  think that the Ubiquity installer and Unity/Compiz will have it's act together by 12.04.

  I think this is why we are here in the forums :)

thanks effenberg.

---

### Post by ventrical on 2011-11-06
> **lesterness said:**
> Two ways to deal with us Unity haters: 1) avoid a patronizing tone ("You'll love brussels sprouts boiled in dog urine if you only give it a chance!!"); 2) 


:)  That one stuck right to the ceiling. :)

---

### Post by wgarcia on 2011-11-06
How can't you get a patronizing tone when again and again the same unfounded criticisms pop up, such as Why does Ubuntu not support non-accelerating graphic cards any more? or Why has Ubuntu abandoned Gnome?

No matter how polite you try to be, at some point it gets to you.

---

### Post by kurt18947 on 2011-11-06
> **ARooster said:**
> Really, it wouldn't run on the same system on Windows? I have to say I really enjoyed Gnome 2 desktop and preferred it over the Windows one, Unity however, as someone who also usually runs 10+ applications as a standard, is simply discouraging me from doing so. I run what I need on Ubuntu now and when I am done I switch back to the more manageable Windows environment. I'm still running Ubuntu with Unity DE, though I remain hopeful that Canonical will stop trying to build an Apple clone with it and add some actual functional **way to keep track of open applications without having to move the mouse or even scroll through a smartphone sidebar.**

Do you know about tint2? It's in the repos and may help with switching between windows.  It adds a bar to the bottom of the screen and each app/window has its own icon. A google search will bring info about how to edit the config file.   I don't know if that will help or not but might be worth a look. Simple to install & uninstall.  I much prefer Gnome 3 shell to Unity for switching between windows & apps, find myself poking the super/windows key in Xfce :).

---

### Post by ErkDemon on 2011-11-06
> **wgarcia said:**
> How can't you get a patronizing tone when again  and again the same unfounded criticisms pop up, such as Why does Ubuntu  not support non-accelerating graphic cards any more? or Why has Ubuntu  abandoned Gnome?

Well, the complication with the crossroads that Ubuntu finds itself  at, is that it now has two classes of incoming criticisms to deal with,  one class comes from the diehard Linux community, and the other comes  from the newbie users (or potential users).

The first group will  bitch about graphics cards and architectural legacy issues and toolsets, and  Shuttleworth's approach to dealing with them is to ignore them. His  point is that Ubuntu has to reach out to the wider population if its  going to reach its full potential, and that setting aside the wants of  this group in the past has gotten Ubuntu to a very, very successful  place in v10.xx. Ubuntu can't be designed for Linux geeks, or its only  audience will be Linux geeks. They "don't get it".

The second  group are the newbies coming from the Windows environment. They're the  target audience, the 90%. Those people have different complaints, like,  how do I move the launcher bar, how do I get back the menu behaviour  that I'm used to, why do these icons look horrible, and how do I change  them, and why does this list of things not seem to work properly. These  are reasonable questions, but unfortunately, those users get given the  same reply that Canonical have for the Linx geeks -- suck it up, you  don't "get it", the system we're implementing is the best possible  system even if you don't understand it, trust us, we know what we're  doing, we know that the current system is great because it's built from  pieces that we took from Win7 and OSX, and those companies employ  professional designers. If you don't like it, you can always use a  different linux distro.

Now, the snag is, for the target  audience, most of these responses aren't approriate. Tell the average  end-user that they're too lazy to look up the information on google and  find it on a third-party tech forum, and they're liable to think, no,  YOU'RE too lazy to put the information where it ought to be, in the OS  itself. Tell them that they need to experiment with other linux distros,  and they'll think, to hell with this, the reason I decided to try  Ubuntu was because people told me that this was the verison of Linux  that actually worked and was user-friendly, and I'm not about to spend  my precious evenings and weekends downloading and installing six  different linux versions just to find something that might be adequate,  when I'm not a computer hobbyist and don't actually give a damn about  the operating system, I just want something that works and lets me find  stuff without constantly tripping me up. 

Most human beings  aren't IT professionals, and while forum regulars might find it  frustrating that these people are too "stupid" to dig a set of  configuration info out of a tech site and use it to solve their problem,  you have to remember that the same goes for every other consumer  product. You might as well complain that car buyers are too lazy and too  stupid to learn metallurgy and hydrocarbon chemistry in order to  understand the best way to treat their engines, or that nobody should be  allowed to buy a house without first passing exams in carpentry,  plumbing bricklaying and electrics. 

The attitude that people  have to mass-market software is that if something doesn't work properly,  it should have been fixed at source. In the age of mass production,  it's more efficient for one person to fix the problem at its source,  than to expect 300,000 end-users to each look up their problem on Google  and apply the workaround themselves. Each of those users will get peed  off, not just because of the time //they// just wasted, but because they  know that that that unnecessary waste is being replicated across the  user-base, and that it's all because someone, somewhere didn't do their  job properly. It's a waste of society's resources.

So,  Shuttleworth's basically in a similar position to where Tony Blair was  towards the end of his Premiership. Blair had the same issue, he had a  dedicated user-base (the Labour Party) who didn't understand that policy  had to be designed to appeal to a wider user-base if it was going to be  successful. So he ignored their complaints and pressed ahead based on  personal conviction, and it was a very sucessful strategy.
The  problem that Blair then hit was that when he started making genuinely  bad decisions, he had no internal compass to tell him that he was going  off the rails, and when everyone was telling him that he was being  stupid, well, he knew that you always get doubters and critics and the  thing to do was not to listen to them. So Blair ended up making stupid  mistakes, that almost everyone on the country apart from him and his  immediate clique knew were //obviously// stupid mistakes (like not  taking the opportinity to excercise the imigration-limiting option that  Britain was offered when the Eastern European countries joined the EU). 

Blair  didn't have enough experience of personal failure to be able to tell  when he was in the middle of a disaster, even when it was painfully  obvious to almost everybody else, and since he'd learnt to ignore  criticism, he had no way of telling when he'd gone disastrously  off-track. He turned from being a popular leader that people pinned  their hopes on as someone who stuck up for the needs of the general  population, to someone that the electorate loathed for not listening to  them. Blair spent a lot of time in his last months complaining that commentators and voters and journalists just "didn't get it", whereas in fact, the one person who didn't "get it" was him.

I think Canonical may be sufferring from Tony Blair  syndrome, they had such a brilliant run of successes up to 10.xx that it  seemed that they could do nothing wrong, and they didn't really  understand what project failure felt like. Since their success was  partly based on ignoring the protests of their core community and  trusting their own convictions, they've they've grown a habit of  thinking that user-protests are just ignorant noise, and that they  automatically know better than the users when the users complain.

But,  like Blair, they're not making a sufficient distinction between the  protests of the "old users" whose views represent a narrow and  unrepresentative interest group that can be set aside, and those of the broader electorate, whose needs it is that the project is supposed to be looking after. 

The user is not always wrong. Often, yes. But not always.

---

### Post by cariboo on 2011-11-06
Actually it isn't the new users that are complaining, the majority of new users have said they like Unity, it is the older users that have been living under a rock for the last year, that are doing most of the complaining. Not old as in age :), but people that have been using Ubuntu for 6 months to 7 years.

The reason I say they've been living under a rock, is that quite a few of them, don't know that Unity is the default desktop, even though it's been well publicized since the release of natty, and the demise of Gnome 2, even though that's been coming for over 3 years and has also been well publicized.

The big problem is that they are uninformed, more than anything else, and many of them aren't willing to look for solutions, so instead they come to the forum, hoping that Canonical will hear their complaints, and we all know how well that works. I give things another couple of weeks and the complaints we get will be less and less, until the next release in April, and then it will start all over again.

---

### Post by lucazade on 2011-11-06
The sad thing is that people that don't like something, say unity in this case, believe they can influence the course of the things by spreading fud and 'hate'.

Never seen these persons providing any viable alternatives or help for the others. They are just caring for their own interests.

---

### Post by mc4man on 2011-11-06
> **kurt18947 said:**
> Do you know about tint2? .
A fairly interesting little app, works pretty good  & seems quite configurable (haven't done more than glance thru the page

If ubuntu was to provide something similar that would be better (maybe with the same hide options as the launcher, option for current or all ws's), in any event does provide window list support, at least to some degree, trying it out now using auto-hide.

page with config options
[http://code.google.com/p/tint2/wiki/Configure](http://code.google.com/p/tint2/wiki/Configure)

---

### Post by NTL2009 on 2011-11-06
First off, I'd like to thank effenberg0x0 for the help he has provided in this and other threads. Now, to answer this post:

> **effenberg0x0 said:**
> You're probably right but I don't care anymore. I gave up understanding. For me it's like a car. Toyota or Honda or whatever brand releases a new model that has a different interior design for the panel. Either you buy it and use it or you don't. ....

Except, the 2011 Honda CRV hasn't replaced the steering wheel with a joy-stick, or moved the brake pedal to a push-button on the dashboard, or told me I don't need a speedometer anymore. The Unity interface is very, very different from my Lucid install, where some pretty simple point-click configurations gave me the panels and settings that make me comfortable (like adjusting the seat and mirrors on a car).


> I can't get all these emotional aspects of "Ubuntu is forcing us to use Unity", "we've been betrayed", etc because it just shows how technically ignorant users are, how unskilled they are to not event try to perform simple Google search and copy/paste procedures. I find it silly. People are lazy and it makes me sick. 

Well, if Linux is going to have a large user base (which I think we need to get the 'critical mass' to get the application/supports we want), if I'm going to recc it to friends, then it needs to address a user-base which is a bit less technically proficient. 

I was "un-lazy" enough to try out Linux (on an eeePC901) in the first place. I was "un-lazy" enough to dump the originally pre-installed Xandros and try Ubuntu (and it sure took me more that 5 minutes of googling to figure _that_ out - which distro? what's all this about partitions, swap space, installing root and home on the separate SSD 4G/16G drives, etc, etc, etc). I was "un-lazy" enough to figure out how to configure it the way that works for me. Now, when I'm looking to upgrade to get a current system, I'm faced with having to try to learn a very different interface, trying to learn if some simple configuration will make it usable for me (I didn't just want to give up on it w/o a fair trial), and trying to figure out if moving to Kubuntu, Xubuntu, XFCE, Lubuntu is a better option for me than trying some of these instructions for replacing Unity in Ubuntu.

Maybe it's 5 minutes for someone like you who already grasps all this stuff. That is not the case for many. many of us. We use Ubuntu, we know a bit about the 'under the hood' stuff, but we don't have a deep understanding. And if we used Ubuntu and liked it (as I did going back to 9.04), we probably know very little about these other distros. We just went on with the business of using our Ubuntu every day.

Even at that, it takes a fair amount of effort to switch from Mac OS (as I did). Learning backup systems, getting my mail and photos ported over from one system to the other was not just 5 minutes of googling. It's far more work than most users want to go through. Don't take away familiar desktops from them on top of everything else.  


> Now, I do believe the currently existing and safe options to disable the Unity plugin should be built into the OS in a wizard-like interface.

Totally agree. It can be a log-in option, as it is for me now after I ran your script(on my experimental install).

How can this approach be supported and pushed? Can I help? What is the constructive way to get our voices heard?


> **wgarcia said:**
> How can't you get a patronizing tone when again and again the same unfounded criticisms pop up, such as Why does Ubuntu not support non-accelerating graphic cards any more? or Why has Ubuntu abandoned Gnome?

No matter how polite you try to be, at some point it gets to you.

Why not simply point to a wiki or other reference? If these questions are coming up so much, maybe that is an indication that things are not being communicated well (by Canonical or the Linux community in general)? I would say, don't let it get to you, just point them to the answers. And I can tell you, I'm confused by the whole Gnome thing. I'm a user, I don't spend much effort tracking road-maps of the components that make up Ubuntu. Gnome 2.x, 3.x, etc - why should I have to know any of this? I just want to install 11.10 and get a system working much like my 10.04. I doubt that I'm alone.

-NTL2009

---

### Post by sgage on 2011-11-06
> **lucazade said:**
> The sad thing is that people that don't like something, say unity in this case, believe they can influence the course of the things by spreading fud and 'hate'.

Never seen these persons providing any viable alternatives or help for the others. They are just caring for their own interests.

That's rather offensive, lucazade, and reinforces the impression of arrogance that has been perceived by many. Some of the biggest Unity "haters" here are long time active members on the forums, and have given countless hours of their time and their expertise to helping others.

Your remark was out of line.

---

### Post by NTL2009 on 2011-11-06
> **cariboo907 said:**
> Actually it isn't the new users that are complaining, the majority of new users have said they like Unity, it is the older users that have been living under a rock for the last year, that are doing most of the complaining. ...

The reason I say they've been living under a rock, is that quite a few of them, don't know that Unity is the default desktop, even though it's been well publicized ...

The big problem is that they are uninformed, more than anything else, and many of them aren't willing to look for solutions, ... 

Well, I can only speak for myself, but maybe this will provide some perspective. I am a fairly 'old user' ( ~ 2.5 years, ~ 18 months as my main system). I was not 'living under a rock' when it came to Unity. I have seen the reports on the web, and had a fair idea what it was about. However, I'm pretty happy with my 10.04 Lucid install. I didn't see any big reason to go thru an upgrade to 10.10, or 11.04 (after all, I'm on an LTS, and it's working for me). But now, we are closer to the next LTS and I'm getting more interested in checking things out in more detail.

I think it is unfortunate that I even need be 'looking for solutions'. I would hope that 12.04 would _be the solution_. But if it doesn't have built in options for drop down menus and panels that I can configure, and I have to go 'looking for solutions', I have to wonder if it is all worth it. As a 'user' more than an 'under the hood' guy, I worry that the more I drift from the out-of-the-box set up (other than simple, supported configuration changes), the more likely I am to have things 'break' or the more futzing I'm going to have to do to keep things working.

I'll offer a 'solution': If Canonical feels that Unity is 'the way' for new users, fine. But they should put right on the download/installation page some info, something like - *'if you prefer a drop-down app menu and panels and applets as in our previous LTS, just DL this install, or go here (link) for a supported set of changes to get that configuration back.'* And having the option available at log-in would be a plus. If Unity is so good, maybe more old users would migrate to it if they could try it once in a while, rather than wipe it from their system.

Is this not do-able? I think it is needed for the 'health and well being' of Ubuntu going forward. I'm not bashing Unity, I just prefer my current set-up, and I want that option in the new LTS w/o having to figure out how/what and will I break stuff doing it. While effenberg0x0 provided the script to do this, I'm clueless as to how this affects my system overall. And theoretically,  a user like me shouldn't even run a script like that unless I actually know what it is doing, or unless it comes from an 'official' trusted source.

I suspect the majority of Ubuntu users are somewhere between 'uninformed' and knowledgeable 'under the hood' types. And that Ubuntu can't be successful w/o those people. They are the ones who will 'sell' their less technical friends on it.

-NTL2009

---

### Post by lucazade on 2011-11-06
> **sgage said:**
> That's rather offensive, lucazade, and reinforces the impression of arrogance that has been perceived by many. Some of the biggest Unity "haters" here are long time active members on the forums, and have given countless hours of their time and their expertise to helping others.

Your remark was out of line.

I'm speaking aboout childish hate, not about critics. Costructive critics.

---

### Post by cariboo on 2011-11-06
@NTL2009, If you plan on upgrading to 12.04 directly, you should be able to install gnome-session-fallback, and have your old interface back. That way you can actually have 3 different desktop environments. Gnome classic, Unity and Gnome-shell. The next LTS version will be supported for 5 years, so that should give you enough time to get used to a different desktop interface. 

The only real problem I can see with sticking with the older interface, is that if you have to change to another distribution for whatever reason, the old 2 panel interface may no longer be available.

---

### Post by effenberg0x0 on 2011-11-06
I think I can't understand what's wrong with Unity because I can't understand how some people use their PC? In my daily use (see below) Unity is far from being so relevant.

Me: As I turn on the PC, I open a couple basic everyday apps (say Firefox, Thunderbird, Banshee) that will be opened all day, like 16 hours straight. I'll probably work with an IDE and a Terminal, so I open Anjuta IDE and a Terminal, that will also be there all day. I'll probably need something to be tested on Windows, so I start a VM.

Then I usually have to work on something like a presentation, a spreadsheet, a text-document: I'll probably open these apps, work on them for 3 or 4 hours straight, close them.

Then I might need to work on some graphics for my files and I might need to use Gimp and Inkscape. More 2 or 3 hours of work. Close graphic apps.

And I'll go back to IDE/Console and code, test, code, test, code, test, etc for a long while. E-mails will be popping in non-stop and I'll answer 50 of them during the day.

That's it, the day is over. You see, I clicked on Unity a couple times, used a couple apps (in this example 11 times). All these apps are in my Launcher shortcuts, because I use them everyday. But that's it. My Interaction with Unity was of less than 15 clicks on it in a day.

Do other people need to open/close/reopen/close/open/reopen/close apps non-stop all day? Do they use hundreds or thousand of applications everyday, every hour? Do they regularly use more apps than fit the launcher space? If so, do typing the first letters of the app name in the search box to find them creates such a distress? 

What are they doing in their PCs? I don't even see Unity more than 15 times a day. Unity is irrelevant. It could be curled into a spiral, with unbearable stroboscopic pink blinking background effects on hover, cause seizures, it could make an elephant sound everytime I click it, etc and still I can't really care about it. It's just an application launcher. I'll use it 15 times a day, to launch 15 apps, and the rest of the time I don't see it.

---

### Post by PaulW2U on 2011-11-06
Mmm, I'd never really thought about all of that before. No matter which variant of 'buntu I'm using, I now have all four installed, I actually use my PC pretty much the same way, open all the applications I know I will need, move them to the required workspace and then get on with it. :)

---

### Post by BillyBoa on 2011-11-06
How is called the person who feels Unity is awkward? I'm one of them. I use it more than 6 months now, but when sometimes I have to switch to the Windows part of my computer,  I have the feeling that Win7 is more ergonomic.

---

### Post by effenberg0x0 on 2011-11-06
> **BillyBoa said:**
> How is called the person who feels Unity is awkward? I'm one of them. I use it more than 6 months now, but when sometimes I have to switch to the Windows part of my computer,  I have the feeling that Win7 is more ergonomic.


Being totally honest with you, I find myself moving the mouse left in windows and expecting the bar to show lately.
 
I think the only serious discussion I have seen so far regards ergonomic aspects, but specifically when using large monitors (apps probably won't be maximized) with the Global Panel on the top. If you search launchpad you'll find a large thread unified with this discussion. I agree that, in this specific situation, having the applications menu back to the applications windows would avoid excessive movement of the mouse to the top/left area. 

But that is never brought up on Unity discussions, seems to not be a bad problem for people that hate Unity. The dash/launcher structure is always the pointed issues.

I have made a mod to allow the dash home shortcuts area to have 15 customized icons. There's a screenshot in this forum section a couple threads below. When I get time to finish the code, I don't think it will be accepted for merge for PP as it is really disconnected from what the people from user interface/experience seem to be trying to achieve, so I'll publish it as a mod deb in my ppa. 

Having 15 easily accessible shortcuts plus the ones in my launcher is really overkill shortcut-wise considering my current use of the PC (see above), but maybe some people do feel the need to alternate between 30 or more apps in a 24 hour period, a day of work, etc? I really can't say, but I'm beginning to wonder if this is the main issue behind all this.

The way I see it, users seem to be OK with Compiz. Some were using Compiz over the previous 2-panel interface. When people talk about Unity problems they seem to be referring to:

**1.The Launcher:** They are facing some kind of issue when finding / launching apps.
**2.Dash:** Seems to me users can be a little lost when finding their apps. No one needs to constantly search / find daily use stuff if they are probably already listed there in "Most Used" apps or had their shortcuts in the launcher. Average users don't use settings apps, so it can only refer to normal use applications finding / launching.
[B]
3.Panel (rarely mentioned):[/B] Seem to only affect people with large monitors, which are a minority. And is not commonly perceived as part of Unity by complainers.

The problem seems to be limited to #1 and #2. Maybe people don't have shortcuts in the launcher or haven't found yet that the launcher shortcuts are fully customizable? Maybe they don't have the application lens installed?

---

### Post by sgage on 2011-11-06
> What are they doing in their PCs? I don't even see Unity more than 15 times a day. Unity is irrelevant. It could be curled into a spiral, with unbearable stroboscopic pink blinking background effects on hover, cause seizures, it could make an elephant sound everytime I click it, etc and still I can't really care about it. It's just an application launcher. I'll use it 15 times a day, to launch 15 apps, and the rest of the time I don't see it.

Wait! You mean you can ***turn off*** that elephant sound? This changes everything!

:KS

---

### Post by NTL2009 on 2011-11-06
> **effenberg0x0 said:**
> I think I can't understand what's wrong with Unity because I can't understand how some people use their PC? In my daily use (see below) Unity is far from being so relevant.

Me: As I turn on the PC, I open a couple basic everyday apps (say Firefox, Thunderbird, Banshee) that will be opened all day, ... It's just an application launcher. I'll use it 15 times a day, to launch 15 apps, and the rest of the time I don't see it.

OK, makes some sense. But I still find it 'much less good' compared to what I have now. Here's what I miss:

I work somewhat like you, open a basic set of apps and I'm good for a long while. But I switch between them _a lot_(every few minutes, typically). To keep my different activities straight, I'll put a subset of windows in their own desktop. So I might have  a few Chromium Browser windows open for one activity (on its own desktop) , along with  related LibreOffice Write & Calc windows, and maybe a File Browser window or two. I keep Mail (T-Bird) in its own desktop.

So the first thing I heavily depend on is the WORKSPACE SWITCHER, which I keep on the lower panel with 8 or so desktops - and I change the number routinely with just a right-click for different ways I work). So right now, 1 for mail, one with a blank desktop, one with system monitor, one with these UBUNTU browser windows and a gedit for notes, another with browser windows and notes on my other installs I'm playing with, one with financial data, one with some file browsers open for another task. I have just a laptop 15" screen, so it helps to keep the display less cluttered, and it help me to organize related tasks together. I have this set so that I can switch with CNTRL-Right/Left, and I can drag any app window from one desktop to another - and I can also access all of this with the mouse, so I'm not moving back/forth from mouse to keyboard, I use whichever I'm on. It's very 'natural' to me. WINDOW LIST lets me easily see and select between the open windows on that desktop, and WINDOW SELECTOR lets me quickly see and select between the open windows on other desktops.

I don't see any way in UNITY to keep a visible list of the windows in a current work-space (w/o hitting alt-tab, which also switches to the next window), or a list of all the windows in all workspaces.In UNITY, if I want to see the workspaces and move windows between them, I have to find it in the sidebar and click it, and it moves around depending on what else is active.

In Lucid, with my panels, these things are all visible, no hunting to click them, and most have key equivalents. This is a big deal for me - I use these features a hundreds of times in the course of a day.

Now, for application launching - sure, I don't do that so often. But for one example, I have several different photo and graphic editors. I don't use them all that often, so it's tough for me to even remember the names of which I use for what. But I have them organized and grouped in my Applications/Graphics menu. This gives me a very visual reminder when I see the list - ' Oh, yeah GIMP is for real detailed editing, digiKam is my photo organizer, showFoto for photo-edits, etc. In a second, I recognize which I want and select it. And if my preferences change, I can re-order or re-group these to my liking.

How many clicks and missed steps would that take me with Unity? Click the Dash, click a subset group (Media?), find/select a 'filter' (Graphics?), find/select the "show more results" text, then have them presented in alphabetical order instead of something that I set up that means something to me.

Sure, that is not the end of the world, but if we are supposed to be making advances in computing, then why does this seem so backward to what I have now? Why would I want to change to this?

That's not meant to bash Unity - it's probably fine for how some work. But it just does not cut it for me and the way I work. I really need these panels with visibility into all my work-spaces, and lists of apps organized in a way that has meaning to _me_.

-NTL2009

---

### Post by PaulInBHC on 2011-11-06
I think MS had it right with Home and Professional versions of Windows.

---

### Post by effenberg0x0 on 2011-11-06
> **NTL2009 said:**
> OK, makes some sense. But I still find it 'much less good' compared to what I have now. Here's what I miss:

I work somewhat like you, open a basic set of apps and I'm good for a long while. But I switch between them _a lot_(every few minutes, typically). To keep my different activities straight, I'll put a subset of windows in their own desktop. So I might have  a few Chromium Browser windows open for one activity (on its own desktop) , along with  related LibreOffice Write & Calc windows, and maybe a File Browser window or two. I keep Mail (T-Bird) in its own desktop.

So the first thing I heavily depend on is the WORKSPACE SWITCHER, which I keep on the lower panel with 8 or so desktops - and I change the number routinely with just a right-click for different ways I work). So right now, 1 for mail, one with a blank desktop, one with system monitor, one with these UBUNTU browser windows and a gedit for notes, another with browser windows and notes on my other installs I'm playing with, one with financial data, one with some file browsers open for another task. I have just a laptop 15" screen, so it helps to keep the display less cluttered, and it help me to organize related tasks together. I have this set so that I can switch with CNTRL-Right/Left, and I can drag any app window from one desktop to another - and I can also access all of this with the mouse, so I'm not moving back/forth from mouse to keyboard, I use whichever I'm on. It's very 'natural' to me. WINDOW LIST lets me easily see and select between the open windows on that desktop, and WINDOW SELECTOR lets me quickly see and select between the open windows on other desktops.

I don't see any way in UNITY to keep a visible list of the windows in a current work-space (w/o hitting alt-tab, which also switches to the next window), or a list of all the windows in all workspaces.In UNITY, if I want to see the workspaces and move windows between them, I have to find it in the sidebar and click it, and it moves around depending on what else is active.

In Lucid, with my panels, these things are all visible, no hunting to click them, and most have key equivalents. This is a big deal for me - I use these features a hundreds of times in the course of a day.

Now, for application launching - sure, I don't do that so often. But for one example, I have several different photo and graphic editors. I don't use them all that often, so it's tough for me to even remember the names of which I use for what. But I have them organized and grouped in my Applications/Graphics menu. This gives me a very visual reminder when I see the list - ' Oh, yeah GIMP is for real detailed editing, digiKam is my photo organizer, showFoto for photo-edits, etc. In a second, I recognize which I want and select it. And if my preferences change, I can re-order or re-group these to my liking.

How many clicks and missed steps would that take me with Unity? Click the Dash, click a subset group (Media?), find/select a 'filter' (Graphics?), find/select the "show more results" text, then have them presented in alphabetical order instead of something that I set up that means something to me.

Sure, that is not the end of the world, but if we are supposed to be making advances in computing, then why does this seem so backward to what I have now? Why would I want to change to this?

That's not meant to bash Unity - it's probably fine for how some work. But it just does not cut it for me and the way I work. I really need these panels with visibility into all my work-spaces, and lists of apps organized in a way that has meaning to _me_.

-NTL2009

I use 8 "desktops" (see screenshot #1). Some of my applications are locked to these desktops automatically using the "Place Windows" plugin (see screenshot #2). 
[ATTACH]206534[/ATTACH]
[ATTACH]206535[/ATTACH]
The launcher puts an arrow on the side of the open apps an highlights all my open apps, at all desktops, all the time (See screenshot #3). See how Nautilus, terminal, gedit, calculator, anjuta, etc are highlighted. Also see in this screenshot how I have placed all the apps I use more in  frequently in the launcher for quick access, and eliminated the need to go through the  dash. 
[ATTACH]206538[/ATTACH]
It is configured to do so in the Ubuntu Unity Plugin (see screenshot #4). When I click one of these opened apps in the launcher, compiz automatically switches to the correct desktop for that app. 
[ATTACH]206536[/ATTACH]
Inside Unity Plugin settings there's also an option to "Bias Alt+Tab" to show only windows in current desktop, which I don't use. 

I also switch a lot using Ctrl+Alt+Right, Ctrl+Alt+Left, Ctrl+Alt+Up, Ctrl+Alt+Down. And sometimes I just press Super+S (Expo Plugin) to see whats happening at all 8 desktops (See screenshot #1) and just use the mouse or arrows to select one.

You can also use Shift +Alt +Up (Scale Plugin) to display only the opened windows in an specific viewport (See screenshot #5). And then use the mouse. It's very practical.
[ATTACH]206537[/ATTACH]
There are many options, many customizations to all these options inside ccsm. And many I don't even use, because I don't need them until now. There are other switchers and ways to switch / customize the switch process. It's a lot to play with. Each person can certainly find ways to make their everyday use more comfortable, easy and productive. In previous "traditional" session, with no Compiz, there was alt+tab. We have a hundred possibilities now.

[B]
EDIT: [/B]One of the things that really make life easier is the possibility to assign and change keyboard shortcuts for all the Compiz Plugins inside CCSM. Check "Bindings" for each plugin. It takes a while to reach the best config for each user and set keys to launch each of them, but you really feel an improvement in speed and productivity once you do so.

---

### Post by effenberg0x0 on 2011-11-06
When I go to the dash I rarely go scrolling and searching  for apps. I just type some word that can relate to the app I want. See  an example in the screenshot. I typed "Photo", and my image related apps  appeared. One click to open the dash, typed "Photo". That's all it took  to see graphic apps.
[ATTACH]206539[/ATTACH]
It's nice cause you don't even need to remember the name of all apps.

---

### Post by NTL2009 on 2011-11-06
effenberg0x0, thanks, these tips help, but they are still a far, far cry from what I've set up which makes my system efficient for me. Some comments:

> **effenberg0x0 said:**
> I use 8 "desktops" (see screenshot #1). Some of my applications are locked to these desktops automatically using the "Place Windows" plugin (see screenshot #2).  This could be handy for my mail and sys-monitor, which I do typically leave in a specific workspace. But most others I use in multiple spaces, often at the same time.


> The launcher puts an arrow on the side of the open apps an highlights all my open apps, at all desktops, all the time (See screenshot #3). Yes, but that is only marginally useful. Of course I know I have my web browser open. But it is open in multiple workspaces - looks like a second click gives a preview window of each open window, but it doesn't tell me enough to know which one they are (they are small), and it doesn't tell me which workspace they are on (is that my Writer window with finance info, or my Writer window with some Ubuntu install notes? They look the same).

My Window List shows me all open windows and gives as much title a there is space for. There are just so many more visual clues this way. 

> I also switch a lot using Ctrl+Alt+Right, Ctrl+Alt+Left, Ctrl+Alt+Up, Ctrl+Alt+Down. And sometimes I just press Super+S (Expo Plugin) to see whats happening at all 8 desktops (See screenshot #1) and just use the mouse or arrows to select one.
Again, not enough visual clues for me. When I do this in my 10.04 setup, the Window List gives me a lot of info. 


> **effenberg0x0 said:**
> When I go to the dash I rarely go scrolling and searching  for apps. I just type some word that can relate to the app I want. See  an example in the screenshot. I typed "Photo", and my image related apps  appeared. One click to open the dash, typed "Photo". That's all it took  to see graphic apps.


It's nice cause you don't even need to remember the name of all apps.

I disagree that this is 'nice'. It's OK for somethings. But like I said earlier, I don't do photo or image editing that often, but I still have a collection of about 18 programs for those tasks. It had me clicking the 'show more', an added step. And they take up valuable screen space with "apps you can download', when I already know I'm looking for something I installed. If I wanted to DL something new, I'll go to the Software Center. 

But in my menu in 10.04, I can have them in an order/grouping that makes sense to me, with separators or sub-folders if that makes sense for what I'm doing. All with either the mouse _OR_ the keyboard, and I do either, depending where my hands are. And it all comes 'naturally', because I know where everything is because I put it there.  That is so much better for me than a list of things matching some entry like 'photo', in an order the computer decides. Sorry, just doesn't cut it for me.

-NTL2009

---

### Post by effenberg0x0 on 2011-11-06
Would this be useful to you? [http://ubuntuforums.org/showthread.php?t=1874814](http://ubuntuforums.org/showthread.php?t=1874814)
See last screenshot I posted.

Also, check Unity Bliss. I think you may like it.
[http://www.omgubuntu.co.uk/2011/11/unity-bliss-an-alternative-application-lens-for-ubuntu/](http://www.omgubuntu.co.uk/2011/11/unity-bliss-an-alternative-application-lens-for-ubuntu/)

[ATTACH]206549[/ATTACH]

Regarding your other comments, I fail to see how having many switcher plugins, each with many different configurations, can possibly represent fewer options than what existed as default in previous Ubuntu releases. It makes no sense to me. The only advice I can give you is to not update or use another distro.

---

### Post by seeker5528 on 2011-11-07
> **PaulInBHC said:**
> I think MS had it right with Home and Professional versions of Windows.

You mean charge extra for the ability to join a domain and to have backup and file permission options that should be there in all versions of windows anyway?

Later, Seeker

---

### Post by PaulInBHC on 2011-11-07
Not exactly. What I have noticed is that some of the Unity likers are casual home users and some of the Unity dislikers are complaining that it interferes with their work flow. This gives me the idea that there could be two install options. One for casual users with Unity and one for businesses with a classic desktop.

---

### Post by seeker5528 on 2011-11-07
> **PaulInBHC said:**
> Not exactly. What I have noticed is that some of the Unity likers are casual home users and some of the Unity dislikers are complaining that it interferes with their work flow. This gives me the idea that there could be two install options. One for casual users with Unity and one for businesses with a classic desktop.

From what I've seen, it seems like the "work flow" issues fall into 4 categories, have not taken the time to see how to take advantage of the way Unity works, can't get used to the way Unity works, refuse to learn something new, and in some corner cases there is a genuine limitation in the way Unity works.

But the people who speak the most loudly the most often about work flow issues in Unity typically are not the people who are able to give a genuine example of how a limitation in Unity has a genuine affect on their work flow. 

People sometimes have specific ways in which they work, which Unity will not allow, but a few small adjustments in the way they approach things could allow something pretty close if you look at it from a standpoint of the work flow as opposed to getting bogged down in the details about the way the tools work.  

It helps too if people posting "Unity improvement" ideas actually make suggestions based on the way Unity works as opposed to throwing out a bunch of random incompatible suggestions based on the way other environments work. That's not to say everybody should know if their ideas are compatible or not, but they should be willing to have a discussion about it and if necessary come up with an alternative suggestion that might fit better, and get suggestions on how to make a good use case argument for why the change should be implemented.

A good, respectfully worded use case showing how Y is a useful new feature or an improvement over existing feature X, or that Z is broken because...., carries more weight that some random poll or vague forum statistic, if you can get it viewed by the right person/people at an opportune time.

Later, Seeker

---

### Post by mc4man on 2011-11-07
> **NTL2009 said:**
> 
looks like a second click gives a preview window of each open window, but it doesn't tell me enough to know which one they are (they are small), and it doesn't tell me which workspace they are on (is that my Writer window with finance info, or my Writer window with some Ubuntu install notes? They look the same).

you may find that enabling the scaleaddons & text plugins useful, they haven't been updated in quite some time & could be refined but do display window title & if room workspace # while in the spread

> **NTL2009 said:**
> 
My Window List shows me .... 

While i'm fine with the spread most of the time, a window list could be a useful option, maybe given some time ubuntu will provide a option or someone will create one

Currently trying an older WL that wasn't designed for ubuntu but works pretty good with some limitations
In all sessions the tooltips don't work, in compiz all workspaces are considered the same desktop so only 1 Wl 
In metacity or mutter each Ws can get it's own Wl

So if some old app can do this there's no reason to think the option will arise. screen show on unity 3d, more visible then appears in screen

As far as your 17 or some video apps - create 1 or 2  category based quicklist icons - faster, more direct than any gnome 2 menu

Edit: the xfce4-panel also works quite well as a bpttom panel for window lists & more if desired, screen 2

---

### Post by sgage on 2011-11-08
> **seeker5528 said:**
> From what I've seen, it seems like the "work flow" issues fall into 4 categories, have not taken the time to see how to take advantage of the way Unity works, can't get used to the way Unity works, refuse to learn something new, and in some corner cases there is a genuine limitation in the way Unity works.

But the people who speak the most loudly the most often about work flow issues in Unity typically are not the people who are able to give a genuine example of how a limitation in Unity has a genuine affect on their work flow. 

People sometimes have specific ways in which they work, which Unity will not allow, but a few small adjustments in the way they approach things could allow something pretty close if you look at it from a standpoint of the work flow as opposed to getting bogged down in the details about the way the tools work.  

It helps too if people posting "Unity improvement" ideas actually make suggestions based on the way Unity works as opposed to throwing out a bunch of random incompatible suggestions based on the way other environments work. That's not to say everybody should know if their ideas are compatible or not, but they should be willing to have a discussion about it and if necessary come up with an alternative suggestion that might fit better, and get suggestions on how to make a good use case argument for why the change should be implemented.

A good, respectfully worded use case showing how Y is a useful new feature or an improvement over existing feature X, or that Z is broken because...., carries more weight that some random poll or vague forum statistic, if you can get it viewed by the right person/people at an opportune time.

Later, Seeker

For many months, people have been giving detailed examples of exactly how Unity disrupts their work flow. It's typically not something that a little tweaking around the edges will address. It's not about refusing to learn something new, or being unable to.

---

### Post by cariboo on 2011-11-08
Moved 5 very off topic posts to the jail.

---

### Post by Maju on 2011-11-09
For me the problems with unity are two (besides that annoying almost useless side tab):

1. I like long unfolding menus with submenus and submenus of the submenus, which apparently unit does not support. 

2. I like my DISTINCT classic top and bottom bars, which help me control my equally DISTINCT windows. 

All that does not seem to work in Unity. I do not "hate" Unity, I do not have technological issues as reported by some with it... but I want an option and somehow Ubuntu is denying it to me (which is, I understand against the very philosophy of the OS, which should be fully configurable).

---

### Post by coffeecat on 2011-11-09
And I've just moved another OT post to the jail.

A reminder:

This is the Ubuntu +1 forum. This thread is to discuss ways of helping people who do not like Unity to get to a "classic" desktop.

This is not the place to post anti-Unity rants.

This is not the place to post "I've moved to Mint" comments.

---

### Post by Maju on 2011-11-09
> **seeker5528 said:**
> People sometimes have specific ways in which they work, which Unity will not allow

Why does it not? Because it is wrongly conceived to FORCE users to work in certain ways. If Unity would be a good idea, it'd be easily configurable to allow users to keep whatever parts of the old methods that they consider appropriate. 

> ... but a few small adjustments in the way they approach things could allow something pretty close

No. I do not see unfoldable menus anywhere in unity, I do not see the low bar (or any alternative place) where my active applications are listed obviously... 


> It helps too if people posting "Unity improvement" ideas actually make suggestions based on the way Unity works as opposed to throwing out a bunch of random incompatible suggestions based on the way other environments work.

Look: I see Unity and I want Gnome! Compiz, Nautilus or whatever but give me back the old feeling or I will have to change OS. 

> That's not to say everybody should know if their ideas are compatible or not, but they should be willing to have a discussion about it and if necessary come up with an alternative suggestion that might fit better, and get suggestions on how to make a good use case argument for why the change should be implemented.

Why don't the devs step down their suicidal pedestal? No menus, no lower bar (or equivalent)... it's a total disaster! I can GO AROUND these problems but it takes a lot of my time and definitely is not what I want for my PC. I want an option to go back to Gnome, and that option should be default in the installation.

---

### Post by effenberg0x0 on 2011-11-09
> **Maju said:**
> For me the problems with unity are two (besides that annoying almost useless side tab):

1. I like long unfolding menus with submenus and submenus of the submenus, which apparently unit does not support. 

2. I like my DISTINCT classic top and bottom bars, which help me control my equally DISTINCT windows. 

All that does not seem to work in Unity. I do not "hate" Unity, I do not have technological issues as reported by some with it... but I want an option and somehow Ubuntu is denying it to me (which is, I understand against the very philosophy of the OS, which should be fully configurable).

You're missing the point. In this very section of the forum (as well as mostly others and many sites - see Google) you'll find a couple ways to re-enable the traditional top/bottom menus, as well as disable the Unity plugin (Laucher/Taskbar/Global Panel), which gives you a desktop very similar to what you got used to. 

If Ubuntu really wanted to deny anyone this, they would create ways to avoid such workarounds, take these packages out of the repos, etc. 

With small efforts, say 10 minutes, you can get exactly what you want back.

---

### Post by effenberg0x0 on 2011-11-09
I just thought of a fun solution, don't know why I haven't thought of that earlier. 

Everyone is working on ways to recreate the old DE experience by going back to the traditional (now unsupported) panels, tweaking stuff, etc. 

What if the two top/bottom panels were recoded as a **Compiz Plugin**? :)

It could easily be activated/deactivated via ccsm, which would auto activate/deactivate Unity, much like conflicting Compiz plugins already work.

It's doable, a (rather useless) fun project, and would somehow calm things down by re-creating the experience some users seem to enjoy and want back. Maybe there are some talented coders among all the people that don't want to use Unity that would contribute and even take over such a project. And it would mitigate the risks of broken systems, suicidal DE changes, etc.

---

### Post by ventrical on 2011-11-09
> **Maju said:**
> Why does it not? Because it is wrongly conceived to FORCE users to work in certain ways. If Unity would be a good idea, it'd be easily configurable to allow users to keep whatever parts of the old methods that they consider appropriate. 



No. I do not see unfoldable menus anywhere in unity, I do not see the low bar (or any alternative place) where my active applications are listed obviously... 




Look: I see Unity and I want Gnome! Compiz, Nautilus or whatever but give me back the old feeling or I will have to change OS. 



Why don't the devs step down their suicidal pedestal? No menus, no lower bar (or equivalent)... it's a total disaster! I can GO AROUND these problems but it takes a lot of my time and definitely is not what I want for my PC. I want an option to go back to Gnome, and that option should be default in the installation.


FVWM-Crystal desktop is available from the repos. So is Cairo.  FVWM uses minimal resources . I do not see what the issue is here. As for GNOME .. I think that there is a point in time where we have to accept .. sort of like that Charlie the Tuna commercial "what .. you want tuna with good taste or tuna that tastes good".  I would think in time before the release of Precise  that the minds at Canonical will have ironed out the 'precise' details as to how to incorporate all the razzle -dazzle GNOME effects into a GNOME fallback session.  I think with the FOSS concept that patience is truly a virtue.

---

### Post by seeker5528 on 2011-11-09
> **sgage said:**
> For many months, people have been giving detailed examples of exactly how Unity disrupts their work flow. It's typically not something that a little tweaking around the edges will address. It's not about refusing to learn something new, or being unable to.

Being detailed and showing that Unity fails to allow a similar work flow pattern as Gnome 2 or does so in a way that negatively impacts productivity are two different things.

And like I said there are some legitimate issues with good use case descriptions. Most commonly with people to often run several apps or have several windows open of a small number of apps and the application windows are spread across multiple desktops.

Most commonly I might have 3 to 5 windows open, 9ish some times, rarely 12 or more. With those numbers, having different combinations of single instances of apps on different desktops, apps on a single desktop with multiple windows, apps with multiple windows spread out of different desktops, organized on different desktops relative to what I am doing, it's pretty quick and easy to switch between different windows on different desktops. Typically clicking the icon of the open app or the desktop switcher to change, but 'Ctrl'+'Alt'+'Arrow' works good. 

Holding the 'Alt' key down and hitting 'Tab' to cycle through the apps and 'Arrow' to get to and from the preview generally seems decent, could probably be better for cases where you have more than 4 windows open from the same app, at least from what I see other people saying. 

Typically I don't have content open in the different windows that is so much the same that I can't tell which window I want even with 12 windows of the same app open.   

Personally I would prefer a larger preview in the background as I am tabbing through the apps and to cycle through previews of an application's open windows with the up and down arrow keys. But I see that as more of a preference thing, not something that really has much affect on my work flow.

And when it comes to Gnome Shell, I can certainly understand people having a preference for it over Unity, but I can't understand how people can claim Unity in it's OOB configuration is a bane of productivity, then claim productivity in Gnome Shell is good in it's OOB configuration.  

Later, Seeker

---

### Post by seeker5528 on 2011-11-09
> **Maju said:**
> Why does it not? Because it is wrongly conceived to FORCE users to work in certain ways. If Unity would be a good idea, it'd be easily configurable to allow users to keep whatever parts of the old methods that they consider appropriate.

Is KDE wrong because it doesn't work like Gnome?
Is Lubuntu wrong because it doesn't work like WindowMaker? 

> No. I do not see unfoldable menus anywhere in unity, I do not see the low bar (or any alternative place) where my active applications are listed obviously... 

Maybe somebody will port the [Classic Menu Indicator](http://ubuntuguide.net/classic-menu-indicator-applet-in-ubuntu-11-04-unity-system-tray)

Personally don't see the need when you can do 'Dash --> More apps --> filter results --> some category --> show more/fewer results' just as quickly.

> Look: I see Unity and I want Gnome! Compiz, Nautilus or whatever but give me back the old feeling or I will have to change OS. 

That old feeling is gone, the Gnome fall back environment is reasonably similar, so no need to change distributions to get that, but it doesn't quite have the same feeling to me.

Don't know what's going on with Mint "keeping Gnome 2" and how long that will last.

Later, Seeker

---

### Post by Hylas de Niall on 2011-11-10
> **seeker5528 said:**
> Don't know what's going on with Mint "keeping Gnome 2" and how long that will last.

Later, Seeker

Well, simple answer is that they're not! Mint 12 is Gnome 3 with a modded Gnome Shell (mods 'switch on and off-able')

[http://blog.linuxmint.com/?p=1851](http://blog.linuxmint.com/?p=1851)

---

### Post by effenberg0x0 on 2011-11-10
A very viable option is to take a screenshot of the old desktop, put it as the screen background and then map mouse-click behaviors at every screen-coordinate (show something, hide something, switch, etc) using xda plus some scripting.

---

### Post by Merk42 on 2011-11-10
I can't wait until the forum change.
Since it will look different it will therefore be diffcult to use so maybe there will be less posting.

> **PaulInBHC said:**
> One for casual users with Unity and one for businesses with a classic desktop.
Read my signature. Not an option.

GNOME 2 **is dead**. Even the GNOME Fallback in GNOME 3 soon will be.

---

