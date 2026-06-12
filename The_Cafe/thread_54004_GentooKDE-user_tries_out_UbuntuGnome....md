---
title: "Gentoo/KDE-user tries out Ubuntu/Gnome..."
date: 2005-08-03
forum: The Cafe
---

### Post by Sushi on 2005-08-03
I have been using Gentoo for a while now. And I have been KDE-exclusive since 1.1 or something. But I recently had the itch to try out a distro that "just works", and according to the talk on the net, Ubuntu is it. I also wanted to try out something different than KDE, so I tried Gnome.

I have tested Gnome in the past. My last experiment was with 2.6 (IIRC) on gentoo, and I wasn't that impressed. But I decided to give it a shot and have an open mind with it. So, here are my experiences:

**Ubuntu**

Compared to Gentoo, installation was a breeze ;). Although Ubuntu doesn't have a graphical installation, it's still easy. The good thing with Gentoo is that if you can install Gentoo, then installation of any other Linux-distro can't be that difficult for you ;).

Ubuntu boots up faster than my Gentoo did. Of course, since you basically build your own Gentoo for you, it simply means that Ubuntu's boot-up procedure is faster than my Gentoo's boot-up procedure. I could make the Gentoo boot faster, but I never really got around to do it. But it's a nice thing that **Ubuntu** boots fast "out of the box".

I really loved the way Gentoo handled the services that are started during boot-up. removing and installing those services was a breeze. It seems to me that Ubuntu is not as slick in that department as Gentoo is. But that might be due to the fact that I'm used to the Gentoo-way of doing things, and I haven't yet gotten my head around the Ubuntu-way of doing it.

Installing software is very easy and very fast when compared to Gentoo (no compiling), Synaptic is a wonderful tool to use. There are front-ends to Portage as well, but I never used them, so I can't really do an Apples to Apples comaprison here.

**Gnome**

Like I said, I have used KDE for a long time, and my experiences with Gnome have been limited. Although I have kept my eye on their activities for a long time.

The two desktops load about as fast (on Ubuntu). Gnome might be faster by a second or two, but the difference is not big enough to really matter.

I REALLY like the look 'n feel of Gnome! I can't really point my finger at any specific thing that makes it look so good, but it does. I think it's the lack of excessive UI-elements that make it pleasure to look at. KDE has been getting better on this area all the time as well.

However, as nice as Gnome is to look at, I did run in to some problems. My Gentoo-installation was an AMD64-system, so I had some problems with some w32-codecs and the like. The machine is still the same, but my Ubuntu-installation is a regural x86-installation, so there shouldn't be any such problems. So I thought that multimedia shouldn't be a problem. I then proceeded to enable multimedia-playback in Firefox. I mean, it can't be difficult, right?

Well, it is. I searched the forums. There are lots and lots of instructions on how to make it work in Ubuntu/Gnome/Firefox. Each instructions more complex that the previous. And I couldn't make it work It tried to load the multimedia-content (in my case, trailers from apple.com) in Totem. But it never played back. It started to buffer, and then it stopped. And then Totem froze. After I had struggled with it for a while, I decided to try DVD-playback instead. And the app that handled that was Totem. Which promptly froze when it tried to play back the DVD.

Frustrated, I decided to try it with Kaffeine. I installed it, and it "just worked". No hassle, no nothing, my DVD's worked like they should. I then installed an app that makes Firefox play back multimedia-content in Kaffeine. After I had installed it, it just worked. Zero hassle.

I have used Gnome/Ubuntu for few days now, so my experiences are limited. I will post more impressions to this thread as time passes :). I can see why many people swear by Ubuntu/Gnome. And while I will propably keep Ubuntu, I'm not 100% sure about Gnome yet. It is a VERY good desktop, no doubt about it. But I might stick with KDE, we'll see.

EDIT: Mixed up Gentoo/Ubuntu when discussing bootup-speed.

---

### Post by TravisNewman on 2005-08-03
I'd say give it a week at least, to get used to things. Frequently, the anxiety of change can be misinterpreted as aversion.  Good post, very insightful, very honest.

But I urge you to keep up Gnome-ing for a few days more ;)

---

### Post by Sushi on 2005-08-03
[QUOTE=panickedthumb]I'd say give it a week at least, to get used to things. Frequently, the anxiety of change can be misinterpreted as aversion.  Good post, very insightful, very honest.

But I urge you to keep up Gnome-ing for a few days more ;)[/QUOTE]

