---
title: "about the new recovery key"
date: 2021-08-18
forum: Ubuntu, Linux and OS Chat
---

### Post by Sandgoose on 2021-08-18
during setup on the latest ubuntu users wanting to use LUKS are **forced **to setup a recovery key.

this key is not editable by the user but is a 16 numerical character long ! Is there any reason why it does not included upper and lower case alpha or even special characters since the keys support using them?

Also is there a reason why this secondary "recovery" key isn't an optional step?

---

### Post by TheFu on 2021-08-18
What is "latest ubuntu" in your mind?
I haven't seen this on either 20.04 or 21.04 encrypted systems.

Update: Perhaps it was presented in the install and I simply ignored it in 21.04?  My 21.04 setup for only for play purposes.

---

### Post by deadflowr on 2021-08-18
There was a discussion on this here: [https://discourse.ubuntu.com/t/ubuntu-21-04-encryption-recovery-key/21685]("https://discourse.ubuntu.com/t/ubuntu-21-04-encryption-recovery-key/21685")
We'll see how the proposed changes for 21.10 turn out.

---

### Post by Sandgoose on 2021-08-19
Don't really want to bump that other thread tthough It was an interesting read, also feel this feature isn't very well thought out for a few reasons.

anyway I recommend anyone just do the following

sudo cryptsetup -v luksKillSlot /dev/driveid keynumber

on a fresh install the recovery keynumber being 1 and then googling how to add a better secondary key if need/wanted

---

