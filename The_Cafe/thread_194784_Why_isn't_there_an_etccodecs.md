---
title: "Why isn't there an /etc/codecs??"
date: 2006-06-11
forum: The Cafe
---

### Post by SSTwinrova on 2006-06-11
I've been thinking about this for a while, and even though I figure that there's a technical reason why this hasn't been done already, I've never encountered a reason why. Here's what I mean:

Inside /etc lives a folder named codecs. Each individual codec has a .cdc file (i.e. vorbis.cdc, theora.cdc, etc.) that contains all the "magical stuff" (technical term) that tells programs how to endoce and decode files in that format. All these .cdc files would be put in /etc/codecs, so any music, encoding, etc. app that supports this would immediately have access to all the codecs in that directory without the need for gstreamer plugins or native support for apps that use another framework.

Hopefully I explained that well enough to get my point across. Feel free to explain why this can't be done now  :)

---

### Post by jazzmuzik on 2006-06-11
How can you successfully propagandize the world if you don't control media? You could not do it. Media will never be free and easy. Media is the most direct route to your brain and you won't see a lack of control unless they supercede the capabilities of what media provides with another technology. Or something like that.

;)

---

### Post by SSTwinrova on 2006-06-12
I'll take that as a "I don't have a good answer"  ;)

---

### Post by Stormy Eyes on 2006-06-12
[QUOTE=SSTwinrova]Hopefully I explained that well enough to get my point across. Feel free to explain why this can't be done now  :)[/QUOTE]

It sounds a hell of a lot like gstreamer to me, actually.

---

### Post by SSTwinrova on 2006-06-12
[QUOTE=Stormy Eyes]It sounds a hell of a lot like gstreamer to me, actually.[/QUOTE]
Like I said, it might very well be, seeing as how I know extremely little in this area. I guess the reason I assumed it didn't is that in Synaptic the gstreamer add-on packages are called "plugins" which just sound more advanced than a file (or two) being added for each additional codec being supported.

---

### Post by jazzmuzik on 2006-06-12
You asked a technical question in the Cafe. What do you expect?

---

### Post by wmcbrine on 2006-06-14
Code (except scripts) doesn't really belong in /etc. I know that wasn't your point; I'm just nitpicking.

---

### Post by mcduck on 2006-06-14
take a look inside /usr/lib/gstreamer-0.10 ;)

---

