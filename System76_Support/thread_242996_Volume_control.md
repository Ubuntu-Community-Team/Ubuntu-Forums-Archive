---
title: "Volume control"
date: 2006-08-24
forum: System76 Support
---

### Post by Kaloma on 2006-08-24
While exploring my new Serval, I noticed that the keyboard volume control (on this machine Fn+F6=mute, Fn+F7=down, Fn+F8=up) adjusts the headphone volume, not the speaker volume (or even better, the master volume).  So far, I have not been able to find any means of changing this behavior.

Any suggestions?

Matthew

---

### Post by crichell on 2006-08-24
I've heard of this one before.  Is the volume control next to the clock set to master?

(Right click speaker > Preferences > Choose Master)

---

### Post by Kaloma on 2006-08-24
Actually, there is no "Master" track on this one.  The device is "HDA Intel (Alsa Mixer)" and the tracks are
[list][*]Headphone[*]PCM[*]Front[*]Microphone[*]Capture[*]Capture 1

My volume control has "PCM" (which I guess is the Master here) as the active track, so I can control the speaker volume fine using the GUI.  But the keyboard controls are still bound to the Headphone track.

Matthew

---

### Post by Kaloma on 2006-08-24
Sorry about my previous post.  I messed up the list, and couldn't find the option to edit my post.

Matthew

---

### Post by crichell on 2006-08-24
Front and PCM both control the main speakers.  This is a bit off topic but to get volume just right you want to set front all the way up then adjust PCM up to the point before the sound gets distorted (you can really tell during shutdown/startup).  Once PCM is set you just use Front to adjust volume up/down.  This will give you the best volume and quality on laptop speakers.

Back to the topic: I don't know - I'll check it out :)

---

### Post by Kaloma on 2006-08-24
Thanks for the advice.  That's what I've got right now, Front at 100%, and I adjust PCM to where I want it. 

I must say that the sound is great.  I didn't expect much from onboard sound in a laptop, but even all the way up the distortion isn't bad.

Matthew

---

### Post by mattias01 on 2006-08-25
I've got the same problem and I have'nt managed to fix it.

---

### Post by crichell on 2006-08-25
Running this command increases both the Headphone and Front speakers:

```
amixer sset Front +1 unmute;amixer sset Headphone 1+ unmute
```

Running this command decreases both the Headphone and Front speakers:

```
amixer sset Front 1- unmute;amixer sset Headphone 1- unmute
```

Running this command mutes both the Headphone and Front speakers:

```
amixer sset Front toggle;amixer sset Headphone toggle
```

We can see these commands in action by opening Volume Control and then running the command in the terminal.  I'm working on determining the best way to change the commands for these hot keys.  We can use xbindkeys but it would be nicer to simply change what Gnome considers Volume Up, Volume Down, and Mute.

This [report]("https://launchpad.net/distros/ubuntu/+ticket/916") leads me to beleive we'll have to go with the xbindkeys method.

---

### Post by crichell on 2006-08-25
**Directions to setup Hot Keys to control both Headphone and Front speaker volume at the same time:**

Before we set this up unmute Front and Headphone and set both to the same volume level in Volume Control.  This will allow the keys to mute/unmute increase/decrease volume on both channels at the same rate and time.

