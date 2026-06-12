---
title: "sed replacing new line and &quot;"
date: 2012-07-06
forum: Server Platforms
---

### Post by MitsuTomoe on 2012-07-06
Hi ,
I've got a file whose last characters are \n"\n (line feed characters)
I'd like to change this to \n , i.e suppress character " and one line feed.
I tried : sed --in-place -e "s/\n\"\n/\n/g" 1131422.xml but it seems to do nothing.

I'm on Ubuntu 12.04 Server.
Thank you for helping

---

### Post by codemaniac on 2012-07-06
Hi ,

Your requirement is not that clear .
Can you please post a snippet of your xml file ?

---

### Post by steeldriver on 2012-07-06
you need special tricks (specifically the 'N' command) to make sed read across newlines, something like

```
sed '$!N;s/\"\n//' myfile
```

(if not EOF then append next line, then search the result for literal " followed by newline and replace with nothing)

---

### Post by MitsuTomoe on 2012-07-06
It didn't work . I did :
sed --in-place -e '$!N;s/\"\n//' 1131422.xml

Here is the end of my file :

</biens>
"

---

### Post by steeldriver on 2012-07-06
how about

```
sed '$!N;s|\n\"||' myfile
```or if you want to match the final text explicitly,

```
sed -r '$!N;s|(</biens>)(\n\")|\1|' myfile
```

---

### Post by MitsuTomoe on 2012-07-06
Both expressions didn't work. Perhaps it's impossible ???

---

### Post by sudodus on 2012-07-06
> **MitsuTomoe said:**
> Both expressions didn't work. Perhaps it's impossible ???
I think it is possible, but we don't understand what your file looks like. Please attach a sample from your file: Is it only one instance of that expression to be changed (at the very end)?

> line-feed doublequote line-feed
and you want that sequence to change to
> line-feed

Or are there several instances with such line-feeds?

Does it look like this in a text editor?
```
line 1
line 2
...
last-line-but-one
"
```
so that it means you should delete the last line?

Or are there several instances, so that you should delete several lines containing only a double-quote?

Anyway, try
```
grep -v \" 1131422.xml > output.xml
```

---

### Post by wojox on 2012-07-06
```
sed 's/\n//' file
```
[Why can't I match or delete a newline using the \n escape sequence?]("http://sed.sourceforge.net/sedfaq5.html#s5.10")

---

### Post by codemaniac on 2012-07-07
what about using tr to suppress newline and " combination .

```
tr -d '\n"' < example.xml
```

However a snippet of the xml file would help to test properly .

---

### Post by MitsuTomoe on 2012-07-07
tr did not work either . I attached the culprit : 1131422.txt . There is only random data in it.

---

### Post by sudodus on 2012-07-07
> > **MitsuTomoe said:**
> tr did not work either . I attached the culprit : 1131422.txt . There is only random data in it.
> **MitsuTomoe said:**
> Both expressions didn't work. Perhaps it's impossible ???
I think it is possible, but we don't understand what your file looks like. Please attach a sample from your file: Is it only one instance of that expression to be changed (at the very end)?

[QUOTE]line-feed doublequote line-feed
and you want that sequence to change to
> line-feed

Or are there several instances with such line-feeds?

Does it look like this in a text editor?
```
line 1
line 2
...
last-line-but-one
"
```
so that it means you should delete the last line?

Or are there several instances, so that you should delete several lines containing only a double-quote?

Anyway, try
```
grep -v \" 1131422.xml > output.xml
```
[/QUOTE]
Try the grep command again. It works for me :-)

Use the appropriate extension (xml or txt) depending on the file name

```
grep -v \" 1131422.txt > output.txt
```

---

### Post by MitsuTomoe on 2012-07-07
grep -v delete first line . I only want last " in file to disappear .

---

### Post by codemaniac on 2012-07-07
```
sed 's/"$//g' example.xml
```

will remove the concerned " on the xml file .

---

### Post by MitsuTomoe on 2012-07-07
It works ! Thanks a lot .

---

### Post by sudodus on 2012-07-07
> **MitsuTomoe said:**
> grep -v delete first line . I only want last " in file to disappear .
OK, with the $ sign (denoting it is the last character of the line, it works with grep.
```
grep -v \"$ 1131422.txt > output.txt
```

But *codemaniac* was faster doing it with sed ;-)

By the way, is this something that you have to do repeatedly (and automatically)?

     -o-

*Edit:* For those who need stream editing of truly binary files, there are ***bvi*** and ***gsar***. bvi is in the repositories and gsar can be compiled or run via wine.

The task of this thread can be solved with the following gsar command line
```
wine gsar -fs:x0a:x22:x0a -r:x0a 1131422.txt output.txt
```
[[COLOR="Red"]_http://home.online.no/~tjaberg/_[/COLOR]]("http://home.online.no/~tjaberg/")

---

### Post by MitsuTomoe on 2012-07-07
Yes it will be done every day .

---

