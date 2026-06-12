---
title: "[SOLVED] GPG does not work anymore"
date: 2008-09-07
forum: Security
---

### Post by ELMIT on 2008-09-07
I got a strange problem.

I had installed in Thunderbird OpenGPG and in February created a key pair. I have sent at that day a test message, so I know it worked at that day.

Today I tried to register at launchpad, which requires gpg again. The passphrase does not work. So I thought I forgot the passphrase and created a new pair of keys. Uploaded it to the keyserver and tried again. 
The received encrypted message I cannot open, again it says password phrase is wrong. This time I had typed the passphrase into a text file and just copied it, so I am very sure it is correct.

I installed then enigmail in Thunderbird (not sure if that is anyway different from OpenGPG), no success.

I installed then gpa and saved the encrypted message into a file. I tried to decrypt the file and again the password phrase is wrong.

What could be the problem?

bye

R.

---

### Post by ELMIT on 2008-09-07
Got it eventually working;

Edit ~/.gnupg/gpg.conf 

added the line:
default-key 12345678


otherwise it uses still the old key !!!!!

bye

R.

---

