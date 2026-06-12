---
title: "Hotcorner is back, and with more problems"
date: 2017-09-04
forum: Ubuntu Development Version
---

### Post by Chanath on 2017-09-04
Hotcorner is back, and with more problems. When there are ~ 89 extensions around and more coming, you'd need an army of devs to keep blocking them. The hotcorner is the normal Gnome shell hotcorner.
None of the other distros with Gnome shell ever made system extensions. The gnome shell extensions are free to install from a web browser or from github.

---

### Post by Chanath on 2017-09-04
Added another extension. Do you see the added icons on the top panel?

---

### Post by ventrical on 2017-09-04
You have to remove dash 2 dock first.

---

### Post by Chanath on 2017-09-04
> **ventrical said:**
> You have to remove dash 2 dock first.

Which Dash to Dock? 
It is not installed at all.
What you see is the normal Gnome Dash and the Ubuntu Dock (system extension) And another extension that put favourites on the panel.
The hotcorner is blocked by the system extension, but can be overruled. And, when overruled, it becomes a bug. And, the users are going to shout.

---

### Post by ventrical on 2017-09-04
> **Chanath said:**
> Which Dash to Dock? 
It is not installed at all.
What you see is the normal Gnome Dash and the Ubuntu Dock (system extension) And another extension that put favourites on the panel.

Did you install that extension? Why?

---

### Post by Chanath on 2017-09-04
> **ventrical said:**
> Did you install that extension? Why?

I'm testing installation of extensions I like. 
That's what the majority of the users do. Ever heard anyone using the default?

---

### Post by ventrical on 2017-09-04
> **Chanath said:**
> I'm testing installation of extensions I like. 
That's what the majority of the users do. Ever heard anyone using the default?

Yeah , me.  But I can expect breakage if I install extensions at this stage. It will clear up or they will be removed. Try removing, see if you can restore.

---

### Post by ventrical on 2017-09-04
> **Chanath said:**
> I'm testing installation of extensions I like. 
That's what the majority of the users do. Ever heard anyone using the default?

Your not alone..

[http://www.zdnet.com/article/linus-torvalds-finds-gnome-3-4-to-be-a-total-user-experience-design-failure/](http://www.zdnet.com/article/linus-torvalds-finds-gnome-3-4-to-be-a-total-user-experience-design-failure/)

---

### Post by Frogs Hair on 2017-09-04
This may have what broke ubuntu dock and dash to dock . The old hot corner works fine and so does dash to panel.

---

### Post by Chanath on 2017-09-05
> **Frogs Hair said:**
> This may have what broke ubuntu dock and dash to dock . The old hot corner works fine and so does dash to panel.

There are no system extensions in any distro that use gnome shell as its main DE. There are ~ 845 extensions around and more to come. Some work, some don't. We don't have any idea what is the next new extension would be. Unity Tweak might have found a way to autohide the Unity top panel, but Unity Tweak was taken into the fold, and the autohiding feature never came to Unity top panel. Gnome tweak cannot be taken into the fold, nor the web based Gnome shell extensions. Right now, Firefox issued with Ubuntu is 50 and it is not compatible with gnome shell extensions addon. You have to install chrome-gnome-shell to get it working, but that's not (freely) available in Software app. Keeping Gnome Tweak away won't help either, as we've used gnome shell before and we know its there. Disabling universe by default won't help either.

@ ventrical,
Thanks for the link. He's right, keyboard is for writing, and mousing for other operations.

---

### Post by ventrical on 2017-09-05
> **Chanath said:**
> There are no system extensions in any distro that use gnome shell as its main DE. There are ~ 845 extensions around and more to come. Some work, some don't. We don't have any idea what is the next new extension would be. Unity Tweak might have found a way to autohide the Unity top panel, but Unity Tweak was taken into the fold, and the autohiding feature never came to Unity top panel. Gnome tweak cannot be taken into the fold, nor the web based Gnome shell extensions. Right now, Firefox issued with Ubuntu is 50 and it is not compatible with gnome shell extensions addon. You have to install chrome-gnome-shell to get it working, but that's not (freely) available in Software app. Keeping Gnome Tweak away won't help either, as we've used gnome shell before and we know its there. Disabling universe by default won't help either.

@ ventrical,
Thanks for the link. He's right, keyboard is for writing, and mousing for other operations.

If I may, it is just my suggestion throughout the rest of this cycle that we try to work gnome-shell in a dry run mode - meaning try to use as least extensions as possible. (there will be plenty of opportunity to test extensions come the next cycle). If you continue to experiment with extensions then please make a list in this fashion:

```

sudo apt-get install <extension-name>

```

because I for one do not understand what extensions you are using (as may others also).

So please use the code tags so that I can understand better what you are trying to convey. I would appreciate that.

Thanks,
Regards..

---

### Post by vasa1 on 2017-09-05
> **ventrical said:**
> Your not alone..

[http://www.zdnet.com/article/linus-torvalds-finds-gnome-3-4-to-be-a-total-user-experience-design-failure/](http://www.zdnet.com/article/linus-torvalds-finds-gnome-3-4-to-be-a-total-user-experience-design-failure/)

That's from 2012 :(

---

### Post by ventrical on 2017-09-05
> **vasa1 said:**
> That's from 2012 :(

:) Yeah .. I know . uhh  I was just trying to balance the scales so to speak ;)
Gnome much better now.

