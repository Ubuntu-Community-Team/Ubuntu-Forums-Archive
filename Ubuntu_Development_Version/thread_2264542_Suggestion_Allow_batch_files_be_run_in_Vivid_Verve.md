---
title: "Suggestion: Allow batch files be run in Vivid Vervet."
date: 2015-02-08
forum: Ubuntu Development Version
---

### Post by NunoLava1998 on 2015-02-08
(I know this is the wrong place, but i dont know where to put suggestions for the next build of ubuntu!)
So i want ubuntu 15.04 vivid vervet be able to run batch files from windows without using wine. With the label/goto bug (4 and more labels will mess up goto command) fixed, and other bugs fixed like if you put way too many echo's and wine runs it cmd will close instantly or just give errors that the text that was supposed to show is not a command/batch file.

Could developers do this in the next build of ubuntu vivid vervet and after?

---

### Post by oldos2er on 2015-02-08
Why not convert your batch files to shell scripts?

---

### Post by NunoLava1998 on 2015-02-08
Well, can the developers do it anyway?

---

### Post by zika on 2015-02-08
Would not that be a security issue?

---

### Post by NunoLava1998 on 2015-02-08
Security issue? Batch is a shell/scripting language. How it would cause harm?

---

### Post by grahammechanical on 2015-02-08
The design decisions for the next release of Ubuntu were taken months ago. Suggestions like these should be aimed about 2 releases in the future. Say towards implementation in 15.10 or even 16.04.

The place to put suggestions like this is at the Ubuntu Online Summit. You may get a developer interested in doing the work. Basically, you desire that the Bash command line interpreter that is used in Linux be modified to run Windows batch commands. Ubuntu engineers do not have responsibility for Bash. Even if a Ubuntu developer was to do the work the changes would need to be accepted and approved by the developers who maintain Bash.

You might be interested in this but I do not think so. I give it anyway.

[http://stackoverflow.com/questions/17510688/single-script-to-run-in-both-windows-batch-and-linux-bash](http://stackoverflow.com/questions/17510688/single-script-to-run-in-both-windows-batch-and-linux-bash)

Regards.

---

### Post by ajgreeny on 2015-02-08
Just acting devil's advocate here, and I'm curious, but what is the point of running a batch file in Linux?

This is Linux after all, not Windows!

Perhaps I've missed something that is obvious to others?

---

### Post by NunoLava1998 on 2015-02-08
1:
Batch programs (there are very amazing ones.) with compatiblity with linux would be good feature.
2:
Batch programmers (like me) Want to code batch in linux
3:
Games would not overheat computer. Batch games would be less than 1 MB, even batch os which are around 1-100KB.

---

### Post by buzzingrobot on 2015-02-08
Since Windows batch files, whether Powershell or the traditional DOS-vintage style, call Windows executables and expect to leverage and use environmental variables that exist only in Windows, giving Ubuntu or any other Linux the ability to interpret them seems to be a nonstarter.

In theory, it might be possible to create something that attempted on-the-fly translation of Windows batch code into a Linux shell script. Again, given their assumption that they are running on Windows, I suspect only the very simplest scripts could be translated and successfully executed.

---

### Post by sudodus on 2015-02-08
> **NunoLava1998 said:**
> 1:
Batch programs (there are very amazing ones.) with compatiblity with linux would be good feature.
2:
Batch programmers (like me) Want to code batch in linux
3:
Games would not overheat computer. Batch games would be less than 1 MB, even batch os which are around 1-100KB.

Before I learned linux I was also using DOS batch programming (in PCs even before Windows). Believe me, bash is much more powerful and flexible, and still 'only' a script language. I know about python, that it is even more efficient, but I have not learned it. So in order to make efficient scripts in linux you should learn one of these program languages instead of that of Windows. Many things are similar, it is really not that hard to switch, and I think that you (as well as I) will find that bash (or if you prefer to skip directly to python) is much more powerful and fun to use.

Try to use ***mkusb*** and look at the file itself, a script file, that is portable between different linux distros and versions because bash is the same :-)

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

[http://phillw.net/isos/linux-tools/mkusb/mkusb](http://phillw.net/isos/linux-tools/mkusb/mkusb)

But a bash script is often a simple one-line file or a rather short script file like you might expect from your experience with bash scripts. You can find many ***good tutorials about bash and python via the internet***. For example you can start here

[https://help.ubuntu.com/community/CategoryCommandLine](https://help.ubuntu.com/community/CategoryCommandLine)

[https://help.ubuntu.com/community/Beginners/BashScripting](https://help.ubuntu.com/community/Beginners/BashScripting)

and select a tutorial or guide that suits your way of thinking. You are also welcome to ask questions here at the Ubuntu Forums, if you get stuck when you are programming.

---

### Post by oldos2er on 2015-02-08
> **NunoLava1998 said:**
> Well, can the developers do it anyway?

You'd have to ask them. I'd try the discussion mailing list: [https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-discuss](https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-discuss)

---

