---
title: "folder modified &amp; created time stamps"
date: 2007-11-10
forum: Server Platforms
---

### Post by foolmeonce on 2007-11-10
I hope this is the right place for this question.  I did read the faq and docs, and searched the net, but did not find anything that helped.

I am rather new to ubuntu, but have successfully installed 6.0.6 from the server iso, along with Samba configured with Swat.

My new server runs just fine, but I have noticed that the shared folders I use to map drives from my windows clients, the folder (and all parent folders) date modified and date created time/date stamp is updated each time a file within that folder is accessed, even if the file is not modified.

As an example:

//DellUbuntu/shared1/drive-g

is mapped on a windows machine as G:

and I have files in 

g:\clients\abcco\2006\

each time I access a file in the 2006 folder, then the date modified and date created date/time stamps are updated on each of the 3 folders - clients, abcco and 2006.

The Netware server I am going to replace does not update either the created date or the modified date.  The Windows XP NTFS shares on the same network update the modified date, but not the created date.

Is there a way to modify this behaviour?

Thanks for any suggestions.

Mike

---

