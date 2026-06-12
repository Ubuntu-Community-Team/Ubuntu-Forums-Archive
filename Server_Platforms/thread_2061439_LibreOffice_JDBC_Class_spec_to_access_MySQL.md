---
title: "LibreOffice JDBC Class spec to access MySQL"
date: 2012-09-22
forum: Server Platforms
---

### Post by mike acker on 2012-09-22
uh-oh an un-washed n00b again:(

I've located and downloaded the JDBC package from the MySQL site. this came as 
my-connector-java-5.1.22.tar.gz
which i then extracted to obtain the
my-connector-java-5.1.22
folder.

the breakdown occurs in LibreOffice help files where it says
select a folder and add the folder to the class path

um,-- there are lots of folders in the downloaded zip.

if anyone knows which one to select -- and how to write it -- please let me know !!
I tried:
/JDBC/my-connector-java-5.1.22-bin.jar and
Home/JDBC/my-connector-java-5.1.22-bin.jar

obviously I don't know what I'm doing:confused: Home/JDBC -- is the directory I created for the extract of the .gz

---

### Post by mike acker on 2012-09-22
holy rat-scratchers!!!!! down in the LibreOffice HELP file I found it!!!!!

it sez: 
Chose: TOOLS | OPTIONS | LIBREOFFICE | JAVA 
and press the CLASS PATH

after this it offered add archive or add folder

I browsed it to the folder  I had unpacked from the .gz and after that the test connection succeeded !!!!! 

it sez to restart LibreOffice.  I fogot that in my enthusiasm and after the connection timed out i was able to end LibreOffice and restart it

then i got into my MySQL DB.

now it's time for lunch and then i'll play with it more

---

