---
title: "Please please please let me delete my tomboy notes!"
date: 2010-12-30
forum: Ubuntu One (CLOSED)
---

### Post by Budoc on 2010-12-30
Hi,

Back when Ubuntu One first became available, I used it to back up important files and I tested out things like the tomboy sync. However, now I wish to only use Ubuntu One for my files, and not my tomboy notes. For some reason, I am only offered the chance to remove my 400+ tomboy notes one by one, and not all at once on [https://one.ubuntu.com/notes](https://one.ubuntu.com/notes). According to [https://answers.launchpad.net/ubuntuone-servers/+faq/927](https://answers.launchpad.net/ubuntuone-servers/+faq/927) by removing the contents of .local/share/tomboy I should be able to restart tomboy with no notes and then sync up with Ubuntu One. However, this does not work for me. If I close tomboy, rm -r ~/.local/tomboy and then restart tomboy by readding it to the panel, an older version of .local/tomboy is present again with old copies of my notes. 

Does anybody have another method of clearing my tomboy notes off Ubuntu One?

I also tried deactivating my Ubuntu One account for a couple of months, but my uploaded data was still there when I set everything up again.

---

### Post by peterfernandes238 on 2010-12-31
I wish to only use Ubuntu One for my files, and not my tomboy notes.
---------
Peter fernandes

---

### Post by sharm on 2010-12-31
Hi Budoc.  You probably have an old copy of your note directory in ~/.tomboy, which is where older versions of Tomboy used to store notes.  By deleting ~/.local/share/tomboy, you put Tomboy back in a state where it is trying to be helpful by copying over your notes from the old directory.

Instead of rm -rf'ing ~/.local/share/tomboy, you should just `rm ~/.local/share/tomboy/*.note` (still, only do it when Tomboy is not running).

And, assuming you already have a backup of your notes, you may as well `rm -rf ~/.tomboy` too.

---

### Post by Matt G Dalian on 2011-01-02
I ran into the same problem.

Here's what I did to fix it:

Open up Tomboy (with no notes on it). Then sync your notes with Ubuntu One.

The firs time you do this, it will download all of your notes from the server.

Then close Tomboy and delete all .note files in your ~/.local/share/tomboy directory.

Now open up Tomboy and sync again with Ubuntu One, and it should delete all of the notes on the server.

---

### Post by Budoc on 2011-01-07
Thank you very much for all of your responses. **Sharm** you were quite correct in assuming that I had an old .tomboy folder in my home directory. I've now removed it.

> **Matt G Dalian said:**
> I ran into the same problem.

Here's what I did to fix it:

Open up Tomboy (with no notes on it). Then sync your notes with Ubuntu One.

The firs time you do this, it will download all of your notes from the server.

Then close Tomboy and delete all .note files in your ~/.local/share/tomboy directory.

Now open up Tomboy and sync again with Ubuntu One, and it should delete all of the notes on the server.

Thanks for this. Unfortunately, when I right click on the tomboy panel applet and select synchronise it pulls some of the notes off ubuntu one and then gives me a fairly unhelpful error message of "Failed to Synchronise. Could not Synchronise notes. Check the details below and try again". The details below are simply a list of perhaps 50 - 80 notes that it has downloaded to ~/.local/share/tomboy along with the word "added" next to them.

Also confusingly, in my tomboy preferences I have in the dropdown menu under synchronisation service both a Tomboy Web service (server: [https://one.ubuntu.com/notes/](https://one.ubuntu.com/notes/) ) and a Ubuntu One service. Which of these do I use? I assumed that they were duplicates of the same thing. 

Thanks in advance, and apologies for taking a while to express my appreciation for the posters in this thread.

---

### Post by sharm on 2011-01-07
> **Budoc said:**
> Also confusingly, in my tomboy preferences I have in the dropdown menu under synchronisation service both a Tomboy Web service (server: [https://one.ubuntu.com/notes/](https://one.ubuntu.com/notes/) ) and a Ubuntu One service. Which of these do I use? I assumed that they were duplicates of the same thing.

They are. "Tomboy Web" is the upstream name for the API that is used for web sync, which is implemented by both Ubuntu One and Tomboy Online (aka Snowy).  The Ubuntu guys made initial authentication a bit easier for U1 by adding an "Ubuntu One" service that is totally identical except in how it does auth when you first set up sync.

---

