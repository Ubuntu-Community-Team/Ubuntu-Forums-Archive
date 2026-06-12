---
title: "Two really useful commandline tricks..."
date: 2011-09-28
forum: The Cafe
---

### Post by shantiq on 2011-09-28
Now i have been using my terminal on ubuntu for the last two years and never knew about these two tricks

I am sure i am not the only one


Got this info [**here**]("http://www.ubuntuka.com/ubuntu-command-line-hints/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+Ubuntuka+%28Ubuntuka%29&utm_content=Google+Feedfetcher")




> Browse the command line history with ctrl-r and then type a few characters that you know are part of the command you are looking for.

first you get this ```
(reverse-i-search)`':
```    then key in your search letters

**Also**
> If you know you typed a command or password wrong, you can use ctrl + u to delete the whole line or ctrl + w to delete just a word.

---

### Post by elliotn on 2011-09-28
well I know if u press the up arrow button u get recently used commands

---

### Post by nothingspecial on 2011-09-28
Moved to the cafe as it is not a support question.

btw

!! expands to the last thing you just typed so, for example if you forget sudo

eg
```

apt-get install really long list of packages that would be really boring to type again
```

you can just type

```
sudo !!
```

---

### Post by shantiq on 2011-09-28
well guys i wonder how many more easy tricks there are  


knew the up and down arrow but thanx for reminding us
as for ```
!!
```  new one on me too

---

### Post by nothingspecial on 2011-09-28
```
cd -
```

will move you back and forth between 2 directories miles away in the file system.

So, say you are at

~/really/deep/directory/far/down/in/your/file/structure

and you move to

~/some/other/deep/deep/directory/miles/away/from/the/previous/one

and you forgot to do something in the first one

```
cd -
```

will take you back there. Type it again to go to the one you moved to.

---

### Post by sisco311 on 2011-09-28
> **nothingspecial said:**
> Moved to the cafe as it is not a support question.

btw

!! expands to the last thing you just typed so, for example if you forget sudo

eg
```

apt-get install really long list of packages that would be really boring to type again
```

you can just type

```
sudo !!
```

Yep, history expansion is very powerful, for example, if you have:
```
apt-get install long list of packages and foo
```
and you want to run the command as root and replace foo with bar:
```
sudo !!:s/foo/bar/
```


```

man bash | less +/"^HISTORY EXPANSION"

```

---

### Post by aeiah on 2011-09-28
speaking of !!:

```

!561
```
will run command number 561, as indexed by ```
history
```

---

### Post by mutley89 on 2011-09-28
Esc then . immediately  expands to the last argument of the previous command.
For example:
```
ls /usr/share/vim
vim [Esc][.]vimrc
```expands to /usr/share/vim/vimrc.  Useful when working with long directory paths

---

### Post by jhonan on 2011-09-28
For me the most useful commandline keystroke is simply [TAB] auto-complete, which makes moving between folders much faster.

[FONT=Courier New]cd hel[TAB][/FONT]
gives me
[FONT=Courier New]cd hello[/FONT]

If there's more than one folder starting with that name, then;

[FONT=Courier New]cd hel[TAB][TAB][/FONT]
gives me
[FONT=Courier New]hello1/ hell/ hell_and_back/[/FONT]

---

### Post by shantiq on 2011-09-28
ok    how is this for lazy


to clear     your have to key in ```
clear
```


5 letters.   Bloody exhausting!




so    ```
ctrl+r
```   key in ```
cl
```    return

3 letters    haaaaaaaaaaaaaaaaa  :KS

---

### Post by coldraven on 2011-09-28
This is for me the best tip
[http://codeinthehole.com/archives/17-The-most-important-command-line-tip-incremental-history-searching-with-.inputrc.html](http://codeinthehole.com/archives/17-The-most-important-command-line-tip-incremental-history-searching-with-.inputrc.html)

So if I want to run the command "alsamixer" which I last used months ago, I just type "al" and hit the up arrow.
Or if I want that very long command like this one
qrencode -o ~/Desktop/test.png -s 6 'Greetings from Joe'
I just type "qr" and press the up arrow a few times
 Bingo!

---

### Post by nothingspecial on 2011-09-28
> **shantiq said:**
> ok    how is this for lazy


to clear     your have to key in ```
clear
```


5 letters.   Bloody exhausting!




so    ```
ctrl+r
```   key in ```
cl
```    return

3 letters    haaaaaaaaaaaaaaaaa  :KS


Not nearly lazy enough.

Press Ctrl-L

it does the same thing.

---

### Post by BrokenKingpin on 2011-09-28
When you get a complete UI lockup you can switch out to the command line with Alt+F1. From there you can print the list of processes with:

```

