---
title: "Auto-hiding menu: Are you kidding me??"
date: 2015-09-20
forum: Ubuntu, Linux and OS Chat
---

### Post by germ65 on 2015-09-20
My experiences with Linux so far have been sporadic. But when my hackintosh (Gigabyte Brix i3), attached to my TV and used as media player, did not boot anymore, I decided to try Ubuntu to avoid the hassle of setting up OS X on an unsupported hardware. 

I was impressed by Ubuntu hardware support: 
- no need for Bluetooth dongle, as built-in Wifi/BT module works
- audio via HDMI (did not work for some reason on the hackintosh)
- Ethernet interface works at full speed (not so on the hackintosh)

What I still haven't managed to fix:
- the rightmost ~20 pixels or so are missing (perused the forums and spent several **hours** tweaking xrandr. Got a reasonable, but not perfect result)
- Logitech wireless BT keyboard does not wake up the computer (again looked in the forums. Perhaps there is some arcane solution, none found yet. But I managed to have the USB mouse to wake up the computer)
- on boot, error message from xrandr command in .xprofile (screen size not large enough) requires using mouse to click on a tiny OK button

But overall the experience is reasonably good, except for the auto-hiding menu. It is driving me crazy. 

THIS IS SO, SO WRONG. Now I have to FIRST bring my cursor to highlight the menu, THEN find the menu I want, THEN move the cursor to that menu. THIS GOES AGAINST ALL KNOWN GUI BEST DESIGN PRACTICES KNOWN TO MAN. 

How many times this happens in a day? Add up all those fraction-of-a-second losses over time, it's a HUGE mistake. 

AND it seems this cannot be turned OFF???

So, I am unhappy with unity. What can I do?
1. Is there a place in canonical/unity to complain---ahem, give feedback?
2. Do I have to load an alternative GUI? Which one? (remember, I am a long time Mac user, cannot stand sub-par GUIs, including the latest iterations of OS X)

Sorry for ranting, but I really cannot stand this behavior. From reading the forums, it seems I am not alone. I am thankful for any advice.

---

### Post by Bucky Ball on 2015-09-20
*Thread moved to **Ubuntu, Linux and OS Chat**.*

If you need specific support with how to install a lighter desktop environment I advise you tone it down a little and post the details in the appropriate support forum. While I understand your frustration, your current tone will only put people off. 

The simple answer is install a desktop environment which isn't Unity. There are pages online which can help, but in a nutshell, if you wanted a light desktop environment install lxde or xfce4 with:

```
sudo apt-get install xfce4
```

Change xfce4 with lxde if you want that. Log out, choose the xfce or lxde session from the sessions menu, log in.

The other option is to install Xubuntu, Lubuntu or Ubuntu Mate instead which don't use Unity (along with others).

As for providing feedback (abuse they don't need) the Unity dev team, presuming there is one, would probably be the place to aim your research.

---

### Post by craig10x on 2015-09-20
It's just a dock...like the mac has...except it is on the left side instead of the bottom...i can't figure why you are making such a fuss about it...

---

### Post by Bucky Ball on 2015-09-20
PS: You can install either lxde or xfce4 via Software Centre rather than a terminal.

---

### Post by buzzingrobot on 2015-09-20
Can't offer anything on the HDMI/TV display issue except that some video card/display combos produce different resolutions depending on the port in use.  Here, my Dell monitor requires using the DisplayPort to get the advertised maximum resolution.  Using HDMI drop it down signficantly.

You don't mention which version of Ubuntu you're using. Look in Systems Settings->Appearances->Behavior to see if you have an option to show menus in the window's title bar or in the menu bar (a bit like OS X).

The most recent release, 15.04, has implemented a "hidden" option to put the menus in the window title bar and make them permanently visible.  Check this quickly Googled link: [URL="http://www.pcworld.com/article/2913391/ubuntu-1504-vivid-vervet-released-revamped-again-menus-systemd-snappy-core-for-smart-devices-and-mo.html"]http://www.pcworld.com/article/2913391/ubuntu-1504-vivid-vervet-released-revamped-again-menus-systemd-snappy-core-for-smart-devices-and-mo.html.


[/URL]

---

### Post by monkeybrain20122 on 2015-09-20
In am not sure what you are asking. Autohide is not enabled by default so you must have changed the settings yourself. To disable autohide, so the launcher always shows. Click the gear on the upper right corner, choose System Settings from the dropdown, then go to Appearance > Behavior and turn off auto hide. That's it.

---

### Post by mystics on 2015-09-20
Unity offers the most Mac-like interface. I'm not sure of your specific issues. The launcher shouldn't be set to hide automatically, so that is in an issue with a setting you changed. Or are you talking about another set of menus?

Anyways, as a Mac user, I'm really happy with Xubuntu (which uses the Xfce desktop) with docky installed to get a Mac-like dock. It doesn't have all the fancy animations that OS X has, but the interface is very well laid out and easy to use and customize.

---

### Post by monkeybrain20122 on 2015-09-20
> **mystics said:**
> 
Anyways, as a Mac user, I'm really happy with Xubuntu (which uses the Xfce desktop) with docky installed to get a Mac-like dock. It doesn't have all the fancy animations that OS X has, but the interface is very well laid out and easy to use and customize.

You will get the fancy animations (and more) if you install Compiz.

---

### Post by mystics on 2015-09-20
> **monkeybrain20122 said:**
> You will get the fancy animations (and more) if you install Compiz.

Oh, yeah, I forgot to mention that. Really also should get to trying Compiz out for myself sooner or later. I've been meaning to do it for a while now but just haven't bothered to do it yet.

---

### Post by Copper Bezel on 2015-09-20
> **mystics said:**
> The launcher shouldn't be set to hide automatically, so that is in an issue with a setting you changed. Or are you talking about another set of menus?
Yes, he is, quite explicitly - the application menu, which is in the same place as on a Mac but autohides like Mac doesn't. Hidden "under" the application title in the top bar. I know there's a way to move them to the window title bar, but I don't know of any way to disable the autohide. 

I'd suggest getting used to the menu search from Alt instead, honestly, if it was universally supported, but not all applications work with it. (For those that do, it's pretty clever at guessing what you want and very good at keeping recent menu items on top without hiding others.)

