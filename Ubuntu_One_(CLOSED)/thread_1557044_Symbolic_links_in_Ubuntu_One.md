---
title: "Symbolic links in Ubuntu One"
date: 2010-08-20
forum: Ubuntu One (CLOSED)
---

### Post by emagar on 2010-08-20
Adding a symbolic link to some directory in your disk in the Dropbox folder immediately syncs all files in that directory with the cloud. The same does not happen in my Ubuntu One. Yet I remember having read somewhere that Ubuntu One would be able to handle symbolic links in this fashion with 10.04... Has anyone solved this?

---

### Post by RainCT on 2010-08-22
[quote=Ellioth Murphy]
We're adding a new feature to Ubuntu One file sharing in Lucid (10.04) which we call user defined folders, or UDF for short. This will allow you to select any folder in your home directory and sync it with Ubuntu One. You can follow along with progress here: [https://blueprints.edge.launchpad.net/ubuntu/+spec/lucid-ubuntu-one-symlinks-and-udfs](https://blueprints.edge.launchpad.net/ubuntu/+spec/lucid-ubuntu-one-symlinks-and-udfs)

Note that while technically it is very easy to sync the symlinks (not follow them, just sync the symlinks), it causes a backwards compatibility problem so we're not currently adding symlink support by default, but we hope that the UDF support will provide the flexibility that people need.
[/quote]

[https://bugs.edge.launchpad.net/ubuntuone-client/+bug/406930](https://bugs.edge.launchpad.net/ubuntuone-client/+bug/406930)
[https://blueprints.edge.launchpad.net/ubuntu/+spec/lucid-ubuntu-one-symlinks-and-udfs](https://blueprints.edge.launchpad.net/ubuntu/+spec/lucid-ubuntu-one-symlinks-and-udfs)

---

### Post by afrowildo on 2010-08-26
Is a symbolic link really necessary? You have the option to right click on a file or folder and select "Synchronise to Ubuntu One" near the bottom of the menu, which I guess is a sym link in it's own right.

---

