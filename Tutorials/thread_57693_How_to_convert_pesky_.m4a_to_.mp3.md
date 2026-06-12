---
title: "How to convert pesky .m4a to .mp3"
date: 2005-08-17
forum: Tutorials
---

### Post by s_p_a_r_k_y on 2005-08-17
I recently got a bunch of m4a files from a mac user from her band...I know I can play it with amarok but not xmms. Also why not just use mp3s which you know everyone and their grandma can use. So below is a quick bash script to automate the process. I'm sure there is a quicker way...but you can use this to convert to mp3s or ogg vorbis or whatever format you like.

```

#!/bin/bash
#
# Dump m4a to wav (first step in conversion)

y=`pwd`
cd "$1"

echo changing directory to $1
sleep 15
echo converting the damned .m4as to mp3s
for i in *.m4a
do
mplayer -ao pcm "$i" -aofile "$i.wav"
done

echo converting the damned .wavs to mp3s
for i in *.wav
do
lame -h -b 192 "$i" "$i.mp3"
done

echo renameding the damned mp3s
for i in *.mp3
do
x=`echo "$i"|sed -e 's/m4a.wav.mp3/mp3/'`
mv "$i" "$x"
done

rm *.wav
rm *.m4a
cd $y

echo changing back to $y

```

---

### Post by dbeckham32 on 2005-08-18
You should try downloading a program called "gnormalize". It will allow you to convert one or an entire directory of MP4 files into MP3 or another output format. Works great, and has a graphical interface to boot.


