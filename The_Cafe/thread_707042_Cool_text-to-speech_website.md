---
title: "Cool text-to-speech website"
date: 2008-02-25
forum: The Cafe
---

### Post by Ripfox on 2008-02-25
[http://vozme.com/index.php?lang=en](http://vozme.com/index.php?lang=en)

This is good for a bit of fun! :)

---

### Post by hhhhhx on 2008-02-25
[http://vozme.com/text2voice.php?description=ubuntu&md5=1d41c853af58d3a7ae54990ce29417d8&tl=en&gn=ml&sa=yes&bookmarklet=no&interface=full](http://vozme.com/text2voice.php?description=ubuntu&md5=1d41c853af58d3a7ae54990ce29417d8&tl=en&gn=ml&sa=yes&bookmarklet=no&interface=full)

( it had to happen :))

---

### Post by ryanhaigh on 2008-02-25
Try this in the terminal:
```

espeak 'This is good for a bit of fun!'

```
For more info checkout the man page using man espeak or System>Help and Support > search espeak

---

### Post by quanumphaze on 2008-02-25
> **ryanhaigh said:**
> Try this in the terminal:
```

espeak 'This is good for a bit of fun!'

```
For more info checkout the man page using man espeak or System>Help and Support > search espeak

And here I am typing:```
echo "your text here" | festival --tts
```
your way is much faster to type

---

### Post by Ripfox on 2008-02-25
> **ryanhaigh said:**
> Try this in the terminal:
```

espeak 'This is good for a bit of fun!'

```
For more info checkout the man page using man espeak or System>Help and Support > search espeak

Yes but can you easily download an mp3 of the text-speech from the terminal? :)

---

### Post by Ripfox on 2008-02-25
> **xhhux said:**
> [http://vozme.com/text2voice.php?description=ubuntu&md5=1d41c853af58d3a7ae54990ce29417d8&tl=en&gn=ml&sa=yes&bookmarklet=no&interface=full](http://vozme.com/text2voice.php?description=ubuntu&md5=1d41c853af58d3a7ae54990ce29417d8&tl=en&gn=ml&sa=yes&bookmarklet=no&interface=full)

( it had to happen :))

[http://vozme.com/text2voice.php?description=oooboontooo&md5=58879a614a1556c4daac81c18bcc9185&tl=en&gn=ml&sa=yes&bookmarklet=no&interface=full](http://vozme.com/text2voice.php?description=oooboontooo&md5=58879a614a1556c4daac81c18bcc9185&tl=en&gn=ml&sa=yes&bookmarklet=no&interface=full)

---

### Post by ryanhaigh on 2008-02-25
> **ripfox said:**
> Yes but can you easily download an mp3 of the text-speech from the terminal? :)

```
espeak 'yes i can' --stdout | lame - test.mp3
```

I have previously used this command to turn an ebook into a robot sounding audiobook. Use ```
pdftotext file.pdf 
``` to convert the pdf to a plain text file, chop out the openning parts associated with publishing info using a plain old text editor. Then use ```
espeak -f file.txt -w file.wav
``` or ```
espeak -f file.txt --stdout | lame - file.mp3
``` and open with your favourite audio player. 

Messing with the voice, pitch and speed can improve the 'listenability' of the audio.

---

### Post by vishzilla on 2008-02-25
> **ryanhaigh said:**
> ```
espeak 'yes i can' --stdout | lame - test.mp3
```

I have previously used this command to turn an ebook into a robot sounding audiobook. Use ```
pdftotext file.pdf 
``` to convert the pdf to a plain text file, chop out the openning parts associated with publishing info using a plain old text editor. Then use ```
espeak -f file.txt -w file.wav
``` or ```
espeak -f file.txt --stdout | lame - file.mp3
``` and open with your favourite audio player. 

Messing with the voice, pitch and speed can improve the 'listenability' of the audio.

Excellent i never knew about this...thanks a million

---

