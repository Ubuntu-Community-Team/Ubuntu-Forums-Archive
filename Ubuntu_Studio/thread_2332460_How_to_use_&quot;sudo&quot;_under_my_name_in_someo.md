---
title: "How to use &quot;sudo&quot; under my name in someone else's account?"
date: 2016-07-31
forum: Ubuntu Studio
---

### Post by javierdl on 2016-07-31
I need to add a repository for Minetest in the Ubuntu Studio account of my daughter. But Ubuntu is telling me that my daughter is not in the list of sudoers. How do I use my name & password then?

Thanks,

JDL

---

### Post by Bucky Ball on 2016-07-31
Why not [add your daughter to the sudoers list ]("http://askubuntu.com/questions/7477/how-can-i-add-a-new-user-as-sudoer-using-the-command-line")instead? You haven't given much detail about her account and its permissions. If you are logged in with her account, how do you expect to use yours? You are an admin and she is a guest?

---

### Post by steeldriver on 2016-07-31
You should be able to use su to **s**witch to your own **u**ser first

```

su yourusername

```
(you will be asked for your own password)

Then run whatever sudo command (you will be asked to confirm your own password again). 

When you are done, you can return the terminal to your daughter's account by exiting the su shell

```

exit

```

---

### Post by javierdl on 2016-07-31
Thank you both for replying guys! :)

steeldriver, that was exactly what I needed! It worked like a charm! Thanks a million! :)

---

### Post by Bucky Ball on 2016-07-31
Good news. Please mark as solved to help others. See Thread Tools at top right or the link in my signature. Thanks.

---

