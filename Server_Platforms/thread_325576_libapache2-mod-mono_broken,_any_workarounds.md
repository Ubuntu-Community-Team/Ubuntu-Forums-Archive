---
title: "libapache2-mod-mono broken, any workarounds?"
date: 2006-12-26
forum: Server Platforms
---

### Post by not_cool on 2006-12-26
Well I have my apache2 server all set up complete with mysql and php (this is being run on my edgy desktop, not server install). However, I also want to be able to use asp or aspx pages and have tried to install libapache2-mod-mono, getting the following result:
```
markus@desktop:~/Web/testing$ sudo apt-get install libapache2-mod-mono
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libapache2-mod-mono: Depends: mono-apache-server (< 1.1.14) but it is not going to be installed or
                                mono-apache-server2 (< 1.1.14) but 1.1.17.1-2 is to be installed
E: Broken packages

```

I know that this is already a [bug]("https://launchpad.net/distros/ubuntu/+source/mod-mono/+bug/65454"), and was wondering if there is any workaround. IE, if the version number is wrong, but it is the correct package, changing the version number (and dependencies version numbers), or if I can checkinstall the mod source, but I don't want to break my apache2 install. Any ideas?

---

### Post by not_cool on 2006-12-26
help?

---

### Post by not_cool on 2006-12-29
nobody knows a workaround? I'm sure I'm not the only one wanting to run asp.net pages?

---

### Post by Brazen on 2006-12-29
try "sudo apt-get -f install"

Also do you have universe and multiverse repos in your sources.list (not sure if they are necessary for mono or not)?

---

### Post by not_cool on 2006-12-29
ya, they're enabled, I'll try forcing the install now
EDIT: doesn't work

---

### Post by Brazen on 2006-12-30
> **not_cool said:**
> ya, they're enabled, I'll try forcing the install now
EDIT: doesn't work

the -f is for "fix" not force.  Just run the "sudo apt-get -f install" and nothing else after it.

---

### Post by not_cool on 2007-01-01
it didn't do anything

---

### Post by jan247 on 2007-01-01
I have the same problem, and ended up manually installed an older version from the dapper repository from [here]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Funiverse%2Fm%2Fmod-mono%2Flibapache2-mod-mono_1.1.10-1_i386.deb&md5sum=5901fa5822d2900e37b49ce0ef4e4c77&arch=i386&type=main").
It installed just fine. Trying it out now to see if it works.

---

### Post by valorin on 2007-01-01
I have the same problem, and I believe its the reason iFolder will not work in Edgy.

---

### Post by jmoschetti45 on 2007-01-06
Read the first portion of this: [http://www.ifolder.com/index.php/HowTo:iFolder_Enterprise_Server_on_Ubuntu_6.10](http://www.ifolder.com/index.php/HowTo:iFolder_Enterprise_Server_on_Ubuntu_6.10)

Fixed it for me

---

### Post by valorin on 2007-01-06
Nope, hasn't helped. It doesn't even look like it installed... And this is on a clean install.

Any other ideas?

---

