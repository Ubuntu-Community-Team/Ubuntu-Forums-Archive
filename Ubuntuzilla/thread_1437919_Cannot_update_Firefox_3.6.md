---
title: "Cannot update Firefox 3.6"
date: 2010-03-24
forum: Ubuntuzilla
---

### Post by yaacovk on 2010-03-24
Hello.
i upgrade my Firefox 3.5 to 3.6 by Ubuntuzilla script.
[http://www.techdrivein.com/2010/01/install-firefox-36-in-ubuntu-super-easy.html](http://www.techdrivein.com/2010/01/install-firefox-36-in-ubuntu-super-easy.html)

the Firefox 3.6 worked fine until i had a notification that my Firefox don't has
a permission to update as the image attached:

---

### Post by nanotube on 2010-03-24
quit firefox, run it with "gksudo firefox", run the firefox check for updates, say yes to restart, quit again. now your firefox will be updated.

also note, that ubuntuzilla.py script is essentially deprecated, there's now a repository. read the documentation on the ubuntuzilla site:
[http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/)

if you follow the current repository method, you can just upgrade using the package manager, as you would any other package.

---

### Post by yaacovk on 2010-03-24
Thanks for you tip, it was help.
by the way, do i mast to proceed with the ubuntuzilla instruction for the [COLOR=#000000][FONT=Arial][FONT=Tahoma]future
updates?

Thanks in advance.

Yaacov.
[/FONT][/FONT][/COLOR]

---

### Post by nanotube on 2010-03-24
Hi
well, if you're happy with what you have for the moment, no need to change anything.

but if you want to switch to using the new repo, use the 'ubuntuzilla.py -a remove' command to remove the script version, and then follow the instructions on the ubuntuzilla site to set up the repository.

(note that the repository is only 32bit)

---

