---
title: "fsync() in the latest kernel (4.15.x ) Broken ????"
date: 2018-07-31
forum: Ubuntu/Debian BASED
---

### Post by cwills on 2018-07-31
So this is a simple one, if I run the following code on Ubuntu 18.04 (4.15.0-29-generic ) and against Ubuntu 16.04 ( 4.4.0-87-generic) I get two different results ; The question is why? It seems that fsync may be broken in the latest kernel and may well be broken as early as 4.10 ? This has huge implications around performance sensitive applications like mysql. (Yes I know it can be turned off in mysql but thats only any good if you like your databases corrupted).


4.4.0-87-generic  - # time ./fsync   
real    0m7.537s     <-----
user    0m0.000s
sys     0m1.060s


4.15.0-29-generic - # time ./fsync
real    1m38.299s    <-----
user    0m0.013s
sys     0m0.893s










#include <stdio.h>
#include <fcntl.h>
#include <time.h>
#include <unistd.h>


void withSync() {
    int f = open( "/tmp/t8" , O_RDWR | O_CREAT );
    lseek (f, 0, SEEK_SET );
    int records = 10*1000;
    clock_t ustart = clock();
    for(int i = 0; i < records; i++) {
        write(f, "012345678901234567890123456789" , 30);
        fsync(f);
    }
    clock_t uend = clock();
    close (f);
    printf("   sync() seconds:%lf   writes per second:%lf\n", ((double)(uend-ustart))/(CLOCKS_PER_SEC), ((double)records)/((double)(uend-ustart))/(CLOCKS_PER_SEC));
}


void withoutSync() {
    int f = open( "/tmp/t10" , O_RDWR | O_CREAT );
    lseek (f, 0, SEEK_SET );
    int records = 10*1000;
    clock_t ustart = clock();
    for(int i = 0; i < records; i++) {
        write(f, "012345678901234567890123456789" , 30 );
    }
    clock_t uend = clock();
    close (f);
    printf("no sync() seconds:%lf   writes per second:%lf \n", ((double)(uend-ustart))/(CLOCKS_PER_SEC), ((double)records)/((double)(uend-ustart))/(CLOCKS_PER_SEC));
}


int main(int argc, const char * argv[])
{
/*    withoutSync();*/
    withSync();
    return 0;
}

---

