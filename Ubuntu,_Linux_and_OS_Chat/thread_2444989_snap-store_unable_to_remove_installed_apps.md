---
title: "snap-store unable to remove installed apps"
date: 2020-06-07
forum: Ubuntu, Linux and OS Chat
---

### Post by corradoventu on 2020-06-07
snap-store unable to remove installed applications
Open snap store, click on 'Installed' select an app I want remove, click 'Remove' I see the message 'Unable to remove ... removing not available'.
tested with 2 different apps both .deb
[https://bugs.launchpad.net/snap-store/+bug/1882417](https://bugs.launchpad.net/snap-store/+bug/1882417)

---

### Post by #&amp;thj^% on 2020-06-07
Dose the terminal work?
```
sudo snap remove $package
```
Sorry not much help with GUI's anymore CLI is how I drive 90% of my applications.
Also sometimes a re-install works:
```
sudo snap install snap-store
```
Now check with:
```
snap-store
```
form your terminal, copy and paste anything that might help.

---

### Post by GhX6GZMB on 2020-06-07
This says everything about snap. Remove the thing.

---

### Post by Dennis N on 2020-06-07
> Open snap store, click on 'Installed' select an app I want remove, click 'Remove' I see the message 'Unable to remove ... removing not available'.
tested with 2 different apps both .deb
The bug report shows you have edge channel enabled for snap-store. Correct? It's highest risk. Maybe you should use stable version. I'm confused by the .deb reference. My snap-store only shows installed snaps in the installed tab. Nothing installed from a .deb package appears here.

```
dmn@Sydney-VM:~$ snap list | grep snap-store
snap-store            3.31.1+git187.84b64e0b      415   latest/stable    canonical*  -
```

---

### Post by #&amp;thj^% on 2020-06-07
Nice catch Dennis N...
```
snap-store 20200414.ac9047f 375 latest/edge canonical&#10003; 
```

---

### Post by corradoventu on 2020-06-08
The problem happens trying remove .deb packages, not snap.
I have the snap-store automatically installed by Ubuntu, nothing else.
To remove .deb packages i can do with terminal or synaptic or gnome-software, 
I don't need snap-store but sometimes i try snap-store just for the sadistic pleasure of finding bugs .
I only opened this thread to report the problem hoping that someone will try and in case subscribe to my bug.

---

### Post by Dennis N on 2020-06-08
I recently installed snap-store again (version shown in post #4, latest stable channel version) on Ubuntu 20.04. It will not display any .deb package versions of software - installed or uninstalled. There is no package browsing possible by categories. Only the search works. 

Screenshot 1: search for libreoffice. The only result is the snap version. There is no selector for .deb packages as in gnome-software. That's why I am confused by your mention of .deb operations in snap store.
Screenshot 2: the installed list. Only snap packages show.

And are you running Ubuntu 20.04? Try the current snap-store stable channel version.

---

### Post by corradoventu on 2020-06-08
I know, here another bug:
[https://bugs.launchpad.net/snap-store/+bug/1874966](https://bugs.launchpad.net/snap-store/+bug/1874966)

---

### Post by Dennis N on 2020-06-08
> **corradoventu said:**
> I know, here another bug:
[https://bugs.launchpad.net/snap-store/+bug/1874966](https://bugs.launchpad.net/snap-store/+bug/1874966)
The lack of browsing categories is a missing feature that needs to be added to the current stable version. But, I do prefer that the snap-store handles snaps only. I think that's a good idea.

EDIT: Later this same day, Snap Store now shows categories for browsing. But the snap-store package appears not to have been updated - same version (415). Anyway, it shows Snap packages only. And as before, only Snap packages appear in Installed tab.

---