Regards..

---

### Post by Chanath on 2017-09-05
> **ventrical said:**
> If I may, it is just my suggestion throughout the rest of this cycle that we try to work gnome-shell in a dry run mode - meaning try to use as least extensions as possible. 

because I for one do not understand what extensions you are using (as may others also).

So please use the code tags so that I can understand better what you are trying to convey. I would appreciate that.

Thanks,
Regards..

Greetings!

I am using Unity now (work time), so any testing of Gnome-shell in default Ubuntu will be later in the evening. You can find extensions here; [https://extensions.gnome.org](https://extensions.gnome.org) 
Some work, some won't. 846 at the moment.

You just enable gnome-shell-extensions in your browser. If you are using the default Firefox 50, you have to install gnome-chrome-shell from the repos. 

These are the ones I tried; [https://extensions.gnome.org/extension/545/hide-top-bar/](https://extensions.gnome.org/extension/545/hide-top-bar/) (this is amust for most of us),[https://extensions.gnome.org/extension/1160/dash-to-panel/](https://extensions.gnome.org/extension/1160/dash-to-panel/) (to check whether it would move Ubuntu dock away. It didn't as it did with Dash to Dock in the past.). Can't remember the other one. 

Most of the extensions have their own settings, which can override other settings, so its a free-for-all like WWA.

---

### Post by ventrical on 2017-09-05
> **Chanath said:**
> Greetings!

I am using Unity now (work time), so any testing of Gnome-shell in default Ubuntu will be later in the evening. You can find extensions here; [https://extensions.gnome.org](https://extensions.gnome.org) 
Some work, some won't. 846 at the moment.

You just enable gnome-shell-extensions in your browser. If you are using the default Firefox 50, you have to install gnome-chrome-shell from the repos. 

These are the ones I tried; [https://extensions.gnome.org/extension/545/hide-top-bar/](https://extensions.gnome.org/extension/545/hide-top-bar/) (this is amust for most of us),[https://extensions.gnome.org/extension/1160/dash-to-panel/](https://extensions.gnome.org/extension/1160/dash-to-panel/) (to check whether it would move Ubuntu dock away. It didn't as it did with Dash to Dock in the past.). Can't remember the other one. 

Most of the extensions have their own settings, which can override other settings, so its a free-for-all like WWA.

Ahhh .. I see .. so these are off-repository extensions or is it safe to assume that they have gone through rigorous testing to be included in the ubuntu main repos?

Anyone can answer this please.
edit: gnome-chrome-shell in repos, ok

Thanks

---

### Post by mc4man on 2017-09-05
> **Chanath said:**
> Hotcorner is back...
What is that supposed to mean? It's certainly not default enabled.

---

### Post by Chanath on 2017-09-05
> **mc4man said:**
> What is that supposed to mean? It's certainly not default enabled.

The default enabling doesn't work, when freely available extensions are installed. There is no way to stop users from installing extensions, is there? It'll be practically impossible to keep guard over all those extensions, and over those not yet arrived.

---

### Post by ventrical on 2017-09-05
> **Chanath said:**
> The default enabling doesn't work, when freely available extensions are installed. 

From the repos? can you give us some examples?

Regards..

---

### Post by Chanath on 2017-09-05
> **ventrical said:**
> From the repos? can you give us some examples?

Regards..

A Gnome shell user installs extensions from here, [https://extensions.gnome.org](https://extensions.gnome.org)

---

### Post by ventrical on 2017-09-05
> **Chanath said:**
> A Gnome shell user installs extensions from here, [https://extensions.gnome.org](https://extensions.gnome.org)

Yes.. thats what I thought . Explains volumes. Thank-you.

Regards..

---

### Post by amano on 2017-09-05
I simply don't get the topic title: 

Hot Corner is back? Nope, fortunately not.

You want it back? That's another thing.

What about filing a bug?


Or is this all a joke? The Openbox user that switches to Unity when that gets ditched by Canonical.

---

### Post by Chanath on 2017-09-05
> **amano said:**
> .

Maybe this is a joke?

---

### Post by fthx on 2017-09-05
What's the point here ?
You have proven that Dash to Panel interfere with Ubuntu Dock (that you cannot easily remove). So if you want to remove UD, delete /usr/share/gnome-shell/extensions UD folder and if you want it working, disable DtP.

---

### Post by Chanath on 2017-09-05
> **fthx said:**
> What's the point here ?
You have proven that Dash to Panel interfere with Ubuntu Dock (that you cannot easily remove). So if you want to remove UD, delete /usr/share/gnome-shell/extensions UD folder and if you want it working, disable DtP.

I am not proving anything. 17.10 is a development issue, and not yet really released. Still time for it to come through. Even, if 17.10 is the trying out release, before 18.04 LTS, all kinds of "unfinished" work would be pointed out to say Ubuntu had failed. So, there is still time to test the development issue, after all this is all about the development daily releases. You also can do some testing, if you care.

There had not been any system extensions in other Gnome shell based distros. As always, Ubuntu is trying out something new. Its a good thing they do. Unity came out because of that Ubuntu attitude. Some people hate Unity, but I don't. I don't hate anything, for I don't know how to hate. 

Gnome shell is all about freedom; to create extensions and to use extensions. And, also to modify extensions. If you block extensions, you are looking for lot of criticism. Gnome shell had been out there so long, its very well known.

---

### Post by ventrical on 2017-09-05
Feature freeze and Debian import freeze already taken place with user interface freeze not far away.

 If we wait prior to the release candidate we will most likely see a lot of fixes down the pipe.

As fthx has pointed out .. we will probably have to use workarounds with  off-repo gnome-extensions.

[https://wiki.ubuntu.com/ArtfulAardvark/ReleaseSchedule](https://wiki.ubuntu.com/ArtfulAardvark/ReleaseSchedule)

Regards..

---

### Post by mc4man on 2017-09-05
> **Chanath said:**
> The default enabling doesn't work, when freely available extensions are installed. There is no way to stop users from installing extensions, is there? It'll be practically impossible to keep guard over all those extensions, and over those not yet arrived.
At the risk risk of enlarging this rabbit hole, in a Ubuntu install there is no default enabling of hot corner so the actual enabled default  does work quite well. 
As far as the rest of this threads mumbo jumbo, so what.. If users install incompatible extensions then it's on them to square away or ask somewhere about such.

---

### Post by Frogs Hair on 2017-09-05
I installed dash-to-dock from synaptic and narrowed the problem down to breakage after gnome-shell updates due to incompatibility of the extension and yes , I own that one. :)

---

### Post by mc4man on 2017-09-05
I don't view this as any much different than compiz & it's plugins. Ubuntu will support elements of and likely do a very good job of it.
As far as 3rd party ext.'s users are on their own though there's no reason to think there won't be decent community based support happening.

---

### Post by vasa1 on 2017-09-05
> **Chanath said:**
> ...
Gnome shell is all about freedom ...
:?:

---

### Post by ventrical on 2017-09-06
> **mc4man said:**
> 
As far as 3rd party ext.'s users are on their own though there's no reason to think there won't be decent community based support happening.

No doubt. Its been a long summer. Just my view that we got to let the community devs come up for air on this one, ya know .. and then there's  wayland..

Regards..

---

### Post by Chanath on 2017-09-06
> **mc4man said:**
>  If users install incompatible extensions then it's on them to square away or ask somewhere about such.

The thing is, extensions were there long before Ubuntu decided to go with Gnome-shell. These extensions are not incompatible with Gnome-shell. [https://extensions.gnome.org/](https://extensions.gnome.org/) is from The Gnome Project. So, every Gnome user is encouraged to create them, use them etc. What might be incompatible with Gnome-shell would be the system extensions. For example, if you use the Hide Top Bar extension--many users need the the whole screen area--everything goes haywire. *That is with just one extension.* You just cannot prohibit the former Ubuntu-Gnome users from using extensions, just because its now the default, can you? You can't ask/demand that from the new users, ones who might move from Unity to Gnome-shell, can you?

EDIT: Hotcorners can be activated without *any* extension. The screeny won't show, where the cursor is. Its at the bottom right corner. You'd notice that the Ubuntu Dock hadn't gone under the top panel, as its not autohidden. (If Hide Top Bar is used, it go under.)

---

### Post by fthx on 2017-09-06
If you're unhappy with Ubuntu's two default extensions (Dock, Indicators) :
1) only few GS extensions will not be running fine (DtP, and I can suppose TopIcons and so on)
2) you can go for gnome-session instead of ubuntu-session and get an vanilla GS

I really do not see what is bad here.

---

### Post by ventrical on 2017-09-06
> **fthx said:**
> If you're unhappy with Ubuntu's two default extensions (Dock, Indicators) :
1) only few GS extensions will not be running fine (DtP, and I can suppose TopIcons and so on)
2) you can go for gnome-session instead of ubuntu-session and get an vanilla GS

I really do not see what is bad here.

The desktop team is working on new theming. After all, it is ubuntu-desktop and it will not be an exact clone of  other gnome-shell DEs on other distros. There is nothing bad here. We are seeing the incorporation of some really awesome ideas that went into building unity in this current cycle being used in the gnome-shell experience.  At least this is how I understand it from the information I have. There are always interim  cycles that will have some breakage and bugs on release day.  This has been the case for ubuntu , especially in off repository installations.

regards..

---

### Post by Chanath on 2017-09-06
> **fthx said:**
> If you're unhappy with Ubuntu's two default extensions...

Unhappy, happy has no meaning here; its called testing the development release.:)

---

### Post by ventrical on 2017-09-06
There are some clarifications:

The developers added desktop code for ubuntu-dock to vanish when people add dash to dock for instance.

quoting Didier,

> 
Our extensions are enabled as a  GNOME Shell mode. This is exactly the same technic than GNOME Classic.  GNOME Shell doesn't have any mechanism to disable the extensions set as  part of the mode.

> 
Of course, if people want to add  another dock or top icon plus, this is a duplication with those  extensions. I don't think they should then be using that session (note:  you have the exact same issue with gnome classic if you enable another  alt-tab extension for instance or any extension overriding the same functionality than one  enabled by GNOME Classic) but rather the "GNOME vanilla" one easily  available via apt install gnome-session and change session in GDM.
 

Regards..

---

### Post by Chanath on 2017-09-06
@ ventrical

I hope Didier (and others) would get around the problems, before the official release. To make the release look like Unity, they had to block the only hotcorner available in Gnome shell. I got around that by using an old script, which was here before Gnome shell times. The screeny in post #31. All four corners can be made "hot."

Actually, trying to make Gnome-shell look like Unity is bit strange. I think its a failing effort. They should've tried something else, like the Deepin devs, or Budgie, something special Ubuntu. I am getting bit bored with Unity, as it is not planning to break. Ubuntu default is giving some excitement, like in the old days.

---

### Post by ventrical on 2017-09-06
> **Chanath said:**
> @ ventrical

I hope Didier (and others) would get around the problems, before the official release. To make the release look like Unity, they had to block the only hotcorner available in Gnome shell. I got around that by using an old script, which was here before Gnome shell times. The screeny in post #31. All four corners can be made "hot."

Actually, trying to make Gnome-shell look like Unity is bit strange. I think its a failing effort. They should've tried something else, like the Deepin devs, or Budgie, something special Ubuntu. I am getting bit bored with Unity, as it is not planning to break. Ubuntu default is giving some excitement, like in the old days.

Here is how Didier puts it:

> 
Yeah, there is no limitation in  term of extensions. Of course, some transitions time can have broke your  installation. But nothing is going to prevent people installing from  extension.gnome.org.
 
 Of course, some extensions are "naturally" unmaintained/broken. But  that's the life of installing things off-repo. However, there should be  no difference than on any other GNOME Shell installations.
 The only thing is what I told: in the ubuntu session, you will have  those 2 extensions enabled (ubuntu dock and ubuntu indicator) that can't  be removed due to how extensions part of a mode is coded under GNOME  Shell (same issue when being in GNOME Classic). I made caution that people can still install dash to dock if they want  to get access to more settings. However, I think it's fair to say "the  ubuntu session is that dock and those indicator supports".
 
 If people want to install another dock, or top icon plus (which are the  only extensions I can think of that can "conflict" in term of  duplicating functionalities, but not breaking code), the GNOME Vanilla  session is for that.
 
 /!\ each new GNOME version has an history of breaking extensions (for  exemple, GNOME Shell 25.90.1 broke dash to dock which needed fixes for  instance). It's getting less frequent though.
 
 Cheers,
 Didier



Regards..

---

### Post by Chanath on 2017-09-06
What is shown in [https://ubuntuforums.org/showthread.php?t=2370670/#2](https://ubuntuforums.org/showthread.php?t=2370670/#2) doesn't happen in Debian Gnome, where Debian doesn't have system extensions. I'm sure this doesn't happen in Arch Gnome too. 

There is no Dash to Dock installed, but was installed and uninstalled. Something inside Ubuntu made it stay.

---

### Post by ventrical on 2017-09-06
> **Chanath said:**
> What is shown in [https://ubuntuforums.org/showthread.php?t=2370670/#2](https://ubuntuforums.org/showthread.php?t=2370670/#2) doesn't happen in Debian Gnome, where Debian doesn't have system extensions. I'm sure this doesn't happen in Arch Gnome too. 

There is no Dash to Dock installed, but was installed and uninstalled. Something inside Ubuntu made it stay.

Perhaps try the gnome vanilla session and see what happens.

ubuntu-session is uniquely an ubuntu-session.  Thats what I am gathering.  For all intents and purposes it is gnome3 but with caveats, otherwise it would not be ubuntu. Feature freeze is laid in stone unless some other decision is made. Personally I think we have a good rolling gnome(ubunt-session/desktop) to work with come the next toolchain.  I am encouraged to stay the course on testing gnome-shell and gnome-shell with wayland  to the end of the 18.04 cycle  and encourage others to test the same if they will.   I also personally affirm the desktop teams current direction. I think it is the right path. If unity7 rolls along with us it will be a double blessing.

apologies for off topic ;)

Regards..

---

### Post by Chanath on 2017-09-06
I am checking few things with Gnome shell on Arch Linux. Back in a few.

EDIT: Wanted to see how Dash to Dock, Dash to Panel and Hide Top Bar works in Arch. When you install both dash extensions, both are showing, and when you disable Dash to Dock only Dash to Panel is showing. And, vice versa. Just disable, not uninstall.

In default Ubuntu, even *after *uninstalling Dash to Dock, it was still there and together with Dash to Panel. Screeny #31 
Ubuntu Dock was uninstalled, but something was holding Dash to Dock back. 

I wanted to check that in Arch.

---

### Post by ventrical on 2017-09-06
> **Chanath said:**
> I am checking few things with Gnome shell on Arch Linux. Back in a few.

EDIT: Wanted to see how Dash to Dock, Dash to Panel and Hide Top Bar works in Arch. When you install both dash extensions, both are showing, and when you disable Dash to Dock only Dash to Panel is showing. And, vice versa. Just disable, not uninstall.

In default Ubuntu, even *after *uninstalling Dash to Dock, it was still there and together with Dash to Panel. Screeny #31 
Ubuntu Dock was uninstalled, but something was holding Dash to Dock back. 

I wanted to check that in Arch.

As the same here .. and so as Didier advised us that it will break .. but not in vanilla gnome?

---

### Post by Chanath on 2017-09-06
> **ventrical said:**
> As the same here .. and so as Didier advised us that it will break .. but not in vanilla gnome?

I read his blog. His advice is not taken, as its pretty normal thing any Gnome shell user does - play with extensions.
Advice to him is, make such a default Ubuntu, so people would not bad mouth Ubuntu.

---

### Post by ventrical on 2017-09-06
> **Chanath said:**
> I read his blog. His advice is not taken, as its pretty normal thing any Gnome shell user does - play with extensions.
Advice to him is, make such a default Ubuntu, so people would not bad mouth Ubuntu.

@ Chanath,

 Your remarks are a little beyond the pale and not topical to U+1. Perhaps maybe Linux OS & Chat?

Regards..

---

### Post by Chanath on 2017-09-06
> **ventrical said:**
> @ Chanath,

 Your remarks are a little beyond the pale and not topical to U+1. Perhaps maybe Linux OS & Chat?

Regards..

Yes, sorry about that. Couldn't stop myself. I am with Arch for while. Thought I'd just only test those extensions in it, but simply liked what I get in Arch. There are no defaults at all. No need to install anything other than what I need. 

I'm going back to using Unity, until it'd live on. The next download of Ubuntu default will be when it'd be officially released. Extensions will be tried on then.

---

### Post by ventrical on 2017-09-06
> **Chanath said:**
> Yes, sorry about that. Couldn't stop myself. I am with Arch for while. Thought I'd just only test those extensions in it, but simply liked what I get in Arch. There are no defaults at all. No need to install anything other than what I need. 

I'm going back to using Unity, until it'd live on. The next download of Ubuntu default will be when it'd be officially released. Extensions will be tried on then.

I'll consider this resolved then. I appreciate it  if when I post something from one of the devs that we could respect that (although you do not have to agree with it).  Otherwise you can contact Didier and perhaps explain yourself more clearly on a one on one with him because it takes a lot of my time trying to liason clarifications from the devs and then they are not respected.

Thank you..

Regards..

---

