---
title: "Downgrade Wine to version 0.9.46"
date: 2009-01-01
forum: Wine
---

### Post by sp3ctum on 2009-01-01
Hi. I would like to test out Wine 0.9.46 to see if it works better with Warcraft 3. I used to have the newest version of Wine, but now I uninstalled it. 
I have Ubuntu 8.04.
This is what I've done on my own so far:

Download the package (wine_0.9.46~winehq0~ubuntu~7.04-1_i386.deb) and try to install it. 
The first error was that there already existed a newer version of Wine. I uninstalled the newest version, and retried the install.
After that the package manager said that it needs the package libldap2, and dpkg reports that it needs version => 2.1.17-1 .

Downloaded libldap2_2.1.30-13.4_i386.deb and tried to install it. It said that it needs the package libgnutls13.

I then downloaded libgnutls13_1.6.3-1ubuntu0.3_i386.deb and tried to install it. It said that it needs the package libopencdk8. I then downloaded libopencdk8_0.5.13-2_i386.deb and installed that.

After that I could install libgnutls13, and after that I tried to install libldap2. The installation resulted in an error:

[SIZE="2"]dpkg: regarding libldap2_2.1.30-13.4_i386.deb containing libldap2:
 libldap-2.4-2 conflicts with libldap2
  libldap2 (version 2.1.30-13.4) is to be installed.[/SIZE]

I tried to uninstall the newer package, but many useful applications that I need (like openoffice) depend on it, so I don't want to.


So my question is, what should I do? Please help me :)

---

### Post by Ng Oon-Ee on 2009-01-01
When trying out older versions of software, I'd recommend compiling from source. There's a HOWTO floating around somewhere on a script which does this for you (the title is something about running multiple versions of wine at once).

Alternatively, your .deb file is merely an archive. You can just extract the needed executables, I think wine 0.9.46 is recent enough that the libraries haven't changed all that much in Ubuntu. This is unsupported, though, the equivalent of manually editing your registry in Windows. Among other things, extracting the executable directly may cause funny bugs due to dependencies not being fulfilled, will cause you not to be able to use Wine directly without calling the entire path to the executable (unless you symlink in /usr/bin), will conflict with any existing Wine, etc.

Things can be bad. If you know what I'm talking about, then proceed, you should be fine. If you're still confused, especially on dependencies, then please use the script I mentioned at the top. Or take this as a chance to learn. Back up everything you need first, though =).

---

### Post by Ng Oon-Ee on 2009-01-01
When trying out older versions of software, I'd recommend compiling from source. There's a HOWTO floating around somewhere on a script which does this for you (the title is something about running multiple versions of wine at once).

Alternatively, your .deb file is merely an archive. You can just extract the needed executables, I think wine 0.9.46 is recent enough that the libraries haven't changed all that much in Ubuntu. This is unsupported, though, the equivalent of manually editing your registry in Windows. Among other things, extracting the executable directly may cause funny bugs due to dependencies not being fulfilled, will cause you not to be able to use Wine directly without calling the entire path to the executable (unless you symlink in /usr/bin), will conflict with any existing Wine, etc.

Things can be bad. If you know what I'm talking about, then proceed, you should be fine. If you're still confused, especially on dependencies, then please use the script I mentioned at the top. Or take this as a chance to learn. Back up everything you need first, though =).

---

### Post by sp3ctum on 2009-01-01
Thanks for the tip. I followed the guide ([http://ubuntuforums.org/showthread.php?t=942269](http://ubuntuforums.org/showthread.php?t=942269)) and got the old wine installed in a separate directory. My framerate has gone up considerably already. I can use the newest wine to emulate other programs besides games.
Thanks again! :)

---

### Post by Ng Oon-Ee on 2009-01-01
You're welcome, glad to help. Normally is a good idea to search out old threads on any specific issues you may have. I also find browsing through  any threads with HOWTO in their titles to be very useful.

---

### Post by sp3ctum on 2009-01-06
Today I learned that Wine 0.9.46 was unable to connect to any games. I then had a bunch of problems, and finally Wine 0.9.45 was the solution to all of them.
I had to turn off everything winecfg had about direct3d to make it work with a decent fps.
I'm posting this in case someone else has the same problem. :)

---

