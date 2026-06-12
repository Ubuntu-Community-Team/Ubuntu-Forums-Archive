---
title: "VMware: &quot;Kernel headers for version 3.2.0-40-generic-pae were not found&quot;"
date: 2013-04-13
forum: Virtualisation
---

### Post by Ergot on 2013-04-13
Hey guys! 

New to linux and the forum but have fallen in love with the format and egar to learn more, but I do need to run Windows 7 for school assignments and you know it's always fun to play around with multiple options :p. So I have managed to get VMplayer installed but I get an error message when attempting to launch. 

"Kernel headers for version 3.2.0-40-generic-pae were not found, If you installed them in a non-deafult path you can specify the path below. Otherwise refer to your distribution's documentation for installation instructions and click Refrest to search again in default locations." 

I am incredibly new to Linux and computers in general (first semester student) and can't make heads or tails of this, I'm not even really sure what a Kernel Header is. But it gets a little more complicated from here, I don't have wifi on the computer (doesn't even think it has wifi capabilities, something is missing) and my dog knocked my computer over the other day and ethernet port no longer works. So I guess what I'm asking is how do I get these kernel headers and how do I install them via an external storage device? I'm running ubuntu 12.04 32bit on a machine built for vista (Dell inspiron 1545 2.0 GHz x 2, 2.9 GiB) if that helps. Any direction or advice you can offer would be much appreciated, I imagine this will be a frustrating but educational experience.

---

### Post by Cheesehead on 2013-04-14
> **Ergot said:**
> "Kernel headers for version 3.2.0-40-generic-pae were not found"

Kernel headers are files used when some new software (like a VM host) needs to be compiled to use the kernel. Each time you update the kernel, that software must be recompiled against the new kernel. Normally, the package manager takes care of that for you.

Header files are not included with the installed kernel, but are trivial to install using the package manager.

If you have the package 'devtools' installed, you can check to see if linux headers for any kernel are installed using the command:
```
$ rmadison linux-headers-3.2.0-40-generic-pae

linux-headers-3.2.0-40-generic-pae | 3.2.0-40.64 | precise-security | i386
linux-headers-3.2.0-40-generic-pae | 3.2.0-40.64 | precise-proposed | i386
linux-headers-3.2.0-40-generic-pae | 3.2.0-40.64 | precise-updates | i386
```

You should be able to use the following command to install the linux headers. Then try re-installing VMplayer. Watch the reinstallation carefully for error messages, and paste them here.
```
sudo apt-get install linux-headers-3.2.0-40-generic-pae
```

---

### Post by Ergot on 2013-04-15
Appreciate the response!

 

 I attempted    to execute the command 'rmadison linux-headers-3.2.0-40-generic-pae' and told me I needed to install program 'rmadison' and gave me a line to type to install 'devscripts' so I attempted but I have no internet and got many &#8220;Failed to fetch&#8221; (missing a driver maybe for the wireless and dog broke my Ethernet port) Is it essential I install these via a connection through the terminal? When reading about installing VMplayer it was recommend packages be installed this way. Is there a way to work around this or should I focus on fixing my network connectivity before attempting to get these headers and re-install? Thank you for your time
 

 I did enter 'sudo apt-get install linux-headers-3.2.0-40-generic-pae' and said it's the newest version if that sheds any more light on the situation.

---

### Post by dcstar on 2013-04-18
> **Ergot said:**
> 
..........
I don't have wifi on the computer (doesn't even think it has wifi capabilities, something is missing) and my dog knocked my computer over the other day and **ethernet port no longer works**. 


Get a working Internet connection and then things that assume and require that you have a working connection just might function.

---

