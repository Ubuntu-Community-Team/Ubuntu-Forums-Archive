---
title: "Firefox Addressbar Unwanted Search Feature"
date: 2011-08-19
forum: System76 Support
---

### Post by jpoRS on 2011-08-19
Hello-

Just upgraded from Karmic to Natty (I know, but stuff came up ... for three years) on my Panp4i.  Seamless upgrade so far, BUT there is a small fly in the ointment.

On all other releases of Firefox, when a common website name was typed into the address bar, it would go direct to the site.  Now when I type in the address bar it simply shows a Google search for what I typed.

Example- Previously, when I typed
```
ubuntu forums
```
into the address bar, I would automatically go straight to
```
http://ubuntuforums.org/
```
Now, when I but the same information in the address bar I get
```
https://encrypted.google.com/search?client=ubuntu&channel=fs&q=ubuntu+forums&ie=utf-8&oe=utf-8
```
*I use the HTTPS Everywhere plugin, thus the encrypted URL*

Is there a known way to revert to the old option, that is to say common website names lead direct to the website?

Thanks,
jim

---

### Post by arzali on 2011-08-19
Hi jpoRS,

This wotks for me (FF6)

open about:config > search for keyword.URL > add "http://www.google.com/search?ie=UTF-8&sourceid=navclient&gfns=1&q="   without quotes as string

---

### Post by jpoRS on 2011-08-20
You're suggesting I set up a new preference called keyboard.url, right?

---

### Post by arzali on 2011-08-20
just like this

[[IMG]http://uppix.net/d/b/0/9d10495fe87bf59b8f9a90d0493d1t.jpg[/IMG]]("http://uppix.net/d/b/0/9d10495fe87bf59b8f9a90d0493d1.png")

---

### Post by lovinglinux on 2011-08-20
> **jpoRS said:**
> You're suggesting I set up a new preference called keyboard.url, right?

It is *keyword.url* not *keyboard.url*. Alternatively, you can install [Browse by Name]("https://addons.mozilla.org/en-US/firefox/addon/222531/") extension.

---

### Post by jpoRS on 2011-08-20
> **lovinglinux said:**
> It is *keyword.url* not *keyboard.url*. Alternatively, you can install [Browse by Name]("https://addons.mozilla.org/en-US/firefox/addon/222531/") extension.

Yeah, typo on my part.

Worked perfect! Thanks!

---

