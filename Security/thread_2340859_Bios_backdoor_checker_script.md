---
title: "Bios backdoor checker script"
date: 2016-10-22
forum: Security
---

### Post by hotuki on 2016-10-22
Hello everyone,

I would like to write a little script to check any bios modification (such as backdoored bios). I don't want to add a password (as it is already done :P ) and as I do not trust password as being totally safe, I would like to try an automatic script, maybe written on a persistent Ubuntu USB drive, that extracts/copy the BIOS rom, hashes it (SHA-256) and compares this signature with the originally installed one.

I thought using something like flashrom to automatically backup BIOS and SHA256SUMS to hash and compare it with its default value. 

Would you think this is something that could work ? Thanks in advance !

---

