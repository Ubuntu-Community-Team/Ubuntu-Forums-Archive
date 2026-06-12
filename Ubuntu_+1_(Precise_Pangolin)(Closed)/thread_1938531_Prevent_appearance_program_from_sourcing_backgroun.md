---
title: "Prevent appearance program from sourcing backgrounds from ~/Pictures"
date: 2012-03-09
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by psych1610 on 2012-03-09
This isn't something new to 12.04(and is probably a design future), but I'm wondering if it's possible to get Ubuntu to stop sourcing background images from the Pictures home directory. As most everyone does, I keep a lot of pictures in there and I don't want most of them being used as backgrounds.

The ones I do I move to /usr/share/backgrounds/ manually (or .backgrounds) and just learned that I can edit /usr/share/gnome-background-properties/ubuntu-wallpapers.xml to make them show up under the Wallpapers sections instead of the Pictures one.

In short, how can I stop Ubuntu from using everything I put in the Pictures section as a potential background choice? Or, any workarounds?

---

### Post by mc4man on 2012-03-09
Do you mean stop making the Pictures dir. from being an available source for backgrounds to you
or
Stop any image in Pictures that is being used as a background from showing in the unity-greeter

The later is possible, the former no clue here

---

### Post by snkiz on 2012-03-09
create a "Photos" directory inside your pictures directory, the appearance app doesn't list sub directories. But you can still tell it where to pull your background from, it doesn't even need to be in your pictures directory.

---

### Post by psych1610 on 2012-03-12
> **mc4man said:**
> Do you mean stop making the Pictures dir. from being an available source for backgrounds to you
or
Stop any image in Pictures that is being used as a background from showing in the unity-greeter

The later is possible, the former no clue here

I'm not sure what the unity-greeter is for certain, but I meant stopping the pictures directory from being an available source for backgrounds.

@snkiz, thanks. I saw that I can choose where to pull the backgrounds from. A good workaround is to just create a photos directory inside of Pictures, my curious side was just trying to figure out a way to stop the appearance app from looking there.

---

### Post by Xgen on 2012-03-12
You can change where Pictures looks for wallpapers by changing the folder location association in ~/.config/user-dirs.dirs. Perhaps create a folder 'Wallpapers' in your home folder and putting only your wallpapers there.

---

### Post by jbicha on 2012-03-13
Xgen, that's probably not a good idea unless you want your default Pictures folder to be ~/Wallpapers. Moving the unwanted pictures somewhere else is a better solution.

---

