---
title: "chmod and chown"
date: 2008-08-27
forum: The Cafe
---

### Post by sameerds on 2008-08-27
It seems that a lot of users on the forum take these two utilities very lightly. [This thread]("http://ubuntuforums.org/showthread.php?t=900434") is a good example of the mayhem that indiscriminate use of chown and chmod can cause. People are quick to paste commands that usually take one of two forms, without any care about side-effects:

```

sudo chown -R user ...
sudo chmod -R 700 (or 777) directory ...

```

What is the best place to put up a big nice warning about being very careful with these commands? Something like the list of malicious commands that you can see in general help.

---

