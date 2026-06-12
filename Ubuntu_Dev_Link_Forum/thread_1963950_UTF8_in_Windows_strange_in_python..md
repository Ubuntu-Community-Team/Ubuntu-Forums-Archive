---
title: "UTF8 in Windows strange in python."
date: 2012-04-23
forum: Ubuntu Dev Link Forum
---

### Post by amsterdamharu on 2012-04-23
For Python 3.2.3

Reading a windows created file in python on Windows XP with the following code:
```

with open("test.txt", encoding='utf-8', mode='r') as dataFile:
        for line in dataFile:
                print(line)
exit()        

```Save it as test.py and run it in the command prompt, always get the following error trying to print the first read line:
```

    print(line)
UnicodeEncodeError: 'gbk' codec can't encode character '\ufeff' in position 0: i
llegal multibyte sequence

```In IDLE it runs just fine, there is however a \ufeff character there that I never put in there, can't see it in the output but it shows in the debugger as value for line:
'\\ufeff&#65279;Some unicode text saved in notepad as utf8\\n'

```

Python 3.2.3 (default, Apr 11 2012, 07:15:24) [MSC v.1500 32 bit (Intel)] on win32
Type "copyright", "credits" or "license()" for more information.
>>> ================================ RESTART ================================
>>> 
&#65279;Some unicode text saved in notepad as utf8

Traceback (most recent call last):
  File "D:\test.py", line 93, in <module>
    exit()
  File "C:\Python32\lib\site.py", line 362, in __call__
    raise SystemExit(code)
SystemExit: None

```Will try it on Ubuntu now and it probably would work just fine, I think this might be a bug in notepad, python for Windows as I suspect the \ufeff character should not be there (when created with geany I think it's not there but will find out and let you know).

My question is: how do I get rid of that error, need this program to run in Windows as well as Linux and people will create their text files with notepad saved as utf8?

---

### Post by qyot27 on 2012-04-23
That's the [BOM](http://en.wikipedia.org/wiki/Byte_order_mark), and it's not really a 'bug', but it is useless for UTF-8 (I'm assuming the reason for it being written there is because the default encoding for Unicode in Windows is actually UTF-16, which does make better use of that character).  As to how to go about resolving the issue, use something other than Notepad.  gedit has a Windows version, and several other alternate text editors (like Notepad2) exist.  They probably don't have this issue.

---

### Post by amsterdamharu on 2012-04-23
Thank you (Stephen?)qyot27

I was thinking the problem is with notepad, when editing the file in geany on Ubuntu the character stays there but newly created files do not have it.

If notepad puts utf16 characters in a file that are saved as utf8 I'd say this is unexpected behavior (bug) in notepad.
According to this page: [http://en.wikipedia.org/wiki/UTF-8](http://en.wikipedia.org/wiki/UTF-8)
utf8 does not need the BOM so I guess it's notepads problem for putting it in there.

Funny thing though is that it doesn't cause an error when run with idle on Windows and no error at all in Lunux. Only in the windows command prompt is it a problem.

Will try to edit the text in several other programs, this came out pretty late because all the test files were created in geany on Ubuntu where I tested and developed. Assuming people will use the tools available in Windows to create the data source files I tested some notepad created files. Very unhappy now because it's a bit of a pain to ask users to use a specific editor and not the default editor that opens .txt files.

Maybe I will create an if statement there checking for that character and remove it after reading the first line (what a pain).

---

### Post by amsterdamharu on 2012-04-23
By the way; .strip() didn't take the BOM out of there so it isn't seen as white space.

---

### Post by qyot27 on 2012-04-23
> If notepad puts utf16 characters in a file that are saved as utf8 I'd say this is unexpected behavior (bug) in notepad.
According to this page: [http://en.wikipedia.org/wiki/UTF-8](http://en.wikipedia.org/wiki/UTF-8)
utf8 does not need the BOM so I guess it's notepads problem for putting it in there.
Not that it puts UTF-16 characters in a file saved as UTF-8.  It's that it probably has to (or Microsoft simply decided to) use the BOM for UTF-16 since Windows uses that internally, and they also use it with UTF-8 for consistency's sake or something.

> Funny thing though is that it doesn't cause an error when run with idle on Windows and no error at all in Lunux. Only in the windows command prompt is it a problem.
You could try seeing if a normal bash prompt (such as MSys' or Cygwin's) can deal with it correctly.  But the case of one terminal emulator having a problem while others don't is somewhat common - MSys doesn't care whether shell scripts have CRLF line endings, but try to use one of those under Ubuntu and it'll choke.

> Assuming people will use the tools available in Windows to create the data source files I tested some notepad created files. Very unhappy now because it's a bit of a pain to ask users to use a specific editor and not the default editor that opens .txt files.
If there aren't any Unicode-specific characters in the code itself, it shouldn't matter whether the .py file is saved as UTF-8 through Notepad (generally speaking; I know nothing about what Python requires).  I'm not sure about Vista or Win7, but on XP Notepad defaults to using 'ANSI' (really Windows-1252 for English) encoding, not UTF-8.  Saving it that way won't put anything extraneous into the file, so you could check that to see if it's okay when run in the Command Prompt.

As an absolute last resort it probably could be removed by using sed to trim the first three(?) characters from the first line of the file, which would remove the BOM.

---

### Post by amsterdamharu on 2012-04-23
Need utf8 for chinese characters and notepad handles it quite well, stripping the file of the BOM.

The files are provided by the user of the script as source of data to fetch translations from google translate to be used in Anki, after corrections have been applied it will fetch the pinyin (Chinese phonetic writing) with the mp3.

The control character is allowed but discouraged. Then python should not show it in read because it's not part of the content. 

Stripping the files before opening has no negative effect when you open them in notepad later so it seems notepad doesn't even need that char. The files are relatively small so I just strip em off it before opening it:

```

def stripBOM(fileName):
        try:
                with open(fileName, encoding='utf-8', mode='r') as f:
                        reading = []
                        for line in f:
                                line=line.replace('\ufeff',"")
                                reading.append(line)
                                for rest in f:
                                        reading.append(rest)
                with open(fileName, encoding='utf-8', mode='w') as f:
                        for line in reading:
                                f.write(line)
        except:
                print("Could not open file:" + fileName + "\nMaybe it is not saved as UTF8")
                exit()

```

---