### Post by ryanhaigh on 2008-02-25
It is amazing what can be achieved via the linux commandline interface. The other day I had to find all my jpg and copy them into a single folder but things were getting overwritten because they had the same filename. Using the command below I copied all the images from 100+ folders into a single folder and any duplicate filenames were backed up (that what cp -b does).
```
find ./ -iname '*.jpg'  -exec cp -b {} ~/Desktop/allpics/ \;
```
But of course there were some duplicates in this folder of a few thousand images, now I could go looking and try and spot them or I could do.
```
fdupes ./ -d
```
Unfortunately this meant that for every file where there were duplicates I had to press 1 then Enter and this got pretty tiresome after the first 30 or so. Once again the terminal came to the rescue. I opened up another terminal and used the bash commands below to simulate me pressing the 1 and return keys 100 times. The sleep 3s allowed time to return mouse focus to the original terminal where fdupes was running and after a couple of runs through all my duplicate files were removed. 
```

counter=100
limit=0
sleep 3s &&
while [ "$counter" -gt "$limit" ];
do
xte "key 1" &&
xte "key Return";
done 

```

This is why the command line is such a great tool under linux, with a little bit of research you can save a great deal of time. You can also keep this valuable little snippets in a simple text file called usefulscripts or something as I do.

EDIT: sorry, went a little off topic there

---

### Post by vishzilla on 2008-02-25
> **ryanhaigh said:**
> It is amazing what can be achieved via the linux commandline interface. The other day I had to find all my jpg and copy them into a single folder but things were getting overwritten because they had the same filename. Using the command below I copied all the images from 100+ folders into a single folder and any duplicate filenames were backed up (that what cp -b does).
```
find ./ -iname '*.jpg'  -exec cp -b {} ~/Desktop/allpics/ \;
```
But of course there were some duplicates in this folder of a few thousand images, now I could go looking and try and spot them or I could do.
```
fdupes ./ -d
```
Unfortunately this meant that for every file where there were duplicates I had to press 1 then Enter and this got pretty tiresome after the first 30 or so. Once again the terminal came to the rescue. I opened up another terminal and used the bash commands below to simulate me pressing the 1 and return keys 100 times. The sleep 3s allowed time to return mouse focus to the original terminal where fdupes was running and after a couple of runs through all my duplicate files were removed. 
```

counter=100
limit=0
sleep 3s &&
while [ "$counter" -gt "$limit" ];
do
xte "key 1" &&
xte "key Return";
done 

```

This is why the command line is such a great tool under linux, with a little bit of research you can save a great deal of time. You can also keep this valuable little snippets in a simple text file called usefulscripts or something as I do.

EDIT: sorry, went a little off topic there

no problem, good info. is there any source where these type of commands are listed?

---

### Post by ryanhaigh on 2008-02-25
I usually find these things through Google, or at least individual parts and then use what I know about bash to tie it all together. When I first started using Linux I wanted to create as lean a system as possible because I didn't have the hardware I have now, so I went through what was installed on my then Debian system using synaptic and tried to determine what I could get rid of. As a side effect I also learned about a heap of small utilities which have proved quite useful.

I will point you to the [advanced bash-scripting]("http://tldp.org/LDP/abs/html/") guide though, I used it when I was prototyping a small application for my thesis and it taught me a lot, and I didn't even get all the way through!

Most things you will pick up as you need them just by keeping in mind that if you can't do it by the GUI (or can't do it quickly) that doesn't mean you can't do it.

---

### Post by gyrfalcon on 2008-10-28
> **ryanhaigh said:**
> .
```
find ./ -iname '*.jpg'  -exec cp -b {} ~/Desktop/allpics/ \;
```...
This is why the command line is such a great tool under linux, with a little bit of research you can save a great deal of time. You can also keep this valuable little snippets in a simple text file called usefulscripts or something as I do.

Can you tell me what I'm doing wrong here?  It doesn't seem to be taking the lines of **find** and putting them into **mv** the way I would like.


```
root@127.0.0.1:/raid0/data# **find /raid0/data/usbhdd/ -name *.lnk **
/raid0/data/usbhdd/sdf1/Other/My Music/Sample Music.lnk
/raid0/data/usbhdd/sdf1/Other/My Pictures/Sample Pictures.lnk
...<cut>

```

