---
title: "Epiphany thinks it's Firefox"
date: 2007-12-18
forum: The Cafe
---

### Post by Luggy on 2007-12-18
[[IMG]http://img143.imageshack.us/img143/1504/epiphanylolzuf1.th.png[/IMG]](http://img143.imageshack.us/my.php?image=epiphanylolzuf1.png)

Just open up Epiphany and for an address type "error:" or some other invalid url thingamabob and you will get that error.

---

### Post by vishzilla on 2007-12-18
Correct if I am wrong...Epiphany is based on the same engine as Firefox

---

### Post by kellemes on 2007-12-18
They're using the same engine so this message doesn't surprise me..

---

### Post by lvleph on 2007-12-18
Someone went cut and paste crazy. lol

---

### Post by SunnyRabbiera on 2007-12-18
yeh they both use the same core so no surprise

---

### Post by RebounD11 on 2007-12-18
I would've expected sth like this from MS :)

---

### Post by FuturePilot on 2007-12-18
Epiphany currently uses the Gecko engine from Firefox.

---

### Post by hanzomon4 on 2007-12-18
It is firefox, dressed in gtk. Ok, not really but they use the same engine so I'm not surprised.

---

### Post by Mr. Picklesworth on 2007-12-18
I blame Gecko ;)

Thankfully, the Epiphany people are forward-thinking enough to be moving this browser over to WebKit...

---

### Post by bruce89 on 2007-12-18
Ubuntu have made the bad decision to build Epiphany on Firefox instead of XULRunner. See [https://bugs.launchpad.net/ubuntu/+source/epiphany-browser/+bug/39033](https://bugs.launchpad.net/ubuntu/+source/epiphany-browser/+bug/39033) and [http://bugzilla.gnome.org/show_bug.cgi?id=333487](http://bugzilla.gnome.org/show_bug.cgi?id=333487)

Once Ubuntu switch to Epiphany with WebKit, this won't be an issue.

---

### Post by adityakavoor on 2007-12-18
Lol :)

---

### Post by Mr. Picklesworth on 2007-12-18
More shocking, actually, is this one:
chrome://browser/content/browser.xul

(And some web sites trigger downloads in weird ways, causing the XUL download manager to open).

Thus, if you still feel an overwhelming urge to use Firefox for some absurd reason, you need not look *any further* than Epiphany.

---

### Post by Luggy on 2007-12-18
> **Mr. Picklesworth said:**
> I blame Gecko ;)

Thankfully, the Epiphany people are forward-thinking enough to be moving this browser over to WebKit...

So then it will say "Sorry Safari can't find the page you are looking for"?

---

### Post by p_quarles on 2007-12-18
> **Luggy said:**
> So then it will say "Sorry Safari can't find the page you are looking for"?
No, that won't happen. As people have pointed out, Ubuntu made the decision to run Epiphany on top of Firefox's Gecko engine -- in other words, it's actually using parts of Firefox. Debian doesn't do this, so if you were to run Epiphany on Debian, you would not get this message.

---

### Post by Thumper! on 2007-12-18
i don't even know why gnome spend there time developing Epiphany? I mean whats the point? it's just a downgraded version of mozilla Firefox, same thing goes to evolution mail, Thunderbird is much better and was already there to use for free?

sometimes i don't understand the Gnome guys....ahh well!

---

### Post by Vadi on 2007-12-18
Uh, yayyy, funny.

No, really. Can it be any more less mature about this? Just file a bug report and move on...

---

### Post by Luggy on 2007-12-18
> **p_quarles said:**
> No, that won't happen. As people have pointed out, Ubuntu made the decision to run Epiphany on top of Firefox's Gecko engine -- in other words, it's actually using parts of Firefox. Debian doesn't do this, so if you were to run Epiphany on Debian, you would not get this message.

So the Ubuntu devs chose for Epiphany to run ontop of Firefox's version of Gecko and not just Gecko itself?

---

