---
title: "[SOLVED] add/remove user's sudo ability"
date: 2008-07-24
forum: Security
---

### Post by sp0nge on 2008-07-24
I know this has to be possible, I just can't seem to understand how. I want to control which users have sudo access and which do not. Even better, can I designate a group for sudo access and assign the users I'd like to the group?

---

### Post by Oldsoldier2003 on 2008-07-24
> **sp0nge said:**
> I know this has to be possible, I just can't seem to understand how. I want to control which users have sudo access and which do not. Even better, can I designate a group for sudo access and assign the users I'd like to the group?

By default, members of the "admin"group can sudo. You can change this and apply subgroups or allow certain users to use certain commands by editing /etc/sudoers. See [uhelp]community/Sudoers[/uhelp]

---

### Post by sp0nge on 2008-07-24
Ok so I may go about this differently. I understand how to create groups and add users to them, but is there a command that will show me what group(s) a user is in?

---

### Post by Oldsoldier2003 on 2008-07-24
> **sp0nge said:**
> Ok so I may go about this differently. I understand how to create groups and add users to them, but is there a command that will show me what group(s) a user is in?

```
id <username>
```

---

