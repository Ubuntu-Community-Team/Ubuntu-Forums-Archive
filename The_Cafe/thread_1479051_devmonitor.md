---
title: "/dev/monitor"
date: 2010-05-10
forum: The Cafe
---

### Post by dragos240 on 2010-05-10
Where would that be? What device file is your first and second monitor in? I'm curious because I am still working on my portal program. One program will run in the first monitor as the text, the second will display ascii art. Help?

---

### Post by insane_alien on 2010-05-10
do you really need to directly access the monitor? would it not be better to pass on the info to the X server and let it sort it out.

---

### Post by dragos240 on 2010-05-10
Sure. How can I set X up so that one monitor redirects to tty2 and another to tty3. Can X do this?

---

### Post by dragos240 on 2010-05-11
Bump....

---

### Post by dragos240 on 2010-05-12
....Bump....

---

### Post by tom66 on 2010-05-12
You want to directly access the frame-buffer of your monitors?

---

### Post by dragos240 on 2010-05-12
Yes. That would be nice.

---

### Post by schauerlich on 2010-05-12
[img]http://grab.by/grabs/77a4d0dd18ebe5b38ba998f040f92a4a.png[/img]
[img]http://grab.by/grabs/675713dc6cf6c104f6dacd09f059bdec.png[/img]

Better get to work.

---

### Post by snova on 2010-05-12
> **dragos240 said:**
> Where would that be? What device file is your first and second monitor in?

I don't think the system even has direct access to the monitor. What do you think it plugs into?

> I'm curious because I am still working on my portal program. One program will run in the first monitor as the text, the second will display ascii art. Help?

This sounds like the wrong way to go about it, if there ever was one...

---

### Post by pwnst*r on 2010-05-12
> **schauerlich said:**
> [img]http://grab.by/grabs/77a4d0dd18ebe5b38ba998f040f92a4a.png[/img]
[img]http://grab.by/grabs/675713dc6cf6c104f6dacd09f059bdec.png[/img]

Better get to work.

lol

---

### Post by Warpnow on 2010-05-12
Ummm...your monitor isn't a piece of hardware like a hard drive or a cd drive, its a peripheral attached to your video card. I think accessing it directly is akin to asking where /dev/escape key is so you can access your escape key directly.

---