### Post by p_quarles on 2007-12-18
> **Luggy said:**
> So the Ubuntu devs chose for Epiphany to run ontop of Firefox's version of Gecko and not just Gecko itself?
That's what I said. Anyway, go back and take a look at the bugs that Bruce89 linked to. You'll get more accurate explanations at Launchpad and Bugzilla than you're likely to get here.

---

### Post by FuturePilot on 2007-12-18
> **Luggy said:**
> So the Ubuntu devs chose for Epiphany to run ontop of Firefox's version of Gecko and not just Gecko itself?

Currently there is no stand alone Gecko engine. But I believe that's what xulrunner solves.

---

### Post by Luggy on 2007-12-18
Meh, I wasn't really trying to point out bugs... I just thought it was funny is all...

---

### Post by jken146 on 2007-12-18
> **Thumper! said:**
> i don't even know why gnome spend there time developing Epiphany? I mean whats the point? it's just a downgraded version of mozilla Firefox, same thing goes to evolution mail, Thunderbird is much better and was already there to use for free?

sometimes i don't understand the Gnome guys....ahh well!

Epiphany is much faster than firefox.  I'll be using it until firefox 3 comes out, and then we'll see.

Evolution is not a downgraded version of thunderbird.  I need Evolution for its better MS Exchange support.

---

### Post by Rashedul on 2007-12-18
> **jken146 said:**
> Epiphany is much faster than firefox.  I'll be using it until firefox 3 comes out, and then we'll see.

Evolution is not a downgraded version of thunderbird.  I need Evolution for its better MS Exchange support.

Edit: Swiftfox from the Swiftfox repository is using Firefox 3.0bpre right now.

---

### Post by bruce89 on 2007-12-18
> **p_quarles said:**
> No, that won't happen. As people have pointed out, Ubuntu made the decision to run Epiphany on top of Firefox's Gecko engine -- in other words, it's actually using parts of Firefox. Debian doesn't do this, so if you were to run Epiphany on Debian, you would not get this message.

Not quite true. Debian build-depend on XULRunner, which is Gecko as well, but separate from Firefox.

> **FuturePilot said:**
> Currently there is no stand alone Gecko engine. But I believe that's what xulrunner solves.

Debian already use it.

> **jken146 said:**
> Epiphany is much faster than firefox.  I'll be using it until firefox 3 comes out, and then we'll see.

[Epiphany in Hardy uses XULRunner 1.9]("https://launchpad.net/ubuntu/hardy/+source/epiphany-browser/2.21.4-0ubuntu2") (as of an hour ago), so all the Gecko improvements will apply to Epiphany now. Hopefully this will mean that removing Firefox is possible now.

---

### Post by Mr. Picklesworth on 2007-12-18
> **Thumper! said:**
> i don't even know why gnome spend there time developing Epiphany? I mean whats the point? it's just a downgraded version of mozilla Firefox, same thing goes to evolution mail, Thunderbird is much better and was already there to use for free?

sometimes i don't understand the Gnome guys....ahh well!

The problem is that Firefox is not integrated into the GNOME desktop in any way. Subscribing to RSS feeds with Epiphany is a wonderful D-Bus powered process, for example, whereas Firefox has a Windows-esque list of arbitrary applications that happen to be the "chosen ones" that Firefox can work with. With Epiphany, if Liferea is running in the background, I can subscribe to it with Liferea. Same with any feed reader that uses D-Bus, even if it was not at all considered by the Epiphany (extension, in this case) developers.

(Speaking of which, we also have Firefox's bother appear when opening RSS feeds... I should see if that's reported).


Compared to Epiphany, Firefox is accessibility-challenged; it does not follow the user's theme settings and (being XUL powered) does not behave like any other application on the GNOME desktop. Its dropdown menus do not (and will not) have configurable menu accellerators, its toolbar buttons are all using Firefox's own theme and display settings, its menus and buttons all have Firefox's own localization instead of stock widgets. Because of XUL, Compiz needs an ugly workaround (any workaround is ugly) to properly recognize Firefox's menus as menus.

