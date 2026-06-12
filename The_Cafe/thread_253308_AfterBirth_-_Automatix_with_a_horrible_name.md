---
title: "AfterBirth - Automatix with a horrible name"
date: 2006-09-08
forum: The Cafe
---

### Post by dyssident on 2006-09-08
I, like every new Ubuntu user, love Automatix. However, I have a few problems with it. Having some time on my hands, I decided to try my hand at hacking some improvements. The product is AfterBirth. Im concentrating on getting the basics down, so AfterBirth currently only does free/nonfree codecs, fonts, security apps and browser plugins. 

AfterBirth has the same goals as Automatix, but aims toward the following improvements

- Be more sane about packages. Take better advantage of the Debian package system. Use apt instead of wget-ing individual debs everywhere possible. Make setup improvements in packages not in code so nonusers can take advantage of tweaks.
- Be more task oriented. Group programs into common needs like Laptop Essentials and P2P File Sharing. If you need AfterBirth, you probably dont know much about which specific programs you want to install.
- Dont hose sources.list. Adds necessary repositories to existing sources.list. Leave repositiories in sources.list when possible so we can take advantage of future updates. 
- Better interface. Uses Perl/Gtk2 for better Gnome integration. Mymics the look of Synaptic system updater tool.

Im in need of people with new installs willing to test AfterBirth out; any feedback would be much appreciated. [You can download the package here](http://www.voxpopulimedia.com/pub/afterbirth/afterbirth_0.0.1-1_i386.deb). You will need to enable the universe repository and install libgtk2-gladexml-perl before installing. After installation, run `afterbirth` from the command line. The rest is self explanatory.

VERY EXPERIMENTAL. Only use on a system you can afford to loose.

---

