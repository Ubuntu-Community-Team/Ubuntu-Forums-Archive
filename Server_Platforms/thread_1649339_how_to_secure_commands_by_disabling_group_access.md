---
title: "how to secure commands by disabling group access?"
date: 2010-12-20
forum: Server Platforms
---

### Post by Alborz on 2010-12-20
Hi

I'm running a server using ubuntu 10.04 x64

I want to disable access of groups to "bin" folder so they cannot execute commands.

[info: actually because of a bug in cPanel (the control panel I installed) Perl will give access to all hosting users to execute commands.]

so what i wanna do is to ban some groups on 'bin' folder, for example 'my_group1' and 'my_group2" cannot access bin but 'my_trusted_group' can access it.

how is it possible?

---

### Post by brettg on 2010-12-22
I may be missing something here but surely this is as simple as;

```
sudo chgrp my_trusted_group /bin/*
sudo chmod 754 /bin/*
```

However, I must warn you that changing permissions of system files can occasionally produce erratic behaviour.

---

