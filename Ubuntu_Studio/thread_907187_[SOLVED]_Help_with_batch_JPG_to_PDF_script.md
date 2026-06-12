---
title: "[SOLVED] Help with batch JPG to PDF script"
date: 2008-09-01
forum: Ubuntu Studio
---

### Post by quanumphaze on 2008-09-01
Hello all.

I need to convert a lot of JPG images inside many folders into PDFs, one per folder. (Scans from stuff)

I currently can do it manually by running ImageMagick```
convert *.jpg something.pdf
```But that requires me to attend to the computer to run it for every folder after n minutes. I would really like to be able to automate this process and let it run overnight, but I don't know how to make bash scripts (or any scripts).

The specific job is that I have to enter many directories inside ~/jpegs like ~/jpegs/first and convert all the jpeg images into the one pdf with the same name as the containing folder (first.pdf) into another folder ~/pdfs

So it runs ```
convert ~/jpegs/first/*.jpg ~/pdfs/fist.pdf
convert ~/jpegs/second/*.jpg ~/pdfs/second.pdf
#and so on
```

It may be easier to just dump the pdf inside the jpeg folders instead of their own separate folder, I don't mind having to fetch them.

Any help or alternatives (or links to how to script :p) would be greatly appreciated.

---

### Post by kaibob on 2008-09-01
I'm new to shell scripting, but the following appears to work.

> #!/bin/bash
for i in $(find /source/directory -type d) ; do
pdfname=$(basename ${i})
convert ${i}/*.jpg ${i}/${pdfname}.pdf
done

If a source directory or file contains spaces, some quoting of variables will be necessary. Also, you need to insert the /source/directory. Initially, as a precaution, be sure to use this script on copies of the source files just in case. 

Perhaps a more experienced forum member will have an alternative or better way of doing this.

---

### Post by quanumphaze on 2008-09-01
Thanks, worked perfectly, just what I needed.

Only problems however are ,as you mentioned, that it chokes on folders with spaces in them unless I use double quotes and find also passes on the containing directory. The finished product being:```
#!/bin/bash
 for i in $(find /home/me/misc/jpegs -type d) ; do
 pdfname=$(basename "${i}")
 convert -verbose "${i}"/*.jpg "${i}"/${pdfname}.pdf
 done
```

-$ find spits out:```
find /home/me/misc/jpegs -type d
/home/me/misc/jpegs
/home/me/misc/jpegs/test1
/home/me/misc/jpegs/test2
```
The find problem however has no effect as convert just finds no *.jpg there and continues n happily.

Thanks again.

---

### Post by kaibob on 2008-09-02
I was unable to get the script to work with directories that contained spaces even after enclosing the variables in double quotes. With ghostdog74's help, I came up with the following which works with both directories and files that contain spaces:

> find /source/directory -type d | while read FOLDER ; do
FILE=$(basename "${FOLDER}")
convert "${FOLDER}"/*.jpg "${FOLDER}"/"${FILE}.pdf"
done 

The earlier script appears to work for you, so no need to change. I wanted to get this to work correctly just to learn.

---

### Post by Creative2 on 2008-09-03
fuoco tools can handle that command line 

convert INPUT OUTPUT

see my signature

---

### Post by quanumphaze on 2008-09-03
[QUOTE="Creative2's sig"]Fuoco universal converter
[http://fuoconverter.wordpress.com/](http://fuoconverter.wordpress.com/)[/QUOTE]

Looks very promising and hopefully will make it in the official repositories in a future Ubuntu version. Good luck with your web hosting problem.

---

