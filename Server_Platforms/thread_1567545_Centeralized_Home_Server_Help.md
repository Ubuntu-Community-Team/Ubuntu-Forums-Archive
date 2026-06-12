---
title: "Centeralized Home Server Help?"
date: 2010-09-03
forum: Server Platforms
---

### Post by 480silverton on 2010-09-03
Hey people. Let me give a small basic background of what I currently have.

I have a personal home server that I use as a central place where I have NFS exporting /home to the client computers so that I have the same thing across my linux computers around the house and on top of that I have NIS going to share the user name and passwords across the linux computers.

Here is where I may want to get a little more complicated. I have a few windows computers around and I was wondering if there was a way to share the user name and passwords off of the personal home server to the windows computers, and have a network drive mounted on the windows for the specific account so that even on the windows, all the files from Linux are still there.

I hope that this wasn't too confusing.

I have read some small stuff on Active Directory, Samba, Kerebros and some other stuff. It was all a bit confusing to me as none really explained if I could do what I just stated above.

Could any one give me a clear answer on if this is possible and where I may find the procedures to do this?

---

### Post by drdos2006 on 2010-09-04
Hi there. For Windows to access a partition, folder then you need NTFS on that partition, folder.

Here is a HOWTO which I found comprehensive and invaluable.
> 
Are you using the most current version of this how-to?
Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab
Setting up a Linux Server, Start to Finish, using Webmin. By Kevin Elwood


> 
[http://ubuntuforums.org/showthread.php?t=249889&highlight=howto+nfs](http://ubuntuforums.org/showthread.php?t=249889&highlight=howto+nfs)
HOWTO: NFS Server/Client 



regards

---