```
root@127.0.0.1:/raid0/data# **find /raid0/data/usbhdd/ -name *.lnk -exec mv '{}' /raid0/data/usbhdd/remove/ \;**
mv: unable to rename `Pictures/Sample': No such file or directory
mv: unable to rename `Pictures.lnk': No such file or directory
...<cut>

```

---

### Post by ratmandall on 2008-10-28
> **ryanhaigh said:**
> Try this in the terminal:
```

espeak 'This is good for a bit of fun!'

```
For more info checkout the man page using man espeak or System>Help and Support > search espeak
```

PaHost_OpenStream: could not open /dev/dsp for O_WRONLY
PaHost_OpenStream: ERROR - result = -10000
PaHost_OpenStream: could not open /dev/dsp for O_WRONLY
PaHost_OpenStream: ERROR - result = -10000
PaHost_OpenStream: could not open /dev/dsp for O_WRONLY
PaHost_OpenStream: ERROR - result = -10000
PaHost_OpenStream: could not open /dev/dsp for O_WRONLY
PaHost_OpenStream: ERROR - result = -10000
PaHost_OpenStream: could not open /dev/dsp for O_WRONLY
PaHost_OpenStream: ERROR - result = -10000

```

---

### Post by -grubby on 2008-10-28
Espeak doesn't work alot of the time here also. Try shutting down any apps using sound

---

### Post by ratmandall on 2008-10-28
> **nathangrubb said:**
> Espeak doesn't work alot of the time here also. Try shutting down any apps using sound
:)

---

### Post by ryanhaigh on 2008-10-28
> **gyrfalcon said:**
> Can you tell me what I'm doing wrong here?  It doesn't seem to be taking the lines of **find** and putting them into **mv** the way I would like.


```
root@127.0.0.1:/raid0/data# **find /raid0/data/usbhdd/ -name *.lnk **
/raid0/data/usbhdd/sdf1/Other/My Music/Sample Music.lnk
/raid0/data/usbhdd/sdf1/Other/My Pictures/Sample Pictures.lnk
...<cut>

```

```
root@127.0.0.1:/raid0/data# **find /raid0/data/usbhdd/ -name *.lnk -exec mv '{}' /raid0/data/usbhdd/remove/ \;**
mv: unable to rename `Pictures/Sample': No such file or directory
mv: unable to rename `Pictures.lnk': No such file or directory
...<cut>

```

I can't reproduce this error, using the same command as you I get errors regarding the usage of find. Also I must point out that you are trying to move files into a subdir and once the find command has found all matching files in the current directory it will also search the 'remove' sub directory, you will therefore receive an error because your command is trying to move remove/shortcut.lnk to remove/shortcut.lnk.

Finally I was able to achieve what you want, albeit using text files, using the following command:

```

ryanhaigh@hostname$find ./ -iname '*.txt' -exec mv -v {} ../dest/ \;
`./sub directory/sub dir file.txt' -> `../dest/sub dir file.txt'
`./file name.txt' -> `../dest/file name.txt'
`./file.txt' -> `../dest/file.txt'

```

The one thing I though of is that perhaps you are using a different shell than I am. I am using bash, you can find out which shell you are using via the command:
```

ps -p $$

