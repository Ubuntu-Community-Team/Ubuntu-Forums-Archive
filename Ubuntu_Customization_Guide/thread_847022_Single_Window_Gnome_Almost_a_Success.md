---
title: "Single Window Gnome Almost a Success"
date: 2008-07-02
forum: Ubuntu Customization Guide
---

### Post by Gnounc on 2008-07-02
I'm sure this has come up quite a lot...so before I ran crying to the forums
I did a substantial amount of digging.

My goal is to have gimp:
1:Open with a project window allready open and maximized
2:Start with tool dialogue and gimp toolbar above the project page

I tried devilspie...it SHOULD do EXACTLY Everything I'm looking for...
but I can't seem to get it to work. Ok, fail on my side I'm sure.

So new route. Wmctrl and a few not so clever roundabouts.

What I've come to is to change the launcher of gimp to open an image by 
gimp-2.4 /home/erebus/xcf.xcf

(with a file in my home directory called xcf.xcf of course)


with that working fine and dandy I just to get the project screen maximized.
Easily done with wmctrl.

wmctrl -r "xcf" -b toggle,maximized_vert,maximized_horz
or alternatively
wmctrl -r "xcf" -b toggle,fullscreen

also keeping the toolbars above is easy, its in the preferences, you just change their window manager hints.

the only problem comes when I try to combine everything into one launcher

What I end up with is 

gimp-2.4 /home/erebus/xcf.xcf wmctrl -r "xcf" -b toggle,maximized_vert,maximized_horz

all inline

I've added quotes, commas, semi colons and pipes...just apparently not correctly. Could someone please explain to me how to get this to work?

(and yes I know about gimpshop)

---

