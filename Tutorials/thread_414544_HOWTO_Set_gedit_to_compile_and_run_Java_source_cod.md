---
title: "HOWTO: Set gedit to compile and run Java source code"
date: 2007-04-19
forum: Tutorials
---

### Post by WiseElben on 2007-04-19
**[SIZE="4"]Introduction[/SIZE]**

I use gedit with the terminal panel plugin when I'm programming small Java programs. This becomes a hassle sometimes, so I created a simple gedit "Tool" that would compile and run Java source files. Some people would prefer using just the plain terminal or a complicated IDE, but this is especially useful for students who just needs a basic yet easy-to-use interface to learn Java on.

**[SIZE="4"]Instructions[/SIZE]**

First, open gedit and go to Tools=>External Tools. Create a new tool and label it something like "Java Compile." Set an accelerator if you want to.

Then inside the Command, insert this:

```

#Compiles the current open Java source file.
echo "Compiling: " $GEDIT_CURRENT_DOCUMENT_PATH
echo '--------------------'
javac $GEDIT_CURRENT_DOCUMENT_PATH

```

The second part (the tool to run the class) is a bit more difficult because gedit runs the script using /bin/sh, which doesn't support the necessary regex command. Because of this, we have to make a separate script file.

Since gedit is already open, make a new file and copy in:

```

#!/bin/bash

#To be used with gedit Tools to run a compiled Java source file.
[[ $2 =~ "\w+" ]]
cd $1
java $BASH_REMATCH

```

Save as **java_run** under a **.gedit** folder in your home folder. You might need to create the **.gedit** folder.

Now, create another Tool. Call this one "Java Run" and copy the following under Command:
```

#Runs a compiled Java source file.
echo "Running: " $GEDIT_CURRENT_DOCUMENT_PATH
echo '--------------------'
bash ~/.gedit/java_run $GEDIT_CURRENT_DOCUMENT_DIR $GEDIT_CURRENT_DOCUMENT_NAME
```

You're done! You might want to create a sample program to test this.

**[SIZE="4"]Final Thoughts[/SIZE]**

This feature in gedit is a bit buggy, so don't be surprised if your custom Tools suddenly vanish or jump around; this happened to me a couple of times when I was figuring this out.

---

### Post by Rhenthalin on 2007-05-07
This little device sounds absolutley wonderful for my purposes however, I do not seem to have the tool=>external tools feature. Is this a Feisty Fawn feature or is my gedit just very noobly.

---

### Post by zobdos on 2008-01-23
actually, there is a much easier way to run the compiled classfile...

code:

java ${GEDIT_CURRENT_DOCUMENT_NAME%\.*}

thats it. lol.

---

### Post by thomas_vergote on 2008-01-28
Hi, 

I'm a beginning java programmer (in two days I have my exam) and I use eclipse by default as editor and compiler. 
However I want to compile and run my java programs also in gedit, because I love the simplicity of gedit and for a fast check, gedit is excellent...
So I found this thread and I am able to compile without any problem, however, running the program just doesn't seem to work out!
This is what I get:
 > 
Running:  /home/thomas/workspace/examenvoorbereiding/src/TestSorteren.java
--------------------
Usage: java [-options] class [args...]
           (to execute a class)
   or  java [-options] -jar jarfile [args...]
           (to execute a jar file)

where options include:
    -client	  to select the "client" VM
    -server	  to select the "server" VM
    -hotspot	  is a synonym for the "client" VM  [deprecated]
                  The default VM is client.

    -cp <class search path of directories and zip/jar files>
    -classpath <class search path of directories and zip/jar files>
                  A : separated list of directories, JAR archives,
                  and ZIP archives to search for class files.
    -D<name>=<value>
                  set a system property
    -verbose[:class|gc|jni]
                  enable verbose output
    -version      print product version and exit
    -version:<value>
                  require the specified version to run
    -showversion  print product version and continue
    -jre-restrict-search | -jre-no-restrict-search
                  include/exclude user private JREs in the version search
    -? -help      print this help message
    -X            print help on non-standard options
    -ea[:<packagename>...|:<classname>]
    -enableassertions[:<packagename>...|:<classname>]
                  enable assertions
    -da[:<packagename>...|:<classname>]
    -disableassertions[:<packagename>...|:<classname>]
                  disable assertions
    -esa | -enablesystemassertions
                  enable system assertions
    -dsa | -disablesystemassertions
                  disable system assertions
Closed: 256

I hope someone can help me get this fixed, I must be doing something wrong and I suppose its something small...

Thanks!

---

### Post by phunkizm on 2008-01-30
thomas, 

I had the same problem, but then I tried zobdos' simpler version and it works great.  Give it a try.

---

### Post by DaymItzJack on 2008-01-31
How can I get this to save the current file before trying to compile? thanks.

---

### Post by danielarseno on 2008-04-06
The following script will compile and, if compilation is successful, run the class.

> 
#!/bin/sh
cd $GEDIT_CURRENT_DOCUMENT_DIR
if javac $GEDIT_CURRENT_DOCUMENT_NAME;
then
java ${GEDIT_CURRENT_DOCUMENT_NAME%\.java}
else
echo "Failed to compile"
fi


---

### Post by officialhopsof on 2008-05-10
Here is a script for compiling and running a java program. I ran into the problem of having to set the class path, my script does this for you. Also, you have to have python installed for this to work.

