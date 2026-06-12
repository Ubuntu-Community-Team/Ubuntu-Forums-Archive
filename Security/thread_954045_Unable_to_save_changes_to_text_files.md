---
title: "Unable to save changes to text files"
date: 2008-10-20
forum: Security
---

### Post by mikebear45 on 2008-10-20
I'm trying to edit text files to correct problems to my wireless network. My system (Hardy 8.04) seems to deny me administrative access to make the changes...I'm the only user on this computer and have an administrator account?
Can someone help me, or steer me in the right direction to remedy this issue?
                            Thank you.
:confused:Huhh??

---

### Post by mikewhatever on 2008-10-20
As for your info, the only user being an admin all the time is bad Windows legacy. Ubuntu is not Windows and you shouldn't expect it to be ([some more info]("http://psychocats.net/ubuntu/permissions")).
Now, to your question, use <gksudo gedit /etc/network/interfaces> command to open that file for editing.

---

### Post by Dr Small on 2008-10-20
Try:
```
gksudo gedit /etc/network/interfaces
```

Also, please read:
[http://help.ubuntu.com/community/RootSudo](http://help.ubuntu.com/community/RootSudo)

Dr Small

---

### Post by mikebear45 on 2008-10-20
Dr Small, mikewhatever,

Thank you for the advice and quick response. I will read up on your provided links for more information about this system. As for now, I apologize for my "rookie" behavior.

                          Thanks, again.:)

---

### Post by mikewhatever on 2008-10-20
No problemos.:) That's what this forum is for.
PS: Nice hat Dr Small.

---

### Post by Dr Small on 2008-10-20
> **mikebear45 said:**
> As for now, I apologize for my "rookie" behavior.
Not a problem. We all have to start somewhere ;)

> **mikewhatever said:**
> PS: Nice hat Dr Small

Thanks mike :)

---

