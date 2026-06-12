---
title: "Question on creating massive accounts"
date: 2008-06-10
forum: Server Platforms
---

### Post by cpthk on 2008-06-10
I am trying to create more than 200 accounts in the system. I tried to write a c program that will read from a file and send command to shell. But I stuck at the passwd command, since this command does not take password from parameter. It only take password when it prompt you to enter new or old password.

Is there any solution right now that can solve this issue? I already have all account username and password typed into a list. I searched on google, lots of people have the same question. But until now, I don't see any solution.

Thanks.

---

### Post by amingv on 2008-06-10
You can try:
```
echo -en "old_pass\nnew_pass\nnew_pass" | passwd <user>
```
Notice that what's behind old_pass and new_pass is a single '\n' character (EDIT: \n is typed as two characters, but it's an escape sequence that represents just one (a newline); just added for clarity on the "single" thing.).

Also, I don't know why do you wish to make a C program since
[PHP]system(<command_here>);[/PHP]
would have the same effect as
```
<command_here>
```
in a shell script, while being more tedious.

---

