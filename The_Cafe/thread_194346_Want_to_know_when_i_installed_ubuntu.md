---
title: "Want to know when i installed ubuntu"
date: 2006-06-11
forum: The Cafe
---

### Post by sbuntu on 2006-06-11
Hi

Is there a way to find out when i installed the xubuntu on my desktop.

I would like to have something like a widget on my desktop that tells me when the installation was done.

sort of like .... BORN ON 4TH OF JULY

this way i can tell when my friends ask me how long i have had it

i use xubuntu 6.06

---

### Post by glinsvad on 2006-06-11
Using the date-attributes of logfiles created during first install might work:
```

ls -l /var/log/installer/messages | sed -r 's%^.*[ \t]+([0-9]+-[0-9]+-[0-9]+)[ \t]+.*$%\1%'

```

There's probably an easier way, but for now...

---

### Post by glinsvad on 2006-06-11
Even better, snip out the first line of text from the install logfile:
```

head base-config.log* --lines=1 | sed -r 's%Script started%Born%;s%([0-9-]+)T([0-9-]+)%\1 at \2%'

```

(I'm not sure its exact filename, hence the asterix: mine is base-config.log.1)

EDIT: path-screwup
```

head /var/log/base-config.log* --lines=1 | sed -r 's%Script started%Born%;s%([0-9-]+)T([0-9-]+)%\1 at \2%'

```

---

