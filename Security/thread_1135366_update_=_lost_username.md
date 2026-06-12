---
title: "update = lost username"
date: 2009-04-24
forum: Security
---

### Post by mcrene on 2009-04-24
My ubuntu recently updated, which so far looks good.
But before I can login its asking me for my username/password.

I am trying all of my usernames, well there are only 3 possible, but trying others just in case. Either way, none are working.

Thinking back whenever Ubuntu would ask for my password previous to updating it had an IP address now and then I think as the username... does that make sense? Maybe that was for hotmail, but I can't remember specifically right now.

So here I am, wanting to get back to using my computer, but I can't because my username/password is not correct.

Is there a way of finding out what my name/pass is? If not, what am I to do?

thanks for all help.

---

### Post by cariboo on 2009-04-24
To find out what your user name is start in recovery mode, press esc at the grub menu, when you get to the menu select drop to root prompt.

Once at the prompt type:

```
cd /home
```

then run a listing of the home directory:

```
ls -l
```

you will see a directory with your user name.

To change your password, at the prompt type:

```
passwd <username>
```

where <username> is your user name without the brackets.

---

### Post by h20son on 2009-04-24
Did you try just using the "tab" key to move from the "username" to the "password" field?

Just a thought.

---

