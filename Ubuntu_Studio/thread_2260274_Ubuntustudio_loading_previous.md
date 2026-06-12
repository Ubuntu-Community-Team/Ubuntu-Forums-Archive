---
title: "Ubuntustudio loading previous"
date: 2015-01-10
forum: Ubuntu Studio
---

### Post by mrule on 2015-01-10
I have unselected "Automatically save sessions on logout" in the "Sessions and Startup" panel of setting manager. Despite this, ubuntustudio is still loading the applications from the previous session at loging. How do I stop this?

p.s.: sorry about the weird title, I have no idea how it got truncated. Should read "Ubuntustudio loading previous sessions at startup?"

---

### Post by bhilmers2 on 2015-01-10
Do you logout through the main menu? There is a checkbox at the bottom that says "[ ] save session for future logins." Is it checked? Also see:
```
~$ xfce4-session-logout
```

---

### Post by mrule on 2015-01-10
Thanks for your reply! 

I do not have such a check box when I logout through the GUI. Logging out via xfce4-session-logout gives the same behaviour?

---

### Post by unimatrixdoc2 on 2015-01-11
Wondering if clicking "Clear Saved Sessions" would do anything. Under, "Session and Startup" --> "Session".

---

### Post by bhilmers2 on 2015-01-11
> **mrule said:**
> I do not have such a check box when I logout through the GUI.
What version of Ubuntu Studio are you running? Do you choose "Shut Down" from the panel?

I would choose "Log Out" from the panel or menu (which should execute xfce4-session-logout) and see if the checkbox is there. Also try unimatrixdoc2's suggesstion above.

After that I am out of ideas.

---

### Post by mrule on 2015-01-12
Thanks bhilmers and unimatrixdoc! 

This worked: I had to check "prompt on logout" in the sessions control panel, then I was able to uncheck 'save session'. ( unchecking save session in the control panel had no effect ). I also cleared saves sessions at the same time, which might have helped?

---

