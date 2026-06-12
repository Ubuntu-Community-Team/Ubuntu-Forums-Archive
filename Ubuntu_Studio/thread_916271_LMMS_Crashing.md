---
title: "LMMS Crashing"
date: 2008-09-10
forum: Ubuntu Studio
---

### Post by Patrick793 on 2008-09-10
I recently downloaded LMMS 0.4.0 RC1. I installed it using the Hardy .debs provided from the LMMS site. The problem is, it keeps crashing. It crashes if I try bringing up the settings box, or if I try to add an .ogg, which is important for the music I make. Here are the errors from the terminal.

Opening settings:
```
patrick@patrick-desktop:~$ lmms
could not set realtime priority.
QMetaObject::indexOfSignal:model: Conflict with QObject::destroyed()
QMetaObject::indexOfSignal:model: Conflict with QObject::destroyed()
QMetaObject::indexOfSignal:model: Conflict with QObject::destroyed()
QMetaObject::indexOfSignal:model: Conflict with QObject::destroyed()
QMetaObject::indexOfSignal:model: Conflict with QObject::destroyed()
QMetaObject::indexOfSignal:model: Conflict with QObject::destroyed()
QMetaObject::indexOfSignal:model: Conflict with QObject::destroyed()
QMetaObject::indexOfSignal:model: Conflict with QObject::destroyed()
QMetaObject::indexOfSignal:model: Conflict with QObject::destroyed()
QMetaObject::indexOfSignal:model: Conflict with QObject::destroyed()
QMetaObject::indexOfSignal:model: Conflict with QObject::destroyed()
QMetaObject::indexOfSignal:model: Conflict with QObject::destroyed()
QMetaObject::indexOfSignal:model: Conflict with QObject::destroyed()
JO-ID 273096 already in use by another object!
JO-ID 273096 already in use by another object!
QMetaObject::indexOfSignal:model: Conflict with QObject::destroyed()
QMetaObject::indexOfSignal:model: Conflict with QObject::destroyed()
QMetaObject::indexOfSignal:model: Conflict with QObject::destroyed()
Segmentation fault
patrick@patrick-desktop:~$
```

Adding an .ogg (like a drum kick or something):
```
patrick@patrick-desktop:~$ lmms
could not set realtime priority.
QMetaObject::indexOfSignal:model: Conflict with QObject::destroyed()
QMetaObject::indexOfSignal:model: Conflict with QObject::destroyed()
QMetaObject::indexOfSignal:model: Conflict with QObject::destroyed()
QMetaObject::indexOfSignal:model: Conflict with QObject::destroyed()
QMetaObject::indexOfSignal:model: Conflict with QObject::destroyed()
QMetaObject::indexOfSignal:model: Conflict with QObject::destroyed()
QMetaObject::indexOfSignal:model: Conflict with QObject::destroyed()
QMetaObject::indexOfSignal:model: Conflict with QObject::destroyed()
QMetaObject::indexOfSignal:model: Conflict with QObject::destroyed()
QMetaObject::indexOfSignal:model: Conflict with QObject::destroyed()
ASSERT failure in QCoreApplication::sendEvent: "Cannot send events to objects owned by a different thread. Current thread 8b0bc10. Receiver '' (of type 'model') was created in thread 83a9a68", file kernel/qcoreapplication.cpp, line 274
Aborted
patrick@patrick-desktop:~$
```

Does anyone know what the problem is? I never had this problem with 0.3.1 or 0.3.2.

---

### Post by Stochastic on 2008-09-10
First and foremost, the **RC1** in the lmms version number is an indication that you're using development software (it stands for release candidate #1), therefore bugs are to be expected and if you don't know how to report/document/fix these bugs then using development software is NEVER recommended.  It seems like your tasks should work, but you're running into some bugs - these should be reported to the LMMS development team.

The only thing that might help is that the first line of your program output looks to imply that there's an issue getting realtime priority set.  Do you have the realtime kernel running?  Is jack running in realtime mode?

---

