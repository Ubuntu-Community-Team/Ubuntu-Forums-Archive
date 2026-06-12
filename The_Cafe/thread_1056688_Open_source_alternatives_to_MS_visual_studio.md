---
title: "Open source alternatives to MS visual studio?"
date: 2009-02-01
forum: The Cafe
---

### Post by Colro on 2009-02-01
I'm taking a C++ class, and really don't want to use MS visual studio. What are some of the best open source alternatives? I'd greatly prefer something that has both windows and linux versions, as I'd like to use it on my laptop and at home.

Thanks in advance for any suggestions :)

---

### Post by vikramaditya on 2009-02-01
[http://www.osalt.com/codeblocks](http://www.osalt.com/codeblocks)
[http://www.osalt.com/monodevelop](http://www.osalt.com/monodevelop)

have fun! :)

---

### Post by igknighted on 2009-02-01
You could use Scite in both linux and windows, but I would recommend using Notepad++ in windows, then either gedit or kate/kwrite in linux.  You should then install Cygwin in windows (think wine, but a linux environment on windows) which comes with gcc to compile, and of course use gcc on linux as well.

---

### Post by RiceMonster on 2009-02-01
I just write my C++ in vim and compile it with g++.

---

### Post by hessiess on 2009-02-01
> **ricemonster said:**
> i just write my c++ in vim and compile it with g++.

+1

---

### Post by HolyJoe on 2009-02-01
> **Colro said:**
> I'm taking a C++ class, and really don't want to use MS visual studio. What are some of the best open source alternatives? I'd greatly prefer something that has both windows and linux versions, as I'd like to use it on my laptop and at home.

Thanks in advance for any suggestions :)

I favor vim+gcc on linux, and mingw on windows. If u prefer something like MS's VS I think u missing ur way.

---

