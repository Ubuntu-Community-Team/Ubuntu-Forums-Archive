---
title: "Encryption recovery problems: filenames messed up"
date: 2011-04-02
forum: Security
---

### Post by Dafydd on 2011-04-02
Hello, 
Have 'recovered' my encrypted home folder after a reinstall.

However, the filenames are all messed up (encrypted?). For instance:

ECRYPTFS_FNEK_ENCRYPTED.FWYrhxCEq1POfkTE54acIf4rqX4o0xG.51VatF-sINkUw5jVw2qY94VMiE--

Is there anything I can do?

Sorry, but I just did not think when reinstalling. I have my original login and encryption passphrase and followed the guidlines at:

[https://help.ubuntu.com/community/EncryptedPrivateDirectory#Recovering%20Your%20Data%20Manually](https://help.ubuntu.com/community/EncryptedPrivateDirectory#Recovering%20Your%20Data%20Manually)

But with the filenames all jumbled up, I am not much further.

Any help would be great!

Thanks

Dafydd

---

### Post by bodhi.zazen on 2011-04-03
You can try this :

[http://bodhizazen.net/Tutorials/Ecryptfs#Live](http://bodhizazen.net/Tutorials/Ecryptfs#Live)

---

### Post by Dafydd on 2011-04-03
Thanks for that suggestion.

I have actually solved my problem.

I restarted and then followed the instructions again at:

[https://help.ubuntu.com/community/EncryptedPrivateDirectory#Recovering%20Your%20Data%20Manually](https://help.ubuntu.com/community/EncryptedPrivateDirectory#Recovering%20Your%20Data%20Manually)

Perhaps what I did wrong the first time was not entering the second file key that is listed after "Inserted auth tok with sig".

Now copying files over. 

What I nightmare losing files is (even if it is temporary)!

Dafydd

---

### Post by bodhi.zazen on 2011-04-03
> **Dafydd said:**
> What I nightmare losing files is (even if it is temporary)!

Dafydd

Glad you got it working, yes there are several potential methods.

Yep, this is the disadvantage of encryption, it makes backup one step harder.

---

