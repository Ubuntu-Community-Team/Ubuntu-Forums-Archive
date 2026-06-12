---
title: "Could not Google &gt;"
date: 2011-05-18
forum: The Cafe
---

### Post by Eldera on 2011-05-18
I am trying to learn the modern meaning of the symbol >.

Google said Your search - > - did not match any documents. Suggestions:
* Try different keywords.

Please don't laugh at me, I studied HS algebra in 1949 and x > y just meant x is greater than y.

Please update me, especially how it is used in the command line.

Thanks in advance, Eldera

---

### Post by Tibuda on 2011-05-18
Yeah > still means "greater than" in maths and in programming (python, ruby, c, java), but in the command line it is used to store the output of a command in a file. Example:
```
ls /home > homefiles.txt
```
will save the list of files in /home in a file named homefiles.txt

---

### Post by |{urse on 2011-05-18
it is usually used to direct output in bash

echo "Put this in myfile" > myfile

in C it is a directional operator 

cout << "this data will be output to the monitor\n";
//whatever is inputted via keyboard will be assigned into y
cin >> y;
cout << y; //whatever was contained in y will be output to the monitor

---

### Post by Eldera on 2011-05-18
Thank you. That was exactly the information I needed.

---

### Post by Thewhistlingwind on 2011-05-18
> **Eldera said:**
> 

Please don't laugh at me, I studied HS algebra in 1949 and x > y just meant x is greater than y.



Nobody actually laughed at you did they? If they did, that's horrible.

Anyway, the meaning hasn't changed, but in the computing world it has (and can have) a lot of them.

In terms of the command line, if your prompt turned into a > symbol, I can't help you.

---

### Post by Eldera on 2011-05-18
No, nobody laughed. I just felt silly because I had to ask. When I can't find it on Google, I feel I am in big trouble.

---

### Post by red_Marvin on 2011-05-18
> **|{urse said:**
> in C it is a directional operator 

cout << "this data will be output to the monitor\n";
//whatever is inputted via keyboard will be assigned into y
cin >> y;
cout << y; //whatever was contained in y will be output to the monitor

Sorry to be nitpicky, but it still means 'greater than' in C
as well as in C++, which your code snippet is in.
<< and >> are separate operators that in C/C++ mean left or right
shift, however for the input and output stream classes they
are overloaded for other tasks.

To the op: I have myself stumbled upon the same problem a couple of times,
alas, there seem to be no easy solution, as google in most cases ignore
special characters: [https://www.google.com/support/websearch/bin/answer.py?answer=134479](https://www.google.com/support/websearch/bin/answer.py?answer=134479)

---

### Post by |{urse on 2011-05-18
> Sorry to be nitpicky, but it still means 'greater than' in C
as well as in C++, which your code snippet is in.
<< and >> are separate operators that in C/C++ mean left or right
shift, however for the input and output stream classes they
are overloaded for other tasks.

I'm pretty certain my snippet is in C and I'm pretty sure thats the definition of a bitwise directional operator. And yes in C/C++ > means greater than.

What makes you say it's C++ and not C? I'm probably wrong, just curious.

---

### Post by Dustin2128 on 2011-05-18
> **Thewhistlingwind said:**
> 
In terms of the command line, if your prompt turned into a > symbol, I can't help you.
I never really knew what that was, but you can get out with Ctrl-C.

---

### Post by NovaAesa on 2011-05-18
> **|{urse said:**
> 
What makes you say it's C++ and not C? I'm probably wrong, just curious.

Something like:
```
cout << "this data will be output to the monitor\n";
```
is definitely C++ if you make the assumption that the semantic meaning is as described in the string. There's no operator overloading in C, and in C the << operator isn't defined to work on const char* and anything.


To the OP, check out [http://en.wikipedia.org/wiki/Greater-than_sign](http://en.wikipedia.org/wiki/Greater-than_sign) you'll find lots of uses there.

---

### Post by Eldera on 2011-05-18
Thanks for the links, everybody. Checking them out now.

---

### Post by Tibuda on 2011-05-18
> **Dustin2128 said:**
> I never really knew what that was, but you can get out with Ctrl-C.

that means it is a continuation bacause your command was not completed, like an unclosed quote.

---

### Post by Dustin2128 on 2011-05-18
> **Tibuda said:**
> that means it is a continuation bacause your command was not completed, like an unclosed quote.
Oh- so what's the proper way to get out of it? Finish your command or something?

---

### Post by NCLI on 2011-05-18
> **Dustin2128 said:**
> Oh- so what's the proper way to get out of it? Finish your command or something?
Write the missing quote and hit enter. The command will fail, but you'll get out :p

---

### Post by Tibuda on 2011-05-18
> **NCLI said:**
> Write the missing quote and hit enter. The command will fail, but you'll get out :p

no, the command will not fail if you close it properly. try it yourself
```
$ echo "multi
> line
> text"
multi
line
text
$
```

it also happens with an unclosed "if" or other structure:
```
$ if [ -f filename.ext ]; then
> echo "filename.ext exists"
> fi
$

```

---

### Post by Dustin2128 on 2011-05-18
Thanks! Been annoying me for a long time!

---

### Post by red_Marvin on 2011-05-19
> **|{urse said:**
> I'm pretty certain my snippet is in C and I'm pretty sure thats the definition of a bitwise directional operator. And yes in C/C++ > means greater than.

What makes you say it's C++ and not C? I'm probably wrong, just curious.

You do not do input/output in C with cin/cout, they are C++ classes, see [|here|](http://www.cplusplus.com/reference/iostream/) for more info.
C does not even have classes, and you (usually) do input/output with printf, and scanf (which you can also use in C++ though)

---

