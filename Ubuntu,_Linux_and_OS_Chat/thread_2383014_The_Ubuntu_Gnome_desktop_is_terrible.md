---
title: "The Ubuntu Gnome desktop is terrible"
date: 2018-01-19
forum: Ubuntu, Linux and OS Chat
---

### Post by JasonFWard on 2018-01-19
And I wish it didn't.

When Unity first came around, I struggled with it for a while, but it improved and I grew to like it, really like it, the way it worked became intuitive, it was slick, it was easy.

Then development of Unity stopped, a shame I thought, but I've changed GUI more than once, and last time I used Gnome is pretty good.

But.... uh... I've tried, I've been using the default Ubuntu Gnome GUI since October, and there are things about it that just find frustrating and annoying.

I want my windows to have their own controls, not hover on a bar on a different monitor, and when I hit a window control (close, minimize, maximise etc) I want to be confident about what window is actually going to be acted on.  I'm actually finding this stuff tiring.

The in GUI search function just doesn't work anything like as well as Unity did.

Any why I can't have the time and date showing all the time in the window chrome I do not know, it's something I really want, I'm forever minimising windows to see the time, or even more bizzarely asking the people around me what time it is, I feel like I've gone back years.

I tried to configure Gnome, tried some addons, but so far nothing fixes any of these problems and I'm wondering if its time to ditch Ubuntu and try something else.

AH!

Thank you for listening to my moan.

---

### Post by litlesam on 2018-01-19
Don't limit yourself to Gnome, you have KDE, Mate, Xfce and more.

Start loading those USB sticks.

---

### Post by galacticstone on 2018-01-19
> **JasonFWard said:**
> And I wish it didn't.

When Unity first came around, I struggled with it for a while, but it improved and I grew to like it, really like it, the way it worked became intuitive, it was slick, it was easy.

Then development of Unity stopped, a shame I thought, but I've changed GUI more than once, and last time I used Gnome is pretty good.

But.... uh... I've tried, I've been using the default Ubuntu Gnome GUI since October, and there are things about it that just find frustrating and annoying.

I want my windows to have their own controls, not hover on a bar on a different monitor, and when I hit a window control (close, minimize, maximise etc) I want to be confident about what window is actually going to be acted on.  I'm actually finding this stuff tiring.

The in GUI search function just doesn't work anything like as well as Unity did.

Any why I can't have the time and date showing all the time in the window chrome I do not know, it's something I really want, I'm forever minimising windows to see the time, or even more bizzarely asking the people around me what time it is, I feel like I've gone back years.

I tried to configure Gnome, tried some addons, but so far nothing fixes any of these problems and I'm wondering if its time to ditch Ubuntu and try something else.

AH!

Thank you for listening to my moan.

I'm still something of a noob, so take this with a generous block of salt. Your mileage may vary.

Unity was my first initial experience with Linux and I found it easy to use and surprisingly intuitive. I didn't really have any complaints, other than a few minor annoyances - the latter are things that can ruin an otherwise spectacular experience for me. I'm crazy like that. So, while trying to make things look and work the way I wanted it to, I wound up with Gnome. For me, it seems more intuitive overall for the types of simple tasks I do (and single workspace). 

The only thing I really like about Unity was the search. I agree that the Gnome search is weaker than Unity, and it's more akin to a straight Windoze search. But, I can generally work around that and I don't use the search much any way.

From someone not previously attached to either one, the fact that the future LTS version of Ubuntu is going to be Gnome is what helped me decide to stick with it for now. Although, if something better comes up down the line, I will look at it.

---

### Post by kansasnoob on 2018-01-19
Maybe try Ubuntu MATE Mutiny DE:

