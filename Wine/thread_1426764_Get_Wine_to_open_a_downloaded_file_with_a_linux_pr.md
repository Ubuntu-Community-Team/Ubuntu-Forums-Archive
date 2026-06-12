---
title: "Get Wine to open a downloaded file with a linux program"
date: 2010-03-10
forum: Wine
---

### Post by Tukanfan on 2010-03-10
Hi there!

I have a little irritating problem here (nothing big). 
My school are unfortunately using the [FirstClass system]("http://www.firstclass.com") from Open Text Corporation. I find the Linux-version of the program reasonable slow and buggy, so I'm using the Windows-version through Wine. 

It performs the vast majority of tasks without any problems, but when it comes to open an OpenDocument file/attachment (yes, just dubble-clicking on it) it saves it to a tempoary folder, and then Wine explorer complains about that there isn't any program associated with the filetype .odt. Are there any ways to associate that file with a linux program as OpenOffice?

I hope you guys can help ;)

Regards!

PS. I've tried to install MSO2007 and then wine recognizes .doc and .docx-files and opens them with MSO. It has something to do with the registry right?

PPS. I want to use OOO (Linux version) not MSO or OOO (Windows version):D

---

### Post by asdfoo on 2010-03-10
> **Tukanfan said:**
> Hi there!

I have a little irritating problem here (nothing big). 
My school are unfortunately using the [FirstClass system]("http://www.firstclass.com") from Open Text Corporation. I find the Linux-version of the program reasonable slow and buggy, so I'm using the Windows-version through Wine. 

It performs the vast majority of tasks without any problems, but when it comes to open an OpenDocument file/attachment (yes, just dubble-clicking on it) it saves it to a tempoary folder, and then Wine explorer complains about that there isn't any program associated with the filetype .odt. Are there any ways to associate that file with a linux program as OpenOffice?

I hope you guys can help ;)

Regards!

PS. I've tried to install MSO2007 and then wine recognizes .doc and .docx-files and opens them with MSO. It has something to do with the registry right?

PPS. I want to use OOO (Linux version) not MSO or OOO (Windows version):D

yes, it's as simple as setting a file type association to open with z:\usr\bin\oowriter (or whatever the linux path is to oowriter)

it might be of the form:

z:\usr\bin\oowriter %1

I think you can set the association with 'ftype' from cmd, atleast that's how you'd do it on windows iirc.

---

### Post by Tukanfan on 2010-03-11
Hi, and thankyou for your reply and your tip!

I've now tried to do the following:

wine cmd  #To get the cmd prompt

then:
assoc .odt=odtfile
ftype odtfile="z:\usr\bin\oowriter" "%1" (some documentation on the commands are available [here]("http://commandwindows.com/assoc.htm"))

Unfortunately it seems that there are problems with the wine cmd. If you take a look at the attached screenshot you will see, that cmd (or the program) hasnt "read" the whole argument. I find that strange...

Are you sure there are no other ways to do it?

---

### Post by Tukanfan on 2010-03-11
Okay, i did find a solution myself.

Here it comes:

First, open a terminal as normal user, and do this:
```

wine cmd
assoc .odt=odtfile
ftype odtfile="z:\usr\bin\your_word_processor" "%1"

```
Note, that the .odt-extension and odtfile can be replaced by any extension and any name you like.

Now, try this:
```

assoc
ftype

```

You'll probably notice by the output that both of the programs didn't get the whole arguments you gave them. Therefore you'll have to open the registry-editor:
```

regedit

```

Now press CTRL+F (or select edit -> find) and search after odt (or whatever extension you may have decided)

You should find a key (a folder) called .odt in HKEY_LOCAL_MACHINE\Software\Classes (if not, search again)

In that key there should be a value with some data (probably odtf). Now change that data to the filetypename you want (in my case odtfile).

In the same directory (Classes) you should find a key with the malformed filetypename from the ftype output. Change that name to the filetypename you set in the previous key.
If you expand the key (clicking the plus mark againg and again) you should end up with a key saying "Command". In that key, change the values data to "z:\home\yourname\odfhandler.py" "%1"

Then download the attached python-script and modify it with your values and place it in your home-directory (or somwhere else, just remember to change the value in the "Command"-key respectively)

I think it should work now...

Regards

PS. I know my python script is a very simple one, and you could definately write a better one :D

---

