---
title: "gVerse error"
date: 2009-04-15
forum: Ubuntu Christian Edition
---

### Post by jonathonblake on 2009-04-15
All:

I'm trying to install/configure gVerse on my system.  I don't know C++. (More precisely, I don't remember enough of it to code in it.)

I downloaded the source from sourceforge. 
Install the required libraries.

run "make".
Error message is:
```

g++ main.cpp -O2 -o gVerse `pkg-config --cflags --libs gtk+-2.0`
main.cpp: In function ‘int main(int, char**)’:
main.cpp:26: error: ‘strcmp’ was not declared in this scope
make: *** [gVerse] Error 1

```

What do I do to fix this error?

#####

Can somebody package gVerse, so that it is available simply by using Synaptic?

jonathon

---

### Post by lintoolman on 2009-04-15
Did you try "make install" or is that what you meant by "run make"?

---

### Post by jonathonblake on 2009-04-15
> **lintoolman said:**
> Did you try "make install" or is that what you meant by "run make"?


The error message I quoted is from running "make", not "make install". 

```

jonathon@linux:~/downloads/epiphany/gVerse-0.5$ make
g++ main.cpp -O2 -o gVerse `pkg-config --cflags --libs gtk+-2.0`
main.cpp: In function ‘int main(int, char**)’:
main.cpp:26: error: ‘strcmp’ was not declared in this scope
make: *** [gVerse] Error 1
jonathon@linux:~/downloads/epiphany/gVerse-0.5$ 
jonathon@linux:~/downloads/epiphany/gVerse-0.5$ make install
mkdir ~/.gVerse
mkdir: cannot create directory `/home/jonathon/.gVerse': File exists
make: *** [install] Error 1
jonathon@linux:~/downloads/epiphany/gVerse-0.5$ 

```

Does that clarify the error any better?

jonathon

---

