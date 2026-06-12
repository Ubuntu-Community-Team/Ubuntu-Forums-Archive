---
title: "Remix - Cannot add or copy contacts"
date: 2010-05-01
forum: Ubuntu One (CLOSED)
---

### Post by marcadams on 2010-05-01
Hi All;

Yesterday I installed Lucid Remix on my wife's computer, and trying to get files, contacts notes etc, all synchronized on Ubuntu One.

I've got everything working, except for Evolution Contacts

On the Ubuntu One address book, when I right click, the ability to add a new contact is disabled. When trying to copy from my personal address book into the Ubuntu One address book, nothing happens.

Also, I've added a contact via the Ubuntu One website interface, and so far that hasn't synchronised up with Evolution either.

I've been working on this issue for many hours now, and beginning to get a little frustrated - any help would be greatly appreciated !

Thanks,
Marc

---

### Post by joshuahoover on 2010-05-03
> **marcadams said:**
> Hi All;

Yesterday I installed Lucid Remix on my wife's computer, and trying to get files, contacts notes etc, all synchronized on Ubuntu One.

I've got everything working, except for Evolution Contacts

On the Ubuntu One address book, when I right click, the ability to add a new contact is disabled. When trying to copy from my personal address book into the Ubuntu One address book, nothing happens.

Also, I've added a contact via the Ubuntu One website interface, and so far that hasn't synchronised up with Evolution either.

I've been working on this issue for many hours now, and beginning to get a little frustrated - any help would be greatly appreciated !

Thanks,
Marc

Hi Marc,

You should be able to add contacts to the Ubuntu One address book. Do you get any error when you try to copy contacts there or does it just not let you do it? If this problem persists can you do the following?

[LIST=1]
[*]Open Applications->Accessories->Terminal, and  run: 

[LIST]
[*]evolution --force-shutdown /usr/lib/evolution/evolution-data-server-2.28  > ~/evolution_debug.log 
[/LIST]
[*]Open Applications->Internet->Evolution Mail 
[*]Try to copy contacts or add new ones
[*]File a bug report at: [https://bugs.edge.launchpad.net/evolution-couchdb/+filebug](https://bugs.edge.launchpad.net/evolution-couchdb/+filebug)
[*]Attach ~/evolution_debug.log to the bug report
[/LIST]
Syncing contacts isn't going to work right now as we had to turn off the service. Ubuntu One has been experiencing large spikes in new users and overall use with the release of Lucid and is making certain key parts of the system to not function properly. We're working on fixing these problems. We'll keep you updated in two ways on our progress:

1) [http://identi.ca/ubuntuone](http://identi.ca/ubuntuone)
2) [https://wiki.ubuntu.com/UbuntuOne/Status](https://wiki.ubuntu.com/UbuntuOne/Status)

Thank you,

Joshua

---

### Post by marcadams on 2010-05-03
Hi Joshua;

For some quick feedback:
- The menu item to add a new contact in the Ubuntu One address book is greyed out. So I cannot even attempt this.
- When I attempted to copy personal -> Ubuntu one book, simply nothing happened (no visual error )

I will follow your instructions, and try to provide more details

Thanks
Marc

---

### Post by zorrak on 2010-11-15
> **marcadams said:**
> Hi Joshua;

For some quick feedback:
- The menu item to add a new contact in the Ubuntu One address book is greyed out. So I cannot even attempt this.
- When I attempted to copy personal -> Ubuntu one book, simply nothing happened (no visual error )

I will follow your instructions, and try to provide more details

Thanks
Marc

Hey,

I'm having the exact same problems since a few hours ago.

---

