---
title: "blindsided by /etc/bash_completion"
date: 2008-06-27
forum: Testimonials &amp; Experiences
---

### Post by PadreSol on 2008-06-27
I couldn't figure out why some things just weren't working anymore.

Example:

display M4  (hit-tab-for-filename-completion)

wouldn't return M4V21211.thm as a possible image file.

bash_completion was preventing that.

I've mv /etc/bash_completion -> /etc/bash_completion.off


My first encounter with bash_completion.  I was unpleasantly surprised.

In this case the "display" command already knows how to handle itself it doesn't need some bash BS to try to do it.

Does anyone know what's up with bash_completion?  It's another fine example of a program trying to do something "smart" for the user.


Like that Clippy thing in microsoft.

---

### Post by PadreSol on 2008-07-09
So everyone's happy with bash_completion? No one knows? No one cares? I was surprised at how bad it is.

---

### Post by spacelem on 2008-07-15
> **PadreSol said:**
> 
display M4  (hit-tab-for-filename-completion)

wouldn't return M4V21211.thm as a possible image file.

bash_completion was preventing that.

Does anyone know what's up with bash_completion?  It's another fine example of a program trying to do something "smart" for the user.


I use the command line all the time and I've always found *bash_completion* to be incredibly useful. It usually prevents you tabbing out files which don't work with a particular program, and it rarely gets this wrong, but the number of times it works well far outweighs the odd few times it doesn't.

Try the following:
```
killall firef [TAB]
man bas [TAB]
apt-get i [TAB]
tar xzf some_gzipped_tarball [TAB]
tar xzf some_bzipped_tarball [TAB]

```

All work exactly as you'd expect, and don't work without bash_completion. Consider these discussions, if you want to extend bash_completion to make it more useful.

[http://www.debian-administration.org/articles/316](http://www.debian-administration.org/articles/316)
[http://www.debian-administration.org/articles/317](http://www.debian-administration.org/articles/317)

Also, I recommend replacing "*display*" with "*feh*". It's a much better image viewer.

---

