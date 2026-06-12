---
title: "Question about home folder encryption"
date: 2010-10-06
forum: Security
---

### Post by zaphod777 on 2010-10-06
So when I installed Ubuntu 10.10 I encrypted my home directory. 

When I login the home folder is automatically decrypted but how secure is this really?

If you get physical access you can gain root access on any Linux box using a live CD. From that live CD you would be able to reset my user password. 

So in the case of someone stealing my laptop they could reset my user password login as me and basically have access to my home folder. 

Is there anyway to make this more secure?

---

### Post by Megaptera on 2010-10-06
Some options in this current thread may interest you ...

[http://ubuntuforums.org/showthread.php?t=1589192](http://ubuntuforums.org/showthread.php?t=1589192)

---

### Post by movieman on 2010-10-06
> **zaphod777 said:**
> So in the case of someone stealing my laptop they could reset my user password login as me and basically have access to my home folder.

Uh, the files are encrypted. Changing your password would allow them to log in, but they can't decrypt the files without your original password as that is (indirectly) used to encrypt the files.

---

### Post by zaphod777 on 2010-10-06
> **movieman said:**
> Uh, the files are encrypted. Changing your password would allow them to log in, but they can't decrypt the files without your original password as that is (indirectly) used to encrypt the files.

Thanks. I was worried that it was all tied together.

---

### Post by bodhi.zazen on 2010-10-06
> **movieman said:**
> Uh, the files are encrypted. Changing your password would allow them to log in, but they can't decrypt the files without your original password as that is (indirectly) used to encrypt the files.

Exactly.

When you change your log in password, you should do it from the graphical interface.

If you change your password either as root or from the command line, your home directory will not be decrypted. You would then need to manually re-wrap the ecryptfs pass phrase.

See :

[http://bodhizazen.net/Tutorials/Ecryptfs/#Password](http://bodhizazen.net/Tutorials/Ecryptfs/#Password)

---

