---
title: "blocked myself out of a folder, trying to unblock it"
date: 2010-04-27
forum: Security
---

### Post by shaf1220 on 2010-04-27
hi i have xubuntu 9.10 and i wanted to password protect some of my work so i went under folder properties, went under permissions and changed access to none.  group -> admin read only. and for others i hit in "none". now i cant even access my folder and it keeps on saying permission denied. how do i unblock it. yet alone, how do i delete the folder?

---

### Post by HermanAB on 2010-04-27
$ sudo chown -R yourusername:yoursusername directoryname

See 'man chown' for details.

---

### Post by shaf1220 on 2010-04-27
i got everything right except the directory name. how do i put that in? for example this is what im writing in  terminal

sudo chown -R bob:bob Downloads/work

---

### Post by shaf1220 on 2010-04-27
i got everything right except the directory name. how do i put that in? for example this is what im writing in  terminal

sudo chown -R bob:bob Downloads/work

---

### Post by gdonwallace on 2010-04-27
If you are in the downloads directory try this:

sudo chown -r bob:bob work 

If you are in the root directory, you just need to make a small change to the command:

sudo chown -R bob:bob **/**Downloads/work 

That should fix the problem.

---

### Post by shaf1220 on 2010-04-27
> **gdonwallace said:**
> If you are in the downloads directory try this:

sudo chown -r bob:bob work 

If you are in the root directory, you just need to make a small change to the command:

sudo chown -R bob:bob **/**Downloads/work 

That should fix the problem.
the blocked folders name is "get outta here"  but its location is   shaf:download/work

after i entered what you told me to enter this is what came out

shaf@shaf-laptop:~/Downloads/work$ sudo chown -R shaf:shafgetouttahere 
chown: missing operand after `shaf:shafgetouttahere'
Try `chown --help' for more information.

---

### Post by cdenley on 2010-04-27
How did you come up with that command? Read the manual!
```

man chown

```
How is there a ":" in your location? I can tell from your output you posted it is in your home directory.
```

cd ~/Downloads/work
sudo chown $USER "get outta here"
sudo chmod -R u+rwX "get outta here"

```

---

### Post by shaf1220 on 2010-04-27
> **cdenley said:**
> How did you come up with that command? Read the manual!
```

man chown

```
How is there a ":" in your location? I can tell from your output you posted it is in your home directory.
```

cd ~/Downloads/work
sudo chown $USER "get outta here"
sudo chmod -R u+rwX "get outta here"

```
got it, it works now. many thanks to all three of you

---

