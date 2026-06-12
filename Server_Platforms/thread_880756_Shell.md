---
title: "Shell?"
date: 2008-08-05
forum: Server Platforms
---

### Post by swu on 2008-08-05
I'm running Ubuntu server 6.06LTS. I am not sure what keystroke combo I hit while typing at the CLI on my server, but now everything I type is in CAPS and it's not taking any commands.

Anything I type in goes in caps (CLEAR  EXIT LS) and comes back with:

- bash: CLEAR: command not found

I can ssh in and that session is fine, but how do I undo whatever it is I did on session that is on the main keyboard and screen?

Thx!

---

### Post by munkyeetr on 2008-08-05
Just to rule out the obvious...your CAPSLOCK key on your keyboard isn't enabled is it?

---

### Post by jonabyte on 2008-08-05
If the above does not help..

when in doubt, reboot!

---

### Post by tamoneya on 2008-08-05
> **jonabyte said:**
> If the above does not help..

when in doubt, reboot!

that sounds like windows talking to me.  That only solves the symptom and doesnt get to the root of the problem.

Can you switch tty sessions?  Do you have the same problem in tty2 (ctrl-alt-F2)?

---

### Post by swu on 2008-08-05
No, it's not the CAPS lock, even if it was that wouldn't explain the command not found error with anything I am typing in.

ctrl-alt-F2 doesn't switch sessions, nothing changes.

This is a production box so rebooting isn't an option until later. Can I kill the session? Is the directly connected keyboard/mon always tty1?

Thx!

---

### Post by ajgreeny on 2008-08-05
> No, it's not the CAPS lock, even if it was that wouldn't explain the command not found error with anything I am typing in.
I'm not quite sure what you mean by this; why wouldn't it explain the command not found error?  Don't forget Linux is case sensitive, so EXIT is not the same as exit.  This is not msdos!

---

### Post by scorp123 on 2008-08-06
> **swu said:**
> No, it's not the CAPS lock, even if it was that wouldn't explain the command not found error with anything I am typing in. Commands are case-sensitive !! ;-)

"exit", "Exit" and "EXIT" are *NOT* the same commands!!

---

### Post by dmizer on 2008-08-06
Can you change to lowercase letters with the <shift> key?

---

