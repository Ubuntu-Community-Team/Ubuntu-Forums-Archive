---
title: "i wish i had a terminal like this"
date: 2008-11-10
forum: The Cafe
---

### Post by chucky chuckaluck on 2008-11-10
i love using terminal apps and tiling window managers, but i also like wallpapers. in order to use a wallpaper as a background for a transparent terminal, the wallpaper has to be of limited contrast, or in colors opposing the text color, if the info in the terminal is to be readable. i would love it if a terminal could somehow read the value of the color behind it and switch text color appropriately. i'd even be happy if it could only do this in black and white at first, with the text being white (or, light gray) over black areas of a wallpaper and black (or, charcoal) over the white areas. how hard would this be to make happen?

---

### Post by elmer_42 on 2008-11-10
While I don't know how hard it would be, I'm not sure I would enjoy using a terminal like that. All the switches between colors would most definitely annoy me.

---

### Post by chucky chuckaluck on 2008-11-10
> **elmer_42 said:**
> While I don't know how hard it would be, I'm not sure I would enjoy using a terminal like that. All the switches between colors would most definitely annoy me.

you just wish you'd thought of it.

---

### Post by JohnFH on 2008-11-10
If the font had a heavy shadow to it then it wouldn't need to change colour.  I'm sure it's already possible to do that in a terminal and I tried something similar a while ago, but it still wasn't as easy to read the terminal.

What you want is for the opacity of the terminal to change over time, so it would be almost opaque as you type but gradually become more transparent if you leave it silent.

I currently use fixed transparency of the terminal set to 50% I think.

---

### Post by chucky chuckaluck on 2008-11-10
> **JohnFH said:**
> If the font had a heavy shadow to it then it wouldn't need to change colour.  I'm sure it's already possible to do that in a terminal and I tried something similar a while ago, but it still wasn't as easy to read the terminal.

What you want is for the opacity of the terminal to change over time, so it would be almost opaque as you type but gradually become more transparent if you leave it silent.

I currently use fixed transparency of the terminal set to 50% I think.

the shadow idea is making this more likely, i think. if the font were white and the shadow black, that would pretty much take care of it, even if one had to shade the terminal a bit. this is really more of a problem in tiling wm's, as the whole desktop area is used.

edit: it looks like all i need is to know how to add font shadow to urxvt and how to color it.

---

### Post by elmer_42 on 2008-11-10
> **chucky chuckaluck said:**
> you just wish you'd thought of it.
Yeah. :'(

---

### Post by Bölvaður on 2008-11-10
You may need opengl that changed each pixel according to the background. This could be very tricky when the background is noisy (would make the letter almost disappear).
But that problem can be countered on the detection side. When you find this noisy background that would make the letters unreadable, you could make the background of the terminal stop being as transparent.
The detection of the background might not be too much problem if you make this as a plugin for compiz.

Would be very good indeed. But perhaps useless ^^

---

### Post by iponeverything on 2008-11-10
cool idea. You could call it Cephalopod.

---

### Post by pp. on 2008-11-10
> **chucky chuckaluck said:**
> it looks like all i need is to know how to add font shadow to urxvt and how to color it.

That would look very cool. You wouldn't be able to read it, though, not at a comfortable pace.

---

### Post by chucky chuckaluck on 2008-11-10
i'm beginning to realize how goofy an idea this is. if i had to use some compiz-like whirlygig, that would sort of defeat the purpose of using lightweight apps on a minimal system. oh well...

---

### Post by pp. on 2008-11-10
Why don't you make a mockup using different backgrounds and lettering colors? Applying different 'mixing' rules with the Gimp shouldn't be all that difficult. That way, you could quite easily see whether it was still legible.

---

### Post by JohnFH on 2008-11-10
> **chucky chuckaluck said:**
> i'm beginning to realize how goofy an idea this is. if i had to use some compiz-like whirlygig, that would sort of defeat the purpose of using lightweight apps on a minimal system. oh well...

Well if you put it that way, yes it is a bit goofy. ;)  Sounds like you want compiz effects without compiz overhead.

My recent waste of time exercise was to display last login information on my grub menu.  Yes it's possible (on a minimal system too), but a bit pointless.

---

### Post by chucky chuckaluck on 2008-11-10
> **JohnFH said:**
> Well if you put it that way, yes it is a bit goofy. ;)  Sounds like you want compiz effects without compiz overhead.

