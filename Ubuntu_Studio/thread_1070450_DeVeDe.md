---
title: "DeVeDe"
date: 2009-02-15
forum: Ubuntu Studio
---

### Post by marcgh on 2009-02-15
Hi,

Until yesterday evening I used DeVeDe almost every day.

Today a sudden problem happens: when generating a preview or encoding a dvd to ISO this is the error I get :

CONVERSION FAILED
IT SEEMS A BUG OF SPUMUX

I did not change any settings since yesterday.

I uninstalled and reinstalled DeVeDe via add/remove programs but this does not resolve the problem.

Any Ideas?

Marc

---

### Post by radi0j0hn on 2009-02-15
Have you tried Googling SPUMUX to see what it is?
Not much help, but try it!

John

---

### Post by marcgh on 2009-02-15
Hi John,

Thanks for your suggestion.
Yes, I googled around and got to know that (probabely) this has to do with the subtitels or encoding of it.
Still searching.....

Marc

---

### Post by rd1381 on 2009-02-17
> **marcgh said:**
> Hi John,

Thanks for your suggestion.
Yes, I googled around and got to know that (probabely) this has to do with the subtitels or encoding of it.
Still searching.....

Marc
i had the same problem 
open your subtitle in ksubtitle or the gnome version of it : if it said unsupported format its probably same error as mine :workaround "subtitle composer" opens this "corrupted" :) subtitle then save them with another name and its fixed

---

### Post by marcgh on 2009-02-17
Hi RD,

Thanks for the help. 
I have tried your work around and it fixed my problem.

Thank you,
Marc

---

### Post by rd1381 on 2009-02-17
> **marcgh said:**
> Hi RD,

Thanks for the help. 
I have tried your work around and it fixed my problem.

Thank you,
Marc

you're welcome;)

---

### Post by jesspepper on 2009-04-10
Hi All,
I had the same problem, but my subtitles file doesn't seem to open with either Subtitle Composer or Subtitle Editor.  Any ideas?

---

### Post by Lucre on 2009-05-28
> **jesspepper said:**
> Hi All,
I had the same problem, but my subtitles file doesn't seem to open with either Subtitle Composer or Subtitle Editor.  Any ideas?



You might just have a bum subtitle file - if it's a popular movie you should be able to find a copy of the subtitle file on the web.  Try googling the name of the film and "subtitles".  Also, I've had pretty good luck with Gaupol, if that's not the Subtitle Editor you're using.

---

### Post by MarkStarCrashes on 2009-10-20
> **marcgh said:**
> ...
Today a sudden problem happens: when generating a preview or encoding a dvd to ISO this is the error I get :

CONVERSION FAILED
IT SEEMS A BUG OF SPUMUX

...

Any Ideas?

Marc

I just had this same problem and solved it by simply displaying the subtitle file (.srt) as a text file and clicking "Save As..." and changing the Character Encoding from "Current Locale (UTF-8 )" to "Western (ISO-8859-15)".

It then was able to be opened by Subtitle Editor and DeVeDe no longer returns that error.

Easy cheesy lemon squeezy!

---

### Post by rev087 on 2009-11-07
I got the same issue...tried converting the .srt to ISO-8859-15 with both gnome-subtitles and gedit, and selecting ISO-8859-15 in DeVeDe. Result? Got the Spumux error message.

Tried with UTF-8 (saving with this encoding, and chosing it in DeVeDe)...no luck.

ACK, SO frustrating! ](*,)

---

### Post by mazzatelli on 2010-01-22
> **rev087 said:**
> I got the same issue...tried converting the .srt to ISO-8859-15 with both gnome-subtitles and gedit, and selecting ISO-8859-15 in DeVeDe. Result? Got the Spumux error message.

Tried with UTF-8 (saving with this encoding, and chosing it in DeVeDe)...no luck.

ACK, SO frustrating! ](*,)

Yeah, this doesn't seem to fix the issue
I've also tried converting the subs to .srt files and re-indexing etc, but devede continues to give me the SPUMUX error.

I have not been able to find any solutions on the net either

---

### Post by mazzatelli on 2010-01-24
Okay I have found it
It involves editing the subtitles with something like Gnome subtitles.

I had alot of {} symbols and odd website references and quotes by the subber in some of the .srt files I was looking at.
Once it was edited to leave just basic text - this error stopped occurring.

---

### Post by yopensource on 2010-02-10
Hi I'm trying the latest version of DeVeDe (3.16).

It works with utf-8 .srt subtitle files. But please select utf-16 or let the program auto detects. ;)

---

### Post by sistematico on 2010-07-02
Same here, with no luck [-o<

[SIZE="1"]Ubuntu Lucid Lynx (32 bits)[/SIZE]

---------------------------- EDIT ----------------------------

I found the problem.

/home/lsbrum/Área\ de\ Trabalho/movie/movie.iso
to
/home/lsbrum/movie/movie.iso

SOLVED for me \\:D/

---

### Post by vipseixas on 2011-05-14
> **sistematico said:**
> 

I found the problem.

/home/lsbrum/Área\ de\ Trabalho/movie/movie.iso
to
/home/lsbrum/movie/movie.iso

SOLVED for me \\:D/

WOW! It solved for me two! 

Who had the great ideia of giving this stupid name to the Desktop folder? It is hard to work with directories that have spaces and accented words :(

Thanx for the tip!

P.S.: Maybe the pt_br translation team should use the MacOS translation "Mesa" for "Desktop".

---

### Post by nkbatsi on 2011-06-01
Guys take extra care with the encoding of subtitles and of course choosing the same encoding method in the subtitle menu in DeVeDe.

For instance if I open a terminal and convert my greek subs from iso8859-7 to UTF-8:

```
iconv -f iso8859-7 -t utf-8 file1.srt > file2.srt
```then I am sure that my encoding is UTF-8, so I choose UTF-8 in the subtitle menu of DeVeDe.

Nevertheless you should always check through your subtitle file for mysterious symbols.

---

### Post by matttbe on 2011-12-30
Hello,

If you still have this problem, this is what I did to fix it:
It seems supmux doesn't support extra subtitle options that are inside {}, (e.g. to change the position, etc.) so simply launch this command to remove these brackets:```
sed -i 's/{.*}//' MY_FILE
```
Or, if you want to repeat this actions for all .srt files in the current directory and all sub-directories: ```
find -name "*.srt" -print0 |xargs -0 sed -i 's/{.*}//'
```
But there is also a problem with html tags... So simply launch this command: ```
sed -i 's/<[^>]*>//g' MY_FILE
```
Or for all .srt files: ```
find -name "*.srt" -print0 |xargs -0 sed -i 's/<[^>]*>//g'
```

PS: I also use Gnome-Subtitle to check if the subtitle is synchronised and to save the subtitle in UTF-8 in my home directory without space character in its name.

---

