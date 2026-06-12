---
title: "[SOLVED] Dynamic File linking in windows 200 Pro?"
date: 2008-02-13
forum: Windows
---

### Post by Warren Watts on 2008-02-13
Is there a way to set up a dynamic link in windows 2000 Professional?

Here is my dilemma:

I have Sims 2 installed on my W2KPro box.  
My wife and I each have seperate accounts on the computer.  

In order to use any custom content in Sims 2, the content must be stored within the user's "My Documents" directory.

In order for my wife and I each to have access to Sims 2 custom content, I have to replicate the custom content directory in BOTH accounts.

Any time I add any new content, I have to add it to BOTH directories.

I want to be able to add a dynamic link that "points" to the directory in the other account, so I don't have to duplicate my content and add each new item twice.

I tried enabling a file share and creating a shortcut to the other directory, but Sims 2 doesn't recognize the shortcut.

In a perfect (Linux) world, I would just create a dynamic link with the "ln" command and be done with it.  Any way to do this in W2KPro?

Apparently W2K Server has a service called "DFS - Distributed File Service" that enables this sort of thing, but I have scoured the net looking for an easy way to accomplish this with W2KPro.

Anyone have any suggestions or a solution?

---

### Post by Warren Watts on 2008-02-14
Problem solved!

I discovered that any windows version that uses NTFS 5.0 or above has a feature that allows for the creation of symbolic links.  
MS themselves don't document it or support it, but I found a program called [Link Magic]("http://www.rekenwonder.com/linkmagic.htm#Junction%20Link") that provides a nice GUI for creating and managing symbolic links in windows.  

I thought I would post the solution here just in case someone else down the line has need for a similar tool.

---

