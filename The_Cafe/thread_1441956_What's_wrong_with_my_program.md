---
title: "What's wrong with my program?"
date: 2010-03-29
forum: The Cafe
---

### Post by dragos240 on 2010-03-29
```

#include <stdio.h>

int main() {
int a;

printf("How do you feel today? 1 = Good 2 = Bad:\n");
scanf("a");
if (a=1) {
printf("Great!\n");
}
else if (a=2) {
printf("What a pity\n");
}

return 0;
}

```

Both 1 and 2 will return "Great!". :(

---

### Post by lisati on 2010-03-29
Suggestion: take a look at your "[scanf]("http://en.wikipedia.org/wiki/Scanf")" statement.

---

### Post by Mmmbopdowedop on 2010-03-29
Meh, probably wrong. 

Edited my nonsense. :)

---

### Post by dragos240 on 2010-03-29
I did that. It still returned "great."

---

### Post by n0dix on 2010-03-29
try with :
```
if (a==1) {
```

---

### Post by Pogeymanz on 2010-03-29
> **n0dix said:**
> try with :
```
if (a==1) {
```

This is the answer.

The double equal sign is how you compare values. The single equal sign sets the left value to the right value.

---

### Post by derrick81787 on 2010-03-29
> **lisati said:**
> Suggestion: take a look at your "[scanf]("http://en.wikipedia.org/wiki/Scanf")" statement.

Yeah, this is definitely the issue.

*****Edit:**
There is also an issue with the "if" statements, too.  The way you have it now, it will always print "Great."

---

### Post by swoll1980 on 2010-03-29
What does scanf do?

---

### Post by dragos240 on 2010-03-29
> **n0dix said:**
> try with :
```
if (a==1) {
```

My now nothing returns when I type an integer. Before they both returned "Great!" now they don't return anything.

---

### Post by RiceMonster on 2010-03-29
== mean equals, whereas = means assignment. Learn the difference between the two.

> **swoll1980 said:**
> What does scanf do?

Loads a value from stdin into a variable

---

### Post by lisati on 2010-03-29
> **n0dix said:**
> try with :
```
if (a==1) {
```
Good call. I missed that when I first looked at the program. I think I'm too accustomed to thinking the way some other languages work (e.g. BASIC)
> **swoll1980 said:**
> What does scanf do?
It didn't look right when I first looked at the program. Have a look here: [http://en.wikipedia.org/wiki/Scanf](http://en.wikipedia.org/wiki/Scanf)

---

### Post by RiceMonster on 2010-03-29
Your other problem is that scanf should look like this:

```
scanf("%d",&a);
```

Oh, and please indent your code.

---

### Post by dragos240 on 2010-03-29
> **RiceMonster said:**
> Your other problem is that scanf should look like this:

```
scanf("%d",&a);
```Oh, and please indent your code.

Hey! That fixed it! What is the %d for?

---

### Post by derrick81787 on 2010-03-29
> **RiceMonster said:**
> Your other problem is that scanf should look like this:

```
scanf("%d",&a);
```

Oh, and please indent your code.

Yeah, because scanf was wrong, "a" didn't equal 1 or 2.  It returned "Great" before because the "if" statements were wrong.  After they were fixed, it didn't return either one because "a" didn't equal 1 or 2.

Once scanf is fixed, I think it should work as intended.

- Derrick

---

### Post by n0dix on 2010-03-29
For read a integer.

---

### Post by RiceMonster on 2010-03-29
> **dragos240 said:**
> Hey! That fixed it! What is the %d for?

It means you're reading in an integer.

---

### Post by swoll1980 on 2010-03-29
> **lisati said:**
> Good call. I missed that when I first looked at the program. I think I'm too accustomed to thinking the way some other languages work (e.g. BASIC)

It didn't look right when I first looked at the program. Have a look here: [http://en.wikipedia.org/wiki/Scanf](http://en.wikipedia.org/wiki/Scanf)

The only language I know anything about is python. I could tell what was going on though. Everything looked fine to me, except maybe scanf since I didn't know what it did. What language is this?

---

### Post by derrick81787 on 2010-03-29
> **dragos240 said:**
> Hey! That fixed it! What is the %d for?

It says that you want an integer.  I think of "d" as standing for "decimal" but I don't really know.

The % says that the "d" is a formatting mark and not just a "d" that you want displayed.  "%c" will get a character, "%f" will get a float, "%s" will get a string, etc.

You can run **man scanf** to see the actual parameters it takes, or just look at the wiki that has been linked to.  It seems like you need to install a package in order to get the man pages though.  The package might be "manpages-dev" but I don't remember for sure.

- Derrick

---

### Post by derrick81787 on 2010-03-29
> **swoll1980 said:**
> The only language I know anything about is python. I could tell what was going on though. Everything looked fine to me, except maybe scanf since I didn't know what it did. What language is this?

This is C.

---

### Post by wmcbrine on 2010-03-29
For future reference, instead of The Community Cafe, you might want to try [Programming Talk](http://ubuntuforums.org/forumdisplay.php?f=39).

---

### Post by chemouna on 2010-03-29
it has 3 problems:
1-if(a==1) not if(a=1):this is an assignment
2-same thing with if(a==2) not if(a=2)
3-scanf("%d", &a)

check out this C tutorial [http://beej.us/guide/bgc/output/html/multipage/index.html](http://beej.us/guide/bgc/output/html/multipage/index.html)

---

### Post by MaxIBoy on 2010-03-29
Think of scanf as the exact opposite of printf. Printf takes a format string and arguments, and turns the result into console output. 

Scanf takes a format string and pointers to some arguments, and uses that to fill out the arguments' values using console input. 

Sprintf takes a format string and arguments, and puts the result in another string for you to do other stuff with. Snprintf is the same but you specify a maximum size (so always use it instead of just sprintf, because otherwise you'll be vulnerable to buffer overrun errors.)

Printf is definitely the easiest to understand of the bunch, although the others are straightforward once you understand printf. So see here for printf: 
[http://www.cplusplus.com/reference/clibrary/cstdio/printf/](http://www.cplusplus.com/reference/clibrary/cstdio/printf/)

You've done string formatting in Python before right? Like as in this stuff:
[http://docs.python.org/release/2.5.2/lib/typesseq-strings.html](http://docs.python.org/release/2.5.2/lib/typesseq-strings.html)
It's basically the same thing for C's printf/scanf/sprintf/snprintf.

---