ps aux

```

From there you can kill the process causing issues:
```

sudo kill -9 [process ID]

```

Now you can switch back to the UI with Alt+F7.

---

### Post by tommpogg on 2011-09-29
> **coldraven said:**
> This is for me the best tip
[http://codeinthehole.com/archives/17-The-most-important-command-line-tip-incremental-history-searching-with-.inputrc.html](http://codeinthehole.com/archives/17-The-most-important-command-line-tip-incremental-history-searching-with-.inputrc.html)


I agree!
By the way, thank you. I was looking for this functionality!

---

### Post by shantiq on 2011-10-26
========================

---

### Post by red_Marvin on 2011-10-26
if you need to run a program with a lot of files as paremeters, like
[COLOR="Navy"][FONT="Courier New"]gvim -p file_name_1 file_name_2 file_name_3 file_name_4 file_name_5[/FONT][/COLOR]
and so on, where the files have some part in common, you can instead do
[COLOR="Navy"][FONT="Courier New"]gvim -p file_name_{1,2,3,4,5}[/FONT][/COLOR]
or instead of
[COLOR="Navy"][FONT="Courier New"]gvim -p main.c main.h usart.c usart.h display.c display.h Makefile[/FONT][/COLOR]
you could
[COLOR="Navy"][FONT="Courier New"]gvim -p {main,usart,display}.{c,h} Makefile[/FONT][/COLOR]

---

### Post by satanselbow on 2011-10-26
Someone wanna sticky this? - it's getting more awesome with every post... except this one :popcorn:

---

### Post by philinux on 2011-10-26
> **satanselbow said:**
> Someone wanna sticky this? - it's getting more awesome with every post... except this one :popcorn:

We already have enough stickies and dont forget the forum search is very useful.

Here are two very useful cli tricks.
```
dpkg -l linux-* | awk '/^ii/{ print $2}' | grep -v -e `uname -r | cut -f1,2 -d"-"` | grep -e [0-9] | xargs sudo apt-get --dry-run remove
```

```
dpkg -l linux-* | awk '/^ii/{ print $2}' | grep -v -e `uname -r | cut -f1,2 -d"-"` | grep -e [0-9] | xargs sudo apt-get -y purge
```

From Here.
[Linky]("http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/")

---

### Post by pr3zident on 2011-10-26
here is some aliases makes things easier when using command line- [http://ubuntuforums.org/showthread.php?t=1858039](http://ubuntuforums.org/showthread.php?t=1858039)

---

### Post by Docaltmed on 2011-10-26
> **nothingspecial said:**
> ```
cd -
```

will move you back and forth between 2 directories miles away in the file system.

So, say you are at

~/really/deep/directory/far/down/in/your/file/structure

and you move to

~/some/other/deep/deep/directory/miles/away/from/the/previous/one

and you forgot to do something in the first one

```
cd -
```

will take you back there. Type it again to go to the one you moved to.

I think I love you.

---

### Post by sffvba[e0rt on 2011-10-26
Cool, actually been reading through a LPCI study-guide and the first chapter is command-line basics and they have about half a page talking about history and auto-complete etc...

Very handy tricks to have :)



404

---

### Post by shantiq on 2011-10-27
CTRL+r seems to have definitely gone belly up on my Oneiric; stopping search after only one key has been pressed and therefore making it useless to trace back entries

ANYONE ELSE finding that?

Any ideas as to fixing it?

---

### Post by mcduck on 2011-10-27
You can repeat the previous command, replacing part of it with something else.

For example:
```
sudo apt-get update
^date^grade
```

---

### Post by matt_symes on 2011-10-27
You can repeat the parameters of the last command using !$. This can come in useful in a number of ways and here is just one.

```
[matthew@myhost ~]$ mkdir -p tmp/tmp/tmp/tmp
[matthew@myhost ~]$ cd !$
cd tmp/tmp/tmp/tmp
[matthew@myhost ~]$ pwd
/home/matthew/tmp/tmp/tmp/tmp
```

---

### Post by Roasted on 2011-10-28
> **nothingspecial said:**
> 
```

