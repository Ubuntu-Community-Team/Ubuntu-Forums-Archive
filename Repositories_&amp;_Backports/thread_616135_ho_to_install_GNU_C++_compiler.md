---
title: "ho to install GNU C++ compiler?"
date: 2007-11-17
forum: Repositories &amp; Backports
---

### Post by arielsegal on 2007-11-17
Hi,
I'm using Gutsy. I'm learning C++ under Linux environment. 
How do I  install GNU C++ compiler?

---

### Post by scorp123 on 2007-11-18
sudo apt-get install build-essential

---

### Post by Kadrus on 2007-11-18
Open Terminal and type this :
```
sudo apt-get install g++

```

When you are finished installing try a simple C++ program..for example:
```
#include<iostream>
using namespace std;
int main()
{
cout<<"Hello World"<<endl;
return 0;
}

```

Save it hello.cpp
Open terminal and type
```
g++ hello.cpp
```

When it compiles bug free
Type in Terminal :
```
./a.out

```

And you should see:
Hello World

Or the program that you wrote..
Hope that helped :)

---

### Post by hondacodonbk on 2008-04-09
Hey,I did what you say and it work,but I do not understand something,please explain to me
1) why my following code do not work :
```

#include<iostream.h>
int maint()
{
    cout<<"hello \n";
    return 1;
}

```
but if I change #include<iostream.h> into #include<iostream> ( not add .h) and add "using namespace std; " and it work.So,what does "using namespace std;" mean ? and who does it used for ?
thank

---

### Post by sean_sf on 2009-02-06
Hello All,

I installed Ubuntu 8.10 on my computer a few hours ago, and this is my first post ... Whew ... What a night it's been.

Now, I'd like to compile my hello.cpp (that's how I found this forum). I tried both of these commands:

sudo apt-get install g++

sudo apt-get install build-essential

... And after executing, this was printed on the command screen (it was identical for both):

Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package g

(Or, for the latter)

E: Couldn't find package build-essential


Do I need to download something from the web? Any help would be greatly appreciated. 

Thanks.

--
Sean

---

### Post by PirateChef on 2009-02-06
I took a C++ class a loooong time ago, and all of our programs started with 
```
#include <iostream>
using namespace std;
```

I forget what namespaces are, precisely, but it's an important concept for programming. Try this article:
[http://en.wikipedia.org/wiki/Namespace_(computer_science)]("http://en.wikipedia.org/wiki/Namespace_(computer_science)")

Do a Google search for "C++ tutorial" for more. I'm sure there's tons of stuff out there.
 
> **hondacodonbk said:**
> Hey,I did what you say and it work,but I do not understand something,please explain to me
1) why my following code do not work :
```

#include<iostream.h>
int maint()
{
    cout<<"hello \n";
    return 1;
}

```
but if I change #include<iostream.h> into #include<iostream> ( not add .h) and add "using namespace std; " and it work.So,what does "using namespace std;" mean ? and who does it used for ?
thank

---

### Post by eye208 on 2009-02-06
> **sean_sf said:**
> Do I need to download something from the web? Any help would be greatly appreciated.
Make sure that your Ubuntu system can access the internet and that all the software repositories are enabled (System->Administration->Software Sources). Once this is configured properly, apt-get will download all the necessary packages automatically. "build-essential" is exactly what you need; it includes the C++ compiler.

---

### Post by swift108 on 2009-04-19
Thanks buddy, it works.

---

### Post by swift108 on 2009-04-19
Thanks for taking the time to nicely format your message. This worked immediately--very useful for someone like me who's in a hurry.

---

### Post by thisismespam on 2009-04-29
hi

i getting the error:
laptop@laptop:~$ g++ übung2.c 
übung2.c: In function »int main()«:
übung2.c:40: Warnung: zu wenig Argumente für Format
übung2.c:41: Fehler: »system« wurde in diesem Gültigkeitsbereich nicht definiert
laptop@laptop:~$ 

with the following program:
include <stdio.h> 
 
int monat2tag(int monat){ 
    int ergebnis=0; 
    switch (monat){ 
    case 1: 
    case 3:      
    case 5: 
    case 7:  
    case 8: 
    case 10:    
    case 12:        
    ergebnis=31; 
    break; 
    case 4: 
    case 6: 
    case 9: 
    case 11:                
    ergebnis=30; 
    break; 
    case 2: 
    ergebnis=29; 
    break; 
    default: 
    printf("fehlermeldung"); 
} 
printf("%d", ergebnis); 
return ergebnis; 
} 
 
 
int main(){ 
    int monat; 
    int tage; 
    printf("geben sie bitte den monat ein"); 
    scanf("%d", &monat); 
    printf("%d", monat); 
    tage=monat2tag(monat); 
    printf("%d", tage); 
    printf("monat hat %d tage\n",tage); 
    system("pause"); 
} 

