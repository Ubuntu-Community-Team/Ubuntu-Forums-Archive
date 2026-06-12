---
title: "chown recursion problem on home directories"
date: 2011-04-26
forum: Server Platforms
---

### Post by pem725 on 2011-04-26
Greetings,

I have a perplexing problem that I was hoping some of you might help me solve.  My servers run 10.10 and also serve as standalone LTSP hosts - none of this is terribly relevant I hope.  Recently, a user complained of permission problems and so I ran a simple command:

```
chown -R username:username /home/username/*
```

and

```
chown -R username:username /home/username/.*
```

The first chown worked just fine but the second buggered the rest of the user accounts by changing the ownership for all dot files to that user.  Now I realize how recursion works but it should stay within the confines of the specified user directory, no?  Because it did not, I suspected that there was a dotfile that was shared across all users and thus, the recursion skipped out of the specified username's home directory and into the other users home directories.  Does that make sense?  Well it doesn't to me either.  I searched for any symbolic links that might link user directories together and found none.  Any suggestions or insights would be greatly appreciated.  

Cheers,

Patrick

---

### Post by egpetrich on 2011-04-26
Ouch. I think that your pattern ".*" caught the directory "..", which is the parent directory (probably /home). So the recursion worked as specified, but you inadvertently pointed one level higher than you expected.

I think the correct way to do this would have been:
```
cd /home
chown -R username:username username
```

---

### Post by samosamo on 2011-04-26
> **egpetrich said:**
> Ouch. I think that your pattern ".*" caught the directory "..", which is the parent directory (probably /home). So the recursion worked as specified, but you inadvertently pointed one level higher than you expected.

I think the correct way to do this would have been:
```
cd /home
chown -R username:username username
```

one command is much more simple

```
chown -R username:group /home/username
```

---

### Post by thinmintaddict on 2011-04-27
To Simplify:

chown -R already catches dot files, so the second command was unneccsary, and included /home/username/.. which translates to /home/*

to fix it just chown -R each of the users home directories back over to them.

---

### Post by pem725 on 2011-04-27
Thanks for the guidance.  When I wrote my script to change ownership of the files, I did not think about the .* being interpreted as the .. as well.  Great catch!  Thanks again everyone.  

NOTE:  I marked the thread as solved.

---

