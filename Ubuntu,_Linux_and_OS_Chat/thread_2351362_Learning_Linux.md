---
title: "Learning Linux"
date: 2017-02-02
forum: Ubuntu, Linux and OS Chat
---

### Post by zeca77 on 2017-02-02
Hello,
I installed ubuntu recently, and I'm getting used to it, and liking it. The main reason why i installed ubuntu is because i want to be a programmer, and I was getting kinda tired of windows, so I thought it was a good idea to change. Anyway, after learning the basics of linux, like using the terminal and knowing where everything is, i dont actually know what my next step as a linux user might be. The only thing that comes to my mind is programming, and i quite enjoy the idea, but besides not knowing absolutely nothing about programming, there isn't really a comprehensive guide, that I found, for people who aspire to be programmers. 
What should I do next?

---

### Post by Bashing-om on 2017-02-02
zeca77; Hello;

> **zeca77 said:**
> Hello,
I installed ubuntu recently, and I'm getting used to it, and liking it. The main reason why i installed ubuntu is because i want to be a programmer, and I was getting kinda tired of windows, so I thought it was a good idea to change. Anyway, after learning the basics of linux, like using the terminal and knowing where everything is, i dont actually know what my next step as a linux user might be. The only thing that comes to my mind is programming, and i quite enjoy the idea, but besides not knowing absolutely nothing about programming, there isn't really a comprehensive guide, that I found, for people who aspire to be programmers. 
[color=green]What should I do next?[/color]

Learn what bash is !
[http://mywiki.wooledge.org/FullBashGuide](http://mywiki.wooledge.org/FullBashGuide)

[INDENT][INDENT]one way to go
[/INDENT][/INDENT]

---

### Post by cariboo on 2017-02-02
This really not a support question. Moved.

---

### Post by oldrocker99 on 2017-02-02
Practically every programming language is available in Linux: Python, Java, Ruby, C, C++, and many more. 

To get started in compiling programs, download the wine .tar.gz source code file from [https://www.winehq.org/announce/2.0](https://www.winehq.org/announce/2.0) and extract it:```
tar -xvf wine-2.0.tar.bz2
```

Enter the resulting folder.

Then make sure you can compile it:```
sudo apt-get build-essential
```

Then type```
./configure
```

There is almost always a "configure" file. The script will see what you have and what you don't, and you MAY have to install some dependencies before it will configure and produce a Makefile. Then:```
make
sudo make install
```

That will compile and install the program. Compilation of wine will take a while. Don't worry about compiler error messages. This will get your feet wet and give you the latest wine version.

---

### Post by ian-weisser on 2017-02-02
One next step for a Linux user who knows where everything is: Become a community contributor. Write documentation. Triage bugs. Test patches. Answer support questions.

These activities will introduce you to other community members, including fellow programmers who can help review your code and mentor you.

---

