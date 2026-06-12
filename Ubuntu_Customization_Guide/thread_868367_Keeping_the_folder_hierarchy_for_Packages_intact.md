---
title: "Keeping the folder hierarchy for Packages intact?"
date: 2008-07-23
forum: Ubuntu Customization Guide
---

### Post by Igtenio on 2008-07-23
Currently, I'm working on my own little Ubuntu remix, and I've run into a snag; I cannot, for the life of me, find a way to recreate the folder hierarchy that packages use.

I'm using the Alternate CD, and while it works if you just dump all of the packages into a folder, I'd rather keep the tree intact for organizational purposes. Helps me find things, and I feel that it just plain looks better.

For the base packages, the ones that come on the CD, it was fairly easy to pull those out; you grab the pool folder, print out a list of packages installed on the main system, then just type;

cp --parents --force <Path to default pool folder>/*/*/<package name>* <Path to new pool folder>

...for each package, and it just copies them into a new pool folder with the hierarchy intact. Easy~peasy.

The problem is with the new packages. For instance, I use KDE-Core in it. I'd like for KDE-Core and its' dependencies to be put into the correct folders, similar to how it'd be on a repository.

However, I'm drawing blanks as to how I could accomplish this, outside of doing it manually. And, frankly, I'd like to avoid that.

Anyone have any ideas as to how I could accomplish this? I could keep the packages as just one mass, but I'd really, really like for the clean hierarchy.

---

### Post by Igtenio on 2008-07-24
Gah, I'm sorry...this's the completely wrong forum. ~_~ I have no clue what happened there. A brain-fart seems most likely. Could one of the mods delete this for me? I'll repost elsewhere.

---

