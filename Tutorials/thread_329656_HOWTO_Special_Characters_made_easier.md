---
title: "HOWTO: Special Characters made easier"
date: 2007-01-01
forum: Tutorials
---

### Post by jem7v on 2007-01-01
This was written for Edgy, but it probably works in other releases too.

Back in Dapper Drake, you could press CTRL+SHIFT and then the unicode for special characters so you didn't have to copy and paste them from the Character palette every time you wanted to use them.  This stopped working in Edgy, which greatly reduced my ability to type in Spanish.  The Spanish keyboard layout doesn't contain any letters with accents except ñ, so it didn't help much.

Then I found the magic solution!  A handy little tool called the COMPOSE KEY.

[SIZE="2"]Go to System -> Preferences -> Keyboard, then go to the Layout Options tab.  There are several headings here, and the important one that says Compose Key Position.  Choose a key you don't use for much, and set it as your Compose key!  (I use my right WINDOWS key)

To use it, hold the Compose key down and then type in the characters you want to mash together.  For example, you can make an ñ by typing <compose>+n+~, or è by typing <compose>+e+`, or ß by typing <compose>+s+s and voila your letters appear.[/SIZE]


Maybe there was already a howto about this, or maybe lots of people already know this - but I looked for an answer to this problem for a long time and I didn't find one.  I heard ABOUT compose keys in other operating systems (like OSX) but didn't figure it out until I was looking for a different keyboard setting.  I hope at least Some people can find this helpful.

---

### Post by userundefine on 2007-01-09
Hé, great hôwtò !  I'm on a US English keyboard and frequently have to type in French, so this makes it SO much easier.  I had to find this thread with the search tool, so I hope more can see this so I'm bumping it to the top!

---

### Post by stalefries on 2007-01-09
One trick that I really like is the Character Palette applet. It's not that good for languages with accent characters, but it is good for keeping around special characters that you use sometimes, like &#12484;. You can define multiple sets of special characters, it comes with several built-in. I keep it in a drawer on my bottom panel.

---

### Post by Buck2348 on 2007-01-11
This is a helpful post, Jem7v.  I stumbled onto the compose key a few weeks ago, probably while reading the Forums.  One of the best features of Linux is that almost anything you do with it can be customized.  Same for using the Compose Key.  For some reason Edgy isn't set up as well as it might be for using it.  For example, you can't make fractions like ½ with it.  To fix that you need to add a line to /etc/environment:
```
gksudo gedit /etc/environment
```
add the following:
```
export GTK_IM_MODULE=xim
```
now copy a file to your home folder:
```
cp /usr/share/X11/locale/en_US.UTF-8/Compose ~/.XCompose
```
This will give you a more complete character set.  Also you can edit that file.  Suppose for example that your keyboard doesn't have a tilde (~).  You can change the lines that require entering a tilde so that a simple "t" (or whatever you like) wil work.  Just don't use a key combination that's already in use somewhere else.  You can check that by entering the combination before you change anything and see if you get any character output.  Also you can browse through this file to find the key combination for the character you want if it isn't fairly obvious.

I learned this from this thread:  [http://ubuntuforums.org/showthread.php?t=209115]("http://ubuntuforums.org/showthread.php?t=209115")

Buck

---

### Post by icefaerie on 2007-01-15
WOW!  Thank you so much for posting this!  This was one of the few things keeping me booting into Windows, because typing essays in Spanish is a pain without the quick input method for special charactes.

---

### Post by userundefine on 2007-01-23
I've been using KDE lately and was missing my Compose Key.  So I found out how to do it in KDE:

Go to Control Center > Regional & Accessibility > Keyboard Layout.

In Xkb Options (simply "Options" for older KDE versions), check "Enable xkb options", scroll down to "Compose Key Position", choose which key(s) you want to use to make your special characters, then Apply.

Ànd áway yoû g&#339;!

---

### Post by ricardisimo on 2007-03-07
I'm in the same position, where my primary language is English, but I write to my family extensively in Spanish. Easily the best compromise has been choosing US International with dead keys as my default keyboard layout. Very simple <ALT> modifier options; <ALT>+n is ñ, <ALT>+a is á, and so on... áéíóúñ¡¿&#8364; with quite a few others that you'll rarely if ever use.

The dead keys are a bit of a problem, more so in Ubuntu than in Windows. The main dead keys are ", ', `, and ~, all of which require you to remember to hit <SPACE> if you actually want them as is, rather than as a modifier. In Windows, it's a bit more intuitive, where you can type an ' and then an s and get 's, rather than &#347; as in Ubuntu. I believe Windows only allows the dead keys to modify the vowels, which makes more sense for any US-family layout. Ubuntu modifies stuff you don't want, or - if there is no character associated with the keycode - drops both of your keys. Typing "I'd" requires you to hit I+'+<SPACE>+d, or else you just get the "I". Windows has similar problems with the double quotes.

