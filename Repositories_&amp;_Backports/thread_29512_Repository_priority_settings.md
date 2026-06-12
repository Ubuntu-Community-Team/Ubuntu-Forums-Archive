---
title: "Repository priority settings"
date: 2005-04-24
forum: Repositories &amp; Backports
---

### Post by JGJones on 2005-04-24
I have quite a list of repositories that I use for my Ubuntu installation, however I would like to ensure that the Ubuntu repositories are the FIRST source for any given software so that the Ubuntu "version" would be the installed one rather than from other sources. 

How do I assign priority settings to each repositories I have listed?

I have read it's something to do with creating a /etc/apt/preferences file?

Many thanks

---

### Post by fdoving on 2005-04-25
[QUOTE=JGJones]I have quite a list of repositories that I use for my Ubuntu installation, however I would like to ensure that the Ubuntu repositories are the FIRST source for any given software so that the Ubuntu "version" would be the installed one rather than from other sources. 

How do I assign priority settings to each repositories I have listed?

I have read it's something to do with creating a /etc/apt/preferences file?

Many thanks[/QUOTE]
 Hello
What you've read about the /etc/apt/preferences file is correct.

In a simple "Apt-pinning"-setup the preferences file would look something like this:

# ----

Package: *
Pin: release a=hoary
Pin-Priority: 700

Package: *
Pin: origin no.archive.ubuntu.com
Pin-Priority: 600

# ----

The default Pin-Priority is 500, everything exceeding 500 will be prioritized.
700 will be prioritized over 600 and so on. Take a look at 'man apt_preferences' (iirc) for more details. 


- Frode

---

### Post by fdoving on 2005-04-25
[QUOTE=fdoving]Hello
What you've read about the /etc/apt/preferences file is correct.

In a simple "Apt-pinning"-setup the preferences file would look something like this:

# ----

Package: *
Pin: release a=hoary
Pin-Priority: 700

Package: *
Pin: origin no.archive.ubuntu.com
Pin-Priority: 600

# ----

The default Pin-Priority is 500, everything exceeding 500 will be prioritized.
700 will be prioritized over 600 and so on. Take a look at 'man apt_preferences' (iirc) for more details. 


- Frode[/QUOTE]
 More info: 

[http://jaqque.sbih.org/kplug/apt-pinning.html](http://jaqque.sbih.org/kplug/apt-pinning.html)

This is for debian, but just change the sources and the release names to fit ubuntu.

- Frode

---

