---
title: "Firefox 3.5 plugins 64-bit"
date: 2009-08-05
forum: Ubuntuzilla
---

### Post by prkos on 2009-08-05
I used ubuntuzilla to install 3.5 and everything is working fine, except the plugins. 

I was able to get the flash to work by copying the libflashplayer.so from  /usr/lib/flashplugin-installer/libflashplayer.so into .mozilla/plugins but other plugins (gecko and mplayer for example) won't work, while they worked in 3.0.12. 

btw there are some broken symlinks in /usr/lib/firefox/plugins/, is that expected?

---

### Post by nanotube on 2009-08-05
Hi

Don't know if it's possible, but you could try pulling the 32bit versions of java and mplayer plugins? Otherwise... you could grab those packages from packages.ubuntu.com, say, extract them manually into the plugins dir...

Unfortunately, mozilla doesn't make 64bit builds, so... that's that.

As far as /usr/lib/firefox/plugins/ - ubuntuzilla doesn't touch that dir at all, so can't tell you anything about it, really. On the recent versions of ubuntu (intrepid and on), the synaptic-installed plugins actually live in /usr/lib/xulrunner-addons/plugins, not in /usr/lib/firefox/plugins...

---

### Post by andrejus on 2009-08-12
Hello!

I am new to Ubuntu (v 9.04). I am very positive about all the system (speed, look, feel etc).

But I want a bit more so I've installed Firefox 3.5.2 with Ubuntuzilla. I have the same problems as prkos.

My Firefox 3.5.2 can not find plugins. How can I enable all the plugins form the previus version of Fireforx (3.0.xx)?

Thanks to Ubuntuzilla I've went back to Firefox 3.0.xx.

If anyone has a clue please; write down a guide for dummies :)

BR

---

### Post by swong on 2009-08-12
I am using 9.04 64-bit, and I am running FF 3.5.2 with no issues, all my plugins/addons are working ok.  But I did not install from Ubuntuzilla, I used the Ubuntu repositories.

I installed using Synaptic Package Manager -> search for "firefox-3.5" -> then install

It will install 3.5, then rely on the updates to move up to 3.5.2

---

### Post by nanotube on 2009-08-12
> **andrejus said:**
> Hello!

I am new to Ubuntu (v 9.04). I am very positive about all the system (speed, look, feel etc).

But I want a bit more so I've installed Firefox 3.5.2 with Ubuntuzilla. I have the same problems as prkos.

My Firefox 3.5.2 can not find plugins. How can I enable all the plugins form the previus version of Fireforx (3.0.xx)?

Thanks to Ubuntuzilla I've went back to Firefox 3.0.xx.

If anyone has a clue please; write down a guide for dummies :)

BR

Hi
please see the ubuntuzilla faq section for 64bit users.

[https://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Ubuntuzilla_FAQ#.5BThunderbird.2C_Firefox.5D_For_64-bit_Ubuntu_users](https://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Ubuntuzilla_FAQ#.5BThunderbird.2C_Firefox.5D_For_64-bit_Ubuntu_users)

---

### Post by Skrypt on 2009-08-16
nm

---

### Post by cujo_77 on 2009-08-16
OK, I am going to ask a very basic question because I am very new to Linux.  How can I copy the libflashplayer.so file to the plugins folder.  I can't drag and drop it and when I try to use the terminal I get an error message saying there is an error message with find there .so file.  I may be typing it in wrong.

---

### Post by nanotube on 2009-08-16
Hi
you can do everything in the gui
open up the file manager, make sure "show hidden files" is enabled (in file manager, select view -> show hidden files)
then navigate from your home directory to the '.mozilla' directory. there, if you see a "plugins" directory, navigate there, if not, create the plugins dir first.

now, extract the .so file to your desktop, from the zipfile you downloaded from adobe, then drag it into the 'plugins' directory which you have open in your file manager.

then, restart firefox, and flash should be working.

---

### Post by Marc van der Wijst on 2009-09-02
> **andrejus said:**
> Hello!

I am new to Ubuntu (v 9.04). I am very positive about all the system (speed, look, feel etc).

But I want a bit more so I've installed Firefox 3.5.2 with Ubuntuzilla. I have the same problems as prkos.

My Firefox 3.5.2 can not find plugins. How can I enable all the plugins form the previus version of Fireforx (3.0.xx)?

Thanks to Ubuntuzilla I've went back to Firefox 3.0.xx.

If anyone has a clue please; write down a guide for dummies :)

BR


I had the same problem, but I fixed it. Shiretoko can be downloaded with the Synaptic Package Manager (firefox-3.5), but I just didn't like the icon and the window title. :)

So I got firefox 3.5.2 with ubuntuzilla (in a terminal: ubuntuzilla.py -a install -p firefox). Installs neatly and works, except for the mplayer plugins.
An extensive web search just didn't give me an answer. But a hint did.

Firefox is 32 bit, my Jaunty 64 bit. The mozilla-mplayer package on my system is 64 bit and firefox expects 32 bit plugins.
Here is a quick howto:
- download mozilla-mplayer_3.55-1.1ubuntu1_i386.deb (32bit package) from [http://packages.ubuntu.com/jaunty/i386/mozilla-mplayer/download](http://packages.ubuntu.com/jaunty/i386/mozilla-mplayer/download)
- right click the file and choose "Open with Archive Manager"
- doubleclick data.tar.gz
- extract the files from ./usr/lib/mozilla/plugins/ to a temp dir ex. /tmp/mplayeri386 (the ten files are mplayerplug-in*.so/xpt)
- close firefox
- open a terminal
- backup firefox 3.5.2 plugins dir: sudo mv /opt/firefox/plugins /opt/firefox/plugins.org
- make new plugins dir: sudo mkdir /opt/firefox/plugins
- copy 32bit mplayer plugins: sudo cp /tmp/mplayeri386/* /opt/firefox/plugins/
- start firefox and check by typing in the address bar "about : plugins" (without the spaces or quotes)
- get popcorn :)

:popcorn:

---

