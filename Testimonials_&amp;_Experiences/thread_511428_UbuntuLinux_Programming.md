---
title: "Ubuntu/Linux Programming"
date: 2007-07-27
forum: Testimonials &amp; Experiences
---

### Post by sgtbob on 2007-07-27
Could some users suggest how to learn programming.  I borrowed a book from the Library ' Linux Programming', but it was so far above my head, I couldn't fathom how to proceed.  It kept talking about 'C' language.  Any suggestions on what books or study material might be available that would help this newby get started into the realm of programming?  Nothing too deep, this is a learning experience for this 74 year old, so woudl appreciate something practical.](*,)

Bob

---

### Post by freebeer on 2007-07-27
Might I suggest that you post this in "Programming Talk" forum?  You're likely to get a better response.  :D

---

### Post by 3rdalbum on 2007-07-28
It might be a good idea to start with a language like Python, as it's easy to pick up and can do a LOT of things.

The Python website ([www.python.org](www.python.org)) has a tutorial and a library reference for download - the tutorial is good and the library reference is invaluable, so that's where I'd suggest you go.

---

### Post by tqk on 2007-07-30
> **sgtbob said:**
> Could some users suggest how to learn programming.  I borrowed a book from the Library ' Linux Programming', but it was so far above my head, I couldn't fathom how to proceed.  It kept talking about 'C' language.  Any suggestions on what books or study material might be available that would help this newby get started into the realm of programming?  Nothing too deep, this is a learning experience for this 74 year old, so woudl appreciate something practical.](*,)

Bob

Start out slow.  Bash scripting would be a good place to start.  You can learn basic things like what you have to work with, programming constructs you can use, data you have to work with.  For example, you can do things in sequence:

```
dothis ; thendothis ; thendothis
```

Toss in conditional execution:

```
if [ $some_condition ]; do
   this
fi
```

Or looping:

```
while [ $condition ]; do
   this
done
```

Keep it simple at the beginning and read the man pages ("man bash").  Understand that the learning curve at the beginning is steep.  The curve flattens out once you know your way around, then everything you've learned builds on everything else you've learned.

At your age, you should have learned the value of patience.  Consider that your strength.

Here's a very gentle HOWTO in shell programming:

  - Edit (somehow) somefile.sh

  - In somefile.sh, enter some commands which do stuff (echo "something" is a     
    start).

  - chmod u+x somefile.sh

  - ./somefile.sh

The "Edit" bit can be any text editor, but I'd suggest "nano" to start.

For commands in somefile.sh, pretty much anything will do.  "df" or "/sbin/ifconfig" or "apropos whatever" or "locate share".

Make the first line of "somefile.sh":

   #!/bin/bash

What else?  Well, flounder around and see what happens.  The more you bang your head on it, the easier it gets.  Ask questions!  Heck, you're welcome to send me email if you want.  I'll be glad to point you in the right direction if I can.

Most important: have fun!  :-)

---

### Post by stchman on 2007-07-31
> **sgtbob said:**
> Could some users suggest how to learn programming.  I borrowed a book from the Library ' Linux Programming', but it was so far above my head, I couldn't fathom how to proceed.  It kept talking about 'C' language.  Any suggestions on what books or study material might be available that would help this newby get started into the realm of programming?  Nothing too deep, this is a learning experience for this 74 year old, so woudl appreciate something practical.](*,)

Bob

Programming and GUI by the API is very difficult.  GO look at a text on programming the Windows interface.  It is very unintuitive.

I recommend you try either Python or Java.  They are far easier.

---

### Post by 3rdalbum on 2007-07-31
Actually now I get the impression that the OP believes the command line to be a form of "programming".

If what you really want is to learn what commands to type into the terminal, then you want [www.linuxcommand.org](www.linuxcommand.org).

---

