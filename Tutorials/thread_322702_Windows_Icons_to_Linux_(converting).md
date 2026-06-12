---
title: "Windows Icons to Linux (converting)"
date: 2006-12-20
forum: Tutorials
---

### Post by Gen2ly on 2006-12-20
*This is an Update, I preserved the original below.*

I found a much better method to make your Icons on Windows available on your Linux Box, and easier too.  The prior method would disguise the .ico file as a .png, completely ignoring multiple layers hidden therein.  This also made the .png impossible to edit in gimp.  Well, I stumbled upon a much better way to have your icons converted.  First we'll need [FONT="Fixedsys"]icoutils[/FONT].

```
sudo apt-get install icoutils
```

Icoutils contains four programs, the two most likely you'll use though are wrestool and icotool.  Whatis reveals what these programs do

[INDENT][I]icotool (1) - Convert and create Win32 icon and cursor files
wrestool (1) - extract resources from Microsoft Windows(R) binaries (exe's and dlls) I assume ``extresso'' automates these tasks with the help of special resource scripts.[/I][/INDENT]

You can use [FONT="Fixedsys"]icotool[/FONT] to see what types of icons are available in an .ico file:

```
icotool -l Emoticon.ico
```

You'll see a list like this:

```
--icon --index=1 --width=32 --height=32 --bit-depth=8 --palette-size=256
--icon --index=2 --width=16 --height=16 --bit-depth=8 --palette-size=256
--icon --index=3 --width=128 --height=128 --bit-depth=32 --palette-size=0
--icon --index=4 --width=48 --height=48 --bit-depth=32 --palette-size=0
--icon --index=5 --width=32 --height=32 --bit-depth=32 --palette-size=0
--icon --index=6 --width=16 --height=16 --bit-depth=32 --palette-size=0
```

In this case it showed six different sizes, I believe this is standard for XP  (and Vista??).

If you want to extract all the icons in the .ico file and converts them to .png: 

```
icotool -x -o . BootCamp_Drive.ico
```

This will extract the six icons listed above in Emoticon.ico.  [FONT="Fixedsys"]-x[/FONT] signifies extract while [FONT="Fixedsys"]-o[/FONT] directs [FONT="Fixedsys"]icotool[/FONT] to an output directory, in this case "." or the same directory.

You will notice that the eight bit depth icons won't carry a proper alpha layer and have a black layer about them.  You probably won't need the eight bit depth icons and they dont' need to be extracted.  To extract an entire directory ignoring eight bit icons [FONT="Fixedsys"]cd[/FONT] into it and just do:

```
icotool -x --palette-size=0 -o /home/user/Desktop/seperate-directory *.ico
```

Ignoring the 256 colored (eight bit) icons, use the palette size of 0 to specify 24 bit and 32 bit.  You also noticed it isn't a bad idea to use a separate output directory.

Thats is.  Enjoy!

**Manual Icon Conversion**

This was the first way I did it, and it works nice, albeit it is a dirty method.  There were no resources that I could locate so I pretty much learned this from scratch.  

I had heard ImageMagik could do this but the program convert gave me a don't understand (.) argument.  Anyways.  Next, I heard Gimp would be perfect for such a little task.  So, I tried to learn how to do batch jobs.  I'm sorry, but the documentation I saw, just overwhelmed me.  Doing batch jobs in Gimp take a pretty experienced person.

So I was just messin' about and decided to change .ico to .png.  OMG, it worked!

That's all I had to do!  The mask and everything was kept.  Now, of course, this isn't the best method if you have hundreds of icons you need converted.  So I tried 'mv *.ico *.png'.  This to my surprise didn't work.  I learned that to do mass renaming like this takes quite a bit more programming knowledge.  Well, to cut this short.  I made a script that first takes spaces out of the icons names and replaced them with underscores, then added the change name extension.  Goto the icon Folder (e.g. cd ~/Desktop/Frosty-Icons) then use the script.  You have to use for the script for all the folders, but it will save you a lot of time.  Just cut/paste into the terminal.
```
for i in *\ *
do
mv "$i" `echo "$i" | tr ' '  '_'`
done
for i in *.ico
do
  j=${i%.ico}.png
  # or: j=${i}l
  mv $i $j
done

```
Note:  Windows .ico's use multiple layers, and png's don't, so opening these files up in Gimp isn't possible unless (of course) you rename the extension back.

---

### Post by aysiu on 2006-12-20
If you don't mind using a graphical tool, you can do mass-renaming with *krename*, which is in the Universe repositories.

---

### Post by DarkN00b on 2006-12-20
You could use [XNview]("http://www.xnview.com/") to select a whole directory and batch convert them all to .png .

---

### Post by ~LoKe on 2006-12-21
Don't you need a config file to turn these icons into a theme?  Shame there's nothing that'll do that for you.

---

### Post by bodhi.zazen on 2006-12-24
Nice How-to

This thread has been added to the UDSF wiki.

[Convert_Windows_icons](http://doc.gwos.org/index.php/Convert_Windows_icons)

---

### Post by sebbe1991 on 2006-12-24
extract .ico from .icl .dll .exe  
```
wrestool -x --output=. -t14
```

convert .ico to .png
```
for i in *.ico; do convert "$i" "$i.png"; done
```

---

### Post by David Floyd on 2007-03-26
> **sebbe1991 said:**
> extract .ico from .icl .dll .exe  
```
wrestool -x --output=. -t14
```


The above code did not work for me - what am a missing?

I get the following error:  wrestool: command not found

Thanks for help,

David

---

### Post by chinaski on 2007-03-28
@ Dirk.R.Gently:

thanks a lot this how-to is very useful ;)

---

### Post by David Floyd on 2007-03-28
> **chinaski said:**
> @ Dirk.R.Gently:

thanks a lot this how-to is very useful ;)

