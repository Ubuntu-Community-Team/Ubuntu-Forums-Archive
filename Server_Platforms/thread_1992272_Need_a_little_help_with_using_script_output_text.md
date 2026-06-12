---
title: "Need a little help with using script output text"
date: 2012-05-31
forum: Server Platforms
---

### Post by legolas_w on 2012-05-31
Hi,

I need to use an script from within a script I am writing. the script which I need to invoke as part of my script returns the following text


```

=========
books=       123
------------
magazines=        628
------------
multimedia=   27
=========

```

How can I parse this output and put each one of the output values into a separate variable named books, magazines...?

Thank you.

---

### Post by spynappels on 2012-05-31
Can you give a little more info on the scripting language, and whether the output from the first scrip is in a file or just as a stdout stream.

This isn't a homework question, is it?

---

### Post by papibe on 2012-05-31
Hi legolas_w.

What language are you using? Is it a awk script? Bash, Python?

Regards.

---

### Post by legolas_w on 2012-05-31
Sorry, I forgot that we can do the script in many languages. I am using bash (shell scripting). So I assume that awk, sed and perl can be used inside my script to check the output. The output is in stdout stream (screen and not a file).

No it is not homework. I am writing my first large script and some places I can figure out on my own (where we need sed, perl or awk to get the part done.)

Thanks.

---

### Post by papibe on 2012-05-31
You can get the 2nd column of line that start with a known pattern using awk:
```
awk '/^books=/{print $2}' input.txt
```
Where:
[INDENT]/^book=/ selects only the lines that start with 'book='
print $2 prints the 2nd column.[/INDENT]
The result will be:
```
123
```
In order to assign it to a variable in bash you use the $() expression:
```
books=$(awk '/^books=/{print $2}' input.txt)
```
I hope that helps, and points you in the right direction.
Regards.

---

### Post by legolas_w on 2012-05-31
Thank you, superb. I fixed the script and can read all variables using the same technique.

am I correct that awk assumes the space between the texts as the field separator by default?

---

### Post by papibe on 2012-05-31
> **legolas_w said:**
> am I correct that awk assumes the space between the texts as the field separator by default?

Indeed.

You can change it easily using awk's -F option. For instance, if you want the '=' to be your separator:
```
awk -F'='  '/^books=/{print $2}' input.txt
```
Note that this would put the spaces into the 2nd column now:
```
       123
```
(that is a string that stars with several spaces and trails the value '123').

Regards.

---

### Post by matt_symes on 2012-05-31
Hi

There are a whole load of ways to do this and papibe has shown you an excellent example using awk.

I just thought i would show another method using bash parameter expansion.

This is only a very basic script and could be made far more robust. The important lines are highlighted in bold.

```
#!/bin/bash

book_num=
mag_num=
media_num=

while read line;
do
        # Paramater expansion
        [B]tmp_left=${line%=*};
        tmp_right=${line##* };[/B]

        # Match up and save .
        case "$tmp_left" in
                books)
                book_num="$tmp_right";
        ;;
                magazines)
                mag_num="$tmp_right";
        ;;
                multimedia)
                media_num="$tmp_right";
        ;;
                *)
                # ignore ??
                ;;
        esac

done < "$1";

echo "Number of books = $book_num";
echo "Number of magazine = $mag_num";
echo "Number of multimedia = $media_num";
```

```
matthew@matthew-Aspire-7540 ~ % cat t
=========
books=       123
------------
magazines=        628
------------
multimedia=   27
=========
matthew@matthew-Aspire-7540 ~
```

```
matthew@matthew-Aspire-7540 ~ % ./tt.sh t 
Number of books = 123
Number of magazine = 628
Number of multimedia = 27
matthew@matthew-Aspire-7540 ~ % 
```

For a basic introduction to the commands

[http://mywiki.wooledge.org/BashGuide/Parameters](http://mywiki.wooledge.org/BashGuide/Parameters)

Kind regards

---

