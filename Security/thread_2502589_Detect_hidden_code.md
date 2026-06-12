---
title: "Detect hidden code"
date: 2024-11-20
forum: Security
---

### Post by netw844f on 2024-11-20
I am looking for a way to check text and code copied from AI tools, specifically from browsers. I use an AI tool in my browser, and sometimes I need to copy texts or code to my computer.

What tools can I use to check if there is hidden code inside the plain text output from AI websites?

This is a good example of what I'm talking about:

[https://briantracy.xyz/writing/copy-paste-shell.html](https://briantracy.xyz/writing/copy-paste-shell.html)

I used the software called 'file' on Ubuntu, and as output, I got this: index.html: HTML document, ASCII text

Supposedly, all characters inside this file are plain text. But is this enough to guarantee that this file doesn't have hidden code inside?

Thank you

---

### Post by TheFu on 2024-11-20
Just disable javascript.

Unless you disable full line input to your shell, since 2022, I think bash has prevented multi-line pastes that automatically run.  I always disable that feature for my sanity and since I'm pulling multi-line code from my personal wiki to run with a single select/paste operation.  

I seldom grab commands from random websites.  The recommended way to handle that is to paste into an editor first.

---

