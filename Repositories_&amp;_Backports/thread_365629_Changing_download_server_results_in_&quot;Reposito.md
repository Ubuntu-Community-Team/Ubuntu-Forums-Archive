---
title: "Changing download server results in &quot;Repositories Changed&quot;"
date: 2007-02-19
forum: Repositories &amp; Backports
---

### Post by dryder on 2007-02-19
Hi,

A package I wanted wasn't in any of my (all of the) repositories.

So I changed the download server from Server for Australia to Main Server.

But it then told me:
> Repositories changed

The repository information has changed. You have to click on the "Reload" button for your changes to take effect

May I ask why? Isn't the repository just a database of packages that can be installed using synaptic manager, in which case why create a new one?

Many thanks - I appreciate the patience of all who help us newcomers to Linux.

David

---

### Post by lhtown on 2007-02-19
It won't actually download a new list from the repository unless it is different than the local copy, it will just check with the new server to make sure that the list of programs Ubuntu (apt-get) has is the same as the repository server.

It is entirely possible that they will be exactly the same.

It is possible that a different server might have a different version of the same program for a short time as it is being updated. However, there is no point in changing Ubuntu repositories hoping to find a package on one Ubuntu server that wasn't on another one. If it were to happen, it would be an error as I understand it.

---

### Post by dryder on 2007-02-19
Many thanks - now I understand ...

---