---

### Post by mystics on 2015-09-20
> **Copper Bezel said:**
> Yes, he is, quite explicitly - the application menu, which is in the same place as on a Mac but autohides like Mac doesn't. Hidden "under" the application title in the top bar. I know there's a way to move them to the window title bar, but I don't know of any way to disable the autohide.

I'm aware of the way the application menu works. I did use Unity for a while before switching over to Xfce so I'm semi-familiar with how it works. But I ended up misreading the OP and thought I saw something that didn't describe that particular menu, but going back to read it I realize that was just me having a stupid moment.

---

### Post by germ65 on 2015-09-21
Sorry, I am talking about the application menu bar, no the dock/launcher. The launcher is not hiding by default (thanks God).

---

### Post by germ65 on 2015-09-21
> **buzzingrobot said:**
> Can't offer anything on the HDMI/TV display issue except that some video card/display combos produce different resolutions depending on the port in use.  Here, my Dell monitor requires using the DisplayPort to get the advertised maximum resolution.  Using HDMI drop it down signficantly.

You don't mention which version of Ubuntu you're using. Look in Systems Settings->Appearances->Behavior to see if you have an option to show menus in the window's title bar or in the menu bar (a bit like OS X).

The most recent release, 15.04, has implemented a "hidden" option to put the menus in the window title bar and make them permanently visible.  Check this quickly Googled link: [URL="http://www.pcworld.com/article/2913391/ubuntu-1504-vivid-vervet-released-revamped-again-menus-systemd-snappy-core-for-smart-devices-and-mo.html"]http://www.pcworld.com/article/2913391/ubuntu-1504-vivid-vervet-released-revamped-again-menus-systemd-snappy-core-for-smart-devices-and-mo.html.


[/URL]

I am on 14.04.3. HDMI gives me all the resolution my old TV can handle.
Happy to hear that 15.04 gives the user the choice. 
I think I am going to try xfce.

---

### Post by deadflowr on 2015-09-21
Easy fix
```
gsettings set com.canonical.Unity always-show-menus true
```
A couple of gui apps can (should) do this, such as unity-tweak-tool or dconf-editor.
But that's the underlying command they'd run to get it to show the menus.
(works for 14.045 and 15.10, at least)

Par for the course, really, as unity comes with a barebones settings manager.
If you were to only use the settings appearance page, you'd have a limited number of settings to change.
And quite a few of the more popular settings aren't even in there.
(like change icons or fonts)

---

### Post by buzzingrobot on 2015-09-23
> **germ65 said:**
> 
I think I am going to try xfce.

XFCE gives some people, including me, problems with video tearing. It's the XFCE window manager and its compositor. There are ways to try to tweak it (e.g., a vertical synch option in settings), and it probably varies on different hardware.  But, I've seen it enough on multiple machines using multiple video cards and multiple distributions to avoid XFCE until I see that it's been addressed.  Pity, because I think Xubuntu is an excellent piece of work.

I don't think it's contrary to the spirit of Linux, whatever that really is, for designers and developers to make decisions about the amount of configurability they choose to expose to users. The "freedom" in FOSS is developer-created and developer-sustained. (I.e., it was not created solely to provide an abundance of choices to users.) So, when a develop chooses one particular approach, that's his or her right.  It's our right as users to decide if we want to use that software. Some cooks open restaurants selling burgers and fries, others open gourmet cafes.  One restaurant, or one Linux desktop environment, can't be expected to offer every dish anyone might want at any time.

Either Unity and Gnome seem the best, but not perfect, fit for my own patterns and preferences.  There are things I'd change in both, but when I use other, more configurable, environments, I typically turn off most of the "flashy" options and set things up like Unity or Gnome, anyway. I've been using  a dock-on-the-left, multiple workspaces scheme for years.

---

### Post by germ65 on 2015-09-24
Deadflowr, THANK YOU, you are a genius. 

No idea why this didn't show up when I googled.


So so much better now.

---

