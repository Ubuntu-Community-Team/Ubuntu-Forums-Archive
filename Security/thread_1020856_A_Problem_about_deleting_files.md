---
title: "A Problem about deleting files"
date: 2008-12-24
forum: Security
---

### Post by Eliad on 2008-12-24
I recently had a problem with Ubuntu 8.04. I'm not sure weather it is my problem or Ubuntu's.
The problem:
When you want to move a folder containing some files to Trash, Ubuntu checks if  you have the permission to delete the folder, but it does not do that for the files. So you can do something you do not have the permission to. But the even bigger problem is when you want to empty your Trash, Ubuntu checks if you have the permission to delete the files, which you do not. So you cannot Empty your Trash and you cannot move them out of your Trash either. Other users cannot see your Trash. So they are stuck in there forever.
What should I do?

---

### Post by albinootje on 2008-12-24
> **Eliad said:**
> 
When you want to move a folder containing some files to Trash, Ubuntu checks if  you have the permission to delete the folder, but it does not do that for the files. So you can do something you do not have the permission to. But the even bigger problem is when you want to empty your Trash, Ubuntu checks if you have the permission to delete the files, which you do not. So you cannot Empty your Trash and you cannot move them out of your Trash either. Other users cannot see your Trash. So they are stuck in there forever.

Open a terminal, and type :
```

gksu nautilus

```
Assuming in the following example that your username is john, you would search within Nautilus for :
```

/home/john/.Trash/
/home/john/.local/share/Trash/

```

---

