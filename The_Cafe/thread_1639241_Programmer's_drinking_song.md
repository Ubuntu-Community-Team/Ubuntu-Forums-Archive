---
title: "Programmer's drinking song"
date: 2010-12-06
forum: The Cafe
---

### Post by Megaptera on 2010-12-06
99 little bugs in the code,
99 bugs in the code,
Fix one bug, compile it again,
101 little bugs in the code.
101 little bugs in the code,
101 bugs in the code,
Fix one bug, compile it again,
103 little bugs in the code.

---

### Post by zer010 on 2010-12-06
:lolflag:

---

### Post by NightwishFan on 2010-12-06
This is so true.

---

### Post by 3Miro on 2010-12-06
Love it!

---

### Post by CharlesA on 2010-12-06
Pure awesomesauce.

---

### Post by theraje on 2010-12-06
Very nice!

My version:

One little bug in the code for my app
One little bug in the code
Fix the bug, build it again
1.9655116271520547192825987446811e+39 bugs in the code.

:( :P

---

### Post by cammin on 2010-12-06
Now write a program that prints the lyrics.

---

### Post by Old_Grey_Wolf on 2010-12-06
> **Megaptera said:**
> 99 little bugs in the code,
99 bugs in the code,
Fix one bug, compile it again,
101 little bugs in the code.
101 little bugs in the code,
101 bugs in the code,
Fix one bug, compile it again,
103 little bugs in the code.

Is that licensed under GPL? 

I know a few programmers I would love to send that song to.

:lolflag:

---

### Post by Old_Grey_Wolf on 2010-12-06
Working on a different version.

```
1 little new bug in the code,
1 little new bug,
Fix the bug, **make** it again,
2 little new bugs in the code.

2 little new bugs in the code,
2 little new bugs,
Fix the bug, **make** it again,
3 little new bugs in the code.

3 little new bugs in the code,
3 little new bugs,
Fix the bug, **make** it again,
4 little new bugs in the code.

...
```

---

### Post by Shining Arcanine on 2010-12-06
Does anyone want to write a version of this in C? :P

---

### Post by Old_Grey_Wolf on 2010-12-06
> **Shining Arcanine said:**
> Does anyone want to write a version of this in C? :P

Are you talking about the C programing language? Or are you referring to C# or C, from the music viewpoint?

:lolflag:

---

### Post by TheWeakSleep on 2010-12-07
```
#!/usr/bin/env python

def main():
    bugs = 1
    while True:
        if bugs <= 1:
            print "One tiny little bug in the code\nOne tiny little bug."
            print "Fix one bug, run it again"
            bugs += 1
        else:
            bugs += 1
            print "%i little bugs in the code\n%i little bugs." % (bugs, bugs)
            print "Fix one bug, run it again"
    return 0

if __name__ == '__main__':
    main()
```

This is my Python contribution. Hope you like it ;)

---

### Post by Megaptera on 2010-12-07
Thanks all, glad it touched a chord - to coin a phrase!

---

### Post by Spice Weasel on 2010-12-07
> **TheWeakSleep said:**
> ```
#!/usr/bin/env python

def main():
    bugs = 1
    while True:
        if bugs <= 1:
            print "One tiny little bug in the code\nOne tiny little bug."
            print "Fix one bug, run it again"
            bugs += 1
        else:
            bugs += 1
            print "%i little bugs in the code\n%i little bugs." % (bugs, bugs)
            print "Fix one bug, run it again"
    return 0

if __name__ == '__main__':
    main()
```

This is my Python contribution. Hope you like it ;)

I love you. :lol:

---

### Post by TheLions on 2010-12-07
> **Shining Arcanine said:**
> Does anyone want to write a version of this in C? :P

void fixBug(int i, int* bugNo){
[INDENT]printf("%i little new bug in the code, \n%i little new bug, \n,Fix the bug, make it again," i, i);
editCode(bugNo);
make(bugNo);
if (bugNo == NULL){
[INDENT]return;[/INDENT]
}
fixBug(i +1, bugNo);[/INDENT]
}

recursive version...

---

### Post by trivialpackets on 2010-12-07
Ruby
```

#!/usr/bin/env ruby

def sing(cycles)
  iterations = cycles.nil? ? 100 : cycles.to_i
  count = bugs = 1

  while count <= iterations
    puts "#{bugs} little bug#{"s" if bugs > 1} in the code,\n#{bugs} little bug#{"s" if bugs > 1}."
    puts "Fix one bug, and run it again...\n\n"
    count += 1
    bugs += Random.new.rand(1..3)
  end
  puts "...and the cycle goes on and on...happy coding!"
end

sing(ARGV[0])

```

