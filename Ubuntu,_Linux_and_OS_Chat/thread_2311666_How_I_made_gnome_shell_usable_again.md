---
title: "How I made gnome shell usable again"
date: 2016-01-29
forum: Ubuntu, Linux and OS Chat
---

### Post by monkeybrain20122 on 2016-01-29
I know there are some gs fans here but for me it is unusable out of the box. I don't know about Ubuntu-gnome since it probably uses patched libraries downstream so maybe the user experience is more agreeable. I did this on Fedora 23 so it is higher version of GS and is closer to upstream.

First of all  gnome-shell's dock is completely useless. Unlike Unity's you can only pin a few applications on it because the icons will become very small after you have maybe 5 and they become drastically smaller all of a sudden, not gradually. Moreover, unlike unity's there is no visual cue of any kind to indicate which applications are open, you cannot click to minimize or unminimize. instead of unminmizing a running app which has been minimised clicking the icon again it opens a new instance. There is no easy way to always hide it as far as I know,  so that if you install a better dock, you end up with two docks which is overkill visually and one of them is completely useless. 

The top panel is a waste of space, even fully maximised windows don't cover it. One feels constricted.

In Nautilus 3.18, the option to permanently delete has been removed (not hidden, but removed), because according to gnome devs it is "confusing " to users. You are forced to send everything to trash instead like WIn10 or OSX. They say you can use the delete key to permanently delete, even if it works it would be a pain because you have to first use the mouse to choose whatever to delete and then reach across to hit delete, but it doesn't even work and I have a G of garbage in trash thinking that they have been deleted. So you basically need to delete everything twice like an idiot.Other features are also[ removed]("https://bugzilla.redhat.com/show_bug.cgi?id=1227946").

To fix this situation I have installed nemo as my default file manager. At first I kept nautilus around but after a few months out of sight I have removed it with no bad effects. nemo works seamlessly except for one thing, which is that it shows or hides hidden files depending on the state of your last exit, I would preferred that hidden files always are hidden by default like Nautilus, but I can live with it.

Then I found [this]("https://extensions.gnome.org/extension/815/simple-dock/") gnome-extension. It is not as fancy as the Cairo dock but it allows you to pin many apps on it without shrinking, it provides visual cue to which app is open, you can click to minimize and unminimise. Those are  big improvements from gnome-shell's waste of space of a dock. Also unlike the gnome dock it can be set to intel hide or always show(gnome's dock needs the dash to dock extension) But best of all, with this installed gnome-shell's dock is automatically suppressed so you won't end up with two docks like you would if you install the Cairo dock or something like that. I would like to have an option to put the dock on the left instead of the bottom, but that is not a big issue.

With the hide top panel [extension]("https://extensions.gnome.org/extension/740/hide-top-panel/") I can make full use of the screen now. There is also a task bar [extension]("https://extensions.gnome.org/extension/584/taskbar/") that provide more information than the simple dock. The preview feature sometimes gets in the way, but can be quite useful especially if you have several instances of the same app running.

With these few changes now it is more usable again. Without extensions gnome-shell is unusable IMO. But gnome-shell extensions are not very reliable, they work in one gs release but may not work any more in the next. Many of them which have received great fanfare on blogs a year or two ago are now all abandoned.

---

### Post by buzzingrobot on 2016-01-29
I like to run one app per workspace, and use the mouse to change workspaces. No hot corners.  No tiling.  No full screen apps.

