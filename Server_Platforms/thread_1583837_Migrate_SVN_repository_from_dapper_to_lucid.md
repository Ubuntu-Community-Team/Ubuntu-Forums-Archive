---
title: "Migrate SVN repository from dapper to lucid"
date: 2010-09-28
forum: Server Platforms
---

### Post by HandleWithCare on 2010-09-28
Hey everyone,

I've been pulling my hair out on this for several hours now so I really hope you can help. I have a (very old) svn repositoy on an ubunta dapper machine. I want to switch to another machine with lucid running. I simply want to "copy" the whole repository to the new machine. I've tried several ways, but the most succesful one was to do a dump on the old machine, copy the file to the new machine and do a load there. The repository has about 28.000 revisions. At revision 3130 it stopped with an error saying some path was not in UTF-8. I tried running a UTF-8 migrationtool on the dapper machine but this told me all files were UTF-8 compatible already. I am really stuck, even a two and a half hour google session didn't provide any answer.

edit: more specific, the error I get is:
> svnadmin: Path 'beginofpath?\218tabase' is not in UTF-8 
The end should have been /database instead of ?\218tabase. When I look in the revision on the dapper machine this path shows a square at that location, so this is wrong also.
When I try to open the dumpdile in gedit I get an errormessage saying:
> Could not open the file /home/usrname/repo.svndump using the Unicode (UTF-8 ) character encoding
When I change the encoding I get the same error for that encoding.

---

### Post by HandleWithCare on 2010-09-29
In reply to myself (since no one else does ;)), here's an update.
I have managed to move around this problem by doing partial dumps an loads. By doing this I was able to single out the revisions that caused the trouble. Luckily, the two revision that were causing all the hassle contained no binary data so I was able to edit those revisions in a text editor. There were some unrecognized characters, must have gone wrong during commit at that time (probably about 5 years ago). After that fix the revisions would load and after two hours of dumping and loading (ok, this starts to sound weird), all was good and we have a new svn server wich is extremely fast compared to the old one.
I will not mark this thread as solved since the actual problem hasn't been fixed, I merely worked around it. Good ideas on how to prevent this in the future are still welcome.

---