---

### Post by Old_Grey_Wolf on 2010-12-07
TheWeakSleep, TheLions, and eric.proctor, I should try running each of those.

:lolflag:

---

### Post by user1397 on 2010-12-07
> **TheWeakSleep said:**
> This is my Python contribution. Hope you like it ;)

when i run that in a terminal it goes on forever...was that your design plan? or can you code it so it stops at 100 or something like that?

---

### Post by matt_symes on 2010-12-07
> **ubuntuman001 said:**
> when i run that in a terminal it goes on forever...was that your design plan? or can you code it so it stops at 100 or something like that?

```
while True:
```

It will keep on going until it falls over. (That'll be the bugs ;))

---

### Post by trivialpackets on 2010-12-08
I'm working on learning python currently, so I fixed the "bug" and added a feature (random bug counts) to the code posted earlier.

```

#!/usr/bin/env python
#Filename: programmers_song.py

import random

def main():
    bugs = 1
    iterations = 0

    print("One tiny little bug in the code\nOne tiny little bug.")
    print("Fix one bug, run it again")
    
    while True:
        bugs += random.randint(1,4)
        iterations += 1
        print "%i little bugs in the code\n%i little bugs." % (bugs, bugs)
        print "Fix one bug, run it again"
        if iterations >= 100:
            return False

if __name__ == '__main__':
    main()
```

---

### Post by Johnsie on 2010-12-08
lol, very good :-)

---

### Post by idi0tf0wl on 2010-12-08
Endless Java version, based on the original song but starting from one:
```
    public static void main(String[] args) {
        int count = 1;
        while (true) {
            for (int i = 0; i < 2; i++) {
                System.out.print(count + " little bug");
                if (count == 1) {
                    System.out.print(" in the code\n");
                } else System.out.print("s in the code\n");
            }
            System.out.println("Fix one bug, compile it again");
            count += 2;
            System.out.println(count + " little bugs in the code");
        }
    }
}
```

---

### Post by sisco311 on 2010-12-08
bash:
```
#!/bin/bash

function printl
{
  string="$1"
  for ((i=0; i<=${#string}; i++)); do
    echo -n "${string[@]:$i:1}"
    sleep 0.08
  done
  echo
}

function prints
{
  printl "$1 little bugs in the code,"
  printl "$1 bugs in the code,"
  printl "fix one bug, compile it again,"
  printl "$(( $1+2 )) bugs in the code."
  echo
}

j=99
while true; do
  prints $j
  j=$(( $j+2 ))
done

```

---

### Post by idi0tf0wl on 2010-12-08
@sisco311 I love your style!

---

### Post by TheWeakSleep on 2010-12-08
> **ubuntuman001 said:**
> when i run that in a terminal it goes on forever...was that your design plan? or can you code it so it stops at 100 or something like that?

The point of it is that it never stops :) but yes, it would be trivial to add something like that.

---

### Post by nlsthzn on 2010-12-08
This is one of those, don't put to many programmers and alcohol in the same room scenarios isn't it :D

---

### Post by trivialpackets on 2010-12-08
> **nlsthzn said:**
> This is one of those, don't put to many programmers and alcohol in the same room scenarios isn't it :D

On the contrary...

[http://xkcd.com/323/](http://xkcd.com/323/)

---

### Post by cpmman on 2010-12-08
**Penalties for possession and dealing**

                                                                                                                                                                               [HTML]
a)Possession:        b)Dealing: 

Class A   Ecstasy, LSD, heroin, cocaine, crack, magic mushrooms, amphetamines (if prepared for injection).
a) Up to seven years in prison or an unlimited fine or both.
b) Up to life in prison or an unlimited fine or both.

Class B     Amphetamines, Cannabis, Methylphenidate (Ritalin), Pholcodine.                     
a) Up to five years in prison or an unlimited fine or both.
b) Up to 14 years in prison or an unlimited fine or both.

