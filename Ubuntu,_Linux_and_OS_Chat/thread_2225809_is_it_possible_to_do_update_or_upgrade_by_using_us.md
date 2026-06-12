---
title: "is it possible to do update or upgrade by using using download manager"
date: 2014-05-23
forum: Ubuntu, Linux and OS Chat
---

### Post by LastDino on 2014-05-23
I'm just curious, but is it possible to do update or upgrade from terminal using any download manager? Example: Aria2?

I'm not just talking about Ubuntu, but any Linux OS in general. 

I somewhere read that I could do ''apt-fast'' instead of ''apt-get'' but that doesn't seems to be available on 14.04 yet, so just wondering.

---

### Post by tgalati4 on 2014-05-23
You can download any package (*.deb) file from the appropriate repository using any download manager you want.  That won't install it.

*sudo apt-get update* provides a check of the software on your system (installed packages and their versions) with the latest snapshot from all of the repositories that you have listed in /etc/apt/sources.list.  This list includes all of the standard repo's and any personal repo's (PPA's) that you have added.

*sudo apt-get upgrade* will then attempt to install newer versions of those packages that were flagged from the previous command.

A download manager simply downloads files from an external source and stores them in a local directory.  I don't see how any download manager can update software without intervention of using the APT system.

I am not familiar with *apt-fast*.  Is this the same as installing delta-packages--installing only small pieces of packages that have changed instead of installing an entire package every time there is an update?

So, either I don't understand the question, or No, you can't update and upgrade your system with a download manager.

---

### Post by LastDino on 2014-05-23
Apt-fast extends apt-get by basically downloading packages in parallel  using one of several different download accelerators. 

I think I worded question little wrong, more accurate version would be: Is it possible to download packages needed to update by using download managers like Aria2.  If yes, how to do that and then install them correctly/as our normal command (sudo apt-get update && sudo apt-get upgrade -y) which I use would do?

---

### Post by SeijiSensei on 2014-05-23
If you're concerned about download speeds during updates, I suggest you pick another server besides the default for your region.  Use the "Software Sources" tool in a graphical package manager and select a server near you.  I live outside Boston and use the mirror at MIT.  It's much faster than the default US server.  

You may find that selecting a different server is all you need to speed up downloads.

---

### Post by LastDino on 2014-05-23
> **SeijiSensei said:**
> If you're concerned about download speeds during updates, I suggest you pick another server besides the default for your region.  Use the "Software Sources" tool in a graphical package manager and select a server near you.  I live outside Boston and use the mirror at MIT.  It's much faster than the default US server.  

You may find that selecting a different server is all you need to speed up downloads.

Yes, that is how I'm dealing with it as of now. Every time there is update available  of considerable size, I do the server check and select the best server. I just wanted to know if there was any way to make do with simply using download manager rather than doing what we are doing.

---

### Post by ibjsb4 on 2014-05-23
Speed counts, but I also like to know that my updates are up to date.  Check it out ..

[https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors)

About what you want to do with a DL manager, sorry can't help you.

---

### Post by LastDino on 2014-05-23
> **ibjsb4 said:**
> Speed counts, but I also like to know that my updates are up to date.  Check it out ..

[https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors)

About what you want to do with a DL manager, sorry can't help you.

Thanks, didn't knew about that page ^^

No worries, it is not exactly a problem, just curiosity.

---