I use the Dash To Dock extension, which is a must have for me. It behaves like a real dock.  Other extensions disable the top left hot corner (did I say Ican't stand hot corners?), put icons for older apps like Dropbox in the top panel, use the mouse wheel to scroll between workspaces, disable the onscreen popups displayed when changing workspaces, and several other tweaks

Without those, I'd find Gnome pretty offputting, too, mainly because of the hot corner business.

In the end, the way I use Gnome is much the same as I use Unity. With the availability of extensions, Gnome is, in fact, more configurable that Unity. (Plus, I never use scopes and lenses, so all that is wasted on me.)

I find that Gnome's Mutter is a better, smoother, window manager that Kwin or xfwm or Mate's Marco.  While I don't game or consume enough streaming video to really care about tearing, they produce such obvious rippling effects as I scroll in ordinary apps or move windows on screen that I'm avoiding them.

---

### Post by monkeybrain20122 on 2016-01-29
Well here is a wtf moment. Removing totem-parser (something for totem to parse playlists !!) somehow removed my whole gnome-desktop (but removing totem itself is ok) and have to dp a reinstall. Luckily I have a separate /home with all my settings and  tweaks. Since I don't use Fedora much except for some obsolete third party apps all of which are in my /home there aren't many things to reinstall. Still took me about 40 minutes.

---

### Post by monkeybrain20122 on 2016-01-29
> **buzzingrobot said:**
> I like to run one app per workspace, and use the mouse to change workspaces. No hot corners.  No tiling.  No full screen apps.

I use the Dash To Dock extension, which is a must have for me. It behaves like a real dock.  Other extensions disable the top left hot corner (did I say Ican't stand hot corners?), put icons for older apps like Dropbox in the top panel, use the mouse wheel to scroll between workspaces, disable the onscreen popups displayed when changing workspaces, and several other tweaks

Without those, I'd find Gnome pretty offputting, too, mainly because of the hot corner business.

In the end, the way I use Gnome is much the same as I use Unity. With the availability of extensions, Gnome is, in fact, more configurable that Unity. (Plus, I never use scopes and lenses, so all that is wasted on me.)

I find that Gnome's Mutter is a better, smoother, window manager that Kwin or xfwm or Mate's Marco.  While I don't game or consume enough streaming video to really care about tearing, they produce such obvious rippling effects as I scroll in ordinary apps or move windows on screen that I'm avoiding them.

I actually like the hot corner so I have activated it in unity as well with ccsm. I don't know about mousewheel but out of the box the touchpad doesn't even work, complained the synaptic driver didn't load, it has been the case since F21 or something, but I suppose it is more of Fedora's shoddy job then gnome's fault. 

There are many gnome extensions but a lot of these functions are either default (like using top panel for menu) or can be enabled through ccsm in Unity. With Unity I don't have a lot of need or desire to configure things so I am not missing much, install the ccsm and set up the things I use, that's it. Everything is in one place, no need to hunt for extensions that may or may not work.

I find my workflow a lot more fluid in unity. In GS I feel clumsy and constricted (in Unity I can move around workspaces by going to edge, can't do it with gs, There was an extension which kind of do that, --but only vertically,--but it is abandoned now apparently) I think with sensible options and defaults you shouldn't need 100 extensions with varying qualities to keep the desktop usable,-- plus half them are broken or unmaintained at any point in time. some extensions are great like the ones I mentioned, and dash to dock when I still used the useless gnome dock for decoration. But others are not so great (like wobbly window, which tears terribly, nothing like the smoothness in compiz) 

It may be hardware or distro related, but I always find gs kind of sluggish and if you do too many things at the same time window animation somehow lags behind (like the icon remains on the dock for a minute after quiting the application) Never experience that in Unity. 

I do find Unity's dash very useful for local search for both documents and applications (I don't do online search) With that I have no use for menu whatsoever. But Gnomeshell's search is rather basic by comparison.

Edited: one thing kind of intrigues me though, why don't you need to provide password if you install an application from gnome's app store? It is installed globally into /usr/bin!

---

### Post by montag dp on 2016-01-29
The thing about both Gnome Shell and Unity is that they kind of force you to do things one way. If you like that way of doing things, they're great, but if you don't, they're very hard to make work differently. I personally like the GS way of doing things more than the Unity way, maybe because I like to use the keyboard a lot and the Expo view or whatever it's called to switch windows. As for searching, I use it 90% of the time just to open programs, so I don't care about all the other bells and whistles that the Unity search provides.

I will say that GS is more configurable because of the extensions, but those tend to break when a new version of GS is released, which can be even more frustrating.

---

### Post by vasa1 on 2016-01-29
> **monkeybrain20122 said:**
> Well here is a wtf moment. Removing totem-parser (something for totem to parse playlists !!) somehow removed my whole gnome-desktop ...
You mean you didn't check what would be removed :shocked:

---

### Post by monkeybrain20122 on 2016-01-29
> **vasa1 said:**
> You mean you didn't check what would be removed :shocked:

Finger spasm.:)

---

### Post by buzzingrobot on 2016-01-29
> **monkeybrain20122 said:**
> ...in Unity I can move around workspaces by going to edge, can't do it with gs, There was an extension which kind of do that

Two different desktop scroller extensions are available at  the moment. (What you see at extensions.gnome.org depends on your Gnome version). I wouldn't be surprised if there's an extension that works by shoving the cursor against a screen edge.

I install CCSM on Unity but only use it to set up desktop scrolling with the mouse wheel and to center windows. The shiny wiggling parts of Compiz don't interest me. 

Cinnamon is just about the only popular interface that won't let me shift desktops with the wheel. I can run an xdindkeys script to do that by flipping a tilting mouse wheel back and forth, but I find it less than ideal.

Gnome and Unity are both pretty good for keyboard navigators, although I'm not one.

I don't actually use enough different apps often enough to have much of an interest in menus vs Overview vs Dash, etc. What I do use on a recurring basis I launch from icons in a  panel or in a dock. A horizontal row of icons (panel) and a vertical stack of icons (dock) are all the same to me. I'm always amazed, though, to come across the fair number of people who seem to go into cognitive panic when their favorite interface makes a change.

I think Gnome made a fundamental design error in their use of that single hot corner to provide access to everything. Better to keep the dock apart from that. So most of the extensions I add nullify the designers' intent. But, I'll give them points for taking Gnome where they want it to go, within the constraints they've set.  Better to do that and create something consistent and reasonably polished that also  turns some people off than build another copy of Windows (aka "traditional" desktop) with a grab bag of features bolted on something that looks like it was designed by first-year college kids. :tongue:

---

### Post by mikodo on 2016-01-29
> **buzzingrobot said:**
>  - snippet - go into cognitive panic 

All you said was informative.

I couldn't help myself. lol. What is, "cognitive panic"? OCD, Panic Disorder, Bipolar Affective Disorder, Paranoid Schizophrenia, I'll have to look it up ...

---

### Post by monkeybrain20122 on 2016-01-30
> **buzzingrobot said:**
> 

I think Gnome made a fundamental design error in their use of that single hot corner to provide access to everything. Better to keep the dock apart from that. So most of the extensions I add nullify the designers' intent. But, I'll give them points for taking Gnome where they want it to go, within the constraints they've set.  Better to do that and create something consistent and reasonably polished that also  turns some people off than build another copy of Windows (aka "traditional" desktop) with a grab bag of features bolted on something that looks like it was designed by first-year college kids. :tongue:

There are many design errors, like gnome apps are completely inconsistent with "normal" apps both visually and functionally (thankful some of these get patched downstream by the Ubuntu team) I don't know why the way gnome apps such as gedit, nautilus and evince all have odd menu system which splatter across the top where for example "new tab" and "new window" appear on opposite sides on the top and prior to gnome 3.18 a separate "file menu" stuck out of the application's window and appear somewhere on the top panel of the screen, kind of a hybrid of the local and global menu. Then I don't understand why all the gnome apps have to be managed through dconf which is obscure and keep changing instead of just have good old .config directories. The dconf thing seems like a registry lite to me.

 But "design errors" happen at many levels, not just aesthetics, but functionality as well. With the removal of startup applications everytime you want to run a script at startup you not only have to make a script but have to make a .desktop file as well, or gnome-tweak tool will not even see it. It is again due to some "design philosophy" according to gnome devs. Now a valid "design philosophy" should make work easier, not to make you jump through more hoops to get simple things done. This has happened in gnome shell for a few years but somehow strartup applications still exists in unity in Ubuntu 15.10 so I think it is downstream maintenance. I hope it works in Ubuntu-gnome as well (oh and the tweak tool is not even installed by default, without it and the extensions I would really hate to use gnome-shell)

The latest straw is the removal of the "delete bypassing trash" option in nautilus and a few other functions as well (which I don't use but from others' bug reports) and then I found out yesterday in  trying to fix another problem that they now don't even let you use other terminals as default anymore by deprecating the gsettings string that does it. So I am now running actually a hybrid system, with nemo in place of nautilus and the mate-terminal instead of gnome-terminal.

I am not much of a fan of the classical-desktop, there are only two modern looking DE on Linux (unity and gnome shell but Unity is Ubuntu only pretty much) in the mist of a dozen of Windows XP/7 look alikes so I certainly disagree with complaints coming from that direction. My problem is that the gnome-team somehow screwed it up by weird decisions, it could have been better.

P.S I don't use a mouse, no idea about mouse wheeling and such. But it is strange that somehow gnome (and downstream projects like Unity) does not have option to useboth edge and two finger scrolling on the touchpad (you have to choose one through the gui) even though both would work if you make a script to invoke them at at stratup.(now edge scrolling simply doesn't work with Fedora 22 and 23 without a script AND copying some Xorg config file, seems like more of a Fedora issue) I think same with xfce too, I have briefly had a partition for manjaro Linux with xfce on this machine and if I recall correctly the same hack needed to be applied.

