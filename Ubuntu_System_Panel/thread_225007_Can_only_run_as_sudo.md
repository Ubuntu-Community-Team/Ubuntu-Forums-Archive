---
title: "Can only run as sudo"
date: 2006-07-28
forum: Ubuntu System Panel
---

### Post by Jedeye on 2006-07-28
Hey first off im new and I can get it to run in a window by itself only as sudo... nothing shows up on my panel when I add it. Am I missing something? easy to follow tips are great :D 

thanks!

---

### Post by chanders on 2006-07-28
I am suspecting that you have permission problems in your 

/usr/share/applications
/usr/share/applications/kde
/usr/local/share/applications 
~/.local/share/applications

folders. I will try to check for this in the next release.

Try running

usp run-in-window

as a normal user and post your output here

---

### Post by Jedeye on 2006-07-28
This is what I get
```
jon@dapper:~$ usp run-in-window
Traceback (most recent call last):
  File "/usr/bin/usp", line 1517, in ?
    menu_factory(app, None)
  File "/usr/bin/usp", line 1508, in menu_factory
    MenuWin(applet, iid)
  File "/usr/bin/usp", line 1373, in __init__
    self.mainwin = MainWindow()
  File "/usr/bin/usp", line 93, in __init__
    self.Todos()
  File "/usr/bin/usp", line 584, in Todos
    openfile = open(self.get_file_path(path), 'r')
IOError: [Errno 13] Permission denied: '/home/jon/.local/share/applications/googleearth.desktop'
jon@dapper:~$

```

---

### Post by chanders on 2006-07-28
> **Jedeye said:**
> This is what I get
```
jon@dapper:~$ usp run-in-window
Traceback (most recent call last):
  File "/usr/bin/usp", line 1517, in ?
    menu_factory(app, None)
  File "/usr/bin/usp", line 1508, in menu_factory
    MenuWin(applet, iid)
  File "/usr/bin/usp", line 1373, in __init__
    self.mainwin = MainWindow()
  File "/usr/bin/usp", line 93, in __init__
    self.Todos()
  File "/usr/bin/usp", line 584, in Todos
    openfile = open(self.get_file_path(path), 'r')
IOError: [Errno 13] Permission denied: '/home/jon/.local/share/applications/googleearth.desktop'
jon@dapper:~$

```

Just as I suspected... All those files should have read permission for all users however on your system they cant be read.

What you cand do is open a terminal

sudo nautilus

Find the files and right click-> properties->permissions and make sure you have read checked for Owner, group, others
You can tell what file is giving trouble from the output above. Eg the above file giving problem was /home/jon/.local/share/applications/googleearth.desktop

---

### Post by Jedeye on 2006-07-29
Thanks! Worked like a charm... this is a great project!!

---

