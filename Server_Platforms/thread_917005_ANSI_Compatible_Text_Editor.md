---
title: "ANSI Compatible Text Editor"
date: 2008-09-11
forum: Server Platforms
---

### Post by Vegan on 2008-09-11
Which text editors are fully compatible with the ANSI standard terminal? It seems I cannot use NANO as it is not compatible.

I need to use one that is ANSI compatible so I can set the system to use it for some editing from the terminal.

---

### Post by ilrudie on 2008-09-11
Most likely vi would be ansi compatible.  Although since you didn't go straight to vi I'm guessing its safe to assume you don't know how to use it or don't want to.  If someone else doesn't come up with a better suggestion try vi or vim though.

---

### Post by Krupski on 2008-09-11
> **Vegan said:**
> Which text editors are fully compatible with the ANSI standard terminal? It seems I cannot use NANO as it is not compatible.

I need to use one that is ANSI compatible so I can set the system to use it for some editing from the terminal.

I use NANO all the time... what doesn't it do that you need? Just curious.

---

### Post by bab1 on 2008-09-11
EMACS is configurable to be used in a terminal.  I believe VI is too.  Curious -- is this a VT 100 terminal?  Is it a real or an emulated terminal?

---

### Post by Vegan on 2008-09-11
I am using the Windows Hyperterm which support ANSI 3.61 terminal.

I also can load up a command prompt and use Telnet which can emulate VT52, VT100 and ANSI

ANSI is color, VT100 is monochrome. VT102 = ANSI is color.

NANO does not work at all, arrow keys don't work. VIM kinda works but the MAN page needs work.

Don't know the usage of EMACS, but I remember Wordstar.

---

### Post by cariboo on 2008-09-11
You may want to give **mc** a try, it is probably more than you'll ever need because of all the extra features, once you install it check out the man page.

Jim

---

### Post by bab1 on 2008-09-11
Wordstar, that takes me back.  Emacs has a steep learning curve. but it should do the trick.  I use vi/vim/gvim myself.  Nothing fancy just some simple bash or perl scripts.  Why hypertem?  There are better ways to connect to a linux host.  I would use ssh (via Putty) myself.  I believe that you can use Gvim (graphical) through ssh.  Not sure, so don't crucify me if it 'aint so.

---

