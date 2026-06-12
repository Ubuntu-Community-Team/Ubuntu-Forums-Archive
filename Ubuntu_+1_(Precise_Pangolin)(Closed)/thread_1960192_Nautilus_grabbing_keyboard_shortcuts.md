---
title: "Nautilus grabbing keyboard shortcuts"
date: 2012-04-16
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by josephellengar on 2012-04-16
UPDATE TO BELOW: Essentially, it seems like every shortcut set through compiz works, while all of the shortcuts set through system settings->keyboard->shortcuts do not work. That's how I set them in 11.10. Does it no longer work in 12.04?

Hello. I just upgraded to 12.04 and I'm having a big problem with my keyboard shortcuts. Anytime that I try to use one of my custom shortcuts, nautilus grabs the input and that little box pops up in the lower right corner. All of my shortcuts are attached to the Windows/Super key, so when I type, for example, Super-J on my desktop to launch Kmymoney, nautilus pops up the box and thinks I'm just typing "J". 

Something similar happens if I try to launch a shortcut from within a terminal as well. If a terminal is in focus and I type Super-T (shortcut to bring up another terminal) the terminal thinks I typed just t. However, when I just used the shortcut from here, a terminal popped up, though my shortcut to bring up kmymoney (super-j) is not working.

Anyway, any advice?

Thanks!

---

### Post by josephellengar on 2012-04-17
bump

---

### Post by jbicha on 2012-04-17
Are you using Unity?

I was having a problem with keyboard shortcuts that use just Super and a letter also. I tried to set Super+T to open the Trash for GNOME Shell users to match the Unity default but it wouldn't work.

---

### Post by josephellengar on 2012-04-17
> **jbicha said:**
> Are you using Unity?
 
I was having a problem with keyboard shortcuts that use just Super and a letter also. I tried to set Super+T to open the Trash for GNOME Shell users to match the Unity default but it wouldn't work.
 
Should have mentioned. No, I'm using Gnome-Fallback.

---

### Post by mc4man on 2012-04-17
It would appear that atm bindings that use Super may only be set in ccsm > commands, likely that anywhere else may fail

I say likely because there are so (too) many places to set bindings atm & combined with all the possible sessions it's quite time consuming to test.
This is also compounded by pretty much none of the possible 'area's' to set bindings can or do check for conflicts/overrides with the other area's

