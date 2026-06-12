---
title: "got some lvm questions..."
date: 2008-05-17
forum: Security
---

### Post by iamnotthemessiah on 2008-05-17
im considering using lvm in order to encrypt my drives. ive got some questions that i would be very happy if someone could answer

ive got 3 physical hdds and i guess i want them all to be part of a large lvm. as far as i can understand that is one thing lvm can do

but im wondering about these things:
-what happens if a physical hdd that is part of a lvm dies? will that disrupt the whole setup and data stored on other hdds be lost?

-what happens if i have sda as root, sdb storing movies and music and sdc storing other things, all these are in one lvm with the password 'ubuntu' (bad password but for simplicitys sake). and then i decide to do a clean install of ubuntu on sda. what happens then? i guess i have to make a new lvm? do i have to use the same passphrase? or will this new install let me enter my old passphrase to open sdb and sdc and then encrypt them using a new passphrase?

---