---

### Post by buzzingrobot on 2016-01-30
> **monkeybrain20122 said:**
> ...gnome apps are completely inconsistent with "normal" apps...


I don't know what a "normal" app is.  No rules exist for this kind of thing other than the constraints imposed by hardware:  keyboard, mice, pixels. 

Design is whatever designers want it to be.  Consistency of design is important, regardless of what I, personally, think of the design. (I.e., personal preference is no measure of design quality. We can recognize good design and still not like it.)  I like the fact that Gnome has a consistent approach to design, even if I don't like some aspects of it. Ditto Canonical with Unity. I like the fact that both enforce their design requirements.  

More Linux projects need to do that:  One, create a consistent design approach.  Two, enforce it. Too many projects are kitchen-sink hodgepodges that excuse sloppy design by chanting about "choice" and "freedom". Designers and developers take the same risk all creative people do:  Some people will like their work, some won't. The freedom users have is to choose another product, not to expect every product to offer the widest possible range of options.

---

### Post by monkeybrain20122 on 2016-01-30
> **buzzingrobot said:**
> I don't know what a "normal" app is.  No rules exist for this kind of thing other than the constraints imposed by hardware:  keyboard, mice, pixels. 

Design is whatever designers want it to be.  Consistency of design is important, regardless of what I, personally, think of the design. (I.e., personal preference is no measure of design quality. We can recognize good design and still not like it.)  I like the fact that Gnome has a consistent approach to design, even if I don't like some aspects of it. Ditto Canonical with Unity. I like the fact that both enforce their design requirements.  