I will keep on using Gnome for now. For starters: I really want to like it. And I do like the UI. But the poor handling of multimedia is a dark cloud in my sky right now.

Like I said: Ubuntu will propably stay, Gnome is still touch 'n go.

---

### Post by Kvark on 2005-08-03
[QUOTE=Sushi]I will keep on using Gnome for now. For starters: I really want to like it. And I do like the UI. But the poor handling of multimedia is a dark cloud in my sky right now.

Like I said: Ubuntu will propably stay, Gnome is still touch 'n go.[/QUOTE]
Make sure you have the package w32codecs. With the codecs most multimedia should work. Firefox plugins in general are still a pain though, for example flash is almost unusable because most text in flash movies is invisible.

Oh, and don't do Ctrl+A followed by Enter on your music collection. For me it opened a separate totem player for each song, all at once. :?

---

### Post by Sushi on 2005-08-03
[QUOTE=Kvark]Make sure you have the package w32codecs. With the codecs most multimedia should work.[/quote]

I do have them, and they "just work" in Kaffeine. But they do not work in Totem (which is used by Gnome by default). Same goes for DVD-playback.

> Firefox plugins in general are still a pain though, for example flash is almost unusable because most text in flash movies is invisible.

I haven't tried Flash yet. I managed to get it work even on my 64bit Gentoo-machine (it needed some Konqueror-hacking though), so it shouldn't be difficult on 32bit Ubuntu. I hope....

---

### Post by Knome_fan on 2005-08-03
[QUOTE=Sushi]I do have them, and they "just work" in Kaffeine. But they do not work in Totem (which is used by Gnome by default). Same goes for DVD-playback.
[/QUOTE]

Just install totem-xine.
Out of the box totem uses gstreamer as a backend, which at least in the version used in hoary can't use w32codecs. However, totem-xine uses xine as a backend (just as kaffeine does), so once you installed it you should be good to go.

---

### Post by Sushi on 2005-08-03
[QUOTE=Knome_fan]Just install totem-xine.
Out of the box totem uses gstreamer as a backend, which at least in the version used in hoary can't use w32codecs. However, totem-xine uses xine as a backend (just as kaffeine does), so once you installed it you should be good to go.[/QUOTE]

I'll give that a shot once I get back home. Thanks :)

---

### Post by poofyhairguy on 2005-08-03
Best Gnome Media Player:

Gxine

Gnome's Kaffine

---

### Post by Lowe on 2005-08-03
[QUOTE=poofyhairguy]Best Gnome Media Player:

Gxine

Gnome's Kaffine[/QUOTE]
 VLC all the way!

---

### Post by Sushi on 2005-08-04
I installed totem-xine and multimedia works in Gnome now. I also noticed that DMA was not enabled on my DVD-drive by default, and enabling it took some tweaking. But luckily the forums helped there :).

---

### Post by matthew on 2005-08-04
Nice post. I would love to see a follow-up of your thoughts and opinions after a week or so and another after a month...no pressure, though.

---

### Post by npaladin2000 on 2005-08-04
[QUOTE=Lowe]VLC all the way![/QUOTE]

Only when using the GNOME/GTK interface...looks ugly otherwise.  But the "G" interface looks REAL smooth and integrates well into Ubuntu.   

MPlayer is nice too when using something like the XFCE skin...too bad it doesn't support DVD menus.  Have to keep Xine around for that....and that's the ONLY reason I keep Xine around (That and Totem-Xine...and I prefer the Totem interface over Xine..ugh).

---

### Post by Sushi on 2005-08-05
Trouble in paradise.... Yesterday I got few weird errors in the system. Basically, X suddenly crashed and dropped be back to CLI. In the first time, I tried switching back to X, only to notice that it wasn't running. Then the entire machine froze. 30 minutes later, it crashed again in similar manner, but this time I manually restarted X, and I was soon back up & running.

I found those crashes distrurbing. I haven't made any changes to the system, and it has been rock-solid for me, apart from those two issues. Well, I DID change the order of drivers in /etc/modules, so I could get DMA working on my DVD-drive. But I don't think that could cause the problems. I wasn't using DVD at the time of the crash.

Firefox has crashed few times, but that's nothing major (although it shouldn't happen). Well, to be fair, on Gentoo I managed to hose Firefox so badly that it wouldn't run at all anymore ;).

