---
title: "Wayland should not be the default in 18.04."
date: 2017-12-06
forum: Ubuntu, Linux and OS Chat
---

### Post by cajuncoder on 2017-12-06
So, excited to try out wayland, I gave it a spin.

And, as long as I pointy-clicky-click on everything, and just run very simple programs, it works. But then, I became very frustrated and confused when I started trying to use keyboard shortcuts, or access my drop-down terminal, or run virtualbox, etc. etc. etc.

You see, ***[COLOR=#000000][SIZE=3]Wayland breaks a LOT of essential functionality[/SIZE][/COLOR]***[COLOR=#000000][SIZE=3][SIZE=2], and people are by and large ignoring this and still forcing it on the desktop.

So, what does wayland break, currently?

1) Keybindings. Even those built into gnome-shell by default, such as Ctrl+Alt+T
2) Drop-Down Terminals
3) Virtual Machines
4) Virtual Keyboards
5) Screen/Video Capturing tools
6) Lots and lots of accessibility tools and utilities such as Workrave, Easystroke, Speech Recognition, etc. etc.
7) Tons of wonderful utilities like xdotool, xrandr, etc. (to be expected, but still)
[/SIZE][/SIZE][/COLOR]
Basically, anything which captures or sends keystrokes or anything to do with the display manager whatsoever is utterly broken, at least in Wayland proper.
On Ubuntu 17.10, the situation is even weirder and very inconsistent: some of these features work some of the time, depending on whether or not the window you have in focus is what I will term "specially protected." IE: switch focus to certain programs, like Firefox, for example, and press Ctrl+Alt+T. A terminal will appear. Now, switch focus to your file browser, and press Ctrl+Alt+T. No terminal will appear, because your Nautilus is apparently a specially protected program that insists on owning all of your keystrokes.

***[SIZE=3]This is really bad / dysfunctional, and will frustrate new users who have no idea why basic functionality doesn't work, or worse yet, mysteriously works sometimes and not others.[/SIZE]***[SIZE=3][SIZE=2]

Worse yet, it will take years for developers to decide on protocols that allow Wayland to implement this functionality, and years more for all of those applications to be updated and make it into the repositories. The fact that even gnome's own keyboard shortcuts don't work tell me that we're in for a very long wait indeed. And all the while distros will be trying their hardest to force this dysfunctional display manager on us and deprecate X.

***[SIZE=3]Why this happens [/SIZE]***[SIZE=3]*[SIZE=2](and a small rant about "security")[/SIZE]*[/SIZE]
[/SIZE][/SIZE]
I'm not the most qualified to explain this, but the gist for those who don't know is this: This happens because Wayland is trying to be more "secure" than X. In X, any application can send or read keystrokes to/from any other application, allowing them to interact with one another. This is what allows all of the above programs, which don't simply operate in a blackbox, to work and integrate with the rest of your desktop. However, it can be a security concern because if you install a malicious program, it too could capture your keystrokes as you're typing in other windows. Wayland seeks to protect against that by confining each window to its own little black box. This, unfortunately, breaks a lot of important and basic stuff.

Anyway, that's mainly what people are talking about when they refer to X being insecure. And here's where my rant comes in.

X11 is not insecure. And, frankly, Wayland's conception of security is misguided and not worth, at least to myself and the vast majority of users, the damage it does.
Wayland is trying to protect against rogue keyloggers that might get installed on a user's system. Essentially, it's the equivalent of keeping all of the doors in your home locked at all times, and having only one key, which only one person has (despite there being, potentially, legitimate family members or guests in your house, who do not have the key and cannot currently be given copies). So, if by chance someone breaks into your house, they'll be confined to a single room.
Do I need to explain why this is foolish? Lock your front door, and secure access INTO your house. If untrusted users are downloading and installing untrusted programs on your system, it should be considered compromised from a security standpoint. There is no protocol that Wayland or anything else could implement that would protect you, nor should there be, as any such protocol that would provide sufficient protection would render the entire system far too locked down for legitimate users.