Class C      Tranquilisers, some painkillers, Gamma, C, C++, Perl, bash
hydroxybutyrate (GHB), Ketamine.                     
a) Up to two years in prison or an unlimited fine or both.
b) Up to 14 years in prison or an unlimited fine or both.                                                [/HTML]        All of the drugs on the list above - whether Class A, B or  C - are designated as controlled substances under the Misuse of Drugs  Act 1971, and using them is illegal.

---

### Post by koenn on 2010-12-08
> **sisco311 said:**
> bash:
```
 ....

```
> **idi0tf0wl said:**
> @sisco311 I love your style!

Yeah, it's beatiful, but it really should be done with a recursive function. That loop at the end looks a bit bolted on.

something like this:
```

#!/bin/bash

function printl
{
  string="$1"
  for ((i=0; i<=${#string}; i++)); do
    echo -n "${string[@]:$i:1}"
    sleep 0.08
  done
  echo
}

function prints
{
  printl "$1 little bugs in the code,"
  printl "$1 bugs in the code,"
  printl "fix one bug, compile it again,"
  printl "$(( $1+2 )) bugs in the code."
  echo
 
 # more bugs here
 prints $(( $1+2 ))
}

# main
prints 99

```

---

### Post by sisco311 on 2010-12-08
> **idi0tf0wl said:**
> @sisco311 I love your style!

Thanks.

> **koenn said:**
> Yeah, it's beatiful, but it really should be done with a recursive function. That loop at the end looks a bit bolted on.


Cool!

Let me add some bugs by removing some unnecessary function calls.

diff:
```
--- 3	2010-12-09 02:23:54.147776233 +0200
+++ 1	2010-12-09 02:24:39.991036254 +0200
@@ -12,10 +12,11 @@
 
 function prints
 {
-  printl "$1 little bugs in the code,"
-  printl "$1 bugs in the code,"
-  printl "fix one bug, compile it again,"
-  printl "$(( $1+2 )) bugs in the code."
+  # added more bugs
+  printl "$1 little bugs in the code,
+$1 bugs in the code,
+fix one bug, compile it again,
+$(( $1+2 )) bugs in the code."
   echo
  
  # more bugs here

```

Anyone interested in a brainf?ck or LOLCODE version?

---

### Post by Dustin2128 on 2010-12-08
awesome! I think I'll *try* to write a perl version since that isn't covered.

---

### Post by nlsthzn on 2010-12-09
> **eric.proctor said:**
> On the contrary...

[http://xkcd.com/323/](http://xkcd.com/323/)

I lol'ed :D

---

### Post by Ozor Mox on 2010-12-09
> **sisco311 said:**
> Anyone interested in a brainf?ck or LOLCODE version?

If anyone writes a Malbolge version, I would buy them a beer in person :)

---

### Post by Bodsda on 2010-12-09
> **eric.proctor said:**
> I'm working on learning python currently, so I fixed the "bug" and added a feature (random bug counts) to the code posted earlier.
 
```

#!/usr/bin/env python
#Filename: programmers_song.py
 
import random
 
def main():
    bugs = 1
    iterations = 0
 
    print("One tiny little bug in the code\nOne tiny little bug.")
    print("Fix one bug, run it again")
 
    while True:
        bugs += random.randint(1,4)
        iterations += 1
        print "%i little bugs in the code\n%i little bugs." % (bugs, bugs)
        print "Fix one bug, run it again"
        if iterations >= 100:
            return False
 
if __name__ == '__main__':
    main()
```
 
Instead of having the if statement near the end, just modify your loop condition. 
 
```

#!/usr/bin/env python
#Filename: programmers_song.py
 
import random
 
def main():
    bugs = 1
    iterations = 0
 
    print("One tiny little bug in the code\nOne tiny little bug.")
    print("Fix one bug, run it again")
 
    while iterations < 100:
        bugs += random.randint(1,4)
        iterations += 1
        print "%i little bugs in the code\n%i little bugs." % (bugs, bugs)
        print "Fix one bug, run it again"
 
if __name__ == '__main__':
    main()
```
 
Bodsda

---

### Post by trivialpackets on 2010-12-09
> **Bodsda said:**
> Instead of having the if statement near the end, just modify your loop condition. 
 

Thank you!  Excellent catch!

---

### Post by nikefalcon on 2011-04-21
```

#/bin/bash
number=99
while :
Do
#sleep 1
echo -e "$number little bugs in the code,\n$number little bugs in the code,\n\
fix one bug,compile it again,"
number=$((number+1))
done

```lol

---

