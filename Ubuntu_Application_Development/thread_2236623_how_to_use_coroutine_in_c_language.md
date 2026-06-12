---
title: "how to use coroutine in c language"
date: 2014-07-28
forum: Ubuntu Application Development
---

### Post by zerop2 on 2014-07-28
[http://www.chiark.greenend.org.uk/~sgtatham/coroutines.html](http://www.chiark.greenend.org.uk/~sgtatham/coroutines.html)

compile the code in above link directly

main.c:6:0: warning: "crReturn" redefined [enabled by default]
main.c:4:0: note: this is the location of the previous definition
main.c: In function ‘function’:
main.c:12:22: error: macro "crReturn" passed 2 arguments, but takes just 1
main.c:12:9: error: ‘crReturn’ undeclared (first use in this function)
main.c:12:9: note: each undeclared identifier is reported only once for each function it appears in
main.c: In function ‘main’:
main.c:19:6: error: ‘for’ loop initial declarations are only allowed in C99 mode
main.c:19:6: note: use option -std=c99 or -std=gnu99 to compile your code
main.c:20:19: error: expected expression before ‘do’

```

#include <stdio.h>

#define crBegin static int state=0; switch(state) { case 0:
#define crReturn(i,x) do { state=i; return x; case i:; } while (0)
#define crFinish }
#define crReturn(x) do { state=__LINE__; return x; \
                         case __LINE__:; } while (0)
int function(void) {
    static int i;
    crBegin;
    for (i = 0; i < 10; i++)
        crReturn(1, i);
    crFinish;
}

int main(void)
{
    crBegin;
        for(int c= 0; c<3; ++c)
           printf("%d", crReturn(c));
        crReturn(EOF);
        crFinish;
    return 0;
}

```

---