Also, as I installed Ubuntu, it correctly detected W2K on another HD on that machine and added it to GRUB. But W2K wont start if I try to load it. However, this is still a bit better than with Gentoo, where I had to do the GRUB-configuration 100% by hand. I did manage to get W2K working in Gentoo, and I think I can do it in Ubuntu as well. Still, it would have been nice if it had "just worked".

Related to this: It would have been nice if Ubuntu had automatically detected the Windows-partitions, and added then to fstab. Gentoo didn't do that either, but maybe I just expect too much automation from Ubuntu ;).

---

### Post by tom-ubuntu on 2005-08-05
Welcome to Ubuntu! :)

I am not the only who switched from Gentoo to Ubuntu :) Didn't want to configure every single step on my own, it just have to work. This is exactly what Ubuntu does. Also installing (new) packages took way to long, even if portage is a very nice tool. Apt is great aswell and very fast. 

Have fun with your new distribution. And I hope you like gnome, it is a great desktop manager. But like everything else, it is a personal choice.

---

### Post by macgyver2 on 2005-08-05
[QUOTE=Sushi]I really loved the way Gentoo handled the services that are started during boot-up. removing and installing those services was a breeze. It seems to me that Ubuntu is not as slick in that department as Gentoo is. But that might be due to the fact that I'm used to the Gentoo-way of doing things, and I haven't yet gotten my head around the Ubuntu-way of doing it.[/QUOTE]
I noticed that also.  I really *really* liked all of those rc- tools in Gentoo! I suppose it was just a minor convenience...but a convenience nonetheless. Anyway, we could always try something like it for Ubuntu...

---

### Post by macgyver2 on 2005-08-05
[QUOTE=joeuser]I am not the only who switched from Gentoo to Ubuntu :) Didn't want to configure every single step on my own, it just have to work. This is exactly what Ubuntu does. Also installing (new) packages took way to long, even if portage is a very nice tool. Apt is great aswell and very fast.[/QUOTE]
Nope, I think a lot of people have already.  :) For me, it was that I like Ubuntu's philosophy...and yeah, for my notebook and desktop the constant emerges and hours (days) of compiling things was getting old. I figure if I really want to trim down a big piece of software I can just redo it myself. For most things, though, it doesn't really matter if an application includes support for whatever even if I don't use whatever. The only thing I'd possibly use Gentoo for now is if I start running a server again. But all that being said, Gentoo was a good teacher...

---

### Post by Mr. Electric Wizard on 2005-08-05
When you guys say **Xine**, do you mean **gxine**?
That's the only one I can find in the repository...
and yes, I have added the extra repositories.

I tried for about an hour to get DVD's to work, and the programs that did not work are:
Totem
MPlayer
Ogle
VLC (play disk)


Thinking about trying Kaffine, is this in the repository?

---

### Post by tom-ubuntu on 2005-08-05
[QUOTE=macgyver2]The only thing I'd possibly use Gentoo for now is if I start running a server again. [/QUOTE]
The "server" install option in Ubuntu is fine. Setuped already a server with it, is running fine.


[QUOTE=macgyver2]The only thing I'd possibly use Gentoo for now is if I start running a server again. But all that being said, Gentoo was a good teacher...[/QUOTE]
Agree 100%! I learned a lot with Gentoo, I wouldn't missed that, was a great learning experience.

---

### Post by Sushi on 2005-08-05
[QUOTE=Mr. Electric Wizard]Thinking about trying Kaffine, is this in the repository?[/QUOTE]

Yes it is, but it's a KDE-app.

---

### Post by Mr. Electric Wizard on 2005-08-05
So, your using KDE with Ubuntu (Kubuntu)?

---

### Post by Sushi on 2005-08-08
[QUOTE=Mr. Electric Wizard]So, your using KDE with Ubuntu (Kubuntu)?[/QUOTE]

I installed regural Ubuntu, and then added the kubuntu-desktop to it. I have both desktops installed.

---

### Post by SKLP on 2005-08-08
totem-gstreamer can use w32codecs thru gstreamer0.8-pitfdll in breezy FYI.
and totem's mozilla plugin is installed by default :)

---

### Post by Sushi on 2005-08-09
Yesterday I did something that was one of the reason I switched to Ubuntu: I got FreeNX up & running. Works like a charm! Gentoo did not have AMD64-packages for it.

---

### Post by Sushi on 2005-08-15
I have used more and more KDE recently. While Gnome is good, I prefer KDE-apps (mainly Kontact, K3b, Amarok and Konqueror) for my work. And if I use those, I might as well use KDE. And I noticed that KDE plays better with FreeNX than Gnome does.

---

