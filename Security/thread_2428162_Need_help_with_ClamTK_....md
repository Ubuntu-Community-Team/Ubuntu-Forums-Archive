---
title: "Need help with ClamTK ..."
date: 2019-09-30
forum: Security
---

### Post by dagmann on 2019-09-30
I have ClamAV and TK installed and they appear to run correctly.
On the ClamTK update page there is a message that there is an update.
Is this update for ClamAV or ClamTK?
Double-clicking Update in the Update section does nothing.
It is set to update automatically as well.
How can you tell if ClamAV and ClamTK are updated?
My ClamTK version is 5.25.
I attempted to join the ClamAV forums but I cannot sign in.
Any help would be appreciated.

---

### Post by #&amp;thj^% on 2019-09-30
They are both the same, use this:
```
sudo freshclam
```

---

### Post by dagmann on 2019-09-30
I tried that command. There is a message when I run it that the ClamAV installation is out-of-date.

---

### Post by ajgreeny on 2019-09-30
The important thing about clamav, (though I have never used it, and suspect that you may not need to either, but that's another question that you didn't ask), is that the virus signatures are up to date.  Running ***sudo freshclam*** as mentioned above by 1fallen, is what keeps those updated.

The version of clamav that uses those signatures is very much less important, so continue using the repository version and you will be fine.

---

### Post by dagmann on 2019-10-01
thanks all

---

