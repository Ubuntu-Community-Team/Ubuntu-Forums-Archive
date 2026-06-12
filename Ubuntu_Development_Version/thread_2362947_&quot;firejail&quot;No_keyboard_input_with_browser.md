---
title: "&quot;firejail&quot;No keyboard input with browser's"
date: 2017-06-04
forum: Ubuntu Development Version
---

### Post by #&amp;thj^% on 2017-06-04
With firejail and any browser in a sandbox>>> no keyboard integration>>>Browser's totally ignores the keyboard.
This is with X11 and wayland sessions.
Same Version of firejail works as expected on 17.04 in both sessions.
I have to use a text editor to insert my text in all fields.
If anyone else using firejail can confirm this.
_On Screen keyboard also ignored._

```
$ xinput
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Logitech M510                               id=10    [slave  pointer  (2)]
&#9116;   &#8627; Lite-On Technology Corp HP USB Multimedia Keyboard    id=12    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; Lite-On Technology Corp HP USB Multimedia Keyboard    id=11    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=13    [slave  keyboard (3)]
    &#8627; HP WMI hotkeys                              id=14    [slave  keyboard (3)]
    &#8627; Lite-On Technology Corp HP USB Multimedia Keyboard    id=15    [slave  keyboard (3)]

```
@jbicha I will wait for you...if you even want this filed as bug yet?

---

### Post by #&amp;thj^% on 2017-06-08
Well as of today 6/8/2017
On a wayland session only>>>firejail with All Browsers I now have my keyboard back.
X11 still have no keyboard input with any Browsers in firejail.

---

### Post by #&amp;thj^% on 2017-06-15
Thanks to halogen2  for the[ link]("https://github.com/netblue30/firejail/issues/116#issuecomment-271516261").

```
GTK_IM_MODULE=xim firejail <your-browser>
```
Now have keyboard input in a X11 session.

---

### Post by ventrical on 2017-06-16
Gee.. you just never give up ! :)

---

### Post by #&amp;thj^% on 2017-06-16
> **ventrical said:**
> Gee.. you just never give up ! :)
You taught me well!  :smile: Just not in my nature I guess.
But I can be a bit wild also. ...off topic I know and sorry.

---

### Post by ventrical on 2017-06-16
> **1fallen said:**
> You taught me well!  :smile: Just not in my nature I guess.
But I can be a bit wild also. ...off topic I know and sorry.

me sorry:)

It's just that you pick some interestingly difficult things to experiment with.

mefallen , not Ufallen :)

---

### Post by jbicha on 2017-06-16
> **1fallen said:**
> 
@jbicha I will wait for you...if you even want this filed as bug yet?

You don't need my permission to file bugs! :p

I don't know anything about firejail. :(

---

### Post by #&amp;thj^% on 2017-06-18
> **jbicha said:**
> You don't need my permission to file bugs! :p

I don't know anything about firejail. :(


You mean I graduated to a big boy status? ;)...I knew I did not need your permission to file a bug, but rather than add a bug report that is non related to Ubuntu. (Still not sure if this is related to Ubuntu/Debian or not)
But I have a good work-around now so all is good.
Kind Regards

---

### Post by ventrical on 2017-06-18
Active development.

[https://launchpad.net/ubuntu/+source/firejail](https://launchpad.net/ubuntu/+source/firejail)

---

### Post by #&amp;thj^% on 2017-06-18
> **ventrical said:**
> Active development.

[https://launchpad.net/ubuntu/+source/firejail](https://launchpad.net/ubuntu/+source/firejail)

Thanks ventrical! :)
netblue30 and Reiner Herrmann are both aware of this.

---

