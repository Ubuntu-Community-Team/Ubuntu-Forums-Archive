---
title: "Windows text editor that can read Linux text files?"
date: 2008-01-17
forum: Windows
---

### Post by Murrquan on 2008-01-17
Hello, all! I've been using Gedit for most of my word processing needs in Fedora (and Ubuntu, when I was using it). It's a lot slicker than Notepad, and I love how it has tabbed browsing.

Trouble is, by default it saves text documents in a format that can't be read in Windows. I found this out when I sent one of my text files to my brother, only to have Windows think it was a virus and delete it!

I later figured out how to save documents in a Windows-readable format, but I still have hundreds of text files that Notepad can't read. Are there any free (preferably open-source!) Windows programs that can read normal Gedit text files?

---

### Post by vambo on 2008-01-17
Get hold of tofrodos from the repos. It provides the unix2dos and dos2unix programs to convert text files to/from one format to the other. More info here:
[http://www.thefreecountry.com/tofrodos/]("http://www.thefreecountry.com/tofrodos/")

---

### Post by someonestolemyname on 2008-01-17
I noticed the same last time I booted into Windows. I'm pretty sure that my favorite editor, PsPad, opened them just fine.

btw, it is an awesome editor.

---

### Post by SunnyRabbiera on 2008-01-17
well why dont you add a .txt to the end of your filenames?
works for me

---

### Post by Phrawm48 on 2008-01-19
I like the following because, among other things, you can specify that the end-of-line match either Windows or *ix conventions:

[Notepad++]("http://notepad-plus.sourceforge.net/uk/site.htm") is a good editor that gets a lot better if you go to *Notedpad++*'s plugins page and get all the cool plugins.  Under Ubuntu, I run Notepad++ under Wine.

[VIM]("http://www.vim.org/download.php") has versions exist for both *ix (of course) and Windows.

[jedit]("http://www.jedit.org/") requires a SUN-standard JDK to run under either *ix or Windows.  The payoff is that *jedit* is highly configurable, and has an amazing number of plug-ins.

Cheers & hope this helps,
Ric
SFO

---

### Post by Murrquan on 2008-01-20
I do save files with .txt extensions in Windows formats, when I want to send them to Windows-using friends. That doesn't help with all the mountains of text files I've already saved, though. ^.^;

Thanks for the help, everyone!

---

### Post by Majorix on 2008-01-20
If you want to convert a UNIX text file to DOS format, then open up the file in Windows, find Search&Replace or whatever that is called, and replace all \n's with \r\n. That will change the line endings to Windows format. You could then write a small script that does it for you for a large number of files. Hope it helps.

---

### Post by LaRoza on 2008-01-22
I use [http://www.crimsoneditor.com/](http://www.crimsoneditor.com/) perfect editor.

---

### Post by ddrplayer512 on 2008-01-22
Notepad++ is one of the best text editors for Windows. And it can handle files created with Mac and Linux just fine.

---

### Post by kernelCompile on 2008-01-27
Just about any Windows text editor other than Notepad will work with Linux/unix type text files. Even wordpad works, but be sure if you save  that you save as text files rather than in wordpad's format. 

Notepad is the text editor that comes free with Windows, and it's over-priced.

---

### Post by andrewjoy on 2008-01-29
Notepad++ Should work just fine.

I run it under wine too :P i am waiting for the day that sumone will port it to linux :P.

---

### Post by LaRoza on 2008-01-29
> **andrewjoy said:**
> Notepad++ Should work just fine.

I run it under wine too :P i am waiting for the day that sumone will port it to linux :P.

It has, under a different name I think.

---

