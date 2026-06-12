---
title: "batch file reading text"
date: 2009-03-13
forum: The Cafe
---

### Post by FraggedLocust on 2009-03-13
I want to write a batch file for Windows that runs a command against each line in a text file.

I want to be able to run something like:

C:\>batch.bat variable1 list.txt

which executes:

command variable1 list.txt.line1
command variable1 list.txt.line2
command variable1 list.txt.line3
....

Where list.txt is a list of files that need to be acted upon
I'm just not sure how to make it read the text file and execute each line separately.
It may have to repeat this depending on how many lines are in the text file.

---

### Post by kestrel1 on 2009-03-13
I would put the commands in the batch file itself.

---

### Post by FraggedLocust on 2009-03-13
> **kestrel1 said:**
> I would put the commands in the batch file itself.

And I want to. I'm having trouble getting the batch file to read the text file that holds the names of the files. I don'r know how to do that. 

I don't know how many files the user want to run through the batch, so doesn't it make sense to have them create a text and read each line in as a parameter to a command?

list.txt
--------
file1
file2
file3
file4

Since the command only takes one file at a time (I've tried putting multiple files into the command), I want the batch file to run the command and be passed file1 separately from file2, in which it would execute the command again on file2.

---

### Post by walkerk on 2009-03-13
Why don't you use VBscript or even better Powershell. Batch scripts are very limited in their capabilities. If you decide to take a look at Powershell (the future of Windows CLI), let me know... I can help.

---

### Post by koenn on 2009-03-13
```
FOR /F %%i IN ( list.txt ) DO command %%i
```
%%i is a variable;
eg ```
FOR /F %%i IN ( list.txt ) DO copy %%i copy_of_%%i 
```
will copy file1.txt to copy_of_file1.txt, same for file2, etc for all items in list.txt.

[http://www.ss64.com/nt/for_f.html](http://www.ss64.com/nt/for_f.html)

---

### Post by FraggedLocust on 2009-03-17
How would I read newline characters as a delimiter? If the strings are each on a separate line, will the batch use that as a space delimiter and use the second line for the second run of the program?

---

### Post by koenn on 2009-03-17
yes

---

### Post by HermanAB on 2009-03-17
How to make a batch file read text?

$ festival --tts file.txt

See this: [http://aeronetworks.ca/text-to-speech-howto.html](http://aeronetworks.ca/text-to-speech-howto.html)
;)

Cheers,

Herman

---

### Post by FraggedLocust on 2009-03-20
> **HermanAB said:**
> See this: [http://aeronetworks.ca/text-to-speech-howto.html](http://aeronetworks.ca/text-to-speech-howto.html)
;)

Cheers,

Nice, but I'm looking for something more practical ;)

So far I have this:

```
FOR /F %%i IN (shapefiles.txt) DO shp2sqlserver.exe "Data Source=SQLDataSourceGoesHere" %%i
```

The text file contains a list of shapefiles like this:

```
C:\Documents and Settings\username\My Documents\Shapes\world_ifl_block02.shp
C:\Documents and Settings\username\My Documents\Shapes\world_ifl_block03.shp
C:\Documents and Settings\username\My Documents\Shapes\world_ifl_block10.shp
C:\Documents and Settings\username\My Documents\Shapes\world_ifl_block11.shp
C:\Documents and Settings\username\My Documents\Shapes\world_ifl_block12.shp
C:\Documents and Settings\username\My Documents\Shapes\world_ifl_block13.shp
```

But when I run this batch, I get:

```
C:\Documents and Settings\username\My Documents\cumberland-0.4.1>shp2sqlserver.
exe "Data Source=SQLDataSourceGoesHere" C:\Documents

Unhandled Exception: System.IO.FileNotFoundException: Could not find file 'C:\Documents'.
```

I've tried putting all manner of quotes in both the batch file and text file and I still get variants of the error. I've tried using " and ' and \' and \".

I figure it's still reading space characters as a delimiter. How do I stop the batch from reading them?

---

### Post by koenn on 2009-03-20
> **FraggedLocust said:**
> 
I figure it's still reading space characters as a delimiter. How do I stop the batch from reading them?
It's more likely the filenames get passed to the windows shell (cmd.exe) correctly  -- you'd have to use additional options for FOR to see whitespace as a delimiter -- but that the *shell* sees the whitespace as a delimiter, and/or that shp2sqlserver.exe sees C:\Documents as the first of a list of arguments

you can check this by running
```
FOR /F %%i IN (shapefiles.txt) DO echo %%i
```
this should give you your file path names


Did you try quoting like this :```
FOR /F %%i IN (shapefiles.txt) DO shp2sqlserver.exe "Data Source=SQLDataSourceGoesHere" "%%i"
``` 


you can probably also avoid the problem like this
```

C:
cd "C:\Documents and Settings\username\My Documents\Shapes"
FOR /F %%i IN (shapefiles.txt) DO .....  %%i

```
you 'd have to modify shapefiles.txt so that it contains only filenames, not absolute paths (with spaces)

---

