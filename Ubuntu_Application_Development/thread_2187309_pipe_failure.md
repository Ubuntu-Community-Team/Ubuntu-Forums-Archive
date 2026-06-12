---
title: "pipe failure"
date: 2013-11-11
forum: Ubuntu Application Development
---

### Post by jamescraigziegler on 2013-11-11
I am using a pipe to send messages from one process to another.

The first process does:
string msg;
ssize_t msg_len=msg.size();
 cnt=write(w_fd, &msg_len, sizeof(ssize_t));
check cnt, if it is not correct (==sizeof(ssize_t)), abort
cnt=write(w_fd, msg.c_str(), msg_len);
check cnt, if it is not correct (==msg_len), abort
repeat for each message
this never aborts

The second process does:
char line[500];
ssize_t msg_len, cnt, cnt2;
do{
cnt=read(r_fds[i], &msg_len, sizeof(ssize_t));
} while (0==cnt || -1==cnt);
 check cnt, if it is not correct (==sizeof(ssize_t)), abort
cnt2=read(r_fds[i], line, msg_len);
check cnt, if it is not correct (==msg_len), abort

these are somewhat simplified from the actual code, e.g code
to account for partial lengths is not shown

the problem is that this works almost all the time, but very 
occasionally it fails.  when it does, the first write has 
completed and the second write is in progress.  The first
read has also completed, and the abort test passed.

However, the msg_len being sent is 49, but the msg length 
received is 2314885530818453536, and no further data can
be read from the pipe.

Any ideas what is going wrong?

---

### Post by TheFu on 2013-11-11
[B]char line[500];
[/B]Is the first issue.  The input is overflowing. Might help if you specified which language was used, BTW.  Isn't there a way to read from any sized input safely in the language used? gets() or fgets() is what you probably want or use the streamio classes.  Different languages might use different sizes too - uint vs int so watch for unintended type conversions.

---

### Post by jamescraigziegler on 2013-11-11
Sorry, that's not it...actual logged message lengths never exceed 200 characters.

---

