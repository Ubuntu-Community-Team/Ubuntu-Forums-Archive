---
title: "[SOLVED] spell check not working with thunderbird 2.0 ubuntuzilla"
date: 2007-08-09
forum: Ubuntuzilla
---

### Post by Joel Duckworth on 2007-08-09
After installing the latest version of Thunderbird using the ubuntuzilla script the spell checker is not working. In the preferences none of the dictionaries are loading in the list. 

Any ideas?

---

### Post by nanotube on 2007-08-09
hmm, i haven't come across the problem before...

try starting a new message, type something, then from the menu choose options -> check spelling, and see if that does anything...

---

### Post by Joel Duckworth on 2007-08-09
I was using 1.5 before hand and I think the dictionaries are linked to the OpenOffice dictionaries. I just download and installed a new dictionary in my ubuntuzilla version and it worked. Maybe there's some way to link the new version the existing dictionaries on the system? Something the script could do.

---

### Post by nanotube on 2007-08-09
hmm, well, maybe, but i don't know where tbird stores dictionaries, nor do i know where openoffice stores dictionaries... so i'd have to do some investigative work there. :) unless you already know and can help me out with some tips. :)

---

### Post by Joel Duckworth on 2007-08-10
I think that the dictionaries come from /usr/share/myspell/dicts/ to upgrade a dictionary for the ubuntu release of thunderbird I could simply install the appropriate myspell package with apt-get and I believe that openoffice uses these too

---

### Post by nanotube on 2007-08-10
> **Joel Duckworth said:**
> I think that the dictionaries come from /usr/share/myspell/dicts/ to upgrade a dictionary for the ubuntu release of thunderbird I could simply install the appropriate myspell package with apt-get and I believe that openoffice uses these too

ah-ha. :)
well, try the following, and see if your dicts from openoffice appear:
```
sudo mv /opt/thunderbird/dictionaries /opt/thunderbird/dictionaries.bak
sudo ln -s /usr/share/myspell/dicts /opt/thunderbird/dictionaries

```

restart tbird, and see if that makes things work like you want them to. :) 

if that works out well, i might add that to the ubuntuzilla installation procedure.

thanks for your help!

edit: oh, and if you want to go back and undo all that, just do
```
sudo rm /opt/thunderbird/dictionaries
sudo mv /opt/thunderbird/dictionaries.bak /opt/thunderbird/dictionaries
```

---

### Post by Joel Duckworth on 2007-08-10
it worked by creating the link! but I didn't have /opt/thunderbird/dictionaries  there in the first place so the first command failed. Not sure why I didn't have that directory, I installed the en-GB version of TB from the ubuntuzilla script... maybe thats why

FYI when I installed the dictionary by downloading, it put at as an extension in my ~/.mozilla-thunderbird/vzuqsty9.default/extensions

I also skipped the gpg when installing because I couldn't access the sites through my firewall (if that makes any difference, I doubt)

Thanks for your help!

---

### Post by nanotube on 2007-08-10
cool, thanks for your feedback. i guess now we know why no dictionaries were showing up - the default dictionaries directory was not even there in your /opt install (i wonder why...)

well, i guess now we can all look forward to a new feature of the ubuntuzilla script, thanks to you. :)

it also looks like firefox and seamonkey would benefit from the same.

---

