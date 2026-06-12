---
title: "Bug in Citadel-server on Ubuntu Server Edition 12.04 LTS"
date: 2013-07-13
forum: Server Platforms
---

### Post by cdysthe on 2013-07-13
Hi,

We are migrating to Ubuntu Server Edition from CentOS. We use the Citadel mail/groupware server a lot but there's a bug in Citadel resulting in the delete button in web mail not to work. The bug is described here:

[http://bit.ly/13d141b](http://bit.ly/13d141b)

Is there a way to fix this without upgrading either Ubuntu Server or Citadel Server, and what would it take to run a newer version of Citadel Server on 12.04 to fix this problem?

---

### Post by cariboo on 2013-07-13
I found this on the Citadel.org website:

> Why doesn't deleting messages free up disk space?

Actually, it does &#8230; eventually.

There are two reasons why you do not see an immediate reduction of disk utilization when you delete messages from a Citadel system.

The first reason is that deletion of messages is one of a number of operations which the Citadel server defers for later processing in order to keep interactive performance running smoothly and quickly. The messages you delete will appear to be gone, but they are actually still in the database. When the nightly auto-purger job runs, those messages will finally be deleted. (For a more technical discussion, read this article on How [deferred processing ]("http://www.citadel.org/doku.php/documentation:developers:deferred_processing")works in Citadel).

The other reason is that Berkeley DB, the underlying data store used in the Citadel server, never shrinks the size of its data files. When messages or other data are removed from the store, that space is made available for other data. As a result, your Citadel data files will stop growing for a while, even if you continue storing more data in them.

Is this the type of behaviour you are seeing, or are the messages never deleted?

---

### Post by cdysthe on 2013-07-13
> **cariboo907 said:**
> I found this on the Citadel.org website:



Is this the type of behaviour you are seeing, or are the messages never deleted?

Messages are never deleted when using the "Delete" button in the toolbar, but you can delete them with the delete button that shows up inline when you open an e-mail. It's described in the bug report I posted a link to. I get a lot of questions from users claiming not to be able to delete mail anymore and i have to tell them to use the inline delete button instead of the one on top in the toolbar. The problem with that is that you have to open an email to be able to delete it. If there's a way to fix in Citadel it would be great. The other option is to try and install a newer version of Citadel in 12.04.

---

