---
title: "Permissions issue"
date: 2014-08-19
forum: Security
---

### Post by rwslippey2 on 2014-08-19
Been a while since I've been around here so maybe I'm missing something completly....   I've got a directory with www-data as owner and a group name as group.....   permissions are 770 (not what I want in the end but....) Even with 770 members of the group can't even read the directory.   Did I miss something?  I've confirmed the users are indeed members of the group... I'm sure I've missed something just plain dump..  Thanks for your help in advance

---

### Post by sudodus on 2014-08-20
Welcome to the Ubuntu Forums :-)

Please give us some more details: post the output of these commands

1. In the directory ***above*** the  directory 'with www-data as owner and a group name as group'

```
sudo ls -l
```

You should see the directory name listed with its permissions.

2. and in the  directory with 'www-data as owner and a group name as group' itself

```
sudo ls -l
```

You should see the files (and sub-directories) listed with their permissions.

-o-

Is there encrypted home? Or is there something else that might stop reading this directory and its files?

---

### Post by fugu2 on 2014-08-20
after you added that user to the group, did you logout and relogin? Sometime programs are fussy like that

---

