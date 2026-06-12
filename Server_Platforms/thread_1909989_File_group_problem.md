---
title: "File group problem"
date: 2012-01-16
forum: Server Platforms
---

### Post by Jay89 on 2012-01-16
Hello,
  We are currently running a ubuntu 8 (I think) server. Every now and then we get a problem where a file that someone creates ends up with the wrong group parameter. When this happens other users who should be able to access it cannot. Somehow the server changes the file group to "Domain Users". We checked and the person creating the file is in the correct group with the correct settings. This only happens randomly so it's hard to predict. 

Is there a way to automatically force the group of every file in the directory to change to the correct one? Only the file not the user. We can't run a script because this has to happen dynamically regardless of the time of day whenever someone creates a file.

We tried "force group" but that gave everyone rwx permissions which we do NOT want.

Any suggestions?

Thanks

---

