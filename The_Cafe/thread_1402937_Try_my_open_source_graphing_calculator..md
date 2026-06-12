---
title: "Try my open source graphing calculator."
date: 2010-02-09
forum: The Cafe
---

### Post by RussianVodka on 2010-02-09
Hello everyone. I've been developing a graphing calculator on and off (mostly off) since last summer, and it's finally become usable.

I was hoping people could use it and give me feedback (especially about how it runs on Linux, since I haven't been able to test that yet.)

So far it seems to work fine on windows, and the only problem with running it on OSX is that the dimensions of the GUI seem disproportionate up.

Here are the links:
[Info Page]("http://epoblaguev.com/?page=Projects/graphCalc.php&subNav=Projects/projectsNav.php")
[Download Page]("http://code.google.com/p/graphingcalculator/downloads/list")

Enjoy.

**Update:**
New release. Lots of changes. I need to start keeping a change log.

New Features:
[LIST]
[*]Values of expressions now stored, insted of evaluated every time they're needed.
[*]Calculator now tells you which angle units (radians or degrees) the expression was evaluated in.
[*]Can save and load the state of the calculator tab. (Doesn't yet work for the graphing tab.)
[*]Can use both base 10 logs [log(var)] and natural logs [ln(var)].
[*]Can add and remove equations from the graph.
[*]Can change color of equation being graphed. (Color assigned at random, I'll add a color picker later.)
[/LIST]

---

### Post by juancarlospaco on 2010-02-09
Fill a *"Need-Packaging Bug"* and maybe you can get it included on the comming up Ubuntu releases.

---

### Post by sanderj on 2010-02-09
Oh, I see: it's a .jar, so it's a java app, right? I have no Java installed, so I can't test it.

About packaging: I believe you first have to proof the packaging & maintenance via PPA.

---

### Post by Firestem4 on 2010-02-09
I'd love to helpb ut I don't know how to use a graphing calculator =*(, lol. However i will say both the .jar and .exe run on my win7-64bit desktop.

---

### Post by dragos240 on 2010-02-09
Your website is a white page with nothing on it.

---

### Post by RussianVodka on 2010-02-09
> **dragos240 said:**
> Your website is a white page with nothing on it.

My website or the google code website?

---

### Post by RussianVodka on 2010-02-09
> **juancarlospaco said:**
> Fill a *"Need-Packaging Bug"* and maybe you can get it included on the comming up Ubuntu releases.

Where would I do that? Would it be in the multiverse repository, or would I have to create my own repository with launchpad?

Also would it be frowned upon that the program is written in java?

> **sanderj said:**
> Oh, I see: it's a .jar, so it's a java app, right? I have no Java installed, so I can't test it.

About packaging: I believe you first have to proof the packaging & maintenance via PPA.

Yep, it's java. I was afraid Ubuntu people might not have java installed. When I used Ubuntu exclusively, i didn't either... Don't remember why though.

---

### Post by Warpnow on 2010-02-10
Nice program. I will likely use it some.

Some features I'd like to see:

Calculation of derivatives.
Ability to place points on the graph and it gives you the formula.
Ability to "solve for variable", as I couldn't find such.

---

### Post by chessnerd on 2010-02-10
Works well for me. 

One thing you could add that might be nice is the ability to give "2x" instead of "2*x" when you input the equation. From just quickly glancing at the code I didn't see how you were reading the information from the JTextField but you could feed the String "2x", "50x", "1000x", etc. to a method like this:

```
private int getNumForMulti(String s) {
   int num;
   if (s.charAt(s.length-1) == 'x') {
      boolean restAreNum = true;
      for (int i = 0; i < s.length-1; i++) {
         if (!Character.isDigit(s.charAt(i))
            restAreNum = false;
      }
      if (restAreNum)
         num = Integer.parseInt(s.substring(0, s.length-2));
   }
   return num;
}
```
You could then use the resulting number for multiplication.

Just a thought. Keep us updated on the progress. It would be nice to have a solid, open source, multi-platform graphing calculator alternative.

---

### Post by MaxIBoy on 2010-02-10
> **RussianVodka said:**
> My website or the google code website?
Your website. See screenshot.

Anyway, I have been looking for something like this for a long time. Although I have in fact gotten nearly all desired functionality out of GNUplot, I hope that this can provide something a little bit better.

---

### Post by sandyd on 2010-02-10
ill make you a deal buddy. if you provide the source code (i dont know if you placed it in google code or not since im on my phone), and the complete compilation intructions, ill create a source deb for ya (ill start attempting tomorow) and attempt to upload to a ppa. p.s. could someone try compiling this w/ openjdk? if it works, i wont have to make sun-java6-jre a complete dependency, just to be fair to openjdk users.

---

### Post by chessnerd on 2010-02-10
> **carlee said:**
> ill make you a deal buddy. if you provide the source code (i dont know if you placed it in google code or not since im on my phone), and the complete compilation intructions, ill create a source deb for ya (ill start attempting tomorow) and attempt to upload to a ppa. p.s. could someone try compiling this w/ openjdk? if it works, i wont have to make sun-java6-jre a complete dependency, just to be fair to openjdk users.

I found the source for it here: [http://graphingcalculator.googlecode.com/svn/](http://graphingcalculator.googlecode.com/svn/)

I ran it using OpenJDK and it worked well, but I didn't try compiling it.

---

### Post by doorknob60 on 2010-02-10
Looks prety good. I probably won't ever use it since I love and know how to use my TI-84 well, but might come in handy someday. Should work on (almost) any OS too since it's in Java.

---

### Post by RussianVodka on 2010-02-10
> **chessnerd said:**
> Works well for me. 

One thing you could add that might be nice is the ability to give "2x" instead of "2*x" when you input the equation. From just quickly glancing at the code I didn't see how you were reading the information from the JTextField but you could feed the String "2x", "50x", "1000x", etc. to a method like this:

```
private int getNumForMulti(String s) {
   int num;
   if (s.charAt(s.length-1) == 'x') {
      boolean restAreNum = true;
      for (int i = 0; i < s.length-1; i++) {
         if (!Character.isDigit(s.charAt(i))
            restAreNum = false;
      }
      if (restAreNum)
         num = Integer.parseInt(s.substring(0, s.length-2));
   }
   return num;
}
```
You could then use the resulting number for multiplication.

Just a thought. Keep us updated on the progress. It would be nice to have a solid, open source, multi-platform graphing calculator alternative.

Actually, most of the code inside the MathEvaluator class isn't mine, I only added the ability to choose between radians and degrees. Last summer I wrote the evaluator code to recursively solve expressions, but it was very buggy, and poorly made (this was before I took a course on compiler design). That is the only code that isn't written by me.

I came across [this]("http://lts.online.fr/dev/java/math.evaluator/") one day, and decided to use it. I dunno if it's open source or not, since it only says "freeware". I emailed the guy, but he never got back to me.

Since he's not responding, I'm thinking of either writing my own evaluator, or using one of the Commons Math libraries from the Apache projects, although they may be overkill for now.

Anyways, I'm pretty sure that I added code that converts "2x, 1(2) and(1)(2)" into "2*x, 1*(2) and (1)*(2)". But since it doesn't work for you, i'll look into it.

> **carlee said:**
> ill make you a deal buddy. if you provide the source code (i dont know if you placed it in google code or not since im on my phone), and the complete compilation intructions, ill create a source deb for ya (ill start attempting tomorow) and attempt to upload to a ppa. p.s. could someone try compiling this w/ openjdk? if it works, i wont have to make sun-java6-jre a complete dependency, just to be fair to openjdk users.

Here it is: [http://code.google.com/p/graphingcalculator/source/browse/](http://code.google.com/p/graphingcalculator/source/browse/)

The Netbeans project is contained inside the "Calculator" directory. Ignore the other directories that are there. This was my first time using a remote CVS repository over which i had no control, so uploaded the code incorrectly the first time and wasn't able delete it later.

---

### Post by RussianVodka on 2010-02-10
Ok, never mind. There was in fact a bug with implied multiplication not being evaluated correctly when graphing. It is now fixed, and i'll upload the new executables after i get some sleep.

---

### Post by RussianVodka on 2010-02-10
Ok, bug fixed and files uploaded.

Here is the download link:
[Link.]("http://code.google.com/p/graphingcalculator/downloads/list")

---

### Post by LeifAndersen on 2010-02-10
Interesting toy.  However, I do enjoy Octave more.

---

### Post by sandyd on 2010-02-10
> **chessnerd said:**
> I found the source for it here: [http://graphingcalculator.googlecode.com/svn/](http://graphingcalculator.googlecode.com/svn/)

I ran it using OpenJDK and it worked well, but I didn't try compiling it.

if it runs in openjdk, thats fine. i was just unsure of weather or not I needed a different (compiled by openjdk) binary to make it run

---

### Post by sandyd on 2010-02-10
im having some issues.
I created the makefile using mmake, and when I compiled it, it turned up.
```

src/calculator/AddVariableWindow.java:3: package exceptions does not exist       
import exceptions.InvalidVariableNameException;                                  
                 ^                                                               
src/calculator/AddVariableWindow.java:4: package expressions does not exist      
import expressions.Variable;                                                     
                  ^                                                              
src/calculator/AddVariableWindow.java:5: package expressions does not exist      
import expressions.VariableList;                                                 
                  ^                                                              
src/calculator/AddVariableWindow.java:69: cannot find symbol                     
symbol  : class Variable                                                         
location: class calculator.AddVariableWindow                                     
                Variable var = new Variable(txtVariableName.getText(), Double.valueOf(txtVariableValue.getText()));                                                                                   
                ^                                                                                  
src/calculator/AddVariableWindow.java:69: cannot find symbol                                       
symbol  : class Variable                                                                           
location: class calculator.AddVariableWindow                                                       
                Variable var = new Variable(txtVariableName.getText(), Double.valueOf(txtVariableValue.getText()));                                                                                   
                                   ^                                                               
src/calculator/AddVariableWindow.java:71: cannot find symbol                                       
symbol  : variable VariableList                                                                    
location: class calculator.AddVariableWindow                                                       
                Iterator itr = VariableList.getVariableList().iterator();                          
                               ^                                                                   
src/calculator/AddVariableWindow.java:74: cannot find symbol                                       
symbol  : class Variable                                                                           
location: class calculator.AddVariableWindow                                                       
                    Variable curVar = (Variable) itr.next();                                       
                    ^                                                                              
src/calculator/AddVariableWindow.java:74: cannot find symbol                                       
symbol  : class Variable                                                                           
location: class calculator.AddVariableWindow                                                       
                    Variable curVar = (Variable) itr.next();
                                       ^
src/calculator/AddVariableWindow.java:80: cannot find symbol
symbol  : variable VariableList
location: class calculator.AddVariableWindow
                VariableList.addVariable(var);
                ^
src/calculator/AddVariableWindow.java:81: cannot find symbol
symbol  : variable VariableTablePane
location: class calculator.AddVariableWindow
                VariableTablePane.refreshTable();
                ^
src/calculator/AddVariableWindow.java:87: cannot find symbol
symbol  : class InvalidVariableNameException
location: class calculator.AddVariableWindow
        } catch (InvalidVariableNameException ex) {
                 ^
11 errors
make: *** [src/calculator/AddVariableWindow.class] Error 1

```using javac to compile it.

oh wait. hehehe.
havent installed sun-java6-jdk...

---

### Post by chessnerd on 2010-02-10
> **RussianVodka said:**
> Ok, bug fixed and files uploaded.

Here is the download link:
[Link.]("http://code.google.com/p/graphingcalculator/downloads/list")

Yep, it's working now. And while I didn't need to think up code for the functionality, I think it was a good exercise. ;)

---

### Post by dragos240 on 2010-02-10
Works nicely.

---

### Post by RussianVodka on 2010-02-11
New release. Lots of changes. I need to start keeping a change log.

New Features:
[LIST]
[*]Values of expressions now stored, insted of evaluated every time they're needed.
[*]Calculator now tells you which angle units (radians or degrees) the expression was evaluated in.
[*]Can save and load the state of the calculator tab. (Doesn't yet work for the graphing tab.)
[*]Can use both base 10 logs [log(var)] and natural logs [ln(var)].
[*]Can add and remove equations from the graph.
[*]Can change color of equation being graphed. (Color assigned at random, I'll add a color picker later.)
[/LIST]

I think there are more, but most of them are internal, and I don't remember them.

Here is the download link:
[Download]("http://code.google.com/p/graphingcalculator/downloads/list")

---

