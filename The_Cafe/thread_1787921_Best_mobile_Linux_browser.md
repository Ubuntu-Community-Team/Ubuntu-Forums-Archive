---
title: "Best mobile Linux browser"
date: 2011-06-21
forum: The Cafe
---

### Post by ki4jgt on 2011-06-21
I have a hacked Linux hand held, it's running Debian SID. The included browser is links. The screen is around 2 inches big, Is there a better browser than links for this? Something like Opera for mobile? I looked at their site, but it's only for androids and apples :-) Since I am neither metal nor organic, I was wondering on what browsers you guys would install. I'd prefer if it was easy to navigate in the pages. Flash is not a concern, RAM is only 300 megs and swap is 512, so I don't plan on doing flash on it any time soon.

---

### Post by NightwishFan on 2011-06-21
I like text based browsers such as links, elinks, w3m etc. I know some of them support graphics but I am not sure which.

---

### Post by NightwishFan on 2011-06-21
You could also try Firefox Mobile:
[http://ftp.mozilla.org/pub/mozilla.org/mobile/releases/4.0.1/linux-i686/fennec-4.0.1.en-US.linux-i686.tar.bz2](http://ftp.mozilla.org/pub/mozilla.org/mobile/releases/4.0.1/linux-i686/fennec-4.0.1.en-US.linux-i686.tar.bz2)

---

### Post by Simon17 on 2011-06-21
Mercy.

[http://smashindex.blogspot.com/p/current-projects.html](http://smashindex.blogspot.com/p/current-projects.html)

---

### Post by ki4jgt on 2011-06-21
> **NightwishFan said:**
> You could also try Firefox Mobile:
[http://ftp.mozilla.org/pub/mozilla.org/mobile/releases/4.0.1/linux-i686/fennec-4.0.1.en-US.linux-i686.tar.bz2](http://ftp.mozilla.org/pub/mozilla.org/mobile/releases/4.0.1/linux-i686/fennec-4.0.1.en-US.linux-i686.tar.bz2)

Just tried Fennec. . . unable to run executable file

tried ./fennec didn't work using root and user.

---

### Post by NightwishFan on 2011-06-21
Works on Debian 6 Stable x64. Any error messages?

---

### Post by ki4jgt on 2011-06-21
> **NightwishFan said:**
> Works on Debian 6 Stable x64. Any error messages?

Nope, just unable to execute. . . As for Mercy, no webkit :-( Plenty of Python, but no webkit

---

### Post by NightwishFan on 2011-06-21
You arent able to use apt? Just install the webkit packages from sid.
```
apt-get install python-webkit
```

---

### Post by Legendary_Bibo on 2011-06-21
How are you neither metal nor organic?

---

### Post by ki4jgt on 2011-06-21
> **NightwishFan said:**
> You arent able to use apt? Just install the webkit packages from sid.
```
apt-get install python-webkit
```

The repos are broken :-( Libwebkit and about 10 others are not available. I'm tried updating them. The OS is deprecated.

---

### Post by ki4jgt on 2011-06-21
> **Legendary_Bibo said:**
> How are you neither metal nor organic?

I was hoping no one would catch that :-)

---

### Post by Legendary_Bibo on 2011-06-21
> **ki4jgt said:**
> The repos are broken :-( Libwebkit and about 10 others are not available. I'm tried updating them. The OS is deprecated.

wget

---

### Post by NightwishFan on 2011-06-21
Ah it must be something custom then. If it were sid it would be quite modern.

What is the kernel and your sources?
```
uname -a
```

```
less /etc/apt/sources.list
```

---

### Post by Macskeeball on 2011-06-21
> **Legendary_Bibo said:**
> How are you neither metal nor organic?

By metal, he's referring to Verizon's robot advertising for their Droid phones. By organic, he's referring to Apple and their iOS.

---

### Post by NightwishFan on 2011-06-21
> **Simon17 said:**
> Mercy.

[http://smashindex.blogspot.com/p/current-projects.html](http://smashindex.blogspot.com/p/current-projects.html)

Oh cool haha. I am technically the original author of Mercy. Interesting.
[QUOTE="Mercy Source Code"]
# Mercy Web Browser is a spin off of Virgil's Web Browser.
# ([http://tinyurl.com/4a7ch2w](http://tinyurl.com/4a7ch2w)) It's original
# code has allowed the creation of this great program.
[/QUOTE]

---

### Post by ki4jgt on 2011-06-21
Due to game on other thread. . . don't want to answer that, but here goes. Linux OpenZipit 2.6.29. Yes, it is custom (for the device) There are literally dozens of OSs for this device, but all of them are deprecated :-( except for one based entirely on the terminal. I love the idea of a terminal OS, but not on a handheld device. The OS, I have is here: [http://zipit.rootnexus.org/files/Z2-USERLAND/RC1-PRE2/](http://zipit.rootnexus.org/files/Z2-USERLAND/RC1-PRE2/)

Sources
```

#deb http://www.emdebian.org/grip/ lenny main contrib non-free
#deb http://ftp.us.debian.org/debian/ lenny main contrib non-free
deb http://http.us.debian.org/debian unstable main contrib non-free

#deb http://www.emdebian.org/grip/ testing main contrib non-free
#deb http://ftp.us.debian.org/debian/ testing main contrib non-free
#deb http://ftp.us.debian.org/debian/ unstable main contrib non-free
deb http://www.emdebian.org/grip/ sid main 


#deb http://ports.ubuntu.com/ lucid main multiverse restricted universe

```

I'm updating the kernel. I've already updated the libertas firmware.

---

### Post by NightwishFan on 2011-06-21
I see, you have a very limited selection for packages in emdebian, but you also have regular sid enabled. I really can't say why it won't work without seeing it myself.

---

