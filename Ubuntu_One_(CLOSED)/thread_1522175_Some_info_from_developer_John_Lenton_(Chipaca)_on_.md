---
title: "Some info from developer John Lenton (Chipaca) on how UbuntuOne works on the desktop"
date: 2010-07-01
forum: Ubuntu One (CLOSED)
---

### Post by NUboon2Age on 2010-07-01
In an irc chat today Chipaca (Canonical UbuntuOne developer John Lenton) explained:

> <Chipaca>  **ubuntuone-client-gnome has essentially three parts**:
The first is u**buntuone-preferences**, which is a gtk application that talks to syncdaemon (the Ubuntu One file syncing client daemon) over dbus and to the Ubuntu One web services REST API, and provides a measure of control over what gets synced and such

The second is u**buntuone-login**, which is a background helper script that aides in signing up and authenticating to Ubuntu One, as well as pairing your local couchdb with the Ubuntu One couchdb.

The third is the **nautilus integration**, this is an extension for nautilus that talks over dbus with syncdaemon to perform different actions and report on the state of synchronization

<Chipaca> **Desktop Couch is a thin layer of python that makes it easier / possible to have a couchdb per user**, and is not (at this moment in time) related to file synchronization.
It is in couch that you will find your contacts, your notes, your gwibber accounts (and messages, for now). You can browse your local couch using futon: point your browser at ~/.local/share/desktop-couch/couchdb.html  .

Unfortunately we've had to disable the public-facing couch in the datacenter for now, but it'll be back soon.

<Chipaca> Ubuntu One has two main building blocks: file sync'ing, and DesktopCouch

[B]Everybody gets what file syncing is about.
We need to explain DesktopCouch more [/B]:)

<Chipaca> **u1sdtool talks to syncdaemon over dbus** .
ubuntuone-login script only needs to run once, to store the secret in the keychain and to pair the couch.
Both syncdaemon and ubuntuone-login are started by dbus activation

<Chipaca>  syncdaemon is a dependency that ubuntuone-client-gnome pulls in.

<Chipaca>  (mentioned) ~/.config/ubuntuone/syncdaemon.conf

Duanedesign added:
> <duanedesign> newboon2age_: i thought **rye did a good job of explaining the Ubuntu One bits in this blog post [http://blog.rtg.in.ua/2009/11/ubuntu-one.html](http://blog.rtg.in.ua/2009/11/ubuntu-one.html)**

Update 7/4/2010
**The UDFs problem: **
UDFs = User Defined Folders: any folders you've designated to be synced in Ubuntu One other than the default "Ubuntu One" folder and its default "Shared With Me" Folder within.
 
If you run into a situation where other synced folders (that you designate as Ubuntu One synced folders besides the "Ubuntu One" folder which are are not propagating to your desktop it could be because UDFs are not supported on your system.   

Here's what Canonical's U1 developer of ubuntu-client-gnome, John Lenton (Chipaca on #ubuntuone irc channel) explained about UDF support:> 
<Chipaca> Karmic didn't have UDFs :) so, you could use a backport of ubuntuone (from the ubuntuone-hackers ppa) on Karmic, and get the UDFs or, not use UDFs at all -- your choice.

Update 7/4/2010
Here are **some wiki pages from [Roman Yepishev]("https://wiki.ubuntu.com/RomanYepishev")** ubuntuone customer support engineer (rye on the #ubuntuone irc channel) that adds some more:

[https://wiki.ubuntu.com/RomanYepishev/UbuntuOne/Diagnostics](https://wiki.ubuntu.com/RomanYepishev/UbuntuOne/Diagnostics)
[https://wiki.ubuntu.com/RomanYepishev/UbuntuOne/ClientControl](https://wiki.ubuntu.com/RomanYepishev/UbuntuOne/ClientControl)
[https://wiki.ubuntu.com/RomanYepishev/UbuntuOne/Documentation](https://wiki.ubuntu.com/RomanYepishev/UbuntuOne/Documentation)

---

