---
title: "Is it possible to make one or more of these changes to apt and snap integration?"
date: 2020-09-10
forum: Ubuntu Development Version
---

### Post by behrangsa on 2020-09-10
Hi,

Can you consider and implement one of these changes?

[LIST=1]
[*] During installation, give the user the option to turn off apt/snap integration.
[*] Modify apt and add a flag that users can pass to apt to indicate they want to install a snap version of a given package. If the snap version doesn't exist, fail with an error message.
```

$ sudo apt install chromium            # Install classic apt package
$ sudo apt install chromium --snap     # Install snap version
$ sudo apt install htop --snap         # Print an error message (e.g. "htop is not available as a snap.") and terminate.
```
[/LIST]

---

### Post by ajgreeny on 2020-09-10
Not at the moment.

In the example you chose, chromium, there is no apt, ie .deb package to use in place of the snap version which is installed even if you use ***sudo apt install chromium***.

There are both install options for other packages. eg VLC which can be either the .deb package or snap, depending on which GUI package manager you use.  If I use a GUI at all it is synaptic, but usually, if I know what I want to install it is command line using apt install.

---

### Post by behrangsa on 2020-09-10
Chromium was just an example. I remember in one of the recent Ubuntu versions even Calculator was installed as a snap. I had noticed it was loading very slowly and typing an arithmetic expression in the search bar (?) wouldn't calculate the result but didn't know that it is due to its "snappiness". I had to uninstall the snap version and reinstall the apt version to fix that issue.

Similarly I remember that I installed an apt package (Inkscape?) and then after checking I noticed that apt has actually installed the snap version.

Using the --snap flag or something similar, users can be confident that snaps are only installed when they explicitly pass the flag to apt.

In the case of Chromium, if apt had that flag, it could print an error message such as "Chromium is not available as a .deb package. To install it as a snap, pass the --snap flag".

---

### Post by ajgreeny on 2020-09-10
If you use synaptic it tells you a lot more than the software-store, or whatever it's now called, which I have never used.

---

