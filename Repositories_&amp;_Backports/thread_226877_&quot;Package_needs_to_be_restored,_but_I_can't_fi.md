---
title: "&quot;Package needs to be restored, but I can't find an archive&quot;"
date: 2006-07-31
forum: Repositories &amp; Backports
---

### Post by drfox on 2006-07-31
I'm getting an error message "The package mfc9700lpr needs to be reinstalled, but I can't find an archive for it" from Package Manager.

This was a package I downloaded from Brother and opened from my Desktop. 
I got an error message when I tried to install it, and now Synaptic seems to be broken. 

How can I clear this error message?

TIA   Larry

---

### Post by timschul on 2008-01-06
Hi drfox,

Here's the thread I found and asked you about in a private message yesterday.  Just noticed the date - ancient history, I'm afraid.

Any recollection of how you solved this?

---

### Post by qwerty1r on 2011-06-13
I just had the same problem and managed to solve it this way:

1) open the problematic file mfc9700lpr.postrm with this command:
sudo pico /var/lib/dpkg/info/mfc9700lpr.postrm

2) navigate to the line(s) that do not start with a '#' sign and delete them (Ctrl-k will delete the entire line quickly)

3) Save the changes (Ctrl-x, then answer Yes)

4) Force the removal of the offending package: 
sudo dpkg --remove --force-remove-reinstreq mfc9700lpr 

Hope this works for everyone else having this problem!

---

### Post by Elfy on 2011-06-13
Closing 3 year old thread.

---