As well as just plain ugly, these are usability issues. When a major application such as the web browser behaves in a manner substantially different from any other application on the desktop, the features provided by that desktop environment (of which there are many) will be difficult to learn and understand. Another point against learnability when we use Firefox: Its icons are likely to be different if the user is not using the distro's default theme for each. This means that people will not get the connection between a particular image and the action that it always represents.

For accessibility, this is a *huge* issue. Here we have a web browser (I will stress: The most common application at this point in time) that will not change if the user needs a high contrast theme due to vision problems. Its font size will not grow if the user chooses a bigger font in the Font settings. Instead, he has to repeat that preference, again, in Firefox.

That is what we are trying to avoid here! GNOME (and Ubuntu, I hope) is all about having a cohesive desktop where one global setting can change the behaviour of every program, such that one does not need to spend more than a short moment making things work. With most of the GNOME applications, that is working beautifully.

Firefox, being a program clearly not built for GNOME, simply does not fit here as a default. As long as it is "Ubuntu's web browser", the default desktop will appear broken.


Sorry, I've turned this into a recurring discussion :(

---

### Post by tageiru on 2007-12-18
> **Thumper! said:**
> same thing goes to evolution mail, Thunderbird is much better and was already there to use for free?
That's not true. Evolution was first.

---

### Post by lvleph on 2007-12-18
> **Mr. Picklesworth said:**
> More shocking, actually, is this one:
chrome://browser/content/browser.xul

(And some web sites trigger downloads in weird ways, causing the XUL download manager to open).

Thus, if you still feel an overwhelming urge to use Firefox for some absurd reason, you need not look *any further* than Epiphany.

Woohoo I am going to crash my browser with that one. If you have RSS ticker, do a bunch of those and see what happens.

You can even open tabs. lol

---

### Post by bruce89 on 2007-12-18
> **Mr. Picklesworth said:**
> Compared to Epiphany, Firefox is accessibility-challenged; it does not follow the user's theme settings and (being XUL powered) does not behave like any other application on the GNOME desktop. Its dropdown menus do not (and will not) have configurable menu accellerators, its toolbar buttons are all using Firefox's own theme and display settings, its menus and buttons all have Firefox's own localization instead of stock widgets. Because of XUL, Compiz needs an ugly workaround (any workaround is ugly) to properly recognize Firefox's menus as menus.
As well as just plain ugly, these are usability issues. When a major application such as the web browser behaves in a manner substantially different from any other application on the desktop, the features provided by that desktop environment (of which there are many) will be difficult to learn and understand. Another point against learnability when we use Firefox: Its icons are likely to be different if the user is not using the distro's default theme for each. This means that people will not get the connection between a particular image and the action that it always represents.
For accessibility, this is a *huge* issue. Here we have a web browser (I will stress: The most common application at this point in time) that will not change if the user needs a high contrast theme due to vision problems. Its font size will not grow if the user chooses a bigger font in the Font settings. Instead, he has to repeat that preference, again, in Firefox.
That is what we are trying to avoid here! GNOME (and Ubuntu, I hope) is all about having a cohesive desktop where one global setting can change the behaviour of every program, such that one does not need to spend more than a short moment making things work. With most of the GNOME applications, that is working beautifully.
Firefox, being a program clearly not built for GNOME, simply does not fit here as a default. As long as it is "Ubuntu's web browser", the default desktop will appear broken.


Sorry, I've turned this into a recurring discussion :(

Even though there are no paragraphs, this is a well put argument.

I assume Ubuntu uses Firefox as people know of it. This seems pointless as all the other programs are different. Even most of the Ubuntu developers use Epiphany.

---

### Post by Thumper! on 2007-12-18
> **jken146 said:**
> Epiphany is much faster than firefox.  I'll be using it until firefox 3 comes out, and then we'll see.

Evolution is not a downgraded version of thunderbird.  I need Evolution for its better MS Exchange support.

My bad......

8-[

---

