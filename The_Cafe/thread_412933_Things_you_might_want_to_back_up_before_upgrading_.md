---
title: "Things you might want to back up before upgrading to Feisty"
date: 2007-04-18
forum: The Cafe
---

### Post by K.Mandla on 2007-04-18
A few staff members have been talking about things you should probably back up before you upgrade to Feisty, if you're considering it.

This is not to suggest you'll have problems, but that it would be good to have things like this duplicated somewhere, if something does go wrong. If you're planning on a clean install (which, personally, I suggest), you'll want to be as comprehensive in your backup as possible. If you're just going to dist-upgrade, it would still be a good idea to mirror these files elsewhere, just in case.

[LIST]
[*]**Personal files**. Of course.
[*]**Bookmarks**. Export your bookmarks from Firefox or your preferred browser, if it's possible. 
[*]**Passwords**. If you're used to the password manager in Firefox remembering your password, it would be wise to write it down or keep it somewhere else so it's not lost if you start afresh. (I've done that before. :oops: )
[*]**Extension settings**. Some extensions will allow you to export their settings (like Tab Mix Plus), so you can easily reapply them if you start new.
[*]**E-mail settings**. If you use Evolution or Thunderbird, make sure the settings and addresses are saved somewhere.
[*]**Saved games**. Some games keep high score files or folders (usally hidden with the dot prefix, like .warzone2100); if you want your saved games or player accounts, copy them to somewhere.
[*]**Setup files or libraries for games**. If you want to reinstall something like Neverwinter Nights, you might want to keep the client and patches somewhere.
[*]**Fonts**. If you add fonts to your machine, find out what they were, or your documents might look goofy when you open them again. :lol:
[*]**Icon sets and themes**. If you have icon sets, themes or wallpaper you like, make sure it's safe. I have a tendency to hand-edit a lot of Openbox themes, so I make sure I dupe my .themes folder.
[*]**.bashrc, etc., files**. If you customize your system to the point where you use .bashrc files, or .Xdefaults, or .gtkrc-2.0, or .gtkrc-mine, copy them too. If you don't know what those are, don't worry about them. ;) Don't forget your .conkyrc file. :)
[*]**Networking settings, passwords, etc**. If you use funky network settings, gateways, masks, address servers or some other wacky arrangement, copy the settings at least as a reference. Don't lose your access to ubuntuforums.org. We'd miss you while you were gone. 
[*]**/etc/fstab**. If you use a networked drive, or a Windows share partition, you might want to copy your fstab file, just as a reference. Remember that Feisty uses sd-series drive designations, so copy-and-paste in the fstab file is probably a really bad idea.
[*]**Drivers, firmware or configuration files**. Some cards or hardware might need firmware updates or drivers (like certain Broadcom cards, or RT61 cards). There's always the chance Feisty will pick up your card and it'll suddenly work like new. But if you're on a unique piece of hardware, make sure you're not running to the library with a USB drive to download a 248Kb file so you can get back online. (I've done that too. :oops: )
[*]**Unusual deb files you compiled or downloaded**. If you compile your own applications and keep debs somewhere, or if you downloaded an application from [GetDeb.net]("http://www.getdeb.net") or elsewhere, see if there's a copy around. (Keeping in mind, as SD-Plissken mentioned, that some applications might need recompiling under Feisty. That'll be for you to discover.)
[/LIST]
From [ComplexNumber]("http://ubuntuforums.org/member.php?u=76421"):

