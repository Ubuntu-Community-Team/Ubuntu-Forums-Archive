---
title: "Difference between C (gcc) and C++ (g++), in a practical way?"
date: 2012-08-05
forum: The Cafe
---

### Post by honeybear on 2012-08-05
Hi,

I would like to know what is the difference between coding towards gcc compiling or g++ compiling. 

It looks like very similar from a point of view ?

I have no background with g++. gcc rather.

Best Regards

---

### Post by Bachstelze on 2012-08-05
C and C++ are different languages. It's like asking the difference between English and German.

---

### Post by ranger1021994 on 2012-08-05
C++ is feature rich as compared to C.
However the base of C++ is derived from C.

---

### Post by vexorian on 2012-08-05
In c++ you can do this:

```

std::string x = "aaa";
std::string y = "bbb";
x = x + y;
std::cout << x << std::endl;

```

In c it looks like this:
```

const char*x = "aaa";
const char*y = "bbb";
char buf[100];
strcpy(buf, x);
strcat(buf, y);
printf("%s\n", buf);

```

But in order to use the c++ one correctly, you must first understand the c one.

---

### Post by MG&amp;TL on 2012-08-05
> **vexorian said:**
> In c++ you can do this:

```

std::string x = "aaa";
std::string y = "bbb";
x = x + y;
std::cout << x << std::endl;

```In c it looks like this:
```

const char*x = "aaa";
const char*y = "bbb";
char buf[100];
strcpy(buf, x);
strcat(buf, y);
printf("%s\n", buf);

```But in order to use the c++ one correctly, you must first understand the c one.

Uh-uh. I've used the C++ one for longer than the C one. And to be honest, the C++ one is easier.[]("http://www.wikivs.com/wiki/C_vs_C%2B%2B")

---

### Post by vexorian on 2012-08-05
C strings are also the root of many security issues. If let's say y was input by the user, and the user puts more than 99 characters, you might be able to write arbitrary data to the program's memory. A good hacker would be able to convert this skill into code injection. 

