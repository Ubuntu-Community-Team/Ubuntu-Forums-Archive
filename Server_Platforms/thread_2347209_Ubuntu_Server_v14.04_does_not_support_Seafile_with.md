---
title: "Ubuntu Server v14.04 does not support Seafile with Apache anymore"
date: 2016-12-22
forum: Server Platforms
---

### Post by nikolaus993 on 2016-12-22
I am running a Seafile cloud server on an Ubuntu server v12.04 for many years without any issues but since
I have upgraded my whole system to Ubuntu v14.04 I got serious issues with my Seafile server.

The problem is, that folder names and file names with umlauts and/or spaces are not handled correctly anymore, which
means you cannot access files within those folders and you cannot access those files either over the Seafile
web-GUI (the used browser does not matter). 

Everyone can reconstruct the problem with a standard Seafile configuration, which means
Apache v2.4.7 + SSL + MySQL - look [here]("https://manual.seafile.com/deploy/") for details.

After some investigation I have found out that the reason for this problem seems to be an
known apache bug, which is fixed in v2.4.12 - maybe the fastcgi or proxy mod is involved too, I am not sure.
For a more detailed explanation you can read the the thread in the official Seafile forum - [here]("https://forum.seafile.com/t/folders-and-files-with-spaces-and-or-umlauts/1062")

The problem for me is, that I cannot upgrade my apache configuration (it is a Plesk v12.5 based virtual server)
and Nginx is also no option because a Nginx-only-setup is not supported by Plesk yet.

I would really appreciate a (apache) hotfix for this problem.

Thank you in advance.

---

### Post by TheFu on 2016-12-22
Looks like you've done all the homework. Sadly, that won't help here.

The best you can do now is to [open a bug report with Canonical ]("https://help.ubuntu.com/community/ReportingBugs").  These forums are end-user to end-user help only.

You'll have to get that from Apache, I'm afraid.  Canonical may apply a fix, but only if provided by the upstream. It is too hard to manage 80,000+ packages otherwise.

If your current VPS doesn't let you have control to which webserver version is installed, perhaps it is time to fire them?

---

