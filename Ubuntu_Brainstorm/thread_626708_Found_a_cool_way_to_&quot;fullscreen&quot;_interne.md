---
title: "Found a cool way to &quot;fullscreen&quot; internet video content"
date: 2007-11-29
forum: Ubuntu Brainstorm
---

### Post by rockin_goliath on 2007-11-29
I was always a little annoyed when watching flash videos on the internet that when I clicked the fullscreen button, it would just open the video in a separate window that I could maximize if I wanted to, but it was still just kind of awkward, especially when in Mac and Windows it is actually full screened.
      As a work around, I started using the zoom function of compiz-fusion to just fullscreen that little bit of the web page. It also really impressed my friends when instead of having such a jarring transition from normal view to fullscreen, it did a really cool zoom effect. With a few modifications of course, could this be a viable way of implementing fullscreen viewing? Perhaps in the form of a Firefox plugin? The reason I ask this on the Ubuntu devel forum is because it is not just Firefox that has problems full screening content. On a separate note, things like F-Spot do not full screen properly when compiz is enabled. Could we maybe implement something that allows applications to work WITH compiz rather then against it? Thanks!

---

### Post by earobinson on 2007-11-29
While its a cool "hack" this is not a feature that could realy be implemented.

---

### Post by tjagoda on 2007-11-29
I agree with the nice ubuntu member man.

---

### Post by raynevandunem on 2007-11-30
It can't be with a Flash video, since the Flash player is closed-source (unless you want to cut your fingers with Gnash pre-alpha). At best, it would be a future embedded Theora video, and I say "future" because the only browser that has implemented it at any length is Opera (closed-source, although they make use of open standards), and their implementation is pre-alpha as well.

Once a Linux web browser like Konqueror or Epiphany implements webpage-embeddable Theora video, then we can start talking about hardware accelerated effects for expanding videos to fullscreen like you said (this hypothetical, open video player will hook directly into OpenGL through its own means, and may or may not deal with Compiz, which is a window manager, to accomplish a zooming fullscreen effect).

The hypothetical web video player, from the best situation of which I can think, would use an plugin for the browser (say, a Firefox extension that uses OpenGL), plus GStreamer and Cairo.

---

### Post by coolen on 2007-12-01
I agree with earobinson. This is a hack, and I don't see any way you could nicely implement this.
As for programs not working properly with Compiz, that would be why it's still under heavy development. This is something that's being worked towards: remember, Compiz is still beta software.

---

### Post by ycason on 2007-12-01
What about a way to quickly pick a bounding box for the zoom?  Say a quick keypress and drag a box, like the screenshot plugin. 

Or for the purpose of a firefox plugin, a way for an outside program to define the box.  That way you get a smooth zoom into the video, and when you're done you can zoom back out.

---

### Post by Ripfox on 2007-12-01
I think it's a great idea...do't let people tell you things are "impossible" as they seldom are.

---

### Post by 23meg on 2007-12-01
[QUOTE=ycason]What about a way to quickly pick a bounding box for the zoom? [/QUOTE]

That's the way to go; it would really be useful.

---

### Post by tjagoda on 2007-12-01
This bounding box concept sounds cool.  I still think the other idea is too hackish.

---

### Post by Drate on 2007-12-01
Wow, maybe I'm wrong, but I don't think this guy was saying to implement EXACTLY THIS METHOD but rather was looking for ideas like the "bounding box" or some way of taking th e PRINCIPLE of his hack and implementing it by a more kosher method.

He was just showing that it principally can be done fairly easily, and with some proper coding could be turned into a functional feature.  Am I wrong?

---

