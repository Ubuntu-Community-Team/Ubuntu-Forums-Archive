---
title: "Ubuntuzilla Firefox/Thunderbird global defaults and printing defaults?"
date: 2010-04-26
forum: Ubuntuzilla
---

### Post by RParr on 2010-04-26
Have used Ubuntuzilla to install Firefox 3.6.x and Thunderbird 3.0.x on Ubuntu Hardy 8.04.

Works fine, for the most part, but having some trouble printing.  The print dialog always defaults to the first CUPS printer (ink1) even though the CUPS default is set to laser2 and the PRINTER environment variable is set to laser2.

May be suffering some bit rot and am trying to determine how/where the Ubuntuzilla variant of the Mozilla built Firefox/Thunderbird gets it's default settings.

Is the PRINTER (or older MOZ_PRINTER_NAME) variable read by this version/packaging of Firefox and/or Thunderbird?

Does this version/packaging pay attention to /etc/firefox and/or /etc/thunderbird (where Debian/Ubuntu allow global defaults)?

Where is the preferred location / method for establishing global defaults, etc.?

Thanks
R.Parr, Temporal Arts

---

### Post by nanotube on 2010-04-26
hi,

the packaging doesn't really do anything at all to the mozilla-distributed builds, except for sticking them inside a .deb.

you are sure to observe the same behavior if you just download the .tar.gz from mozilla.com, extract, and run. 

so you probably will get more informative answers if you ask directly on a mozilla forum...

---

### Post by RParr on 2010-04-27
Thanks for the reply.

I have asked on the Mozilla Thunderbird newsgroup but so far no replies.

Thanks again

R Parr, Temporal Arts

---

### Post by nanotube on 2010-04-27
ok, please post back here if you find anything out - it may come in handy to others in the future. :)

---

