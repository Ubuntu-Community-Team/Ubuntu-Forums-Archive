---
title: "Kernighan &amp; Ritchie - Really basic problem, hoping someone can advise :-)"
date: 2010-05-28
forum: The Cafe
---

### Post by anandamide on 2010-05-28
Well, I have a year off study so thought I'd finally get around to learning C.

Have a copy of K&R, and I've come unstuck at a really early stage and am at a total loss as to why!

This is the program given at 1.5.1, page 17, describing a simple while loop:

```
#include <stdio.h>

/*copy input to output, v2 */

main ()
{
	int c;

	while ((c = getchar()) !=EOF)
	putchar(c);
	
}

```

This is meant to have a program display input from the keyboard onto the screen until [ENTER] is hit, at which point the loop ends. 

Problem is, it doesn't end. I need to press CTRL-D. Subsequent programs given in section 1.5.2 have exactly the same problem.

I've spent all morning thinking that I must be going mad, because I can't understand how an example given by the guys who wrote the C language can be cocking up on my system, and have been assuming I *must* have been getting something wrong. But I can't see how my program differs from that in the book other than the comments.

Can anyone shed any light on this? I'm using gcc, if that helps.

---

### Post by lykwydchykyn on 2010-05-28
I'm no expert, but I believe ctrl-D is EOF; "Enter" doesn't constitute EOF.  Your loop is testing for EOF, so it makes sense that ctrl-D is required to exit.  This behavior is pretty standard in programs that accept stdin.

It's worth noting too that both Unix and C have changed significantly since K&R, though my knowledge of C is passing at best so don't ask me how.

---

### Post by nmaster on 2010-05-28
ctrl+D indicates the EOF.  if you tried this with a text file (instaed of stdin) it should work the way you expect.

```
 cat testfile.txt | a.out 
```

---

### Post by anandamide on 2010-05-28
[facepalm]

I knew it was going to be something glaringly obvious.

Thanks so much guys, at least I know to be on my guard for niggles like that.

:-)

---

