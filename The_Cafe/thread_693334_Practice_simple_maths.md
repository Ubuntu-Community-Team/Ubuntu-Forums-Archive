---
title: "Practice simple maths?"
date: 2008-02-10
forum: The Cafe
---

### Post by ironfistchamp on 2008-02-10
Hey all,

I have a problem with doing sums quickly in my head, and I really need to get better at doing it. Does anyone know of an application (preferably cross platform) that can churn out a load of simple questions that I can just type the answer to?

Any responses would be great.

Thanks

Ironfistchamp

---

### Post by tehet on 2008-02-11
Hi Ironfistchamp,
this may not be exactly what you ordered, but ... I'm a C-programming noob and thought I'd try to make such a program for edutainment purposes. It's pretty crappy because:
- It always starts with the same not-so-random numbers (edit: fixed)
- It freaks out at input other than numbers
- It produces a compiler warning that I don't understand (edit: fixed)
I may try to fix those later.

Anywho, for now it sort of works ;)

```
/*
** Practice simple math
**
** Generate sum questions and verify answer.
** Form: (0/99) +/- (0/99) = answer.
*/

#include <stdio.h>
#include <stdlib.h>

int i = 1;

int get_random_number(void);

main()
{
        while (1)
        {
                int number1, number2, solution1, solution2, answer;

                number1 = get_random_number();
                number2 = get_random_number();
                solution1 = (number1 + number2);
                solution2 = (number1 - number2);

                printf("%d + %d = \n", number1, number2);
                scanf("%d", &answer);
                if (answer == solution1) printf("Correct!\n\n");
                else printf("Alas, the correct answer is %d.\n\n", solution1);

                printf("%d - %d = \n", number1, number2);
                scanf("%d", &answer);
                if (answer == solution2) printf("Correct!\n\n");
                else printf("Alas, the correct answer is %d.\n\n", solution2);
        }
}

int get_random_number(void)
{
        int n;
        while (i)
        {
                srand((unsigned int)time(NULL));
                i = 0;
        }
        n = rand() / (int)(((unsigned)RAND_MAX + 1) / 100);
        return n;
}
```

---

### Post by pedro_orange on 2008-02-11
Get a rip off of that Dr.K's Brain Training. Or something along those lines. 
Sped up my mental arithmetic no end

---

### Post by ironfistchamp on 2008-02-11
Thanks for the replies. I tried to make a little C# program, but was too tired to get it to work correctly. That code looks pretty good tehet, and will be good practice for you aswell!

I'll look into one of those brain training things. Thanks

Ironfistchamp

---

### Post by Whiffle on 2008-02-11
marker + index cards = flash cards!  


They fit in the palm of your hand, don't require any power, and you can take them anywhere! ;)

---

