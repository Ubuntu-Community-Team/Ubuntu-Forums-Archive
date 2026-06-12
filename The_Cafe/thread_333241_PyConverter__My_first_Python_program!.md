---
title: "PyConverter:  My first Python program!"
date: 2007-01-07
forum: The Cafe
---

### Post by Phatfiddler on 2007-01-07
PyConverter is a python scripted program that converts integers to binary, hexadecimal, and octal, and floating point decimals from fahrenheit to centigrade, and centigrade to fahrenheit.  I designed it to be easy to use, and went for the minimalist style for the GUI.

**There are now 2 versions of the program included in the tar.gz**

PyConverter - Original dual-window version; read-only output; corrected spelling
PyConverterSWM  - New single-window version; read-only output; corrected spelling; expanded output field to accommodate larger outputs.

The program is best used if a quick-launch icon is placed on the panel ,so that you may access it quickly.
I have included the tar.gz file that has the scripts, instructions, and GPL license.

The only dependancies are python and tkinter.


Let me know what you think!

---

### Post by pmj on 2007-01-07
I'm not a big fan of interfaces with multiple windows, especially not as simple ones as this. I also wish you had used GTK instead of this tkinter thing, because I really need some very simple GUI code to rip off for my own little project. ;)

---

### Post by 3rdalbum on 2007-01-07
> **pmj said:**
> I'm not a big fan of interfaces with multiple windows, especially not as simple ones as this. I also wish you had used GTK instead of this tkinter thing, because I really need some very simple GUI code to rip off for my own little project. ;)

Tkinter is much simpler than GTK, and you can run it on Python on any platform. Though admittedly, I too would've liked some GTK to rip off into my own project ;)

---

### Post by EdThaSlayer on 2007-01-07
Being a Python programmer myself(but lacking the guts to share my projects since it won't be real proffesional) I can't wait to see your code. I also code in Tkinter(nice and easy but it only lacks the eyecandy).

btw-I was having problems with finding a way to copy things to the clipboard but reading your code solved that ^_^. Nice program, seems your better than me with using definitions. :-k

---

### Post by xyz on 2007-01-07
Just a thought...shouldn't this be in the FAQ, HowTo section of the site?
A mod would then approve it and it would be added to the "Faqs, Howto, Tips & Tricks".

---

### Post by Lord Illidan on 2007-01-07
> **Phatfiddler said:**
> PyConverter is a python scripted program that converts base 10 decimals to binary, hexadecimal, and octal, and farenheit to centigrade, and centigrade to farenheit.  I designed it to be easy to use, and went for the minimalist style for the GUI.  The interface is Python/Tkinter, and features 2 separate windows to allow the user to place the inbox/output where they may be most effective.  There is also a button to copy the converted data to the clipboard for use in documents.

The program is best used if a quick-launch icon is placed on the panel ,so that you may access it quickly.

I have included the tar.gz file that has the script, instructions, and GPL license.

The only dependancies are python and tkinter.


Let me know what you think!

Pretty good for a first program.

However, multiple windows are not my preference, especially when they are so small as they can be easily placed in a bigger one.

I'd also like to see floating point and negative number support, would be cool...oh, and gtk+ would be nicer. I know that Tk is easier, and indeed your program does a lot of work for just 70-80 lines, but GTK+ looks better, integrates with the desktop, plus...we can use it too :)

Good luck on your electronics major btw.

---

### Post by Phatfiddler on 2007-01-07
> **Lord Illidan said:**
> 
I'd also like to see floating point and negative number support, would be cool...oh, and gtk+ would be nicer. I know that Tk is easier, and indeed your program does a lot of work for just 70-80 lines, but GTK+ looks better, integrates with the desktop, plus...we can use it too :)


Actually, the temperature converter uses floating point, while octal, hex and binary uses integer.  Same for negative numbers, supported by temperatures, but not hex, oct, or binary.

I'll edit the source a little and make a single-window program as well as make a few other adjustments.

I'll look into making a GTK+ version, but it will be a seperate version since I tend to favor Tk because of it's simplicity and portability.

You may see the single-window version as early as today:)

EDIt:  The entire program is 76 lines without the beginning comments :p

---

### Post by meng on 2007-01-07
Firstly, kudos! Although from your initial post I thought that the base conversions would accept floats as input. (I was thinking of proposing this for the next Weekly Programming Challenge, since Python by default only converts integers to octal and hexadecimal.)

Echo the comment about a single window! Have the output go to a second text book that the user can't edit. Also, spelling check! Fahrenheit and Celsius.

