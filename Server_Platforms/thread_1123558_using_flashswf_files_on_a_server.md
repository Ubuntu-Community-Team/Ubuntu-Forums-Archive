---
title: "using flash/swf files on a server"
date: 2009-04-12
forum: Server Platforms
---

### Post by mjfroggy on 2009-04-12
Hello all,

 This may sound strange but is their anything special that needs to be installed on a ubuntu LAMP stack inorder to get flash/swf files to work?? I ask because locally I can get a swf file to work in my browser but then when I put it up on my in house server the browser says downloading and it never loads?

 So just want to make sure its not an issue with a missing module on the server itself

thanks

---

### Post by cariboo on 2009-04-12
Check the permissions on the files, as that maybe why the can't be played. THe files should have a permission of 755, readable by everyone, writeable by the owner.

Jim

---

### Post by mjfroggy on 2009-04-12
Ahh ok that fixed it. 

 Thanks!

---

