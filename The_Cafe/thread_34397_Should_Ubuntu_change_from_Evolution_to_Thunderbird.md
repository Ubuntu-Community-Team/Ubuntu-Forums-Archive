---
title: "Should Ubuntu change from Evolution to Thunderbird?"
date: 2005-05-14
forum: The Cafe
---

### Post by RastaMahata on 2005-05-14
By default, Ubuntu installs Evolution as your mail client. Many people dont uninstall it because of the "ubuntu-desktop is going to be uninstalled too" fear.

I was reading a bit about thunderbird, and found out something about a calendar program in the works (sunbird, and lightning in the case of mozilla suite... i think). So far, it seems that thunderbird/mozilla is about to get a calendar, as an incorporation to the software or an application apart.

With all of this calendar projects in the works, should Ubuntu change it's default mail client from Evolution to Thunderbird? Should Ubuntu devs work in the integration of Thunderbird into Gnome?

Please forgive my english :(

---

### Post by TravisNewman on 2005-05-14
Lightning will actually tie sunbird and thunderbird together, from what I understand.

But I don't really have much of an opinion here. If thunderbird is chosen, probably about the same amount of people who currently don't uninstall Evo because of removing u-d, will install Evo and not uninstall Thunderbird because of removing u-d.

---

### Post by WildTangent on 2005-05-14
i think so, i like thunderbird alot more than evolution. i use it on all my windows and linux machines

-Wild

---

### Post by TravisNewman on 2005-05-14
[QUOTE=WildTangent]i think so, i like thunderbird alot more than evolution. i use it on all my windows and linux machines

-Wild[/QUOTE]
 Maybe that's why the baby's so upset. ;) The baby wants you to use evolution. The baby will eat you if you don't.

love that avatar.

I think that whatever is chosen, there should be a good way to uninstall the default and install the non-default without uninstalling ubuntu-desktop. It IS only a metapackage, but if you keep it around for 6 months and want to dist-upgrade, not having that ubuntu-desktop package can cause problems. Caused LOADS from Warty to Hoary if you didn't have it.

---

### Post by RastaMahata on 2005-05-14
[QUOTE=panickedthumb]Maybe that's why the baby's so upset. ;) The baby wants you to use evolution. The baby will eat you if you don't.

love that avatar.

I think that whatever is chosen, there should be a good way to uninstall the default and install the non-default without uninstalling ubuntu-desktop. It IS only a metapackage, but if you keep it around for 6 months and want to dist-upgrade, not having that ubuntu-desktop package can cause problems. Caused LOADS from Warty to Hoary if you didn't have it.[/QUOTE]
 so first, the mail client shoudl be removed from the meta package "ubuntu-desktop", and THEN changed to something else (thunderbird) ?

---

### Post by arctic on 2005-05-14
although thunderbird is an okay mail client, i prefer evolution because it offers a complete package for administrating my everyday work-stuff in a simple and efficient manner. and sunbird is yet far away from a stable release.

stick to evolution as long as it does the job we expect it to do.

---

### Post by TravisNewman on 2005-05-14
I think it's possible to have an either/or dependency so you can have it depend on either Evolution, thunderbird, or something else

---

### Post by WildTangent on 2005-05-14
[QUOTE=panickedthumb]Maybe that's why the baby's so upset. ;) The baby wants you to use evolution. The baby will eat you if you don't.

love that avatar. [/QUOTE]
guess i cant change it now ;)

-Wild

---

### Post by Lovechild on 2005-05-15
Evolution is nicely integrated in my GNOME desktop, I like how it works with my panel clock to show me when I have something I need to do.

Call me when Thunderbird even gets close to being a HIG application with the same feature set as Evolution.

---

### Post by Dylanby on 2005-05-15
I prefer Evolution.
As long as both are officially supported in main I don't see the point of changing the default. Gnome is Ubuntu's default & Evolution is part of Gnome.
Canonical would like to grab some corporate desktops too & I think Evolution's feature set is a better match for this audience.

---

### Post by 23meg on 2005-05-15
i'd vote for evolution, for both corporate and personal use. a few reasons off the top of my head: more stable, loads faster, vfolders, working calendar. it would be nice but not essential to have a choice at setup though, and even nicer if evolution could be unintstalled without touching ubuntu-desktop.

---

### Post by TravisNewman on 2005-05-15
I'd like to see Evolution get GOOD nntp and imap support. Then I'd totally use it. It's got the calendar and the integration and everything, but these basic things it chokes on.

I'd also like to see either of them have a decent extension/plugin for a notification area icon.

Edit: well I'll be. You CAN do NNTP in Evolution. Its strange and not concise, but you can do it. I'll be giving it another shot ;) It's still got some IMAP problems, so hopefully I don't run into those.

---

### Post by rwabel on 2005-05-15
Evolution has much more features and is for sure the better choice in enterprises. For me thunderbird is the better fit and you can switch to windows while using the same mails etc.

the plans with thunderbird to include the calendar and more such features is great thing. I hope that ubuntu can help there too and includes thunderbird more in gnome.

---

### Post by Segovia on 2005-05-15
I don't find Thunderbird to be very useful.  I suppose it's OK for sending a couple emails a week to Grandma, but for business use it chokes hard-core.

My inbox averages around 6-10 gigs, usually around 4000-6000 emails (most with large attachments).  Thunderbird has EXTREME problems with this volume of email.

---

### Post by rosslaird on 2005-05-15
OK, just to take the other side:
Thunderbird is far better at dealing with IMAP accounts than Evo.
Thunderbird has better Junk filtering, is faster, offers excellent RSS integraiton, has better mail notification (by way of the notification area with an extension, something Evo does not have). I've used both extensively, and I do prefer TB.

Now, a preview release of Sunbird 0.2 is available in Deb format  [here](http://www.asoftsite.org/s9y/) . Unfortunately, it does not install in Ubuntu. I emailed the packager and he emailed back:

"If you find someone who is willing to build an ubuntu package, I can send him the diff, so he can actually build an ubuntu package."

Anybody know how to do this, or want to do this?

Ross

---

### Post by Dylanby on 2005-05-15
Sunbird is in universe as mozilla-calendar.

---

### Post by pjack76 on 2005-05-16
I vote Thunderbird. I hate Evolution, because Evolution reminds of me of Outlook, and I LOATHE Outlook. 

I very much prefer the way Mac OS X does it: Three different applications, each with its own specialized, simple and to the point user interface. In this sense I think Evolution breaks GNOME's own HIG.

I think there should be a concept of "Interchangeable parts" here. A simple Address Book application with an LDAP interface, so ANY mail program can read from it to autocomplete addresses. I think the mailto: URLs are already handled at a system level, so Firefox knows what mail agent to open when I click a link. Is there a Calendar standard? If so I don't see why everything must be integrated into one monolithic beast.

On a similar note, it would be lovely if the Palm conduit didn't depend on Evolution. Again, I don't see why the Palm conduit can't just read from LDAP and produce Palm-format whatever it produces.

---

### Post by rwabel on 2005-05-16
[QUOTE=Dylanby]Sunbird is in universe as mozilla-calendar.[/QUOTE]
 I don't think that mozilla-calendar from hoary is sunbird? I've installed it but it's just the integration into mozilla.

---

### Post by rosslaird on 2005-05-16
Right. The mozilla-calendar and sunbird share code, but they are not the same thing. Sunbird is a stand-alone application. Also, the version available from asoftsite.org is the May 10 0.2+ version of Sunbird, which is significantly newer than the Jan.11 version of the calendar extension available for Thunderbird/Mozilla/Firefox.

Ross

---

