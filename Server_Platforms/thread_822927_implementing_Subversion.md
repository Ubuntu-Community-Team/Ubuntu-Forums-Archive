---
title: "implementing Subversion"
date: 2008-06-08
forum: Server Platforms
---

### Post by fhqwhgad on 2008-06-08
I have recently installed subversion on my server.
It is a Mud server, so there will be several people working on C code. I have read a few how-to's but i'm not entirely sure i have it setup yet.
I have imported a directory in the rep, but does it move those files in my filestructure, or does it keep them where they are added?
What i want is to keep the filestructure i have created, when the files are added to the rep.

---

### Post by indigoparadox on 2008-06-08
I'm not sure I fully understand your question, but the way Subversion works is roughly this:

You can start by "importing" a local directory you want to track into your repository using your Subversion client. Once you've done this, you can then delete the *local* directory you've imported (or move it someplace temporarily if you're not quite sure you're doing it right yet) and "check out" a copy from the repository to wherever you want to keep your local working copy (again, using your Subversion client).

This checked-out copy will have the files you imported as well as meta-data regarding those files (the meta-data is stored in subdirectories called ".svn", so don't delete these!). You can then modify your files in this checked-out directory and, when you're ready, "commit" them back to the repository using your Subversion client.

If you want a slightly friendlier interface than the standard svn command, I recommend RapidSVN.

As an after-note, you can only access files from the repository by checking them out or exporting them. The repository directory on the server uses a specialized database format that only Subversion (or other tools designed for this purpose) can read.

I hope this was at least a *little* helpful...

---

### Post by fhqwhgad on 2008-06-09
Thank you, it was infact quite helpful. If i do a svn checkout, it does give me the updated files.
However, this is my setup and how i would like it to work:
I have a server where all this code (and svn) is located. The code needs to be compiled and executed on this same server.
People will need to checkout the code remotely to update it. Once they commit, i would like the server's code to be updated, so we can make and run the new changes.
Would i have to make a svn checkout on the server to get these updates, everytime, or could i somehow make it write the updates in the /home/mud/src dir directly, when someone commits?

---

