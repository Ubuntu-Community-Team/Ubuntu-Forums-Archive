---
title: "Administration Question"
date: 2009-05-10
forum: Security
---

### Post by NvidiaN on 2009-05-10
Hi, I'm very noob...but I'm trying to not be so much. Here goes!

How do I turn off all security requirements, password requirements, etc. in Kubuntu Jaunty? I am being prompted for passwords I don't have while attempting to change system settings, and told that I need to be administrator, when I'm the only account (not talking about in terminal). I can't even change my account 'user picture'! It's annoying, and I want to turn it all off so that I can just modify anything.

Thank you

---

### Post by bodhi.zazen on 2009-05-10
What you are asking is not directly supported.

Learn to use sudo and kdesudo

```
kdesudo kate /path/to/file-to-edit
```See : [uwiki]RootSudo[/uwiki]

---

