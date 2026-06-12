---
title: "filename problem in bash script"
date: 2013-01-25
forum: Server Platforms
---

### Post by Toriku on 2013-01-25
I cobbled together a script using bits on the internet I found, to take a csv file of file locations, and copy those files into another tidier location:

> #!/bin/bash
INPUT=filenames.csv
OLDIFS=$IFS
IFS=,
[ ! -f $INPUT ] && { echo "$INPUT file not found"; exit 99; }
while read file1 file2 file3 file4 file5 file6
do
	cp $file1 /home/<user>/Audio/language1
	cp $file2 /home/<user>/Audio/language2
	cp $file3 /home/<user>/Audio/language3
	cp $file4 /home/<user>/Audio/language4
	cp $file5 /home/<user>/Audio/language5
	cp $file6 /home/<user>/Audio/language6
done < $INPUT
IFS=$OLDIFS



but when I run the script I get the error:
> 
cp: cannot stat `<filepath>\r': No such file or directory


on each file... I don't know where the "`" is coming from, and each item at the end of the row has what appears to be a newline "\r".

None of the files have copied, it can't find them, where did I go wrong?

---

### Post by steeldriver on 2013-01-25
Did the csv file originate from a Windows system? if so you may need to translate the \r characters e.g. pipe the file through tr

```
done < <(tr -d '\r' < $input)
```The "`" is just how stat reports filenames i.e. 

```
$ stat nofile
stat: cannot stat `nofile': No such file or directory

```

 [HINT: don't use all upper case variable names - you could also use a -d ',' delimiter to 'read' rather than messing with IFS, I think]

---

### Post by matt_symes on 2013-01-25
Hi

As well as following steeldrivers good advice, also wrap $file in quotes for each copy in case the filename/path contains spaces.

```
cp "$file1" /home/<user>/Audio/language1
...
```Kind regards

---

### Post by Toriku on 2013-01-25
> **steeldriver said:**
> Did the csv file originate from a Windows system? if so you may need to translate the \r characters e.g. pipe the file through tr

```
done < <(tr -d '\r' < $input)
```The "`" is just how stat reports filenames i.e. 

```
$ stat nofile
stat: cannot stat `nofile': No such file or directory

```

 [HINT: don't use all upper case variable names - you could also use a -d ',' delimiter to 'read' rather than messing with IFS, I think]


Yes, my csv file is from a windows system, I'll add that in, thanks


> **matt_symes said:**
> Hi

As well as following steeldrivers good advice, also wrap $file in quotes for each copy in case the filename/path contains spaces.

```
cp "$file1" /home/<user>/Audio/language1
...
```Kind regards


Yes I've just spotted that there are spaces in there (its really messy, hence this script), thanks

---

### Post by SeijiSensei on 2013-01-25
Install [tofrodos](http://manpages.ubuntu.com/manpages/precise/man1/fromdos.1.html) from the repositories.  It will strip the excess returns.  You can use it in a pipe, too.

---

### Post by Toriku on 2013-01-25
ok; thankyou for your help so far guys! I now have nearly 6000 relocated and renamed audio files, however; there are nearly 1000 missing.
 As these files have all come over from a windows system they've not bothered to make sure everything is case sensitive, so I've got nearly a thousand files that it 'can't find' because the case is different... Is there something I can do to ignore the case? Or if not, change the names of all the files to lower case...  :S

---

### Post by steeldriver on 2013-01-25
You could maybe replace the lines like

```
cp $file1 /home/<user>/Audio/language1
```with 

```
find . -ipath "./$file1" -exec cp -n -t "/home/<user>/Audio/language1/" {} **\;**
```which will perform a kind of case-insensitive lookup from the current dir (I think... haven't tested it)

Alternatively you could add another 'tr' that will convert all the filenames from the csv file to upper (if that is the correct way around? are the actual files all-upper or the names in the spreadsheet?) e.g.

```
done < <( (tr -d '\r' | tr '[:lower:]' '[:upper:]') < "$input")
```EDIT: added 'no-clobber' ("-n") because you probably don't want to overwrite files if the case-insensitivity produces non-unique names

---

### Post by Toriku on 2013-01-25
I got an error:
"find: missing argument to `-exec'"
on every attempt to copy

---

### Post by steeldriver on 2013-01-25
apologies - I omitted the terminator:

```
find . -ipath "./$file1" -exec cp -n -t "/home/<user>/Audio/language1/" {} **[COLOR=Red]\;[/COLOR]**
```

---

