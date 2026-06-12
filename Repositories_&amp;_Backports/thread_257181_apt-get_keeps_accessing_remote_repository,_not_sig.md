---
title: "apt-get keeps accessing remote repository, not signed local one"
date: 2006-09-14
forum: Repositories &amp; Backports
---

### Post by jamadagni on 2006-09-14
I created a local repo by creating the Packages.gz, Release, Release.gpg files, and apt-key add-ed the key used to sign.

Now still apt-get keeps accessing remote repository, not the signed local one, for a package that is of the same version in both repositories.

What do I do to make apt-get access my local repository only?

P.S: I should confess that the Release file was a dummy one without md5sums. Is that the problem?

---

### Post by Sarisar on 2006-09-14
Did you change your sources files to point to the local repositories?

---

### Post by jamadagni on 2006-09-14
Sure I did. And that entry precedes the remote entry.

---

### Post by HIV on 2006-10-30
I'm going through the same...it keeps going online...It's annoying.

I installed apt-proxy and managed to overcome this as the remote repositories are configured in apt-proxy and not in /etc/apt/sources.list. Your sources.list will only point to your computer and as such the local packages seem to get the needed priority. 

The only problem is that even though apt-proxy (supposedly) lets you import the .deb files (apt-proxy-import) from /var/cache/apt/archives (or your local pool) I couldn't get it to work and as such I had to re-download everything through apt-proxy. It just tells me it can't find a suitable repository to store my already downloaded packages.

Well anyway I'm a newbie...

---

