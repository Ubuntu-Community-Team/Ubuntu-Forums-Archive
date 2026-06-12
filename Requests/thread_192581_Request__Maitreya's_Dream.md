---
title: "Request:  Maitreya's Dream"
date: 2006-06-08
forum: Requests
---

### Post by PaganHippie on 2006-06-08
OK, so the Dapper requests in Launchpad don't seem to be open yet....

I'd like to see some astrology software more sophisticated than 'astrolog' available for Ubuntu, and Maitreya's Dream has a good reputation.

---

### Post by Ceyx on 2008-04-06
Maitreya 5.0 is quite good in my opinion....it is available at 
[http://saravali.de/maitreya/](http://saravali.de/maitreya/)

There is a Windows version compiled, or you can download source code for Ubuntu. 

It has both Western and Vedic capabilities, and is customizable.  Try it!

Have fun!

---

### Post by marseille on 2008-06-13
hello... 

i had success w/ maitreya 4.1 in feisty but now that i have hardy heron, i just keep getting an errno2 code when i try 'make' on maitreya 5 --  i think something about a GUI issue.  then i saw something about this on a *china* ubuntu site but i couldnt understand.

anyway, i tried 2 reinstall maitreya 4.1 but i get that same error code.  

any advice?

thx...

ERRO LOG (MAITREYA 5)
$ ./configure

  Configuration successful!

General options
   Directory :   /usr/local/maitreya
   Debugging :   false

wxWidgets options
  wx version :   2.8.7
   wx-config :   /usr/bin/wx-config   

You can type 'make' now


$ make


How to Start
------------
You can start the program with the following commands
cd src/gui
./maitreya


$ cd src/gui
$ ./maitreya
**Fatal Error: stat failed, errno is 2**

---

### Post by Ceyx on 2008-06-13
I have no idea what the error 2 is. I go to the usr/local/bin directory and click on the shortcut to Maiteya which should be there.

I am running Maitreya 5.0 on Hardy. It was hit and miss (mostly miss) for a while, but I found that if I compile WXWidgets myself with "./configure-- enable unicode" then everything ran smoothly after that.  I believe the package manager does not enable unicode for WxWidgets.

See: [http://wiki.wxpython.org/InstallingOnUbuntuOrDebian](http://wiki.wxpython.org/InstallingOnUbuntuOrDebian)

Download it to a folder you can use exclusively or create one.
Unpack wxwidgets and read the .dsc file.  Get everything listed in the dependencies, then compile WxWidgets with the "./configure -- enable unicode".  Don't forget to use the LDconfig command

Then compile Maitreya - should work. 

This probably is not very intellectual or economical in terms of file space, but it works.

Let me know how it goes......

---

### Post by marseille on 2008-06-17
[SIZE="4"]first off: many thx :KS[/SIZE]

when i initially attempted installation, i did enable unicode according 2 [this page]("http://www.saravali.de/maitreya/charset.html"), then did make ~ like so:

**$./configure --enable-unicode**
**$make**

my issue stemmed from failing 2 understand -- since 4.1 let me get away from dealing w/ unicode (my bad) --  i incorrectly installed maitreya truetype font.  i mistakenly put it in .font [local font] instead of **usr/share/fonts/truetype**

so i had 2 copy my newly downloaded 'MaitreyaSymbols.ttf' (located in ../src/fonts) 2 '/usr/share/fonts.' then [flush font cache]("https://wiki.ubuntu.com/Fonts") so it would take.
[B]
$sudo cp MaitreyaSymbols.ttf /usr/share/fonts/truetype
$sudo fc-cache -f -v[/B]

after i did that i could do:
**$sudo make install**

then actually run it according 2 their INSTALL file;)
> You can start the program with the following commands
cd src/gui
./maitreya


[B]$ cd src/gui
$ ./maitreya[/B]
Creating config directory /home/myAccount/.maitreya5 for the first time ...
Creating view directory /home/myAccount/.maitreya5/view for the first time ...
Copy file /usr/local/maitreya/locations.dat to /home/myAccount/.maitreya5/locations.dat
Copy file /usr/local/maitreya/view/VedicComprehensive.view to /home/myAccount/.maitreya5/view/VedicComprehensive.view
Copy file /usr/local/maitreya/view/WesternSimple.view to /home/myAccount/.maitreya5/view/WesternSimple.view
Copy file /usr/local/maitreya/view/VedicSimple.view to /home/myAccount/.maitreya5/view/VedicSimple.view
Copy file /usr/local/maitreya/view/VedicBhava.view to /home/myAccount/.maitreya5/view/VedicBhava.view
Copy file /usr/local/maitreya/view/Midpoint.view to /home/myAccount/.maitreya5/view/Midpoint.view

[IMG]http://ubuntuforums.org/picture.php?albumid=268&pictureid=874[/IMG]

---