apt-get install really long list of packages that would be really boring to type again
```

I love this... I have a command saved up on my Evernote account. I just log in, copy, paste it over on every Ubuntu system I set up. Here it be:



sudo apt-get install gnome-tweak-tool gnome-shell audacious audacity sonata vlc gparted samba system-config-samba thunderbird chromium-browser pidgin xchat hardinfo gimp inkscape etherape cheese leafpad exaile openshot winff wifi-radar apache2 clementine deluge synaptic stellarium p7zip-full wireshark soundconverter

---

### Post by shantiq on 2011-11-05
> **elliotn said:**
> well I know if u press the up arrow button u get recently used commands



Now i was bellyaching since i was having problems with CTRL+r and the fact that is was not letting me go beyond one letter


well the answer was there all the time


and 2 YEARS into using Ubuntu i finally understood something most of you know already;   or was it not just me

the arrow up thing i had always used to scroll back through my recent entries


BUT   what i had never tried/understood/got

was that if you enter one or two letters **it does that with those letters as starting info**



DER....      so CTRL+r    is no longer so useful when you know that


if i go

```
ge
```  for example  and hit upward arrow  all my get-iplayer commands pop up one after the other



also works for

```
cd
``` of course



i guess you all knew that right........just me that is this slow on the uptake   :KS

---

### Post by markbl on 2011-11-05
> **Docaltmed said:**
> I think I love you.
Anybody who likes the "cd -" tip may like my little personal enhancement which I have been using for years. See [https://github.com/bulletmark/cdhist](https://github.com/bulletmark/cdhist).

---

### Post by markbl on 2011-11-05
By the way, many of the tips above are using the emacs command line editing mode of bash which is the default. This is a quirk of history but probably most linux people use the vi/vim editor so perhaps many would prefer to add a "set -o vi" in their ~/.bashrc. This will allow you to simply press ESC and then use your familiar vi commands to find and edit your command history. Start with "/" to search previous commands and then edit the line with normal vi keys. See man bash.

Similarly, add "set editing-mode vi" to your ~/.inputrc and then any program with it's own built-in command interpreter which uses readline will use vi history editing mode.

---

### Post by shantiq on 2011-12-15
ok still trying to undertand something here



 i used to use CTRL+r to see my previous entries in terminal


 and then it stopped working; but then i realized if i entered ```
ti
```



 for example and hit the upward arrow these would come up

```
timidity -iA

```




and all the related ones


 so i thought who needs CTRL+r ?


 THEN I REINSTALLED THE OS [ONEIRIC IN THIS CASE]...



 and CTRL+r works again but AND SADLY


 when i hit   ```