[LIST]
[*]Your **.tomboy **folder (or your Zim repository, if you're like me and you prefer Zim).
[*]Your **.mozilla** folder, but clear the cache folders first.
[*]Any **theme engines** or **GDM themes** you may have installed, and want to keep.
[/LIST]

Yes, it would probably work to just copy your /home folder onto an external drive, but that might not get everything. So think about it, and reflect for an hour or so, and make sure your upgrade is a pleasant one. 

And by all means, add to the list if you like. :D

---

### Post by karellen on 2007-04-18
a very comprehensive list...:D (I usually just burn some cd's with my /home folder content, and I reinstall the rest of the settings like themes/network config/fonts etc)

---

### Post by justin whitaker on 2007-04-18
You probably want to back up your audio files somewhere, and you want to back up your Rhythmbox.db file. if you added alot of podcasts. You should also save all your playlists, regardless of what audio player you use.

---

### Post by K.Mandla on 2007-04-18
Good call. I didn't think about music applications that might index your music.

---

### Post by Biochem on 2007-04-18
> **K.Mandla said:**
> [LIST]
[*]**/etc/fstab**. If you use a networked drive, or a Windows share partition, you might want to copy your fstab file, just as a reference. Remember that Feisty uses sd-series drive designations, so copy-and-paste in the fstab file is probably a really bad idea.[/LIST]

Why is it a bad idea? I did it and it worked. 
What is the difference between sd-series drive designattions and whatever it was before?

a n00b in search of enlightment

---

### Post by tbroderick on 2007-04-18
smb.conf
maildir if you are using one

---

### Post by H.E. Pennypacker on 2007-04-18
Shouldn't the list be "Back up whatever is important to you"?  Much of what is on that list, I would never backup.

---

### Post by FoolsGold on 2007-04-19
> **K.Mandla said:**
> 
[LIST]
[*]**Passwords**. If you're used to the password manager in Firefox remembering your password, it would be wise to write it down or keep it somewhere else so it's not lost if you start afresh. (I've done that before. :oops: )[/LIST]
Unless of course you're stupid like me and use the same exact password for EVERYTHING you do. :( 

Seriously, the experts suggest that you don't save your password in the manager because it's a security risk. In the same breath almost, they suggest a really complicated password that is hard to crack, but ultimately impossible to remember. Let's not forget you shouldn't write the password down anywhere, as this is also a security risk. What are you suppose to do?

---

### Post by K.Mandla on 2007-04-19
> **Biochem said:**
> Why is it a bad idea? I did it and it worked. 
Hey, if it worked, cool. :)

---

### Post by K.Mandla on 2007-04-19
> **H.E. Pennypacker said:**
> Shouldn't the list be "Back up whatever is important to you"?  Much of what is on that list, I would never backup.
To each his own. It's meant more as a list of reminders, in case someone has installed something, and wants it to carry over to a new installation. Some of those things I don't bother backing up either, but that's going to differ between people. ;)

---

### Post by K.Mandla on 2007-04-19
> **FoolsGold said:**
> Seriously, the experts suggest that you don't save your password in the manager because it's a security risk. In the same breath almost, they suggest a really complicated password that is hard to crack, but ultimately impossible to remember. Let's not forget you shouldn't write the password down anywhere, as this is also a security risk. What are you suppose to do?
:mrgreen: Beats me. I don't use the password manager, because I got burned once. And I change passwords every three months, using [a random password generator]("https://www.grc.com/passwords.htm"). Has it been worth the effort? Probably not. But until computers can scan brainwaves, I suppose we're both stuck. :lolflag:

---

### Post by FoolsGold on 2007-04-19
> **K.Mandla said:**
> I don't use the password manager, because I got burned once.
What happened? Did someone discover the "Show Passwords" button or something?

---

### Post by K.Mandla on 2007-04-19
No, I just got sloppy and forgot three or four passwords that were in the password manager. I reinstalled and couldn't remember them. I felt ... kind of like this: :oops:

---

### Post by PartisanEntity on 2007-04-19
I usually do a clean install, but this time I would like to upgrade, will X server crash due to the latest Nvidia drivers I am using? What are your experiences with upgrading and graphics drivers?

---

### Post by K.Mandla on 2007-04-19
Depends on the card. I haven't dist-upgraded in a while, but that's because I use a Geforce4 440 Go, which somehow fell through the cracks in the 9631 driver, and I get a dead screen. 

Which card are you using?

---

### Post by PartisanEntity on 2007-04-19
I have the Nvidia GeForce Go 6200.

I am also using TwinView in order to use my TFT monitor with my laptop (so I have added the necessary changes to xorg.conf).

---

### Post by K.Mandla on 2007-04-19
Unless I'm mistaken, a Go 6200 should still use nvidia-glx and the 9631 driver. I don't know that there's a canonical list (other than [this old one]("http://http.download.nvidia.com/XFree86/Linux-x86/1.0-8762/README/appendix-a.html")), but I think the new nvidia-glx package is intended for FX cards and later.

---

### Post by beercz on 2007-04-19
I backup up /home and /etc on a daily basis using to a backup server using [rsnapshot]("http://rsnapshot.org")
Therefore I am happy to update, upgrade or completely mess around with my system to my heart's content, knowing that I will be able to recover quite quickly and not loose anythint,

---

### Post by picpak on 2007-04-19
Other suggestions:

.mplayer/config
/etc/mpd.conf
.desklets (or wherever you keep your adesklets/gdesklets/etc, I know I don't like losing the configs for these)
.qt (If you theme programs with qt3config, this is a good one to backup)
.gftp (Keep your bookmarks! It's also good to backup if you autologin)
.pan2 (I know I can't remember Usenet connection information...also useful if you save articles)
.Xmodmap, .xbindkeysrc (only if you have customized keys on your keyboard)
.nanorc

Really, just backup your /home...or put it on a separate partition, it lets me reinstall with ease.

---

### Post by Muppeteer on 2007-04-20
Thanks for the list...

I'm gonna do a clean install too as Edgy was the first time i really got into linux and i've experimented a lot, so it would be nice to start fresh :) 

It took me ages to get my xorg.conf setup for my mouse and keyboard etc, can't remember if that was on the list but it's the first thing on my list :)

---

### Post by Rhapsody on 2007-04-20
The only thing really important to me is the firmware I need to get my router working. Seeing as I have no less than three copies of that on floppies (and one more on my separate /home partition), I feel pretty safe. Everything else on here is quite replaceable.

---

### Post by Endolith on 2007-04-20
> **FoolsGold said:**
> Seriously, the experts suggest that you don't save your password in the manager because it's a security risk. In the same breath almost, they suggest a really complicated password that is hard to crack, but ultimately impossible to remember. Let's not forget you shouldn't write the password down anywhere, as this is also a security risk. What are you suppose to do?

Come up with something that *looks* random but is actually well-defined, like... concatenating the first initials of the presidents of the United States in order:

[G]eorge Washington
[J]ohn Adams
[T]homas
[J]ames
[J]ames
[J]ohn
...

would make a password like "gjtjjj...".  Looks random, but isn't.  Make sure it's not something that can be guessed, like if you're a Star Trek nerd don't memorize something Star Trek related, but it should be something that you can easily look up and that won't vary from one place to another.   You memorize the "key" to retrieving your password, in other words, but you don't have to memorize the password itself, and it's not written down where someone can find it.  Of course you will tend to memorize the password itself by typing it over and over again, but if you ever forget the exact letters, you can look it up.

---

### Post by RedSquirrel on 2007-05-01
> **K.Mandla said:**
> 
And by all means, add to the list if you like. :D


If you have any **important email messages** that you haven't yet saved in another location (printed out or saved as a text file somewhere else) then you should back those up too. I had some semi-important emails that I forgot to save before wiping with KillDisk. Not the end of the world, but I was a little disappointed when I realized that I had forgotten all about them.

I also saved **/etc/X11/xorg.conf** since I did a fair bit of tweaking with it. It's still possible to cut & paste a lot of that stuff rather than doing it from scratch.

---

### Post by diskotek on 2007-05-01
i think i had to read this thread last week. by the way that's great thread...

may be you can add .msn & .gaim (for sessions etc) / .amule (configs & temp files) / .exaie (or players like that for database indexes, haha but i'm not sure if it's works)... and of course **.conkyrc**

ok these are specific things....

---

