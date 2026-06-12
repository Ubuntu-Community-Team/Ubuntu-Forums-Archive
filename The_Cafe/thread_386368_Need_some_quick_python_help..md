---
title: "Need some quick python help."
date: 2007-03-16
forum: The Cafe
---

### Post by TheRingmaster on 2007-03-16
I am trying to follow this guide on python and it talks about using the print_twice function. When I use that command, python tell me that print_twice is undefined. I am sure that I don't to create that function. what is going wrong here?

[How to Think Like a Computer Scientist: 3. Functions]("http://www.ibiblio.org/obp/thinkCSpy/chap03.html#auto7")

Thanks,
The Ringmaster

---

### Post by kano on 2007-03-16
You need to define that function, like it says in the guide.

```

def print_twice(bruce):
     print bruce, bruce

```

---

### Post by TheRingmaster on 2007-03-16
That seems like a function that should already be defined, but now I see how to do it.

> word = "'spam'*4"

def print_twice(word):
    print word, word

print_twice(word)outputs:
> 'spam'*4 'spam'*4Yeah, I did it!!

---

### Post by TheRingmaster on 2007-03-16
what if I wanted to use print_twice to print any thing I put into it two times? Do I have to keep Defining new print_twice functions with different parameters?

---

### Post by o_fortuna on 2007-03-17
> **TheRingmaster said:**
> what if I wanted to use print_twice to print any thing I put into it two times? Do I have to keep Defining new print_twice functions with different parameters?
Just put whatever you want into whatever variable you want. For example:
```
def print_twice(word):
     print word, word

lunch = "Carrot Sticks!"
dinner = "Turkey!"
print_twice(lunch)
print_twice(dinner)
```

Variables are internal to a function. Think of it like a big black box. You dump whatever you want, the function works its magic, and gives the output. What goes on specifically inside the function won't affect the variables in the rest of the program. In fact, the box is black, so not only can you not see inside, but the Function Magician (aka code) inside the box can't see outside. It only knows what you tell it. Since you defined the input as "word", when you dump whatever you want into the function, it thinks it's a word. Whether it's called "word" outside the function is irrelevant.

---

