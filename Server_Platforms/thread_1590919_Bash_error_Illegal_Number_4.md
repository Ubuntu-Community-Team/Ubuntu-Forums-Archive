---
title: "Bash error: Illegal Number: 4"
date: 2010-10-08
forum: Server Platforms
---

### Post by gunghogarrett on 2010-10-08
Hello, Below is part of a script I'm working on.  I have a problem with this section though.  When I run the script and $MIN is -gt $MAX, i get an illegal number error, as follows:

[: 35: Illegal number: 4

When searching online, the other scripts with this problem were quite different in function.  This error does not appear to affect script operation, but i'm not sure yet if that's true.  Any ideas?

```

MAX="9"
MIN="`du /repo/daily/ | awk '{print $1}'`"

if [ "$MIN" -lt $MAX ]; then
        mkdir $yesterday
        else
        continue
fi

ls $daily | egrep -v dirlist  | egrep -v `date +%Y%m%d` | sort -n | tail -1 > $dirlist

for i in $(cat $dirlist)
do
if [ $i -eq `date +%Y%m%d -d "-1 day"` ]; then
         continue
         else
         if [ $i -ne `date +%Y%m%d -d "-1 day"` ]; then
         mkdir $yesterday
         cp -al $i/*.deb $yesterday
         continue
         fi
fi
done

```

---

### Post by lloyd_b on 2010-10-08
I would suggest adding some echoes to that code.  Specifically, have ```
echo $MIN[CODE] before that comparison line.

You will get that "illegal number" error if the 'du' command is returning a multi-line response.  For instance, here's the output of the du | awk on a particular directory on my machine:[CODE]lloyd@dell:~/stuff$ du
4    ./sub
43780    .

``` and when I run it through a test script and attempt to compare that against a number, I get the following:```
[: 10: Illegal number: 4
43780
ONE is *not* less than TWO
```Net result is if there is a subdirectory under the directory specified, it'll generate that "Illegal Number" error.

Perhaps you should be using "du -s" to summarize the output from 'du', so that it's guaranteed to produce only a single line of output?

Lloyd B.

---

### Post by asmoore82 on 2010-10-09
Variable references in Bash scripts should almost always be quoted.
This is good practice and can eliminate all kinds of sneaky bugs before they happen.

Also, any for loop in the form of "for something in $( ... )" is asking for trouble.
The for loop list is parsed by the shell's rules and splits on any whitespace.
Splitting by lines is almost always the intended behavior,
This is better accomplished with a "while read" loop...

```
#!/bin/bash

#This quotes the entire file - the loop will only be run once.
#for line in "$( cat $file )"
#do
#    echo "$line"
#done
#
#This has the quotes moved to the right place,
# but will break on whitespace, possibly looping too many times.
#for line in $( cat "$file" )
#do
#    echo "$line"
#done

#This is the only one that actually does what it is meant to -
# echo-ing or looping only one whole line at a time...
cat "$file" | while read line
do
    echo "$line"
done
```
^The only catch is that variables set within the while loop are only valid within it.
It could be argued that this a feature instead of a bug because it is
almost like real namespace/scope control of a full programming language.

The most shell friendly way to use this to your advantage is to keep the pipeline alive
after the while loop - this way "echo" statements within the loop act like proper return values...
```
#!/bin/bash

# A simple line numberer - the last `cat` is just for fun!
count="0"
cat "$file" | while read line
do
    echo "$((++count))> $line"
done | cat > "${file}.numbered"

#Caveat - This will still say "0" (Zero)!!!
echo "The final count is $count"
```

---

### Post by gunghogarrett on 2010-10-11
Lloyd_b,

The du -s actually fixed the problem.  The script works as it's supposed to now.  Thanks for everyone's input.

---

