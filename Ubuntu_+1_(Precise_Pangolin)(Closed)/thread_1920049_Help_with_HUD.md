---
title: "Help with HUD"
date: 2012-02-04
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by wotte on 2012-02-04
I was trying to install hud on ubuntu 12.04 by following the instructions on omgubuntu:
 
[http://www.omgubuntu.co.uk/2012/01/how-to-install-unitys-hud-feature-in-ubuntu-12-04/](http://www.omgubuntu.co.uk/2012/01/how-to-install-unitys-hud-feature-in-ubuntu-12-04/)

and it simply does not show up when I press the alt key. is there something else i need to do? I have restarted my computer several times since the install.

---

### Post by Elfy on 2012-02-04
Thread moved to Ubuntu +1 (Precise Pangolin).

---

### Post by zika on 2012-02-04
> **wotte said:**
> I was trying to install hud on ubuntu 12.04 by following the instructions on omgubuntu:
 
[http://www.omgubuntu.co.uk/2012/01/how-to-install-unitys-hud-feature-in-ubuntu-12-04/](http://www.omgubuntu.co.uk/2012/01/how-to-install-unitys-hud-feature-in-ubuntu-12-04/)

and it simply does not show up when I press the alt key. is there something else i need to do? I have restarted my computer several times since the install.
Two successive clicks on Alt and hold after second... At least that was the case at my machine (while it was installed, purged due to Unity 5.2 testing)...

---

### Post by MG&amp;TL on 2012-02-04
Well...it was working for me, but a recent update borked it, so I imagine it's temporarily broken.

---

### Post by lolpenguin on 2012-02-04
It might be because the Unity version in HUD testing PPA (5.1) is lower than the one in the repos (5.2).

---

### Post by duanedesign on 2012-02-04
For me to get HUD display I have to 'tap' the Alt key. Very quickly I press the key and it displays. If I click and hold or click real slow it does not pop up.

---

### Post by wotte on 2012-02-04
I tried all of your suggestions and nothing has worked so far. I believe that an icon is supposed to show up in compiz config settings manager according to the previously mentioned article, but there is no icon in the unity plugin menu. Is there any specific reason as to why this might happen?

---

### Post by cariboo on 2012-02-04
Check what version of Unity you are using by typing in a terminal:

```
unity --version
```

In my case I'm using 5.2, so the output looks like this:

```
unity --version
unity 5.2.0
```

---

### Post by wotte on 2012-02-04
my output also says:

unity 5.2.0

---

### Post by cariboo on 2012-02-04
As far as I know HUD hasn't been updated to work with Unity 5.2 yet, that's why you are having problems.

---

### Post by zika on 2012-02-05
> **cariboo907 said:**
> As far as I know HUD hasn't been updated to work with Unity 5.2 yet, that's why you are having problems.
I think we've covered that [http://ubuntuforums.org/showthread.php?t=1918193](http://ubuntuforums.org/showthread.php?t=1918193) as @guitara warned us...

---

