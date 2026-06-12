---
title: "Request Tracker + fresh install"
date: 2005-12-10
forum: Server Platforms
---

### Post by iwalmsley on 2005-12-10
Stumbling upon this issue:

Now I am experienceing this issue, when trying to follow this HOWTO:

[http://wiki.bestpractical.com/index.cgi?UbuntuInstallGuide](http://wiki.bestpractical.com/index.cgi?UbuntuInstallGuide)

root@ares:/etc/apache2/mods-available# sudo apt-get install libapache2-mod-fastcgi
Reading package lists... Done
Building dependency tree... Done
Package libapache2-mod-fastcgi is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libapache2-mod-fastcgi has no installation candidate

tried to download it manually, but my server cannot find 'make'

---

### Post by tncmmngs on 2005-12-10
Try this:

```
prompt$ whereis make
```

If your answer is
```
make:
```

you'll need to install make...

```
prompt$ sudo apt-get install make
```

I'm interested in RT, so let me know how this goes. Good luck!

---

### Post by iwalmsley on 2005-12-10
Great. that got me the 'make' program;

now I get this error:

root@ares:/home/iwalmsley/mod_fastcgi-2.4.2# make
Makefile:12: /usr/share/apache2/build/special.mk: No such file or directory
make: *** No rule to make target `/usr/share/apache2/build/special.mk'.  Stop.

Can't get pass this, here are the instructions I am trying to follow:

  *NIX
  ====

    $ cd <mod_fastcgi_dir>
    $ cp Makefile.AP2 Makefile
    $ make
    $ make install

    If your Apache2 installation isn't in /usr/local/apache2, then
    set the top_dir variable when running make (or edit the
    Makefile), e.g.

      $ make top_dir=/opt/httpd/2.0.40

    Add an entry to httpd.conf like this:

      LoadModule fastcgi_module modules/mod_fastcgi.so

---

### Post by iwalmsley on 2005-12-11
fresh new install again.
followed the directions to a tee ( [http://wiki.bestpractical.com/index.cgi?UbuntuInstallGuide](http://wiki.bestpractical.com/index.cgi?UbuntuInstallGuide) ).... it bails on:

apt-get install libapache2-mod-fastcgi

with this message:

root@luther:/home/iwalmsley# apt-get install libapache2-mod-fastcgi
Reading package lists... Done
Building dependency tree... Done
Package libapache2-mod-fastcgi is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libapache2-mod-fastcgi has no installation candidate

And the above comments was when I tried to download the mod-fastcgi package and manually compile it.. 

Any suggestions?

---

### Post by tncmmngs on 2005-12-11
Ahh. 

Check your /etc/apt/sources.list file.

If the repositories listed begin  with US like this:
```
deb http://us.archive.ubuntu.com/ubuntu breezy main restricted
```

you need to update the file. Point your web browser to [http://www.psychocats.net/linux/sources.php]("http://www.psychocats.net/linux/sources.php") and follow the directions for replacing the Breezy sources.list file.

You should then be able to install the missing package.

I really can't figure out why Ubuntu decided to put this crippled sources.list file in the build...maybe somebody else knows. Again, let me know how this goes!

---

### Post by iwalmsley on 2005-12-12
I got it to work! RT is now running on my machine. I would recommend RT to anyone who wants to track "issues" within their network! I also got some help from this thread: [http://www.ubuntuforums.org/showthread.php?t=102251](http://www.ubuntuforums.org/showthread.php?t=102251).

---

