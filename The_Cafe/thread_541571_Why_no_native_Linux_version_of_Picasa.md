---
title: "Why no native Linux version of Picasa?"
date: 2007-09-03
forum: The Cafe
---

### Post by FuturePilot on 2007-09-03
Call me slow for just discovering this or call me smart if you didn't know this. Whatever.
Anyways, I just found out that the Linux version of Google's Picasa isn't a true native Linux app. It's a slightly modified Windows version that runs on top of a heavily modified version of Wine. Why did they do that? I don't understand the logic behind it especially considering that the Linux versions of Google Earth and Google Desktop are both true native Linux apps. I feel very deceived right now:-&

---

### Post by Fbot1 on 2007-09-03
It's still a native app.

---

### Post by sumguy231 on 2007-09-03
> Why did they do that?
Because it was easier than a full port. It's still native by conventional definitions of the term.

---

### Post by RomeReactor on 2007-09-03
> **FuturePilot said:**
> Call me slow for just discovering this or call me smart if you didn't know this. Whatever.
Anyways, I just found out that the Linux version of Google's Picasa isn't a true native Linux app. It's a slightly modified Windows version that runs on top of a heavily modified version of Wine. Why did they do that? I don't understand the logic behind it especially considering that the Linux versions of Google Earth and Google Desktop are both true native Linux apps. I feel very deceived right now:-&

Yeah, I noticed that a while back too. It's obvious once you see how the cursor changes when you move it from outside the application to inside its window. I tried both Picasa and Acrobat and found them to be too slow for my taste. F-Spot and Evince are just fine for my needs.

---

### Post by FuturePilot on 2007-09-03
Yeah, I like F-Spot too.

---

### Post by psychicist on 2007-09-03
The problem with Google's Linux applications is that they're closed source and x86 only. So if I want to run any of them on my MIPS or SPARC machines I can't. This is a reason for me to do without them on x86 as well. In the case of Picasa it's not only non-native but suffers from quirks as well. Also it hadn't been updated for a while the last time I tried to run it, so the native Windows version had had a couple more versions released.

In this day and age Linux and open source applications are more important than some closed source, architecture-specific ones that may not be around in 5 years anymore and should be avoided unless they currently are critical to the company's or individual's existence.

---

### Post by Spr0k3t on 2007-09-03
Google did not develop Picasa.  This was an application they acquired in a business merge.  After they acquired this application, they submitted quite a few improvements to WINE to be able to get the application running as smooth as it does.  Kudos to them for accomplishing what they have so far.

---

### Post by jcconnor on 2007-09-03
Just saw an article on Slashdot where Google is announcing some native Linux apps later this year.  Linked article [ here]("http://techrythm.com/index.php/new-google-linux-apps-coming-soon/").  

Hopefully this will mean a non-Wine version of Picassa (though the Wine version works great for me!!)

John

---

### Post by stmiller on 2007-09-03
Native Picasa would be great. Not everyone here is running Ubuntu on x86 or X86_64. :popcorn:

---

### Post by Anthem on 2007-09-03
Yeah, I think people are misunderstanding what "native" means.

There's no reason for them to do GTK or QT, because either one means half their audience is using a "non-native" version anyway.  So they used the wine libs, which is a toolkit just like GTK or QT is a toolkit.

---

### Post by FuturePilot on 2007-09-03
> **Anthem said:**
> Yeah, I think people are misunderstanding what "native" means.

There's no reason for them to do GTK or QT, because either one means half their audience is using a "non-native" version anyway.  So they used the wine libs, which is a toolkit just like GTK or QT is a toolkit.

Yes, I see where you're coming from, but running a Windows binary on top of a compatibility layer is not my interpretation of "native"
If you look at what's inside the deb it's mostly dlls and other Windows binaries. I might as well install Wine and then install the Windows version of Picasa. I just don't see what their point in doing that was. I would really like to see a native Linux version of Picasa.

---