More Linux projects need to do that:  One, create a consistent design approach.  Two, enforce it. Too many projects are kitchen-sink hodgepodges that excuse sloppy design by chanting about "choice" and "freedom". Designers and developers take the same risk all creative people do:  Some people will like their work, some won't. The freedom users have is to choose another product, not to expect every product to offer the widest possible range of options.

Well it seems that the only "consistency" about gnome is consistently erratic. There is no consistency if you have to install a whole bunch of third party extensions which work in one release but not the next, or may be in conflict with each other just to get basic functions.
  

If anything gnome's approach is singularity inconsistent. I am not a big fan of KDE but you can't complain about inconsistency there. Why would you go hunt for menu for similar tasks (open new tab, open new window) at opposite sides of the applications' window and instead of having one menu you have several splattered about? Up til GS 3.18 one part of the menu is in a separate file menu which stuck to the top panel while the rest is in the apps' window (so they get both global AND local menu) The Unity team fixed that since 14.04. Now there is still a "file menu" separated from the rest but thankfully it is no longer stuck to the top panel. Which goes to where (the gear menu or the "file menu") seems completely arbitrary. Gedit has a big 'save' button, but 'save as' is buried somewhere in one of the two or three menu blocks. "open a new document" is not in the 'file menu" but in another button with no explanation. These only happen in gnome applications. I am willing to listen but I can't think of any good reason, "design" or otherwise, for doing that. 

