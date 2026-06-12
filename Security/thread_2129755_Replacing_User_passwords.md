---
title: "Replacing User passwords"
date: 2013-03-27
forum: Security
---

### Post by cbillson on 2013-03-27
If i had two boxes, i added a user to one and set a password.

I then add the user to the second box using useradd.

How can i take the encrypted password from box 1 for input into box 2 - ideally something i can use in a shell script.

I've tried so far, searching and replacing, but the passwords contain "/$." etc, I've also tried fully replacing the shadow file and cat >> shadow, but this has mixed results usually ending with a blank shadow file.

I can use passwd "user" but this required the typing of the unencrypted password.

I've noticed some of the user creation commands have the ability to take an encrypted password, however i'm struggling with the syntax of this.

Ideally i'd like to be able to take the encrypted data from one box and have a command such as - "command" "user" "encrypted data"

Any thoughts on how i can achieve this?

Cheers
chris

---

