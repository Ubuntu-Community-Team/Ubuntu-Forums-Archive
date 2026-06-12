---
title: "Wireshark - won't allow me to upload key file to decrypt SSL"
date: 2014-07-02
forum: Security
---

### Post by Bobby_James on 2014-07-02
I have a curious issue with Wireshark.

I want to decrypt SSL traffic from a .cap file with a key file.

I go to Preferences / Protocols / SSL / RSA keys list / New. Now, from images I've seen, the 'Key File' box should allow me to select the file from my hard drive.  As you can see from the screenshot attached, it's just a static box.  

How can I get round this wierdness?

---

### Post by bapoumba on 2014-07-02
Open after Staff review.

---

### Post by untrustytahr on 2014-07-03
That is strange.  I quickly setup a vm to check it out and it worked fine (with ability to select from dialog menu).
 

 If it allows you, I would just enter the full path to the key.  If it doesn't I would check the logs to see if there were any errors encountered.  If the logs have no errors, I would try to re-install Wireshark and if it still persisted, log a bug with Wireshark & Ubuntu.

 

 Sorry I couldn't be more helpful.

---

