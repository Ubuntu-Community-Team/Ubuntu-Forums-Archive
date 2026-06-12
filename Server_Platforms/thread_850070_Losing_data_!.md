---
title: "Losing data !"
date: 2008-07-05
forum: Server Platforms
---

### Post by gilbertr on 2008-07-05
I am hoping someone can point me in the right direction....

I have a setup with a 6.06 LTS server, and Samba.
Clients are WinXP.

The problem we are encountering is that regularly (although not always), when we are using our standard applications on the clients and working on updating our data files, the data files will DISAPPEAR.

The sequence of events to which I have narrowed this down is :

- Application is being used to modify data.
- User selects to save updated file
- Original file on server is removed
- Error appears to say the file already exists
- New file is not written

The last 3 steps are the overwrite process but this is where it goes wrong, although the original file is no longer there, the application receives a message to say that the original file still exists.

The result is ofcourse that neither the original nor the new file exist anymore.
Trust me, this is annoying to say the least...

IS this a Samba configuration gone wrong ?

Please help.

---

### Post by prshah on 2008-07-05
> **gilbertr said:**
> 
The sequence of events:

- Application is being used to modify data.
- User selects to save updated file
- Original file on server is removed
- Error appears to say the file already exists
- New file is not written

The last 3 steps are the overwrite process but this is where it goes 


Is this overwriting done manually? Eg, do you have a script that deletes the old file, then saves the new file? Or do you just save the new file over the old, and answer "yes" when asked to overwrite?

---

### Post by gilbertr on 2008-08-01
Sorry - lost track of this issue.

To answer your question, this is new over old and "yes" is answered to the question whether you want to overwrite.

---

