---
title: "ASLR Protection in Action"
date: 2011-03-25
forum: Security
---

### Post by jeff.biggeek02 on 2011-03-25
Hi everyone,

I am playing around a bit to try and understand ASLR.  I wrote a simple program in C:

#include <stdio.h>

void function (int a) {
    void * myAddr = __builtin_return_address(0); //get this function's address
    printf("My integer: %i\n", a);
    printf("My address: %p\n", myAddr);

    myAddr = __builtin_return_address(1); //get the CALLER address
    printf("My address: %p\n", myAddr);
    
    //This changes on every run...ASLR in action for sure.
    printf("My address stored on the stack: %p\n", &myAddr);    
}

int main() {
  function(1);
}


I compile it like so:
gcc -g buff1.c -o buff1

And when I run it several times in a row, the only value that changes is my stack location for myAddr.  I'm surprised to see that my return addresses remain the same on Ubuntu (latest) with ASLR built-in.

Here are a few sample runs of my program.  I'm curious why ASLR doesn't randomize where DLL execution code is loaded.  Any thoughts?  Again, this is just for fun and learning, but I'm a little stumped.  Maybe my definition of ASLR was too broad.  Got it from wikipedia, so it should be reasonably accurate:
[http://en.wikipedia.org/wiki/Address_space_layout_randomization](http://en.wikipedia.org/wiki/Address_space_layout_randomization)

reeds@ReedsHPMini:~/src/research/buff1$ ./buff1 
My integer: 1
My address: 0x8048440
My address: 0x6aace7
My address stored on the stack: 0xbf97b4bc
reeds@ReedsHPMini:~/src/research/buff1$ ./buff1 
My integer: 1
My address: 0x8048440
My address: 0x126ce7
My address stored on the stack: 0xbf8a68dc
reeds@ReedsHPMini:~/src/research/buff1$ ./buff1 
My integer: 1
My address: 0x8048440
My address: 0x2e6ce7
My address stored on the stack: 0xbfd1ffec
reeds@ReedsHPMini:~/src/research/buff1$ ./buff1 
My integer: 1
My address: 0x8048440
My address: 0x59fce7
My address stored on the stack: 0xbf912eac

---

### Post by njdove on 2011-03-25
My C is a bit rusty, but I know that you must explicitly compile with ASLR support:[FONT=Courier New] gcc -fpie -pie -g buff1.c buff1[/FONT]. With these "Position Independent Executable" compiler and linker options in place, your test code's addresses are randomized.

To my understanding, ASLR randomizes the locations of the heap, libraries, stacks, and executables with PIE enabled. Perhaps someone more knowledgeable than me can correct or clarify.

You may be interested in the [checksec.sh script]("http://www.trapkit.de/tools/checksec.html"), which enumerates executables' compiled-in security features.

---

