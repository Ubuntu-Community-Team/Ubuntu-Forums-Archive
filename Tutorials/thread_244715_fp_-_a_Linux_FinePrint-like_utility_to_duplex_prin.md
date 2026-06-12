---
title: "fp - a Linux FinePrint-like utility to duplex print .ps files into A5 booklets."
date: 2006-08-26
forum: Tutorials
---

### Post by docplastic on 2006-08-26
Purpose: To emulate SOME of the booklet printing functions of the Windows FinePrint utility ([http://www.fineprint.com/](http://www.fineprint.com/)), i.e. trying to save a few sheets of paper.

         It will not concatenate .ps files.
         It will not properly print to a .pdf file, nor to any other thing besides a physical printer.
         It has been tested to reliably print to many printers (both InkJet and Laser).
         It will manually print front and rear (duplex), even in plain, non duplex, printers.


A. **Command Line Version** (there is also a "point-and-click" version to print from the Nautilus File Browser, see B. paragraph bellow)

1. Copy and paste the following code it into a text file named fp
2. Make it executable  with the command: *chmod 755 fp*
3. **Copy that file to a directory in your PATH**. You may want to copy it into your own private /bin dir created with the command:  *mkdir -p /home/`whoami`/bin*. If you name it /bin It will be automatically added to your environment the next time your system boots.
4. Print the file with the command: fp filename.ps
5. Remember that any printed file in Linux starts its life as a .ps file, so all what you have to do is, from any program, select "Print", choose any printer, click the "print to file" check mark and print it into a .ps file.

```
#!/bin/bash
#
# fp is a fineprint-like utility to duplex print postscript - .ps -
#    files into A5 booklets.
#
# Tested with HP, Epson and Canon InkJets.
# It prints front and rear, even in plain (non duplex) printers.
#
# It will accept a .ps file and modify it (compressing
# and rotating each two A4 pages into a single A4 sheet).
#
# It will print front (odd) pages and then wait for you to
# reinsert the printed paper. Once paper reinserted it will
# print rear (even) pages.
#
# In the end you may fold the printed sheets to form an A5 booklet;
#
# Copyright © 2005-2008 by J. Antas.
# Licensed under a GPL 2.0 License (full text available
# at http://www.gnu.org/copyleft/gpl.html)
#
if !((test -f /usr/bin/psbook) && (test -f /usr/bin/pstops)) ; then
	echo -e "\nYou need to (re)install the 'psutils' package, " ;
	echo -e "Try installing it with 'sudo apt-get install psutils'\n" ;
	exit 62;
fi;
if [ -z "$1" ] ; then
	echo -e "\nUsage: `basename $0` filename.ps\n";
	exit 64;
fi;
if [ -f "$1" ] ; then
	echo -e "Script `basename $0` started...\n" ;
	#
	/usr/bin/psbook $1 | /usr/bin/pstops -q -p a4 
"4:1L@0.7(21.0cm,14.95cm)+0L@0.7(21.0cm,0.6cm),3L@0.7(21.0cm,14.95cm)+2L@0.7(21.0cm,0.6cm)" 
> "tmp-$1";
	echo -e "\nPrinting to the default printer: odd pages first...";
	# printer def: -P PrinterName as seen using: lpstat -a
	# If no printer it will use the default printer
	# You may also set the PRINTER env variable with: export PRINTER=tp0
	/usr/bin/lpr -o page-set=odd -o outputorder=reverse "tmp-$1";
	echo -n "...after printing this batch, load the paper back in and hit 
<enter>";
	read dummy;
	echo -e "\nNow printing even pages...\n";
	/usr/bin/lpr -o page-set=even "tmp-$1";
	echo -e "Done.\n";
	/bin/rm "tmp-$1";
else
	echo -e "\nFile '$1' was not found. Program aborted\n";
	exit 66;
fi;
exit 0;
#end of code

```


**UPADATE: 2010.01.10 - Attached bellow is code to "point-and-click" print from Ubuntu's Nautilus File Browser**

B. **"Point-and-Click" Version**:

This version will let you **print directly from the Nautilus File Browser by right clicking at the selected .ps file**.
NOTE: In Linux a  printed file starts its life as a .ps (postscript) file. In order to have a .ps file, all what you have to do is, from any program, select "Print", choose any printer, click the "print to file" check mark and print it into a .ps file.

1. Copy and paste the following code it into a text file named fprint
2. Make it executable: chmod 755 fprint
3. **Copy that file to $HOME/.gnome2/nautilus-scripts**
4. Start printing by right clicking at the desired .ps file and selecting fprint from the right click drop-down menu.

```
#!/bin/bash
#
# fprint: fineprint-like utility to duplex print a .ps files into A5 booklets.
#  prints front and rear, even in plain (non duplex) printers;
#  accepts a .ps file and modifies it, compressing
#  and rotating each two A4 pages into a single A4 sheet;
#  prints front (odd) pages first and then waits for you to
#  reinsert the printed paper. Once paper reinserted it will
#  print rear (even) pages.
#  you may fold the printed sheets to form an A5 booklet;
#
# Copyright © 2005-2010 by J. Antas.
# Released under a GPL 2.0 License (full text available
# at http://www.gnu.org/copyleft/gpl.html)
#
# make this script executable and copy it to ~/.gnome2/nautilus-scripts/
#
IFS=$'\n' ; # Set word splitting to happen at a new line, instead of spaces
NEEDBIN="/usr/bin/psbook"
NEEDPACK="psutils"
test -x $NEEDBIN || { zenity --question --title="ERROR: uninstalled dependencies" --text="${0##*/} needs the $NEEDPACK package which is not installed.\n\nTo install $NEEDPACK run the following from a shell terminal:\n\n  sudo aptitude -R install $NEEDPACK" && exit; }

printer=$(lpstat -d | sed 's/\(.*\) \(.*\)/\2/') # get DEFAULT PRINTER
# if you configure a printer instance as BW and put bw somewhere in its device name, you will be able to print in BW only:
#printer=$(lpstat -a | sed -n '/bw/s/\([^ ]\+\) .*/\1/p') # choose black&white printer
# if you configure a printer instance as COLOR and put color somwhere in its device name, you will be able to print in color only:
#printer=$(lpstat -a | sed -n '/color/s/\([^ ]\+\) .*/\1/p') # choose black&white printer

tmpfile=$(mktemp)
for FILE in $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS ; do
	file="$(echo "$FILE" | sed 's/ /\\ /g')"
	$NEEDBIN "$file" | /usr/bin/pstops -q -p a4 "4:1L@0.7(21.0cm,14.95cm)+0L@0.7(21.0cm,0.6cm),3L@0.7(21.0cm,14.95cm)+2L@0.7(21.0cm,0.6cm)" > $tmpfile
	echo "$file" | grep " " > /dev/null 2>&1 && { zenity --info --title="ERROR: pathname has spaces" --text="Offending file: $file"; break; }  # if pathname has spaces, abort.

	/usr/bin/lpr -P $printer -o page-set=odd -o outputorder=reverse $tmpfile
	if zenity --question --title="Fine Printing to $printer..." --text="Printing $file\nPrinting odd pages first,\nWhen finished load the paper back in and click OK"; then
		/usr/bin/lpr -P $printer -o page-set=even -o outputorder=reverse $tmpfile
	fi 
	killall zenity
done
[ -f $tmpfile ] && /bin/rm $tmpfile
exit 0

```


Enjoy,

J. Antas

---

### Post by wilberfan on 2006-08-27
I LOVE fineprint!   But I can't get this to execute...   Typing 'fp' into a terminal just results in a "bash: fp: command not found" error message.

I know it must be something ridiculously simple I'm missing...but I can't for the life of me figure out what it is...!

---

### Post by Nokia on 2006-08-27
I guess you've missed STEP 2.
> 2. Put it into a directory in your PATH.

---

### Post by docplastic on 2006-08-27
The code was "redone" to make the page setup even more customizable.

I would like to see this to grow into some kind of printer filter useable from any program without the extra assle of first producing a .ps file, then enter that file's dir and finally "fp" (fineprint) it.

But, as is, it is already a rather good "paper saver".

P.

---

### Post by docplastic on 2006-08-27
> **wilberfan said:**
> I LOVE fineprint!   But I can't get this to execute...   Typing 'fp' into a terminal just results in a "bash: fp: command not found" error message.

Either you put it in a directory somewhere in your path. To see what your current PATH is, open a terminal window and execute the command:
 ```
echo $PATH
```

Or, you may just put your .ps files in the same directory where you have put the fp script and "dot-slash execute" it:
 ```
./fp some_test_file.ps
```

P.

---

### Post by wilberfan on 2006-08-28
> **docplastic said:**
> Either you put it in a directory somewhere in your path. To see what your current PATH is, open a terminal window and execute the command:
 ```
env | grep PATH
```

Or, you may just put your .ps files in the same directory where you have put the fp script and "dot-slash execute" it:
 ```
./fp some_test_file.ps
```

P.

Hey, thanks for this.  It helps.  Well, a little. 

OK, that 'PATH' thing confused me--never having encountered it before (aren't n00bs annoying?!).  I (assumed) it was my "home" folder, or something...

This is what comes up when I execute that grep PATH command:

PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games

I don't really know what it's saying, but it sure explains why 'fp' wouldn't run on my system!

---

### Post by wilberfan on 2006-08-28
Ooooo-kay.   I've got PATH figured out.  (Who knew??!)  But I had to install 'psutils'.  And now I get this: 

/> usr/bin/pstops release 1 patchlevel 17
Copyright (C) Angus J. C. Duggan, 1991-1995. See file LICENSE for details.
Usage: /usr/bin/pstops [-q] [-b] [-wwidth] [-hheight] [-dlwidth] [-ppaper] <pagespecs> [infile [outfile]]
/usr/local/bin/fp: line 35: 4:1L@0.7(21.0cm,14.95cm)+0L@0.7(21.0cm,0.6cm),3L@0.7(21.0cm,14.95cm)+2L@0.7(21.0cm,0.6cm): command not found

Printing to the default printer: odd pages first...
/usr/bin/lpr: Error - no default destination available.


I guess I now have to figure out how to set my 'default printer'!  :-k

---

### Post by Nokia on 2006-08-28
In GNOME, take a look in System-Administration-Printing. It might help. Right now I'm on a laptop with no printer at hand, but it worth to try :)

---

### Post by docplastic on 2006-08-28
> **wilberfan said:**
> Ooooo-kay.   I've got PATH figured out.  (Who knew??!)  But I had to install 'psutils'.  And now I get this: 
...I guess I now have to figure out how to set my 'default printer'!  :-k

1. Please note that line 35 is a single line that starts with "/usr/bin/psbook..." and ends with "tmp-$1"
   and between "...-p a4" and "4:1L@0.7..." there should only be a single space and nothing else.

2. In the Gnome menu (menu at the top os the screen) select "System" -> "Administration" -> "Printing" and (re)install your printer. After checking that it is installed, right click on it, open "Properties" and select "Print a Test Page" and check if it spoils some paper. Then click "Close".

3. At the "Printing" screen left click on your printer and after that right click on it and select "Make Default" (if this option is unavailable it most probably means that it already is your default printer).

4. Get out of screen that and try using "fp" again.

P.

---

### Post by wilberfan on 2006-08-28
> **docplastic said:**
> 1. Please note that line 35 is a single line that starts with "/usr/bin/psbook..." and ends with "tmp-$1"
   and between "...-p a4" and "4:1L@0.7..." there should only be a single space and nothing else. 

Wow.  Thanks.  I NEVER would have caught THAT one.  (I had "text wrap" on in gedit....  Again, who knew?)


> 2. In the Gnome menu (menu at the top os the screen) select "System" -> "Administration" -> "Printing" and (re)install your printer. After checking that it is installed, right click on it, open "Properties" and select "Print a Test Page" and check if it spoils some paper. Then click "Close". 

"The CUPS server could not be contacted".   Crap.   I wonder what's wrong NOW?...  :confused: 

OK....more debugging...    But thanks loads for the help so far! 

Scott

---

### Post by Nokia on 2006-08-28
What brand is your printer ?

In a terminal, do >  sudo apt-get update && sudo apt-get install cupsys

---

### Post by wilberfan on 2006-08-28
> **Nokia said:**
> What brand is your printer ? 

It's an HP 820Cse.  It was working the other day--and it was networked through my other dual-boot box!  :D 

>  In a terminal, do sudo apt-get update && sudo apt-get install cupsys 

You think it got uninstalled somehow?    I'll give it a try.   Thanks!

---

### Post by wilberfan on 2006-08-28
> 
In a terminal, do sudo apt-get update && sudo apt-get install cupsys 

Nope.  No dice.   Still can't contact CUPS server....  Something else is wrong...:-k

---

### Post by Nokia on 2006-08-28
If you had it operational the day before, check the cables and power switch

---

### Post by wilberfan on 2006-08-28
> **Nokia said:**
> If you had it operational the day before, check the cables and power switch

Tried that.  There's something else seriously wrong:   Now I don't even get the error message about not being able to contact the CUPS server.  Sometimes I get an empty error window--that "is not responding".   

And NOW my UBuntu Power Off button takes, like, 2 minutes to respond!!

I even reinstalled CUPS via synaptic... 

Nope.  There's somethin' serious goin' on here...   ](*,)

---

### Post by wilberfan on 2006-08-29
> **wilberfan said:**
> Tried that.  There's something else seriously wrong:   Now I don't even get the error message about not being able to contact the CUPS server.  Sometimes I get an empty error window--that "is not responding".   

And NOW my UBuntu Power Off button takes, like, 2 minutes to respond!!

I even reinstalled CUPS via synaptic... 

Nope.  There's somethin' serious goin' on here...   ](*,)

Well, just for the record, I pussed-out and turned to the only remedy I had the patience for:   I re-installed Ubuntu.  I'm not proud; but it got me out of the hole I found myself in.   

[big exhale] How can something be so interesting--and so friggin' frustrating--all at the same time?!  ](*,)

---

### Post by Nokia on 2006-08-29
Next time try searching a bit more the forums. I'm not a linux expert, but i can assure you that given time and patience you'd have found solutions for your problem on the forums. There's a rare situation when a novice finds a never-seen-before problem and there's no one able to find a solution in a fair amount of time.
One more thing. It would be best if you could be more specific next time you encounter a problem. No one could've guessed that you had a functional printer the day before untill you mentioned it, for instance ;)
Best wishes,
N.

---

### Post by wilberfan on 2006-08-29
> **Nokia said:**
> Next time try searching a bit more the forums. I'm not a linux expert, but i can assure you that given time and patience you'd have found solutions for your problem on the forums. There's a rare situation when a novice finds a never-seen-before problem and there's no one able to find a solution in a fair amount of time.
One more thing. It would be best if you could be more specific next time you encounter a problem. No one could've guessed that you had a functional printer the day before untill you mentioned it, for instance ;)
Best wishes,
N.

Point well taken.   I think I just hit the wall.  I've been spending some 10-12 hour days on this stuff, and sometimes the brain and body just scream *"enough"!*  It was a choice between continued digging--or just getting it back to "normal" so I could get on with my life.

"Normal" would take a couple of hours; who knows how long more digging would have taken.  

It's fun; it's frustrating; I'm learning a lot; I'm proud of my progress; I'm pissed-off... 

I'm guessing that's pretty standard Penguinista N00b-itis?  :rolleyes:

---

### Post by haelen on 2007-02-08
This works brilliant. Only one problem: The page margins are unequal and I'm not sure how to adjust them.

---

### Post by haelen on 2007-06-20
> **haelen said:**
> This works brilliant. Only one problem: The page margins are unequal and I'm not sure how to adjust them.

I've just upgraded to Feisty Fawn and now I get this when I try fp:

```
The program 'fp' is currently not installed.  You can install it by typing:
sudo apt-get install fp-ide
Make sure you have the 'universe' component enabled
bash: fp: command not found
```

---

### Post by fullburned on 2007-10-28
Here is my problem...
The script runs ok, no problems in terminal, but the printer actually doesn't print! My error_log messages:
```
E [28/Oct/2007:13:17:01 +0200] [Job 38] Cannot Process Raster
E [28/Oct/2007:13:17:01 +0200] PID 6397 (/usr/lib/cups/filter/rastertoz35) stopped with status 1!
E [28/Oct/2007:13:17:05 +0200] [Job 38] Job stopped due to filter errors.
```
I have lexmark z25, maybe there are some special page parameters for it?:confused:

---

### Post by docplastic on 2007-10-29
> **fullburned said:**
> 
I have lexmark z25, maybe there are some special page parameters for it?:confused:

Start here:
<http://openprinting.org/show_printer.cgi?recnum=Lexmark-Z25>

And then try again.

---

### Post by fullburned on 2007-11-07
> **docplastic said:**
> Start here:
<http://openprinting.org/show_printer.cgi?recnum=Lexmark-Z25>

And then try again.
I've already installed drivers using this man earlier.
Any ideas? :(

---

### Post by kolesarm on 2008-09-11
Great utility, docplastic, I've used it extensively over the past two years - saved me tons of paper whenever I had to print articles.

One question: I have previously used it with a4 paper, but I have now moved over to the US and I am trying to configure it for letter paper. I understand that I need to change `a4' to `letter' in

> **docplastic said:**
> 
```
usr/bin/psbook $1 | /usr/bin/pstops -q -p a4 
"4:1L@0.7(21.0cm,14.95cm)+0L@0.7(21.0cm,0.6cm),3L@0.7(21.0cm,14.95cm)+2L@0.7(21.0cm,0.6cm)" 

```


But I am not sure how to calculate the margins - the pstops man page only gives example for a4 paper. Any ideas?

---

### Post by kolesarm on 2008-09-11
Ok, that was a stupid question to ask as 30mins of googling provided ample answers.

**Answer 1:**
```
4:1L@0.65(8.5in,5.5in)+0L@0.65(8.5in,0in),3L@0.65(8.5in,5.5in)+2L@0.65(8.5in,0in)
```

or something along those lines.
 
**Answer 2:**
```
/usr/bin/psbook $1 | /usr/bin/psnup -2 > "tmp-$1"
```

The psnup utility, like the pdfnup utility can work out the dimensions itself. The advantage is that you don't have to change the script whenever you go overseas.

I have to say, however, that the letter paper produces much poorer booklets, as its aspect ratio is a bit off. I guess I'll have to live with it...

---

### Post by doncristobal on 2008-10-31
I followed the instructions; all I get is: 

```
$ fp test.ps
Script fp started...

/usr/bin/pstops release 1 patchlevel 17
Copyright (C) Angus J. C. Duggan, 1991-1995. See file LICENSE for details.
Usage: /usr/bin/pstops [-q] [-b] [-wwidth] [-hheight] [-dlwidth] [-ppaper] <pagespecs> [infile [outfile]]
/usr/bin/fp: line 35: 4:1L@0.7(21.0cm,14.95cm)+0L@0.7(21.0cm,0.6cm),3L@0.7(21.0cm,14.95cm)+2L@0.7(21.0cm,0.6cm): command not found

Printing to the default printer: odd pages first...
/usr/bin/lpr: No file!?!
...after printing this batch, load the paper back in and hit 
<enter>

Now printing even pages...

/usr/bin/lpr: No file!?!
Done.

```

My printer (that prints fine normally) does not move.

There is a file /usr/bin/lpr

I have Ubuntu 8.04, all updates installed. 

I tried googling for the lpr error message, but I did not find out anything. 

Can anybody help? Thanks!

P.S. Something like this little script should be included in the standard ubuntu printing window - unfortunately I don't have any idea how to start this :-(

---

### Post by omelette on 2009-01-26
As a huge Fileprint fan on Windoze, I installed this script in the hope that it would concatenate multiple .ps files sent to it, outputting the resulting single file to my default 'printer', which is actually a CUPS->PDF thingy (installed via Synaptic)  - well, not only can it not concatenate files, it will not even work with the PDF 'printer'...

Disappointed :(

---

### Post by rajanvn on 2009-02-15
Today, I had to take a lot of pages in the booklet mode. I had three tools - only three tools.

The steps that I followed
1. Converted my documents into PS format
2. from commandline gave the command [FONT="Courier New"]psbook <infile> <outfile>[/FONT]
3. converted the the outfile.ps to outfile.pdf using ps2pdf
4. using Adobe's Acrobat Reader, first printed multiple pages on one sheet to PDF
5. Using the second PDF, printed oddsides first and then printed the evensides.

---

### Post by mdmcginn on 2009-10-08
The Point and Click version of kolesarm's code is:
```

tmpfile="$file~"
/usr/bin/psbook "$file" | /usr/bin/pstops -q -p letter "4:1L@0.65(8.5in,5.5in)+0L@0.65(8.5in,0in),3L@0.65(8.5in,5.5in)+2L@0.65(8.5in,0in)" > "$tmpfile";

```
and
```
/usr/bin/psbook "$file" | /usr/bin/psnup -2 > "$tmpfile";
```

I thought this script was supposed to work for PDF too, but Point and Click only works for me on PS files - otherwise I get wide-text printouts that begin with 
```
%%BeginProcSet: PStoPS 1 15
```

When I was typesetting books with FinePrint, I discovered that my top and bottom margins were smaller/more reasonable on letter size paper if my word processor was set for legal size paper and the original font was set at 14-18 points to allow for the reduction. I'll keep experimenting.

---

### Post by rocksockdoc on 2012-04-02
> **rocksockdoc said:**
> 

[LIST]
[*]Booklet Imposition (no cutting, folded in half lengthwise & centerline stapled)
[LIST]
[*]The   first and last pages are printed on one side of a standard "letter"   sheet of paper, with the second and penultimate page on the other side   of that same sheet of paper.
[*]This first/last second/penultimate relationship follows for every sheet of paper until it meets in the middle
[*]The printed stack of paper is then folded in half (lengthwise)
[*]And lengthwise staples are placed in the crease to 'bind' the booklet
[*]The result is a 8.5" tall by 5.5" wide stapled booklet
[/LIST]
 
[*]Book Imposition (cut in half widthwise & bound at the inside edge)
[LIST]
[*]The   first and middle page is printed on one side of a standard "letter"   sheet of paper, with the second page and middle-of-the-book+1 page   printed on the other side of the sheet of paper.
[*]The printed stack of paper is then cut in half (widthwise)
[*]And then the two stacks are bound together in a 'perfect binding'
[*]The result is a 8.5" tall by 5.5" wide bound paperback book
[/LIST]
[/LIST]
For the record, see this recent thread in the beginners section of the forum:

[LIST]
[*][COLOR=#980101]**[ubuntu]**[/COLOR] 			 			[Printing ebook PDFs: Is there only one fineprint like utility for Ubuntu users?]("http://ubuntuforums.org/showthread.php?t=1950441")
[/LIST]
One suggestion was to install the java-based Sourceforge JpdfTweak Windows/Linux freeware imposition printing utility with GUI:


[LIST]
[*][jPdf Tweak - Swiss Army Knife for PDF files]("http://jpdftweak.sourceforge.net/")
[/LIST]
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=215347&stc=1&d=1333422237[/IMG]


I haven't yet been able to get it to print book imposition or booklet imposition ... so if anyone already knows how, it would be nice to show the rest of us!

---

