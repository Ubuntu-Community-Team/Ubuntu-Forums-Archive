---
title: "Seamless mode not working anymore"
date: 2008-04-26
forum: Virtualisation
---

### Post by Lothas on 2008-04-26
I've been using VirtualBox for a while now with Ubuntu as Host and WinXP as guest. For a while it worked great but about 2 months ago the seamless feature stopped working. I waited to see if it got fixed in 8.04 but still no luck.

The VirtualBox runs smoothly but when I press ctrl+L for seamless, the whole thing just disappears and I can't see a thing. If I press ctrl+L again, it comes back. Any ideas why this would happen?

Also, I don't know if I installed properly the non-free usb supporting version but I can't see the usb icon for configuration anywhere. Could there be some problem or am I just using the open-source version?

---

### Post by NNG on 2008-04-26
Seamless mode has a minor bug in it. In order to work properly, at least one window needs to be open and showing on the Desktop. one of the better ways to do this is just to open a folder, make it as small as possible, and drag it out of the way.

Also, regarding your USB, it would seem that you have the open source version if there is no option for it in configuration.

---

### Post by Lothas on 2008-04-27
Actually that is not my problem. I've known of this bug almost since I started using VirtualBox and I didn't have problems with it because I use Google Desktop which is always open. I'll try installing the non-open-source version and see if the problem gets fixed... Any other ideas?

---

### Post by nikolko on 2008-10-24
hmm...
I've noticed, that option -A for rdesktop works not like "seamless", but like "fullscreen" -f option. I have non-ose version, but it behaves same.

---

