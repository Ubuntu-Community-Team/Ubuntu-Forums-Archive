---
title: "CVS-like editor (like gedit)"
date: 2004-12-02
forum: The Cafe
---

### Post by ubuntu_demon on 2004-12-02
I was just reading :

Regarding High Level Computing

[http://www.osnews.com/story.php?news_id=9021&page=2](http://www.osnews.com/story.php?news_id=9021&page=2)

> 
Why do we have a save function in Word 2003? The same function existed 9 years ago in Word 6. Thousands of users have lost their documents during blackouts. Thousands more will lose their work in the future. Saving can be automatic. I am not talking about partial solutions (like Vi and Emacs do) which protect the user from losing work. I am talking about the whole idea of saving. Why torture the user with the save function at all? The application should save the document at all times keeping different versions and revisions. The whole .doc file should contain all user actions on the document (think CVS in a single file).Opening the file would be a simple question. Open the latest version or edit the version of a specific date/time. The Word application should not have a save menu/button anywhere on the interface. The user doesn't care about this. (Ok, ok maybe a "save as...” which just relocates the document file but you get the idea).


I think a CVS-like editor like gedit would be great.

---

### Post by airtonix on 2006-10-31
roxors!!!!! this would be sooo cool.

this would save the bollocks that many bring upon them selves with date based foldernames techniques for backup routines.

damn rar files.

---

### Post by mustang on 2006-10-31
This is a *very* interesting idea. I'd be up to beta test it.

---

### Post by Mr. Picklesworth on 2006-10-31
I agree :)
Automatic saving is a reason why I like TomBoy (wiki note-taker that's included with the default Edgy).

The reminder of how nice it is has actually inspired me just now!
I may stare at OpenOffice and see if I can figure out how to shove in such a feature, jsut as a proof of concept...

---

### Post by skymt on 2006-10-31
Scribes has automatic saving, but I don't think it has change tracking.

One potential problem with this idea is that if a program writes to disk whenever you make a change, it creates a lot of disk activity. The best way would be to follow the undo model and save whenever a group of edits is completed.

---

### Post by shining on 2006-10-31
why not do that for every files, instead of only the ones edited by a particular editor?
It would be so cool, but there is probably a performance and size problem. I think I would love to have a server with a huge disk array, and high speed network, and diskless clients. No backup troubles anymore.
Btw, I believe that's what plan9 does:
[http://plan9.bell-labs.com/magic/man2html/4/fossil](http://plan9.bell-labs.com/magic/man2html/4/fossil)

---