```

---

### Post by ryanhaigh on 2008-10-28
> **nathangrubb said:**
> Espeak doesn't work alot of the time here also. Try shutting down any apps using sound

Yeah espeak uses the OSS sound system which doesn't necessarilly work all the time but I'm pretty sure you can get ALSA to provide a wrapper using the alsa-oss package but I haven't worried about it myself as I don't use espeak that often.

---

### Post by ack389 on 2008-10-28
Alright, back to the original poster. I made a tune while feeling really "creative"  Go to (  [http://vozme.com/index.php?lang=en](http://vozme.com/index.php?lang=en)  ) , then past in this but make sure you select the female voice:

```
za aaaa aaaaaa, ooboon two, ah. ah oob oontu aaaaaa, ooboon two, ah. ah oob oontu aaaaaa, ooboon two, ah. ah oob oontu aaaaaa, ooboon two, ah. ah oob oontu aaaaaa, ooboon two, ah. ah oob oontu awoombtawoombtawoombtawoombtawoombtawoombtawoombtawoombtawoombtawoombtawoombtawoombtawoombtawoombtawoombtawoombtawoombtawoombtawoombtawoombtawoombta  ta  ta ta tata ta  ta  ta ta tata ta  ta  ta ta tata ta  ta  ta ta tata.  woombtawoombtawoombtawoombtawoombta  roompta roompta  roompta aaaaaa, ooboon two, ah. ah oob oontu aaaaaa, ooboon two, ah. ah oob oontu aaaaaa, ooboon two, ah. ah oob oontu aaaaaa, ooboon two, ah. ah oob oontu aaaaaa, ooboon two, ah. ah oob oontu
```

It is actually really cool and you can make many, many different tunes with this thing.  You just can't go to long or you get an error about using too much memory instead of the mp3 generation.
I want to see if anyone else can come up with something, this is fun!  It really is amazing the sounds this thing can replicate.:guitar:

---

### Post by gyrfalcon on 2008-10-28
> **ryanhaigh said:**
> ```

ryanhaigh@hostname$find ./ -iname '*.txt' -exec mv -v {} ../dest/ \;
`./sub directory/sub dir file.txt' -> `../dest/sub dir file.txt'
`./file name.txt' -> `../dest/file name.txt'
`./file.txt' -> `../dest/file.txt'

```

The one thing I though of is that perhaps you are using a different shell than I am. I am using bash, you can find out which shell you are using via the command:
```

ps -p $$

```

Sorry I should have explained more... I'm running busybox w/the Linux Kernel 2.6.13 on a NAS device with 'find' that doesn't support the -iname switch.

I also posted the wrong error output:

```
root@127.0.0.1:/raid0/data#find /raid0/data/usbhdd/ -name *.lnk
/raid0/data/usbhdd/sdf1/Other/My Music/Sample Music.lnk
/raid0/data/usbhdd/sdf1/Other/My Pictures/Sample Pictures.lnk
...<cut>


root@127.0.0.1:/raid0/data#find /raid0/data/usbhdd/ -name *.lnk -exec mv '{}' /raid0/data/usbhdd/remove/ \;
mv: unable to rename `/raid0/data/usbhdd/sdf1/Other/My': No such file or directory
mv: unable to rename `Music/Sample': No such file or directory
mv: unable to rename `Music.lnk': No such file or directory
mv: unable to rename `/raid0/data/usbhdd/sdf1/Other/My': No such file or directory
mv: unable to rename `Pictures/Sample': No such file or directory
mv: unable to rename `Pictures.lnk': No such file or directory
...<cut>
```

It seems like spaces are causing all the problems.

---

### Post by ryanhaigh on 2008-10-28
Ok so I installed busybox to try and come up with a solution. You are indeed correct that the spaces are what is causing the trouble. That said the eventual fix turned out to be rather simple too (I just wish I had tried it first). Just needed to add another set of quotes to ensure that the filename remains intact.

```

find ./ -name "*.lnk" -exec mv -v '"{}"' ../dest/ \;

```

---

### Post by gyrfalcon on 2008-10-29
> **ryanhaigh said:**
> Ok so I installed busybox to try and come up with a solution. You are indeed correct that the spaces are what is causing the trouble. That said the eventual fix turned out to be rather simple too (I just wish I had tried it first). Just needed to add another set of quotes to ensure that the filename remains intact.

```

find ./ -name "*.lnk" -exec mv -v '"{}"' ../dest/ \;

```


Wow, thanks a ton for the help... it's a lot more than I ever expected.  

I actually tried to do this a few hours ago:  ```
find /raid0/data/usbhdd/ -name *.lnk -exec mv '{''}' /raid0/data/usbhdd/remove/ \;
```

As you can tell I'm pretty bad with syntax and the shell/s. ](*,)

Hopefully I'll get a lot better with linux/unix/gnu systems in the near future.  Again thanks a TON! :D

You :guitar:

---

