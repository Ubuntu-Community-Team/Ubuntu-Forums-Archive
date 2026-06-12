---
title: "How to create a keyboard shortcut that executes a terminal command in clipboard"
date: 2021-06-29
forum: Ubuntu Application Development
---

### Post by d3mz on 2021-06-29
Most of my setup time is doing the following:
[LIST=1]
[*]Copy a command from the internet
[*]Paste into Terminal
[*]Go to the start of the line in the terminal and remove the $ prefix
[*]Run command
[*]Go back into the browser, and repeat for the next step.
[/LIST]

How do I change the above process to
[LIST=1]
[*]Copy a command on the internet
[*]Press a couple keystrokes that opens a terminal and runs the last copy from clipboard.
[/LIST]

Any pointers in the right direction would be helpful, I'm unfamiliar with the APIs and how to interface with them in Ubuntu

Thanks in advance!

---

### Post by TheFu on 2021-06-29
Doing what you seek is EXTREMELY dangerous.  Things you see on the internet are not always actually what is there.

The "best practice" for doing this stuff is to 
[LIST=1]
[*]have an editor open, 
[*]copy/paste the commands into the editor,
[*]look up any commands you don't know/understand,
[*]look up any options/switches in the command you don't know/understand,
[*]select the line(s) you wish to run from the editor, 
[*]paste those into a terminal
[*]Takes your chances.
[/LIST]
For making the look-up easier, consider using **explainshell.com**. Just paste each line into that.  There are issues with it, but mainly because it shows a manpage for each command that is recent, but not THE EXACT VERSION your system is likely to be using.  For that, we need to use the local manpages instead. manpages are part of each package, so the manpage on your system came with the version of the program(s) installed.  The good news is that most shell commands don't really change much from version to version.  OTOH, I was missing out on the -h options for df, du, and sort for way too many years after those were added. They changed my life.

In my beginning Linux class, I would setup a website that had some commands/steps listed and we'd work through this in class.  I'd embed a nasty bit of code both in plain site and hidden (thanks HTML!) into the steps.  Some classes would blindly run all the commands - every student.  Most would have at least 1 student who recognized the evil, in-your-face, command and would question it. Others would learn from that.  NOBODY, EVER, would see the embedded, nasty, HTML-hidden, bad commands until it was too late.

Don't trust anyone on the internet or any web pages on the internet to be perfect.

When I was in high school learning to drive, the driving instructor took us to down-town which had a bunch of 1-way streets. He started saying to turn left, right, which was normal - instructors always tell were to go. At one point he said to turn the wrong way down a 1-way street to make a point.  The driver is responsible, regardless of who is providing instructions. Clearly, that lesson stuck with me.  The same applies to running commands on a computer.

BTW, if there is a leading $, why not just skip copying it?  
[LIST]
[*]<cntl>-a goes to the beginning of a line in the default bash shell.  
[*]<cntl>-e goes to the end.  
[*]<cntl>-w deletes the word to the left.
[*]<cntl>-k deletes from the cursor to the end of the line.
[*]<cntl>-c cancels the current line completely.
[/LIST]

For more of these handy shortcuts, re-re-read this every year. [https://github.com/jlevy/the-art-of-command-line](https://github.com/jlevy/the-art-of-command-line)  Why yearly?  Because every year, you'll be ready to understand stuff you missed in prior years or simply didn't need.

---

