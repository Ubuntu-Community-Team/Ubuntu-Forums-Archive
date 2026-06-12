---
title: "Add users to media server"
date: 2010-04-29
forum: Server Platforms
---

### Post by jay3712 on 2010-04-29
I have a home server that has two shares: media and data. I currently just have one user (mine - 'jason') that the other people who access the shares also use. I think that someone has been accidentally (or not) deleting files. I now need to add a new user to restrict what the other people can access & make changes to. Specifically, 'jason' still needs to be able to have full read-write privileges and the new user 'guest' that will be used by all the other people and can only read existing files and add new files to the shares but cannot delete or change any of the existing files.

I know how to add users with the adduser command but I guess I need more direction on how to set the permissions correctly.

Thanks!

---

### Post by krodrigue on 2010-05-01
Try

adduser <username>

---