I value freedom and control over my computing experience, and I practice common sense safety. Wayland doesn't give me the first, currently, enforcing overly strict security measures that attempt to protect me from myself, and in the process breaks far too much core functionality to be of use for me. 

I don't think I'm alone in this regard, and making it the default is only going to confuse, annoy, restrict, and turn-off many users -- especially those who don't know what's going on or that they should switch to Xorg.

I'm sure that I've gotten a few details wrong and people will nit-pick and correct me (which they should! I want to learn/be corrected), but are my concerns, overall, not valid?

---

### Post by wildmanne39 on 2017-12-06
The last I read the decision to make wayland default had not been decided, has that changed and if so do you have a link?

---

### Post by cajuncoder on 2017-12-06
> **wildmanne39 said:**
> The last I read the decision to make wayland default had not been decided, has that changed and if so do you have a link?

[https://www.ubuntu.com/desktop/1710](https://www.ubuntu.com/desktop/1710)

"New Wayland
            The default display server is Wayland, but can also run x.org as a session or on systems that cannot support Wayland" 

It installs and selects Wayland by default, unless you have incompatible hardware (ie, Nvidia graphics cards)

---

### Post by Frogs Hair on 2017-12-06
The Gnome Shell runs on both Xorg and Wayland which is why both sessions are available on 17.10. This gives 17.10 users a chance to report bugs affecting both sessions.

---

### Post by vasa1 on 2017-12-06
> **cajuncoder said:**
> ...
I'm sure that I've gotten a few details wrong and people will nit-pick and correct me (which they should! I want to learn/be corrected), but are my concerns, overall, not valid?
Well, you can correct your initial post as you learn more :)

Also, a softer approach would be more likely to get folks to focus on the issue :)

For example, "Should Wayland be default in 18.04" would get less emotionally charged responses than "Wayland should NOT be default" ;)

Just to be clear, I think it would be useful to have a list of what works and what doesn't. Obviously, this list may evolve.

---

### Post by wildmanne39 on 2017-12-06
Yes I see now, I thought you were referring to using it in 18.04 LTS, it was supposed to replace xserver completely in 18.04 but I believe they have been rethinking the issue about having it the only graphical session in 18.04. I hope they leave xserver in as well as wayland.

I have been using wayland without issue in 17.10 but I do not try to do the things you listed in your post.

---

### Post by cajuncoder on 2017-12-06
> **vasa1 said:**
> Well, you can correct your initial post as you learn more :)

Absolutely! Will do.

> **vasa1 said:**
> 
Also, a softer approach would be more likely to get folks to focus on the issue :)

For example, "Should Wayland be default in 18.04" would get less emotionally charged responses than "Wayland should NOT be default" ;)

Just to be clear, I think it would be useful to have a list of what works and what doesn't. Obviously, this list may evolve.


That's very good advice, and a thoughtful response. Thanks :)

I think you're right. I feel very strongly about this, and so I guess my wording is a bit strong. I just feel like many developers / distros are too quick to throw the concerns of many users under the rug, especially when it comes to things like accessibility and compatibility/customizability.

You're right about maintaining a list, though. That could be quite useful, and we could even include work-arounds and alternatives. I think that would be best suited for another thread, though.

Edit: I'm hesitant to change my title or wording nonetheless, because I still feel that, from an objective point of view -- at least, if we are considering the user's experience, Wayland should not be the default. That said, I'm very open to discussing this and entertaining the possibility that I'm wrong. My intent is not to debate or incite combative discussion. I just earnestly feel that this design decision on the part of the Ubuntu team is a bit ridiculous and not well thought out, and want to make that sentiment clear along with supporting reason and logic.

---

### Post by Frogs Hair on 2017-12-06
> **cajuncoder said:**
> Absolutely! Will do.




