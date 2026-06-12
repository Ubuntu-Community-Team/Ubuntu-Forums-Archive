---
title: "How to restore Java?"
date: 2008-03-15
forum: System76 Support
---

### Post by Vadi on 2008-03-15
Help - Java that came with my serval was working perfectly fine, but along the way, I messed it up. I've uninstalled all java-related packaged now, but I don't know which ones to install back to get it working... could anyone tell please?

---

### Post by thomasaaron on 2008-03-17
Go to System > Administration > Synaptic Package Manager
Search for and install: sun-java6-jdk

When it's finished go to a terminal and run this command:
sudo update-alternatives --config java

Press whatever number corresponds with 'java-6-sun' and press enter.

Now you have sun java 6 installed and configured as your default java version.

---

### Post by Vadi on 2008-03-17
Ok thanks!

---

### Post by Vadi on 2008-03-19
I did that, restarted my firefox, but java applets still don't work. They just come up as gray :(

---

### Post by thomasaaron on 2008-03-19
1. The plugin might already be installed, but just in case...
sudo apt-get install sun-java6-plugin

2. In firefox, go to Edit > Preferences > Content and make sure the "Enable Java" checkbox is checked.

3. Restart Firefox.

4. If that doesn't do the trick, try disabling Desktop effects (System > Prefs > Appearance > Visual Effects > None)

5. If that doesn't work, send me the site with the java applet so I can have a look.

---

### Post by Vadi on 2008-03-19
First step failed...

> vadi@ubuntu:~$ sudo apt-get install sun-java6-plugin
[sudo] password for vadi:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-plugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-plugin has no installation candidate
vadi@ubuntu:~$ 


---

### Post by thomasaaron on 2008-03-19
Go to Synaptic Package Manager and search for it.
I see it there. See screenshot. Do you see the same thing?

---

### Post by Vadi on 2008-03-19
I don't, oddly enough.

---

### Post by thomasaaron on 2008-03-19
Oops. I didn't realize this, but...

I think this is the answer:
[http://ubuntuforums.org/showthread.php?t=596614](http://ubuntuforums.org/showthread.php?t=596614)

I was looking on my old, white Darter. It only takes 32-bit Ubuntu, so that's why I see it and  you don't.

---

### Post by compholio on 2008-03-19
You need to install [nspluginwrapper]("http://packages.ubuntu.com/gutsy/nspluginwrapper") and then install the flash plugin and tell the wrapper to wrap the plugin.  There are some [fedora instructions]("http://www.cyberciti.biz/tips/linux-flash-java-realplayer-under-64bit-firefox.html") you can work from starting at "How do I use this software?" after you've got the wrapper installed.

---

### Post by Vadi on 2008-03-19
It's OK, I need java, not flash

---

### Post by compholio on 2008-03-20
> **Vadi said:**
> It's OK, I need java, not flash
Sorry, replace "flash" with "java" - the plugin is for wrapping any 32-bit plugins to work with a 64-bit browser.

---

### Post by Vadi on 2008-03-20
They use rpms and yums... not exactly what I need here heh. 

I almost got it working via these instructions ([click]("https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins?action=show&redirect=Firefox2AMD64Flash9Java")), just managed to screw up permissions somewhere.. oops.

---

### Post by compholio on 2008-03-20
> **Vadi said:**
> They use rpms and yums... not exactly what I need here heh. 

I almost got it working via these instructions ([click]("https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins?action=show&redirect=Firefox2AMD64Flash9Java")), just managed to screw up permissions somewhere.. oops.

Right, that's why I was suggesting to only follow the directions at the end.  To install in the first place you should just need to run "sudo apt-get install nspluginwrapper".

---