So, did you get the code:

wrestool -x --output=. -t14

to work?

I got the error message :

wrestool: command not found

and I don't know how to proceed from there.

David

---

### Post by chinaski on 2007-03-28
no sorry,

I am using this metod

```
for i in *\ *
do
mv "$i" `echo "$i" | tr ' ' '_'`
done
for i in *.ico
do
j=${i%.ico}.png
# or: j=${i}l
mv $i $j
done
```described in [COLOR=Blue]**[first post]("http://ubuntuforums.org/showpost.php?p=1913036&postcount=1")**[/COLOR]

---

### Post by David Floyd on 2007-03-28
> **chinaski said:**
> no sorry,

I am using this metod

```
for i in *\ *
do
mv "$i" `echo "$i" | tr ' ' '_'`
done
for i in *.ico
do
j=${i%.ico}.png
# or: j=${i}l
mv $i $j
done
```described in [COLOR=Blue]**[first post]("http://ubuntuforums.org/showpost.php?p=1913036&postcount=1")**[/COLOR]

In addition, wrestool -x --output=. -t14

is supposed to extract icons from .dll .icl & .exe, but I cannot get it to work :(

see another post in this thread:

[http://ubuntuforums.org/showpost.php?p=1925973&postcount=6](http://ubuntuforums.org/showpost.php?p=1925973&postcount=6)

---

### Post by Gen2ly on 2007-05-16
Updated the howto.

---

### Post by bodhi.zazen on 2007-05-17
Thanks for the update :) 

Again, well done !

---

### Post by eentonig on 2007-05-17
> **David Floyd said:**
> So, did you get the code:

wrestool -x --output=. -t14

to work?

I got the error message :

wrestool: command not found

and I don't know how to proceed from there.

David

You need to install that command. As it is not know to your system. I don't know which package this is in though.

---

### Post by bodhi.zazen on 2007-05-17
LOL !

*wrestool* is in *icoutils*



See post #1 of this thread :lolflag:


```
sudo aptitude install icoutils
```

It's in Universe so you may need to enable the universe repository :

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by gibbylinks on 2008-03-03
Sorry, I know this has been dormant for a while, but I just did a yahoo search and found this thread.

Excuse my ignorance, but I have a dual boot computer with Win XP and Gutsy. My PC has a hard drive full of music that I have collected. When viewed in windows I have one icon for MP3's I have ripped direct from my CD collection and one icon for MP3's I have "acquired".

Would this enable me to view these icons correctly in my Ubuntu ?

If not is this possible to do and if so how ?

Cheers :guitar:

---

### Post by watricky on 2008-10-07
Sorry for this extremely late addition to the thread. I hope it actually helps someone. :)

> **sebbe1991 said:**
> extract .ico from .icl .dll .exe  
```
wrestool -x --output=. -t14
```

convert .ico to .png
```
for i in *.ico; do convert "$i" "$i.png"; done
```

Might help to mention the file. ;)

```
~$ wrestool --help | grep Usage
Usage: wrestool [OPTION]... [FILE]... 
```

Thus the full way to get the icon resources out of an example.dll is:
```
~$ wrestool -x --output=. -t14 example.dll
```

Gibbylinks, I'm not sure how to help specifically. If you can find where the icon is on your Windows system then you can use the given methods to extract the icon.

---

### Post by jvdurme on 2010-12-13
> **watricky said:**
> Sorry for this extremely late addition to the thread. I hope it actually helps someone. :)



Might help to mention the file. ;)

```
~$ wrestool --help | grep Usage
Usage: wrestool [OPTION]... [FILE]... 
```Thus the full way to get the icon resources out of an example.dll is:
```
~$ wrestool -x --output=. -t14 example.dll
```Gibbylinks, I'm not sure how to help specifically. If you can find where the icon is on your Windows system then you can use the given methods to extract the icon.