### Post by Toriku on 2013-01-25
the file-names' cases are erratic, there have been so many modifications to the files that there is no one pattern or style that they follow, some have descriptive names, some are capitals, some lower case, some numbers... Some are capitalised in the beginning of the name, and then the csv file that records each files location isn't necessarily written in the same case.

---

### Post by Toriku on 2013-01-25
> **steeldriver said:**
> apologies - I omitted the terminator:

```
find . -ipath "./$file1" -exec cp -n -t "/home/<user>/Audio/language1/" {} **[COLOR=Red]\;[/COLOR]**
```

magic! That seems to have sorted the case sensitivity problem, it returned no errors for any of the six and a half thousand files, however it didn't copy any of the files to the new location :S

> 
find . -ipath "./$file1" -exec cp -n -t "/home/<user>/Audio/language1/audio$count.mp3" {} \;
find . -ipath "./$file2" -exec cp -n -t "/home/<user>/Audio/language2/audio$count.mp3" {} \;
find . -ipath "./$file3" -exec cp -n -t "/home/<user>/Audio/language3/audio$count.mp3" {} \;
find . -ipath "./$file4" -exec cp -n -t "/home/<user>/Audio/language4/audio$count.mp3" {} \;
find . -ipath "./$file5" -exec cp -n -t "/home/<user>/Audio/language5/audio$count.mp3" {} \;
find . -ipath "./$file6" -exec cp -n -t "/home/<user>/Audio/language6/audio$count.mp3" {} \;
echo $count
count=$(( count + 1 ))


I also tried it without the -n, still nothing.. what does the -t do? I read that 'exec' causes the script to finish, could that be affecting it as well?

---

### Post by steeldriver on 2013-01-25
Hmm.. that probably just means that the 'find' is failing to find any of the files - that's probably because the pathname isn't an exact match even when case is taken out of the picture - sometimes these things need a bit of tweaking and I'm having to guess what your spreadsheet entries look like (do they have a leading / for example?)

It would help if you could post one or two specific examples i.e. exactly what the values of "$file1" and the supposedly matching filename are

---

### Post by steeldriver on 2013-01-25
it *should* work, I think e.g. here is a quick test of the basic idea:

```
$ touch "BiZZarRely nAmeD filE"
$ 
$ file="bizzarrely named file"
$ 
$ find . -ipath "./$file"
./BiZZarRely nAmeD filE
$ 
$ mkdir newdir
$ 
$ find . -ipath "./$file" -exec cp -vnt newdir/ {} \;
`./BiZZarRely nAmeD filE' -> `newdir/BiZZarRely nAmeD filE'
$ 
$ ls newdir/
BiZZarRely nAmeD filE
$ 

```

---

### Post by Toriku on 2013-01-28
well the filepaths are erratic..

> 
/home/user/NewYork/Update15Nov2011/******** DT/converted/nyect245.mp3

/home/user/NewYork/********/POR/GL DT POR Nov 28/GL DT POR 008.mp3

/home/user/NewYork/11Sept2012Update/mp3/English/DT ENG 014B.mp3


 However the software that processes the audio isn't case sensitive, and can run a validity check, which returns all mp3s found, so the csv file lists the correct directory's.

---

### Post by Toriku on 2013-01-28
for the time being I've solved the problem, by running the script on a Mac, as Macs aren't case sensitive, they are case preserving, the script worked fine with no problems. Marking as solved but open to better solutions for next time...

---

### Post by steeldriver on 2013-01-28
my apologies I completely missed that you were renaming the files (/../../**audio$count.mp3**) at the same time as copying them  - unfortunately 'cp -t' doesn't work in that case (-t specifies a target *directory* for the copy)

---

### Post by Toriku on 2013-01-28
> **steeldriver said:**
> my apologies I completely missed that you were renaming the files (/../../**audio$count.mp3**) at the same time as copying them  - unfortunately 'cp -t' doesn't work in that case (-t specifies a target *directory* for the copy)

 No need to apologise
 Thankyou for trying so hard, I really did appreciate your effort! :D

---

### Post by steeldriver on 2013-01-28
well it's ugly but you might be able to get it to work if you change each cp line to 

```

trufile=$(find . -ipath "./$file1")
if [ -f "$trufile" ]; then
  cp "$trufile" "/home/<user>/Audio/language1/audio$count.mp3"
fi
trufile=$(find . -ipath "./$file2")
if [ -f "$trufile" ]; then
  cp "$trufile" "/home/<user>/Audio/language2/audio$count.mp3"
fi
.
.
.

```

---