That's very good advice, and a thoughtful response. Thanks :)

I think you're right. I feel very strongly about this, and so I guess my wording is a bit strong. I just feel like many developers / distros are too quick to throw the concerns of many users under the rug, especially when it comes to things like accessibility and compatibility/customizability.

You're right about maintaining a list, though. That could be quite useful, and we could even include work-arounds and alternatives. I think that would be best suited for another thread, though.


I think if you search a bit you'll find other distributions are having some of the same issues with Wayland. Ubuntu users involved in testing reported many bugs in the 17.10 cycle and that will be on going during the 18.04 development cycle.

---

### Post by mörgæs on 2017-12-07
Agree, Wayland should not be default. There should be a limit to how unfinished a product Canonical presents to its users. 

Lubuntu also made a major change in the 17.10 release by introducing LXQt. This was not made default, on the contrary the well-known and highly stable LXDE continued to be the main offering. 

LXQt was and is presented as a separate 'use-at-your-own-risk' ISO called Lubuntu Next. 

The results: The Lubuntu user feels that he is being taken seriously by receiving an honest warning about a work in progress. The Lubuntu developer does not have to deal with a flow of messages from surprised/disappointed users.

---

### Post by mastablasta on 2017-12-07
> **mörgæs said:**
> 
The results: The Lubuntu user feels that he is being taken seriously by receiving an honest warning about a work in progress. The Lubuntu developer does not have to deal with a flow of messages from surprised/disappointed users.

that makes more sense to me as well.  

if user get's frustrated with wayland they will just switch to X. who has time to report bugs? which is why on LTS X should be default and wayland optional. maybe on 18.10 wayland could be default. 
it all depends how well it is all done and how finished the product is.


additionally having many bug reports is one thing, solving them is another. the OP is right it may take a few years to erase the major bugs.

---

### Post by Frogs Hair on 2017-12-07
I'll be using Xorg on 18.04 and may switch to Budgie. I think generating a list of issues without officially reporting them does little good. Reporting bugs is the current method to give feedback to developers and affect the decision to include Wayland or not.

---

### Post by grahammechanical on 2017-12-07
We should not assume that Gnome.org has finished its implementation of Gnome Shell as a Wayland compositor. The Gnome developers admit that they have more work to do. This page seems to be up to date. It mentions Canonical's decision to switch to Gnome/Wayland.

