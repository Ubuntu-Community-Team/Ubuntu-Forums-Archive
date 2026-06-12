---
title: "Get rid of Unicode in console"
date: 2012-04-30
forum: Server Platforms
---

### Post by aarta on 2012-04-30
Hi guys, I need to get rid of Unicode in ubuntu's console, I need a pure ASCII console.

unicode_stop is not enough...

I tried: 
export LANG=en_US
setfont
loadkeys it
stty -iutf8
etc etc

I'm using an italian keyboard. 
I tried playing with those commands, but when I type an accented letter (like ò,à,ù) the screen prints 2 weird characters, or it prints the right accented character but when I delete it, two character are deleted instead of one.
It seems like the keyboard keeps pushing two bytes even if unicode is off.


I also have an Opensuse server, and unicode_stop works fine there... what's up with Ubuntu's console ?

---

### Post by aarta on 2012-04-30
I did it at last...
apparently there's a bug in 
/root/.kbd/.keymap_sv  
(mine is the italian keymap, I don't know other languages, your mileage may vary)

I had to modify the following lines, adding a + in front of these character names:

keycode   4 = three            +sterling        
keycode  13 = +igrave           asciicircum      +iacute           Control_asciicircum
keycode  18 = +e               +E               +currency         Control_e        Control_e        Meta_e           Meta_E           Meta_Control_e  
keycode  26 = +egrave           +eacute           bracketleft      Escape          
keycode  39 = +ograve           +ccedilla         at               nul             
keycode  40 = +agrave           +degree           numbersign       Control_g       
keycode  43 = +ugrave           +section          +uacute          


Then in the console:
export LANG=en_US
unicode_stop

and the ASCII keyboard works as expected, at last :)

---

### Post by aarta on 2012-05-04
Now this thread is one of the first results in google, nice :lolflag:
I'll write my latest discoveries then...

Different installations of Ubuntu lead to different results... but the following commands apparently are working for most of the various Linux versions:

export LANG=POSIX
export LC_ALL=POSIX
unicode_stop

POSIX because afaik it should be present in every distro, so there's no need to generate locales by adding them in "/var/lib/locales/supported.d/local" + "locale-gen"


In some Ubuntus I don't have the bug for the accented letters, but I do have it for the following characters "ç°§£", in this case I have to correct the keymap file by hand, and play with "loadkeys it".

):P

---

