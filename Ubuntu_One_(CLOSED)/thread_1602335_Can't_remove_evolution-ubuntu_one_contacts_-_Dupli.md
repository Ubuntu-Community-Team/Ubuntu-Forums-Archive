---
title: "Can't remove evolution-ubuntu one contacts - Duplicate couchdb entry in gnome-keyring"
date: 2010-10-21
forum: Ubuntu One (CLOSED)
---

### Post by ghedda on 2010-10-21
Hi,
looks like many people had issues in deleting multiple contacts from evolution-couchdb-ubuntuone address book. I had an issue (on more than one pc, and different ubuntu one accounts) and can't recognize if there are related posts. Something is messed up, but why?

The reason why I'm opening a new thread is to ask: is gnome-keyring manager expected to have two entries for couchdb in the default behavior?
Or this may be the cause of everything messing up?

This is my issue.

I want to erase my address book. After Ctrl+A > Ctrl+D > Yes and no effect, I can't delete single nor multiple contacts. Evolution states:

"Eliminazione del contatto non riuscita. Altro errore"

In Italian that means: Cannot delete the contact. Other error. (Maybe: undefined eror, unexpected error in en localization).

---

### Post by LaptopU on 2010-10-22
I am having exactly this problem.  I can edit and delete contacts online and they will appear fine on Evolution, but I cannot edit or delete contacts on Evolution at all.

More annoyingly I have two blank contacts on Evolution that do not appear online and I cannot delete these either, because they do not appear online I cannot get rid of them at all.  Very annoying.

---

### Post by ghedda on 2010-10-26
So do I. I omitted that in my previous post. Three empty contacts that are not listed on the web interface. I can't delete both regular and empty contacts from evolution.

---

### Post by NHclimber on 2010-10-26
I filed a bug in Launchpad for part of this (#666404 - Cannot reliably delete contacts).  You can add your comments there plus mark that it effects you - that will help get it fixed faster.

---

### Post by Dr.Dran on 2010-10-30
I'va add a commet in launchpad!

This is an annoying bug... I'll hope that someone of the ubuntu one team solve this problem.

Best Regards

Franco

---

### Post by ds_shellback on 2010-10-30
Also suffering from this problem - it's very frustrating.

I've added my comment to your bug report.

Looking forward to a solution

---

### Post by gino90 on 2010-11-01
Hi,I have the same problem as you folks have..marked the bug as affecting me,hopefully this is going to be fixed soon!:(

---

### Post by EsbenHaabendal on 2010-12-07
I have the same problem(s) here.

3 empty contacts in Evolution Ubuntu One addressbook that cannot be deleted and which does not appear online, and I cannot delete or modify contacts in Evolution Ubuntu One addressbook.

---

### Post by L33tCh on 2010-12-08
Well, I checked my Ubuntu One account on the web and the contacts hadn't been uploaded there yet, so I then logged directly onto my local couchdb management page (you can get to it by opening this file in a browser "[FONT=Courier New]~/.local/share/desktop-couch/couchdb.html[/FONT]") and deleted the whole contact database and created a new one... You can also edit them one at a time but I didn't see any way to delete multiple other than what I did, removing all.

---

### Post by duanedesign on 2010-12-08
> **NHclimber said:**
> I filed a bug in Launchpad for part of this (#666404 - Cannot reliably delete contacts).  You can add your comments there plus mark that it effects you - that will help get it fixed faster.

This morning I grouped together the different reports on this issue.
The 'master' bug for this is [LP:673568]("https://bugs.launchpad.net/evolution-couchdb/+bug/673568") There is a developer assigned to this bug so it is being worked on.

The reason why contacts cannot be edited or deleted is the corrupted internal structures of the document that is being JSON-encoded via couchdb-glib and then sent to CouchDB. CouchDB does not like invalid keys in the document and returns Bad Request

thank you,
duanedesign

---

