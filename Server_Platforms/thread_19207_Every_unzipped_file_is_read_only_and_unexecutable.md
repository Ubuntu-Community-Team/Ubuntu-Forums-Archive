---
title: "Every unzipped file is read only and unexecutable"
date: 2005-03-10
forum: Server Platforms
---

### Post by Benf on 2005-03-10
I'm trying to run a counter-strike server using the latest steam linux dedicated server distribution.  My problem is that everything I unzip or new directory that is created is created as read and execute only for the group and no permissions at all for Others.

Is there a way to stop this from happening?  Or even to change all the file permissions at once?  Since I'm not "the owner" of the files (root is), I can only change them using sudo in the console.

I've also been reading around trying to figure out how to get root access to everything in order to change those file permission in the gui, but all I can come up with is sudo -s and sudo passwd root.  What do I do once I do these things in order to have root access?

Thanks,
Ben

---