I'm wondering what would be easier: adding the <ALT> combinations to US English, or removing the dead keys from US International. There is a "Clear" command with xmodmap that seems to do something like what I'm seeking, but I'm uncertain of the syntax I need to use, and being still noobish I'm wary of losing keyboard functionality in any way and not knowing how to restore defaults. I'd appreciate any suggestions. thanks.

---

### Post by dhallar on 2007-03-12
I've chosen the right Ctrl key as my compose key. Now: How do I set the key combinations that I want? [I need a Spanish set.  I'm using Edgy.]

---

### Post by Flavian on 2007-05-10
Hi guys. Maybe someone of YOU can help me :( I am really desperate, because I can't get this to work. Since I am an Austrian and we speak German here I got the following problem. Some characters would look weird.
I've kinda found out that with unicode they don't.
With Evolution i've got the following problem that I already postet in another thread but never got an answer :( 
It can be found here:
[http://ubuntuforums.org/showpost.php?p=2531021&postcount=11](http://ubuntuforums.org/showpost.php?p=2531021&postcount=11)

Also with attachments that I send in Evolution it sometimes does not treat the filenames right. and places like ? in place of the Üs :(

Maybe someone can help me with that.
Thanks in advance.
Florian

---

### Post by cosmolee on 2007-05-14
Setting the Compose key is a great solution for inputting accented characters!  

However, I've discovered a vexing problem when displaying such text with `vi`.  Take the following line I created using the Compose key (note: there are tabs between the words, not spaces):

poder   uede    emos    éis    ueden   riXX


Starting with the cursor at the beginning of the line, one moves from word to word with the `w` command.  Hitting `w` three times, thus moves the cursor to the beginning of the word "éis",  However, once more, then the cursor moves to the letter "i" instead of the next word "ueden".  Hitting `w` again, the cursor moves to the letter "s" instead of the word "ueden".  Hitting `w` once again, the cursor moves to the next word, but instead of positioning at the first letter "u" of "ueden", it positions at the second letter "e" of "ueden".  ie, the cursor positioning gets all screwed up visually.  `vi` thinks it's at the beginning of the word "ueden", but the display shows it at the letter "e".  Hitting `w` again, the cursor then moves to the next word "riXX", but is positioned at the second letter "i" instead of the first letter "r".

Any idea what gives??

TIA.

---

### Post by userundefine on 2007-05-15
I don't know, maybe your vi is old?  Are you using vi or vim?  Works for me no problem in vim.  I didn't try vi.

vim > vi anyway.

---

### Post by cosmolee on 2007-05-16
`vi` and `vim` are the same on Ubuntu.  I'm using Dapper 6.06.  My version of `vim` is 6.4, 2005-10.  Is your version newer?  

Here's the odd behavior I get with `vim`:

insert-mode - I type:

<right-alt-e>'xxx<tab><right-alt-i>'yyy


displayed on screen - notice extra <spaces>:

<accented-e><space>xxx<tab><accented-i><space>yyy


However, after I <ctl-L> to redraw the screen, the <spaces> disappear from view!:

<accented-e>xxx<tab><accented-i>yyy


If I am in command-mode, and move backward and forward with "w" and "b", the cursor moves around as if the <spaces> are still there, and treats the (invisible) <space> as if it's a separate word.  I tried copying the letters from Character Map and the same thing happens with the extra spaces.  

I tried this on an Ubuntu Edgy box - same thing.  Nobody else getting anything like this with `vim`??

I also tried entering the accented letters with Open Office, and this appears to work fine without any of the above issues.  This therefore seems like a vim-specific problem.

---

### Post by userundefine on 2007-05-16
vim - 7.0.164

éxxx    íyyy

Feisty.

No spaces, everything works.

Upgrade vim.

---

### Post by cosmolee on 2007-05-18
Ah, I found the problem - it's the setting of the LC_TYPE environment variable.  Type `locale` at the command line to see the various values for your environment.  

For anyone reading this in the future, you must set it to a type that is not incompatible with accented characters.  The incompatible types include "C" and "POSIX".  (To replicate the odd behavior I described previously, set LC_CTYPE or LC_ALL to one of these.)  

The tricky part is that if you set LC_ALL to a value, it also sets LC_CTYPE (and a bunch of other subordinate environment variables) to that value.  And in order to set LC_CTYPE to a value, LC_ALL must *first* be set to a NULL value in order to reset LC_CTYPE.  If LC_ALL is set to a non-NULL value and you try to set LC_CTYPE to something, LC_CTYPE (and other subordinate variables) won't take the new value.

I did this in my .bashrc file by doing the following (you could also do this on the command line):

export LC_ALL=
export LC_CTYPE=en_IN


Note that execution order is important.  If you set LC_ALL=POSIX after the above lines, it will override the LC_CTYPE value.  So, if you want to use LC_ALL to set a bunch of subordinate values, first do that, then set LC_ALL to a NULL value, then set your individual LC_* values - in this example, LC_CTYPE - to whatever individual values you wish to set.

HTH.

---

### Post by oldHat on 2007-05-19
> **userundefine said:**
> Hé, great hôwtò !  I'm on a US English keyboard and frequently have to type in French, so this makes it SO much easier.  I had to find this thread with the search tool, so I hope more can see this so I'm bumping it to the top!

I don't want to hijack this thread, but if you simply want to type in French, there's an easier way.

See:  [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_type_extended_characters]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_type_extended_characters")

This gives you éèíìáóçô in 2 simple keystrokes (accent + character). ü takes 3 keystrokes:  shift,¨+u

You also get these:  € £ ¥ ° ¶¹²³¤¼½¾÷æ

---

### Post by userundefine on 2007-05-19
> **oldHat said:**
> I don't want to hijack this thread, but if you simply want to type in French, there's an easier way.

See:  [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_type_extended_characters]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_type_extended_characters")

This gives you éèíìáóçô in 2 simple keystrokes (accent + character). ü takes 3 keystrokes:  shift,¨+u

You also get these:  € £ ¥ ° ¶¹²³¤¼½¾÷æ
Hey, nice tip !  Thank you.

---

### Post by hughh on 2007-07-22
> This was written for Edgy, but it probably works in other releases too.This should work not only in all Ubuntu releases, but in all Linux distributions as well.  See this [blog post]("http://www.pthree.org/2006/11/30/its-unicode-baby").

---

### Post by yogo on 2007-09-10
Thanks Jem7v,

That was simple, I was looking at all kinds of things and your was the quickest!

Thanks.

---

### Post by Skrean on 2009-02-16
> **jem7v said:**
> This was written for Edgy, but it probably works in other releases too.

Back in Dapper Drake, you could press CTRL+SHIFT and then the unicode for special characters so you didn't have to copy and paste them from the Character palette every time you wanted to use them.  This stopped working in Edgy, which greatly reduced my ability to type in Spanish.  The Spanish keyboard layout doesn't contain any letters with accents except ñ, so it didn't help much.

Then I found the magic solution!  A handy little tool called the COMPOSE KEY.

[SIZE="2"]Go to System -> Preferences -> Keyboard, then go to the Layout Options tab.  There are several headings here, and the important one that says Compose Key Position.  Choose a key you don't use for much, and set it as your Compose key!  (I use my right WINDOWS key)

To use it, hold the Compose key down and then type in the characters you want to mash together.  For example, you can make an ñ by typing <compose>+n+~, or è by typing <compose>+e+`, or ß by typing <compose>+s+s and voila your letters appear.[/SIZE]


Maybe there was already a howto about this, or maybe lots of people already know this - but I looked for an answer to this problem for a long time and I didn't find one.  I heard ABOUT compose keys in other operating systems (like OSX) but didn't figure it out until I was looking for a different keyboard setting.  I hope at least Some people can find this helpful.

Thanks!!
After installing Language support for French I was still not able to type the characters.:confused: Setting up the 'compose' key solved my problem.:)

---

### Post by joker77 on 2009-04-16
Character palette set up using character map turns out to be best for me: occasional use of arrows, greek letters, mathematical symbols & the like.

Thanks for that! 

I guess the faster options (keyboard shortcuts) are useful for those with frequent requirements, eg accented letters, etc

---

### Post by guriinii on 2009-10-07
Thanks for the advice, really helpful.
The only thing now is the upside down spanish ? ! 

Can anybody help?

---

### Post by polt on 2012-02-02
i love you jem7v!

---

### Post by carol3 on 2013-10-06
I can't get this to work for me at all.  I am on Ubuntu 12.04 and I need to write Spanish.  Can anyone explain in plain language for the technically challenged how I can do this please?

---

### Post by LatGrc on 2013-10-20
> **Buck2348 said:**
> 
...
```
cp /usr/share/X11/locale/en_US.UTF-8/Compose ~/.XCompose
```
...
Buck

Thank you Buck, I needed exactely this line two recover my .XCompose file - if anyone is interested in productiv AncientGreek writing, I've written an "additi&#333; Graeca" for .XCompose to be combined with a new Version of the Layoutfile "gr": [http://ubuntuforums.org/showthread.php?t=2137250&p=12741640#post12741640](http://ubuntuforums.org/showthread.php?t=2137250&p=12741640#post12741640)

It is based on the Windows-Layout, which allows fluent writing in AncientGreek :) As I am "typing on" I will make updates of it for sure, when it is "ripe" :)

Maybe my reuse of unecessary "dead_keys" is helpful to design other keyboard layouts for scripts with many diacritics :)

Thank you all again :)

M&#257;rcus Veneri&#257;nus Lat&#299;n&#275;Am&#257;ns

---

### Post by tea for one on 2013-10-29
> **carol3 said:**
> I can't get this to work for me at all.  I am on Ubuntu 12.04 and I need to write Spanish.  Can anyone explain in plain language for the technically challenged how I can do this please?

Good evening,

Here is a list of Spanish characters with their keyboard shortcuts. 
Please ensure that you have _not_ set a Compose key under Keyboard > Layout Settings > Options

AltGr semi-colon a		=	á

AltGr semi-colon e		=	é

AltGr semi-colon i		=	í

AltGr semi-colon o		=	ó

AltGr semi-colon u		=	ú

AltGr [ u 				=	ü

AltGr ] n				=	ñ

AltGr semi-colon c		=	ç

AltGr semi-colon shift a	=	Á

AltGr semi-colon shift e	=	É

AltGr semi-colon shift i	=	Í

AltGr semi-colon shift o	=	Ó

AltGr semi-colon shift u	=	Ú

AltGr [ shift u			=	Ü

AltGr ] shift n			=   	Ñ

AltGr semi-colon shift c	=	Ç

AltGr shift !			=	¡

AltGr shift underscore	=	¿

As an example for line one, press Alt Gr together with semi-colon, release the keys and then press lower case a.

Result should be á

However for ¿, you have to press three keys simultaneously i.e. Alt Gr and Shift and Underscore

Hopefully, you will find it useful

Kind regards

---

