---
title: "Epiphany + WebKit"
date: 2007-10-14
forum: The Cafe
---

### Post by bruce89 on 2007-10-14
I have made an Epiphany package based off of Debian's 2.20.0-3 package. 

It has a WebKit package (epiphany-webkit) built.

If I get accepted into the launchpad beta testers team, I'll upload this to my PPA.

Gutsy only.

---

### Post by undine on 2007-10-14
Does epiphany-webkit bring any advantages over the current Gecko backend?

---

### Post by bruce89 on 2007-10-14
> **undine said:**
> Does epiphany-webkit bring any advantages over the current Gecko backend?

Not really, it's really for testing purposes ATM.

I've found out that extensions no longer work, I'll look into this.

---

### Post by mostwanted on 2007-10-14
Cool, might try it out. I switched to Epiphany starting with Gutsy and it really is a great browser.

---

### Post by bruce89 on 2007-10-14
Gecko:
[ATTACH]46346[/ATTACH]
WebKit:
[ATTACH]46347[/ATTACH]

WebKit has proper widgets, but the port is in its early days. It also uses non MS fonts for some reason.

You can see the limitations at the moment, the title is wrong, the progressbar is broken and the Back/Forward buttons don't work.

---

### Post by bruce89 on 2007-10-15
I know it's mean to bump your own posts, but  the packages are at [https://launchpad.net/~bruce89/+archive](https://launchpad.net/~bruce89/+archive)

They aren't compiled yet, but they will be reasonably soon.

---

### Post by mostwanted on 2007-10-15
> **bruce89 said:**
> I know it's mean to bump your own posts, but  the packages are at [https://launchpad.net/~bruce89/+archive](https://launchpad.net/~bruce89/+archive)

They aren't compiled yet, but they will be reasonably soon.

Thanks.

---

### Post by yatt on 2007-10-16
I (on Debian Sid) have found that Epiphany + Webkit only renders properly after the page has been loaded in Epiphany + Gecko.

Is it that way on Ubuntu, too?

---

