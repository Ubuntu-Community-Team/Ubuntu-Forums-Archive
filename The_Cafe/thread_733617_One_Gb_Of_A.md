---
title: "One Gb Of A"
date: 2008-03-24
forum: The Cafe
---

### Post by silentabe939 on 2008-03-24
Okay so I have an odd question. What would a .txt document that consists of nothing but the lowercase "a" character repeated to fill one gigabyte of space look like? How many pages would that be following MLA format? How small of a file could i compress that to? Finally is there some way to write a program that would acomplish the task of creating a 1gb "a" file? Thanks for the help.

---

### Post by hhhhhx on 2008-03-24
> **silentabe939 said:**
> How many pages would that be following MLA format?
depends, are you using a header, and also a works cited page?

---

### Post by jpkotta on 2008-03-24
> **silentabe939 said:**
> Okay so I have an odd question. What would a .txt document that consists of nothing but the lowercase "a" character repeated to fill one gigabyte of space look like? How many pages would that be following MLA format? How small of a file could i compress that to? Finally is there some way to write a program that would acomplish the task of creating a 1gb "a" file? Thanks for the help.

That is an odd question.  Care to say why you want to know?

The file would look very monotonous.

I don't know about MLA any more.  I haven't used that braindead style since high school.

It should compress to a very small size.  In fact, files with compression ratios like that are dangerous.  They're called tarbombs, and can be used to maliciously fill someone's hard disk.

It's easy to create the file with a shell script:
```

echo -n a > file 
for i in $(seq 1 15) ; do
    cat file file > temp
    cat temp temp > file
done

```

---

### Post by happysmileman on 2008-03-24
> **jpkotta said:**
> It should compress to a very small size.  In fact, files with compression ratios like that are dangerous.  They're called tarbombs, and can be used to maliciously fill someone's hard disk.

Yup, I've seen 7MB zip files that decompress to over 100GB. In theory a GB of 'a' could probably be compressed to FAR less than a megabyte, but I'm not sure exactly how the compression/decompression systems work.

---

### Post by jpkotta on 2008-03-24
> **happysmileman said:**
> Yup, I've seen 7MB zip files that decompress to over 100GB. In theory a GB of 'a' could probably be compressed to FAR less than a megabyte, but I'm not sure exactly how the compression/decompression systems work.

I got mine to compress to 768 bytes with bzip2.  How much it compresses is dependent upon what you define as a decompressor.  See [http://en.wikipedia.org/wiki/Kolmogorov_complexity](http://en.wikipedia.org/wiki/Kolmogorov_complexity).  The only information in the file is that it contains 2^30 'a's.

---

