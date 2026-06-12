---
title: "Hidden launchers are recognized and run at startup"
date: 2012-08-11
forum: Security
---

### Post by hakermania on 2012-08-11
I've -multiple times- created launchers at ~/.config/autostart/ so as to start a program/something on startup (when I login).

The thing is that the system recognizes even the files that start with . (dot) and end with .desktop and executes them manually.

We are not used to find hidden files under hidden directories, but, of course, it is possible.

And, as most of as, I think, I have used to only do
```

ls

```
or
```

ls -l

```
and no
```

ls -a

```
**inside** the hidden directories.

So, a malicious script may place (with normal user permissions(!)) a hidden .desktop file under ~/.config/autostart and the system will execute it normally.

When the user goes to see its launchers it will not probably see the malicious .desktop file; he will probably miss it.


What do you think? When can I report this as an idea? Is [http://brainstorm.ubuntu.com/](http://brainstorm.ubuntu.com/) the right place for this?

---

### Post by vexorian on 2012-08-11
define normal user permissions. .desktop files are not supposed to run without "executable" flag. Does it run without it?

You should probably talk about this in launchpad, it is closer to a bug than an idea.

Edit: meh, all my launchers in that folder have no executable permission. It seems the startup thing runs them without it.

Edit 2: The startup apps menu command in the system menu of the indicator shows hidden launchers anyway.

---

### Post by hakermania on 2012-08-11
> **vexorian said:**
> Edit 2: The startup apps menu command in the system menu of the indicator shows hidden launchers anyway.
I know about it, but still, we have all get so much used to the fact that everything is hidden only under our $HOME that, even if we see something 'strange' there (let's say that the bad-guy has named the program Grub-Wrapper so as not to be easily detectable) and look under ~/.config/autostart, we will not find anythin (because it is hidden) and we will assume that it is something system dependent that we should better "not to touch".

At least that is what I would do if I didn't know about hidden launchers. Now, what would a new user do? I'm in linux 3.5 years...

---

