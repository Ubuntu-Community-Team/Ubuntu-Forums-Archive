---
title: "Seahorse won't generate PGP key"
date: 2009-01-12
forum: Security
---

### Post by thomasyen on 2009-01-12
I've been trying to create a new personal PGP key using Seahorse, but whenever I reach the stage where the passphrase is typed and retyped, the textbox where I retype the passphrase remains empty - it just remains blank, without placeholders, no matter how many words I type. How do I fix this?
    Also, when I checked the homepage of Seahorse, it says that the latest release is 2.24.0, instead of the 2.24.1 in the official repository. What's this about?

---

### Post by kevdog on 2009-01-12
First of all I think you want to generate a GPG key rather than PGP key, and why don't you just use the command line to generate your keypair?

gpg --gen-key --enable-dsa2

Then pick the appropriate options for you!!

---

### Post by thomasyen on 2009-01-14
Thanks for the post! But I was wondering if you could tell me a bit more about why the current version is 2.24.1 instead of 2.24.0, and why Seahorse failed. Is it a bug?

---