[http://news.softpedia.com/news/ubuntu-mate-17-10-welcomes-unity-fans-with-new-mutiny-layout-ships-with-snaps-518132.shtml](http://news.softpedia.com/news/ubuntu-mate-17-10-welcomes-unity-fans-with-new-mutiny-layout-ships-with-snaps-518132.shtml)

I also believe that a group of people are trying to keep Unity 7 working "as is" until UBports completes their fork of Unity 8.

I actually preferred either GNOME Shell or the "flashback" session over Unity beginning with 14.04 so I'm biased but I do understand your frustration.

---

### Post by DuckHook on 2018-01-20
I sympathize. That's not just a throw-away sentiment: I really do. But as an old-timer on these forums I've seen this movie repeatedly.

When Unity first appeared, the sky was falling. Likewise when Kubuntu went to Qt. Gnome going from version 2 to 3 generated more bags of hate mail than some serial murder trials.

All eventually evolved into very nice desktops that work quite effectively. Partly, we as users get used to how they do things differently. Partly, those desktops learn from prior iterations and get steadily better. It takes time.

Ubuntu has ***seven*** official flavours (dropping to six in a few years). There's everything from soup to nuts. They're free to all for the time investment of a download. We can wander through them like a kid in a candy store trying this, dropping that, settling on what we like, all the while, blithely secure in the confidence that they share the same base and therefore will be as stable as we are ever likely to achieve in this imperfect world. In contrast, if we were stuck in the proprietary sphere, we get no choice. If you don't like what they have on offer, you can go pound salt.

I think it's worthwhile collaborating with the devs on what can be improved, what's irritating, what's awkward, etc. So, don't moan. Instead, get involved.

---

### Post by again? on 2018-01-20
I can appreciate the frustration with gnome but parts of your post baffle me.
gnome-tweak-tool allows you to configure window buttons.
By default the window controls are in the application window and why can't you always see the time in the top panel?

---

### Post by JasonFWard on 2018-01-20
> **guber2 said:**
> I can appreciate the frustration with gnome but parts of your post baffle me.
gnome-tweak-tool allows you to configure window buttons.
By default the window controls are in the application window and why can't you always see the time in the top panel?

UH?  What?  Really?  That's not how things are for me.

I have two monitors and try what I might, the window controls remain on the right hand monitor on the top panel.  I'm looking gnome-tweak-tool as I type and I can find no option to change this.

The top panel can and does have the time, BUT, many games I play go full screen or even a fake full screen (borderless window but with min, max etc) and cover up the bar, which under Unity was never a problem since the the bar was also on the second monitor.  But its a double issue, because with the bar covered up, I can't minimise any windows, including the window that covers the controls.

EDIT : I should clarify, I run virtually everything full screen, and under Unity I could still see Window chrome, in Gnome I cannot, this is why I see no controls associated with the window I'm currently using.

---

### Post by again? on 2018-01-20
I'm  on 17.10 using the ubuntu Xorg session.
```
glen@artful:~$ lsb_release -dc
Description:	Ubuntu 17.10
Codename:	artful
glen@artful:~$ echo $DESKTOP_SESSION 
ubuntu-xorg
```

You could use a conky window, set above, to always display the time in the bottom right corner(see attached pic).
Shows for fullscreen windows including while playing counterstrike.
[ATTACH=CONFIG]278258[/ATTACH] [ATTACH=CONFIG]278259[/ATTACH] [ATTACH=CONFIG]278261[/ATTACH]

If you predominantly use fullscreen windows you can use keyboard shortcuts for window manipulation.
[ATTACH=CONFIG]278262[/ATTACH]

You can also use hide top bar and dash to dock extensions which both have autohide settings.
Then just use maximised windows instead of fullscreen. How that works on dual monitors I don't know though.

---

### Post by Chanath on 2018-01-20
Have a look at Ubuntu Community site.
You'd find few links here; [https://community.ubuntu.com/t/testing-unity-session-in-18-04/987](https://community.ubuntu.com/t/testing-unity-session-in-18-04/987)
Also, there is a dedicated forum on Unity 7 in Ubuntu; [https://community.ubuntu.com/c/desktop/ubuntu-unity-dev](https://community.ubuntu.com/c/desktop/ubuntu-unity-dev)

You can install Ubuntu Unity desktop by,  

> [COLOR=#333333][FONT=Consolas]sudo apt-[/FONT][/COLOR][COLOR=#333333][FONT=Consolas]**get**[/FONT][/COLOR][COLOR=#333333][FONT=Consolas] install ubuntu-unity-desktop[/FONT][/COLOR]
You can download Unity 7 based live installable isos from [here]("https://sourceforge.net/projects/unity7sl/") and [here]("http://people.ubuntu.com/~twocamels/archive/"). 
Once you install, just do > sudo apt update && sudo apt upgrade

And, join [https://community.ubuntu.com/c/desktop/ubuntu-unity-dev](https://community.ubuntu.com/c/desktop/ubuntu-unity-dev)

---

### Post by cariboo on 2018-01-20
@JasonFWard as a note of caution, I'd suggest ignoring the first link, as the author of the iso hasn't stepped forward publicly to offer any support, or even reveal his identity, so we don't know if there is any malicious packages included in the iso, and if there are, we don't know who to go after to get the problems resolved.

---

### Post by kansasnoob on 2018-01-20
> **cariboo said:**
> @JasonFWard as a note of caution, I'd suggest ignoring the first link, as the author of the iso hasn't stepped forward publicly to offer any support, or even reveal his identity, so we don't know if there is any malicious packages included in the iso, and if there are, we don't know who to go after to get the problems resolved.

Just to be 100% clear, you mean avoid this link:

[https://sourceforge.net/projects/unity7sl/](https://sourceforge.net/projects/unity7sl/)

---

### Post by cariboo on 2018-01-20
> **kansasnoob said:**
> Just to be 100% clear, you mean avoid this link:

[https://sourceforge.net/projects/unity7sl/](https://sourceforge.net/projects/unity7sl/)

Yes.

---

### Post by JasonFWard on 2018-01-21
OK thanks everyone for your replies.

Back when Unity was  terminated I decided to I would stick with whatever was going to be the  default GUI as like I say I'd adapted to new GUI's before and this  change was supposed to be minimal, but most of all because I want  something that can easily be supported.

But after sticking with  it for several months and finding my dislike increasing not decreasing,  and taking the opportunity of this thread to think about it, I'm going  to try a different GUI.

---

### Post by speedwell68 on 2018-01-21
Give Xubuntu a try.  It really is an awesome experience.

---

### Post by lammert-nijhof on 2018-01-21
The new Ubuntu 17.10 is great and I like it. Maybe I am adapting easily to new situations, because I worked and lived in a number of countries. I never had a problem adapting to a new HMI. I liked Unity from the start and I like 17.10 too. I don't miss 16.04, maybe some of its features, that I can't remember now. But I have other features, I like from 17.10, like Night Light, the dynamic management of the # of desktops, the nice integration of Vbox VMs and their appearance in the launcher. 

I'm 72, but I have the feeling that there are many grumpy "old" men in the Linux community. If you move to another country you have to adapt to the local habits, you can't live in exactly the same way as in your own country. The same is true for changes to the HMI, be flexible and use your intelligence to adapt your way of doing things.

What gives me some problems is the location of the icon to the menu of the programs. Too often I start the file manager (top icon) instead of the program menu, but I know I will get used to it even with 72.

---

### Post by DuckHook on 2018-01-21
> **lammert-nijhof said:**
> The new Ubuntu 17.10 is great and I like it. Maybe I am adapting easily to new situations, because I worked and lived in a number of countries. I never had a problem adapting to a new HMI. I liked Unity from the start and I like 17.10 too. I don't miss 16.04, maybe some of its features, that I can't remember now. But I have other features, I like from 17.10, like Night Light, the dynamic management of the # of desktops, the nice integration of Vbox VMs and their appearance in the launcher. 

I'm 72, but I have the feeling that there are many grumpy "old" men in the Linux community. If you move to another country you have to adapt to the local habits, you can't live in exactly the same way as in your own country. The same is true for changes to the HMI, be flexible and use your intelligence to adapt your way of doing things.

Bravo. And you do not give yourself enough credit…

…there are a lot of grumpy *young* men in the Linux community too.

---

