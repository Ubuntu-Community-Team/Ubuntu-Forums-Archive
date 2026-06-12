---
title: "curses not working"
date: 2011-04-22
forum: Ubuntu Dev Link Forum
---

### Post by FirefoxRocks on 2011-04-22
I'm trying to do some simple programming with curses but it is not working with Ubuntu.

At school I believe the server we program on uses openSUSE. At home my only Linux operating system is Ubuntu (10.10 at the moment).

I have installed libncurses5-dev and the program compiles with no error, but nothing happens when I run it.

Here is the program code if it helps:
```
#include <curses.h>

int main() {

        initscr();
        move(10,10);
        printw("%s", "Hello world");
        refresh();
        endwin();
}
```

I don't know what I'm doing wrong?

---

### Post by wojox on 2011-04-22
Mine got errors and I add what I needed:

```
#include <curses.h>

int main() {

        initscr();
        move(10,10);
        printw("%s", "Hello world");
        refresh();
        getch();
        endwin();

        return 0;
}

```

```
gcc -Wall -W -pedantic cursors.c -o test -lncurses
```

---

### Post by FirefoxRocks on 2011-04-22
Ok I tried your code and it works in the Terminal, but then I realized my own code works in tty-2 or the one where you press CTRL+ALT+F2, F3, and so on...

Why is this?

---

