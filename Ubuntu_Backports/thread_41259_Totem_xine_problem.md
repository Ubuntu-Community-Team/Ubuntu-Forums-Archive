---
title: "Totem xine problem"
date: 2005-06-12
forum: Ubuntu Backports
---

### Post by RastaMahata on 2005-06-12
I was unable to play the audio in my quicktime files. This is the output from the console when running totem and loading a .mov file:
```
alvaro@Eleanor:~$ totem
wine/module: Win32 LoadLibrary failed to load: qtmlClient.dll, /home/alvaro/.gnome2/totem-addons/qtmlClient.dll, /usr/lib/win32/qtmlClient.dll, /usr/local/lib/win32/qtmlClient.dll
```I can see the movie just fine, but no audio at all.

---

### Post by Darrena on 2005-06-12
Have you installed the w32codecs package?

---

### Post by RastaMahata on 2005-06-12
[QUOTE=Darrena]Have you installed the w32codecs package?[/QUOTE]
 the w32codecs package isnt supposed to be neccessary to use xine :/

---

### Post by Darrena on 2005-06-12
[QUOTE=RastaMahata]the w32codecs package isnt supposed to be neccessary to use xine :/[/QUOTE]
 It is to play some formats

---

### Post by RastaMahata on 2005-06-12
[QUOTE=Darrena]It is to play some formats[/QUOTE]
 woah, thanks for the fast reply.

Since when is this true? I was able to play quicktime moves just fine before this backport (that's  totem-xine 1.0)

---

### Post by Burgundavia on 2005-06-12
Those codecs were borken out of xine due to patent/copyright issues. You have always needed them to play quicktime with totem-xine.

Corey

---

### Post by RastaMahata on 2005-06-12
[QUOTE=Burgundavia]Those codecs were borken out of xine due to patent/copyright issues. You have always needed them to play quicktime with totem-xine.

Corey[/QUOTE]
 Oh, I see...

apt-got the w32codecs package, worked like a charm. Thanks people.

damn patents.

---

