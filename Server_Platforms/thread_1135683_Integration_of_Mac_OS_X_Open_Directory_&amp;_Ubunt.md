---
title: "Integration of Mac OS X Open Directory &amp; Ubuntu Server"
date: 2009-04-24
forum: Server Platforms
---

### Post by jffryhn on 2009-04-24
We have a Mac OS X Server infrastructure, with Open Directory served by one of the Mac OS X hosts.  Recently, we added an Ubuntu 8.04 host to serve NFS (primarily due to the poor performance of Mac OS X server's NFS implementation in a high i/o environment). This works very well. 

What we want to do now is to move the user's home directories (currently on a Mac OS X host), working under the existing Mac OS X open directory master, onto the Ubuntu server. For a variety of reasons, the open directory master needs to remain on the Mac OS X host.

Has anyone done this? I'd appreciate any help and/or links to resources or threads where this may have already been discussed.

Thank you.

---

### Post by nroussi on 2009-10-02
I have the exact same issue. I created a directory on the xserve under / and named it ldaphomes. Through the NFS share GUI of the xserve, I created a static mount and I can see all the directories only if I search for ldaphomes through spotlight, but they are there. Then I exported all users from my Ubuntu LDAP server, used passenger to convert the file to Open DIrectory format and it seems to be working ok.

The problem that I have now is that when a user tries to log in to an ubuntu client I get the following error:
> cannot set your user group

When the same user logs in to the xserve everything works perfectly.

Any ideas?

Thanks


--edit--
jffryhn: Check this out: [AppleDocs]("http://docs.info.apple.com/article.html?path=ServerAdmin/10.5/en/c9xg14.html")

---