ti
```




 i do not get my previous timidity entries but simply the previous entry in chronological order then the one after and so on



 So my question IS 



 Why is it doing all this? i would much rather have the upward arrow memory thing than CTRL+r


 How can i bring it back? Does it switch to that after one has used CTRL+r for a while; or was it a kink? 



 Some of you must know..... surely

---

### Post by SlugSlug on 2011-12-15
> **coldraven said:**
> This is for me the best tip
[http://codeinthehole.com/archives/17-The-most-important-command-line-tip-incremental-history-searching-with-.inputrc.html](http://codeinthehole.com/archives/17-The-most-important-command-line-tip-incremental-history-searching-with-.inputrc.html)

So if I want to run the command "alsamixer" which I last used months ago, I just type "al" and hit the up arrow.
Or if I want that very long command like this one
qrencode -o ~/Desktop/test.png -s 6 'Greetings from Joe'
I just type "qr" and press the up arrow a few times
 Bingo!


++1 to this, 
only found it the other month ~ best mod I've installed

---

### Post by shantiq on 2011-12-15
slug slug [sorry it was Coldraven] you have answered my previous question here



obviously in my new install i had forgotten to add this



```
sudo gedit  ~/.inputrc
```

then copy

```
"\e[A": history-search-backward
"\e[B": history-search-forward
"\e[C": forward-char
"\e[D": backward-char
``` in the document and save


**bingo!**   amazing functionality is back :KS 

```
ti
```   and hitting the upward arrow

now gives me all my timidity entries again

so thank you   and thanx to the guy who designed this

---

### Post by SlugSlug on 2011-12-15
> **shantiq said:**
> slug slug you have answered my previous question here



obviously in my new install i had forgotten to add this



```
sudo gedit  ~/.inputrc
```then copy

```
"\e[A": history-search-backward
"\e[B": history-search-forward
"\e[C": forward-char
"\e[D": backward-char
``` in the document and save


**bingo!**   amazing functionality is back :KS 

```
ti
```   and hitting the upward arrow

now gives me all my timidity entries again

so thank you   and thanx to the guy who designed this



was **coldraven** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=11293319#post11293319") that posted :)

---

### Post by shantiq on 2012-09-04
remove gaps in a filename[s]  for "_"   or for "nogap"   or for  "." or for &#9668;&#9658; or for a nice Tao sign



**for one filename**


```
rename 's/\ * /_/g'   "my fil e   name.extension"
```



**bulk:**    




===============================================================================


first cd to folder then ::

```
for f in *; 
do rename 's/\ * /_/g'   "$f"  "${f%.*}.*" ;done
```

```
for f in *; 
do rename 's/\ * //g'   "$f"  "${f%.*}.*" ;done
```

```
for f in *; 
do rename 's/\ * /./g'   "$f"  "${f%.*}.*" ;done
```

```
for f in *; 
do rename 's/\ * /&#9668;&#9658;/g'   "$f"  "${f%.*}.*" ;done
```

```

for f in *; 
do rename 's/\ * /&#9775;/g'   "$f"  "${f%.*}.*" ;done
```


or for any symbol which amuses you:

> [SIZE="4"]&#9829; &#9754; &#9755; &#9742; &#9730; &#10026; &#10029; &#10015; &#9774; &#9775; &#9765; &#9770;[/SIZE]


---

### Post by shantiq on 2013-01-26
now this one here is a recent favorite  when one wants to cd to a folder which has a long name with gaps



can be a pain to trace and to get it right and you have to add "" marks to make it works



but there is a really easy way


find a section in the folder name **which is unique** to that long name in the directory and simply place inside 2 asterisks


see example here:


> cd Desktop/***alla***
shantiq@shantiq-00000000000000000000000:~/Desktop/Rozalla Look_No_Further  [1995]


or say

> 
cd /home/shantiq/other/*inda*
shantiq@shantiq-00000000000000000000000:~/other/Hinda Hicks (2004) Still Doin' My Thing#1$ 




and voila   ....    this has really simplified my life at the terminal

---

### Post by shantiq on 2013-04-11
say you want to find a command you used previously and you remember one specific word in that command





```
history | grep wordyouwant



```

and then        ```
!numberyoufound
```    to use again


use in the same way to simply find **any file **which has a name you want anywhere on your computer; handy when you 'lose' files




```
find|grep nameyouwant

```or if you want case-insensitive  ```
find|grep -i nameyouwant
```

=======================

**also**

to remove all bash history permanently [omit w in command if you want this just for current session]


```
history -cw



```


to remove one line from your bash history same principle  [say line 345]


```
history -d 345
```      then   ```
history -w

```

---