[http://en.wikipedia.org/wiki/Buffer_overflow](http://en.wikipedia.org/wiki/Buffer_overflow)

---

### Post by honeybear on 2012-08-05
```
g++ test3.cpp -o test3 -lSDL -lSDL_image  -lSDL_ttf
```


thanks... but this code, is it c++ or C ? I use g++.
```


//The headers
#include "SDL/SDL.h"
#include "SDL/SDL_image.h"
#include "SDL/SDL_ttf.h"
#include <string>



//Screen attributes
const int SCREEN_WIDTH = 640;
const int SCREEN_HEIGHT = 480;
const int SCREEN_BPP = 32;

bla... 

int main( int argc, char* args[] )
{

        SDL_Event event;
        int game_score,game_done;


        //Quit flag
        bool quit = false;

        //Keep track of the current frame
        int frame = 0;

        //Whether or not to cap the frame rate
        bool cap = true;




        //Initialize
        if( init() == false )
        {
                return 1;
        }

int main( int argc, char* args[] )
{

        SDL_Event event;
        int game_score,game_done;


        //Quit flag
        bool quit = false;

        //Keep track of the current frame
        int frame = 0;

        //Whether or not to cap the frame rate
        bool cap = true;




        //Initialize
        if( init() == false )
        {
                return 1;
        }

bla


```

---

### Post by anewguy on 2012-08-05
That appears to be standard C.  You can use gcc with it.  I'm not positive, but I would think you should be able to compile it using g++ as well, since C++ is based in C.  I don't know if you are familiar with the concept of object-oriented programming and function overloading, but the object-orientation, the declaration of some variables, etc., is the main difference between the 2.

---

### Post by 3177 on 2012-08-05
> **Bachstelze said:**
> C and C++ are different languages. It's like asking the difference between English and German.
terrible answer

---

### Post by vexorian on 2012-08-05
That code is C++.

```

#include <string>
```

---

### Post by jerome1232 on 2012-08-05
> **3177 said:**
> terrible answer

Okay, they are two different languages, it's like asking the difference between English and Latin.
:guitar:

---

### Post by anewguy on 2012-08-06
> **vexorian said:**
> That code is C++.

```

#include <string>
```

Thanks for catching that - I missed a few things in there!

---

### Post by markbl on 2012-08-06
> **jerome1232 said:**
> Okay, they are two different languages, it's like asking the difference between English and Latin.
:guitar:
Another terrible answer ... :confused:

---

### Post by jerome1232 on 2012-08-06
> **markbl said:**
> Another terrible answer ... :confused:
 
Whoosh!

English is derived from Latin, C++ is de... oh never mind, It was a bad joke anyways

---

### Post by honeybear on 2012-08-06
> **jerome1232 said:**
> Whoosh!

English is derived from Latin, C++ is de... oh never mind, It was a bad joke anyways

C is derived from B language. 

In the C museum I tried to read about B language. Never found much.  I am a bit curious what is the history of the B language. All from these languages came from Dennis alone?

---

### Post by markbl on 2012-08-07
> **jerome1232 said:**
> 
English is derived from Latin, C++ is de... oh never mind, It was a bad joke anyways
Yeah, but it is a poor analogy. C++ is essentially a superset of C.  Anybody who can read/write C++ can read/write C. I a native English speaker but I can't read Latin!

---

### Post by vexorian on 2012-08-07
C++ is merely "kind of" a superset of C. Sure it started like that. But there's C code that won't run in C++.
[http://en.wikipedia.org/wiki/Compatibility_of_C_and_C%2B%2B](http://en.wikipedia.org/wiki/Compatibility_of_C_and_C%2B%2B)

---

### Post by vexorian on 2012-08-07
Edit: betrayed by slow connection, unintentional duplicate.

---

### Post by honeybear on 2012-08-09
I must say that I dont like that much the object oriented coding. Old fashion sounds easier to me. Are they others with similar pref., i.e. towards C?

---

### Post by MG&amp;TL on 2012-08-09
> **honeybear said:**
> I must say that I dont like that much the object oriented coding. Old fashion sounds easier to me. Are they others with similar pref., i.e. towards C?

Yes, I find it a little confusing and counter-intuitive, but try creating something that benefits from OO (game programming is a commonly-used example) in C, then try in C++ and see the advantage. There is good reason for using C++ and OO languages.

---

### Post by steeldriver on 2012-08-09
I had a real-world example a couple of years back - we were simulating the performance of some digital decoder hardware, and needed versions to work for both fixed-point and floating-point hardware implementations, and for both binary and non-binary code symbols. 

In C that would be a huge headache - essentially requiring 4 separate code bases with different data types and function prototypes everywhere. With C++ polymorphism, we could use 90% common code with just the very lowest level of the implementation being different in the 4 cases.

---

### Post by markbl on 2012-08-09
> **honeybear said:**
> I must say that I dont like that much the object oriented coding. Old fashion sounds easier to me. Are they others with similar pref., i.e. towards C?
Linus Torvalds has famously [said so](http://blogs.cio.com/esther_schindler/linus_torvalds_why_c_sucks).

---

### Post by vexorian on 2012-08-09
OOP is a tad overrated and should not be used as much as it is. In certain problems, it is a great idea. Specially if you avoid making the mistake of seeing OOP as inheritance and start seeing OOP as polymorphism. In games, polymorphism can really, really help you.

It is not just OOP. In fact, you can code in C++ (and take advantage of its features) without doing OOP.

strings for example. C strings (or lack thereof) are an absolute nightmare, did I bring that point already? Oh, I actually did. Not only are they a nightmare, but also a source of not few security issues.

C++ offers namespaces. It is quite possible to code a large project without namespaces, but I imagine it becomes a nightmare scenario of prefixes and other awful things.  With a namespace you can organize your code and have a level of scope control. For libraries, it is really a basic feature not to expose implementation details to users. This is quite a shortcoming in C.

Finally, we got things like STL and boost. OOP is not that useful, but parametrized types seriously are.

Then we have operator overloading. This is something you won't value until you have to compare using something like the GMP arbitrary precision library in C vs. C++.

---

### Post by honeybear on 2012-08-12
> **markbl said:**
> Linus Torvalds has famously [said so](http://blogs.cio.com/esther_schindler/linus_torvalds_why_c_sucks).

maybe this is old generation type coders. New generations are likely not to be converted. 

Actually C coders are nowadays rather difficult to free to work for free ;) They usually 'd request to be paid for some package upgrading.


EDIT:

I may quote: [http://blogs.cio.com/esther_schindler/linus_torvalds_why_c_sucks](http://blogs.cio.com/esther_schindler/linus_torvalds_why_c_sucks)   

> Linus Torvalds has recently gotten into the fray, posting a message on a techie list in which he says outright that C++ is a horrible language. "It's made more horrible by the fact that a lot of substandard programmers use it, to the point where it's much much easier to generate total and utter crap with it. Quite frankly, even if the choice of C were to do nothing but keep the C++ programmers out, that in itself would be a huge reason to use C."


 "I first looked at Git source code ..."
well, I do not use GIT with passion. GIT is made too complicated, creating an account, login, upoading,  ...  are pain, ... 

Things are to be simpler with the time, and being better. 
Whatever it is good or bad, GIT intention was good. And we should really give a lot of respect. Thank you for making GIT and keeping it running. Lot of respect, kind regards.

---

### Post by honeybear on 2012-08-16
The annoying thing with C is that you always have to define variables first. Is it possible that gcc detects himself that ? Would be similar to vba, bash, ...

---

### Post by smartboyhw on 2012-08-16
Well, g++ supports Object-orientated programming, that's the biggest difference. Also different ways for headers.

---

### Post by Elfy on 2012-08-16
*Thread moved to **The Community Cafe**.*

Not a support question

---

### Post by mips on 2012-08-16
> **jerome1232 said:**
> Whoosh!

English is derived from Latin...

Wrong. English is a Germanic language with Latin influences (400+ yrs of occupation has that effect :biggrin: ). Latin is a Italic language which is a different branch to Germanic. They are however both branches on the Indo-European tree of languages.

[http://upload.wikimedia.org/wikipedia/commons/4/4f/IndoEuropeanTree.svg](http://upload.wikimedia.org/wikipedia/commons/4/4f/IndoEuropeanTree.svg)
[http://en.wikipedia.org/wiki/Germanic_languages](http://en.wikipedia.org/wiki/Germanic_languages)
[http://en.wikipedia.org/wiki/Italic_languages](http://en.wikipedia.org/wiki/Italic_languages)

---

### Post by jerome1232 on 2012-08-16
> **mips said:**
> Wrong. English is a Germanic language with Latin influences (400+ yrs of occupation has that effect :biggrin: ). Latin is a Italic language which is a different branch to Germanic. They are however both branches on the Indo-European tree of languages.


Fine! I concede the point. With me not being a language expert nor a programming expert, I was doomed to failure anyways.

---

### Post by mips on 2012-08-16
> **jerome1232 said:**
> Fine! I concede the point. With me not being a language expert nor a programming expert, I was doomed to failure anyways.

Now we just need to get you guys on that side of the pond to spell properly :tongue: :biggrin:

---

### Post by forrestcupp on 2012-08-16
> **markbl said:**
> Yeah, but it is a poor analogy. C++ is essentially a superset of C.  Anybody who can read/write C++ can read/write C. I a native English speaker but I can't read Latin!I disagree. Anybody who can read/write C++ can write functional C code, but not necessarily read every C code that anyone writes.

> **honeybear said:**
> I must say that I dont like that much the object oriented coding. Old fashion sounds easier to me. Are they others with similar pref., i.e. towards C?I learned to program in BASIC and Assembly on my Commodore 64. So I've had procedural programming methods ingrained in my head. When I started learning C++, it took me a while to understand OOP, but finally one day a light bulb went off and I got it. When you get to where you understand it, you'll see how powerful it is. I don't always use classes and objects when I program in C++, but I would never want to go back to where it's not available.

> **jerome1232 said:**
> Fine! I concede the point. With me not being a language expert nor a programming expert, I was doomed to failure anyways.One thing you need to learn is that no matter how much you think you know about any subject in the world, there is always someone online right here in these forums that will make you look like a blithering idiot. ;)

---

