---
title: "Newbie to Terminal"
date: 2009-06-20
forum: Server Platforms
---

### Post by drumking88 on 2009-06-20
I'm pretty new to Ubuntu linux, but have learnt some unix in the past. My problem is:

I have used PuTTY in the past to connect to a debian server (dev.domain.com) and have had no problems using PuTTY to do my work. 

Today, I installed Ubuntu onto my laptop and am trying to familarise myself with the Terminal which is where I am having trouble trying to connect to the server. 

my username on my laptop is admin, whereas my username on the server is p_umf. 

How would I access the server from terminal?

Thanks for your help guys!

S

---

### Post by Sef on 2009-06-20
Moved to Server Platforms.

---

### Post by davidmigl on 2009-06-21
I'm pretty sure you could just use ssh, since that's what putty is for windows:

```
ssh p_umf@dev.domain.com
```

The command is of the form ssh username@server. Add -X if you'd like to launch gui windows from the server on your computer.

---

