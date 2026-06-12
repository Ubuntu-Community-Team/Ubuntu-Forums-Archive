---
title: "Upgrade Doubts"
date: 2004-12-23
forum: Repositories &amp; Backports
---

### Post by EternalNewbie on 2004-12-23
Hi,
     I installed Ubuntu from the CD I was sent and everything works albeit slowly on my old computer. My problem is that the system always has wanted to download 117 MB of updates from the internet.
      This is with only security and main binary deb. as the selected repositories. Is this as unreasonable as it seems to me ? The situation is the same with Synaptic as with apt-get from the shell.

                                                             Thanks for any help,
                                                                     John Duncan

---

### Post by randy on 2004-12-23
That sounds like it's right to me.

---

### Post by nocturn on 2004-12-23
[QUOTE=EternalNewbie]Hi,
     I installed Ubuntu from the CD I was sent and everything works albeit slowly on my old computer. My problem is that the system always has wanted to download 117 MB of updates from the internet.
      This is with only security and main binary deb. as the selected repositories. Is this as unreasonable as it seems to me ? The situation is the same with Synaptic as with apt-get from the shell.

                                                             Thanks for any help,
                                                                     John Duncan[/QUOTE]
Ok, this may seem like a large update.  But don't forget that this includes patches/updates for the entire OS *and* all installed applications.
So, no 117 MB does not sound unreasonable (if you compare it with service packs for MS Windows, the number is quite low).

If you are on a slow connection, it may be annoying.  Anyhow, if you are on a dialup connection *and* running behind a firewall, you may be able to skip a lot of those updates (although I do recomment installing them).

---

### Post by EternalNewbie on 2004-12-24
O.K.,
            I installed the updates since they seem to be expected. Thanks for the re-assurance.

                                               All the best,
                                                   John Duncan

---

### Post by HiddenWolf on 2004-12-25
[QUOTE=EternalNewbie]Hi,
     I installed Ubuntu from the CD I was sent and everything works albeit slowly on my old computer. My problem is that the system always has wanted to download 117 MB of updates from the internet.
      This is with only security and main binary deb. as the selected repositories. Is this as unreasonable as it seems to me ? The situation is the same with Synaptic as with apt-get from the shell.

                                                             Thanks for any help,
                                                                     John Duncan[/QUOTE]


I just went back from Hoary to Warty, and indeed, I was quite amazed and a bit pissed off at the amount of updates.

---

### Post by randy on 2004-12-25
Why are you pissed off about the amount of updates?  It's similiar in amount for most operating systems and it's only keeping your system secure.

---

### Post by HiddenWolf on 2004-12-25
[QUOTE=randy]Why are you pissed off about the amount of updates?  It's similiar in amount for most operating systems and it's only keeping your system secure.[/QUOTE]

Because i tend to read changelogs, and I get to download a new package because there is some undeclared statement fixed, or about a byte of changed binary. :-)

I feel if an update is done to the repros, ubuntu should produce a new downloadable iso.
I'm ok with the fact that if I use my official cd, i'll have to update, but I don't like downloading 600mb, and then 120mb in updates within the hour, which could've easily been prevented.

---

### Post by Sensebend on 2005-01-03
Perhaps they could have incremental ISO releases such as a new ISO for the stable distribution every month or so. That would be helpful for those who deploy Ubuntu on multiple systems and install it for other people as well. I tend to update frequently, and occasionally read the changelogs. I just don't like missing out on the latest and greatest OSS has to offer, even if that means getting a few undocumented features :D

---

### Post by hazza96 on 2005-01-03
[QUOTE=Sensebend]for those who deploy Ubuntu on multiple systems and install it for other people as well.[/QUOTE]
If you are doing that then I would suggest following these directions:
[http://www.ubuntuguide.org/#backuprestoredownloadedrepositoriescache](http://www.ubuntuguide.org/#backuprestoredownloadedrepositoriescache)

Or course you would not be moving them to a different directory but burning them to a CD to take with you. Install the base system copy over the two directories and run the update after that.

I have three Ubuntu machines, the first is a server that makes /var/cache/apt and /var/lib/apt available to the other two via NFS. I only have to download a package once.

---

### Post by hazza96 on 2005-01-03
[QUOTE=HiddenWolf]I just went back from Hoary to Warty, and indeed, I was quite amazed and a bit pissed off at the amount of updates.[/QUOTE]
Would you rather that they not do any updates and leave you open to the security holes?

---

### Post by crun on 2005-01-03
It's certainly a lot of updates for a stable distribution. If you're using the standard repositories than I wonder what causes the difference in size in updates compared to say Debian Woody (which very seldom has to download any new packages). Maybe Ubuntu's base install includes packages that have more frequent security fixes than a base Woody?

---

