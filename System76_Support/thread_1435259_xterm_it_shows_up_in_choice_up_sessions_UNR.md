---
title: "xterm?? it shows up in choice up sessions UNR"
date: 2010-03-21
forum: System76 Support
---

### Post by black_ice=cream on 2010-03-21
i just removed xfce from synaptic and it worked perfectly but now "xterm" shows up in list of sessions, along with GNOME and failsafeGNOME. What is xterm?! Why did it appear after I removed xubuntu?

---

### Post by thomasaaron on 2010-03-22
I think it's just a terminal emulator for Xubuntu. (Just like Accessories > Terminal in UNR.)

Not sure why it didn't un-install when you removed xubuntu.

---

### Post by snowpine on 2010-03-22
xterm is the X windows system terminal. It has nothing to do with Xubuntu. :)

---

### Post by HotShotDJ on 2010-03-22
> **black_ice=cream said:**
>  What is xterm?! Why did it appear after I removed xubuntu?Try this: [http://www.google.com/search?q=xterm&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a](http://www.google.com/search?q=xterm&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a)

Also, I have always had an xterm option in the session menu and I've never installed xubuntu. I double checked before posting this, and lo and behold, there it was as one of the options -- and I've only ever had straight Ubuntu on this computer.  My guess is that you only noticed it after trying Xubuntu.

---

### Post by black_ice=cream on 2010-03-22
would it just be a CLI if I booted into it?

---

### Post by isantop on 2010-03-22
I believe that the ubuntu-desktop package depends on xterm. Ditto for the UNR desktop package.

EDIT: Confirmed. running:
```

sudo apt-cache depends ubuntu-desktop | grep xterm
```

returns:
```
Depends: xterm
```

Same for package ubuntu-netbook-remix.


> **black_ice=cream said:**
> would it just be a CLI if I booted into it?

No. If you log in to an xterm session from GDM, it will start a basic graphical session (without gnome) and open xterm in a window. (Try pressing alt-f2 and running "xterm").

You can use a CLI by pressing Ctrl-Alt-F1 at any time. You can get back to GNOME with Ctrl-Alt-F7.

---

