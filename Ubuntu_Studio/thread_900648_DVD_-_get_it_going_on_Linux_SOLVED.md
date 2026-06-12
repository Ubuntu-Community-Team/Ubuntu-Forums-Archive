---
title: "DVD - get it going on Linux SOLVED"
date: 2008-08-25
forum: Ubuntu Studio
---

### Post by smakarl on 2008-08-25
*        &#8236;The* ´&#8236;get-it-going*´ &#8236;minimum* ´ &#8236;to the point*´ &#8236;setup for DVD playing on Linux* – &#8236;IT WORKS*!
         -------------------------------------------------------------------------------------------------------------*

Install VLC Player* – &#8236;it installs many dependencies for which you are looking.

install libdvdread3*                    &#8236;By the method you prefer:
sudo apt-get install libdvdread3* &#8236;in the terminal,* &#8236;or the Synaptec Package Manager.

cd* &#8236;/usr/share/doc/libdvdread3*  &#8236;Go to the libdread3* &#8236;directory

ls install-css.sh*                         &#8236;Verify that you have the program with the CODECs.
*                                                 &#8236;Executables are in green.

sudo chmod* &#8236;755* &#8236;install-css.sh*  &#8236;Secure maximum executability

sudo* &#8236;./install-css.sh*                   &#8236;Execute the installer as the super user

*                                                  &#8236;Done.

Install your favorite Media player and enjoy.
I prefer the VLS PLAYER because you can play most any audio* &#8236;/* &#8236;video media* &#8236;-* 
and anything that it plays you can stream over your network to all of your computers.
It runs on Linux,* &#8236;Windows.* &#8236;It will stream to Windows Media player.
To switch your default auto-run media player:

---

