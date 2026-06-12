---
title: "Problem with GCC/C/header file structure"
date: 2012-08-14
forum: Ubuntu Application Development
---

### Post by Santillana on 2012-08-14
This may or may not be a strictly Ubuntu question, but the competence to see through this problem is certainly found on this forum.

I have a problem with an exceptionally small C program whose only purpose is to secure that I have understood the principle of modularization through the use of header files.

I have one main program:

```
#include <stdio.h>
#include "funko_support.h"

struct person
{
   char namn[20];
   int alder;
};

struct person p[5];

main()
{
   
   int i, aldst;
   for (i=0; i<5; i++)
   {
      p[i]=inperson();
   }
   aldst=0;
   for (i=0; i<5; i++)
   {
      if (p[i].alder>aldst)
      {
         aldst=i;
      }
   }
   utperson(p[aldst]);
}
```The mechanism/algorithm is really irrelevant, but I could explain it in a snap. Obviously, it refers to a header file called funko_support.h that I have written. In that file is contained the functions inperson() and utperson():

```
   struct person inperson(void);
   void utperson(struct person p); 
```These, of course, are declarations. The definitions pertaining to these declarations are in funko_support.c:

```
#include <stdio.h>

struct person inperson(void)
{
   printf("Skriv namn och ålder med mellanslag: ");
   struct person p;
   scanf("%s %d",p.namn,&p.alder);
   return p;
}

void utperson (struct person p)
{
   printf("Personen %s, %d år, är äldst\n",p.namn,p.alder);
}
```ALL THESE FILES ARE IN THE SAME CATALOG, /home/martin/C_programs. CHECKED THAT 928792847 TIMES.

No amount of effort or restructuring keeps me from getting the error message 

/tmp/cc7trJgi.o: In function `main':
testa_struct.c:(.text+0x34): undefined reference to `inperson'
testa_struct.c:(.text+0xdb): undefined reference to `utperson'
collect2: ld returned 1 exit status

when I enter the text from $ below:

martin@martin-1001PX:~/C_programs$ gcc -o testa_struct.out testa_struct.c


WHAT
 
am I doing wrong? What is keeping GCC from finding this header file and the contained functions?

Any help would be more than appreciated, including pointers to COMPREHENSIVE tutorials on GCC and headers. The official Using the GNU Compiler Collection (GCC) may be very good but isn't helping anything with this specific problem.

---

### Post by steeldriver on 2012-08-14
you need to list BOTH your .c files on the gcc command line I think

```
gcc -o testa_struct.out testa_struct.c funko_support.c
```you will probably also need to move your struct person definition into the header file, and include that in your funko_support.c file - else it won't understand the return type of your inperson function (or the argument type of utperson)

---

### Post by Santillana on 2012-08-14
> **steeldriver said:**
> you need to list BOTH your .c files on the gcc command line I think

```
gcc -o testa_struct.out testa_struct.c funko_support.c
```you will probably also need to move your struct person definition into the header file, and include that in your funko_support.c file - else it won't understand the return type of your inperson function (or the argument type of utperson)

Ah. Several directions to try to move in. Thanks! This place is bustling with experts like you. :)

And most impressive of all is the speed at which experts move in. Quick help is double help.

---

