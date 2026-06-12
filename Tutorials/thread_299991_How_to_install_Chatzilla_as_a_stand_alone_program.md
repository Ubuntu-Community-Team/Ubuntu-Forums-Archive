---
title: "How to: install Chatzilla as a stand alone program"
date: 2006-11-15
forum: Tutorials
---

### Post by kopilo on 2006-11-15
Ok the only programs you'll need is [Xulrunner]("http://releases.mozilla.org/pub/mozilla.org/xulrunner/releases/1.8.0.4/linux-i686/en-US/xulrunner-1.8.0.4.en-US.linux-i686.tar.gz") and [Chatzilla]("http://chatzilla.rdmsoft.com/xulrunner/download/chatzilla-0.9.76-xr.zip").
The requirements for Xulrunner can be found [here]("http://chatzilla.rdmsoft.com/xulrunner/sysreq/").

The first thing you will need to do is download and extract the xulrunner to your desktop, from there open up terminal (Applications -> Accessories).
And then move the xulrunner to system location (effectively installing it)
```
sudo mv ~/Desktop/xulrunner /usr/share/
```
Then navigate to that directory in terminal
```
cd /usr/share/xulrunner
```
Then you need to register xulrunner.
```
./xulrunner --register-user
./xulrunner --register-global
```

Now comes the slightly more exciting part... Installing Chatzilla. Make sure you have downloaded chatzilla to your desktop.
```
sudo ./xulrunner --install-app ~/Desktop/chatzilla-0.9.76-xr.zip

```

Now navigate to where chatzilla has been installed.
```
cd /usr/lib/chatzilla
```

Now make everything readable and executable (because it doesn't by default).
```
sudo chmod a+rx *
sudo chmod a+rx *
sudo chmod a+rx chrome/icons/default/*
sudo chmod a+rx chrome/branding/*
sudo chmod a+rx defaults/preferences/*
sudo chmod a+rx extensions/*/*

```

Ok now obviously you'll want a shortcut to run chatzilla, one way to do this is to right click on the ubuntu logo and selecting 'edit menu' which will start 'Alacarte Menu Editor'.

Then left click on 'Internet' and then click file -> New Entry
Name: chatzilla
comment:
command: ```
/usr/lib/chatzilla/chatzilla
```

Note: It may come up with a 'malformed file error on 'install.rdf' but I have not found this to be an issue, so you can probably just ignore the error messege.

This how to was created with the help of:
[http://chatzilla.rdmsoft.com/xulrunner/](http://chatzilla.rdmsoft.com/xulrunner/)

---

### Post by kindofabuzz on 2008-03-26
you have to do a sudo chmod a+rx chrome/* also

---

### Post by mykmelez on 2008-11-12
It's not a good idea to randomly "make everything readable and executable."  It's better to fix the specific permissions that are wrong so that they are correct.

For the Chatzilla 0.9.83 package available from [http://chatzilla.rdmsoft.com/xulrunner/](http://chatzilla.rdmsoft.com/xulrunner/), the files with incorrect permissions are the following (inside the /usr/lib/chatzilla directory):

[LIST]
[*]chrome/chrome.manifest
[*]defaults/preferences/update-prefs.xr.js
[*]chrome/icons/default/chatzilla-window16.xpm
[*]chrome/icons/default/chatzilla-window.ico
[*]chrome/icons/default/chatzilla-window.xpm
[/LIST]

All these files should be set to permissions 644 (-rw-r--r--), i.e. the owner (root) has read and write access, while the group and others have only read access:

```
cd /usr/lib/chatzilla
sudo chmod 644 chrome/chrome.manifest defaults/preferences/update-prefs.xr.js chrome/icons/default/chatzilla-window16.xpm chrome/icons/default/chatzilla-window.ico chrome/icons/default/chatzilla-window.xpm

```

I have reported the permissions problems to the package maintainer.

Note also that xulrunner is now available from Ubuntu's package repository.  The "xulrunner" package is version 1.8, while the "xulrunner-1.9" package is version 1.9, which is a stable release (the same code used in Firefox 3; see [https://developer.mozilla.org/en/XULRunner](https://developer.mozilla.org/en/XULRunner) for more info) and probably the preferable one.

---

### Post by mykmelez on 2008-11-17
Note: Chatzilla 0.9.84 is now available (from the [Chatzilla on XULRunner web site]("http://chatzilla.rdmsoft.com/xulrunner/")), and its files all have the correct permissions, so there's no need to fix them.

---

### Post by tpapastylianou on 2009-11-03
Just a thought.
If what you're trying to achieve is simply to launch chatzilla ONLY without having to launch the firefox browser first  (rather than actually having a firefox-installation-independent chatzilla, which is what's been described above, I believe), then a simple way to do it is to make a launcher for the command "firefox -chat" as mentioned in the official chatzilla faq ([http://chatzilla.hacksrus.com/faq/#start](http://chatzilla.hacksrus.com/faq/#start))

Google "chatzilla logo" to customize your launcher completely with its own icon. I put mine in the .mozilla->chatzilla folder and linked to it :)

Note that you can specify an irc:// URL too in that, e.g.
[indent][font=courier]firefox -chat irc://irc.freenode.org/ubuntu[/font][/indent]
(if you just do    [font=courier]firefox irc://irc.freenode.org/ubuntu[/font]  ,   this will first launch the browser with an empty tab, and only subsequently open chatzilla in that channel)

---

### Post by JamesTheAwesomeDude on 2013-01-07
When I try to --register-user, it says "Error: unrecognized application.ini path.

What do I need to do?

---

