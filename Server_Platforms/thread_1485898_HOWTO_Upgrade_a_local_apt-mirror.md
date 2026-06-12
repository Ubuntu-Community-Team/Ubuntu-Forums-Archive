---
title: "HOWTO: Upgrade a local apt-mirror"
date: 2010-05-17
forum: Server Platforms
---

### Post by sherl0k on 2010-05-17
After digging around trying to figure out how to upgrade my local apt-mirror to 10.04, I figured I would share it here so anyone else who does this, can do it with ease. It requires a few steps, and editing a couple files, but the process is relatively painless.

This assumes you have an apt-mirror already running on your server. Also it assumes you're using /var/www/ubuntu as your root where all your packages are stored.

The first step is to visit [http://changelogs.ubuntu.com](http://changelogs.ubuntu.com) and download the meta-release packages. Create a new directory, /var/www/ubuntu/upgrade, and drop the files there.

After downloading the files, edit the 'meta-release' file. Scroll to the bottom and you'll find the following:

```
Release-File: http://archive.ubuntu.com/ubuntu/dists/lucid/Release
ReleaseNotes: http://archive.ubuntu.com/ubuntu/dists/lucid-proposed/main/dist-upgrader-all/0.134.8/ReleaseAnnouncement
ReleaseNotesHtml: http://archive.ubuntu.com/ubuntu/dists/lucid-proposed/main/dist-upgrader-all/0.134.8/ReleaseAnnouncement
UpgradeTool: http://archive.ubuntu.com/ubuntu/dists/lucid-proposed/main/dist-upgrader-all/0.134.8/lucid.tar.gz
UpgradeToolSignature: http://archive.ubuntu.com/ubuntu/dists/lucid-proposed/main/dist-upgrader-all/0.134.8/lucid.tar.gz.gpg

```

Each of those files, you will also have to download and drop in the upgrade folder. After doing so, edit the file so the URLs match your apt-mirror's server address. For me, my apt-mirror is at 10.10.10.252 so I simply edit the line to look like such:

```
Release-File: http://10.10.10.252/ubuntu/upgrade/Release
ReleaseNotes: http://10.10.10.252/ubuntu/upgrade/ReleaseAnnouncement
ReleaseNotesHtml: http://10.10.10.252/ubuntu/upgrade/ReleaseAnnouncement.htm
UpgradeTool: http://http://10.10.10.252/ubuntu/upgrade/lucid.tar.gz
UpgradeToolSignature: http://http://10.10.10.252/ubuntu/upgrade/lucid.tar.gz.gpg
```

I renamed the 'ReleaseNotesHtml' file and gave it a .htm extension because it is the same filename as the plain-text one.

Edit the 'release-notes-lts' file also, if needed. Do the same changes.


On the client's end, a single file needs to be edited, /etc/update-manager/meta-release. Change the URI's in that file to the URI of your apt-mirror and run your update manager. Your upgrade will start, only asking if you want to change your paths in your sources.list. Agree to it, and the packages will download and configure.

---

### Post by jejones3141 on 2010-05-19
Many thanks for the post; I find myself in the same situation.

A question or two: when you say "the meta-release packages", what do you mean? Looking at the meta-release file on my system, it just mentions meta-release and meta-release-lts; are those all I need to fetch from [http://changelogs.ubuntu.com/?](http://changelogs.ubuntu.com/?)

---

### Post by sherl0k on 2010-06-17
No, each of those files - Release-File, ReleaseNotes, ReleaseNotesHTML, UpgradeTool, and UpgradeToolSignature - need to be downloaded from archive.ubuntu.com and put somewhere on your local webserver. update-manager looks for these files when doing a release upgrade, and if they are not present it won't let you continue the upgrade.

---

