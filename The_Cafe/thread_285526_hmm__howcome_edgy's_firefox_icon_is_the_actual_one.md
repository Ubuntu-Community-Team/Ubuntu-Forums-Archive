---
title: "hmm  howcome edgy's firefox icon is the actual one, not the little world thingie?"
date: 2006-10-26
forum: The Cafe
---

### Post by user1397 on 2006-10-26
i thought that they were going to use a different name, different logo and everything, but in edgy, the real firefox logo is used by default.  what's up with that?

---

### Post by qamelian on 2006-10-26
Read here for the answer: [http://cbeard.typepad.com/mozilla/2006/10/mozilla_and_ubu.html](http://cbeard.typepad.com/mozilla/2006/10/mozilla_and_ubu.html)

---

### Post by mushroom on 2006-10-26
They're complying with Mozilla's wishes as far as I know, which is cool. Sometimes practicality needs to take precedence over philosophy, at least with something this trifling. Now if Ubuntu would at least provide the option to install proprietary codecs and such with full warning of why they're not included by default (a multiverse metapackage that downloads the stuff from the web would satisfy me), it would make everything that much simpler. Not that that has anything to do with the question, I'm just thinking aloud...

---

### Post by IYY on 2006-10-26
Seems to me that the Firefox guys just got a bit scared. They know that Ubuntu, unlike Debian, is the distro that new users flock to, and they don't want to lose brand recognition.

---

### Post by mushroom on 2006-10-26
Nah, Mozilla just doesn't want their brand on Firefox builds incorporating unofficial patches and Debian wasn't willing to do that, but Ubuntu is, apparently. This really shouldn't be grounds to make Mozilla out to be bad guys; Firefox is possibly the most important piece of software in the FLOSS movement, and it needs to be avidly protected for the time being.

---

### Post by Polygon on 2006-10-27
i guess we talked to mozill and ubuntu/mozilla came to an agreement

i would still like to see iceweasel as an package in the repos though, i find it to be much faster then firefox (well.. at least ff 1.7.0.7, version 2 is pretty fast now)

---

### Post by Wolki on 2006-10-27
Is there an easy way to remove the firefox icon completely from the system, without breaking anything?

I don't really want to switch to debian over this, as I've grown used to Ubuntu and its speedy inclusion of new GNOME.

---

### Post by user1397 on 2006-10-27
> **Wolki said:**
> Is there an easy way to remove the firefox icon completely from the system, without breaking anything?

I don't really want to switch to debian over this, as I've grown used to Ubuntu and its speedy inclusion of new GNOME.yea just press ALT+F2, and then type **gksudo nautilus**.  then navigate to /usr/share/pixmaps/  and try to find the mozilla one.  you can delete it if you want, and then you can choose the more familiar default icon, or whatever you want.

---

### Post by MedivhX on 2006-10-27
It's better that way. I like the Firefox logo, not some ugly-drewn globe...

---

### Post by user1397 on 2006-10-27
> **MedivhX said:**
> It's better that way. I like the Firefox logo, not some ugly-drewn globe...o yea me too, i was just wondering cause i originally thought that iceweasel was going to be used in 6.10, i didn't keep up too much with it as u can see.

---

### Post by MedivhX on 2006-10-27
I really don't like the whole Debian's idea about IceWeasel and IceDove... It's a kind of theft...

---

### Post by shining on 2006-10-27
> **mushroom said:**
> Nah, Mozilla just doesn't want their brand on Firefox builds incorporating unofficial patches and Debian wasn't willing to do that, but Ubuntu is, apparently. This really shouldn't be grounds to make Mozilla out to be bad guys; Firefox is possibly the most important piece of software in the FLOSS movement, and it needs to be avidly protected for the time being.

Every comments I saw trying to defend mozilla always made it much worse. It's apparently still the case.

I originally had nothing agaisnt ubuntu getting an agreement with mozilla, but all these sad comments from users who apparently don't know anything about the issue just makes me regret they did.

---

### Post by user1397 on 2006-10-27
> **MedivhX said:**
> I really don't like the whole Debian's idea about IceWeasel and IceDove... It's a kind of theft...hmmm...IMO it isn't really a kind of theft, since the source code's available, is more like a fork made out of spite for mozilla.but i think it was a bad decision from debian, firefox is one of the most important and basic new user program need for a distro, IMO

---

### Post by Wolki on 2006-10-27
> **erik1397 said:**
> yea just press ALT+F2, and then type **gksudo nautilus**.  then navigate to /usr/share/pixmaps/  and try to find the mozilla one.  you can delete it if you want, and then you can choose the more familiar default icon, or whatever you want.

That's not enough, the icon is also in some other places. Too busy to figure it out right now, might have a look later.

---

### Post by user1397 on 2006-10-27
> **Wolki said:**
> That's not enough, the icon is also in some other places. Too busy to figure it out right now, might have a look later.
well when you have time, i guess you could go to places > search, and search for all instances of the firefox logo, and one by one delete them inside a root nautilus.  (or with the terminal, whatever)

---

### Post by Wolki on 2006-10-27
> **erik1397 said:**
> well when you have time, i guess you could go to places > search, and search for all instances of the firefox logo, and one by one delete them inside a root nautilus.  (or with the terminal, whatever)

That's why I was asking whether there is an easy way :)

Thanks for the help though.

---

### Post by user1397 on 2006-10-27
> **Wolki said:**
> That's why I was asking whether there is an easy way :)

Thanks for the help though.ah, good point.  :-k

---

### Post by jss on 2006-10-27
How can I change the globe icon in workspaces to the firefox icon?

---

### Post by user1397 on 2006-10-27
> **jss said:**
> How can I change the globe icon in workspaces to the firefox icon?
no idea, but i think that it's not possible.  anyone else care to opinionate?

---

### Post by GStubbs43 on 2006-10-27
> **jss said:**
> How can I change the globe icon in workspaces to the firefox icon?

In Edgy?

```
sudo cp /usr/share/pixmaps/firefox.png /usr/share/firefox/chrome/icons/default/default.xpm 
```

I believe this works, It changes the menu icon (In the upper right corner of the window) to the Fx icon, which changes the icon in the workspace switcher. It worked for me. :D

---

### Post by warlorddagaz on 2006-10-27
> **GStubbs43 said:**
> In Edgy?

```
sudo cp /usr/share/pixmaps/firefox.png /usr/share/firefox/chrome/icons/default/default.xpm 
```I believe this works, It changes the menu icon (In the upper right corner of the window) to the Fx icon, which changes the icon in the workspace switcher. It worked for me. :D

When I did it, I right clicked the icon, went to properties, and did it from there (there's a button to do it).

---

### Post by jss on 2006-10-27
Thanks GStubbs43! You're method worked perfectly.

---

### Post by GStubbs43 on 2006-10-27
> When I did it, I right clicked the icon, went to properties, and did it from there (there's a button to do it).
What I said, changes the actual icon *on the Firefox window* not the Alacarte Menu icon. I believe that is the icon the workspace switcher uses.

> Thanks GStubbs43! You're method worked perfectly.
No problem, glad I could help!

---

### Post by user1397 on 2006-10-27
> **GStubbs43 said:**
> In Edgy?

```
sudo cp /usr/share/pixmaps/firefox.png /usr/share/firefox/chrome/icons/default/default.xpm 
```I believe this works, It changes the menu icon (In the upper right corner of the window) to the Fx icon, which changes the icon in the workspace switcher. It worked for me. :D
man, was i wrong! ;)

---