Once caveat to using xbindkeys is that we won't see the Gnome graphic moving volume up and down or muting.  It is happening but we're doing it outside of gnome.  This is an oversight by Gnome devs (something I read they're working on).

First we need to remove Gnome's settings.  Go to System > Preferences > Keyboard Shortcuts

Choose Mute and press Backspace to Disable the hot key - do the same for Volume Down and Volume Up > Close the window

```
sudo apt-get install xbindkeys xbindkeys-config
xbindkeys --defaults > ~/.xbindkeysrc
xbindkeys
xbindkeys-config
```

In the xbind keys GUI that popped up click "New" at the bottom.

Give the new binding the Following Properties
Name: Mute
Key: Click "Get Key" > Once the Windows pops up press Fn+F6 (Mute)
Action: amixer sset Front toggle;amixer sset Headphone toggle

Click "New" Again

Give the new binding the Following Properties
Name: Decrease Volume
Key: Click "Get Key" > Once the Windows pops up press Fn+F7 (Decrease Volume)
Action: amixer sset Front 1- unmute;amixer sset Headphone 1- unmute

Click "New" Again

Give the new binding the Following Properties
Name: Increase Volume
Key: Click "Get Key" > Once the Windows pops up press Fn+F8 (Increase Volume)
Action: amixer sset Front 1+ unmute;amixer sset Headphone 1+ unmute

Click "File > Save to default file"
Click "Save & Apply & Exit" on the right side

Add xbindkeys to the gnome startup session

System > Preferences > Sessions
Startup Programs Tab
Click "Add"
Startup Command = xbindkeys

You can test that it's working correctly by opening Volume Control and using the Hot Keys to adjust volume and mute.  You'll see the sliders move up and down and mute via your new key mappings.

---

### Post by Kaloma on 2006-08-25
Thanks for all your help, Carl.  Your recent suggestions helped me to find [this Wiki page]("http://gentoo-wiki.com/HOWTO_Use_Multimedia_Keys") and [this blog entry]("http://livegnudegirls.blogspot.com/2005/08/amixer-is-afriend.html"), with which I solved the problem without resorting to xbindkeys!

Basic idea:
[list][*]find out the keycode for the key combination you want to assign; use **xev** or just look at current metacity volume keybindings which are in hexadecimal (on my Serval, mute is 0xa0 or 160)
[*]create in your home directory the file **.Xmodmap** (see my attached example); this file will contain mappings from keycodes to X keysym names (which can be found in /usr/share/X11/XKeysymDB in Ubuntu)
[*]use gconf-editor to assign amixer commands to these keys (see second link above)
[/list]

On a technical note, adjusting PCM using amixer didn't work nicely.  It didn't recognize 'toggle' or combined commands like '10%+,10%+ unmute'.  So I just have my shortcuts control the Front track and leave PCM at 100%.

I also don't get to see the pop-up volume meter in the middle of my desktop, but that's not much of a loss.

Thanks again for your time Carl!

Matthew

---

### Post by Kaloma on 2006-08-25
I forgot to mention, the you need to log out and log in again after making the changes I described.  The first time you do this, the X server will presented you with a dialog that asks which modmaps to load.  Add the new file you created, and make sure the box that reads "Don't sow this warning" is checked.

Enjoy!

Matthew

---

### Post by mattias01 on 2006-08-29
I dug a little bit deeper and changeing the volume with channel "Master" is hardcoded in the source. Look in acme-volume-alsa.c at [http://cvs.gnome.org/viewcvs/gnome-control-center/gnome-settings-daemon/actions/](http://cvs.gnome.org/viewcvs/gnome-control-center/gnome-settings-daemon/actions/)

---

### Post by crichell on 2006-08-29
mattias - that's precisely what causes the Hot Keys to adjust Headphones rather than Front.  Headphones = Master.  I think the Gnome guys are working on it though.  Ideally we should be able to adjust Gnome Hot Key commands or  simply set volume hot keys to the device that you want to adjust.

---

### Post by lord trousers on 2006-08-29
The main problem is that volume control on laptops is seriously, seriously messed up. According to what I've read, the AC'97 spec is vague on its pin assignments. Others followed suit, and sometimes they did it obviously wrong on purpose for compatibility! Because of that, there's no standard way to tell which track is the correct master volume control.

That's why the Gnome people let you choose which device and track the volume applet (speaker icon next to the clock) drop-down controls. The oversight is that they don't let you choose the device and track when you set up your keyboard shortcuts. D'oh!

Yeah, they're working on it. I use xbindkeys because it lets me muck with things without logging out and back in.

---

### Post by mattias01 on 2006-08-31
Thanks for the help with xbindkeys anyway. It works.

---

### Post by jigantor on 2006-12-16
Thanks Kaloma for your links - I had this problem and they fixed it quickly and easily. My only comment is unlike the blog, I had to put single quotation marks (') around the channel when using amixer, as in:

```
amixer -q sset 'PCM',0 toggle
```

not

```
amixer -q sset PCM,0 toggle
```

Other than that, a great guide! Thanks!

---

### Post by est on 2007-03-27
This seems to be fixed in Feisty!
Gnome 2.18 has a "default mixer tracks" component. Whatever's selected will be what changes when multimedia keys are pressed.

---

### Post by Kaloma on 2007-03-27
Yes, this is indeed now fixed! In fact, although I changed nothing manually, PCM automatically became the default for my other user login (which I had never played with). I guess I can disable my custom hotkey commands for my primary user now. Very nice.

Matthew

---

