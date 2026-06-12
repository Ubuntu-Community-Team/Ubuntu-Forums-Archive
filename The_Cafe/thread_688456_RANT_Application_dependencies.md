---
title: "RANT: Application dependencies"
date: 2008-02-05
forum: The Cafe
---

### Post by abickerton on 2008-02-05
For  the next release would it be possible to allow us to remove some of the cruft that will never be used. By NOT ... I REPEAT NOT!!! setting every package to rely ubuntu-desktop.

:-x

It really is one of the thing that really annoys almost every one I introduce to Ubuntu Linux.

Applications that are particularly annoying in this respect:

1 Evolution
2 Groupwise
3 Palm sync

I removed this then I might as well install gentoo for the amount of aggro involved.

</rant>

---

### Post by justin whitaker on 2008-02-05
> **abickerton said:**
> For  the next release would it be possible to allow us to remove some of the cruft that will never be used. By NOT ... I REPEAT NOT!!! setting every package to rely ubuntu-desktop.

:-x

It really is one of the thing that really annoys almost every one I introduce to Ubuntu Linux.

Applications that are particularly annoying in this respect:

1 Evolution
2 Groupwise
3 Palm sync

I removed this then I might as well install gentoo for the amount of aggro involved.

</rant>

Some of those are Gnome dependencies, but I get where you are coming from with that. It's part and parcel of the *buntu experience.

---

### Post by abickerton on 2008-02-05
I just needed to vent... all better now.

---

### Post by FuturePilot on 2008-02-05
The ubuntu-desktop package makes it easy to upgrade to the next version. If it were to be gotten rid of it would be hard to pull in new apps that are installed by default. For example, Hardy will come with Brasero by default. If there was no ubuntu-desktop dependency it would make it hard to pull in Breasero when upgrading from Gutsy to Hardy.

Evolution has been removed from the ubuntu-desktop dependency.

---

### Post by OffHand on 2008-02-05
It's a meta-package. It's a package that points to all the apps that make Ubuntu Ubuntu. So you can uninstall evolution without a problem. All your other apps will still be there.

---

### Post by urukrama on 2008-02-05
As pointed out, you can remove ubuntu-desktop without affecting any of the other packages.

If you plan to dist-upgrade (rather than reinstall) to the next Ubuntu release, you might experience some difficulties without this meta-package, though. If you want to play safe(r), you could reinstall ubuntu-desktop before you upgrade and remove it after the upgrade, I suppose.

---

### Post by 23meg on 2008-02-05
> As pointed out, you can remove ubuntu-desktop without affecting any of the other packages.

Most things you'll want to uninstall no longer remove ubuntu-desktop. Try removing Evolution.

> If you plan to dist-upgrade (rather than reinstall) to the next Ubuntu release, you might experience some difficulties without this meta-package, though.

The dist-upgrade tool will take care of it.

---

### Post by urukrama on 2008-02-05
Thanks 23meg for correcting me. That is good to know. Is this new in Gutsy?

---

### Post by 23meg on 2008-02-05
It's been the case since Feisty. Related blueprints:

[https://launchpad.net/ubuntu/+spec/default-package-groups](https://launchpad.net/ubuntu/+spec/default-package-groups)
[https://blueprints.launchpad.net/ubuntu/+spec/recommends-support](https://blueprints.launchpad.net/ubuntu/+spec/recommends-support)

---

### Post by urukrama on 2008-02-05
Thank you. I do command line installs, so I had never noticed.

---

### Post by abickerton on 2008-02-12
> **urukrama said:**
> As pointed out, you can remove ubuntu-desktop without affecting any of the other packages.

If you plan to dist-upgrade (rather than reinstall) to the next Ubuntu release, you might experience some difficulties without this meta-package, though. If you want to play safe(r), you could reinstall ubuntu-desktop before you upgrade and remove it after the upgrade, I suppose.

This was something I originally thought was the case. Unfortunately on re-installing the meta package, evolution et were re-installed.

I should point out that this PC is not entirely a clean gutsy install. My only disc with ubuntu on it has dapper, so it has kinda grown.

Now I don't have an issue with the ubuntu-desktop package. Just the fact that if I remove it, the updates stop because it doesn't know I'm running gutsy.

---

