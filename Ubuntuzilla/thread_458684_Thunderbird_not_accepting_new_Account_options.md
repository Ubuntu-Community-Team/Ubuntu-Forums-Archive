---
title: "Thunderbird not accepting new Account options"
date: 2007-05-29
forum: Ubuntuzilla
---

### Post by shane2peru on 2007-05-29
Ok, here is what happened to the best of my memory.  I switched my account from IMAPI to the pop.  I duplicated the accounts and then put in a bad server name for the imap one.  Left it for a few days.  I decided I didn't need it any longer and deleted the account from the **Edit -> Account Settings** from within Thunderbird.  I accidentally deleted the wrong account, :oops:  I know that was dumb because it even asks you to confirm.  Sometimes my fingers go faster than my brain does.  So I put all the settings back in, and then remembered I had just rsync'ed to my external hdd, so I shut down Thunderbird and just restored that directory.  Then I reopened TB, and went to delete the other account.  Deleted fine, but now any time I want to try and change any settings in any account in TB, and I hit OK, at the bottom it does NOTHING!  The window doesn't even close unless I hit cancel or the X.  Does anyone have any ideas as to what this could be?  or how to fix it?  Thanks.

Shane

PS, I'm using the TB installed from the scripts here, and haven't had any problems.  This one seems to be one of my own making.

---

### Post by nanotube on 2007-05-29
> **shane2peru said:**
> Ok, here is what happened to the best of my memory.  I switched my account from IMAPI to the pop.  I duplicated the accounts and then put in a bad server name for the imap one.  Left it for a few days.  I decided I didn't need it any longer and deleted the account from the **Edit -> Account Settings** from within Thunderbird.  I accidentally deleted the wrong account, :oops:  I know that was dumb because it even asks you to confirm.  Sometimes my fingers go faster than my brain does.  So I put all the settings back in, and then remembered I had just rsync'ed to my external hdd, so I shut down Thunderbird and just restored that directory.  Then I reopened TB, and went to delete the other account.  Deleted fine, but now any time I want to try and change any settings in any account in TB, and I hit OK, at the bottom it does NOTHING!  The window doesn't even close unless I hit cancel or the X.  Does anyone have any ideas as to what this could be?  or how to fix it?  Thanks.

Shane

PS, I'm using the TB installed from the scripts here, and haven't had any problems.  This one seems to be one of my own making.

hmm... well, that seems like a hard problem to figure out... did you happen to install any extensions in between? all i can think of to suggest is to try restoring your rsync backup again (before you deleted that other account)? or maybe also to remove and then install thunderbird (in case some file in the application directory got messed up)...

---

### Post by shane2peru on 2007-05-30
> **nanotube said:**
> hmm... well, that seems like a hard problem to figure out... did you happen to install any extensions in between? all i can think of to suggest is to try restoring your rsync backup again (before you deleted that other account)? or maybe also to remove and then install thunderbird (in case some file in the application directory got messed up)...

No, I didn't install or change any of the extensions in between this my restore.  It seems that the actual program files are fine, rather somehow just my profile is messed up or something.
Ok, this is really getting annoying.  I uninstalled and re-installed the program (via the scripts)  Then I backed up the new installation .thunderbird directory to a separate location and copied mine over to that location.  Opened up TB, and it :( didn't work correctly same problem.  So I copied the new installation back over it and opened it up and the account setting thing worked fine.  So then I copied just the .thunderbird/nko298a9asd/ part of the folder over and it :( didn't work.  I don't want to loose everything, and I certainly don't want to try and import all of that stuff again any ideas?  Thanks.

Shane
**Edit**  Just a thought could this be a permissions problem after my rsync?  I assume that rsync is supposed to preserve permissions, but perhaps that is the problem.

---

### Post by nanotube on 2007-05-30
> **shane2peru said:**
> No, I didn't install or change any of the extensions in between this my restore.  It seems that the actual program files are fine, rather somehow just my profile is messed up or something.
Ok, this is really getting annoying.  I uninstalled and re-installed the program (via the scripts)  Then I backed up the new installation .thunderbird directory to a separate location and copied mine over to that location.  Opened up TB, and it :( didn't work correctly same problem.  So I copied the new installation back over it and opened it up and the account setting thing worked fine.  So then I copied just the .thunderbird/nko298a9asd/ part of the folder over and it :( didn't work.  I don't want to loose everything, and I certainly don't want to try and import all of that stuff again any ideas?  Thanks.

Shane
**Edit**  Just a thought could this be a permissions problem after my rsync?  I assume that rsync is supposed to preserve permissions, but perhaps that is the problem.

well, it /could/ be permissions - go in and see if everything is owned by your user:group, and if everything in there has at least a u+rw permissions. 

or you could just do the following
```
chown -R youruser:yourgroup ~/.thunderbird
chmod -R u+rw ~/.thunderbird
```
that would make sure of correct permissions...

if that doesn't work, then just start with a fresh profile, create your accounts, and then just copy over the mail folders into the proper locations.

---

### Post by shane2peru on 2007-05-30
> **nanotube said:**
> well, it /could/ be permissions - go in and see if everything is owned by your user:group, and if everything in there has at least a u+rw permissions. 

or you could just do the following
```
chown -R youruser:yourgroup ~/.thunderbird
chmod -R u+rw ~/.thunderbird
```
that would make sure of correct permissions...

if that doesn't work, then just start with a fresh profile, create your accounts, and then just copy over the mail folders into the proper locations.

let me try that, I was thinking of starting a new profile, but am not sure of how to do that.

Shane

**Edit:**  No go with the chmod and chown thing.  Didn't help matters.  I think I will just restore the fresh install thing, and then just move my mail and address book and calendar.  How do I do that without getting everything?  Thanks.

---

### Post by shane2peru on 2007-05-30
> **shane2peru said:**
> let me try that, I was thinking of starting a new profile, but am not sure of how to do that.

Shane

**Edit:**  No go with the chmod and chown thing.  Didn't help matters.  I think I will just restore the fresh install thing, and then just move my mail and address book and calendar.  How do I do that without getting everything?  Thanks.

Ok, got this figured out.  I restored my rsync version, and it worked.  So then I deleted one account, and it still worked.  For some reason when I delete the imap account that I left in there, it makes the edit account's thing quit working.  I don't know why, or what I can do to fix this.  So I left it for now.  I don't have time to mess with it.  I will have to export my address book, and re-import it into a new account as it seems as that is all I loose.  I would like to be rid of that account as it keeps trying to check it and can't find the server since I changed the server name to make it incorrect.  Any suggestions are welcomed.  Thanks nanotube for the help!

Shane

---

### Post by nanotube on 2007-05-30
> **shane2peru said:**
> Ok, got this figured out.  I restored my rsync version, and it worked.  So then I deleted one account, and it still worked.  For some reason when I delete the imap account that I left in there, it makes the edit account's thing quit working.  I don't know why, or what I can do to fix this.  So I left it for now.  I don't have time to mess with it.  I will have to export my address book, and re-import it into a new account as it seems as that is all I loose.  I would like to be rid of that account as it keeps trying to check it and can't find the server since I changed the server name to make it incorrect.  Any suggestions are welcomed.  Thanks nanotube for the help!

Shane

well, you could at least stop the account from checking for new mail (it's under account settings -> server settings). so it would remain there, but won't bother you about a bad server. :)

---

