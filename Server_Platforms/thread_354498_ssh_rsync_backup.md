---
title: "ssh rsync backup"
date: 2007-02-06
forum: Server Platforms
---

### Post by noppeli on 2007-02-06
i have problem is following

how can i make access to user. i want user can only access home folder and
copy files other server use rsync and ssh with certificate.

now i have user use rbash, but this is not enough

---

### Post by tribaal on 2007-02-06
I'm not sure I understand your question.

The easiest way to have a script accessing a user's account by ssh is to put his paste his public key into the *target machine's* ~/ssh/authorized_keys2 file.
This way ssh shouldn't ask for a password if the account's provate ssh key matches the public key stored in that file.

Note that your ssh shell will have exactly the same rights that the target machine's user.

Hope I make sense. :)

- trib'

---

### Post by noppeli on 2007-02-06
sorry i write bad english,
i did make ssh-keygen pub and private key file.
putting to ~/.ssh/authorized_keys file. but i want that only rights user have is use
rsync. thatis: rsync -"some options" -e ssh -i id_rsa /tmp/* user@192.168.1.2:folder

---

### Post by conjur3r on 2007-02-08
What you want is chrooted environment.  Plenty of [google]("http://www.google.com.au/search?num=100&hl=en&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aofficial&hs=QdS&q=linux+ssh+chroot&btnG=Search&meta=") articles.

---