### Post by phrostbyte on 2009-02-01
Here is some GTK+ options if you prefer:
[apt://geanie]("apt://geanie") - Good for small C++ projects (like a few files), this is probably best option for school
[apt://eclipse]("apt://eclipse") - Good for large C++ projects with many developers, this is a heavy IDE kinda like VS (except it supports many more languages)

This is all opinion by the way.

---

### Post by samjh on 2009-02-01
Eclipse and Netbeans are probably the closest to MS Visual Studio.

CodeBlocks, KDevelop, Anjuta, Monodevelop and others provide a similar capability in more specialised development fields (eg. C/C++ for CodeBlocks, KDevelop for KDE-related stuff, Anjuta for Gnome-related stuff, Monodevelop for Mono-related stuff, etc).

---

### Post by mr.propre on 2009-02-01
My advice, use windows MS Visual Studio if you are going to program windows (.NET) based program in class. It's more important that you learn how to program Object-oriented and that's hard enough. After you have learn that, you always can decide to start programming under Linux.

I'm in the same situation as you, but whit Visual Basic.NET, it's my second year and for the moment I keep it to Visual Studio, after I master that I probably will start with c++ and after that I will start under Linux.

---

### Post by directhex on 2009-02-01
> **mr.propre said:**
> My advice, use windows MS Visual Studio if you are going to program windows (.NET) based program in class. It's more important that you learn how to program Object-oriented and that's hard enough. After you have learn that, you always can decide to start programming under Linux.

I'm in the same situation as you, but whit Visual Basic.NET, it's my second year and for the moment I keep it to Visual Studio, after I master that I probably will start with c++ and after that I will start under Linux.

```
jms@destiny:/tmp$ cat >>hello.vb <<EOF
> Module Example
>     Sub Main()
>         System.Console.WriteLine("Hello World!")
>     End Sub
> End Module
> EOF
jms@destiny:/tmp$ vbnc hello.vb 
 version  (Mono 2.0 - r)



Assembly 'hello, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null' saved successfully to '/tmp/hello.exe'.
Compilation successful
Compilation took 00:00:01.0788460
jms@destiny:/tmp$ mono hello.exe 
Hello World!
```

Nobody's forcing you not to use VB.NET on Linux if you want to use it

---

### Post by Johnsie on 2009-02-01
There are 'alternatives' but there are no 'equivalents'. Visual Studio is very comprehensive compared to the Open Source alternatives. Eclipse is ok but doesn't come close.

If you're wanting to program VB then I would recommend checking out Gambas or RealBasic for Linux. I have personally written few Gambas programs and kinda liked it. It's not quite as fully featured ad VB6 or VB.NET but is ok.

I would also recommend looking into PHP and Java as alternative programming languages that are worth learning. C++ is good too, but for most projects you will be fine with VB, PHP or Java.

---

### Post by gnomeuser on 2009-02-01
MonoDevelop 2 is really nice, easy to use and yet very powerful.

---

### Post by directhex on 2009-02-01
> **gnomeuser said:**
> MonoDevelop 2 is really nice, easy to use and yet very powerful.

And no, not in Ubuntu yet. Give it a couple of weeks

---

### Post by MaxIBoy on 2009-02-01
I'm pretty sure vim has this feature as well, but in Emacs, the command to drop into a shell is M-x, then type eshell. (M means meta, which is usually the alt key.) Then type "exit" when you're done. There are other commands for opening different files in the same copy of Emacs and switching between them. So you can have a full project in multiple source code files, compile, run, debug, code, and so on, without leaving Emacs. 

Emacs is-- well, let's put it this way, Emacs is very full-featured. It's got an Email client, Tetris, and I think even a web browser, all built in. You can use Emacs for days without closing it. 

You might say it's bloated, and you wouldn't be wrong, but that doesn't mean it isn't amazing.

---

### Post by rkulp on 2009-02-03
> **directhex said:**
> And no, not in Ubuntu yet. Give it a couple of weeks

I just installed MonoDevelop 2 Alpha 1 after seeing

[http://ubuntuforums.org/showthread.php?t=1058151&highlight=monodevelop](http://ubuntuforums.org/showthread.php?t=1058151&highlight=monodevelop)

The PPA reference has both the Alpha 2 unstable and Alpha 1 releases.

It is worth a look. I primarily use VS 2005 but want to be able to develop for multiple platforms so am very slowly learning Mono.

---

### Post by directhex on 2009-02-03
> **rkulp said:**
> The PPA reference has both the Alpha 2 unstable and Alpha 1 releases.

Imagine how much faith I have in a PPA calling itself "Ubuntu Mono Maintainers" operated by someone who has never even contacted the Ubuntu Mono maintainers. Or the Debian ones.

---

### Post by RiceMonster on 2009-02-03
> **MaxIBoy said:**
> I'm pretty sure vim has this feature as well, but in Emacs, the command to drop into a shell is M-x, then type eshell. (M means meta, which is usually the alt key.) Then type "exit" when you're done. There are other commands for opening different files in the same copy of Emacs and switching between them. So you can have a full project in multiple source code files, compile, run, debug, code, and so on, without leaving Emacs. 
Yeah, you edit and manage multiple files in vim as well. You can open them in tabs, or you can split the screen with multiple files. You can also run shell commands from vim by doing :!command.

> Emacs is-- well, let's put it this way, Emacs is very full-featured. It's got an Email client, Tetris, and I think even a web browser, all built in. You can use Emacs for days without closing it. 

Yeah, that's why I don't like it. Who needs to browse the web and play tetris in an editor? In the end though, it's best to try them both and use what you prefer.

Edit: If you want a full featured IDE instead of a simple editor (that's what I like) you can try NetBeans.

---

### Post by jimi_hendrix on 2009-02-03
vim

---

### Post by Bölvaður on 2009-02-03
For school projects Geany should be well good enough. You can edit the compile, build and run scripts.

---

### Post by ThePinkPoo on 2009-02-03
I know a lot of people use Dev-C++:
[http://www.bloodshed.net/devcpp.html](http://www.bloodshed.net/devcpp.html)

---

### Post by mattman85 on 2009-02-03
> **Colro said:**
> I'm taking a C++ class, and really don't want to use MS visual studio. What are some of the best open source alternatives? I'd greatly prefer something that has both windows and linux versions, as I'd like to use it on my laptop and at home.

Thanks in advance for any suggestions :)
how are your computer specs?  b/c if you *really* wanted to stick with VStudio so that you could follow along with class notes while at home (and provided you have a spare copy of XP somewhere available), you could install [VirtualBox]("http://virtualbox.org"), then install XP onto a virtual machine.  Then, if you are a Computer Science student, go to [dreamspark.com]("http://dreamspark.com") and register, then you can get the full version of Visual Studio 2008 for FREE because you are in a CS degree program.  You will have to verify that you are in college first.  its an option..  I have all of the Dreamspark files, just because I was in your situation last year..

---

### Post by phrostbyte on 2009-02-03
There really isn't that important in Visual Studio for C++ development. If you are doing C++ development,  then really Geany should be more then enough to be very productive. But if you want a big fat IDE on Linux Eclipse is pretty good, and does things that VS can't do (like actually suggest and then automatically fix many common problems).

---

### Post by Bölvaður on 2009-02-03
> **phrostbyte said:**
> But if you want a big fat IDE on Linux Eclipse is pretty good

Can you point me out to a tutorial on how to start a new C++ project on eclipse. I used to use it for java few years back but now I am unable to get it working with C++ (with the eclipse-cdt package for having c++ in eclipse).
I tried to follow a howto for windows on their wiki but somehow I find it more difficult to start a c++ project in eclipse than making L-system displaying program with opengl in Geany. I even spent equally long time on both things.. trying to get c++ in eclipse to work and making that program read L-systems from a config file and displaying them.

---

### Post by Tomosaur on 2009-02-03
> **Bölvaður said:**
> Can you point me out to a tutorial on how to start a new C++ project on eclipse. I used to use it for java few years back but now I am unable to get it working with C++ (with the eclipse-cdt package for having c++ in eclipse).
I tried to follow a howto for windows on their wiki but somehow I find it more difficult to start a c++ project in eclipse than making L-system displaying program with opengl in Geany. I even spent equally long time on both things.. trying to get c++ in eclipse to work and making that program read L-systems from a config file and displaying them.

If you have the necessary plugins / modules installed, then you should just be able to switch to the C/C++ perspective and start coding. Look near the top right of your Eclipse window, you should see a button labelled 'Java'. Just to the left of that there is an icon which looks like a 'new window' icon. Click there, select 'other', then choose C/C++ from the menu.

---

### Post by jay576 on 2009-02-03
I've used dev-c++, dev-pascal, eclipse, notepad++, and bluej on windows based systems and geany, eclipse and bluej on linux.

Most of my java based classes at the university level try and get students to use eclipse.  It is pretty bulky piece of software but it is extremely nice and advanced but may be to feature rich for what you want.  It is mainly used for fairly large projects.
Geany is probably all you would need and will run a lot faster than eclipse.  I haven't used it much but it looks like a decent IDE.

You could always go the route of a text editor and compiler too but that isn't as user friendly

---