so what have ive done wrong,
this program work under win xp

---

### Post by trebach on 2009-05-05
> **PirateChef said:**
> I took a C++ class a loooong time ago, and all of our programs started with 
```
#include <iostream>
using namespace std;
```

I forget what namespaces are, precisely, but it's an important concept for programming. Try this article:
[http://en.wikipedia.org/wiki/Namespace_(computer_science)]("http://en.wikipedia.org/wiki/Namespace_(computer_science)")

Do a Google search for "C++ tutorial" for more. I'm sure there's tons of stuff out there.
If you don't use ```
using namespace std;
``` then the compiler doesn't have a default class to look into when it sees a function. If you wanted to use the <iostream> functions without that line, you would have to add std:: before each function and object in iostream.

You may want to refer this question to the programming forum for more information.

---

### Post by Jiraiya_sama on 2009-05-05
> **thisismespam said:**
> hi

i getting the error:
laptop@laptop:~$ g++ übung2.c 
übung2.c: In function »int main()«:
übung2.c:40: Warnung: zu wenig Argumente für Format
übung2.c:41: Fehler: »system« wurde in diesem Gültigkeitsbereich nicht definiert
laptop@laptop:~$ 

with the following program:
```

include <stdio.h> 
 
int monat2tag(int monat){ 
    int ergebnis=0; 
    switch (monat){ 
    case 1: 
    case 3:      
    case 5: 
    case 7:  
    case 8: 
    case 10:    
    case 12:        
    ergebnis=31; 
    break; 
    case 4: 
    case 6: 
    case 9: 
    case 11:                
    ergebnis=30; 
    break; 
    case 2: 
    ergebnis=29; 
    break; 
    default: 
    printf("fehlermeldung"); 
} 
printf("%d", ergebnis); 
return ergebnis; 
} 
 
 
int main(){ 
    int monat; 
    int tage; 
    printf("geben sie bitte den monat ein"); 
    scanf("%d", &monat); 
    printf("%d", monat); 
    tage=monat2tag(monat); 
    printf("%d", tage); 
    printf("monat hat %d tage\n",tage); 
    system("pause"); 
} 
```

so what have ive done wrong,
this program work under win xp

First of all, you are using system, which is not defined by stdio.h(you need stdlib.h for that). Second of all, you are using pause, which I understand is a windows only command. This is discussed in the programming forum. Finally, please attempt to translate your error messages at least. You're much less likely to be helped if people have to take your error messages and run them through babelfish and the like.

To get functionality like "system("pause")" is rather easy.

```

char useless=getchar();

```

will do the same thing across all platforms.

---

### Post by Niemand000 on 2012-04-30
Now that I've installed GNU C++ Compiler, how do I access it?

---

### Post by DaviesX on 2012-04-30
```

gcc InputFile.c -o OutFileName

```

Or you might use an IDE like code blocks or something else

---

### Post by RintheGreat on 2012-04-30
Hi everyone,
I've just upgraded to Ubuntu 12.04 and gcc does not work any more because of this problem:

/usr/local/bin/ld: this linker was not configured to use sysroots
collect2: ld returned 1 exit status

Can anyone show me how to fix this problem?

Thank you very much!

---

### Post by DaviesX on 2012-05-01
Have you tried re-installing it ?

```

sudo apt-get install gcc build-essential

```

---

### Post by RintheGreat on 2012-05-01
Yes, I've tried that many times but it does not fix the problem.

---

### Post by DaviesX on 2012-05-01
Do you use makefile or just simply gcc a file ?

---

### Post by RintheGreat on 2012-05-01
I just gcc a file. But makefile does not work too.

---

### Post by DaviesX on 2012-05-02
I have got this
[https://bugs.launchpad.net/ubuntu/+source/gcc-4.4/+bug/582645](https://bugs.launchpad.net/ubuntu/+source/gcc-4.4/+bug/582645)

You might install it as a root, if that doesn't work, you may compile it yourself :mad:

I have got many problems with 12.04 before because I was upgrade from other version. However, after I make a fresh install, it works fine. You might have a trial to re-install a fresh Ubuntu to see if this can be solved :)

---

