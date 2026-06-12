---
title: "enigmail not accepting typed password"
date: 2008-12-25
forum: Security
---

### Post by tonybaloney867 on 2008-12-25
I'm fairly new to Enigmail, gpg, etc and would like to figure out a problem I'm having. When I'm generating a key using the Enigmail interface, it asks for a password (without which, I assume, gpg will refuse to use the private key). The password is accepted with asterisks. However, after the key was generated, it asks for the password in a separate dialog box to generate a revocation certificate. In that dialog box, no asterisks will show. However, thinking it's like a login on a text console where it doesn't show asterisks, I type the password. The password comes up as invalid. It has done this for the past five times so I assume I'm not typing in the password incorrectly. I even tried a simple one as an experiment to test for this. I suspect something may be up with how the dialog box is collecting input. Has anyone experienced this before and, if so, is there a solution to get that dialog box to accept input?

EDIT:
Invoking gpg --gen-key from the terminal seems to work fine and asks for a password on the command line.
Invoking gpg2 --gen-key from the terminal pops the same dialog box up outside the terminal window after going through the questions and it won't accept input there.

---

