---
title: "Test gnome software - replacement for USC"
date: 2016-01-15
forum: Ubuntu Development Version
---

### Post by grahammechanical on 2016-01-15
Here is where I read about it.

[http://www.omgubuntu.co.uk/2016/01/test-new-ubuntu-16-04-software-center](http://www.omgubuntu.co.uk/2016/01/test-new-ubuntu-16-04-software-center)

It is not yet ready to go into the xenial archive. So, we install a PPA. Remember to run dis-upgrade before installing gnome-software. Get dependency errors otherwise. There is a script that we can download appstream.sh. It is supposed to populate gnome software. I could not figure out the command to run a script.

Gnome software does not at first appear in the Dash. Load it from the terminal. Then lock its icon to the Launcher. From then on it appears in the Dash. It is blisteringly fast at loading.

Regards.

---

### Post by sammiev on 2016-01-15
Thanks grahammechanical

---

### Post by rrnbtter on 2016-01-16
Greetings,
sudo apt install appstream

It works but you would have to be a die-hard gnome'r to prefer this to Unity Software Center.

---

### Post by sammiev on 2016-01-16
I started up my computer this morning and had a notification from GSC that updates were available and if I wanted to install them.

---

### Post by grahammechanical on 2016-01-16
> **sammiev said:**
> I started up my computer this morning and had a notification from GSC that updates were available and if I wanted to install them.

I got that yesterday in the xenial I was going to install gnome software on. The update did not change USC into gnome software. Installing gnome software from the PPA is supposed to remove USC. It least that is the way I read things. But that did not happen. I have another install of xenial where I am letting things take place naturally. Except of the occasional dist-upgrade.

At present gnome software has very few apps in the store. The script appstream.sh is supposed to populate gnome software with apps. I think that installing gnome software would install appstream. I will check it out.

Regards.

---

### Post by sammiev on 2016-01-16
I used Software Updater tonight and noticed a wonderful change. 

Greeted with a detailed display as you would expect from using the terminal.

Bad part was I had to enter in my password before the check and then again before the install. ( Usually once is enough )

---

### Post by DogMatix on 2016-01-16
> **grahammechanical said:**
> Here is where I read about it.

[http://www.omgubuntu.co.uk/2016/01/test-new-ubuntu-16-04-software-center](http://www.omgubuntu.co.uk/2016/01/test-new-ubuntu-16-04-software-center)

It is not yet ready to go into the xenial archive. So, we install a PPA. Remember to run dis-upgrade before installing gnome-software. Get dependency errors otherwise. There is a script that we can download appstream.sh. It is supposed to populate gnome software. I could not figure out the command to run a script.

Gnome software does not at first appear in the Dash. Load it from the terminal. Then lock its icon to the Launcher. From then on it appears in the Dash. It is blisteringly fast at loading.

Regards.

I also read the OMGubuntu post. I got itchy trigger fingered and took the plunge by adding the PPA. I ran the downloaded shell script with:

```
sudo sh appstream.sh
```

Although it doesn't seem to have been correctly populated with installable software. However, It does list installed software. It also showed up in the Dash searching with the term 'software'.

USC was not replaced it has installed alongside. Also little glitch with the theme (square black corners on the window as noticed with other apps)

---

### Post by grahammechanical on 2016-01-16
@DogMatix

Thank you. I learnt something.

Regards.

---

### Post by mc4man on 2016-01-16
you could probably read some of the recent comments here - [https://lists.ubuntu.com/archives/ubuntu-desktop/2016-January/thread.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2016-January/thread.html)

---

### Post by philinux on 2016-01-17
Testing tomorrow.

---

