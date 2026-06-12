---
title: "is  a  ubuntuone bug?"
date: 2010-07-06
forum: Ubuntu One (CLOSED)
---

### Post by luofeiyu on 2010-07-06
i have delete my "Ubuntu One" in  /home/pt  for some reasons.
i found i can't  remake it ,when i download my data,
pt@pt-laptop:~$  mkdir /home/pt/ubuntuone
pt@pt-laptop:~$   u1sync  --init  /home/pt/ubuntuone

Initializing directory...

Writing mirror metadata...

Done.
pt@pt-laptop:~$   u1sync  --action=download  /home/pt/ubuntuone

Reading mirror metadata...

Scanning directory...

Fetching metadata...
23ce33e9-584d-4373-9e04-4b0385895b77 DIR  /  sha1:da39a3ee5e6b4b0d3255bfef95601890afd80709

Merging trees...
23ce33e9-584d-4373-9e04-4b0385895b77 DIR  /  sha1:da39a3ee5e6b4b0d3255bfef95601890afd80709

Syncing content...

Updating mirror metadata...

Done.
pt@pt-laptop:~$ 
what's wrong?
is it a bug?
i can't get my file in [https://one.ubuntu.com/files/](https://one.ubuntu.com/files/) ?

---

### Post by duanedesign on 2010-07-06
You do not need to use u1sync. In fact it is recommended that you don't use it. It is available for testing purposes but not recommended for daily use. Simply recreating your Ubuntu One folder should be enough.

---

