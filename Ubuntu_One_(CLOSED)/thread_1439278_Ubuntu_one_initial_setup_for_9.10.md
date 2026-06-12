---
title: "Ubuntu one initial setup for 9.10"
date: 2010-03-26
forum: Ubuntu One (CLOSED)
---

### Post by ic3man5 on 2010-03-26
I've installed ubuntu remix 9.10 on my lenovo S10e and noticed ubuntu one on here so I signed up on the website but I don't see any options to setup a username/pw in the software to let it sync. I've tried looking at the wiki/forums but haven't found anything useful so far. How do I set this up?

---

### Post by joshuahoover on 2010-03-26
> **ic3man5 said:**
> I've installed ubuntu remix 9.10 on my lenovo S10e and noticed ubuntu one on here so I signed up on the website but I don't see any options to setup a username/pw in the software to let it sync. I've tried looking at the wiki/forums but haven't found anything useful so far. How do I set this up?

For Karmic, you should be able to make use of the tutorials here: [https://wiki.ubuntu.com/UbuntuOne/Tutorials](https://wiki.ubuntu.com/UbuntuOne/Tutorials)

It sounds like you have an account setup based on what you posted so it's probably just a matter of copying files to your ~/Ubuntu One folder and letting the files sync. If you have more questions, you can hop on #ubuntuone on Freenode IRC and ask for me (joshuahoover) Monday-Friday, 13:00-21:00 UTC.

Thank you,

Joshua

---

### Post by ic3man5 on 2010-03-26
I followed the subscription tutorial but I don't have the same results when I go to internet->Ubuntu one.

Here is a screenshot of what I get:
[http://i41.tinypic.com/ekp94k.jpg](http://i41.tinypic.com/ekp94k.jpg)

Dragging files into the Ubuntu One folder doesn't do anything and the cloud with the ! always says disconnected.

I know its not syncing because [https://one.ubuntu.com/files/](https://one.ubuntu.com/files/) still shows no files.

---

### Post by duanedesign on 2010-03-27
You might try quiting Ubuntu One Applet by clicking on it and selecting quit. Then start Ubuntu One as you normally would Applications > Internet > Ubuntu One. Do you still get the '!'?

---

### Post by ic3man5 on 2010-03-27
> **duanedesign said:**
> You might try quiting Ubuntu One Applet by clicking on it and selecting quit. Then start Ubuntu One as you normally would Applications > Internet > Ubuntu One. Do you still get the '!'?

Strange that worked. I'm pretty sure I've restarted since I've had the problem which should of done the same thing?

---

### Post by duanedesign on 2010-04-04
The problem is probably occurring at start up. Read [bug 498444]("https://bugs.launchpad.net/ubuntuone-client/+bug/498444") as this sounds like it might be your issue. You can see if setting the Connect on Start to 'Never' helps. You would just start Ubuntu One manually when you want to do a sync.

---

