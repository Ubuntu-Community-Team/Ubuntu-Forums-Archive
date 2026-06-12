---
title: "Uzbl - the hardcore browser"
date: 2009-09-06
forum: The Cafe
---

### Post by Copernicus1234 on 2009-09-06
If you have a lot of time and feel todays browsers are too full of features and bloated, you may want to check out Uzbi.

Uzbl follows the UNIX philosophy - "Write programs that do one thing and do it well. Write programs to work together. Write programs to handle text streams, because that is a universal interface."

[http://www.uzbl.org/](http://www.uzbl.org/)

No tabs, history, cookies, anything.... :)

But apperently it gets perfect scores in the Acid3 tests and [will work]("http://blog.duwanis.com/past/2009/5/17/installing_uzbl_on_ubuntubased_distros/") on Ubuntu as well.

---

### Post by K.Mandla on 2009-09-06
uzbl is the closest thing to a rock star Linux has.

:guitar:

---

### Post by speedwell68 on 2009-09-06
> **Copernicus1234 said:**
> If you have a lot of time and feel todays browsers are too full of features and bloated, you may want to check out Uzbi.

Uzbl follows the UNIX philosophy - "Write programs that do one thing and do it well. Write programs to work together. Write programs to handle text streams, because that is a universal interface."

[http://www.uzbl.org/](http://www.uzbl.org/)

No tabs, history, cookies, anything.... :)

But apperently it gets perfect scores in the Acid3 tests and [will work]("http://blog.duwanis.com/past/2009/5/17/installing_uzbl_on_ubuntubased_distros/") on Ubuntu as well.

But surely without tabbed browsing, cookies or anything else for that matter it is going to give you a very limited experience of the internet.  I am going to give it a try even so.

---

### Post by coldReactive on 2009-09-06
> **Copernicus1234 said:**
> No cookies

Sorry, but if it doesn't have this, it's not even usable to me. (Though, I also need flash.)

---

### Post by sertse on 2009-09-06
uzbl is too hardcore but me to really use, but as far as I understand it, No tabs, no cookies etc is a *design feature* of doing things the UNIX way, "one thing and one thing well". 

If you want cookies, get a specialised cookie script and use it to interact with uzbl.  If you want tabs, get a specialised tab manager script and use it to interact with uzbl. IIRC there are example scripts to included w/ uzbl to demonstrate this and for you to add in if you want. There are also more examples in the community.

Uzbl uses webkit though, so your plugins/flash works fine. 

uzbl is about separating each function into individual parts, so each part focuses on it's own thing, and do it better.  Your overall web experience becomes better when each one of those separate, now better things interact with each other. Compare this to your usual web browser tries tries to take on doing all those things by itself.

That's the beauty of uzbl.

---

### Post by RATM_Owns on 2009-09-06
> **speedwell68 said:**
> But surely without tabbed browsing, cookies or anything else for that matter it is going to give you a very limited experience of the internet.  I am going to give it a try even so.
There is the included uzbl_tabbed.py, which gives it tabs.
And there are included cookie scripts.

I've been using it since I saw it first on Arch Linux Forums forever ago.

---

### Post by chucky chuckaluck on 2009-09-06
i think i'd have to be a lot more bitter at the world before i tried this browser again.

---

### Post by dragos240 on 2009-09-06
I installed it on my archbox. It works....... but I have no idea how to use it :p I can't even use text fields!

---

### Post by kk0sse54 on 2009-09-06
Uzbl is a fantastic browser that I've been using it on Arch for a while. It's definitely not for everyone but I'd still recommend it.

---

### Post by Raffles10 on 2009-09-06
What's the point ? If your purpose is to browse the internet you're better of with Firefox, Midori etc. Good software makes the job easy not difficult. Uzbl is a rather pointless way of wasting your time.

---

### Post by Barrucadu on 2009-09-06
> **dragos240 said:**
> I installed it on my archbox. It works....... but I have no idea how to use it :p I can't even use text fields!

Are you insert mode? :P

Default shortcut: 'i'

---

### Post by purgatori on 2009-09-06
Great browser, and I had little difficulty in getting it up and running insofar as configuring it and all the rest was concerned, but a couple of versions ago, I got a "mutex" error whenever a page was loaded (even uzbl.org), causing the application to instantly crash. Successive updates have not corrected the problem, and I am at a loss to determine what is causing it,  since the error output does not specify exactly which libraries or whatever are involved in the "mutual exclusion" in question. A bug report has been filed for this issue, and some users who encountered the same thing on Ubuntu suspected it might be a problem with libsoup, but if 9.04 users are not encountering this error.... then I don't know. 

Anyway, this is a [great guide](http://tuxtraining.com/2009/09/05/uzbl-and-uzbl_tabbed-py-a-browser-that-adheres-to-the-unix-philosophy) for properly configuring uzbl, and it even covers how to enable a tabbed-interface.

 I do so wish I could get it work again :(

---

### Post by chris200x9 on 2009-09-06
I can see how this is better if you like to customize and tinker but it just doesn't make sense to have a browser where *everything* is externally controlled in an interpreted language in my opinion. Plus wouldn't that make it slower than most other browsers?

---

### Post by purgatori on 2009-09-06
> **chris200x9 said:**
> I can see how this is better if you like to customize and tinker but it just doesn't make sense to have a browser where *everything* is externally controlled in an interpreted language in my opinion. Plus wouldn't that make it slower than most other browsers?

Actually, most of the heavy-lifting is done by Webkit, just as it is by Gecko in Firefox, for instance. The external configuration options pertain mostly to the interface.

---

### Post by dragos240 on 2009-09-06
> **Barrucadu said:**
> Are you insert mode? :P

Default shortcut: 'i'

I pressed i, and nothing happened. It just changed what was it the title.

---

### Post by RATM_Owns on 2009-09-06
The little [C] in the bottom left should change to [I].
(Pressing ESC by default brings it back to command mode.)

---

### Post by conehead77 on 2009-09-06
> **dragos240 said:**
> I pressed i, and nothing happened. It just changed what was it the title.

Did you copy the example config files?
```

cp -r /usr/share/uzbl/examples/data/uzbl/ ~/.local/share/
cp -r /usr/share/uzbl/examples/config/uzbl/ ~/.config/

```
(create folders if necessary)

I had the same problem and now it works.

---

