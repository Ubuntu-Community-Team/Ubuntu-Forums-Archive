---
title: "malloc free is 22% slower on ubuntu 14.04"
date: 2015-09-08
forum: Ubuntu, Linux and OS Chat
---

### Post by sameer-s-mahajan on 2015-09-08
[FONT=Helvetica Neue]When I run the following program on ubuntu 10.04 and 14.04, I notice that 14.04 is 22% slower. Any ideas?[/FONT]

#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <time.h>
#include <sys/time.h>

int func()
{
   char* b = (char *) malloc(4096);
   free(b);
   return(0);
}

int main(int argc, char** argv)
{
   int i;

   struct timeval start, end;
   gettimeofday(&start, NULL);

   for (i = 0; i < atoi(argv[1]); i++)
   {
       func();
   }

  gettimeofday(&end, NULL);

  printf("time taken is %ld seconds\n", end.tv_sec - start.tv_sec);
}
[FONT=Helvetica Neue]The behavior is consistent. The hardware of the two machines is identical.[/FONT]

---

### Post by RichardET on 2015-09-08
Have you done other benchmarks?

---

### Post by sameer-s-mahajan on 2015-09-09
@[COLOR=#DD4814][COLOR=#000000][RichardET]("http://ubuntuforums.org/member.php?u=1842352"): What other benchmarks you have in mind? I was trying to narrow down slowdown hit by one of our scenarios when I stumbled upon this.[/COLOR][/COLOR]

---

### Post by RichardET on 2015-09-09
another idea is to look at FFT test suites

---

