---
title: "[SOLVED] Ubuntuzilla 4.4.0 released"
date: 2007-08-23
forum: Ubuntuzilla
---

### Post by nanotube on 2007-08-23
Just made a new release of ubuntuzilla, 4.4.0.

the major new feature is the addition of "removeupdater" action, that takes out the update checking cronjobs (as a counterpart to "installupdater" that puts it in)
also made the download steps more robust, with multiple retries in case of failure. 

i have tested all the changes pretty well, so should be bug-free, but if anyone cares to play around with it some more, please do so. :)

---

### Post by r_l on 2007-08-25
Hi, thank you for the program.

I use ubuntuzilla to install thunderbird2, but the Ubuntu update manager keep popping up to ask for security update 15.0.12 tp 15.0.13.  I know that this is more of the Updater's issue than to Ubuntuzilla, but when I looked at my Synaptic manager, I saw that all my thunderbird packages are listed as 1.5++.  Is this normal?

If not, will the new version help with this problem?

Thanks.

---

### Post by Dark Star on 2007-08-25
Thanks for the updates :)

---

### Post by nanotube on 2007-08-26
> **r_l said:**
> Hi, thank you for the program.

I use ubuntuzilla to install thunderbird2, but the Ubuntu update manager keep popping up to ask for security update 15.0.12 tp 15.0.13.  I know that this is more of the Updater's issue than to Ubuntuzilla, but when I looked at my Synaptic manager, I saw that all my thunderbird packages are listed as 1.5++.  Is this normal?

If not, will the new version help with this problem?

Thanks.

hi, 
yes, this is quite normal and nothing to worry about. see this faq item on the ubuntuzilla site for more info:
[http://ubuntuzilla.wiki.sourceforge.net/#tochome18](http://ubuntuzilla.wiki.sourceforge.net/#tochome18)

---

### Post by nanotube on 2007-08-26
> **Dark Star said:**
> Thanks for the updates :)

enjoy :)

---

### Post by r_l on 2007-08-26
> **nanotube said:**
> hi, 
yes, this is quite normal and nothing to worry about. see this faq item on the ubuntuzilla site for more info:
[http://ubuntuzilla.wiki.sourceforge.net/#tochome18](http://ubuntuzilla.wiki.sourceforge.net/#tochome18)

Much thanks for the reply!

---

### Post by aysiu on 2007-08-26
Perhaps one of the default behaviors (though this can be something asked of the user) would be the locking of package versions for the Mozilla application being installed.

Presumably, the person is using Ubuntuzilla in order to use the Mozilla build of Firefox (or Thunderbird or Seamonkey) and not the Ubuntu repositories version. The prompt for an update of the old version just confuses people.

---

### Post by por100pre1 on 2007-08-26
Thanks for the update. :)

---

### Post by nanotube on 2007-08-26
> **aysiu said:**
> Perhaps one of the default behaviors (though this can be something asked of the user) would be the locking of package versions for the Mozilla application being installed.

Presumably, the person is using Ubuntuzilla in order to use the Mozilla build of Firefox (or Thunderbird or Seamonkey) and not the Ubuntu repositories version. The prompt for an update of the old version just confuses people.

interesting thinking, but at least in the case of firefox, the repos gecko engine gets used in other ubuntu software (i think add applications may be one of them, and some others), so the security updates to ff1.5 would still be quite recommended. one wouldn't want to ignore them.

may be possible with thunderbird whithout repercussions, but again... a security update never hurt anyone. so i think it's better to leave as is... that's why we have the faq item after all - and these forums to point people who don't read the faq to said faq. :)

---

