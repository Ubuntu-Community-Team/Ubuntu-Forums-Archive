---
title: "Firefox  1.0.4-1ubuntu3~5.04ubp5 upgrade issues"
date: 2005-06-13
forum: Ubuntu Backports
---

### Post by mtron on 2005-06-13
just a hint to the latest firefox upgrade. i installed today Firefox version 1.0.4-1ubuntu3~5.04ubp5 with "sudo apt-get dist-uprade" and it generated an error due to the package mozilla-firefox-gnome-support. ( i think it's a small bug in the dummy package due to the rename)

so type 
```

sudo apt-get update
sudo apt-get install firefox-gnome-support
sudo apt-get dist-upgrade 
```

and the update will go ok. after the update i typed "about:config" in the adress bar to check the general.vendor.sub and it also resulted in an error, but after a x-server restart (ctrl & alt & backspace) it's ok now.

---

### Post by gte258v on 2005-06-15
I'm having issues with the dist-upgrade. I'm getting:

```
$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  mozilla-firefox-gnome-support: Depends: firefox-gnome-support but it is not installed
E: Unmet dependencies. Try using -f.
```

Should I follow your instructions in reverse order, i.e.:

```
sudo apt-get install firefox-gnome-support && sudo apt-get dist-upgrade
```

Thanks for the help.

---

### Post by mtron on 2005-06-15
sure.

i did the upgrade and got the same, then i installed the firefox-gnome-support and afterwards again the dist upgrade.

thanks for the hint i will correct the first post.

---

