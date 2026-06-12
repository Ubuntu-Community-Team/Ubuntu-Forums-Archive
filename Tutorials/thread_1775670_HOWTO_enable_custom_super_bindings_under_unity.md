---
title: "HOWTO enable custom super bindings under unity"
date: 2011-06-05
forum: Tutorials
---

### Post by erjoalgo on 2011-06-05
This post provides a workaround for the issue of Unity stealing the super key modifier and hence preventing custom keybindings which use this modifier.

Under the default settings for Unity it seems that pressing the super key can only be used for unity related tasks. This can be problematic if user would like to keep Unity, but, 


[LIST]
[*]User would like to change/disable the default maps for <Super>+S, <Super>+A, <Super>+F, which in Unity are used for particular tasks. Unity does not currently provide a setting to change these bindings, someone should probably file a bug about it.
[/LIST]

[LIST]
[*]In general, user would like to map <Super>+key to a custom command, such as Super+L = lock the screen, Super+n = negative, or Super+scroll = zoom desktop.
[/LIST]
The problem with the default settings is that, as soon as <Super> is pressed, an action is taken to pass focus to Unity's interface, and subsequent key presses are muted. This effectively disables Super as a modifier key in most cases. 


A possible workaround involves changing the default key to bring up unity's interface. 

[LIST=1]
[*]Go to ccsm
[*]unity, behaviour
[*]Change the "key to show the launcher" to <Super>+anotherModifier (or some other sequence of only modifier kes)
[*]Press back or exit ccsm to apply changes
[/LIST]


[LIST]
[*]Note, in order to continue to be able to use unity's useful  <Super>+[0-9] feature, "anotherModifier" must be a modifier key,  such as alt, shift or control.
[*]I  recommend <super>+<alt> since it is close to the Super key and usually both can be pressed with the thumb
[*]If you want the <Super>+n for "toogle screen negative" and <Super>+mouseScroll for zoom utilities back, simply re enable "Negative" and "Zoom Desktop" from ccsm. They now should work.
[/LIST]
Now, previous "unity commands" which were accessible via <Super>+[0-9asf] are accessible via <Super>+anotherModifier+[0-9asf]. This frees up <Super>+nonModifier to any custom action/command.   

I have been frustrated with all this for a while, and there have been  numerous bugs filed about this, I hope this helps someone.

---

### Post by danduq on 2011-06-21
Helped me, thanks! I find the Unity launcher agonizingly slow sometimes, whereas GNOME-Do is super-quick! I wanted to keep <super><space> as my GNOME-Do launcher, and now I can. GNOME-Do, UNITY-Don't.  ;)

Of course I could always revert back to Ubuntu Classic...

---

### Post by geazzy on 2011-06-21
thanks for this tutorial :)

---

### Post by lytithwyn on 2011-06-22
Thanks, erjoalgo; it works great!  Just to clarify for those who (like me) aren't really familiar with compiz configuration:

[LIST]
[*]ccsm is the CompizConfig Settings Manager and can be installed via `sudo apt-get install compizconfig-settings-manager`
[*]Within ccsm you want to look under the "Desktop" category and click on the "Ubuntu Unity Plugin" icon (this is the unity from erjoalgo's step 2).  At least this is where it is in the Natty version of ccsm anyway.
[/LIST]

---

### Post by pxa on 2011-11-17
Bad news, I guess. I tried those changes and it doesn't impress Unity in 11.10 to much. It just ignores all settings in ccsm, which leads me to the question. Where are those settings stored (in a file) and can I change them manually? The GUI aided changes work more or less as aspected, but that Super Key won't quit functioning. A hint where to look? Somebody, please ?!

Thank you in advance,
Patrick

---

### Post by pxa on 2011-11-17
I've found it! Follow me. ;-)
Use xev to identify the keystroke you might want to disable:

```
me@ubuntu:~$ xev
 KeyPress event, serial 33, synthetic NO, window 0x &#8230;.
 &#8230; keycode 133 (keysym 0xffeb, Super_L), same_screen YES, &#8230;

 me@ubuntu:~$ xmodmaps -pke 
```
- shows all available key-stroke events by keycode
- forward all of them into a file; call it whatever you like:
```
me@ubuntu:~$ touch xmodmap.conf
me@ubuntu:~$ xmodmap -pke > xmodmap.conf
```
- edit with favorite texteditor:
```
me@ubuntu:~$ nano xmodmap.conf
```
- find key-strokes you want to disable; do so by deleting everthing behind &#8222;=&#8220;
```

 keycode 133 = Super_L NoSymbol Super_L  &#8594; <empty>
 keycode 134 = Super_R noSymbol Super_R  &#8594; <empty>
 keycode 206 = NoSymbol Super_L NoSymbol NoSymbol  &#8594; <empty>

```
- save and execute:
```
me@ubuntu:~$ xmodmap xmodmap.conf
```
- add this line to a script executed at login or startup and your done. No more Super key ...

---

