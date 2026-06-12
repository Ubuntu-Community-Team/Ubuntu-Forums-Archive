---
title: "Unable to install new software in 9.10"
date: 2009-11-24
forum: Ubuntu Moblin Remix
---

### Post by spectrevk on 2009-11-24
After considerable wrangling, I managed to install UNR 9.10. Now, all I have to do is install flash, maybe some video codecs, and I have a working netbook, right?

Hold on there. Ubuntu Software Center doesn't work. No install buttons, and the install option on the menu is greyed out. It never asks for authentication, which is (I'm sure) why I'm not seeing these options. I tried to report the software problem, but when I selected that option from Help, I got a message saying that this wasn't a genuine ubuntu package. This is especially confusing as I installed the OS using Wubi, which is Canonical software.

---

### Post by snowpine on 2009-11-24
I've never used this "Ubuntu Software Center" of which you speak, but it's really easy to install applications using the Terminal (Applications->Accessories->Terminal)

First you refresh your list of what's available:

```
sudo apt-get update
```

Next, install the application(s) you want. I suggest ubuntu-restricted-extras because it includes Flash and lots of other codecs:

```
sudo apt-get install ubuntu-restricted-extras
```

You can use that to install any package in the repositories, for example to install Battle for Wesnoth:

```
sudo apt-get install wesnoth
```

Good luck!

---

### Post by spectrevk on 2009-11-24
Thank you for the refresher on apt-get; I really do appreciate it. I'm still hoping to get the software center to work as it is supposed to, though.

EDIT: The problem appears to have abated. Not sure what was causing it, to be honest.

---

