---
title: "Upgrade to oneiric failed... what's next?"
date: 2011-11-20
forum: Server Platforms
---

### Post by Trunkles on 2011-11-20
Hi folks.
I upgrade my server to oneiric and eek! Pain when rebooting.. kernel panic!

I've got it running by starting the previous version but things like postfix aren't happy - can't send mail.

So... what next... re-do the upgrade and see what happens?

Or what. :)

Simon.

---

### Post by Paddy Landau on 2011-11-20
I'm answering because I see no one else has answered you.

Often, upgrades don't work so well or even at all. It is always safer to back up all your data and do a fresh installation.

If your home folder is on a separate partition, this is normally painless (as long as you remember not to format the home folder).

So, my suggestion is to back up **all** your data (it's probably worth backing up the entire /home folder, but take care if any users' folders are encrypted as you need to back up the **de**crypted data); install 11.10 from scratch; and, if necessary, restore your data.

---

