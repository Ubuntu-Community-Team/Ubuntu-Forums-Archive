---
title: "What is something you wish you learned sooner when starting out with Linux"
date: 2023-11-14
forum: Ubuntu, Linux and OS Chat
---

### Post by nebraskait308 on 2023-11-14
Hi everyone,


What is something you learned later on that would have made learning easier?

I've been taking an introductory Linux course this semester. We have done things such as installation, working with the filesystems, Bash scripts, and some administrative tasks.

---

### Post by TheFu on 2023-11-14
1. **To read manpages.**  They provide the answers and are already on your system. They are laid out as reference materials, so the the beginning is for people who already know something about each command, read farther to learn more and more details about the command.  Most manpages are sufficient. Some are works of art - like rsync and ssh. Those pages are freakin' amazing.

2. Unix file and directory permissions. I wasted about 6 months not really understanding them, until I "decided" to work on it and learn it by trying every possible combination of permissions while using 3 different userids and 2 groups.  It took me about 45 minutes and I'd wasted months for something that less than 1 hour of concentrated learning solved.

3. The Art of the Command line: [https://github.com/jlevy/the-art-of-command-line](https://github.com/jlevy/the-art-of-command-line)  ... though it didn't exist when I started.  I was being overwhelmed back then with so much new information.  About 10 yrs ago, I started reading it once a year. Almost always, there's something I didn't need before that was there, but with the new reading, it was great knowledge.

4. I use emacs as an editor initially, because vi was too hard.  My background was using ISPF (SPF Edit) on a mainframe to edit things, so Unix was completely new to me.  After about 6 months and using emacs' vi-mode more and more, I finally switched to using vi (now vim) as my main editor.  It was an organic change.  These were the days of tight disk space and my DEC Alpha workstation didn't have enough disk storage to have emacs on it.  I was using emacs from a SunOS system to edit files in my HOME.  remote X11 rocks and has been available over 30, if not 40 yrs.  I use Remote X11 over ssh constantly.  Kids these days don't realize you don't need a remote desktop to run and use other computers. This has been built-into X/Windows for many decades - seamless GUI program use across many different systems.  I look forward to when Wayland has this seamless capability.  Read today that Firefox is planning to ship Wayland-enabled versions only soon, which will break my workflow.  I run web browsers on a hardened system over remote X11, never on my local workstation.

5. regex.  That really isn't fair, because at my first Unix job, we used regex pattern matching extensively to create hyperlinks in documents. Some of those regex patterns were nearly 200 characters to get only what we needed for 1 side of the link.  Imagine creating hyperlinks from a book Index at the end to specific pages and from the Table of Contents into specific sections in a document.  If you don't know regex, it would be very difficult.  Just linking figures and tables can be complex.  Practice with **egrep**.

6. If you don't already understand the difference between _relative paths_ and _absolute paths_, this needs to be the #1 thing to learn.  MS-Windows, MacOS, MS-Dos, and all Unix have this idea and they work the same way, so I'm always surprised when I come across people who don't know it.  Earlier today, in these forums, there was someone who clearly didn't understand this concept. How do you deal with files and directories at all without this understanding?  I at a total loss.

---

### Post by VMC on 2023-11-14
#**4**. Above. I work for the Bell System.,Unix was developed there. Used 'ed', at the time 'vi' wasn't created. Needed 'sed' and other tools to rearrange what 'ed' couldn't. Then 'vi' appear. We thought we died and went to heaven. A visual editor! No more monkeying around with 'ed' and the gang! Never got the hang of 'emacs' so we didn't use it. I do know that 'emacs' was very popular though.

As far as regex goes, my bible is "Mastering Regular Expressions" now in its 3rd edition.

---

### Post by TheFu on 2023-11-15
Before X/Windows, we were stuck with a terminal and a shell.  

Emacs provided nearly a windowing system thanks to the ability to swap buffers for lots of different programs.  Much nicer than simple job control that's built into all the shells the last 30+ yrs.  I came after X/Windows. It was odd to be stuck on a console-only on my workstation.  If you don't have any windowing, you'll use emacs and buffers if your job is interactive.  Emacs wasn't bad for programming - a top buffer for editing and bottom buffer with gdb  and side buffer to run make after any changes.  The debugger would have the editor show the current line being executed in our C/C++ code. Better than trying to follow along in the code manually inside vi.   With X/Windows, we used xxgdb, which was almost as good as Borland C++, but on a real computer. ;)

But is learning vi really more important than reading manpages?  I suppose that's like saying I can help you pull in a fish, but never show you how to hook it, bait the line, or know where to go fishing ...

---

### Post by akay008 on 2023-11-16
terminal options and git you can read more from this

---

### Post by nebraskait308 on 2023-11-16
Thanks everyone for your responses. I really appreciate it!

---

### Post by The Cog on 2023-11-16
I wish I had learned to use sed and awk earlier. Both very handy command-line tools for text processing. Not for the absolute newby, but as you are getting a little familiar then you should at least put some effort into knowing what they are, and what they can do for you.

---

### Post by TheFu on 2023-11-16
> **The Cog said:**
> I wish I had learned to use sed and awk earlier. Both very handy command-line tools for text processing. Not for the absolute newby, but as you are getting a little familiar then you should at least put some effort into knowing what they are, and what they can do for you.

I only know the very basics of awk and find sed's regex engine to be too weak for many of my needs.  Back when I was just starting, I asked the local super admin what scripting language he suggested that I learn - for good or bad, he suggested perl.  There is nothing that sed or awk can do that perl can't do. Perl is heavier than both, but processing performance and capabilities for most "filters" don't make that very important. I'm happy I learned perl 30 yrs ago and have maintained that skill all this time.  

Perl has the most amazing regex engine of all that are available. It can do anything.  I'd add the regex from Ruby and Python as equally great, if you prefer those languages.  Actually, I love Ruby, but the performance being 10x less than the same perl code is a real problem.

I suppose some people would push for learning bash. bash scripting is a necessary thing, but it becomes unwieldy fast, making it unsuitable for more complex programming needs.  My rule of thumb is that when a bash script becomes longer than 1 page, it is time to stop and rewrite it in perl or ruby or python.  I strive to make all my programming "functions" less than 1 page. Learned that doing C/C++ coding. It too has served me well.  Humans can work on bite sized code fairly well and being able to fully test a function of 50 lines or less isn't a huge problem either. It is excellent programming practice.

So ... I don't wish I learned perl sooner, because when I learned it was just the right time, but it was definitely during my 1st year on Unix systems.  Knowing a nice, general purpose, scripting language is important to get more from your Unix/Linux time.

---

### Post by adamking999 on 2023-11-21
I want to know its security control mechanisms and how Ubuntu is different from the other typical OS ,like Redhat Linux, Mac OS and windows.

---

