---
title: "mailmgr with SARG"
date: 2013-05-15
forum: Server Platforms
---

### Post by umfunix on 2013-05-15
I've got a Ubuntu server with squid3, dansguardian and SARG report generator.  I want to install mailmgr ([http://sarg.sourceforge.net/mailmgr.README.txt](http://sarg.sourceforge.net/mailmgr.README.txt)).  I've downloaded the file and run /.configure but get the following error:
> checking host system ......
checking for gcc.....no
checking for cc ..... no
configure: error: no acceptable cc found in $path

What should I do to fix or install mailmgr for SARG?

---

### Post by SeijiSensei on 2013-05-15
You have no compiler.  Install the **build-essential** package from the repositories and try again.

---

### Post by umfunix on 2013-05-16
Hi

I tried, but it seems as if I have a unistalled dependency issue.  I tried to run apt-get install -f but it wouldn't install

> The following packages have unmet dependencies:
build-essential : epends: libc6-dev but it is not going to be installed or libc-dev
Depends: gcc .... but its not going to be installed
Depends: g++ ..... same
Depends: make .... same
Depends: dpkg-dev .... same
sarg: Depends: libgd2-xpm .... same


---

### Post by umfunix on 2013-05-16
After restarting the server and running apt-get install -f again, is reports that there is some unresolved dependencies, mainly with SARG and libgd2-xpm. Also ssub-process /usr/bin/dpkg returned an error code (1).

---

### Post by SeijiSensei on 2013-05-16
Well you can try fixing the libc6-dev problem by installing that package manually ("sudo apt-get install libc6-dev") and see if that helps.

---

