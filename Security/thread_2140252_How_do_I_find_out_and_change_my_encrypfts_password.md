---
title: "How do I find out and change my encrypfts password?"
date: 2013-04-29
forum: Security
---

### Post by JessicaTsang on 2013-04-29
I used this to see if my home folder is encrypted:

[COLOR=#333333][FONT=Ubuntu Beta]> Check with ls -A /home. There should be a .ecryptfs folder, if you have encryption of your home folder.


And I find that my home folder is indeed encrypted. However, I don't remember the password for it at all. Strange.

But I can still access the home folder without any problems at all. I was wondering if there is a way to find out what my password is and how do I change the encryption password?
 

Does this work? 

[/FONT][/COLOR]
   **ecryptfs-rewrap-passphrase**

---

### Post by trundlenut on 2013-04-30
Did you choose "encrypt my home directory" (orwhatever it says exactly) when you installed ubuntu?

If so the the encryption is linked to your user password.  Do you have the Ubuntu set to logon automatically?

---

