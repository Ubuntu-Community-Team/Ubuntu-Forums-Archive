---
title: "Why is Kubuntu suppose to come out the same date as Ubuntu?"
date: 2006-07-11
forum: The Cafe
---

### Post by Christmas on 2006-07-11
I was thinking, if Ubuntu using GNOME has this 6 months interval following the GNOME releases, why should Kubuntu be released the same way? If Kubuntu would be released after some major KDE release, the only problem would be the version number as the dates GNOME and KDE are released differ. 

If Kubuntu would not be tide by GNOME releases, than I think it could have more up-to-date packages and after all it should be different from Ubuntu as a distro and it might be better to have its own release dates and version numbers.

I'm not that much into how both of them are developed as I'm relatively new to Linux and Ubuntu and didn't participate to the IRC conferences the developers held (except the two logs when Dapper was delayed 2 months). So maybe I'm missing something though it looks logical to me. Please discuss.

---

### Post by DrSturgeon on 2006-07-11
That sort of makes a lot of sense, but the issue is with the repositories.  Think about it this way: when a version is released, the testing repository for that version all of a sudden becomes the stable repository.

Since you cannot have a single repository be stable for ubuntu, and testing for kubuntu, different release times would require splitting into two seperate repositories, and since presumably you'd still want the opposite desktop environments in the other repositories, this would mean maintaining two copies of everything; seperately.  Sounds like a nightmare.

Hmm, an idea:  What if the Ubuntu core was split into a different repository from the desktop environments?  Then you could run a stable core and an unstable gnome; or a stable core and a stable gnome, but an unstable KDE.  Then the Gnome and KDE repositories could become stable at different times, and it wouldn't matter.

The difficulties with maintaining compatibility between versions would probably make this impossible; but it's a cool idea.

---

### Post by Jucato on 2006-07-11
This was an issue discussed during the recent Ubuntu Development Summit (UDS) in Paris. There were actually proposals to release Kubuntu separately from Ubuntu (with Xubuntu probably following suit). AFAIK, there has been no final decision on it yet. IMO, there are also other factors involved, like the unity of the Ubuntu project, marketing, manpower, etc. It's not just a simple "following the release schedule of the DE" thing.

---

### Post by asimon on 2006-07-11
> **Fenyx said:**
> This was an issue discussed during the recent Ubuntu Development Summit (UDS) in Paris.
[Sebestian Kuegler, one of the attendees, blogged about this](http://vizzzion.org/?blogentry=624). See the second paragraph.

---

