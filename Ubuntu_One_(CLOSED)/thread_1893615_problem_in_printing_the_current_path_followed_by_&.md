---
title: "problem in printing the current path followed by &gt;"
date: 2011-12-10
forum: Ubuntu One (CLOSED)
---

### Post by smomani on 2011-12-10
Hello,

I'm trying to print the current path followed by ">" character,so i wrote the following code :

int p;
p = fork();
   if(p == 0) {     // Child

      execl("/bin/pwd", "/bin/pwd", NULL);
     
   }
   wait(NULL);
 printf(">");


but the output were as follows:
/home/user
>

but I need them to be in the same line...

If anyone can help me with this I'll appreciate it..

Thanks,

---

