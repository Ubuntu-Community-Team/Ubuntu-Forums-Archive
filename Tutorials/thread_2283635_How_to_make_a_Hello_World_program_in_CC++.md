---
title: "How to make a Hello World program in C/C++"
date: 2015-06-23
forum: Tutorials
---

### Post by aaronsantiago89 on 2015-06-23
Hello there, it's Aaron, and I'm here to show you how to make a Hello World program in the C and C++ programming languages.

First, go to the text editor of your choice, but personally, in my opinion, I recommend a IDE like Code::Blocks or even MonoDevelop (Which requires the Mono Runtime which you can get off Ubuntu Software Centre.) Then input this into the text editor window below. *NOTE IN C.

```

#include <stdio>

int main(char argc, int argv[1])
{
       printf("Hello World!\n");
; return 0;
}

```


Then save this as a .c in the folder of your choice.


But if you want to make a hello world program in C++, however, which, in my opinion, I don't like very much.

Repeat step 1, but this time, input the code below, instead of the code above:


```

#include <iostream>
using namespace std;

int main()
{
   std::cout << "Hello World" << std::endl;

; return 0;
}

```

This time, for step 3, save it ***_AS A .CPP _***or it will not compile with GNU GCC or any compiler in general.


Word of advice, I heavily suggest putting a semicolon both before and after the return statement, as compiling it without that will result in a error if you try to compile it and/or run it.


):P Aaron out!!!!

---

### Post by steeldriver on 2015-06-23
What error do you get exactly if you remove the semicolon before the return statement?

The arguments to `main` should have types

```

int main([COLOR=#0000ff]**int**[/COLOR] argc, [COLOR=#0000ff]**char ***[/COLOR]argv**[COLOR=#0000ff][][/COLOR]**)

```

I think. The first is a count of the arguments, and the second is a pointer to an array of character strings representing the arguments themselves.

And shouldn't [FONT=courier new]<stdio>[/FONT] be [FONT=courier new]<stdio[COLOR=#0000ff]**.h**[/COLOR]>[/FONT]?

Also from the man pages, the recognized C++ extensions are

```

       file.cc
       file.cp
       file.cxx
       file.cpp
       file.CPP
       file.c++
       file.C
           C++ source code that must be preprocessed.  Note that in .cxx, the
           last two letters must both be literally x.  Likewise, .C refers to
           a literal capital C.

```

although in fact you can use any extension so long as you indicate the language using the -x option.

---

### Post by Ricial on 2015-07-18
Does Code::Blocks have the same functions and features as DevC++ offers?

---

### Post by brian-mccumber on 2015-09-07
If you're using namespace std; you do not have to include the std:: in this line. - 
std::cout << "Hello World" << std::endl;

You can just write it like - cout << "Hello World" << endl;

---

### Post by flaymond on 2015-09-10
Personally, I think it's better with C -

[php]#include <stdio.h>

int main(int argc, char *argv[])
{
    puts("Hello, world!");                 // or printf("Hello, world!\n");

    return 0;
}
[/php]

and personally for C++ -

[php]#include <iostream>

int main(int argc, char *argv[])
{
    std::cout << "Hello, world\n";

    return 0;
}

[/php]

then you can compile both of them with

```
make filename
```

or ```
 g++ yourfilename.cpp -o yourfilename       # or g++ yourfilename.c -o yourfilename 
```


For IDE, I agreed with Aaron for Code::Blocks, it's nice and elegant, also cross platform(says you want to share the project structure so other people on different platforms can compile it too).

and Anjuta if I want to dealing with Vala + GTK or gtkmm. Anyway, I just use vim for general editing.

---

