---
title: "Procmail exitcode"
date: 2010-11-25
forum: Server Platforms
---

### Post by wasanzy on 2010-11-25
Hi All,

I have written a script that is being invoked from  procmail. Now I want procmail to wait untill the program finishes and  check it's exitcode.

My question is, how do I check the exit code of the script and take an action on it in procmail?

Regards

Emanuel

---

### Post by SeijiSensei on 2010-11-26
Just a guess, but I doubt that's possible.  Usually you're using a pipe to the script.  After the message has been passed along, I doubt procmail is paying attention any longer as it has fulfilled its task.

Stll "man procmail" is pretty extensive.  If you can accomplish what you want to do, the answer lies there somewhere (or maybe in "man procmailrc").

---

