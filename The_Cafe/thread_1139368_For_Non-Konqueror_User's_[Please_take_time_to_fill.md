---
title: "For Non-Konqueror User's [Please take time to fill this]"
date: 2009-04-27
forum: The Cafe
---

### Post by GnuBoi on 2009-04-27
If you don't like Konqueror or find something lacking in it and do not
use konqueror. Please take time to fill this survey and help making
konqueror a better browser...
[URL="http://spreadsheets.google.com/viewform?formkey=ckpvbXFCNnF6R3ZtREVOSFMzSHcxcnc6MA.."]
http://spreadsheets.google.com/viewform?formkey=ckpvbXFCNnF6R3ZtREVOSFMzSHcxcnc6MA..[/URL]

Regards,
Ujjwol

Ps: Even Konqueror user's fill the survey to help improving Konqueror

---

### Post by Skripka on 2009-04-27
FYI-

On Arch, there is an excellent Webkit-svn backend now available via AUR.  It was just updated tonight.  Makes Konqueror fully compatible with everything out there, and as fast as Midori/Arora.

KHTML is one of Konqueror's main problems-stop using KHTML and it is quite good.

---

### Post by CraigPaleo on 2009-04-27
> **Skripka said:**
> FYI-

On Arch, there is an excellent Webkit-svn backend now available via AUR.  It was just updated tonight.  Makes Konqueror fully compatible with everything out there, and as fast as Midori/Arora.

KHTML is one of Konqueror's main problems-stop using KHTML and it is quite good.

That's certainly good news! I checked Jaunty backports and prerelease but didn't see it. I'll try finding a deb for it. 

Maybe we should hold off on filling this out until we all have the Webkit backend.

---

### Post by cookieforyou on 2009-04-27
My online banking webpage here is South Africa produces nothing but a blank screen AFTER successfully logging in (I get the sms on my cellphone indicating that I have logged in).  Unusable.  Works fine with Firefox.  This same blank screen problem occurs with Opera too.

---

### Post by Skripka on 2009-04-27
> **CraigPaleo said:**
> That's certainly good news! I checked Jaunty backports and prerelease but didn't see it. I'll try finding a deb for it. 

Maybe we should hold off on filling this out until we all have the Webkit backend.

I don't know when or if it will be available for Jaunty or *buntu backports-I only know Arch and AUR

For your reference, the package in the AUR is called webkitkde-svn 957817-1.

You can get the source tarball on this page: [http://aur.archlinux.org/packages.php?ID=25929](http://aur.archlinux.org/packages.php?ID=25929)

In theory it should compile.  Be sure to use whatever command to make it a package, and not just loose source code-for your system...no warranties of it working of course.  Once it compiles, and if it works, you'll need to change Konqueror's default "view" from KHTML to Webkit to default to it.

---

### Post by CraigPaleo on 2009-04-27
You know what? It is in the repos after all: [webkitkde]("apt:webkitkde") After installing it, go to a webpage in Konqueror (you must visit a webpage first or the "view mode" option will not be available), go to view, view mode, and chose "Webkit." I can actually see Yahoo.com with it! 

I've noticed that the above must be done every single time a page is viewed. Skripka, how did you make it default?

---

### Post by Skripka on 2009-04-27
> **CraigPaleo said:**
> You know what? It is in the repos after all: [webkitkde]("apt:webkitkde") After installing it, go to a webpage in Konqueror (you must visit a webpage first or the "view mode" option will not be available), go to view, view mode, and chose "Webkit." I can actually see Yahoo.com with it! 

I've noticed that the above must be done every single time a page is viewed. Skripka, how did you make it default?

In a Terminal type:

```

keditfiletype text/html

```

click on the "Embedded tab", and in the listing, move "Webkit(webkitpart)" to the very top to make it default.

...some Konqueror functionality is absent in Webkit vs KHTML, such as adding RSS pages to Akregator while in Konqueror-but the web works great...Flash just works, as does Gmail etc.

---

### Post by CraigPaleo on 2009-04-27
> **Skripka said:**
> In a Terminal type:

```

keditfiletype text/html

```

click on the "Embedded tab", and in the listing, move "Webkit(webkitpart)" to the very top to make it default.

...some Konqueror functionality is absent in Webkit vs KHTML, such as adding RSS pages to Akregator while in Konqueror-but the web works great...Flash just works, as does Gmail etc.

That has worked. Thanks.

---

