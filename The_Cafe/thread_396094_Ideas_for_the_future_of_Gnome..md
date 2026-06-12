---
title: "Ideas for the future of Gnome."
date: 2007-03-29
forum: The Cafe
---

### Post by junior aspirin on 2007-03-29
I have been reading allot about the future of Gnome lately. Here is a list of features that i would like to see included in the future.  I will say though that these are mostly not my ideas, but just grouping together ideas floating around the web.

The main topics i will discuss here are: Tagging and Search, Extensibility, Integration of Applications and Services, Splitting up Evolution, Contextual Menus and Toolbars and Instant save.

[B]
Tagging and Search.[/B]
Desktop search: Tracker/Beagle should be installed by default which indexes everything in the users home directory.
Tagging: There should be a global uniformed way of tagging data meta-data, so every application can take advantage of it from one database file which is directly linked with the search daemon.

Now that search and meta-data are directly linked, Tracker/Beagle should be integrated into almost every gnome application so they can all take advantage of the user specific data. This would prevent duplication amongst programs, at the moment epiphany,f-spot etc. each have their own ways of tagging files and data which makes it awkward for other applications to make use of, using a uniform solution nautilus, gimp, and any other application can make use of this information.
As part of an applications UI there should be a search bar (preferably in the top right of the application to keep consistent) that utilises Tracker, but limited to what the application can handle. eg. in fspot only image data, rhythmbox only audio etc. this could also have live queries (like firefox 2.0's search box).  Tags can be made in any program and be accessible in any other, a good use for this is in nautilus.  
E.g. Had a big event or party and want to keep everything organised or find quickly. a simple search in nautilus would bring up everything tagged with "Holiday" including emails, music, photos, notes, IM Conversations, which could also be set as a saved search.
Tags should replace Genres in Rhythmbox since they would be far more useful, and are practically the same thing.
Tagging should also be prescient in the save dialogue.

**Extensibility**
Using Firefox as an example, it has been shown that plug-ins can help make a program more customisable to the user and also allow other users to create them, which the application maintainer has no interest in implementing. I believe that most applications can take advantage of plug-ins, rhythmbox, gedit and epiphany already do. but others don't like f-spot, inkscape...OK in fact most do, but it is not obvious to the user, they need to have a default layout and location in the menus.
[B]
Integration of Applications and Services[/B]
The telepathy project is starting to take shape now. once it matures it would be good if more applications made use of it. No need for Gaim to be open all the time, a simple Status applet on the panel would be good enough, that could be set to sign in on log on. Jokosha already wants to make use of it for collaborative recording, Abiword etc could also make use of this.  I will come back to this later.

**Split evolution**
Evolution should be split into smaller programs that do its jobs, but better. it is simply too buggy and bloated at the moment.  The back-end could possibly be kept as a standard database for all email clients, address books, and calenders.  If you decide you do not like a certain mail program, just switch to another, no importing mail and address books, its just a front-end.  Im not sure of any email clients like this available at the moment, but tinymail may be suited, but i may be wrong. This is where telepathy links,if a user is on-line who sent you an email is on-line, the mail program will notify you in some way, possibly linked by the address book...
'Contacts' should replace Address books, they don't just contain email addresses but birthdays, phone numbers etc , so why doe evolution have to be running to access it easily. it should be its own small app, accessible to any program (abiword for mail merges...). telepathy here again, there address book should be used for storing all of your contacts details, if they are on-line it will tell you. this would also enable multiple email addresses and user names to be linked to one contact, useful for the mail program above.
Dates is a small program that aims to replace the calender functionality of evolution, why do you want to open a huge program like evolution to add a reminder.  i have also seen a modified clock applet mock up that allows you to add dates on the fly.
Tasks is another small program being developed to replace the functionality of evolution.
Again all this should be integrated together. Dates should list birthdays from Contacts, Tasks with deadlines should be shown in the calender and it goes on, of course all this data is tag-able and search able through tracker/Beagle.

**Contextual Menus and Toolbars**
Something i read by Jono Bacon, the fact that menus and toolbars should know what you want to do. if a button is greyed out, why show it?  programs could possibly Learn from what functions you use most, but implemented in a far more intuitive way than those annoying compacted menus that Windows insists upon.

**Instant save**
Why must we save everything before a document is closed, why not auto save like tomboy?  Why does undo not persist once the document is closed. undo/redo information should be saved along with the file (probably not in the file but maybe as /.undo.FILE.odt a hidden file that is saved in addition to the document itself)


The above may sound complex, but the fact is allot of the software and mechanisms are already there. Telepathy, tracker and tagging are all actively being developed and are reaching a use-able state.  Open source has a great opportunity over closed/proprietary since everything is easy to use and get hold of. Imagine being able to link meta-data search into some windows applications. On windows everyone (especially Microsoft) wants you to use their product, think MSN Messenger opening Internet Explorer, not the default browser. there are about 5 different desk top search engines for Windows all done differently with no chance of easily being integrated.


i hope that immensely long rant made sense! opinions?...

---

### Post by karellen on 2007-03-29
well mail these suggestions to the gnome developers ;). it's the best way to bring your ideas to life

---

### Post by siimo on 2007-03-29
> **junior aspirin said:**
> 
**Contextual Menus and Toolbars**
Something i read by Jono Bacon, the fact that menus and toolbars should know what you want to do. if a button is greyed out, why show it?  programs could possibly Learn from what functions you use most, but implemented in a far more intuitive way than those annoying compacted menus that Windows insists upon.


This is because users prefer to have some consistency.  Otherwise how would they know a function is not available.  They would be thinking.... where the heck is my "X button"!! instead of seeing it grayed out and realising that function isn't available with what they are working with currently.

---

### Post by vificunero on 2007-03-30
I think gnome needs a cleaning tool for all the file left in the home dir by all the programs. Epiphany cache, nautilus thumbnails, recent documents and so on.

---

### Post by Ryoushi19 on 2007-07-31
Here's one I've noticed:  you can drag things from the application bar, but there's no way to drop them.  What's the point of that?  They should add some functionality to that if it's going to be possible.

---

### Post by mech7 on 2007-07-31
i think it will take a very long time before these features are implented.. its taken now 2 years and still no drag and drop support from file roller :confused:

---

### Post by Ultra Magnus on 2007-07-31
Best customisation like in KDE

---

### Post by bread eyes on 2007-07-31
Merge with KDE and just provide patches to make KDE Gnome-like. Seriously, that would be nice.

---

### Post by DC@DR on 2007-07-31
> **bread eyes said:**
> Merge with KDE and just provide patches to make KDE Gnome-like. Seriously, that would be nice.

I'd prefer keeping Gnome and KDE separated, provided the apps could be bundled with proper theme-engines so they would look native on each DE, so we could keep our own taste without sacrificing the native look&feel of common apps  :)

---

### Post by bread eyes on 2007-07-31
> **DC@DR said:**
> I'd prefer keeping Gnome and KDE separated, provided the apps could be bundled with proper theme-engines so they would look native on each DE, so we could keep our own taste without sacrificing the native look&feel of common apps  :)

I'm sure a Gnome-like KDE would retain the look and feel of gnome.

---

### Post by hanzomon4 on 2007-07-31
I like your suggestions, my Gnome now seems so outdated... Thanks

---

