---
title: "Unity2d: change in behaviour when using Dash to start programs by name"
date: 2012-02-19
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by keithpeter on 2012-02-19
Hello All

Unity2d installed from 5.4.0-0ubuntu1:

[LIST=1]
[*]Tap Windows key to bring up Dash
[*]Type name of program, e.g. Gedit
[*]When Gedit is the first app listed, press enter
[*]Gedit does **not** start
[/LIST]

This is a change in behaviour from when I last used Unity2d. Is it a deliberate change or a bug?

Above sequence in Unity full fat will start Gedit.

---

### Post by mc4man on 2012-02-19
Probably not intentional, unity-2d recently switched to using unity 3d Dash style, maybe a break in implementation

---

### Post by keithpeter on 2012-02-22
Hello All

I've reported this as a bug as it is still here after today's large updates.

[#938998]("https://bugs.launchpad.net/ubuntu/+source/unity-2d/+bug/938998")

If you are using Unity2d and you see the same (non) behaviour, just add yourself.

400+ bugs on Unity2d :-(

---

### Post by keithpeter on 2012-02-24
Hello All

I'm bumping this in the hope that others can confirm the behaviour and add themselves to the bug.

Unity-2d 5.4.0-0ubuntu1 is the package version. I'd hate this to slip into a release candidate

---

### Post by ppd on 2012-02-24
I have confirmed it.
I wonder what's up with Unity 2D. No (easily) resizable launcher and the push to reveal does also not seem to have landed in Unity 2D yet.

---

### Post by keithpeter on 2012-03-07
Hello All

This bug seems to have been corrected in the latest Unity2d update, but not shown on launchpad. I'll mark it as 'no longer a bug' when I work out how to

Cheers

---

