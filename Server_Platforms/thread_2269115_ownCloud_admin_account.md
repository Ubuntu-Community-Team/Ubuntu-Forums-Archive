---
title: "ownCloud admin account"
date: 2015-03-13
forum: Server Platforms
---

### Post by nerdtron on 2015-03-13
Hi All,

Anybody used owncloud here? I have already installed owncloud 8 and it is working as expected. I was able to create the initial admin account and a few users.
My question is there a way for the admin account to view/delete files of the normal users? It's for a small group and I need the admin account some kind of power that can view and delete files of normal users.

Any inputs can be appreciated.

---

### Post by mastablasta on 2015-03-16
I believe so. why not? did you get any issues?

anyway if you have root to server you can do whatever you want on it. :P

I find owncloud less and less useful for my needs :-k

---

### Post by nerdtron on 2015-03-17
> I believe so. why not? did you get any issues?
issue on owncloud? none
on owncloud admin account? none
on viewing/editing and deleting other users files? yes. I don't where to start since by default owncloud won't let you see the other people files. Even the admin account can't see other user files.

> anyway if you have root to server you can do whatever you want on it. :P
Yes i can be root but how can I give the admin an easy way to access/view ALL files on the server? I mean, If I setup filezilla to login as root, that is not a very good intuitive interface (and it is meant for downloading/uploading files). I'm looking for other user friendly access.

> I find owncloud less and less useful for my needs :-k

I'm looking for a way to give users remote storage needs, and the admin person to manage the user creation. First I'd tried samba, but adding/deleting users and shares on a  regular basis would become a chore (not to mention complicated) so I choose OwnCloud. If you have any other suggestions, I'm listening.

Thanks!

---

### Post by mastablasta on 2015-03-20
sea file is another alternative, but it has "80 easy steps to install" :)

anyway I wanted to check this but my modem died yesterday. so maybe I will check it today if I have the time. the new replacement I have has some stuff done in a strange way. among others I can not seem to be able to forward the 80 port.

---

### Post by nerdtron on 2015-03-20
Hmm.. I already think of a solution.

I made the data folder of owncloud as a samba share for the root account. Then the admin person can just view the share from his windows box and look/edit/delete files from other owncloud users.

It's not a pretty solution and security is an issue, but then again just a small company and small user group so I guess I'll settle with it until I find a better solution.

---

