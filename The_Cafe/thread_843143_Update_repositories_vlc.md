---
title: "Update repositories? vlc?"
date: 2008-06-28
forum: The Cafe
---

### Post by munky99999 on 2008-06-28
I'm just wondering why the repositories seem to be so far behind for vlc... 

Current version out is 0.8.6h but the repositories are still at 0.8.6e which was months ago.

Hardy-amd64 is my setup.

---

### Post by mcduck on 2008-06-28
Al the package versions are frozen at certain point during development, and updates are genarally only provided for security reasons and to fix serious problems.

You shouldn't expect VLC to be updated at all until next Ubuntu release, as it's unlikely to have a serious security problem..

Some packages that have relatively little dependencies and that are simple to update may get updated, and these updates will be avaiable in the Backports-repository. Enable that, if you haven't alredy, and you _might_ get an update for VLC. But I wouldn't hold my breath waiting..

You could also check if the new version is in getdeb.net, or some third-party repository.

---

### Post by awakatanka on 2008-06-28
You can also use the nightly update's from vlc and be up to date with vlc. Put that line in your source.list

deb [http://nightlies.videolan.org/build/hardy-i386/arch](http://nightlies.videolan.org/build/hardy-i386/arch) ./

---

