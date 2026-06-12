---
title: "I still receive some updates after system EOL"
date: 2023-06-14
forum: Security
---

### Post by timomak on 2023-06-14
[FONT=arial][SIZE=2] Hi all,             
[/SIZE][/FONT]
[FONT=arial][SIZE=2]On my Iaptop i run Xubuntu 18.4, which stopped receive ubuntu security updates on 31/5/23.             
[/SIZE][/FONT]
[FONT=arial][SIZE=2] A week ago i switch to ubuntu pro security, to secure the system.
Thus i' m able to upgrade or make a fresh install of a newer release whenever  have i available time.             [/SIZE][/FONT]

[FONT=arial][SIZE=2]However i noticed that the software and updates program still shows new available updates, such as ubuntu base or ffmpg(something with video and media) if i remember correctly.             [/SIZE][/FONT]
[FONT=arial][SIZE=2]Also no root/admin password in asked.             [/SIZE][/FONT]
[FONT=arial][SIZE=2] Is all that normal or something goes wrong ?

Thankful for any advice
             [/SIZE][/FONT]

---

### Post by deadflowr on 2023-06-14
> However i noticed that the software and updates program still shows new available updates, such as ubuntu base or ffmpg(something with video and media) if i remember correctly.
Also no root/admin password in asked.
Is all that normal or something goes wrong ?
Normal.
Software Updater will only ask for a password when the updates need to install new software,
Updates for existing software on the system will not need to be authenticated.

This only works this way because your logged in user is an admin.
If you logged in as a non-admin user it should require an admin user/password to install the updates.
Or at least that is how it is suppose to work.

---

### Post by timomak on 2023-06-16
It' s clear, thank you very much.:smile:

---

### Post by guiverc on 2023-06-16
Are you using a *supported* architecture for Ubuntu Pro?

Ubuntu 18.04 LTS was available for many more architectures than are *supported* with Ubuntu pro.

> Ubuntu 18.04 LTS will remain fully supported until April 2028 with an Ubuntu Pro subscription. Ubuntu Pro is available for *amd64, arm64, s390X*, and *PowerPC* architectures.

If you're using one of the *unsupported* architectures then no upgraded packages can be downloaded to your box (*alas they'll still show* *from what I've seen*), and you're wasting (*as I understand it*) your Ubuntu Pro subscription on an *unsupported* box.

---

### Post by timomak on 2023-06-21
It' s amd64, Dell Latitude D630. I believe is supported.

---

