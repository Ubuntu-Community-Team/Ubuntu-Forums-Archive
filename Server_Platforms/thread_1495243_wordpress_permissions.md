---
title: "wordpress permissions"
date: 2010-05-27
forum: Server Platforms
---

### Post by blakep2 on 2010-05-27
I just installed word press but to edit i need to enable writable permissions.  Can someone show me how to this and give me some recommendations on good, safe permissions.

---

### Post by Queue29 on 2010-05-27
Basically you need to read a tutorial on how to use **chmod**

When you finish, you should understand the command: 

```
chmod -R a+w
```

And it should be apparent why you would not want to do that anywhere near a directory exposed to the internet. If you want exact answers just handed to you, then you're using the wrong operating system.

---

