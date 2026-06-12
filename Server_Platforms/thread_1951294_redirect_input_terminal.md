---
title: "redirect input terminal"
date: 2012-04-02
forum: Server Platforms
---

### Post by cris_1986 on 2012-04-02
hy,
in a terminal i open a new terminal:
```
gnome-terminal
```

now i have 2 terminal: the main terminal and the second terminal.
Can i redirect the keyboard input from the main to the second?

Example:
Main terminal:
```
echo hello world
```

second terminal:
```
hello world
```

---

### Post by Paddy Landau on 2012-04-02
You can redirect both input and output for child processes using [FONT=Lucida Console]coproc[/FONT]. However, it does not work for a Bash terminal, because the input and output are internal to the terminal.

You could have output from the second terminal redirect to a file (I suggest a RAM file; create a temporary file in [FONT=Lucida Console]/run/shm[/FONT] using [FONT=Lucida Console]mktemp[/FONT]), and have the first terminal watch for changes to the file using [FONT=Lucida Console]tail --follow[/FONT] or [FONT=Lucida Console]inotifywait[/FONT].

---

