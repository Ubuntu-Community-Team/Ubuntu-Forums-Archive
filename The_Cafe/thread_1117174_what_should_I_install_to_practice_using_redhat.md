---
title: "what should I install to practice using redhat?"
date: 2009-04-05
forum: The Cafe
---

### Post by sp0tz on 2009-04-05
First off, I know that there's a redhat forum on this site, but I can't start a new thread in it.

Anyways, I've taken an interest in becoming a linux network administrator. A strong interest. I've set up a server in my house running ubuntu that functions as a samba filesharing server (used to also function as a dnla server, but I wasn't getting much use from that). And since people look for linux sysadmins with an RHCE, I'd like to get that cert., but I've got no redhat system to practice on. The cheapest available redhat license is $80/year, which is somewhat affordable, but if at all possible, I'd like to avoid payment. I've found a torrent of the installation disks, but I expect to be stopped during the install when I don't have a license, which makes sense. Anyways, My RHCE studyguide says that you can download redhat at no cost, (which is why I'm working on that torrent) but I can't find a download link on the redhat site. To get to the heart of the matter:

What OS should I install to prepare for an RHCE exam, or at least get "experience with redhat", as some of the jobs I'm looking at require it?

Thanks,
Sp0t

---

### Post by Kingsley on 2009-04-05
Check out CentOS. It's a clone of RHEL, but totally free.

---

### Post by sp0tz on 2009-04-05
according to the centos wikipedia page, there are no differences between redhat and centos besides centos' removal of all redhat trademarked material. Is this true?

---

### Post by swoll1980 on 2009-04-05
It's built right from the the Red Hat source package. No difference, it's just re-branded.

---

### Post by gnomeuser on 2009-04-05
> **sp0tz said:**
> according to the centos wikipedia page, there are no differences between redhat and centos besides centos' removal of all redhat trademarked material. Is this true?

The biggest changes are that the artwork has all the RH trademarks removed for legal reasons, and since they are not bound by RHs business model and products you get everything on one DVD instead of several separate products. Finally at least in the old days a number of the tools were named redhat-config-<foo> which was changed to be system-config-<foo> but I think that is actually the standard now.

Aside that if you want an early look at the upcoming RHEL improvements you can look to Fedora and side projects like oVirt (which is bucket loads of awesome btw.). RHEL 6 will be based on Fedora 11 or possibly Fedora 12 (plus what ever work they elect to put into the product during their hardening and QA processes), so that might also be nice to try just to see what new things will be available

Regardless for RHCE preping on the cheap CentOS is your best choice. It is RHEL without the support but it is the real deal to every detail you would need to know.

The list of packages with CentOS 5.3 changes compared to RHEL 5.3
[http://wiki.centos.org/Manuals/ReleaseNotes/CentOS5.3#head-e206ad965f52945e6958c2eac768eb69c377ba29](http://wiki.centos.org/Manuals/ReleaseNotes/CentOS5.3#head-e206ad965f52945e6958c2eac768eb69c377ba29)

---

### Post by sp0tz on 2009-04-05
awesome. RHEL5 torrent has been canceled, centos torrent is about half done. Thx for the help.

Also, the system that I plan on installing to is something of a junker, an old Dell optiplex gx260, pentium 3, something like 512 Megs of ram. I plan on using it as a samba, ftp, and webserver. Anyone see a problem with that? Speed is not an issue so much as functionality is. If it works, then I'll get a beefier machine later. (clearly I don't want to spend money on something that I may or may not take a long term interest in, though.)

---

