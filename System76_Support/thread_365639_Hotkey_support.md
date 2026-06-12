---
title: "Hotkey support"
date: 2007-02-19
forum: System76 Support
---

### Post by AusIV4 on 2007-02-19
I was wondering how hotkey support is coming along. When I got my Gazelle, before running the upgrades, the sound keys, media keys, the touchpad-disabling button worked fine, but after updating the system they all quit. Today I thought I'd map them using xmodmap, then use beryl to make them function, but xev didn't even return a keycode for the buttons.

It would be quite nice to have these buttons working. Are there any kernel modules I could load to get them working again? Is there any progress being made towards working hotkeys?

---

### Post by crichell on 2007-02-19
I'm surprised they aren't working.  Is side scrolling working on the touchpad?  Can you go to System > Preferences > Keyboard Shortcuts to set hot keys?  Do you have the Gazelle Performance with nVidia graphics or the Gazelle Value w/ Intel graphics?

Thanks, Carl

---

### Post by AusIV4 on 2007-02-19
I have a gazelle value. Turns out I would have gotten a long way by running the System76 driver program after the update.

I'm running KDE, so it's not completely configured, but now that I've got it recognizing the buttons it should be fairly easy to get configured the rest of the way. I was having issues whether I ran Gnome or KDE, but now it works fine under Gnome, and just needs some configuration under KDE.

Thanks.

---

### Post by AusIV4 on 2007-02-19
At a second glance, it seems to be more of an issue of suspend vs fresh boot. I'm not sure the driver program had anything to do with the issue being fixed, but it caused me to reboot, so the buttons work. When my machine comes back out of suspend, the buttons aren't recognized.

Anything I can add to my ACPI config to get things back on track?

[EDIT]
It seems to work fine coming out of hibernate, even if I've suspended since the last fresh boot. Something like this

Boot
Hotkeys work
Suspend
Hotkeys don't work
Hibernate
Hotkeys work

Any ideas?

---

### Post by crichell on 2007-02-20
This may be a hot key module that we need to add to the acpi-support file (I'm not sure if a specific module controls hot keys).  Anyone know?  I'll do some googling.

---

### Post by crichell on 2007-02-20
I should have seen this one :).  in lsmod there is a hotkey module.  Lets try adding it to acpi-support to see if unloading during suspend and reload upon resume will fix the issue.

```
sudo cp /etc/default/acpi-support /etc/default/acpi-support_orig
sudo gedit /etc/default/acpi-support
```

Look for a line that looks like this

```
# Add modules to this list to have them removed before suspend and reloaded
# on resume. An example would be MODULES="em8300 yenta_socket"
#
# Note that network cards and USB controllers will automatically be unloaded 
# unless they're listed in MODULES_WHITELIST
MODULES="snd_hda_intel snd_hda_codec"
```

Add "hotkey" to the list so it looks like this

```
# Add modules to this list to have them removed before suspend and reloaded
# on resume. An example would be MODULES="em8300 yenta_socket"
#
# Note that network cards and USB controllers will automatically be unloaded 
# unless they're listed in MODULES_WHITELIST
MODULES="snd_hda_intel snd_hda_codec hotkey"
```

---

### Post by AusIV4 on 2007-02-20
That didn't help. I also tried manually unloading and reloading the hotkey module, and that didn't help either.

Any other ideas?

---

### Post by crichell on 2007-02-20
not sure - i'll have to hack at it a bit.

---

### Post by AusIV4 on 2007-02-20
I've been looking at different information on google and the ubuntu wiki, but I haven't really found anything very useful. I've tried a number of different methods for getting Multimedia Keys to work, but I can't find anything to indicate Ubuntu is registering the key press at all.

Are you able to reproduce this, or am I in a unique situation?

[EDIT]
I've continued my research a little bit, and I think I have a general understanding of how the hotkeys work. Normally, pressing a button triggers an acpi event in the format 
```

hotkey ATKD xxxxxxxx xxxxxxxx

```
Where the x's represent a number indicating which key was pressed. This can be viewed with the command acpi_listen.

Config files in the /etc/acpi/events/ folder dictate what what action should be taken when the event occurs, generally pointing to scripts in the /etc/acpi/ folder. The scripts in that folder are run when the above event is detected. Most of these call acpi_fakekey $KEY_NUMBER, which is then interpreted by the ACPI manager associated with the desktop manager.

For whatever reason, when I press my buttons after resuming from suspend, no events are triggered. acpi_listen remains blank no matter what buttons I press. So far, I haven't been able to find anything that would indicate why the events are not being triggered. I don't know if there is a kernel module that could trigger these events, or if the problem could be somewhere else.

I don't have time to do any more looking into this right now, but I thought I might write this up to help move things along.
[ANOTHER EDIT]
I just ran lsmod into a file while hotkeys were working, suspended, came back and ran lsmod into another file, compared the files, and the exact same list of modules are loaded, so I'm pretty sure there aren't any kernel modules I could load to fix this.

Also, running ```
sudo acpi_fakekey 115
``` has the same effect as pushing the volume up button, so I'm fairly sure if I can get the acpi events to register, the rest should fall into place.

---

### Post by AusIV4 on 2007-02-22
I'm beginning to think it may not be possible to get the buttons working after suspend. The exact same kernel modules and programs are loaded after suspend and hibernate, so I'm wondering if the buttons could be turned on by the bios, which is run on reboot and wake from hibernate, but not suspend.

If this turns out to be the case, I'll probably just start using hibernate more than suspend, which is a little disappointing because it takes ~5 times longer than suspending. If anyone finds anything on the subject, by all means post your solution, I'd like to hear about it.

---

### Post by crichell on 2007-02-22
I'm sure we can get hot keys after suspend rolling.  We'll be working on it over the weekend.

---

### Post by AusIV4 on 2007-02-22
I appreciate the effort Carl. If I'd had this problem with a PC from Dell or HP I'd have been completely on my own. It's good to know you're so committed to getting things working for your customers.

I still haven't established whether or not this is a general issue with Gazelles or if I'm the only one who has had this problem. Has anyone else reproduced this?

---

### Post by crichell on 2007-02-22
I know I haven't had this problem on my Darter.  I've heard from one customer that fn+f2 didn't work after suspend but not much else.  I'll know more once I can get to hacking on our Gazelle Value over here.

Cheers, Carl

---

### Post by AusIV4 on 2007-03-01
Any news?

---

### Post by don_jones on 2008-01-28
sudo /etc/init.d/acpid restart

solved the problem for me... it did even played all events that occured in the meantime.

---

