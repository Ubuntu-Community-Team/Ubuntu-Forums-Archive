---
title: "Change Mutter theme"
date: 2022-04-12
forum: Ubuntu Development Version
---

### Post by rodride on 2022-04-12
my Mutter theme is set to Adwaita even though it says Orchis-grey-dark on Gnome Tweaks. How do I change that?

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=290276&stc=1[/IMG]

---

### Post by deadflowr on 2022-04-12
The shell theme is different than the window theme.
[s]Best option to change shell themes is

1)Have Extensions program installed. (Should be installed as part of the gnome-shell-extension-prefs package. if not install that)

2) Enabled the user themes extension. (This is part of the gnome-shell-extensions package, install it if not installed)

3) Place the shell theme you want inside the a .themes directory inside your home folder. 
(If the .themes directory does not exist, make it; it is .themes, so remember the dot, it's important.)

(*Note that you might also be able to set a themes directory inside the ~/.local/share directory too.
That folder would not need the dot, as the dot is already set for the .local directory.)

4) In gnome-tweaks, goto Appearance, and you should be able to toggle the theme in a dropdown for the shell item listing.
(If gnome-tweaks is not installed, just install the package gnome-tweaks)
 The toggle will only list actual gnome-shell themes so if you try a non-shell theme it will not show.

I'm sure this is probably convoluted, but I hope it makes some sense.[/s]

Edit: Sorry, I now realize the wm theme is probably also different from the shell theme.
I think you can change it in dconf editor (needs to be installed)
It's in the section org > gnome > desktop > wm > preferences, the option is theme.

Can also use the gsettings command like
so
```
gsettings get org.gnome.desktop.wm.preferences theme
```
to see the current theme.
```
gsettings set org.gnome.desktop.wm.preferences theme <new-theme-name>
```
to set a new theme; replace <new-theme-name> with the theme name, no brackets required.

and to revert back to the defaults run
```
gsettings reset org.gnome.desktop.wm.preferences theme
```

Maybe that is what you want.
[B]
Second Edit:[/B] I now see the key is marked as deprecated and ignored, so I don't know what to think or do about it.
I don't know where it's set at now.
Sorry for being rather convoluted about it.

---

### Post by rodride on 2022-04-13
Thanks for your answer deadflowr

It works fine with gsettings command

---