```
#!/bin/sh

cd $GEDIT_CURRENT_DOCUMENT_DIR

python -c "
import os

arg = '$GEDIT_CURRENT_DOCUMENT_DIR/$GEDIT_CURRENT_DOCUMENT_NAME'
package = ''
data = open(arg, 'r').readlines()

for i in range(len(data)):
	temp = data[i].strip()
	if temp[0:7] == 'package':
		package = temp[8:len(temp)-1]

if package != '':
	for i in range(package.count('.') + 2):
		arg = arg[0:arg.rfind('/')]
	
	os.system('javac -cp ' + arg + ' ' + '$GEDIT_CURRENT_DOCUMENT_DIR/$GEDIT_CURRENT_DOCUMENT_NAME')
	os.system('java -classpath ' + arg + ' ' + package + '.' + '${GEDIT_CURRENT_DOCUMENT_NAME%.java}')
else:
	os.system('javac $GEDIT_CURRENT_DOCUMENT_NAME')
	os.system('java ${GEDIT_CURRENT_DOCUMENT_NAME%.java}')
"

```

it works for my purposes. There is just one case that i can see that this wont work on, if you have something like this. my script will see the other package statement there and think it is the one we need. 
```

/*
this is the old package
package something.another.and.another;
*/
package something.else.in.another.place;
```

that being the case, the following would work fine


```
//this is the old package
//package something.another.and.another;

package something.else.in.another.place;
```

because of the leading "//"

enjoy

---

### Post by D.Sync on 2008-07-25
I had several issues here:

1) The following error occured when I import java.util.* to called the Scanner.

> Exception in thread "main" java.util.NoSuchElementException
	at java.util.Scanner.throwFor(Scanner.java:855)
	at java.util.Scanner.next(Scanner.java:1478)
	at java.util.Scanner.nextInt(Scanner.java:2108)
	at java.util.Scanner.nextInt(Scanner.java:2067)
	at Q8.main(Q8.java:32)

Exited: 256

2) If the .java file is located on another drive, eg: /media/WINXP/Documents and Settings/UserName/My Documents/My Java, the following error will occured. But still, it will still run the .class file.

> cd: 10: can't cd to /media/WINXP/Documents

---

### Post by KdotJ on 2010-04-12
This is fantastic! This will save me some time!
thanks

---

### Post by matshofman on 2010-05-20
I wanted to do this but I can't find see the Tools menu :S Does anyone know how to solve this?

**[Solved]**
I solved it, i needed to enable the External Tools plugin. Edit > Preferences > Plugins > External Tools

I'm using this code by the way to compile and run my Java file
```
#!/bin/sh
#Runs a compiled Java source file.
echo "Compile And Run:" $GEDIT_CURRENT_DOCUMENT_PATH
echo '--------------------'
javac $GEDIT_CURRENT_DOCUMENT_PATH
java ${GEDIT_CURRENT_DOCUMENT_NAME%\.*}

```

---

### Post by genoskill on 2010-08-29
> **matshofman said:**
> I wanted to do this but I can't find see the Tools menu :S Does anyone know how to solve this?

**[Solved]**
I solved it, i needed to enable the External Tools plugin. Edit > Preferences > Plugins > External Tools

I'm using this code by the way to compile and run my Java file
```
#!/bin/sh
#Runs a compiled Java source file.
echo "Compile And Run:" $GEDIT_CURRENT_DOCUMENT_PATH
echo '--------------------'
javac $GEDIT_CURRENT_DOCUMENT_PATH
java ${GEDIT_CURRENT_DOCUMENT_NAME%\.*}

```

Thank you very much matshofman, that code worked for me.

---

### Post by SvenVP on 2010-10-28
ive used a xterm to open java aplication... i cant figure it out for gnome-terminal??? if you can it will be helpfull... thanks

> #!/bin/sh
#Compiles the current open Java source file.
echo "Compiling Java Programm..." $GEDIT_CURRENT_DOCUMENT_PATH
echo '--------------------------'
javac $GEDIT_CURRENT_DOCUMENT_PATH

echo "Running Java Program... " $GEDIT_CURRENT_DOCUMENT_NAME;
echo '-----------------------';

xterm -hold -e java ${GEDIT_CURRENT_DOCUMENT_NAME%\.*}

---

### Post by bhaveshnande on 2011-06-22
It works perfect!
But how can I compile Java ME(Micro Edition) files in gedit?

---

### Post by Skorzen on 2011-10-05
Guys,

And what if I need to pass arguments in my Java classes? This scripts just compile a given source code, right?

You saved me a lot of time, but I may need this feature. Can you please give me some light on this?

Best regards,

---

### Post by oldnik on 2012-10-18
Hello everyone! It seems that thread is quite old, but methods still exist and are usable. I have configured my gedit to compile java code with adding an external tool to run the code: ```
#!/bin/sh
/usr/lib/jvm/java-7-openjdk-i386/bin/javac $GEDIT_CURRENT_DOCUMENT_PATH
java ${GEDIT_CURRENT_DOCUMENT_NAME%\.*}
``` I used the full path for javac compiler because it didn't find one with only 'javac'. But here is an another problem. I've been using Eclipse IDE for a while and want to run the code from a project. It gives an error: ```
Exception in thread "main" java.lang.NoClassDefFoundError: myClass (wrong name: math/myClass)
``` but if i comment the ```
package: math
``` part then it gives this: ```
Exception in thread "main" java.util.NoSuchElementException
    at java.util.Scanner.throwFor(Scanner.java:907)
    at java.util.Scanner.next(Scanner.java:1416)
``` while starting the program. Now i need to writedown the path to math lib or what?

---

