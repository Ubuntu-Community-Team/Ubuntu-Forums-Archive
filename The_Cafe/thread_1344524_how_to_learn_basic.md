---
title: "how to learn basic"
date: 2009-12-03
forum: The Cafe
---

### Post by karimruan on 2009-12-03
I figured out that there are many dialects of basic on the net. Here is what I am looking for... Nothing gambas. I want it to have plenty of documentation online, and I need an editor with syntax highlighting and/or indentation.

Can anyone help me?

---

### Post by Frak on 2009-12-03
REALbasic - Couple hundred bucks, but Linux version is free (as far as I remember)
Visual Basic - Windows only, but Mono implementation still in the works.

There.

---

### Post by pelle.k on 2009-12-03
People are gonna think you're crazy! :)
That said, i used to do a lot of basic programming with PureBasic before i discovered linux (then i started using python). PureBasic is quite advanced, although it isn't object oriented. It's a compiled language, and the GUI parts are built using wxwindows, so it's pretty cross platform. It's available for Windows, Linux, OS X and even AmigaOS!

What was so good with purebasic though was the editor. Built in "function browser", call-tips, autocompletion, API documentation (mark keywords and press f1), smart indenting, super nice syntax highlighting, integrated debugger (nice and simple overview of the variables in the running app), you could create executables in one click, GUI editor for creating widgets, etc etc. It was very streamlined.
You could build .dll's and also import .dll's (if the source wasn't available), as well as use "real" binary .dll's created with C/C++. You could also directly interface with the operating system API (in my case it was the windows API), if funtionality wasn't provided by purebasic functions.
Very nice community, and lots of nice tutorials around.

If i didn't get hooked on python (and OO programming), i would probably still be messing with it. It was lots of fun, and i can highly recommend it if you're looking for a modern basic variant.

---

### Post by Exodist on 2009-12-03
> **Frak said:**
> 
Visual Basic - Windows only, but Mono implementation still in the works.

Mono version, sweet.. I been programming in BASIC since like 4th grade.

---

### Post by kalaharix on 2009-12-04
Hi,

KBasic?

I must say Gambas is just right FOR ME although I accept that the documentation is not very helpful for beginners (like me!).

I use it for commercial-related mySQL work and find it rock solid. I think the IDE is one of the best around. It has both syntax highlighting and indentation.

rgds

---

### Post by karimruan on 2009-12-04
what i don't like about gambas (right now) is that i prefer to do all the coding, not use a gui builder such as the one in VB. I made a web browser in vb, it was fun, but it shoots you right past the basics of the language itself. If I could find a basic tutorial on the BASIC dialect that gambas uses, i would be happy to use gambas! 

If anyone knows where to find this, great!

---

### Post by cammin on 2009-12-05
I'd be amazed if this acutally worked.
```

10 print "what?"
20 goto 40
30 print "Google"
32 goto 90
35 print "I forgot what I was going to put here."
40 print "took 2 seconds using"
44 goto 30
50 print "Who uses basic these days anyway?"
55 goto 120
90 for i= 1 to 100 step 5
95 print ""
100 next i
110 goto 50
120 k=1
122 print "_____"
124 if k<> 1 then goto 150
125 for j= 1 to 3
130 print "|    |"
135 next j
140 k=2
145 goto 122
150 end

```


Anyway.

[http://gambasdoc.org/help/lang](http://gambasdoc.org/help/lang)

---

### Post by openuniverse on 2009-12-05
.

---

### Post by karimruan on 2009-12-05
sdl basic is good, but there really isn't much going on with the community. Maybe i am being too picky!

---

### Post by LeifAndersen on 2009-12-05
> **cammin said:**
> I'd be amazed if this acutally worked.
```

10 print "what?"
20 goto 40
30 print "Google"
32 goto 90
35 print "I forgot what I was going to put here."
40 print "took 2 seconds using"
44 goto 30
50 print "Who uses basic these days anyway?"
55 goto 120
90 for i= 1 to 100 step 5
95 print ""
100 next i
110 goto 50
120 k=1
122 print "_____"
124 if k<> 1 then goto 150
125 for j= 1 to 3
130 print "|    |"
135 next j
140 k=2
145 goto 122
150 end

```
Anyway.

[http://gambasdoc.org/help/lang](http://gambasdoc.org/help/lang)


And that, is why I am happy that Java banned the use of goto.  That code is a mess.

BTW, why do you want to learn basic in the first place?  Python is much better, and faster, not to mention it integrates with C better too.

---

### Post by Frak on 2009-12-05
I would say learn something like HaXe. It compiles into just about everything and is truly cross platform. C++ for speed, Neko for portability, SWF for super portability.

---

### Post by karimruan on 2009-12-05
I have played with HaXE. I just want to learn a BASIC, don't know why. I have decided on freebasic, but get this error message when I try to compile my hello world program:

```


mat@mat-laptop:~$ fbc test.bas
/usr/share/freebasic/bin/linux/ld: cannot find -lXpm
mat@mat-laptop:~$ 


```


i cannot find the Xpm library anywhere (I THink that is what i need.) Anyone know how to fix this? Sorry about any wierd caps or lowercase, my keyboard has sticky keys! Time to take my lappy apart! lol

---

### Post by NoaHall on 2009-12-05
Try ```
sudo ldconfig
``` first. Maybe that'll fix it.

---

### Post by jfloydb on 2009-12-05
Can BASIC really produce a working application in the Linux world? I used to program in a structured BASIC that would accutually produce stand-alone Windows applications. Is there a (structured) BASIC that can produce Linux/Ubuntu applications?

---

### Post by openuniverse on 2009-12-05
.

---

### Post by pelle.k on 2009-12-06
> Is there a (structured) BASIC that can produce Linux/Ubuntu applications?
As i previously wrote in this thread, yes. PureBasic, is a structured basic (or as close as you can get). It does produce windows/macos/linux(wxgtk)/amigaos binaries.

---

### Post by karimruan on 2009-12-06
where can i get purebasic and an IDE/interpreter. i like gui, do not understand the greatness of coding from terminal.

---

### Post by pelle.k on 2009-12-07
> where can i get purebasic and an IDE/interpreter. i like gui, do not understand the greatness of coding from terminal.
Unfortunately, like realbasic, purebasic is a proprietary product. You get it all in one package. IDE, GUI builder, documentation, and compiler. You can download a demo version if you want to try it out though.
Homepage: [http://purebasic.com/](http://purebasic.com/)
User forums: [http://www.purebasic.fr/english/](http://www.purebasic.fr/english/)
Here's a good intro: [http://www.xs4all.nl/~bluez/purebasic/index.htm#top](http://www.xs4all.nl/~bluez/purebasic/index.htm#top)

---

### Post by mivo on 2009-12-07
I second the recommendation of PureBasic. It has been years since I purchased it, and it's really neat to quickly come up with working GUI apps. It's cross-platform, too, and less expensive than RealBasic. There's a good community and a large code archive.

There's a free book that doubles as an introduction to programming and as a textbook for PureBasic. It can be [downloaded here]("http://www.purebasic.fr/english/viewtopic.php?t=37059").

---

### Post by karimruan on 2009-12-07
i will definitely check be purchasing purebasic, but still also want a free one (so I can write any size programs) until then. unfortunately, right now i make enough to pay bills and buy my kid what he needs/wants. Since he comes before my hobbies, it might be a while till i can buy it. Can anyone suggest a free, well popular (By popular, i mean much source code on the net, lots of tutorials, etc) BASIC dialect? I have already checked out sdlbasic, and i love it, but without tutorials (They have documentation, but it just lists all the commands and what they do, I have used it as much as possible, but still need to see the code in action!) I can only do so much. qbasic is for windows, and I can't find very many get straight to the point tuts for kbasic, which seems promising.

If any of you use a basic on ubuntu, let me know which one, where i can get it, how well documented it is on the net (tuts, source code, etc) and I will give it a try.

I love python but basic seems really fun!

---

### Post by kalaharix on 2009-12-07
hi,

I had a good look at Purebasic and liked what I saw - up to a point. There seems to be a problem with cross-platform applications in general: the development favours the dominant OS. I don't say that is wrong, it just does not help Linux developers. Bugs are treated much more casually in Linux Purebasic than in Windows Purebasic. If I were clever enough to write Purebasic I would do exactly the same.

And it's not object oriented. 

And if I see one more objection to BASIC on the basis that it uses GOTO statements I will scream - it is just so ignorant. I have programmed various types of BASIC but it must be 20 years since I used a GOTO. 

Gambas is Linux only. This means that bugs receive an immediate response from the author.

As with most Linux software, I would not use Gambas to write software for widespread distribution. This is a criticism of Linux rather than Gambas and results from the standard libraries which programs like Gambas rely on. For example QT4 is quite capable of causing problems with software written using QT3. It is not as backwards compatible as it should be.

Having said that, I am using Gambas on two point-of-sale terminals and a separate goods-receiving machine. One of the tills acts as a mySQL server. Works all-day every-day. Gambas is rock-solid.

---

### Post by openuniverse on 2009-12-07
.

---

### Post by mivo on 2009-12-07
Yabasic has been dead for two years: [http://www.yabasic.de/](http://www.yabasic.de/)

---

### Post by openuniverse on 2009-12-07
.

---

### Post by rCXer on 2009-12-07
> **karimruan said:**
> I have played with HaXE. I just want to learn a BASIC, don't know why. I have decided on freebasic, but get this error message when I try to compile my hello world program:

```


mat@mat-laptop:~$ fbc test.bas
/usr/share/freebasic/bin/linux/ld: cannot find -lXpm
mat@mat-laptop:~$ 


```


i cannot find the Xpm library anywhere (I THink that is what i need.) Anyone know how to fix this? Sorry about any wierd caps or lowercase, my keyboard has sticky keys! Time to take my lappy apart! lol

Installing freebasic in Ubuntu is a little tricker than people relize.  Too bad it's not in the repositories yet. To install it download and unpack the regular linux version (not standalone) to /home/username/FreeBASIC

Then...
```
	
cd ~/FreeBASIC/
sudo ./install.sh -i

#Download and install "getlibs-all.deb".
wget http://frozenfox.freehostia.com/cappy/getlibs-all.deb
sudo dpkg -i getlibs-all.deb	

sudo getlibs -p libxpm-dev
sudo getlibs -p libxrandr-dev
sudo getlibs -p libxrender-dev
sudo getlibs -p libncurses5-dev
sudo apt-get install libncurses5
sudo apt-get install libncurses5-dev

```

There's a [thread](http://www.freebasic.net/forum/viewtopic.php?t=13487) about this at the freebasic forums.

---

### Post by squilookle on 2009-12-07
```
10 print "i'm not crazy"
20 goto 10
```

---

### Post by bonfire89 on 2009-12-07
I did QuickBasic back in early highschool...


I'm curious as to why anyone would bother with it in 2009?


also

> **squilookle said:**
> ```
10 print "i'm not crazy"
20 goto 10
```

my teacher would fail any assignment that contained a goto... even if it was the end of year project that was worth 30%

---

### Post by Simian Man on 2009-12-07
I can't think of a single reason to use Basic instead of Python.

---

### Post by karimruan on 2009-12-07
I can, pure fun! I am not trying to do any serious programming, i want to learn it for the same reason I play roguelikes, and for the same reason I use dosbox to play kings quest.

Simple, really :)

---

### Post by bonfire89 on 2009-12-07
> **karimruan said:**
> I can, pure fun! I am not trying to do any serious programming, i want to learn it for the same reason I play roguelikes, and for the same reason I use dosbox to play kings quest.

Simple, really :)

fair enough. heh

---

### Post by kalaharix on 2009-12-08
> I can't think of a single reason to use Basic instead of Python.

Python is a fine language and much better than Gambas when you need to be close to the OS.

It does not have an integrated GUI IDE. Some see this as an advantage: i don't. Glade sucks.

Database work is much, much, much easier on Gambas.

rgds

---

### Post by mivo on 2009-12-08
> **Simian Man said:**
> I can't think of a single reason to use Basic instead of Python.

I can't think of a single reason to use Italian instead of English, either, or why I need a third language, yet I enjoy learning and using it.

Python is a good interpreted scripting language (though I prefer Ruby), but I'll still use PureBasic if I need a fast and small GUI application. PureBasic generates tiny and incredibly fast binaries/executables that take very little time to cook up. I, too, grew up with Basic (Locomotive Basic, ST Basic, GFA Basic, VB (okay, I was already grown up when I used VB ;))), and I like the language family. It's much like my mother language.

---

### Post by karimruan on 2009-12-08
well said!

---

### Post by Frak on 2009-12-08
> **mivo said:**
> Python is a good interpreted scripting language (though I prefer Ruby)
Same. It just flows so nicely.

do this
when this
unless this
end.

---

### Post by kalaharix on 2009-12-10
How about a little challenge to Python supporters? The following Gambas2 code:

1	Deletes a file test.sqlite in the users home directory (if it exists).
2	Creates an SQLite database test.sqlite and defines a table sampleTable with two integer fields, one a sequence (yes, I know SQLite does that internally anyway!) and the other a random number.
3	Fills the table with 10000 records with rollback.
4	Displays the results in a gridview.

I suspect that Python will not produce an equivalent with anything like the elegance (language, not my code!) nor readability of the Gambas code. I will also be surprised if it is as blindingly fast.

On Gambas you need nothing more than a gridview (gridview1) on an otherwise empty form (You could also instantiate the gridview from code). The only bit that may need explanation is the GridView1_Data event. This is called to fill an empty gridview cell as it is exposed (by scrolling). It saves having to load all 10000 records into the gridview with the time penalty that would imply.

A hint for the two flat-earthers in this thread (in case they can't work it out for themselves): there are no GOTO statements!

> 
' Gambas class file
PRIVATE $hConn AS NEW Connection
PRIVATE $res AS Result
'-------------------------------------------------
PUBLIC SUB Form_Open()
  DIM iCount AS Integer
  DIM hTable AS Table
  DIM rTest AS result
  DIM sql AS String
  
  'define the gridview layout
  GridView1.header = GridView.Horizontal
  GridView1.grid = TRUE
  GridView1.Rows.count = 0
  GridView1.Columns.count = 2
  GridView1.Columns[0].text = "ID"
  GridView1.Columns[1].text = "Value"
  GridView1.Columns[0].width = 55
  GridView1.Columns[1].width = 55
  
  
  WITH $hConn
[INDENT].Type = "sqlite"
.host = User.home   
.name = ""[/INDENT]    
  END WITH 
  
  'delete an existing test.sqlite  
  IF Exist(User.home & "/test.sqlite") THEN 
[INDENT]KILL User.home & "/test.sqlite"[/INDENT] 
  ENDIF 
  
  'create test.sqlite
  $hConn.Open
[INDENT]    $hConn.Databases.Add("test.sqlite")[/INDENT]
  $hconn.Close
  
  'define the table sampleTable
  $hconn.name = "test.sqlite"
  $hConn.Open
[INDENT]    hTable = $hConn.Tables.Add("sampleTable")
    hTable.Fields.Add("s_seq", db.Integer)
    hTable.Fields.Add("s_rndm", db.Integer)
    hTable.PrimaryKey = ["s_seq"]
    hTable.Update[/INDENT]
    
  'fill the table with generated data
  $hconn.Begin
[INDENT]    rTest = $hConn.Create("sampleTable")
    FOR iCount = 1 TO 10000
[INDENT]      rTest!s_seq = iCount
      rTest!s_rndm = Int(Rnd(0, 100))
      rTest.Update[/INDENT]
    NEXT[/INDENT]
  $hConn.Commit
  
  'read the database
  sql = "select s_seq as ID, s_rndm as Value from sampleTable"
  $res = $hconn.Exec(sql)
  
  CATCH 
    $hConn.Rollback
    Message.Error(DConv(Error.Text))
    
END
'-------------------------------------------------
PUBLIC SUB Form_Activate()
  'change the rowcount of the gridview from 0 to the number of records. 
  'This triggers the data handling event

  GridView1.Rows.Count = $res.Count  
END
'-------------------------------------------------
PUBLIC SUB GridView1_Data(Row AS Integer, Column AS Integer)

  $res.moveTo(row)
  GridView1.Data.text = Str($res[GridView1.Columns[column].text])
END
'-------------------------------------------------
PUBLIC SUB Form_Close()

  $hconn.Close
END
'-------------------------------------------------



---

### Post by kalaharix on 2009-12-13
Hi

What? No Takers? I thought all these Python people would be falling over themselves to show how superior Python was in duplicating the Gambas code in this thread. It'll only take half-an-hour.

C'mon, I am genuinely interested in how Python would do this. I haven't set any traps (If I wanted to do that, I would have made my sample more gui intensive)

rgds

---

### Post by drawkcab on 2009-12-13
Lock yourself in a room for a month with an apple IIc.

That's how I learned basic.

---