[https://wiki.gnome.org/Initiatives/Wayland](https://wiki.gnome.org/Initiatives/Wayland)

Once the decision was made to switch to Gnome Shell it became sensible (in my opinion) to quickly begin the change over. A change to a different User Interface has to be made between LTS releases as any experimentation during the life cycle of an LTS version risks upsetting users who prefer LTS versions because of their stability.

The work being done as explained by a Ubuntu developer

[https://didrocks.fr/2017/08/14/ubuntu-gnome-shell-in-artful-day-1/](https://didrocks.fr/2017/08/14/ubuntu-gnome-shell-in-artful-day-1/)
[https://didrocks.fr/2017/08/15/ubuntu-gnome-shell-in-artful-day-2/](https://didrocks.fr/2017/08/15/ubuntu-gnome-shell-in-artful-day-2/)

[https://didrocks.fr/2017/09/20/ubuntu-gnome-shell-in-artful-day-13/](https://didrocks.fr/2017/09/20/ubuntu-gnome-shell-in-artful-day-13/)


Regards

---

### Post by mastablasta on 2017-12-08
heh... LTS material indeed:

> 
[LIST]
[*]Nvidia binary drivers do not work currently
[/LIST]


i still wish they went with KDE. it just seems a better option for desktop (especially since they practically abandoned the extra desktop work). sure gnome was there before, but that was a different gnome. if they had to stay with gnome (say because of know how) it would be better to lend assistance to cinnamon project.

---

### Post by uRock on 2017-12-08
I admit Wayland was enough to make me dump Debian Buster and ubuntu 17.10 on machines and go back to 16.04. There are still three more years to get Wayland squared away.

---

### Post by ulysses77 on 2017-12-08
I suppose part of it could be my hardware, but Wayland has been an absolute disaster so far on my machine. It'll be snappier in some respects, then just degrade into a complete and utter mess. I don't think Wayland is bad really, I just think it has a ways to go. I believe once Wayland has some more spit and polish it'll be suitable to replace Xorg.

---

### Post by sulobanks2 on 2017-12-24
I agree with cajuncoder. My few sessions with Wayland were frustrating because of the (already mentioned) stuff that didn't work. Between Wayland's issues and snappy forcefully adding folders and loop devices on my system, 17.10 definitely feels like a test release. If Wayland becomes the default in 18.04 (and a few other issues I see in 17.10), I may exhaust the entire support period for 16.04. I understand the desire to move to Wayland, but I'm getting tired of distros defaulting to unfinished software in stable releases (Every KDE release since 3, Unity, GNOME 3, etc). That's what we have unstable/testing releases for.

While Wayland (and snaps) will probably make the Linux desktop more attractive to new users, it's far from ready and should not be the default in an LTS.

---

### Post by rrnbtter on 2017-12-24
Greetings,
I'm using Gnome Wayland in Ubuntu 18.04 and through the entire 17.10 run.  I have zero problems and Win7 in virtual box is perfect. There were guest problems with Vbox for a while but it is fixed now, by Oracle of course. I wouldn't get to wound up until the LTS is released. The software dev build for the OS not the OS building for the Software.  It should all come together by release time. I was upset in the beginning of Wayland because I couldn't use Luckybackup in super user mode which was the only way to save a profile.  It is now working with Wayland Everything is perfect on my two machines both running Wayland and Gnome. I think it is the best OS I have ever used since MSDOS 2.9 on my Tandy 1000.

---

### Post by uRock on 2017-12-24
> **sulobanks2 said:**
> ...I may exhaust the entire support period for 16.04....

That's my plan. If I can't run GUIs as SU without doing workarounds, then I won't use it.

---

### Post by QIII on 2017-12-24
So long as the Wayland developers maintain their arrogant attitude about what users need to do and do not need to do as root, I'll not be using it.

---

### Post by uRock on 2017-12-25
> **QIII said:**
> So long as the Wayland developers maintain their arrogant attitude about what users need to do and do not need to do as root, I'll not be using it.

It's almost as if they forget this is Linux and the Admin user should be able to do whatever he/she wants to do at his/her own risk.

---

### Post by kansasnoob on 2017-12-25
> **sulobanks2 said:**
> I agree with cajuncoder. My few sessions with Wayland were frustrating because of the (already mentioned) stuff that didn't work. Between Wayland's issues and snappy forcefully adding folders and loop devices on my system, 17.10 definitely feels like a test release. If Wayland becomes the default in 18.04 (and a few other issues I see in 17.10), I may exhaust the entire support period for 16.04. I understand the desire to move to Wayland, but I'm getting tired of distros defaulting to unfinished software in stable releases (Every KDE release since 3, Unity, GNOME 3, etc). That's what we have unstable/testing releases for.

While Wayland (and snaps) will probably make the Linux desktop more attractive to new users, it's far from ready and should not be the default in an LTS.

About this:

> I may exhaust the entire support period for 16.04

I still have about 45 out of 60 machines running Trusty (14.04) and I'm undecided if I'll just upgrade to Xenial or wait for the first point release of Bionic. I have tested Xenial again on a variety of older hardware and the original kernel (version 4.4) seems to be fairly well sorted out, but I have twice had kernel updates break USB and flash card reader I/O. Both times that happened though it was sorted out quickly - so quickly I didn't need to file a bug report :)

I'm really torn at the moment about some of the UI changes in GNOME - little stuff like general appearance of various apps. The functionality is still there but things just look "clunky" to me, and I'm NOT just talking about Ubuntu's implementation of GNOME. I've honestly never been so uncertain about which way to go. I'm certainly considering waiting for 20.04, or maybe a different flavor?

There are a lot of really great options. Maybe I'll need a roll of the dice to make the decision :lolflag:

---

### Post by xmbwd on 2018-01-01
Can someone let me know what Wayland brings to the table in terms of usability?  

I find it a pain.  In addition to the aforementioned restrictions on what sudo can do (seriously, that is not Wayland's decision to make), I use Linux because I can make my workstream more efficient using window tiling and setting up "put windows" (in Gnome, CCSM in Unity) to open applications in specific locations (e.g., terminal - left upper quarter; gedit - maximized left; firefox - maximized right; mail - maximized full).  These settings save hours over the course of a year.

---

### Post by again? on 2018-01-02
> **xmbwd said:**
> Can someone let me know what Wayland brings to the table in terms of usability?  

I find it a pain.  In addition to the aforementioned restrictions on what sudo can do (seriously, that is not Wayland's decision to make), I use Linux because I can make my workstream more efficient using window tiling and setting up "put windows" (in Gnome, CCSM in Unity) to open applications in specific locations (e.g., terminal - left upper quarter; gedit - maximized left; firefox - maximized right; mail - maximized full).  These settings save hours over the course of a year.

[Why is Wayland better?]("https://askubuntu.com/a/11561") <---- link
Stick to 16.04 until tiling with wayland is further developed.
Ubuntu 16.04 still has more than three years of support left.
By the time of the next LTS release of Bionic, things should have improved.
```
**[COLOR="#006400"]glen@GU17:~$[/COLOR] distro-info --all --fullname --days=eol**
Ubuntu 4.10 "Warty Warthog" -4265
Ubuntu 5.04 "Hoary Hedgehog" -4081
Ubuntu 5.10 "Breezy Badger" -3917
Ubuntu 6.06 LTS "Dapper Drake" -3094
Ubuntu 6.10 "Edgy Eft" -3539
Ubuntu 7.04 "Feisty Fawn" -3362
Ubuntu 7.10 "Gutsy Gibbon" -3181
Ubuntu 8.04 LTS "Hardy Heron" -2427
Ubuntu 8.10 "Intrepid Ibex" -2804
Ubuntu 9.04 "Jaunty Jackalope" -2628
Ubuntu 9.10 "Karmic Koala" -2440
Ubuntu 10.04 LTS "Lucid Lynx" -1699
Ubuntu 10.10 "Maverick Meerkat" -2093
Ubuntu 11.04 "Natty Narwhal" -1892
Ubuntu 11.10 "Oneiric Ocelot" -1699
Ubuntu 12.04 LTS "Precise Pangolin" -251
Ubuntu 12.10 "Quantal Quetzal" -1327
Ubuntu 13.04 "Raring Ringtail" -1436
Ubuntu 13.10 "Saucy Salamander" -1265
Ubuntu 14.04 LTS "Trusty Tahr" 470
Ubuntu 14.10 "Utopic Unicorn" -894
Ubuntu 15.04 "Vivid Vervet" -710
Ubuntu 15.10 "Wily Werewolf" -529
[COLOR="#FF0000"]Ubuntu 16.04 LTS "Xenial Xerus" 1205[/COLOR]
Ubuntu 16.10 "Yakkety Yak" -166
Ubuntu 17.04 "Zesty Zapus" 23
Ubuntu 17.10 "Artful Aardvark" 198
Ubuntu 18.04 LTS "Bionic Beaver" 1940
```

---

### Post by monkeybrain20122 on 2018-01-03
> **guber2 said:**
> 
By the time of the next LTS release of Bionic, things should have improved.


I won't bet on  it and you did not answer any of the concerns raised by others. Wayland maybe better, *eventually*, but not now and very unlikely by April from a user's perspective. It just makes no sense to default to a half baked technology without feature parity in a LTS, which is supposed to be solid and ready for production.

---

### Post by again? on 2018-01-03
> **monkeybrain20122 said:**
> I won't bet on  it and you did not answer any of the concerns raised by others. Wayland maybe better, *eventually*, but not now and very unlikely by April from a user's perspective.
  
For those that understand the difference between wayland and xorg or need certain functionality, it shouldn't be too much of a stretch to use an xorg session.
Does it really matter if wayland is the default session?

---

### Post by uRock on 2018-01-03
> **guber2 said:**
> Does it really matter if wayland is the default session?

Yes. A user should not have to log out and change sessions. Ever.

---

### Post by QIII on 2018-01-03
IMO, yes it does matter.  The default should in any case be the one that is most likely to work.  Consider a new user who comes to Ubuntu.  Having no background or understanding of the Wayland/X situation, he has an issue and attempts to follow suggestions to correct it -- only to find that he can't do it.

Wayland is not ready for prime time and the poor attitude of the developers ensures that it will not be for the foreseeable future.  Until they face the reality that Wayland must support what the *user expects* and not their own arbitrary standard of what the user should or should not need to do, we would be trapped in a world where the user experience is just the way you'd better like it.

I know of another OS that operates that way...

I suggest that using Wayland as the default will turn out to be as regrettable as Mir/Unity was in the end.  Unfortunately, Canonical seems not to have learned from that experience.

Wayland is the future.  Wayland needs to be available.  Wayland needs to be tested and bugs reported.  But it is not suitable as a default -- particularly in a flagship LTS -- any more than a concept car is suitable for the showroom floor at a dealership.

---

### Post by QIII on 2018-01-03
> **uRock said:**
> Yes. A user should not have to log out and change sessions. Ever.

^This.

---

### Post by again? on 2018-01-03
If there are major issues with Wayland by the time of the Bionic release, I doubt it will be default anyway.

---

### Post by mastablasta on 2018-01-04
> **uRock said:**
> Yes. A user should not have to log out and change sessions. Ever.

if they can even enter a session....

---

### Post by virgosun on 2018-01-06
Totally [COLOR=#ff0000]AGREE.[/COLOR] I've tried 17.10 Wayland on my tablet, but it breaks TouchScreen features on Gnome 3. For example: caribou, terminal, etc[COLOR=#ff0000][/COLOR]

---

### Post by Perfect Storm on 2018-01-07
I can't even use wayland with my nvidia card. Nvidia need to written some new drivers for that.

---

### Post by mc4man on 2018-01-07
> **Artificial Intelligence said:**
> I can't even use wayland with my nvidia card. Nvidia need to written some new drivers for that.if you have a non hybrid (Optimus) gpu then you *should* be able to get a wayland session with recent  Nvidia drivers. Nvidia kms needs to be enabled in same fashion that hybrid gpu users would do to get prime sync under X

---

### Post by sonicwind on 2018-01-26
[h=2][SIZE=2]Ubuntu 18.04 LTS is Switching back to Xorg[/SIZE][/h][http://www.omgubuntu.co.uk/2018/01/xorg-will-default-display-server-ubuntu-18-04-lts](http://www.omgubuntu.co.uk/2018/01/xorg-will-default-display-server-ubuntu-18-04-lts)

---

### Post by cruzer001 on 2018-01-26
> **sonicwind said:**
> [h=2][SIZE=2]Ubuntu 18.04 LTS is Switching back to Xorg[/SIZE][/h][http://www.omgubuntu.co.uk/2018/01/xorg-will-default-display-server-ubuntu-18-04-lts](http://www.omgubuntu.co.uk/2018/01/xorg-will-default-display-server-ubuntu-18-04-lts)

Nice, I can live with xorg for 2/4 more years :)

---

### Post by PaulW2U on 2018-01-27
> **sonicwind said:**
> [h=2][SIZE=2]Ubuntu 18.04 LTS is Switching back to Xorg[/SIZE][/h][http://www.omgubuntu.co.uk/2018/01/xorg-will-default-display-server-ubuntu-18-04-lts](http://www.omgubuntu.co.uk/2018/01/xorg-will-default-display-server-ubuntu-18-04-lts)

> **cruzer001 said:**
> Nice, I can live with xorg for 2/4 more years :)
Agreed.

I recently installed the development version of Ubuntu 18.04 and opened LibreOffice. Bug [https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1729433](https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1729433) was immediately apparent. If a major application such as LibreOffice doesn't work as intended then Wayland is not yet ready for being the default on the next Ubuntu release which will of course be an LTS and supported for **five** years.

May be the default for Ubuntu 20.04 in two years time?

---

### Post by The Cog on 2018-01-27
> **PaulW2U said:**
> May be the default for Ubuntu 20.04 in two years time?

But why???? I looked at post#1 and I use nearly all the broken features in that list. Why are they wasting their time with this? Just because it's a new idea, a chocolate teapot is not necessarily better than a conventional old-fashioned china one.

---

### Post by yetimon_64 on 2018-01-28
> **sonicwind said:**
> **[SIZE=2]Ubuntu 18.04 LTS is Switching back to Xorg[/SIZE]**

<snipped link>

That is good news here. =d>

> **The Cog said:**
> ... I looked at post#1 and I use nearly all the broken features in that list...

Same here regarding the features listed in the first post. I know that both xorg and wayland were to be available, but agree that leaving xorg as default is a much easier idea to deal with for my setting up on new installs of 18.04. This news is especially good for new starters who may have been caught out having to change session types on a first install.

---

### Post by titan.rose on 2018-01-29
> **sonicwind said:**
> **[SIZE=2]Ubuntu 18.04 LTS is Switching back to Xorg[/SIZE]**

[http://www.omgubuntu.co.uk/2018/01/xorg-will-default-display-server-ubuntu-18-04-lts](http://www.omgubuntu.co.uk/2018/01/xorg-will-default-display-server-ubuntu-18-04-lts)

That's good news. I was having problems with my touchscreen in my initial tests with wayland, so I welcome this decision. I have no problem with Wayland when it gets more mature though.


----

Sysadmin and Ubuntu fan

---

### Post by orange47 on 2018-07-31
guess you never had pleasure of dealing with 'TeamViewer10' rootkit.
I, for one, think wayland should be *mandatory*.

---

### Post by QIII on 2018-07-31
Perhaps when Wayland is ready for prime time ... and when the Wayland developers have decided that the "things users don't need to do" are not theirs to decide.

---

### Post by rrnbtter on 2018-08-01
Greetings,

Distributor ID:	Ubuntu
Description:	Ubuntu Cosmic Cuttlefish (development branch)
Release:	18.10
Codename:	cosmic
inxi -Sxx
System:
  Host: rrnbtter-Lenovo-ideapad-320-15IAP Kernel: 4.17.0-6-generic x86_64 
  bits: 64 compiler: gcc v: 8.1.0 Desktop: Gnome 3.28.3 wm: gnome-shell 
  dm: gdm3 Distro: Ubuntu 18.10 (Cosmic Cuttlefish) 
$DESKTOP_SESSION
ubuntu-wayland
$XDG_SESSION_TYPE
wayland
GNOME Shell 3.28.3
Version: 3.28.3-0ubuntu2
loginctl type
Type=wayland

Using Ubuntu 18.10 Gnome/Wayland and loving it every day. Nothing but the very best.  People will always get what they "think they want and need" when they write their own software.  The rest settle for what they get.  If you want to know the answer to anything, follow the money trail.

---

### Post by coffeefiend on 2018-08-01
Sorry, I'm a Cybersecurity guy by trade (more manager than technician at that) so all of this tech talk is making my head spin. I have read a few things previously about Wayland, but still don't really have a good grasp of what it is/does. Can someone break it down into simple terms for me? Feel free to explain it like you would to a three year old, because that is about the level of my understanding right now. Lol

---

### Post by DuckHook on 2018-08-01
> **coffeefiend said:**
> Sorry, I'm a Cybersecurity guy by trade (more manager than technician at that) so all of this tech talk is making my head spin. I have read a few things previously about Wayland, but still don't really have a good grasp of what it is/does. Can someone break it down into simple terms for me? Feel free to explain it like you would to a three year old, because that is about the level of my understanding right now. LolI'm sure as a cybersecurity guy, you are far more knowledgeable than you let on. ;)

I'm the furthest thing from a security guru myself, but FWIW I can try summarizing my limited knowledge of the matter in a couple of paragraphs. What follows is certain to contain errors and omissions; I'm happy to learn from my betters, so gurus should feel free to correct me:

X is, by now, ancient technology that suffers from a lot of the loosey goosey tech design that was common in its day and considered okay at the time, but which today, has definitely proven to be lax and insecure. For one thing, it is unsandboxed such that it is child's play for any GUI app to gain access to both restricted system and user memory space. Wayland OTOH is properly sandboxed so that it is far harder for a rogue app to penetrate restricted memory. X is also monolithic. If it is destabilized by, say, a bad app, it can blow up your entire GUI session as the app goes down. Wayland is more robust and there's an excellent chance that a misbehaving app will be contained and won't damage your other apps much less take down the entire GUI environment.

So, on paper, Wayland is the superior GUI subsystem. However, as QIII and others have pointed out, its devs have taken a very high-handed approach to dictating what is and is not allowed. Many old ways of doing things are broken for what feels like no good reason—just a unilateral decision on the part of the devs that things won't be allowed. Since the power of Linux (at least to power users) is its flexibility and freedom to do anything (as root), such restrictions are not only constraining, but seem to offend the very spirit of what many users like about Linux.

The details are more complicated than what I've just so simplistically described, but I hope this helps.

---

### Post by coffeefiend on 2018-08-01
Oh trust me, I do not jest when I say I really don't understand exactly what it is. All I know is it has something to do with graphics rendering, but it seems like there is more to it than just that. The network I manage is Windows Server 2003 with XP desktops. Yeah, ancient technology (Go Navy!). I won't know what it is like to manage a real network until I retire next year.

---

### Post by QIII on 2018-08-01
[Wayland]("https://wayland.freedesktop.org/") and X are display servers.

Arch has perhaps a more understandable description [here]("https://wiki.archlinux.org/index.php/wayland"), with a couple of links to definitions.

---

### Post by coffeefiend on 2018-08-02
Thanks for the link! That is much easier to read than the Wiki page. Tiny pockets of understanding are starting to form in my over-worked and under caffeinated brain.

---

### Post by twily2018 on 2018-08-04
Wacom tablets also don't work so good on wayland. The tablet pen shows up as a second cursor which I read that it's done by design but sometimes the tablet cursor become invisible and that's with Xorg 1.20 where it was supposed to be fixed. Anything below Xorg 1.20 the tablet just didn't work at all in any application for me.

---

### Post by exploder on 2018-08-04
I use the wayland session in Ubuntu 18.04 and it works perfect with my hardware. I did have to make a start up entry so Synaptic work work but other than that I really like it.

---

### Post by mc4man on 2018-08-10
By all rights Ubuntu shouldn't default to wayland until the severity of gnome-shell crashes in wayland  is mitigated by some means to get like with Xorg, i.e not a Desktop crash.
Till then it would be irresponsible to do so.

---

### Post by uRock on 2018-08-11
Wayland was the gift that made it even easier for me to make the change Kubuntu, because I also can't stand Gnome.

---

