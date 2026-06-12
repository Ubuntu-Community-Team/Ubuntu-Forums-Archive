---
title: "Easy install package"
date: 2008-03-21
forum: Ubuntu Brainstorm
---

### Post by mac9416 on 2008-03-21
Hello,
I am a SERIOUS newb so excuse me if everything I say is laughable.
:lolflag:

I download all of my software, linux and windoze, from a windows computer that is hooked up to the net (my Ubuntu Ultimate machine is not connected). Most of the time when I bring a .deb home on a flash drive it will not install because it has to download something or other.
My question is 'Is it possible to have a package with all required files attached to it so that I do not have to have an internet connection to install, say, Supertux 0.3.1?'.
Or am I crazy?

Thanks

-SeriousNewb aka mac

---

### Post by tagra123 on 2008-03-21
Neither of these links are exactly what you are looking for but might help get you started.

[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)

[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

You may be able to use ldd on the binary file itself

ldd someexecutablefile

---

### Post by maybeway36 on 2008-03-22
aptoncd should be able to fetch the depends for you. :)

---

### Post by mac9416 on 2008-03-29
Thanks, and sorry I have been away for a while.

That looks great but I have one problem. I download ALL of my files from a Windoze machine.:mad:

Thanks for the help but that doesn't look like what I need.

PS: What is ldd

---

### Post by mac9416 on 2008-10-07
Just in case you found this by searching Google and need a good solution, I now use [Keryx]("http://keryx.betaserver.org") to download packages and dependencies from Windoze or Ubuntu!

---

### Post by UbuWu on 2008-10-07
Thanks, nice find!

---

