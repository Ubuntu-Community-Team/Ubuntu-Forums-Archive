---
title: "New Firefox 1.0.4 Backport Available"
date: 2005-05-24
forum: Ubuntu Backports
---

### Post by jdong on 2005-05-24
I've backported Breezy's Firefox 1.0.4 (before, I applied old Ubuntu patches to official source).


Note that it's now compiled with GCC 4.0 (as specified by the build scripts explicitly, so I complied!), and is called "firefox" instead of "mozilla-firefox"


This is quite interesting, as it marks the **first GCC 4.0 build to hit Backports**. :)

My initial testing shows it works, and that it's snappier!

---

### Post by NateC on 2005-05-24
Yay... firefox now opens in 1.5 seconds :)

---

### Post by jdong on 2005-05-24
That's not the only point of GCC 4.0.... From a security standpoint, Firefox will be **immune** to buffer/stack overflow attacks.

---

### Post by ow50 on 2005-05-24
Just upgraded, seems to work fine. One problem with the name update though, I had to uninstall libdevhelp-1-0. For some reason, it doesn't accept firefox providing mozilla-firefox and wants to install mozilla-firefox. Not that I'd necessarily need libdevhelp-1-0, I can't even remember why I have it.

---

### Post by vassalle on 2005-05-24
[QUOTE=ow50]Just upgraded, seems to work fine. One problem with the name update though, I had to uninstall libdevhelp-1-0. For some reason, it doesn't accept firefox providing mozilla-firefox and wants to install mozilla-firefox. Not that I'd necessarily need libdevhelp-1-0, I can't even remember why I have it.[/QUOTE]
 cant find it.. :(

---

### Post by Ali_Baba on 2005-05-24
I updated firefox too.It opens really fast now  :grin: Will be great if all gcc 4.0 applications are as fast as this.

---

### Post by jdong on 2005-05-24
**sudo apt-get install firefox**

For some reason, APT doesn't understand this transition. I don't know how to force it.

---

### Post by vassalle on 2005-05-24
[QUOTE=jdong]**sudo apt-get install firefox**

For some reason, APT doesn't understand this transition. I don't know how to force it.[/QUOTE]
 dont mind me.. im just plain stupid i guess... didnt unmark the backports-staging in my sources.list.. managed to installed it tho.. ;)

---

### Post by Technoviking on 2005-05-24
We may want a dummy transition package for mozilla-firefox, so ubuntu-desktop does not have to be uninstalled.

Mike

---

### Post by jdong on 2005-05-24
[QUOTE=Ali_Baba]I updated firefox too.It opens really fast now  :grin: Will be great if all gcc 4.0 applications are as fast as this.[/QUOTE]

From my initial testing of Fedora, **it seems that way :)**

---

### Post by dodongo on 2005-05-24
[QUOTE=jdong]That's not the only point of GCC 4.0.... From a security standpoint, Firefox will be **immune** to buffer/stack overflow attacks.[/QUOTE]

Just out of curiosity, **why** is the C compiler so much smarter all of a sudden?  It would seem to me (as someone who only knows enough about C to break things) that this type of thing should require a lot of work on the part of the developer.  Is GCC 4.0 just more strict about how it allocates memory space?

And if you don't really want to answer, I'd settle for an informative URL :)

Thanks for the great work, too!

---

### Post by jdong on 2005-05-25
[http://www.google.com/search?hl=en&lr=&client=firefox&rls=org.mozilla%3Aen-US%3Aunofficial&q=mudflap+gcc&btnG=Search](http://www.google.com/search?hl=en&lr=&client=firefox&rls=org.mozilla%3Aen-US%3Aunofficial&q=mudflap+gcc&btnG=Search)

[http://www.google.com/search?hl=en&lr=&client=firefox&rls=org.mozilla%3Aen-US%3Aunofficial&q=gcc+FORTIFY_SOURCE&btnG=Search](http://www.google.com/search?hl=en&lr=&client=firefox&rls=org.mozilla%3Aen-US%3Aunofficial&q=gcc+FORTIFY_SOURCE&btnG=Search)

---

### Post by jdong on 2005-05-25
[QUOTE=Mike Basinger]We may want a dummy transition package for mozilla-firefox, so ubuntu-desktop does not have to be uninstalled.

Mike[/QUOTE]
great suggestion.

---

### Post by man.life on 2005-05-25
Will this new firefox work with mozilla-firefox-locale-*? Or do we have to wait for a firefox-locale-* backport?

---

### Post by jdong on 2005-05-25
Hmm, the name change might warrant the need for a new locales backport, but I don't even see them present in Breezy at the moment.

---

### Post by jasplund on 2005-05-25
[QUOTE=man.life]Will this new firefox work with mozilla-firefox-locale-*? Or do we have to wait for a firefox-locale-* backport?[/QUOTE]

I was also wondering about this. Is the namechange really necessary?

---

### Post by dlpfmVfH on 2005-05-25
[QUOTE=jasplund]I was also wondering about this. Is the namechange really necessary?[/QUOTE]
 I'm dutch, and installed the new firefox, it's menu is in dutch, so are the dialogs

so guessing it works, with the locale

---

### Post by jdong on 2005-05-25
[QUOTE=jasplund]I was also wondering about this. Is the namechange really necessary?[/QUOTE]
This happened in Breezy, so it's out of my control.

From the looks, all the "mozilla-firefox-dev"-dependent packages may suffer from incompatibility thanks to this change.


Please see if , for example, you can get epiphany to work with this backport.

---

### Post by man.life on 2005-05-25
Much faster and it detects the language pack. That menu entry is annoying, they should have left it as it was and not rename it to just "Firefox".  [-X

---

### Post by ow50 on 2005-05-25
I can try crafting transitional dummy packages.

I think we need transitional dummy packages for all the packages (firefox, firefox-gnome-support, firefox-dom-inspector, firefox-dev). There's already a transitional dummy package for firefox-dev in the breezy source. Also, I think the firefox-* packages should thereby only conflict with versions < 1.0.4 of mozilla-firefox-* packages.

---

### Post by ow50 on 2005-05-25
[QUOTE=jdong]From the looks, all the "mozilla-firefox-dev"-dependent packages may suffer from incompatibility thanks to this change.[/QUOTE]
But that has a transitional dummy package. Doesn't that solve the dependencies?

[QUOTE=jdong]Please see if , for example, you can get epiphany to work with this backport.[/QUOTE]
Epiphany works.

---

### Post by fluideye on 2005-05-26
> I've backported Breezy's Firefox 1.0.4 (before, I applied old Ubuntu patches to official source).


Note that it's now compiled with GCC 4.0 (as specified by the build scripts explicitly, so I complied!), and is called "firefox" instead of "mozilla-firefox" 
I have added the backports and am unable to find the firefox package.  Tried apt-get and synaptic and no go.  Is this still available?

---

### Post by jdong on 2005-05-26
It's in the -staging area now. This backport will need time for testing because of the potential issues introduced by the new compiler and the new name.

---

### Post by fluideye on 2005-05-26
> It's in the -staging area now. This backport will need time for testing because of the potential issues introduced by the new compiler and the new name. 
Thanks for the heads up.

---

