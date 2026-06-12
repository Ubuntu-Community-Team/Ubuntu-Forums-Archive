---
title: "Garbled Fonts in Wine"
date: 2009-05-15
forum: Wine
---

### Post by KamikazeNY on 2009-05-15
Sorry if this has already been asked but I couldn't find a solution on my own. I have a programmable remote and running the remote software in Wine works mostly correct, except the fonts in one particular dropdown are garbled. I copied all the fonts over from a Vista box without any change.

I know it's a vague question but does anyone have any ideas? Screenshot attached.

Thanks.

---

### Post by asdfoo on 2009-05-15
> **KamikazeNY said:**
> Sorry if this has already been asked but I couldn't find a solution on my own. I have a programmable remote and running the remote software in Wine works mostly correct, except the fonts in one particular dropdown are garbled. I copied all the fonts over from a Vista box without any change.

I know it's a vague question but does anyone have any ideas? Screenshot attached.

Thanks.


Which Wine version are you using?

If not the latest then try wine 1.1.21 - [http://winehq.org/download](http://winehq.org/download)

---

### Post by KamikazeNY on 2009-05-15
> **asdfoo said:**
> Which Wine version are you using?

If not the latest then try wine 1.1.21 - [http://winehq.org/download](http://winehq.org/download)
Sorry for not specifying!

Tested using 1.0.1 and 1.1.21. Behavior exists in both.

---

### Post by asdfoo on 2009-05-15
> **KamikazeNY said:**
> Sorry for not specifying!

Tested using 1.0.1 and 1.1.21. Behavior exists in both.

hmm, ok

does the following command help?

wget [http://kegel.com/wine/winetricks](http://kegel.com/wine/winetricks) && sh winetricks comctl32

---

### Post by KamikazeNY on 2009-05-15
> **asdfoo said:**
> hmm, ok

does the following command help?

wget [http://kegel.com/wine/winetricks](http://kegel.com/wine/winetricks) && sh winetricks comctl32
Nice one. That did the trick!

Wasn't aware of winetricks. Totally gonna remember that one!

Thanks!

---

