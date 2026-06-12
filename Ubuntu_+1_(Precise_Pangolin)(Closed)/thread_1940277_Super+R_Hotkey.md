---
title: "Super+R Hotkey?"
date: 2012-03-13
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by neu5eeCh on 2012-03-13
I pressed this combination thinking I would get a Run dialogue box. Instead, it turned my desktop into a sort of meta-desktop where I  could move the entire desktop with my mouse "underneath the launcher and panel" (but couldn't click on the launcher or panel). Since I'm still learning about Unity. What the ****heck**** did I do? I could ***not*** get out of it. I couldn't click on anything. I finally had to hard reboot? (I googled "Super-R Unity" but couldn't find anything useful.)

---

### Post by grahammechanical on 2012-03-13
That combination is not listed in the keyboard shortcuts overlay that appears when holding down Super.

That overlay shows that Alt+F2 gives the 'Run command' mode.

Regards.

---

### Post by screaminj3sus on 2012-03-13
I ran super + r here and same thing happened. This hotkey should either be fixed (what the hell is it actually supposed to do?), or disanbled by default before release... I had to ctrl + alt + f1 and sudo reboot to get out of it lol. You don't want users accidently invoking whatever that is in its current state haha.

---

### Post by x-shaney-x on 2012-03-13
That combo does nothing here.
Could it be related to compiz plugin?

I have things pretty much set to default here with no other compiz plugins enabled.

---

### Post by screaminj3sus on 2012-03-13
I havent enabled anything extra in compizconfig (all I've done is disabled sync to vblank)

---

### Post by mc4man on 2012-03-13
It's a default enabled 'ezoom' key as seen in the screen.  Seen directly in gconf, currently have no clue what 'unfits' it 
Edit: setting a zoom out binding will restore
(would be nice it that was in the overlay & how to return to normal

Also seen in ccsm > ezoom > zoom area movement


Re-edit: - bug on 
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/953278](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/953278)

---

### Post by tanari on 2012-03-13
arrgh, I just pressed win+R :(, why I did that...

---

### Post by jbicha on 2012-03-13
According to the [Compiz wiki]("http://wiki.compiz.org/Plugins/Ezoom"), Super+1 might be the hotkey to get back to normal zoom. Of course, that won't work in default Unity.

---

### Post by jbicha on 2012-03-13
See also [http://ubuntuforums.org/showthread.php?t=1172386](http://ubuntuforums.org/showthread.php?t=1172386)

---

### Post by keithpeter on 2012-03-13
Hello All

I'm seeing this Super-R behaviour and I don't have gconf-editor installed, nor CCSM. Only MyUnity.

Clearly needs to be either removed, or a way of reverting to normal provided along with documentation.

Or we could spread a rumour that it was a new GUI enhancement :twisted:

---

### Post by matt_symes on 2012-03-13
Yep. 

This is the oddest key combination i have ever pressed on any keyboard, anywhere, at any time.

---

### Post by neu5eeCh on 2012-03-13
Thanks for all your comments. I *wondered* what happened!?! Now I feel just a little less stupid. Just a little... Added a comment to the bug report.

---

### Post by mc4man on 2012-03-13
Looking down a bit in gconf-editor there is a zoom out key disabled by default, set it here to <Super>o & that restores
(as it turns out the option is right there in ccsm > ezoom, missed it somehow

Still doesn't account for a user going Super+t & hitting r instead or otherwise hitting that combo as it's not documented

---

### Post by jb5 on 2012-03-18
```
alt+F2
unity --replace
```Will also reset desktop should you accidently press super+R, though this will throw any opened windows about aswell.

---

### Post by scradock on 2012-03-18
For me hitting Super+R again de-zoomed the desktop. Looks like a toggle.

Looks like a fun feature - I wonder what we can do with it?

---

### Post by neu5eeCh on 2012-03-18
> **scradock said:**
> For me hitting Super+R again de-zoomed the desktop. Looks like a toggle.

Looks like a fun feature - I wonder what we can do with it?

Hmmm... maybe they squished that bug? I'm still too shaken up by my last experience to test it. 8-[

---

### Post by scradock on 2012-03-18
> **VTPoet said:**
> Hmmm... maybe they squished that bug? I'm still too shaken up by my last experience to test it. 8-[

I'm not sure it's a bug - just an undocumented feature of the "Enhanced Zoom" plugin. For some reason that defaults to on, and one of its many settings has "Super+r" to toggle the default zoom. Looks as if that's about the only keyboard binding that isn't disabled by default! I've disabled the whole plugin.

---

### Post by jb5 on 2012-03-19
Doesn't appear to toggle for me!
```
gconftool-2 --set /apps/compiz-1/plugins/ezoom/screen0/options/fit_to_window_key --type string "Disabled"

gconftool-2 --unset /apps/compiz-1/plugins/ezoom/screen0/options/fit_to_window_key
```appears to successsfuly disable / reset respectively.
[May need to install gconf-editor, if not already installed, to get the above to work.]

---

### Post by jrobiii on 2012-04-01
Yeah, coming from Windows, I use Super (Windows) R out of habit to bring up the Run dialog.

The unity --replace is a decent workaround until I can break the habit.

---

### Post by mc4man on 2012-04-01
This is fixed in current trunk - will show up in next compiz-plugins-main upgrade (there will be no default key set to zoom

---

### Post by ubuntu27 on 2012-04-03
Hitting the Super+R key now opens the Unity Launcher (if it is hidden) without opening the Dash. And the Unity launcher stays open or visible until you hit SUPER key.

---

### Post by xyzzyman on 2012-04-03
While I'm pulling in 100MB's of upgrades which includes the fix for this, I went and pressed Super+R before reading the thread to see what comes up instead of a run box... Oops.

---

### Post by ubuntu27 on 2012-04-04
Ubuntu News at iloveubuntu.net: [New keyboard shortcuts landed in Precise Pangolin ]("http://iloveubuntu.net/new-keyboard-shortcuts-landed-precise-pangolin")

---

