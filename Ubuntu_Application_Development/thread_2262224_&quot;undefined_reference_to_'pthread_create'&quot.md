---
title: "&quot;undefined reference to 'pthread_create'&quot;"
date: 2015-01-23
forum: Ubuntu Application Development
---

### Post by pilotRHK on 2015-01-23
"undefined reference to 'pthread_create'" my pthread.h file show that 'pthread_create' is external.:
extern int pthread_create (pthread_t *__restrict __newthread,
               const pthread_attr_t *__restrict __attr,
               void *(*__start_routine) (void *),
               void *__restrict __arg) __THROWNL __nonnull ((1, 3));

How do I get this to work?

---

### Post by steeldriver on 2015-01-23
Hello and welcome to the forums

Undefined references are **link time errors** - we will need to know how you are trying to compile and link the code

---

### Post by pilotRHK on 2015-01-23
Solved!
I need to compile like:
gcc -pthread -o xxx xxx.c

I did not have -pthread.

pilotRHK

---

### Post by steeldriver on 2015-01-23
So... all good now? if so please take the time to mark the thread [SOLVED] using the drop-down 'Thread Tools' menu

---

