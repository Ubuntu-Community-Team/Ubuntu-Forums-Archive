---
title: "How can i unistall Ubuntu One?"
date: 2013-07-17
forum: Ubuntu One (CLOSED)
---

### Post by dinodxr on 2013-07-17
i think there's a command? anyone knows? grazie ;) (Ubuntu 12.04)

---

### Post by Irihapeti on 2013-07-18
Do you mean that you want to get rid of Ubuntu One altogether, or that you want to remove your user details so that you can solve an authorisation problem?

---

### Post by dinodxr on 2013-07-18
i'm not using ubuntu one so i want to get rid of it

---

### Post by Irihapeti on 2013-07-19
I think that if you try to remove Ubuntu One completely, you risk removing other essential things as well.

The Ubuntu One FAQ at [https://one.ubuntu.com/help/faq/how-do-i-completely-remove-and-reinstall-ubuntu-one/](https://one.ubuntu.com/help/faq/how-do-i-completely-remove-and-reinstall-ubuntu-one/) will allow you to remove the client software but not all the libraries and so on.

---

### Post by bwallum on 2013-08-05
I find Ubuntu One too intrusive. For example, there is a cloud icon in my top panel that has an attached Ubuntu One menu. One item on the menu is to turn Ubuntu One off. When I do this it turns itself back on again. I don't like this lack of control, particularly where network access is concerned. Does anybody have explicit instructions in removing this application? I am seriously considering changing distros if I can't fully control Ubuntu One.

EDIT
Found the relevant bits:-

Run the following in a terminal session:

    ```
killall ubuntuone-login ubuntuone-preferences ubuntuone-syncdaemon
```
```
sudo rm -rf ~/.local/share/ubuntuone
```
```
rm -rf ~/.cache/ubuntuone
```
```
rm -rf ~/.config/ubuntuone
```
```
mv ~/Ubuntu\ One/ ~/UbuntuOne_old/``
```

If you have UDFs, rename the respective folders. E.g. if you were syncing Documents folders, rename it to Documents_old.

Delete Ubuntu One token:

        Open the Dash by clicking the Ubuntu Logo in the upper left corner. Type: Passw . Click Passwords and Encryption Keys. Go to the Passwords tab, click to expand the Password folder, delete the entry called "Ubuntu One". Note that this may not be loaded if you have not subscribed.

In a terminal session run:

    ```
sudo apt-get purge ubuntuone-client python-ubuntuone-storage*
```

---