Every feature has some detractors but usually there are some justifications, whether they fit your use case or not (e.g global menu for small screens, even though I hate it on a 15"" laptop) But gnome is unique in that it has no justification for many things other than blanket 'design decision" which can mean anything (I checked out bug reports on their mailing list occasionally)

About the kitchen-sink hodgepodge approach, I think there is a more or less universal way in Linux to manage configurations, namely to edit config files. Nothing is really hidden except the files themselves  (worst you just delete the .config file/folder and start fresh) But no, for gnome apps you have to go edit these obscure and cryptic gsettings. There location on dconf-editor seems to change from release to release so that people copy and paste gsettings commands from old tutorials wouldn't even know they don't work (no error message). It has no advantage as far as I can see, it seems to be just a way to imitate WIndows' registry (which is the source of a lot of Windows issues)

---

### Post by malspa on 2016-01-30
> **monkeybrain20122 said:**
> I know there are some gs fans here but for me it is unusable out of the box.

Yep, I guess I'm one of those fans (although I think Unity's great, too). I've used various extensions in the past but now I find that I get around quite comfortably in GNOME Shell without having any extensions enabled. Go figure.

---

### Post by buzzingrobot on 2016-01-30
Gnome seems consistent to me, especially visually, which I think is the most important aspect of design.  Granted, like all FOSS projects, Gnome lacks the resources to retain everything in-house until it's perfect.  They rely on that 6-month release cycle to push things out for trial-and-error by users.  Plus, the non-Gnome apps are from developers who play by their own rules. Unless a distribution starts kicking apps out of its repos for failure to adhere to design guidelines, Linux users are stuck with this.

KDE finally put together a visual design team for its new version, after years of distracting and purposeless visual doodads cluttering up its displays.I'm not fond of Breeze and all the flatness, but at least they've recognized that design is a skill apart from development and that talented people are needed for both.

Nothing I've ever seen in Linux, though, has the design consistency the Apple enforces in OS X and iOS, or even Google in Android.

---

### Post by monkeybrain20122 on 2016-01-30
> **buzzingrobot said:**
> Gnome seems consistent to me, especially visually, which I think is the most important aspect of design.  Granted, like all FOSS projects, Gnome lacks the resources to retain everything in-house until it's perfect.  They rely on that 6-month release cycle to push things out for trial-and-error by users.  Plus, the non-Gnome apps are from developers who play by their own rules. Unless a distribution starts kicking apps out of its repos for failure to adhere to design guidelines, Linux users are stuck with this..

You said you find gnome offputting without extensions so where is the appeal of 'consistency'? It is quite ironic that you talk about banning apps from repo a la Apple while GS would be much less functional and visually appealing if not for these haphazard extensions that allow users to overcome many of its design defects. At least KDE users are not all over the internet looking for themes and extensions to change the default functions and look.

Banning apps not conforming to UI design like Apple is not feasible for Linux distros, let alone wrong. If you try that with Gnome shell then your repo will soon end up with only a few mediocre gnome apps like evnice, totem and Rhythmbox together with those gstreamer junks. Now at least KDE has some kickass apps (Kdenlive, Okular, Krita , to name a few), can't think of any for gnome.

---

