---
title: "[SOLVED] Trouble generating reliable MD5's in Ubuntu..."
date: 2008-12-06
forum: Security
---

### Post by shaggy999 on 2008-12-06
I was looking into generating md5sum's of passwords and ran into a little trouble. I used two seperate "online md5 calculators" to generate md5's and they both agreed with each other. But when I generate an md5sum using the md5sum command on my computer I get a completely different result! Anybody have any idea what is going on? Here's an example:

Password: secret 

[http://md5-hash-online.waraxe.us/:](http://md5-hash-online.waraxe.us/:)        5ebe2294ecd0e0f08eab7690d2a6ee69
[http://www.fileformat.info/tool/hash.htm:](http://www.fileformat.info/tool/hash.htm:) 5ebe2294ecd0e0f08eab7690d2a6ee69
echo "secret" | md5sum:                   dd02c7c2232759874e1c205587017bed

Interestingly enough, I performed an md5sum on a local copy of my ubuntu-8.04.1-desktop-i386.iso file and it MATCHED the MD5SUM file.

---

### Post by shaggy999 on 2008-12-06
I'm starting to wonder, is generating an MD5 different from generating an MD5SUM?

---

### Post by Dr Small on 2008-12-06
> **shaggy999 said:**
> I'm starting to wonder, is generating an MD5 different from generating an MD5SUM?
```
<?php
echo md5("secret");
?>

Result:
5ebe2294ecd0e0f08eab7690d2a6ee69
```

```
echo "secret" | md5sum 
dd02c7c2232759874e1c205587017bed  -
```

Apparently there is.

---

### Post by lordadi on 2008-12-06
Interesting:

```
echo "secret" | md5sum
dd02c7c2232759874e1c205587017bed  -

```

vs.

```

echo "secret" | md5
dd02c7c2232759874e1c205587017bed

```

They are the same! (except for the "-")!!


Lordadi.

---

### Post by kevdog on 2008-12-06
Not sure how to explain this right now

---

### Post by Dr Small on 2008-12-06
> **kevdog said:**
> Not sure how to explain this right now
We have stumped the cryptologist! :D
All laughing aside, I am rather perplexed too, and would like to know the difference between the php md5() function and md5sum.

---

### Post by lordadi on 2008-12-06
Hi,

I say that there is a difference in the way the site handles MD5 and Ubuntu handles it because @ [http://www.fileformat.info/tool/md5sum.htm]("http://www.fileformat.info/tool/md5sum.htm") uploading a file with string "secret" gives the same hash (choose to view the file, not the binary).


For comparison, I have attached the txt that I  uploaded. 

The various results I get:

```

echo "secret"|md5
dd02c7c2232759874e1c205587017bed

and 

echo "secret"|md5sum
dd02c7c2232759874e1c205587017bed  -

and (from the site's file upload):

dd02c7c2232759874e1c205587017bed

and from your second link:

5ebe2294ecd0e0f08eab7690d2a6ee69


```

This leads me to say that Sun/Java's way of doing MD5 is different.



LordAdi.

---

### Post by shaggy999 on 2008-12-06
I figured it out. When you use echo it automatically inserts a newline at the end of your text. So I was actually running md5sum on "secret\n". To get it to work right you have to do:

echo -n secret | md5sum

DOH!

---

### Post by Dr Small on 2008-12-06
> **shaggy999 said:**
> I figured it out. When you use echo it automatically inserts a newline at the end of your text. So I was actually running md5sum on "secret\n". To get it to work right you have to do:

echo -n secret | md5sum

DOH!
Yep, that's the problem. Thanks for explaining that! :)

---

### Post by kevdog on 2008-12-06
Hmm

I did not know that echo was passing a /n in a pipe.  That is interesting.  Thanks.

---

