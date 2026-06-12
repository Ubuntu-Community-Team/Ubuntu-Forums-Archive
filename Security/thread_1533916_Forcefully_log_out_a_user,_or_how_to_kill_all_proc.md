---
title: "Forcefully log out a user, or how to kill all processes of a user"
date: 2010-07-18
forum: Security
---

### Post by diegoful on 2010-07-18
You can force a user to logout by killing all the processes started by her/him. Here's a simple way that works for me:

```
ps -ef | awk '/*username*/ {print $2}' | xargs kill -9
```

You can also **log yourself out** this way. Doing so sends you back to the login screen.

---

### Post by Agent ME on 2010-07-18
Running "kill -9 -1" kills all processes that your user can kill (just their own unless they're root), so doing "sudo su username -c 'kill -9 -1'" also does the trick and I find it's easier to remember. But then yours doesn't intrude on the other user's account so much, so guess that's a more proper way.

---

### Post by FuturePilot on 2010-07-18
You're all making it too complicated ;)

```
sudo pkill -u user
```

Replace user with the username.

---

