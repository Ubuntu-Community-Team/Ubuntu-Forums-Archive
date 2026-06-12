---
title: "Generate Excel or Text File from a Directory?"
date: 2010-08-03
forum: The Cafe
---

### Post by Kdar on 2010-08-03
I have a directory where I keep all my movies (with folders for each movie inside of it). How can I general a text file or excel file from there? So that I can keep truck of what movies I have and what I do not.

---

### Post by RiceMonster on 2010-08-03
cd /video/directory/
ls -lR > movies.txt


or are you looking to do it based on tags?

---

### Post by Confuzius on 2010-08-03
You can also do it to movies.csv and excel or calc should be able to import it and save as a spreadsheet.

---

### Post by Kdar on 2010-08-03
thanks. I forgot I could send output from terminal to a file!

How can I do it with tags?

---

### Post by RiceMonster on 2010-08-03
> **Kdar said:**
> How can I do it with tags?

You would have to find a command line program that reads video tags, and then have it recursively read all the tags of your videos. It wouldn't be as simple as doing it by file names.

---

### Post by Kdar on 2010-08-03
> **Confuzius said:**
> You can also do it to movies.csv and excel or calc should be able to import it and save as a spreadsheet.

what is movies.csv?

---

### Post by alphaniner on 2010-08-03
csv stands for comma separated values.  It is a way of formatting a text file so that it can be imported by excel (etc) as a table.

[wikipedia: csv]("http://en.wikipedia.org/wiki/Comma-separated_values")

---

### Post by ajgreeny on 2010-08-03
csv = a file of type "comma separated values".  csv files are opened by default in spreadsheets usually, ie OOo Calc in ubuntu.

---

### Post by LowSky on 2010-08-03
If you want to do it in Windows you can create a simple .bat file that will do just that

open notepad

type

```
dir *location of info* > report.xls
```

mine looks like this

```
dir C:\home\input > Report.xls
```
save the file as runreport.bat or *whatever*.bat

when it runs it should place a file name report.xls on in the same folder as the .bat.

---

### Post by aromo on 2010-08-03
try

find /video/directory -exec ls -la {} \; > report.txt

---

