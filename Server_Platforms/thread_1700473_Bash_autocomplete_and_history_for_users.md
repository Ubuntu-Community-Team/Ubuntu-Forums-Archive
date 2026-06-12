---
title: "Bash autocomplete and history for users"
date: 2011-03-05
forum: Server Platforms
---

### Post by Demented ZA on 2011-03-05
Hi, 

If I do a 
```
sudo su user1
``` 
to impersonate user1 with root permission, I have no tab autocompletion, I can't use the up/down arrow keys to cycle history and my command prompt is a single 
```
$
```

I have googled the problem, but most solutions are only for a single aspect of my problem, and every aspect requires a seemingly different solution.

AFIK, this is a bash problem and it should be as simple as copying over a bash script from root or a skeleton, shouldn't it?

Also, I would like to do the same for my mail and www-data users, can this be done? Do these "users" have a home directory or something similar associated with it?

Thank you in advance.

---

### Post by SeijiSensei on 2011-03-05
Try

```

$ sudo su
# su user
$ 

```

I've always gotten histories and tab-completion this way.

---

### Post by Demented ZA on 2011-03-05
Thanks for the reply, but that doesn't work for me. It still gives me a single $, no history, and no autocomplete. TAB literally jumps my cursor forward. This also doesn't work for www-data or mail user.

---

### Post by Demented ZA on 2011-03-06
I found the solution to my own problem:

First off, www-data and mail users have already been created by the system and thus use the Bourne Shell, not Bash.

As for some of the users I have created, not all exibited the same problem. It had something to do with the commands I used uppon creating them. At the moment, if i create new users, they work fine.

The solution can be applied to both users, or the www-data or mail accounts:

```
sudo chsh -s /bin/bash user_name
```Voila! Now my problematic users and www-data and mail users have autocomplete, history and shows 
```
user@hostname:path$
```Basically what the above command does is change the shell from Bourne Shell to Bash for the user you specify.

---

