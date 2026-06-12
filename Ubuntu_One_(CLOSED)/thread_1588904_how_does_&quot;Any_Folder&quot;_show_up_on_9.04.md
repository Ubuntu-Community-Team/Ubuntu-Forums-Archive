---
title: "how does &quot;Any Folder&quot; show up on 9.04"
date: 2010-10-05
forum: Ubuntu One (CLOSED)
---

### Post by crf112 on 2010-10-05
I have two 9.04 systems (my desktop machine and my wife's netbook) and sync my bash scripts using Ubuntu One.  I put the scripts in "$HOME/Ubuntu One/bin" and a symbolic link from "$HOME/bin" to "$HOME/Ubuntu One/bin".  This works fine for what I'm trying to accomplish.

I am planning to upgrade my desktop machine to 10.10 and I see that, starting with 10.04, I can now use U1 to sync "Any Folder".  Would those folders show up at all on the 9.04 system?  If so, where would they be?

---

### Post by duanedesign on 2010-10-06
Your older version of Ubuntu One will only recognize the root folder (~/Ubuntu One). You could always install a newer version from the ppa.

thank you,
duanedesign

---

### Post by crf112 on 2010-10-06
Thanks for the answer.  I was hoping the other folders would show up under "$HOME/Ubuntu One" on the older system.

I will probably continue with my present method of letting U1 own the folders that I want to share and then use symbolic links in the appropriate places.  Once I can convince my wife to let me upgrade her netbook, then I'll use the "Any Folder" method.

---

