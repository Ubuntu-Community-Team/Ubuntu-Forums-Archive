---
title: "Dunno where to put, but Can you turn a Firefox patch into an Extension?"
date: 2007-07-31
forum: The Cafe
---

### Post by cookies on 2007-07-31
I dunno where to put this, so I'll stick it here. If it is in the wrong place, mods please move it.

Okay, so there is a Patch for Firefox and enabling Windowless Mode (WMODE=transparent, so that, for example, JavaScript menus can appear over flash on sites like [http://www.adobe.com](http://www.adobe.com)) in Linux, and that patch is here:
[https://bugzilla.mozilla.org/attachment.cgi?id=169650](https://bugzilla.mozilla.org/attachment.cgi?id=169650)

Just theoretically, (or maybe even really) can we turn this patch into an extension so a lowly non-developer like me can apply it?

---

### Post by bread eyes on 2007-08-01
Yes

---

### Post by cookies on 2007-08-01
Ookaayyy, so that's great! But I'm not a developer....

Think there's anyone who would like/wants to do this? (I'm pretty sure there must be, it's an annoying issue)

---

### Post by DoktorSeven on 2007-08-01
Actually, extensions can't change core Firefox window rendering, they're just Javascript stuff that build off of existing Firefox stuff, right?

The patch looks like it changes core rendering issues, and so I don't think an extension can handle it.

---

### Post by cookies on 2007-08-01
Well I've seen extension do things like implement XForms:
[https://addons.mozilla.org/en-US/firefox/addon/824](https://addons.mozilla.org/en-US/firefox/addon/824)

---

### Post by DoktorSeven on 2007-08-01
I could be wrong, of course, but it seems that implements new functionality  (somehow, possibly you can create a library file to call).  Changing existing functionality hard-coded in the Mozilla/Firefox core, I would think, would be harder.

As I said, I could be wrong, but I'd think it'd be easier to wait on someone integrating the patch into mainline or creating a separate package for it.  I could try, but the resulting package wouldn't be Ubuntu-friendly (I compile my own version of Firefox -- the "Bon Echo" non-branded version -- and put it in a simple tarball).

---

### Post by cookies on 2007-08-01
> **DoktorSeven said:**
> I could be wrong, of course, but it seems that implements new functionality  (somehow, possibly you can create a library file to call).  Changing existing functionality hard-coded in the Mozilla/Firefox core, I would think, would be harder.

As I said, I could be wrong, but I'd think it'd be easier to wait on someone integrating the patch into mainline or creating a separate package for it.  I could try, but the resulting package wouldn't be Ubuntu-friendly (I compile my own version of Firefox -- the "Bon Echo" non-branded version -- and put it in a simple tarball).


Meh, hey, what the hell, try it.

As for the developers, they said they couldn't make it into Gecko 1.9, which makes NO sense since we have the patch right here!

---

### Post by DoktorSeven on 2007-08-01
Well, I compiled it but it didn't fix anything; according to the Mozilla bug the latest Flash plugin version (which I have) is supposed to support it.  Yet on adobe's site (and others) the Flash still draws itself over the menus that pop up.

Apparently Konqueror does it right, though, verified in 3.5.6 here (Feisty).

---

### Post by cookies on 2007-08-01
> **DoktorSeven said:**
> Well, I compiled it but it didn't fix anything; according to the Mozilla bug the latest Flash plugin version (which I have) is supposed to support it.  Yet on adobe's site (and others) the Flash still draws itself over the menus that pop up.

Apparently Konqueror does it right, though, verified in 3.5.6 here (Feisty).

Yeah, Konqueror does do it right. Using 3.5.7 here.

What about the latest Adobe Beta Flash:
[http://labs.adobe.com/downloads/flashplayer9.html](http://labs.adobe.com/downloads/flashplayer9.html)

It uses XEmbed and GTK.

---

### Post by DoktorSeven on 2007-08-01
No improvement.  Ah well, worth a shot.

---

### Post by cookies on 2007-08-13
Sorry for the Bump, but the Latest Firefox Gran Pardiso Alpha 7 has support for WMODE, now Adobe has to make Flash Player Linux do the same, then we'll be all good in Firefox 3. 

Just thought I'd point it out.

---

