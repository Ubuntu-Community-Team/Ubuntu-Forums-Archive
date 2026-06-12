---
title: "Thunderbird 1.5"
date: 2006-01-12
forum: Requests
---

### Post by akurashy on 2006-01-12
Howdy around! just to let you guys know that thunderbird 1.5 is in final and I wonder if is in dapper already. lots of GUI fixes etc etc 

hope this get added :)


[LIST]
[*]Automated update to streamline product upgrades. Notification of an update is more prominent,              and updates to Thunderbird may now be half a megabyte or smaller. Updating extensions has also improved.
[*]Sort address autocomplete results by how often you send e-mail to each recipient.
[*]Spell check as you type.
[*]Saved Search Folders can now search across multiple accounts.
[*]Built in phishing detector to help protect users against email scams.
[*]Podcasting and other RSS Improvements.
[*]Deleting attachments from messages.
[*]Integration with server side spam filtering.
[*]Reply and forward actions for message filters.
[*]Kerberos Authentication.
[*]Auto save as draft for mail composition.
[*]Message aging.
[*]Filters for Global Inbox.
[*]Improvements to product usability including redesigned options interface, and SMTP server management.
[*]Many security enhancements.[/LIST]
[http://weblogs.mozillazine.org/rumblingedge/archives/2006/01/1-5.html](http://weblogs.mozillazine.org/rumblingedge/archives/2006/01/1-5.html) < a list of bug fixes and security

---

### Post by atom on 2006-01-12
its not in dapper, yet. :(

---

### Post by ember on 2006-01-12
And from my 2 hours windows experience I can say that it might be worth waiting for 1.5.0.1 - I had strange display problems (e.g. text not showing) that disappeared if I switched to another app and then back. Also there is a known bug in the new attachment functions in IMAP accounts.

---

### Post by jetpeach on 2006-01-12
I think it could be a while before another version, even a .0.1.  I've been using the RCs on windows since November without any issues and definitely look forward to using it on Ubuntu.

EDIT: well I went ahead and downloaded 1.5 from Mozilla.  Surprisingly, there is no need for complicated installs or anything like that whatsoever, at least for the basic app (perhaps it isn't set as the default email client, I may have to configure that somehow.)  Just down, extact, double click "thunderbird" and everything worked well.  I'll have to set my shortcuts up now though...

---

### Post by akurashy on 2006-01-12
that just are the binaries, i compiled mine from the sources and it works smoothly also they fixed some memory leaks and its really worth it having in backports imho

---

### Post by Philippe Worontzoff on 2006-01-13
Does anyone has any ideas about when Thunderbird 1.5 will be backported (approximately)?

---

### Post by teolemon on 2006-01-13
It's very likely that we'll encounter the same problems as with Firefox 1.5 as they both use the same engine and share big parts of cade.Best thing is that you install it from the Mozilla.org website if you can't wait for Dapper

---

### Post by macleod199 on 2006-01-15
[QUOTE=Philippe Worontzoff]Does anyone has any ideas about when Thunderbird 1.5 will be backported (approximately)?[/QUOTE]

There's no sign of it even in Debian experimental yet. This guy:

[http://www.asoftsite.org/s9y/](http://www.asoftsite.org/s9y/)

Seems to be one of (the only?) Debian thunderbird maintainer, and hasn't update his blog since early decemeber. Does not bode well.

---

### Post by foxy123 on 2006-01-17
I've been using RC2 which is effectively the release for few weeks and have not had any problems. I hope that TB has less dependencies than FF but I guess we will have to wait for Dapper to see both of them in repositories.

---

### Post by Miguel on 2006-01-17
AFAIK, Thunderbird should have no dependency problems. I haven't got dapper, but trying to uninstall thunderbird in my laptop does not ask for any other app to be uninstalled. 

**To use Thunderbird 1.5 as your default mail program in Ubuntu:**
[list][*]Download the binary from mozilla, site. 
[*] Unzip it to somewhere you have permissions. You don't need to unzip it in /usr/local if you don't plan to give it to every user. I would do
```
$ mv thunderbird-1.5.tar.gz ~/
$ cd
$ tar -zxf thunderbird-1.5.tar.gz

```
This will extract thunderbird-1.5 in your home folder in a folder named thunderbird-1.5
[*] Change or add a launcher at your taskbar that points at $HOME/thunderbird-1.5/thunderbird
[*] Go to System->Preferences->Favourite Applications and on the Mail reader tab choose "Custom", with the command "$HOME/thunderbird-1.5/thunderbird". You shouldn't check the "open in terminal" box
[*] If you want Thunderbird 1.5 to have access to your former e-mail,
```
$ cp -r ~/.mozilla-thunderbird/ ~/.thunderbird 
```
[/list]

This is longer said than done, and paths will change to wherever you have extracted thunderbird, but you get the idea. And the best thing of this is...

You don't need Root Power!!!!

OT: The real firefox problems is that, due to licensing, there is no i.e. libgecko (an html rendering library). And ubuntu uses gecko (firefox's engine) for all html rendering inside gnome. A new gecko version should be accompanied by a rebuild of every part that uses gecko for rendering. 

Kubuntu should not have those problems, though, as html rendering in KDE is done via khtml (OS X's safari uses it too)

---

### Post by voyageur_01 on 2006-01-17
There is unofficial package of thunderbird but it works really good for me.
[http://download.ubuntu.pl/mozilla/thunderbird/]("http://download.ubuntu.pl/mozilla/thunderbird/")

To save your configuration acounts you have to copy:
> cp -R ~/.mozilla-thunderbird/* ~/.thunderbird/
Have fun

---

### Post by ogregore on 2006-01-17
Upgraded using the mozilla.org source.  Seems to be running much more stable than the FF1.5 upgrade has.  

The only problems I ran into were that there are really no step x step instructions on where everthing gets located (file system wise) and it took a while for me to wrap my head around the fact that everything was installed into >thunderbird< directories instead of >mozilla-thunderbird< , once I figured that out it went smoothly.

Haven't had a crash since upgraading and the spam filters seem to be much more robust (maybe just my perception).

Cheers
Ogre

---

### Post by macleod199 on 2006-01-17
This package was created with checkinstall, and seems to have some problems, especially if you have the thunderbird-enigmail extension installed.

---

### Post by jasplund on 2006-01-20
TB 1.5 is in dapper now

Johan

---

### Post by macleod199 on 2006-01-23
[QUOTE=jasplund]TB 1.5 is in dapper now

Johan[/QUOTE]

All the Ubuntu changes have yet to be merged into it. In particular the enigmail package isn't built.

---

### Post by OPaul on 2006-01-24
Once I've installed Thunderbird 1.5 with the mozilla.org download, where can I get an icon to use for top panel?

---

### Post by jbebel on 2006-02-06
ping.  This is in dapper.  What's the status of a backport?  There a couple reverse dependencies that I hope can also easily be backported, such as enigmail.

Joel

---

### Post by mr_pouit on 2006-02-07
[QUOTE=jbebel]ping.  This is in dapper.  What's the status of a backport?  There a couple reverse dependencies that I hope can also easily be backported, such as enigmail.

Joel[/QUOTE]

But the language packs aren't available for thunderbird 1.5 yet (only the old 1.0 version), so it can't be installed without removing language support... :???:

---

### Post by macleod199 on 2006-02-07
[QUOTE=jbebel]ping.  This is in dapper.  What's the status of a backport?  There a couple reverse dependencies that I hope can also easily be backported, such as enigmail.

Joel[/QUOTE]

The current recommendation from the debian/ubuntu maintainers is to just install the enigmail extension yourself, becuase they intentionally made an almost unpatched package of it. The debian/ubuntu patches will slowly make their way back in.

---

### Post by daacosta on 2006-03-03
[QUOTE=Miguel]AFAIK, Thunderbird should have no dependency problems. I haven't got dapper, but trying to uninstall thunderbird in my laptop does not ask for any other app to be uninstalled. 

**To use Thunderbird 1.5 as your default mail program in Ubuntu:**
[list][*]Download the binary from mozilla, site. 
[*] Unzip it to somewhere you have permissions. You don't need to unzip it in /usr/local if you don't plan to give it to every user. I would do
```
$ mv thunderbird-1.5.tar.gz ~/
$ cd
$ tar -zxf thunderbird-1.5.tar.gz

```
This will extract thunderbird-1.5 in your home folder in a folder named thunderbird-1.5
[*] Change or add a launcher at your taskbar that points at $HOME/thunderbird-1.5/thunderbird
[*] Go to System->Preferences->Favourite Applications and on the Mail reader tab choose "Custom", with the command "$HOME/thunderbird-1.5/thunderbird". You shouldn't check the "open in terminal" box
[*] If you want Thunderbird 1.5 to have access to your former e-mail,
```
$ cp -r ~/.mozilla-thunderbird/ ~/.thunderbird 
```
[/list]

This is longer said than done, and paths will change to wherever you have extracted thunderbird, but you get the idea. And the best thing of this is...

You don't need Root Power!!!!

OT: The real firefox problems is that, due to licensing, there is no i.e. libgecko (an html rendering library). And ubuntu uses gecko (firefox's engine) for all html rendering inside gnome. A new gecko version should be accompanied by a rebuild of every part that uses gecko for rendering. 

Kubuntu should not have those problems, though, as html rendering in KDE is done via khtml (OS X's safari uses it too)[/QUOTE]


Miguel,

In the installation wiki for Firefox 1.5 [https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion) everything is moved to the /opt folder.  Why the difference?

Rgds,


-D-

---

### Post by Zeroangel on 2006-03-13
IMO, the Klik version is better than the vanilla version. The Klik thunderbird 1.5 is only 15MB as a single file, whereas the Thunderbird 1.5 from the mozilla site is 30MB and must be extracted to a folder.

Also, I have noticed that the klik download of thunderbird seems to launch faster than the installed version, so that almost rules out the possibility of it being a compressed file.

Why would you want to extract thunderbird directly to home? There are no real practical reasons to do so and if anything it will just clutter up your home directory.

---

