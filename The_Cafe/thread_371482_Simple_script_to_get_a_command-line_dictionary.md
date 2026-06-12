---
title: "Simple script to get a command-line dictionary"
date: 2007-02-27
forum: The Cafe
---

### Post by IYY on 2007-02-27
First, make sure that you have the Lynx web browser:

```
sudo apt-get install lynx
```

Now, make the following script:

```
#!/bin/sh

lynx -dump "http://wordnet.princeton.edu/perl/webwn?s=**$1**" | grep -B 1000 References | grep -A 1000 relations | less
```

Now you can define any word from the terminal. For example, suppose I want to know the definition of 'psychoanalysis', I can simply run:

```
./define psychoanalysis
```

and get the definition printed out.

```

   Key: "S:" = Show Synset (semantic) relations, "W:" = Show Word
   (lexical) relations

  Noun

     * [4]S: (n) psychoanalysis, [5]analysis, [6]depth psychology (a set
       of techniques for exploring underlying motives and a method of
       treating various mental disorders; based on the theories of
       Sigmund Freud) "his physician recommended psychoanalysis"

   [7]WordNet home page
References

```

It's nothing fancy; just grabs the output from an online dictionary and spits it out to the terminal, but I find it to be very useful.

---

### Post by Spr0k3t on 2007-02-27
Quite niphty.  Thanks for the suggestion.

---

### Post by Ob1 on 2007-02-27
Is it possible to request the definition from dictionary.com, since it's my preferred online dictionary.

---

### Post by GrimRazer on 2007-02-27
very handy IYY
Thanks

---

### Post by grte on 2007-02-27
You should look into the dict package.

---

### Post by Erunno on 2007-02-27
Very nice, thanks for sharing that with us :D

---

### Post by fieroboom on 2009-03-18
> **Ob1 said:**
> Is it possible to request the definition from dictionary.com, since it's my preferred online dictionary.

Yes.
...but it would be more in-depth, such as perl + curl + some perl regex ninjitsu. :D
-Paul

---

### Post by lautarop on 2009-06-08
hey, is there any way to use google dictionary instead?

---

### Post by SoulSmasher on 2009-06-14
this post brings google translate as a terminal program
[http://ubuntuforums.org/showpost.php?p=6870143&postcount=3](http://ubuntuforums.org/showpost.php?p=6870143&postcount=3)

but sadly google still doesn't open its api for the dictionary

---

### Post by lautarop on 2009-06-15
well that's pretty cool too!
thx!

---

### Post by JayCarman on 2009-11-03
Very useful!  The URL has changed slightly since the original post:

```
#!/bin/sh

lynx -dump "http://wordnetweb.princeton.edu/perl/webwn?s=$1" | grep -B 1000 References | grep -A 1000 relations | less

```

---

### Post by davidgutu on 2010-11-18
when you say 'add a script, ' how do I do that?
thanks

---

### Post by JayCarman on 2010-11-19
> **davidgutu said:**
> when you say 'add a script, ' how do I do that?
thanks

Simply open your favorite text editor, paste in the code, and save it using a name that makes sense (something like *define*).  Next, you'll need to change permissions to allow you to execute it.

```
chmod 755 <filename>
```

Be sure to change <filename> to the actual name you chose.  That's how you 'add a script'!  :D

---

