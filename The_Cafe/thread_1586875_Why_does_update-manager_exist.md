---
title: "Why does update-manager exist?"
date: 2010-10-02
forum: The Cafe
---

### Post by ki4jgt on 2010-10-02
If update-manager can't update some packages, then why have it? Why not tie Ubuntu software center into synaptic and update through it?

---

### Post by bash on 2010-10-02
> **ki4jgt said:**
> If update-manager can't update some packages, then why have it? Why not tie Ubuntu software center into synaptic and update through it?

If update manager can't update some packages, then there normally is something wrong with the packages or their dependencies. This has nothing to do with update-manager. Broken dependencies can be a result of some ppas updating specific components and thereby breaking the dependencies of other packages.

Are you having a problem with a specific package?

---

### Post by ki4jgt on 2010-10-02
No, but this isn't the first time I've updated Ubuntu with um and had to resort to using synaptic b/c I got a message stating that the system could only do a partial upgrade.

---

### Post by Bachstelze on 2010-10-02
> **bash said:**
> If update manager can't update some packages, then there normally is something wrong with the packages or their dependencies.

I don't know about update-manager, but if it's like [font=monospace]apt-get upgrade[/font] it will not upgrade a package if the upgrade requires installation of a new package. It happens from time to time, for example when a new revision of the kernel is released, and doesn't mean there is something wrong in the user's system.

---

### Post by CharlesA on 2010-10-02
> **Bachstelze said:**
> I don't know about update-manager, but if it's like [font=monospace]apt-get upgrade[/font] it will not upgrade a package if the upgrade requires installation of a new package. It happens from time to time, for example when a new revision of the kernel is released, and doesn't mean there is something wrong in the user's system.

You'd have to use apt-get dist-upgrade to add those.

I'm not sure if update manager works the same way or not.

---

### Post by bash on 2010-10-02
> **CharlesA said:**
> You'd have to use apt-get dist-upgrade to add those.

I'm not sure if update manager works the same way or not.

Should be - update-manager calls them partial upgrades. AFAIK partial upgrade of update-manager only appears if there is a new package that needs to be installed or a package that will be removed.

---

### Post by ki4jgt on 2010-10-02
No offence but, it's still annoying and forces the user to revert to Synaptic.

---

### Post by Lucradia on 2010-10-02
> **ki4jgt said:**
> No offence but, it's still annoying and forces the user to revert to Synaptic.

apt-get is not synaptic. Synaptic is worse off to do dist-upgrades with.

---

### Post by ki4jgt on 2010-10-02
That's what I always do my upgrades with. It doesn't come up with any errors. Or none that it notifies me about.

---

### Post by cariboo on 2010-10-02
If you're running a released version, there is nothing wrong with doing partial upgrades, it just means that some of the dependencies aren't available yet. If you set your updates for weekly, or bi-weekly, you'll almost never see a partial update.

---

### Post by CharlesA on 2010-10-02
> **cariboo907 said:**
> If you're running a released version, there is nothing wrong with doing partial upgrades, it just means that some of the dependencies aren't available yet. If you set your updates for weekly, or bi-weekly, you'll almost never see a partial update.

I don't usually use update manager, but I think the only time I see something like "some packages were held back" is when there are updates to the kernel.

Are those also considered "partial upgrades" as well?

---

