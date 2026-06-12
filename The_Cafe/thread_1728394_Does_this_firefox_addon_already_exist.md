---
title: "Does this firefox addon already exist?"
date: 2011-04-13
forum: The Cafe
---

### Post by Dustin2128 on 2011-04-13
I wanted to work on my first firefox addon (if this doesn't exist already; I couldn't find it): a url lengthener :D. Basically it just helps to make sure tinyrul, goo.gl, etc. stuff doesn't point to... certain disturbing images (to quote xkcd, if you don't get it, don't google it). It seems very simple though, is there an addon for this already?

---

### Post by Mmmbopdowedop on 2011-04-13
If a url points to something most people don't want to see; i'd click it just to see what it is, dependant if it is or not.

Just out of curiousity.

I'm not sure you described it fully?

You mean, instead of tinyurl/?????? it shows the real link?

Meh, i'd still click it. :)

---

### Post by Enigmapond on 2011-04-13
I don't think there is an add-on. Tinyurl has a preview if that helps. I don't know about the others.

[http://tinyurl.com/preview.php?num=xxxxx](http://tinyurl.com/preview.php?num=xxxxx) (xxxxx = the tinyurl)

---

### Post by Dustin2128 on 2011-04-13
It's for all url shorteners, I figure I just write a small program that traces where the link goes and displays the full url on mouse over rather than just the shortened one.

---

### Post by CraigPaleo on 2011-04-13
> **Dustin2128 said:**
> It's for all url shorteners, I figure I just write a small program that traces where the link goes and displays the full url on mouse over rather than just the shortened one.

One exists. You may be able to improve on it. It also needs to be updated for FF4  [LongURL]("https://addons.mozilla.org/en-us/firefox/addon/long-url-please-mod/")

---

### Post by Dustin2128 on 2011-04-13
> **CraigPaleo said:**
> One exists. You may be able to improve on it. It also needs to be updated for FF4  [LongURL]("https://addons.mozilla.org/en-us/firefox/addon/long-url-please-mod/")
Thanks, I've started work on a firefox 4 version, but it looks like I need to brush up big time on my javascript.

---

### Post by lovinglinux on 2011-04-13
> **Dustin2128 said:**
> Thanks, I've started work on a firefox 4 version, but it looks like I need to brush up big time on my javascript.

Before starting working on it, I would contact the original author. The extension is still under active development and was updated on March 15. Additionally, it doesn't seem to have an open source license.

There are other similar extensions without FF 4 support:

[https://addons.mozilla.org/en-US/firefox/addon/longurl-mobile-expander/](https://addons.mozilla.org/en-US/firefox/addon/longurl-mobile-expander/)
[https://addons.mozilla.org/en-US/firefox/addon/xpndit-short-url-expander/](https://addons.mozilla.org/en-US/firefox/addon/xpndit-short-url-expander/)
[https://addons.mozilla.org/en-US/firefox/addon/detiny-short-url/](https://addons.mozilla.org/en-US/firefox/addon/detiny-short-url/)
[https://addons.mozilla.org/en-US/firefox/addon/therealurl/](https://addons.mozilla.org/en-US/firefox/addon/therealurl/)
[https://addons.mozilla.org/en-US/firefox/addon/expand-short-url/](https://addons.mozilla.org/en-US/firefox/addon/expand-short-url/)

---

### Post by 3177 on 2011-04-13
> **lovinglinux said:**
> Before starting working on it, I would contact the original author. The extension is still under active development and was updated on March 15. Additionally, it doesn't seem to have an open source license.

???
I didn't think linux firefox could install proprietary add-ons.

---

### Post by lovinglinux on 2011-04-14
> **3177 said:**
> ???
I didn't think linux firefox could install proprietary add-ons.

Why not?

---

### Post by 3177 on 2011-04-14
Ive tried to install proprietary add-ons in ubuntu firefox 4, but when I search for them, it says "only for windows", or doesnt show at all. Ex. silverlight(witch my wife needs for online classes.)

---

### Post by lovinglinux on 2011-04-14
> **3177 said:**
> Ive tried to install proprietary add-ons in ubuntu firefox 4, but when I search for them, it says "only for windows", or doesnt show at all. Ex. silverlight(witch my wife needs for online classes.)

Oh I see. That is not the real reason. You couldn't install because the add-on was developed only for Windows. This happens when it relies on OS-specific features, not because of license. For instance I develop some open-source add-ons that works only in Linux and others that works on any OS. Depends how the extension was developed and depends if the author specifies compatibility in the extension installation file.

Plugins like Silverlight are more complicated and need to be OS specific.

---

### Post by lovinglinux on 2011-04-14
BTW, your wife can install Moonlight, which is the Silverlight for Linux.

[http://www.go-mono.org/moonlight/prerelease.aspx](http://www.go-mono.org/moonlight/prerelease.aspx)

---