---

### Post by Phatfiddler on 2007-01-07
Updated the original post

Added a single-window version due to popular request!
Fixed spelling issues
Added labels to help with navigation
Output is now read-only
Output field expanded to accommodate larger conversions

The single-window version is designed to span the top of your desktop so that you may place it on the title-bar of windows.  This works extremely well when PyConverter is kept on top of all windows.

---

### Post by Phatfiddler on 2007-01-08
I've decided to learn a little GTK+ a make a version using these libraries.  It will be a little more full-featured and have the ability to convert back to integer, as well as binary -> hex, oct etc.

Meng, Lord:

If either of you know how to use floating point with all of the conversions let me know.  While I figured out the binary stuff, and the hex and octal are built in, I could only use integers like you said.  I would love to incorporate full floating for all conversions.

---

### Post by meng on 2007-01-08
> **Phatfiddler said:**
> I would love to incorporate full floating for all conversions.
I would have thought about doing it manually (!) unless there's a numpy/scipy library to take advantage of.

---

### Post by Phatfiddler on 2007-01-09
After looking around for a while I'll probably have to do it manually.  No biggie, just takes a little more thought than I was prepared for;) 

Btw, started the Gtk+ version and I finished the GUI.  Looks pretty sharp.  I'll have more details after I sleep:p

[IMG]http://cutlersoftware.com/pyc.png[/IMG]

---

### Post by Lord Illidan on 2007-01-09
> **Phatfiddler said:**
> I've decided to learn a little GTK+ a make a version using these libraries.  It will be a little more full-featured and have the ability to convert back to integer, as well as binary -> hex, oct etc.

Meng, Lord:

If either of you know how to use floating point with all of the conversions let me know.  While I figured out the binary stuff, and the hex and octal are built in, I could only use integers like you said.  I would love to incorporate full floating for all conversions.

I only know how to floating point conversions in binary, and manually, anyway. I've just learned how to do it in A level CS.

However, I know of a great desktop calculator, called Qalculate which does this, perhaps you can take a look at the source and rip off something?

[http://qalculate.sourceforge.net/downloads.html](http://qalculate.sourceforge.net/downloads.html)

Apparently, that uses C++...so you might be a disadvantage

EDIT : You could always google for more solutions. I found this : [http://aspn.activestate.com/ASPN/Cookbook/Python/Recipe/393090](http://aspn.activestate.com/ASPN/Cookbook/Python/Recipe/393090)

---

### Post by meng on 2007-01-09
Hmm, to convert floats to other bases manually, I think you'd multiply the fraction by the base, discard the (new) fraction, then obtain the last digit and that's your first digit after the "decimal" point. Then restore the fraction, multiple the number by the base, obtain the last digit after base conversion, and that's your second digit after the "decimal" point.

e.g. to convert
0.12345 base 10, to base 8
multiply by 8 is 0.9876, 0 in base 8 is 0 so first digit is 0
multiply 0.9876 by 8 gives 7.9008 so second digit is 7
multiply 0.9008 by 8 gives 7.2064 so third digit is 7
multiply 0.2064 by 8 gives 1.6512 so fourth digit is 1
multiply 0.6512 by 8 gives 5.2096 so fifth digit is 5

so 0.12345 base 10 is 0.07715.... base 8

---

### Post by Valinski on 2007-01-09
Had a look at your program. Looks good! Im still working around the basics of programming so cant really give a good review but least to say i was impressed.

---

### Post by Phatfiddler on 2007-01-09
Had a long 8-hour class today, so took some pen and paper to try and figure some of this out.  Should be able to incorporate negative binary now.

Lord:

I COULD use the C++ from that program, but I would have to import the code from a seperate file, and would need to learn some C++ in order to have it work as I needed it to.  From what I understand, the C++ integration could cause issues for some interpreters.  Probably not all that complicated - just time consuming.  But, since I am learning Python currently, I think I'll have a go at it manually.  At least that way I'll get to learn some new tricks in the process, along with pyGtk and Glade.

Meng:

Thats the way I was thinking of doing it, but I was hoping for a cleaner way.  This is how I will probably end up getting the results I need for the program, and I can experiment with it after I have it working the way I want.

I have a few of the conversions working in pyGtk without the Glade interface, so I am going to get them all working, and then use the new interface that I included above.  Keep in mind that it is a rough idea right now, and may very well change.  Also, look forward to "Integer" being removed from those radio buttons;) 

Wish me luck!

---

