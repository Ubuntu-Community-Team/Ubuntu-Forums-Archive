---
title: "skype 4"
date: 2009-02-15
forum: Wine
---

### Post by SonnHalter on 2009-02-15
the install fails when trying to contact server. I think WINE isn't using my network or doesn't want to connect to the internet the way i'm telling it to. 


Is there a way to add a network config to WINE?

---

### Post by alex.rayu on 2009-02-15
Is there something in Skype 4 that would need you to use it over Skype for Linux?

---

### Post by hikaricore on 2009-02-15
[https://help.ubuntu.com/community/Skype](https://help.ubuntu.com/community/Skype)

Here's some info to read on installing the linux version of Skype.

---

### Post by SonnHalter on 2009-02-15
I don't want the sucky linxu version of skype that is 2 years behind. I want 4.0


I do have linux skype installed but it has too many problems and is barely usable. It never saves my settings and my webcam only works if it feels like it

---

### Post by khelben1979 on 2009-02-15
[This link]("http://wiki.winehq.org/FAQ#head-0344b4325219c69636aeffeaa3596d6855283afd") might help you out.

---

### Post by superolmo on 2009-03-17
I know this tread is old, but just to let you know. I wanted to do the same thing, so I tried to install Skype 4 with Wine. It did not work. So I tried using the _Skype Business version (MSI file)_ and I was able to install it. 

*wine msiexec /i Skype.msi*

Unfortunately, there are are still many errors to solve. I have been playing with substituting the libraries with natives one, especially wininet.dll which seems to be the major problem.

Hope this helps somebody with more time then me to continue testing!

Claudio

---

