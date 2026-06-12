---
title: "xdiagnose fails to upgrade"
date: 2012-06-16
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by MacUntu on 2012-06-16
... due to Python syntax error:

```
Setting up xdiagnose (2.7) ...
  File "/usr/lib/python3/dist-packages/xdiagnose/assistant.py", line 72
    print 'sixa action setup part1'
                                  ^
SyntaxError: invalid syntax
```

Replace ```
print 'foo'
``` with ```
print('foo')
``` in said file and you're good to go.

---

### Post by MacUntu on 2012-06-16
Or wait five more minutes to get xdiagnose 2.8 - dammit! :D

---

### Post by pressureman on 2012-06-16
Welcome to Python 3! ;-)

I expect to see more minor breakages like this during the transition period.

---

### Post by jerrylamos on 2012-06-17
> **MacUntu said:**
> Or wait five more minutes to get xdiagnose 2.8 - dammit! :D

Waited a lot more than 5 minutes it's still 2.7 and still failed.
Launchpad bug #1013911 comment #6 said removing xdiagnose and re-installing worked.  So I did
sudo apt-get remove xdioagnose 
sudo apt-get install xdiagnose
now it's 2.8 and
Now no error...

Jerry

---

### Post by balloons on 2012-06-18
> **jerrylamos said:**
> Waited a lot more than 5 minutes it's still 2.7 and still failed.
Launchpad bug #1013911 comment #6 said removing xdiagnose and re-installing worked.  So I did
sudo apt-get remove xdioagnose 
sudo apt-get install xdiagnose
now it's 2.8 and
Now no error...

Jerry

Finally! I had this problem all weekend. The fix was not quick in coming.

---

