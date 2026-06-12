---
title: "Hanging reboot"
date: 2008-10-26
forum: Server Platforms
---

### Post by jonke_ on 2008-10-26
I upgraded a machine from 7.10 to 8 with do-release-upgrade from a ssh connection.
For some unknown reason this machine didn't pass the setup console part
 It stalls on  * Setting up console font and keymap... (like forever)

ctrl-c and try with dpkg --configure -a.
still no luck.

so, I restart the machine... or so I think.
Because sudo shutdown -r now don't work.
sudo init 6 don't work.
Something seems to be locking my attempts to reboot the machine.
(and I have to wait till tomorrow to go to location where the server actually are).

---

### Post by jonke_ on 2008-10-27
It turned out that for some reason, a tty console had alot of gibberish and didn't respond. After killing all the ttys the shutdown worked as it was supposed to do. I don't think that the gibberish came from the do-relase-upgrade or anything with the upgrading part at all but mere a random thing because some keyboard had been sending some very weird things into this machine.

---

