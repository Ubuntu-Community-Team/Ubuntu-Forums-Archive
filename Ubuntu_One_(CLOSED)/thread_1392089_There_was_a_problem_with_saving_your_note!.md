---
title: "There was a problem with saving your note!"
date: 2010-01-27
forum: Ubuntu One (CLOSED)
---

### Post by MickSulley on 2010-01-27
Hi,

I have 2 machines both on Karmic and I have synchronised Tomboy Notes on  them, that seemed to work OK.
Now if I log on to the website and try to edit a note soon after I start typing I get a message - 

There was a problem with saving your note!

and none of the changes are saved.  Am I doing something wrong or is there a bug?

Cheers

Mick

---

### Post by JacekZ on 2010-01-27
I had the same problem when I tried the service over a week back, also the first sync went fine, but later changes to notes on either machine were not getting synchronised either reliably or more often - not at all.  I had over a hundred notes, so tried it with less.  Then I tried reinstalling u1, tomboy etc, all to no avail.  I gave u1 some feedback through their online form, but got no reply.

You might not want this by my solution for now is to port entire notebooks of tomboy notes into a single open office text doc using a nice notes template, use the outliner (f5) to navigate around.  To switch between notebook docs I created an index doc with links to the others, saved that as html and put it on my firefox bookmarks toolbar - set to show in left frame.  So my notes are just a click away.  Then I sync between machines with unison over ssh with keys set up.  This is more secure than u1 and still fairly granular, so one doc can be worked on one machine and another on the other at the same time.

---

### Post by MickSulley on 2010-01-27
Thanks for the feedback.  I was migrating to BasketNotes (seems to have better functionality) until I saw the sync options with Tomboy, which made me think again.  I guess I will give it a while to see if it becomes stable.

Thanks
Mick

---

### Post by duanedesign on 2010-01-28
currently editing the notes on the web UI can be problematic. The Ubuntu One team is working on a solution, if not already solved this. I expect it to be fixed soon.

If you are experiencing tomboy sync problems other than this i suggest the following.
   1. Quit Tomboy
   2. Applications->Accessories->Terminal, and run:
tomboy --debug > ~/tomboy_debug.log 
   3. Try to reproduce the bug and then attach ~/tomboy_debug.log to a bug report 

Note that attaching the Tomboy debug log will show information about what you are attempting to sync with Ubuntu One. If you do not want this to be public, please mark the bug as private and this bug report will only be available to you and the Ubuntu One team.

---

