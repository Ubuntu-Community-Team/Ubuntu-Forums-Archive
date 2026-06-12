---
title: "How did this guy get his Ubuntu fonts to look so good?"
date: 2006-07-30
forum: The Cafe
---

### Post by Kernel Sanders on 2006-07-30
[**Link**]("http://img325.imageshack.us/my.php?image=desktopmay293og.png")

John :)

---

### Post by Footissimo on 2006-07-30
Possibly using these debs..

[http://ubuntuforums.org/showthread.php?t=180647&highlight=font+rendering](http://ubuntuforums.org/showthread.php?t=180647&highlight=font+rendering)

---

### Post by Kernel Sanders on 2006-07-30
Thats so cool, why cant this be done "out of the box"?

---

### Post by Footissimo on 2006-07-30
Problems with patents and whatnot need to be cleared up first I believe :)

---

### Post by CronoDekar on 2006-07-30
I was able to get my fonts to look really good by putting this in .fonts.conf (note that the filename starts with a dot) in my /home/username and then logging back in:

```

<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
  <match target="font">
    <edit name="autohint" mode="assign">
      <bool>true</bool>
    </edit>
  </match>
</fontconfig>

```

---

### Post by ahaslam on 2006-07-30
> ***John* said:**
> Thats so cool, why cant this be done "out of the box"?

I've heard a lot about Ubuntu fonts and I don't understand why.
The link that you showed looks exactly the same on my box. 
Here's a screen, maybe I'm missing something.

[ATTACH]13443[/ATTACH]


Tony.

PS. I assume that you're referring to the desktop fonts. I didn't see those, he's using a far higher resolution than me.

---

### Post by allans on 2006-07-30
It looks a lot like windows with a clearlooks theme to me...

---

### Post by NESFreak on 2006-07-30
my default fonts look better clearlooks suck. (i simply have best shapes selected in the font config window.)

---

### Post by tageiru on 2006-07-30
> **allans said:**
> It looks a lot like windows with a clearlooks theme to me...
Yeah, that is Windows.

---

### Post by TravisNewman on 2006-07-30
It's Windows, look at the system tray. It's an Ubuntu theme, but it's not Ubuntu.

---

### Post by Footissimo on 2006-07-30
> **allans said:**
> It looks a lot like windows with a clearlooks theme to me...

Doh

I've even installed the clearlooks theme on my XP partition before.

---

### Post by agger on 2006-07-30
I don't know which it is, but the fonts look exactly the same as on my Xubuntu box - even tho it appears to be Windows. :-)

Maybe it just goes to show that fonts and font quality aren't really an issue any longer?

---

