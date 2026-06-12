---
title: "QR Code Generator Application"
date: 2009-11-29
forum: The Cafe
---

### Post by kevdog on 2009-11-29
Does anyone know of a QR Code Generator Application available for linux/windows?  I see many on-line websites but would like an installable application.

---

### Post by Dayofswords on 2010-01-09
(yes old, few months in fact, i know)

heres one
[clicky]("http://translate.google.com/translate?u=http%3A%2F%2Fwww.psytec.co.jp%2Fdocomo.html&sl=ja&tl=en&hl=&ie=UTF-8")

its for windows and needs something for Japanese characters, play around a bit and you can figure out what stuff does(the computer screen button can scan qr code that are currently on your screen)

try it
[IMG]http://dayofswords.com/qr/fancy.bmp[/IMG]

---

### Post by dmizer on 2010-01-09
There used to be a firefox add-on that I used for a while, but it's not been updated and doesn't work with the 3.x branch.

Here's a lot of options for you: [http://www.linux.com/archive/feature/126948](http://www.linux.com/archive/feature/126948)

---

### Post by cthlhu1987 on 2010-05-27
> **Dayofswords said:**
> (yes old, few months in fact, i know)
heres one
[clicky]("http://translate.google.com/translate?u=http%3A%2F%2Fwww.psytec.co.jp%2Fdocomo.html&sl=ja&tl=en&hl=&ie=UTF-8")
its for windows and needs something for Japanese characters, play around a bit and you can figure out what stuff does(the computer screen button can scan qr code that are currently on your screen)
try it
[IMG]http://dayofswords.com/qr/fancy.bmp[/IMG]
I'll figure it out, but haven't you something in german, russian or egnlish?

---

### Post by heypete on 2010-06-04
I think the package "qrencode" would fit the bill. It's command-line only, but it's simple.

---

### Post by airtonix on 2010-06-07
> **heypete said:**
> I think the package "qrencode" would fit the bill. It's command-line only, but it's simple.

[http://manpages.ubuntu.com/manpages/intrepid/man1/qrencode.1.html](http://manpages.ubuntu.com/manpages/intrepid/man1/qrencode.1.html)

mix it with zenity and you have a gui.

---

### Post by firehelix on 2010-09-09
Hate to bring back a dead thread, but I was looking for the same thing.
Read the thread, and this is what I came up with.
It's a quick, dirty, hammered out script, but it works for me.

```
#!/bin/bash

me=`whoami`
outpath=`zenity --entry --title="Save path?" --text="What folder would you like to save the QR image to?  Default of /home/$me/Pictures will be used if one is not entered."`
button0=$?
if [ $button0 -eq 0 ];then
if [ -z $outpath ];then
outpath=/home/`whoami`/Pictures
fi
pname=`zenity --entry --title="What filename?" --text="What name should be used for the output?  ex: filename > filename.png"`
button1=$?
if [ $button1 -eq 0 ];then
if [ -z $pname ];then
zenity --info --title="Failure" --text="You failed to enter a filename. Exiting."
else
content=`zenity --entry --title="Content --" --text="What do you want your QR code to say?"`
button2=$?
if [ $button2 -eq 0 ];then
if [ -z $content ];then
zenity --info --title="Failure" --text="You failed to enter any content. Exiting."
else
qrencode -o "$outpath"/"$pname".png "$content"
zenity --info --title="Finished --" --text="Your QR code is located at : $outpath/$pname.png"
fi
else
zenity --info --title="Canceled" --text="QR code generation canceled - content"
fi
fi	
else
zenity --info --title="Canceled" --text="QR code generation canceled - filename"
fi
else
zenity --info --title="Canceled" --text="QR code generation canceled - file path"
fi
```


I know theres no comments... Like I said, quick and dirty.

---

### Post by kevdog on 2010-09-11
Hey thanks for this script -- it looks good.

---

### Post by nailora on 2010-10-10
attached is a program that can generate qr-codes as you type.
it works completely offline.

you need to have "python-qrencode" installed. either install it using apt-get/synaptic (but it is only in debian, not in ubuntu) or use the the attached packages (works for lucid) or build it from source (works for jaunty, karmic).

ps: feedback is welcome, see mail addresses in source code or post here.
code can be cloned via git clone git://devzero.de/cutercode

---

### Post by TJUndead on 2011-03-26
@admins:
Sorry for up some old thread, but I really need to thank for this great app nailora creates.

@nailora:
THX!!! This app you make is so simple, but so effective that now I even don't need use wine to run windows QRcode generators anymore. *__*

---

### Post by hsantanna on 2011-09-30
> **nailora said:**
> attached is a program that can generate qr-codes as you type.
it works completely offline.

you need to have "python-qrencode" installed. either install it using apt-get/synaptic (but it is only in debian, not in ubuntu) or use the the attached packages (works for lucid) or build it from source (works for jaunty, karmic).

ps: feedback is welcome, see mail addresses in source code or post here.
code can be cloned via git clone git://devzero.de/cutercode

Your software is great. Exactly what I was looking for. And I was surprised that I didn't found any similar software at Ubuntu repositories.

By the way, KDE 4.7.1 haves this feature built in through Klipper.

---

### Post by nailora on 2012-04-24
As there still seems to be some interest in cutercode, I decided to upload the code to github for greater ease of use:

[https://github.com/mnagel/cutercode](https://github.com/mnagel/cutercode)

---

### Post by kevdog on 2012-04-29
Ill take a look at this later. Thanks

---

### Post by frup on 2012-06-29
[http://www.omgubuntu.co.uk/2012/06/qreator-offers-fast-creation-of-qr-codes-in-ubuntu](http://www.omgubuntu.co.uk/2012/06/qreator-offers-fast-creation-of-qr-codes-in-ubuntu)

---

