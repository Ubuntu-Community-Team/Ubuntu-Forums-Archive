---
title: "Xfce: What am I missing??"
date: 2007-06-14
forum: The Cafe
---

### Post by ThinkBuntu on 2007-06-14
Most places I go, people seem to really enjoy Xfce and sing its praises. Off the top of my head, I have these complaints about it though: Directional keys are useless on the desktop, not much customizability, especially with panel applets, and no progress indicators when manipulating files (i.e. copying my 6GB home folder backup off my iPod is a matter of just guessing when it's finished!).

So, what am I missing? I used Zenwalk for a while, and was still able to work in the environment, but it seemed to have shortcomings besides silly stuff like eye candy and bundled apps. To the Xfce people here: are there ways to circumvent these issues? Can Xfce be made to be an awesome environment, or at least on par with GNOME, etc?

I used KDE for a while, and now am a GNOME user, but I always felt that Xfce was a trimmed-down DE that really could be a drop-in for GNOME, only I didn't know what I was doing.

---

### Post by celsofaf on 2007-06-14
I have mostly exactly the same concerns as you do. By the way, I'm realy enjoying running Arch Linux with XFCE and, although I don't realy mind those minor problems you talk about, it would be nice to have them circumvented at least.

Anyone?

---

### Post by FuturePilot on 2007-06-14
Hmmm. I've also found it has its shortcoming. The one thing I really liked was the built in composite manager. Worked good on my laptop which can't handle Beryl. But then the shadow under the xfce panel disappeared and I couldn't get it back:-?
The menu editor is bad, pretty much useless when it comes to editing what's already in the menu. After playing around with XFCE for a while I went back to Gnome.

---

### Post by LightB on 2007-06-14
Here's one thing it has better (than Gnome at least): You can actually use svg icon sets without the file manager grinding to a halt. In fact, they seem even faster than png, but that could just be my imagination.

---

### Post by ThinkBuntu on 2007-06-14
Not that I care, but the composite manager for Xfce included in Zenwalk didn't work...

---

### Post by crimesaucer on 2007-06-14
Have you ever tried to write your own gtkrc for XFce and the xfce-engines?

I found it very easy to learn how to write for xfce, and I have been able to make it look many different ways. 

Check out the deviantART Linux-XFce section and you will see about 10 different themes I have done for xfce. This is my Gallery: [http://crimesaucer.deviantart.com/gallery/](http://crimesaucer.deviantart.com/gallery/)

Plus...the Xfce-Looks.org page has many different themes...And if I wanted to use any other theme engine like Murrina or clearlooks, I am able to do that as well, so there is no shortage of themes. Same thing goes for icons.

I am very happy with xfce4.4...I don't use the composite because I use Beryl...and I have to admit that I've only used xfce since xubuntu was my first install...but I have tried gnome in ubuntu a few times and I didn't like it much except that it was more beginner friendly...and most guides and "HowTo's" are written for gnome in Ubuntu Forums, and to do the same things with xfce4.4, you always have to figure it out for xubuntu.

I agree with the fact that the menu editor is difficult...and to edit the included system menu, you have to edit it here: [http://ubuntuforums.org/showthread.php?t=421973&highlight=menu+edit+include+system](http://ubuntuforums.org/showthread.php?t=421973&highlight=menu+edit+include+system)

Personally, for me, I just love how much faster it is than gnome. I have grown to really like the Xfce Terminal and the Thunar File System. I also like the Orage calendar and the other panel plug-ins.

I think they could work on a few things, but I use it because of how fast it is and because I like how it is "less" of a beginner OS...so I have to actually learn the correct Linux ways to do things.


EDIT- I also have a progress bar for file transfer...and my directional keys work, the only things that doesn't work on my HP Laptop are my volume mute hp buttons...but they didn't work in ubuntu either. And writing a gtkrc can change any app and theme, and as for the panel...with the menu and launcher...just write a .gtkrc-2.0 with an image and you will have a glossy panel.

this is mine:

```

style "panel"
{
  bg[NORMAL] = "#E9B9D3"
  bg_pixmap[NORMAL] = "panel89.png"
  fg[NORMAL] = "#000000"
  }

widget_class "*Panel*"      style "panel"
widget "*Panel*"            style "panel"
class "*Panel*"             style "panel"



```

---

### Post by FuturePilot on 2007-06-14
For your volume buttons you should look into xev to get them working.;)

---

### Post by crimesaucer on 2007-06-14
You mean the LED buttons, like the power off button? If so, do you have a link to a page of instructions of how to fix it?

Thanks.

---

### Post by FuturePilot on 2007-06-14
I mean your volume and mute buttons. Hope this helps:)
[http://ubuntuforums.org/showthread.php?t=457059&showpost=#2]("http://ubuntuforums.org/showthread.php?t=457059&showpost=#2")

---

### Post by crimesaucer on 2007-06-15
Thank you, that would totally work except I have most of my F1 - F12 keys used for Beryl plug-in bindings and other things...plus, I have the xfce panel plug-in with volume that works perfectly...so I'll probably just leave them inactive...but thanks for the nice guide.

---

### Post by SoulinEther on 2007-06-15
For me, I have (virtually) no problems using Xfce. I've used GNOME for a long time.. but after installing a whole bunch of extra features (including Beryl), I found better results in using Xfce. Faster, lighter, smoother.

Thunar is quick. Like... really quick. I don't really care for the lack of the progress bar to be honest, lol. And if you really want a progress bar, run Nautilus instead of Thunar. That's the beauty of Xfce; it's not one package, but rather a set of packages that create a fully featured desktop. You can pick and choose whatever you want. I've ran xfce with the gnome desktop. Xfce with gnome panels. Xfce with Nautilus. Etc.

AND xfce is much more customizable than Gnome - all from a very convenient menu.

Xfce is more "meat" than bread.

---

### Post by RAV TUX on 2007-06-15
I found the best distro for Xfce is [**[B]Wolvix.**[/B]]("http://wolvix.org/")

---

### Post by SoulinEther on 2007-06-15
I found the best way to get +1 is to post somewhat relevant but obviously irrelevant information in topics, but hey, that's just me. :D

---

### Post by crimesaucer on 2007-06-15
Is this the xfce progress bar that you were talking about?

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-129.png[/IMG]

---

### Post by dannymichel on 2007-06-15
> **jordanmthomas said:**
> Well, on the plus side I know what you're talking about now.
On the down side, I have actually wondered how to fix this myself (at least in nautilus)  
I've looked around but can't really come up with anything.  I guess someone else will have to hop in here and offer some sort of suggestion.

XFCE is kind of like gnome-light (or so they say) and it uses gtk themes just like Gnome.  In my experience it's becoming about as heavy on resources as Gnome is.  

Engines that aren't Murrina:  Pixmap, Clearlooks, Candido, Rezlooks, etc.
Changing engines won't let you fix the buttons in nautilus.  A theme for Firefox *might* work though.
I don't JUST want to change it on Firefox though.
I want to chage it for every window on my desktop.
What's this?
[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-71-1.png[/IMG]
> **mcduck said:**
> That padding is defined in themes, to change it you need to edit the themes gtkrc file. Or try to find another theme with less padding..
How do I edit my themes gtkrc file?

> **jordanmthomas said:**
> 
XFCE is kind of like gnome-light (or so they say) 
My desktop is a LOT slower when I use XFCE  session.
Is that the only difference for XFCE? Because if the supposed speed is suppose to be the only difference I have no reason to use it.

[[IMG]http://www.geekdum.com/forums/gallery/data/501/medium/XFCE_Panel.png[/IMG]]("http://www.geekdum.com/forums/gallery/data/501/XFCE_Panel.png")
You see the size of that icon?
Why is it so tiny when I shrink my panel size?
I mean, I set my panel size to 24 on my REGULAR Ubuntu desktop and it's the equivalent of when I set my panel size(height) to 16 on XFCE(why is that?)
Why is the icon so small when I set it to 16?
This is a bug?

---

### Post by crimesaucer on 2007-06-15
> **dannymichel said:**
> I don't JUST want to change it on Firefox though.
I want to chage it for every window on my desktop.
What's this?
[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-71-1.png[/IMG]

How do I edit my themes gtkrc file?


My desktop is a LOT slower when I use XFCE  session.
Is that the only difference for XFCE? Because if the supposed speed is suppose to be the only difference I have no reason to use it.

[[IMG]http://www.geekdum.com/forums/gallery/data/501/medium/XFCE_Panel.png[/IMG]]("http://www.geekdum.com/forums/gallery/data/501/XFCE_Panel.png")
You see the size of that icon?
Why is it so tiny when I shrink my panel size?
I mean, I set my panel size to 24 on my REGULAR Ubuntu desktop and it's the equivalent of when I set my panel size(height) to 16 on XFCE(why is that?)
Why is the icon so small when I set it to 16?
This is a bug?

The pictured apps are: Firefox 2, Xfce Terminal, and the widget factory...a program to view your buttons and theme modifications....known as widgets.

What you are looking at is one of my gtk-2.0 themes that actually is lightning fast on my xubuntu...it themes Firefox 2 so that you don't need a slower Firefox theme...there are no pixmaps used in this theme, except my panel .gtkrc-2.0 which uses a bg_pixmap[NORMAL]

I also use a small userChrome.css image for the Firefox tab-bar to make it look better...with no slowing effects...And I put my own Toolbar.png icons in the browser folder.


Using GIMP, I made a custom image for my Xfce Terminal to match my gtk-2.0 theme...it's just a gradient layer that blends into the original !!!Dalek!!! graffiti art...but it matches my exact bg[NORMAL] color of my gtk-2.0 theme.

To learn more read this beginner "HowTo" I wrote, all of my new tricks are on page two (but read page one to learn about the gtkrc): [http://ubuntuforums.org/showthread.php?t=377397](http://ubuntuforums.org/showthread.php?t=377397)

...and ask your questions in there so I don't steal people's threads...and I'll help you with what I know in that "HowTo" thread.

---

### Post by zugu on 2007-06-15
Thunar and Mousepad are two amazing utilities. IMO, GNOME should replace Nautilus and Gedit with Thunar and Mousepad.

I don't like XFCE because I find its menus to be too KDE-like. The right-click menu is not contextual, it was almost the same wherever I clicked. Overall, I don't find GNOME more intuitive and streamlined than Xfce.

---

### Post by ThinkBuntu on 2007-06-15
> **zugu said:**
> Thunar and Mousepad are two amazing utilities. IMO, GNOME should replace Nautilus and Gedit with Thunar and Mousepad.

I don't like XFCE because I find its menus to be too KDE-like. The right-click menu is not contextual, it was almost the same wherever I clicked. Overall, I don't find GNOME more intuitive and streamlined than Xfce.
What on earth is amazing about Mousepad? It probably has fewer features than nano, and no plugins package I could find. In a pinch, GEdit is great for my code work, and it really isn't so heavy. The thing launches virtually instantly.

---

### Post by zugu on 2007-06-15
I find Mousepad faster and cleaner than Gedit, though Mousepad is actually based on Gedit code. I perceive Mousepad to be faster than Gedit, or at least this is how they behave on my machine.

I like to think about Mousepad as a Notepad replacement, something very basic that starts instantaneously and is able to display and edit plain text files. For slightly more complex tasks, I think AbiWord is excellent - though more complex than Windows' Wordpad, I like to put them in the same category. For heavy text editing and document management there's OpenOffice, of course.

---

### Post by Copter on 2007-07-19
Hi!

Some time ago I have switched from KDE to Xfce because I found KDE being too slow and from Edgy it really looks silly. I had to spend a lot of time on it to force it not to look as candy as Win XP.

Pros:
- it is faster than Gnome and KDE
- it can use Gnome's and KDE's plugins
- it looks better (not as candy as KDE)

Cons:
- it cant handle file associations properly. QT and GTK apps are using different apps for example for viewing mpeg files even after setting up 'open with...' multiple times  
- for me editing Xfce menu is less intuitive than quantum mechanics
- it wants to use gxine to open everything
- it misses lots of default icons for example 'about Xfce' in Xfce menu
- it messes up icons on desktop. Every time I login they are in different places
- it misses several Xfce-specyfic settings GUI apps

Damn, afer all I wrote I started to ask myself why am I still using Xfce... :)

copter :]

---

### Post by picpak on 2007-07-19
> **crimesaucer said:**
> Have you ever tried to write your own gtkrc for XFce and the xfce-engines?

I found it very easy to learn how to write for xfce, and I have been able to make it look many different ways. 

I've always wanted to learn how to make themes. Is it similar to making Opera themes? That's fairly easy.

Maybe I'm just disillusional, but I can't say I have many problems with Xfce. It's everything I want it to be: fast, easy, intuitive, and useful.

Now the menu is what needs a lot of work: outdated, hard to edit, etc. Other than that it'd be perfect.

---

### Post by dca on 2007-07-19
I see no reason to run anything other than KDE or Gnome on systems that can handle it.  The two DE(s) are fully customizable.  That being said, the benefits realized w/ XFCE, Fluxbox, etc is the ability to run GUI/DEs on out-dated or old equipment.  You get the benefits of both worlds that way, not that I'm telling anybody anything new.  Try installing WinXP on a Celeron 300 w/ 128MB RAM...

---

