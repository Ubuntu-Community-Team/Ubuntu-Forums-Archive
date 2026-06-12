---
title: "Specifics of a dist-upgrade"
date: 2007-10-02
forum: Repositories &amp; Backports
---

### Post by coolen on 2007-10-02
I recently wrote a HowTo on using apt-cacher.
What I'm wondering is, will this be undone during a dist-upgrade?

To use it, you must alter the lines of your sources.list (every line, including the official repos).
Does anyone know how Update Manager handles the transition? Does it simply replace any occurance of the word Feisty with Gutsy, or does it rewrite the lines for the official repos?

---

### Post by Seisen on 2007-10-03
This is from the apt man page

> dist-upgrade, in addition to performing the function of upgrade, also intelligently handles changing dependencies with new versions of packages; apt-get has a "smart" conflict resolution system, and it will attempt to upgrade the most important packages at the expense of less important ones if necessary.

or basically in a nutshell will put all the newest packages from the repositories. Also you have to physically change your source list to from Feisty to Gutsy by using certain commands or going in yourself and changing Feisty to Gutsy. Dist-upgrade will not change the source list to the newer distribution either.

---

### Post by coolen on 2007-10-03
Sorry, I worded that wrong.
I know a dist-upgrade from the command line would do nothing if you haven't changed your sources.list. I was referring to the Update Manager.

My HowTo instructs the user to modify their sources.list. If the Update Manager rewrites these lines with those provided by Canonical, these changes would be undone. If, however, they simply replace Feisty with Gutsy in the file, then it won't be a problem.

---

### Post by Seisen on 2007-10-05
Update Manager basically does the same thing that  Synaptic or apt-get does. The only way a source list gets rewritten is if you give a command in the terminal to rewrite your source list,  you manually edit you /etc/apt/sources.list or you if add or remove repositories in Software Sources.

---

### Post by coolen on 2007-10-05
The Update Manager can detect when a new version of Ubuntu's out, and upgrade your system. I did this on my brother in law's laptop from Edgy to Feisty.
I assume that, in the process, your sources.list is altered to reflect the new version.

---

### Post by tchoklat on 2007-11-02
Na, You have to replace the word 'feisty' with the word 'gutsy' in the sources list or the upgrade will not work. I have done this today to update 7.04 to 7.10.

tchoklat

---

### Post by wgrant on 2007-11-02
> **tchoklat said:**
> Na, You have to replace the word 'feisty' with the word 'gutsy' in the sources list or the upgrade will not work. I have done this today to update 7.04 to 7.10.

tchoklat

update-manager does that automatically - that's largely the point.

---

### Post by tchoklat on 2007-11-03
yep, you are right, I wasn't thinking. Thanks fujitsu!

---

