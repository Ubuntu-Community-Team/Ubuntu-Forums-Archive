---
title: "Multiple Commands in Single Line"
date: 2007-08-21
forum: The Cafe
---

### Post by cawill on 2007-08-21
I know ; and && can be used to put multiple commands into a single line, but they don't always work.

How do you have a single line command were it runs to programs at the same time even if the other one runs or fails to run.

For example: ```
conky ; avant-window-navigator
```  or the && variant will only run the command that is first (either conky or AWN depending on which is first)

Also when replacing window managers (eg metacity --replace) the commands stop there and don't continue.

How can I get round this?

---

### Post by Bachstelze on 2007-08-21
```
command &
```

Will run the command in the background and bring you back to the prompt, so you can do

```
command1 &
command2 &
command3 &
```

and so on...

---

### Post by ynnhoj on 2007-08-21
something like
```
$ command1 & ; command2 &
```
ought to work too, if you really want it to be a one-liner.

---

### Post by garba on 2007-08-21
try this:

(command1 &);(command2 &)

that should spawn two concurrent processes

---

### Post by init1 on 2007-08-21
> **ynnhoj said:**
> something like
```
$ command1 & ; command2 &
```
ought to work too, if you really want it to be a one-liner.
No.
```

ls & ; ls &
bash: syntax error near unexpected token `;'

```

---

### Post by Bachstelze on 2007-08-21
Use parentheses, as garba suggested.

---

### Post by Compucore on 2007-08-21
I've always used the pipe character which is | for putting multiple commands on the same line. It worked for me in linux before. And when I used to type commands in AIX when I was in the command line. Give that a try as well as an alternative. :D

Compucore

---

### Post by ynnhoj on 2007-08-21
> **init1 said:**
> No.
```

ls & ; ls &
bash: syntax error near unexpected token `;'

```
i did
```
leafpad & ; mirage & ; gtkpod &
```
and it was a-okay.  but my shell is zsh, not bash -- perhaps that explains it?

edit: and fer the record, the example you posted works fine for me as well :)

---

### Post by ynnhoj on 2007-08-21
> **Compucore said:**
> I've always used the pipe character which is | for putting multiple commands on the same line. It worked for me in linux before. And when I used to type commands in AIX when I was in the command line. Give that a try as well as an alternative. :D

Compucore
pipe is a bit of a different story, though -- it will redirect the output of one program into another. for example, to read the listing of a directory with many files, page-by-page, you could do
```
ls | more
```
which, of course, is considerably different from
```
ls & ; more &
```
(or something along those lines)

---

### Post by gaellafond on 2010-05-12
Using this:
command1; command2

Will execute both commands, **whatever append** after the first one.

If you want to execute 1 command, than execute a second one **only if the first one succeed**, you have to use this:
command1 && command2

**Explanation:**
The && is the binary AND operator. When you use it with commands, the line is evaluate as a Boolean expression. To be TRUE (succeed), the expression must have both parts TRUE. If the first one is FALSE (the command fail), the system do not need to evaluate the second one since "FALSE && whatever" is always FALSE.

**NOTE:** You can use this with multiple commands:
command1 && command2 && command3 && command4
You can also mix it with the **OR** operator (two pipes **||**), but it make code very difficult to understand. If you want to execute something more complex, use the **if** statement.

---

### Post by janpetel on 2011-08-19
I use this sometimes to start some apps full screen. E.g. ('Loopy' is a game I sometimes play from the Simon Tatham collection and is only an example. I have other apps that require more wmctrl tweaking, like displaying vlc nicely on a second monitor):

# (loopy &) ; (sleep 1) ; (wmctrl -F -r Loopy -b add,fullscreen &)

[omit the hash tag!]

In this case, I obviously want the sleep command to execute first (to ensure the game is visible), so it has no ampersand there.
This has to go in a script file to be called from a desktop launcher, still, because in a launcher this doesn't work. If someone could tell me why?

And if you have a script file, why bother with single lines?

---

### Post by Iowan on 2011-08-19
Closed.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