[http://gnormalize.sourceforge.net/](http://gnormalize.sourceforge.net/)

---

### Post by s_p_a_r_k_y on 2005-08-18
[QUOTE=dbeckham32]You should try downloading a program called "gnormalize". It will allow you to convert one or an entire directory of MP4 files into MP3 or another output format. Works great, and has a graphical interface to boot.


[http://gnormalize.sourceforge.net/](http://gnormalize.sourceforge.net/)[/QUOTE]

thanks for the info will install it on my desktop. I wrote the script for the fileserver which holds my music which doens't have X installed so I wanted something to do over ssh. However I will definately in the future convert files before I move them to my fileserver. Thanks again

---

### Post by dude2425 on 2005-08-18
lol, funny thing is, I had to convert a bunch of m4a's that my bro gave me to mp3's so I can transfer them to my ipod with gtkpod, and had come up with this script:

 > #!/bin/bash
  for i in *.m4a; do
      out=$(ls "$i" | sed -e 's/.m4a//g')
      faad -w "$i" > "$out.wav"
  done
  for i in *.m4b; do
      out=$(ls "$i" | sed -e 's/.m4b//g')
      faad -w "$i" > "$out.wav"
  done
  for i in *.wav; do
      out=$(ls "$i" | sed -e 's/.wav//g')
      lame -h -b 64 "$i" "$out.mp3"
  done

  rm *.wav 

Your's seems to give more info than mine does, but mine uses faad instead of mplayer. Great minds think quite similar.

Also, I've heard about gnormailize, but hadn't tryed it out. Wish I would have seen it before I set this up as a nautilus script lol

---

### Post by hidinginthemountains on 2008-06-25
The second script worked better for me. I misfired on the first script and ended up wiping out my songs...my bad, just didn't read the script thouroughly enough

---

### Post by hidinginthemountains on 2008-06-26
Well, unfortunately the mp3's I ended up with were nothing but static. ...trying to find another way

---

### Post by hidinginthemountains on 2008-06-26
just to save anyone reading this in the future a bit of effort. You can go to [http://multimedia.t27.ca/](http://multimedia.t27.ca/) and run the script from that page. When done you will be able to simply right click on the file you wish to convert, and the option will be there in your context menu.

Thanks to Tim.

---

### Post by WaNaBePi on 2009-02-23
sorry for being a newb but...

im not sure what i need to change (in order to convert a given music file from .aac to .mp3) exactly, I got as far as installing faad im using the second script:


#!/bin/bash
for i in *.m4a; do
out=$(ls "$i" | sed -e 's/.m4a//g')
faad -w "$i" > "$out.wav"
done
for i in *.m4b; do
out=$(ls "$i" | sed -e 's/.m4b//g')
faad -w "$i" > "$out.wav"
done
for i in *.wav; do
out=$(ls "$i" | sed -e 's/.wav//g')
lame -h -b 64 "$i" "$out.mp3"
done

rm *.wav

this is what i tried i installed faad..... 

projectmayhem@projectmayhem-lapbottom:~$ .m4a; do
bash: syntax error near unexpected token `do'
projectmayhem@projectmayhem-lapbottom:~$ out=$(ls "$i" | sed -e 's/.m4a//g')
ls: cannot access : No such file or directory
projectmayhem@projectmayhem-lapbottom:~$ faad -w "$i" > "$out.wav"out=$(ls "$i" | sed -e 's/.m4a//g')
ls: cannot access : No such file or directory
The program 'faad' is currently not installed.  You can install it by typing:
sudo apt-get install faad
bash: faad: command not found
projectmayhem@projectmayhem-lapbottom:~$ faad -w "$i" > "$out.wav"sudo apt-get install faad
The program 'faad' is currently not installed.  You can install it by typing:
sudo apt-get install faad
bash: faad: command not found
projectmayhem@projectmayhem-lapbottom:~$ sudo apt-get install faad


here is i what i got after i installed faad:


projectmayhem@projectmayhem-lapbottom:~$ out=$(ls "$i" | sed -e 's/.m4a//g')
ls: cannot access : No such file or directory
projectmayhem@projectmayhem-lapbottom:~$ faad -w "$i" > "$out.wav"
projectmayhem@projectmayhem-lapbottom:~$


it seemd logical in my newb mind to only put in the part before the first done...just to be safe...dont know what im doing and dont want to mess up something by puting in a bad script, by me not changing a variable correctly or some thing....

---

### Post by nunki on 2009-02-23
Great script! However, you may want to consider using named pipes to avoid the intermediate .wav step i.e.
```

mkfifo pipe.wav

lame [whatever options] pipe.wav output.mp3

mplayer -ao pcm:file=pipe.wav source.m4a


```

---

### Post by WaNaBePi on 2009-02-23
please some one tell me how to use these scripts properly. please?

---

### Post by rduke15 on 2009-10-23
**The easy way:**

It should be noted that these scripts may be useful in special cases, but that most people looking in the Ubuntu forums for a way to convert .m4a files to .mp3 will probably prefer to use SoundConverter:

  apt-get install soundconverter lame

Give it a folder, set the options, and it will find all files needing to be converted, and will preserve the tags.

---

### Post by phenest on 2009-11-01
Mp3's are about as archaic as MS Windows.

M4a's: Welcome to the future!

[rant]Mp3's are not popular because it's a good format. That's like saying everyone uses Windows so it must be a good OS.[/rant]

---

### Post by cdeobald on 2009-12-04
To use these scripts, first check that you are using Nautilus as your file manager, then:
[LIST][*]Create a new text file in Gedit or whatever you use for that purpose[*]Paste the script code into that file[*]Save it into /home/myhome/.gnome2/nautilus-scripts (where "myhome" is your username.[*]Navigate to the file, right-click on it, select Properties, Permissions, and check "Allow executing file as program."
[/LIST]

To use the script, right click in the folder in which you have the files you wish to convert.  Choose "Scripts" and then select the script you wish to run.

BTW, always back up the songs before attempting a conversion, as many of these scripts delete the originals as the last step.  If something goes haywire, you will still have the original files.  The original script in this thread is a good example.  It cost me a full CD of files.

---

### Post by brucewagner on 2010-02-27
> **rduke15 said:**
> **The easy way:**

It should be noted that these scripts may be useful in special cases, but that most people looking in the Ubuntu forums for a way to convert .m4a files to .mp3 will probably prefer to use SoundConverter:

  apt-get install soundconverter lame

Give it a folder, set the options, and it will find all files needing to be converted, and will preserve the tags.

Sound Converter does not seem to accept M4A files...  :(

---

### Post by burkas on 2011-10-13
It's 2 am in my country and still can't sleep. So I optimized your script with "great UI ::LOL::" 

> 
#!/bin/bash

y=`pwd`
fileName="$1"

if [ -z "$fileName" ]; then
echo "Process in current folder"
jef=ls *.m4a|tail -1
if [ -f $jef ]; then
echo "Next to process"
else
echo "File not found at first"
exit
fi
else
if [ -d "$fileName" ]; then
cd "$fileName"
jef=ls *.m4a|tail -1
if [ -f $jef ]; then
echo "Process in target folder"
else
echo "File not found at second"
exit
fi
else
echo "Folder not found"
exit
fi
fi

for i in *.m4a
do
#convert ke wav
mplayer -ao pcm:file=tes.wav "$i"
#namening
name=`echo $i |sed -e 's/m4a/mp3/'`
#convert ke mp3
lame -h -b 192 tes.wav "$name"
#remove wav-nya
rm tes.wav
done

cd $y


Just my 2 cents

---

### Post by ohbill on 2012-08-23
a simple script that converts m4a to mp3...


for i in *.m4a; do mplayer -quiet -ao pcm:fast:waveheader:file=output.wav "$i" && lame --quiet -h -b 320 output.wav "$i.mp3" && mv "$i.mp3" "`echo "$i.mp3" | sed -e 's/m4a.mp3/mp3/'`" && rm output.wav && rm "$i"; done

---

### Post by Airycat on 2012-11-15
> **dbeckham32 said:**
> You should try downloading a program called "gnormalize". It will allow you to convert one or an entire directory of MP4 files into MP3 or another output format. Works great, and has a graphical interface to boot.


[http://gnormalize.sourceforge.net/](http://gnormalize.sourceforge.net/)


How does one install this? I'm a total noob and need explicit instructions/code. the code on the dl page didn't work. I only just figured out that this is why I'm not getting half my music.

---

### Post by qneill on 2013-01-17
> **Airycat said:**
> How does one install this? I'm a total noob and need explicit instructions/code. the code on the dl page didn't work. I only just figured out that this is why I'm not getting half my music.

Near the bottom of the [http://gnormalize.sourceforge.net/](http://gnormalize.sourceforge.net/) page there is:

[INDENT]
To install gnormalize, with root privilege, execute the bash script command:
tar zxvf gnormalize-version.tar.gz
cd gnormalize-version/
./install[/INDENT]

So you must download it (click on the link on that page), open a terminal window (google it), then type the commands as you see them.  The first extracts files out of the "gnormalize-version.tar.gz" archive.  The second changes your current directory into the newly extracted one.  The third run installs the software.
-- 
qneill

---

