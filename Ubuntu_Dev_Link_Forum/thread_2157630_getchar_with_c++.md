---
title: "getchar with c++"
date: 2013-06-26
forum: Ubuntu Dev Link Forum
---

### Post by SirGuineaPig on 2013-06-26
Hello. I am trying to set up a pause function in my program. I have tried cin.get() and getchar(), but they only work once in each of my functions.
The program likes to skip to the very last one and use that one only. It is for a text adventure, and here is the code for it.

```

int wait()
{
    cout<<"Press enter to continue..."<<endl;
    somePauseFunction();
}

```

Are there any other pausing commands that I could use? Thanks!

---

### Post by TheFu on 2013-06-26
Don't cin and cout use buffered IO?  You want to use unbuffered IO, right?  What, exactly, is in the wait() function?

BTW, I find the code hard to read. A little more white space would help.

---

### Post by SirGuineaPig on 2013-06-27
I just wanted to make a pause function to stop the program like system("PAUSE") would, but to where it isn't system-dependent.
It has skipped over the first time the wait() function appears in the program and gone to the next.
Also, I am kind of fuzzy on what unbuffered/buffered IO is. What are they?

---

