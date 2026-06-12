---
title: "Failsafe Terminal"
date: 2015-02-26
forum: Server Platforms
---

### Post by cackles on 2015-02-26
Hi,
I am migrating my server to new hardware using the eggsonbread tutorial [http://eggsonbread.com/2010/01/28/move-ubuntu-to-another-computer-in-3-simple-steps/](http://eggsonbread.com/2010/01/28/move-ubuntu-to-another-computer-in-3-simple-steps/)

It says to open a failsafe terminal. How do you do that with a command line server?

From what Ive seen you just hold alt when booting, that does take me to a menu but failsafe isn't an option.

Ive already tried a few times and when I migrate the server wont start at all.

Maybe there is also an easier tutorial.

---

### Post by nerdtron on 2015-02-27
I'm not sure of a failsafe terminal but I think he is pertaining to a terminal session that you can disconnect but will still run on the background. Probably a screen session or a terminal on the server itself (not ssh).

I also won't recommend this upgrade path. I don't know, it's outdated and I don't think will work on all server setups. But still though, everything is up to you.

---

### Post by cackles on 2015-02-27
Thanks for the reply nerdtron. It didn't work, but I have spent the last day working out a good way to do it that I will post in tutorials later on.

---

### Post by ian-weisser on 2015-02-27
By "failsafe", they mean a console (CTRL+ALT+F1), terminal window, or any other terminal you can reach.

Egad, that's an awful tutorial. Rather a cross-your-fingers-and-wish-really-hard method.

A much less fragile method is to document your customizations, so you can reproduce them on any supported hardware and any supported version that you wish.

---

