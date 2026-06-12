---
title: "[SOLVED] muxing ogm / ogg"
date: 2008-09-07
forum: Ubuntu Studio
---

### Post by soxs on 2008-09-07
Is there somewhere a _good_ tutorial which explains howto mux existing video and audio files into ogm/ogg container?
thx for every/any help

---

### Post by eye208 on 2008-09-07
Ogg containers support a limited set of formats only, most notably Theora video and Vorbis audio. OGM is more versatile, but has been superseded by Matroska. There is a graphical Matroska muxer (mkvtoolnix-gui) in the universe repository which is considered very easy to use.

---

### Post by soxs on 2008-09-08
Ok , that GUI tool isn't what I am searching for. Is there a commandline way to do muxing into mkv?

---

### Post by vanadium on 2008-09-08
If there is a separate gui, then there is probably a command line tool under the hood.

---

### Post by soxs on 2008-09-08
I got over that aswell ;-)
mkvmerge is the tool i was searching for.. [SOLVED] (unless I will stumble across problems)

---