So if using the fallback with compiz you should probably set in ccsm > commands & for the most part refrain from using those that unity has taken for super
(- though maybe it doesn't matter? The ccsm > commands is not aware of unity super bindings not set in ccsm 
probably the unity super+ are in a .xml or coded in..

The whole deal has gotten a little messy

---

### Post by josephellengar on 2012-04-17
> **mc4man said:**
> It would appear that atm bindings that use Super may only be set in ccsm > commands, likely that anywhere else may fail
 
I say likely because there are so (too) many places to set bindings atm & combined with all the possible sessions it's quite time consuming to test.
This is also compounded by pretty much none of the possible 'area's' to set bindings can or do check for conflicts/overrides with the other area's
So if using the fallback with compiz you should probably set in ccsm > commands & for the most part refrain from using those that unity has taken for super
(- though maybe it doesn't matter? The ccsm > commands is not aware of unity super bindings not set in ccsm (probably the unity super+ are in a .xml or coded in..
 
The whole deal has gotten a little messy
 
Problematic because CCSM only allows up to 20 arbitrary commands at that moment and I have near 60. Also, oddly enough it worked in 11.10, so I'm not sure why it doesn't work now that I have upgraded to 12.04. The only thing that I did was I installed LXDE to try it out and then uninstalled it, so is it possible that that changed some setting somewhere?

---

### Post by mc4man on 2012-04-17
> **josephellengar said:**
> Problematic because CCSM only allows up to 20 arbitrary commands at that moment and I have near 60. Also, oddly enough it worked in 11.10, so I'm not sure why it doesn't work now that I have upgraded to 12.04. The only thing that I did was I installed LXDE to try it out and then uninstalled it, so is it possible that that changed some setting somewhere?
The use of super+ in unity has grown considerably since 11.10 - 
I can say that earlier in 12.04 dev I could set super+'a key unity doesn't use' successfully, right now I can't & that includes  
a key like Ctrl or Shift or Alt+super+`a key' - basically the super key is ignored when using the binding

Is this now intended or not - don't know, I'm pretty sure this is the way it is currently, my installs are just a couple of days old
Can you find a way around? - maybe.
Is this a bug?, haven't checked

If you're not using unity* I'd wonder what would happen if you purged out all unity* packages that can be safely removed & any leftover files
(I myself have not tried, guess I could, I've no real attachment to any of my 12.04 installs that a flash drive can't  attend to

Edit. the fact that you could alter/use super+t for something other than opening trash is interesting

---

### Post by josephellengar on 2012-04-17
> **mc4man said:**
> The use of super+ in unity has grown considerably since 11.10 - 
I can say that earlier in 12.04 dev I could set super+'a key unity doesn't use' successfully, right now I can't & that includes  
a key like Ctrl or Shift or Alt+super+`a key' - basically the super key is ignored when using the binding

Is this now intended or not - don't know, I'm pretty sure this is the way it is currently, my installs are just a couple of days old
Can you find a way around? - maybe.
Is this a bug?, haven't checked

If you're not using unity* I'd wonder what would happen if you purged out all unity* packages that can be safely removed & any leftover files
(I myself have not tried, guess I could, I've no real attachment to any of my 12.04 installs that a flash drive can't  attend to

Edit. the fact that you could alter/use super+t for something other than opening trash is interesting

When I took some frequently-used commands and put them into the Compiz shortcut manager it worked, oddly. I already had purged most of the Unity packages. However, even the built-in shortcuts in the gnome settings manager (such as opening my home directory, Super+n) don't work with the super key. But opening the terminal (super+t) did. Definitely buggy.

---

### Post by mc4man on 2012-04-17
At least here where all sessions are available the only place that super can be used freely seems to be in GS > org.gnome.desktop.wm.keybindings

or in compiz (ccsm
Though haven't searched all possibilities

Now that I'm thinking back I may have been altering a .lens file to add a super+ to start a lens 
(it was the recoll lens that used a default file not realizing that it had a super+ defined that was already taken 
So maybe couldn't set a super+ binding outside of compiz or .wm

---

### Post by mc4man on 2012-04-17
There are 2 new changes slated for gsettings bindings (mutter & wm

What affect if any on various sessions other than GS they'll have I know not
[https://bugs.launchpad.net/ubuntu/+source/gsettings-desktop-schemas/+bug/982719](https://bugs.launchpad.net/ubuntu/+source/gsettings-desktop-schemas/+bug/982719)
[https://bugs.launchpad.net/ayatana-design/+bug/969235](https://bugs.launchpad.net/ayatana-design/+bug/969235)

---

### Post by josephellengar on 2012-04-19
Bump. Still open to ideas.

---

### Post by mc4man on 2012-04-23
You can try this - 
for _custom commands_ set in System Settings > keyboard > Shortcuts > Custom .. that use 'something'+super+'something' but don't work,  try this

Set them anyway, then open gconf-editor > /desktop/gnome/keybindings/
Open up each custom & replace super with Mod4
You'll notice after doing so it changes quite a bit when re-opening System Setting ....

Can also work with super+ if not taken by unity
referenced [here]("http://askubuntu.com/questions/124417/keyboard-shortcut-win-key-doesnt-work-for-custom-commands/124538#124538")

---

### Post by josephellengar on 2012-04-23
> **mc4man said:**
> You can try this - 
for _custom commands_ set in System Settings > keyboard > Shortcuts > Custom .. that use 'something'+super+'something' but don't work,  try this

Set them anyway, then open gconf-editor > /desktop/gnome/keybindings/
Open up each custom & replace super with Mod4
You'll notice after doing so it changes quite a bit when re-opening System Setting ....

Can also work with super+ if not taken by unity
referenced [here]("http://askubuntu.com/questions/124417/keyboard-shortcut-win-key-doesnt-work-for-custom-commands/124538#124538")

Thanks! It works. A little annoying, but it works.

Just have one question:

Where would I find the gconf key for modifying the built in commands- such as moving a window to another workspace or something like that. I couldn't find the key, and obviously I can't make that a custom key (that's just an example; there are a few that I'd like to modify that are "default" commands in that dialog)

---

### Post by mc4man on 2012-04-23
Look in apps/metacity/* though I wouldn't be surprised if not all work

There are also at least 2 places in  gsettings for bindings though I think they're are for Gnome-shell.
(though I have seen a gsettings command I ran to alter some gtk color defines end up also in gconf

Ot. just need to test something, will probably delete - 
I've noticed at times some of my text files are turning into glade files with I'm guessing certain words, letter combos
So i want to post this sentence & see if I paste into a new empty  file what it turns into

```
ambiance gtk2 menus are wrong color based on current light from light, dark from dark.
```

---