no, there's nothing about compiz that i like. when i still used openbox, i used a ton of different wallpapers and haven't got that out of my system yet. i have found myself making more use of wallpaper-like wallpapers though, so maybe i just need to make the limitation into a catalyst for a whole new style of making wallpapers. you know, instead of big panoramas, just make little patterns that i could tile as a backdrop.

---

### Post by brunovecchi on 2008-11-10
> **chucky chuckaluck said:**
> no, there's nothing about compiz that i like. when i still used openbox, i used a ton of different wallpapers and haven't got that out of my system yet. i have found myself making more use of wallpaper-like wallpapers though, so maybe i just need to make the limitation into a catalyst for a whole new style of making wallpapers. you know, instead of big panoramas, just make little patterns that i could tile as a backdrop.

By the by, do you know where to get that kind of wallpapers? I stumbled upon a few the other day, and they are really pleasant to have. They are difficult to look for though, any links?

---

### Post by JohnFH on 2008-11-10
Just found urxvt - that looks like a good option.

(Am I allowed to use the link below?)
[urxvt on Arch]("http://bbs.archlinux.org/viewtopic.php?id=48097")

---

### Post by chucky chuckaluck on 2008-11-10
> **JohnFH said:**
> Just found urxvt - that looks like a good option.

that's what i usually use. it's lighter than xterm and can be made transparent with tinting and shading. unfortunately, it doesn't look like there's an easy way to do text shadows.

@brunovecchi - i usually just make my own wallpapers for what you asked about. i'll take some little ornament, make it small and then just tile it for wallpaper.

---

### Post by lukjad on 2008-11-10
> **chucky chuckaluck said:**
> i love using terminal apps and tiling window managers, but i also like wallpapers. in order to use a wallpaper as a background for a transparent terminal, the wallpaper has to be of limited contrast, or in colors opposing the text color, if the info in the terminal is to be readable. i would love it if a terminal could somehow read the value of the color behind it and switch text color appropriately. i'd even be happy if it could only do this in black and white at first, with the text being white (or, light gray) over black areas of a wallpaper and black (or, charcoal) over the white areas. how hard would this be to make happen?
When I get home, I'll try to figure out how to upload my settings if you like, but what I do is darken the shade to about 50% and have the font be a semi-light gray. If you really want to have something consistent, you can just choose a specific wallpaper to fake a background. That way you won't have to worry about radical colour changes.

---

### Post by chucky chuckaluck on 2008-11-10
> **lukjad007 said:**
> When I get home, I'll try to figure out how to upload my settings if you like, but what I do is darken the shade to about 50% and have the font be a semi-light gray. If you really want to have something consistent, you can just choose a specific wallpaper to fake a background. That way you won't have to worry about radical colour changes.

this is what i'm using now...

[i]urxvt*foreground: #dddddd
urxvt*background: #000000
urxvt*scrollBar: false
#urxvt*inheritPixmap: true
urxvt*font: xft:monospace-7
#urxvt*shading: 50
#urxvt*cursorColor: #B82C7F
urxvt*cursorColor: #027af6[/i]

were you talking about something much different?

---

### Post by lukjad on 2008-11-10
Uhh... I don't know. I'm far away from home. I'm working on a Win machine.

---

### Post by chucky chuckaluck on 2008-11-10
> **lukjad007 said:**
> Uhh... I don't know. I'm far away from home.

i think it sounds about the same as what you've described, which makes me wonder if i've done a poor job describing what i'm after here (wouldn't be the first time).

---

### Post by LateNiteTV on 2008-11-10
ETerm!!!!!!!!!!!!!!!!!

---

### Post by init1 on 2008-11-10
> **chucky chuckaluck said:**
> that's what i usually use. it's lighter than xterm and can be made transparent with tinting and shading. unfortunately, it doesn't look like there's an easy way to do text shadows.

xterm is too heavy?

---

### Post by elmer_42 on 2008-11-10
To me it also sounds like you (chucky) and lukjad are talking about the same thing. I use a similar setting, a 50% transparent dark bg w/ a light grey (I use #e6e6e6) text color.

---

### Post by handy on 2008-11-10
Have you seen this page on the Arch Wiki Chucky?

***_[http://wiki.archlinux.org/index.php/Configuring_Terminal_as_a_Transparent_Wallpaper](http://wiki.archlinux.org/index.php/Configuring_Terminal_as_a_Transparent_Wallpaper)_***

---

