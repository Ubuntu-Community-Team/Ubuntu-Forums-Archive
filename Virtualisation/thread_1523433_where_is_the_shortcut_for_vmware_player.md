---
title: "where is the shortcut for vmware player?"
date: 2010-07-03
forum: Virtualisation
---

### Post by Bif Powell on 2010-07-03
I'm sorry I'm not asking this on vmware's site, but f that site, to be honest.

Brand new install of ubuntu 10.04 64.  First programs I installed were chrome then vmware player.

I downloaded a .bundle file - fwiw it wasn't obvious what to do with the .bundle file.  Not even anything in a readme that I could find - it wasn't even on vmware's site when I did find the answer Googling showed doing $sudo sh VMware-Player-3.1.0-261024.x86_64.bundle made it install.

Everything ran really well and smoothly and installation was a success!  I couldn't have hoped for a better installation process after that.

But I don't see an icon and I can't find anything telling me where the program was installed to.

I then rebooted after reading that maybe it wasn't showing up in menus.  After some googling I found:

Categories=Application;Internet;Network;WebBrowser;

needed to be added to a /usr/share/applications/google-chrome.desktop

to make chrome show up and that did make chrome show up, but I could find no corresponding entry/file that I might edit to make the shortcut for vmware player to show up.

I installed again, and it went so smoothly this time that it didn't even prompt me for anything it just said "everything is installed properly".  That's great.

I still can't launch vmware player.  Any guidance appreciated.

---

### Post by darkmaxa on 2010-07-04
I have exactly the same problem.

I've installed Chrome, VMWare and Sybase ASA, and everything went fine. Immediately after installation VMWare and Sybase ASA icons was located in "System Tools", but after restart they gone. On the other side, Chrome icon is still in the "Internet" menu.

---

