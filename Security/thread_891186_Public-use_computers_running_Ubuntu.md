---
title: "Public-use computers running Ubuntu"
date: 2008-08-15
forum: Security
---

### Post by altonbr on 2008-08-15
Hi everyone,

I've been asked by a friend of mine to help him finalize his Internet cafe. He'll have about 10 Windows XP computers for gaming and 4 Ubuntu computer for free use (1-hour limit).

I've been installing Ubuntu on the desktop since 5.10 and in fact have my own scripts to speed the process, but I'm wondering if anyone would like to share their tips on securing public use computers.

What do you think would be smartest? Thin-clients?

What about programs and personal preferences? I don't want programs like Firefox and Pidgin to remember e-mail addresses and I don't want people to be able to edit the Firefox settings.

Nor do I want a document memory such as 'Places > Recent Documents...' but I can get rid of that by remaking .recently_used.xbel to a folder, correct?

Essentially I'll make a stripped down user that has no admin privelages and give root a very cryptic password so that reboot and boot as root backdoor can not be used.

Stuff like that. Can anyone share their experiences?

I appreciate your help!

---

### Post by Mister.Vash on 2008-08-16
Have you thought about something along this line?
[http://www.debiosk.org/](http://www.debiosk.org/)
Basically a debian kiosk

---

### Post by Oldsoldier2003 on 2008-08-16
you can use kiosk mode in Kubuntu. its a KDE feature.

---

### Post by altonbr on 2008-08-16
I think something like Sabayon ([http://www.gnome.org/~seth/blog/sabayon](http://www.gnome.org/~seth/blog/sabayon)) and some GNOME tweaking ([http://www.redhat.com/docs/manuals/enterprise/RHEL-4-Manual/desktop-guide/ch-ddg-lockdown.html](http://www.redhat.com/docs/manuals/enterprise/RHEL-4-Manual/desktop-guide/ch-ddg-lockdown.html)) is what I was looking for.

(Thanks to [https://answers.launchpad.net/ubuntu/+source/firefox/+question/1169](https://answers.launchpad.net/ubuntu/+source/firefox/+question/1169)).

What about Edubuntu and the thin-client to server method. How would I go about setting that up?

---

### Post by FakeOutdoorsman on 2008-08-16
I've often wondered this myself. I would personally try the thin client setup, not based on any experience, but because I've never tried it before and it sounds interesting.  I believe it also has the potential to be less work since you only have to keep one machine updated and maintained instead of 4.  Since you only have 4 to begin with, would using one machine as a LTSP server make it unusable to the public?  Here's a good start from the Wiki:
[Thin Client Howto]("https://help.ubuntu.com/community/ThinClientHowto")
[Ubuntu LTSP Quick Install]("https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall")

---

### Post by Scotty Bones on 2008-08-17
for the firefox side of things
1.  under the preferences, privacy tab- check mark "Always clear my private data when I close firefox" and uncheck "Always ask before clearing private data".
2.  There are some add-ons that can help lock down FF like public fox [https://addons.mozilla.org/en-US/firefox/addon/3911](https://addons.mozilla.org/en-US/firefox/addon/3911)

---

