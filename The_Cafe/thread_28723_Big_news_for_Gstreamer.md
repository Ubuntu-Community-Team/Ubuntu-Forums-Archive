---
title: "Big news for Gstreamer"
date: 2005-04-21
forum: The Cafe
---

### Post by Nis on 2005-04-21
According to [Ronald Bultje](http://www.advogato.org/person/rbultje/), a major hacker on Gstreamer, Gstreamer now has the ability to load DLLs like Mplayer and Xine.  As soon as he gets this working for Totem this means there is no need for totem-xine as long as you have the w32codecs and this Gstreamer component.  One step closer to a Gstreamer based multimedia solution. :)

The bad news is that this "solution" is not really ideal; I would much rather have ffmpeg work like they say it should.  But until then I'll gladly take this over another library dependence (libxine) and a fragmented multimedia solution (Gstreamer + Xine).  

Any chance we'll see this Breezy (if it works in time)?  Better yet, how about a backport for all us loyal Hoary users (hint, hint jdong ;))?

---

### Post by Nano on 2005-04-21
[QUOTE=Nis]According to [Ronald Bultje](http://www.advogato.org/person/rbultje/), a major hacker on Gstreamer, Gstreamer now has the ability to load DLLs like Mplayer and Xine.  As soon as he gets this working for Totem this means there is no need for totem-xine as long as you have the w32codecs and this Gstreamer component.  One step closer to a Gstreamer based multimedia solution. :)

The bad news is that this "solution" is not really ideal; I would much rather have ffmpeg work like they say it should.  But until then I'll gladly take this over another library dependence (libxine) and a fragmented multimedia solution (Gstreamer + Xine).  

Any chance we'll see this Breezy (if it works in time)?  Better yet, how about a backport for all us loyal Hoary users (hint, hint jdong ;))?[/QUOTE]
 I'll believe it when I'll see it.
:)

---

### Post by bored2k on 2005-04-21
That's great news. It even made me sudo apt-get install totem-gstreamer ^_^.

edit > Nevermind... went back to totem-xine :roll:

---

### Post by poofyhairguy on 2005-04-21
Good. Something needed to happen before Totem was officially declared useless.

---

### Post by bored2k on 2005-04-21
[QUOTE=poofyhairguy]Good. Something needed to happen before Totem was officially declared useless.[/QUOTE]
 If vlc would do something regarding wmv videos [[or allow external plugins]] nothing could beat it. It's my weapon of choice regarding video files. That and xine-ui for things that vlc can't handle [plus, it's new gtk2 UI is viewtiful -- hidden videogame reference].

---

### Post by Stormy Eyes on 2005-04-21
[QUOTE=poofyhairguy]Good. Something needed to happen before Totem was officially declared useless.[/QUOTE]

Too late, IMHO.

---

### Post by Nis on 2005-04-21
pittfdll (the Gstreamer component to dynamically load DLLs) now works with Totem. :)  When I get a change I'll try to get it working.  I might be able to ditch totem-xine entirely soon. :)

---