Great! Worked for me. ;)

---

### Post by hydrox24 on 2011-05-06
This was a really helpful and succinct post. Thanks for adding even more quality and trust to the world of Ubuntu and linux!

---

### Post by melifaro on 2011-06-22
simple script for creating icons from windows files. I found it on some forum, but was not working, modified. Now everything works.

requires: imagemagik (convert)

  How to use:
> 
 $ wineicons.sh file.exe file.png
 Source code:
> 
#!/bin/sh

f=`mktemp`


if wrestool "$1" -x -t14 > $f && [ -s $f ]; then
        id=`icotool -l $f | awk '{
                ci=int(substr($2,index($2,"=")+1));
                cw=int(substr($3,index($3,"=")+1));
                cb=int(substr($5,index($5,"=")+1));

                if (cw > w || (cw == w && cb > b)) {
                        b = cb;
                        w = cw;
                        i = ci;
                }
                }
                END {
                        print i;
                }'`

        icotool -x --index=$id $f -o "$2"
        convert -resize 48x48 "$2" "$2"         # optional
else
        cp '/usr/share/icons/crystalsvg/48x48/mimetypes/exec_wine.png' "$2"
fi

rm $f



---

### Post by geazzy on 2011-06-22
great tutorial :)

---

### Post by novatotal on 2012-04-13
> **Gen2ly said:**
> *This is an Update, I preserved the original below.*

I found a much better method to make your Icons on Windows available on your Linux Box, and easier too.  The prior method would disguise the .ico file as a .png, completely ignoring multiple layers hidden therein.  This also made the .png impossible to edit in gimp.  Well, I stumbled upon a much better way to have your icons converted.  First we'll need [FONT="Fixedsys"]icoutils[/FONT].

```
sudo apt-get install icoutils
```

Icoutils contains four programs, the two most likely you'll use though are wrestool and icotool.  Whatis reveals what these programs do

[INDENT][I]icotool (1) - Convert and create Win32 icon and cursor files
wrestool (1) - extract resources from Microsoft Windows(R) binaries (exe's and dlls) I assume ``extresso'' automates these tasks with the help of special resource scripts.[/I][/INDENT]

You can use [FONT="Fixedsys"]icotool[/FONT] to see what types of icons are available in an .ico file:

```
icotool -l Emoticon.ico
```

You'll see a list like this:

```
--icon --index=1 --width=32 --height=32 --bit-depth=8 --palette-size=256
--icon --index=2 --width=16 --height=16 --bit-depth=8 --palette-size=256
--icon --index=3 --width=128 --height=128 --bit-depth=32 --palette-size=0
--icon --index=4 --width=48 --height=48 --bit-depth=32 --palette-size=0
--icon --index=5 --width=32 --height=32 --bit-depth=32 --palette-size=0
--icon --index=6 --width=16 --height=16 --bit-depth=32 --palette-size=0
```

In this case it showed six different sizes, I believe this is standard for XP  (and Vista??).

If you want to extract all the icons in the .ico file and converts them to .png: 

```
icotool -x -o . BootCamp_Drive.ico
```

This will extract the six icons listed above in Emoticon.ico.  [FONT="Fixedsys"]-x[/FONT] signifies extract while [FONT="Fixedsys"]-o[/FONT] directs [FONT="Fixedsys"]icotool[/FONT] to an output directory, in this case "." or the same directory.

You will notice that the eight bit depth icons won't carry a proper alpha layer and have a black layer about them.  You probably won't need the eight bit depth icons and they dont' need to be extracted.  To extract an entire directory ignoring eight bit icons [FONT="Fixedsys"]cd[/FONT] into it and just do:

```
icotool -x --palette-size=0 -o /home/user/Desktop/seperate-directory *.ico
```

Ignoring the 256 colored (eight bit) icons, use the palette size of 0 to specify 24 bit and 32 bit.  You also noticed it isn't a bad idea to use a separate output directory.

Thats is.  Enjoy!



I know it is really late to be joining, but tried your tuto and got some errors; found a way around it and I'm posting it in order to help others.

This is the instruction that gave me problems and also the key to converting all the files: ```
icotool -x --palette-size=0 -o /home/user/Desktop/seperate-directory *.ico
```

The easy way is to open the terminal in the folder where you have your icons, ```
(sudo apt-get install nautilus-open-terminal)
```
Reboot your pc, and then open said folder and right click on an empty space inside it; **open terminal here**

then: ```
eduardo@eduardo-desktop:~/Escritorio/Alienware Breed$ icotool -x -o . *.ico
```

And presto! now all you have to do is use them.

---

