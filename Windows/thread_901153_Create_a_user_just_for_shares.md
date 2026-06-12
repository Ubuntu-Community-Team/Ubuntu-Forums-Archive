---
title: "Create a user just for shares?"
date: 2008-08-26
forum: Windows
---

### Post by Metallion on 2008-08-26
Hello

I'm trying to share some files with my collegues at work. When they want to access shared files on my comp it asks for a user and password. This is the part that I like. Don't want everybody accessing my files now do I? :)

The part that I don't like is that the only way I have found to create a username for this is by creating a limited user account for windows as a whole. This doesn't feel very secure to me. Sure it's limited but everyone being able to login to my computer, browse everything and change most is not something I'm very comfortable with.

I know we Linux users love to bash MS for it's insecurity but there must be a way to make an account that has only access to the files I'm sharing on the network isn't there? ..... Isn't there? [-o<

Anyone can help?

---

### Post by Calash on 2008-08-28
You can do that, but not using the "User Accounts" program in control panel.  You will want to go into the computer management page (Right Click on My Computer, Select Manage), then click on the "Local Users and Groups" followed by groups.  You can add a user here, then limit there groups.  In practice you can remove them from all the groups, then assign individual permissions to the share in question.  The account can still be used to login, but without the Users group it will not be doing much..similar to Linux.

---

