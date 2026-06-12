---
title: "Running ANSI C programs in the desktop"
date: 2014-11-16
forum: Ubuntu Application Development
---

### Post by pauls2 on 2014-11-16
I am writing code for a ballistics program in ANSI C. I continue to compile and run it in a terminal window from Geany and it all works well.'

What do I have to do to make the executable run from the desktop - or is it even possible with ANSI C?

I am and old DOS software guy who hasn't written anything in more years than I wrote code.
I am new to ANSI C (learning a lot) and fairly new to Ubuntu - running 14.04.1 on a 64 bit system using an I5 quad core Intel processor.

Help?

Paul

---

### Post by sudodus on 2014-11-16
If the program is compiled and linked, you can just make its file executable with chmod (maybe it is already executable). The default name is a.out, but you can change the file name with the option

```
-o filename
```

```
chmod ugo+x a.out
```
or
```
chmod ugo+x filename
```

Check with

```
ls -l
``` in the directory where you have the file.

*Edit* {
example: ```

ls -l /bin/cp
-rwxr-xr-x 1 root root 120708 nov 19  2012 /bin/cp

```
In this case x indicates that it is executable for user, group, and others
}

Then run it from a terminal window with the command

```
./a.out
```
or
```
./filename
```

(You need no exe extension in linux.)

---

### Post by pauls2 on 2014-11-16
As I understand this, it opens a terminal window and runs it there.

I am hoping to run it without the terminal window - right from the desktop - without a terminal window.

Is that possible?

---

### Post by steeldriver on 2014-11-16
What kind of program is it? You can make a [desktop launcher]("https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles") - however if it needs standard input / output it will still need to run in a terminal (Terminal=true)

---

### Post by pauls2 on 2014-11-16
The program is (will be) a 6 degrees of freedom exterior ballistics program and it has LOTS of input and output that I will be releasing under the open source rules.

So, does that mean that it must be run in a terminal window only?

Since it is ANSI C, there are no fancy menus, pop-up windows or anything but text input and output to the screen and file access to the drive within the current directory.

I am far from done with the software but every time I add a function or change the code I compile, make and run the changed code to ensure it is error free and looks as it should.

I guess I will put up with the terminal window if that is the only way to run it, I am not sure that most will use it if it must be run in a terminal window. (but then without all the drop-down menus and pop-up windows most people won't want to use it anyway)

---

### Post by pauls2 on 2014-11-16
Here is what I get when I try to run it:

```

   paul@paul-desktop:~$ cd Documents/C-files 
 paul@paul-desktop:~/Documents/C-files$ ls 
 EXHAUST2.C  EXTBAL50.C  ExtBal6.c  LAWSON.CPP  TITLESCR.C 
 EXTBAL43.C  ExtBal6     ExtBal6.o  SCANIT.C 
 paul@paul-desktop:~/Documents/C-files$ ls -l 
 total 304 
 -rw------- 1 paul paul    57 May  3  2010 EXHAUST2.C 
 -rw------- 1 paul paul 72225 Mar 15  1993 EXTBAL43.C 
 -rw------- 1 paul paul 78855 Jan 18  2012 EXTBAL50.C 
 -rwxrwxr-x 1 paul paul 26038 Nov 15 21:12 ExtBal6 
 -rw------- 1 paul paul 26077 Nov 16 11:38 ExtBal6.c 
 -rw-rw-r-- 1 paul paul 41632 Nov 15 21:12 ExtBal6.o 
 -rw------- 1 paul paul 35993 Nov 12  1993 LAWSON.CPP 
 -rw------- 1 paul paul  5334 Dec 20  1991 SCANIT.C 
 -rw------- 1 paul paul  3851 Sep 25  1993 TITLESCR.C 
 paul@paul-desktop:~/Documents/C-files$ ExtBal6 
 ExtBal6: command not found 
 paul@paul-desktop:~/Documents/C-files$  

```

I am in the directory in which the file is in. Do I need to precede the filename with "./"?

It runs fine when I enter "./ExtBal6" so I need to identify the directory. What I am understanding is that this is the only way to run the program (inside the Terminal window) - and that there is no way to run it in the GUI desktop.
Can you confirm this?

---

### Post by steeldriver on 2014-11-16
Yes, if the directory ~/Documents/C-files is not on your executable search path ($PATH environment variable) you need to specify the path explicity, either as a relative path

```

./ExtBal6

```

or an absolute path
```

/home/paul/Documents/C-files/ExtBal6

```

---

### Post by sudodus on 2014-11-17
*steeldriver* fixed the issue. Sorry that I missed the ./ prefix for a local executable file (or giving the full path).

And alternative is to put the executable file in PATH. One good way is to create an own bin directory ```
mkdir ~/bin
```
The next time you reboot, it will be recognized and included in PATH, so if you link or move your executable file(s) to **~/bin**, it can be run without any prefix

so ```
filename
``` works, no need to type ```
./filename
```

---

### Post by pauls2 on 2014-11-18
Thanks for the help! My question has been answered. I still have a lot to do before it will be ready to use.
When I complete the software I will be back to get help making it into a package that can be added to the software list.
Maybe some interested parties can port it to other OS's and maybe phones and such.

---

