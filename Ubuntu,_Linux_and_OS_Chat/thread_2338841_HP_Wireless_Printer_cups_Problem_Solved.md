---
title: "HP Wireless Printer cups Problem Solved"
date: 2016-10-02
forum: Ubuntu, Linux and OS Chat
---

### Post by littlemul on 2016-10-02
Just spent 12 hours getting my HP Officejet Pro 8610 back online after a major printer dropout.
Tried HP for help, suggestions there included reboot your computer, reboot your printer and reboot your wireless router.
Did all three but no solution to my problem.

I got the following print error message:-
There was an error during the CUPS operation: 'server-error-internal-error'.
Looked on line for Ubuntu Help and found an old thread dealing with this issue.
Very detailed advice about adding lines to the /etc/cups/cupsd.conf file
Sorry but this was way beyond my newbie pay grade.
The best advice was from [                                                      [IMG]https://ubuntuforums.org/customavatars/avatar241895_2.gif[/IMG]                                              ]("https://ubuntuforums.org/member.php?u=241895")                                                                                     [URL="https://ubuntuforums.org/member.php?u=241895"][B][COLOR=#000000]tgalati4
[/COLOR][/B][/URL]
It's possible that your cups installation is badly broken.  Try removing and reinstalling.

Once I had figured out how to do this in Synaptic Package Manager and checked that my Ubuntu 16.04 was up to date
(I needed to adjust the Software & Updates to turn on the Source Code mirror and to turn off the CD-ROM/DVD to get this right).
The reload of cups produced a working GUI that recognised my printer and problem solved.
Thanks tgalati4

---

### Post by DuckHook on 2016-10-02
I am glad that the forums contributed to your finding a solution.

However, because this is not a technical help request&#8230;

*Thread moved to **Ubuntu, Linux and OS Chat** as the more appropriate forum.*

---

