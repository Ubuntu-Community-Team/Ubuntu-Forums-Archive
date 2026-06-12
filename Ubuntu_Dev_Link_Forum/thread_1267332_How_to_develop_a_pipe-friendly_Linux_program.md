---
title: "How to develop a pipe-friendly Linux program"
date: 2009-09-15
forum: Ubuntu Dev Link Forum
---

### Post by mihnea.radulescu on 2009-09-15
Hello everybody!

I have been thinking how the traditional Linux apps are designed to be pipe friendly (the pipe-and-filter software architecture).

Writing to stdout is obvious, but how does one know to read from stdin? If one attempts to read data using the read() C library function, one ends waiting forever for something to be input from the keyboard and doesn't know when to stop.

So I guess the C library function select() is used to poll whether or not stdin contains something. Is this the way to go?

Thank you for reading my post! :)

---

### Post by lloyd_b on 2009-09-15
> **mihnea.radulescu said:**
> Hello everybody!

I have been thinking how the traditional Linux apps are designed to be pipe friendly (the pipe-and-filter software architecture).

Writing to stdout is obvious, but how does one know to read from stdin? If one attempts to read data using the read() C library function, one ends waiting forever for something to be input from the keyboard and doesn't know when to stop.

So I guess the C library function select() is used to poll whether or not stdin contains something. Is this the way to go?

Thank you for reading my post! :)

Most programs use the parameters they're given to determine whether or not to read stdin (for example, "grep" assumes it's to read stdin if no FILE parameter is supplied on the command line or that parameter is "-").  They continue reading until they hit an EOF ("<CTRL> D" will issue an EOF if you're entering data at the terminal).

I think you're overthinking the issue - just use the parameters to determine whether to read stdin or not.  If the user winds up misusing the program, and gets stuck at the "waiting for input forever" it's his own problem :)

Lloyd B.

---

