---
title: "Root user...."
date: 2007-05-02
forum: Server Platforms
---

### Post by sloggerkhan on 2007-05-02
Question: 
My system>admin>users&groups shows a root user on feisty fawn....
I have not meant to enable a root account, but apparently one is enabled (possibly might have been required for virtualbox (which I've gotten rid of) or something?)
In any case, how do I de-enable it? Or am I missing something?

---

### Post by jtc on 2007-05-02
The root user exists no matter if you have enabled it or not.

Still, to answer your question. You can use the following command to disable root login.

```
sudo passwd -l root
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

