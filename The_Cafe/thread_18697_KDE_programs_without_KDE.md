---
title: "KDE programs without KDE?"
date: 2005-03-08
forum: The Cafe
---

### Post by Lynx on 2005-03-08
Is it possible for me to run KDE products without running the KDE gui? I ask this because of one program, that program being K3b. Also, are there any good programs that can convert Ogg to MP3 for KDE?

---

### Post by lao_V on 2005-03-08
As far as I know, you can quite happily install and run any kde programs under GNOME(or any other DM) as long as you install all the dependencies as well!

---

### Post by landotter on 2005-03-08
k3b is a little quirky about permissions under Ubuntu, though it runs perfectly. Best idea is to go to ubuntulinux.org and search for the wiki/howto on installing k3b. It's pretty easy, but there's just a couple things to watch out for.

If you can't log back into Gnome after installing k3b, don't panick, it's a known bug. Just drop into a console "ctrl alt f2", log in, type "rm .ICE*" and you'll be able to log in by pressing "crl alt f7"

---

### Post by amoser on 2005-03-08
If you need something like K3b, why don't you give Gnomebaker a try.  It has most of the features that K3b has,  but it is made in GTK, so you don't need to install any of the KDE dependencys.

~Alan

P.S. It can be found at gnomebaker.sourceforge.net

---

### Post by Jad on 2005-03-08
I give my vote to Gnome Baker, its great
give it a try man

---

### Post by jdong on 2005-03-08
KDE apps, for the most part, run wonderfully under GNOME, and also vice-versa. Running K3bsetup is an exception, because it resets some home folder stuff to root ownership... However, it's not KDE's fault, more of K3bsetup's fault.


Note that starting KDE apps from GNOME for the first time (in a session) causes KDE's initialization process to start, which may mean 5 or so seconds of disk activity before the app loads. Most of the times, it's bearable and unnoticeable.


Some people don't like installing all of the KDE dependencies that come along, but all-in-all, it takes ~50MB to install KDE dependencies for K3b, which is very little on modern systems. Having them around doesn't slow down your system in any way, so why not?

---

### Post by poofyhairguy on 2005-03-08
[QUOTE=Lynx]Is it possible for me to run KDE products without running the KDE gui? I ask this because of one program, that program being K3b. Also, are there any good programs that can convert Ogg to MP3 for KDE?[/QUOTE]

I wrote a guide. PLEASE USE IT FOR YOUR OWN SAKE!

[http://www.ubuntulinux.org/wiki/K3BHowto/view?searchterm=k3b](http://www.ubuntulinux.org/wiki/K3BHowto/view?searchterm=k3b)

---

