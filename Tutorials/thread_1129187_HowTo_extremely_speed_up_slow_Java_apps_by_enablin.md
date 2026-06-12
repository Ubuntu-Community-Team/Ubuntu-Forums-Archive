---
title: "HowTo: extremely speed up slow Java apps by enabling them to use OpenGL"
date: 2009-04-18
forum: Tutorials
---

### Post by Patrick Metz on 2009-04-18
[SIZE="4"]_Introduction_[/SIZE]
I recently moved from Vista to Ubuntu. And everything went really smooth. Way better than
expected. But one thing really disturbed me: 
many of the bigger Java apps (Vuze, for example) seem to have really slow and
unresponsive user interfaces. Trivial things like scrolling down a list of files contained
within a torrent become a real ordeal. So I searched around the Web and found advices
like "downgrade from Java 6 to Java 5", etc... but they did not make any difference
at all.

So I googled... and googled... and googled... and finally found this:
[http://java.sun.com/j2se/1.5.0/docs/guide/2d/new_features.html#ogl](http://java.sun.com/j2se/1.5.0/docs/guide/2d/new_features.html#ogl)

Among other things this link tells you, that there's a command line switch
(-Dsun.java2d.opengl=true), that you can use to turn on OpenGL-acceleration for
your Java programs... So I tried it out on Vuze... and was totally surprised to 
see how its GUI performance skyrocketed through the roof. So I decided to 
create this tutorial to share my new nerd trick ;)

I'm going to explain the steps in general and then I'm going to show two real
world examples and tell you how to speed up Vuze and SmartSVN (chosen because 
they're two Java based apps which I use daily).


[SIZE="4"]_Requirements_[/SIZE]
1) An installed and enabled OpenGL-driver for your graphics card

   ([https://help.ubuntu.com/community/BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto)) Note to Nvidia-Users:
   Don't use driver version 177 anymore; it's got serious 2D performance issues.

2) Sun Java version 5 or higher 

   ([https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java))

3) A Java application with a sluggish user interface ;-)

4) Ability to unterstand a bit of shell scripts...

... uhm... well that's a "bit" tricky... because in order to find the right place
to put the command line switch into, you've got to understand a bit of shell scripts.
Explaining this would be totally out of the scope of this tutorial. If you have a
programming background it's a nobrainer. But if you are not able to read shell
scripts, I suggest you either ask someone who is able and let him or her find the
right spot, or... if you're the adventurous type... feel free to dive right into a tutorial
about shell scripting ;-) For Example: [http://steve-parker.org/sh/sh.shtml](http://steve-parker.org/sh/sh.shtml) or
[http://tldp.org/LDP/abs/html/index.html](http://tldp.org/LDP/abs/html/index.html)


[SIZE="4"]_General Steps_[/SIZE]
It seems that Java apps are launched via shell scripts most of the time.
These shell scripts typically set up command line options (among other things)
for the application and finally start java with the command line options and the
path of your application. So this is what you've got to do:

Step 1)
You've got to find the script that launches your particular application;
examine the properties of your programs shortcut to get the path.

Step 2)
Open the launchscript in your favourite texteditor

Step 3)
Find the right place to add the command line switch, paste it there and save the file.

Step 4)
Launch your application and enjoy a snappy userinterface 8-)

[SIZE="4"]_Example: Vuze_[/SIZE]
Without OpenGL accelleration Vuze was extremely sluggish. But after I set the OpenGL
switch, I even ditched uTorrent (running on Wine) because Vuze is so responsive now
that I can really enjoy its powerful features.

I'm using Vuze 4.2.0.2. I downloaded the Linux package from their homepage, unzipped
it to /opt/vuze and made a shortcut on my desktop.

Step 1)
Rightclick the shortcut, open its properties and find out where the corresponding 
shell script is. In my case it's /opt/vuze/vuze.

Step 2)
Open the script in an editor. Let's assume your editor is gedit: Push ALT+F2,
type "gedit /opt/vuze/vuze" (without the quotes) and confirm by pushing enter.

Step 3)
You examine the script and find this at its end
```
${JAVA_PROGRAM_DIR}java "${JAVA_ARGS}" \
	-cp "${CLASSPATH}" \
	-Djava.library.path="${PROGRAM_DIR}" \
	-Dazureus.install.path="${PROGRAM_DIR}" \
	-Dazureus.script="$0" \
	$JAVA_PROPS \
	$START_CLASS "$@"
```
Now you change the code to
```

${JAVA_PROGRAM_DIR}java "${JAVA_ARGS}" \
	-cp "${CLASSPATH}" \
	-Djava.library.path="${PROGRAM_DIR}" \
	**[COLOR="Red"]-Dsun.java2d.opengl=true \[/COLOR]**
	-Dazureus.install.path="${PROGRAM_DIR}" \
	-Dazureus.script="$0" \
	$JAVA_PROPS \
	$START_CLASS "$@"

```

and save the file.

4) You run Vuze and are amazed, because it's really really fast :cool:

[SIZE="4"]_Example: SmartSVN_[/SIZE]
Another application I managed to get on speed is SmartSVN. It had really frustrating
slowdowns, especially when scrolling through the source of compared files. But thanks
to the OpenGL switch this is a story from the past :-)

I'm using version 5.0.5 and installed it into /opt.

Step 1)
Examine the shortcut, view its properties and find the shell script. In my case
it's /opt/smartsvn/bin/smartsvn.sh.

Step 2)
Open the script. Let's again assume, that your editor is gedit.Just push ALT+F2
and then type "gedit /opt/smartsvn/bin/smartsvn.sh" (without the doublequotes)
and hit enter to confirm.

Step 3)
You need to change this line at the end of the file
```

$_JAVA_EXEC -classpath "$_CP" $_VM_PROPERTIES -Xmx${MAXIMUM_HEAP_SIZE} -Dsmartsvn.vm-xmx=${MAXIMUM_HEAP_SIZE} SmartSVN "$@"

```

into this
```

$_JAVA_EXEC -classpath "$_CP" $_VM_PROPERTIES [COLOR="Red"]**-Dsun.java2d.opengl=true**[/COLOR] -Xmx${MAXIMUM_HEAP_SIZE} -Dsmartsvn.vm-xmx=${MAXIMUM_HEAP_SIZE} SmartSVN "$@"

```

and save the shell script.

4.) Run SmartSVN and feel free to scroll up and down and compare files as much as you like :-)

[SIZE="4"]_The End_[/SIZE]
Thats it. I hope you enjoyed my tutorial. Feel free to offer constructive criticism :D

---

### Post by Nano on 2009-04-20
This sounds very interesting.

You mean one of the reasons why java IDEs like Netbeans and Eclipse run significantly slow is because they're not using OpenGL?
Do you think this would speed them up?

---

### Post by Patrick Metz on 2009-04-20
> **Nano said:**
> This sounds very interesting.

You mean one of the reasons why java IDEs like Netbeans and Eclipse run significantly slow is because they're not using OpenGL?
Do you think this would speed them up?

I have not tested it with Eclipse yet, but someone who read my tutorial pointed
me to this page of the Netbeans documentation: [http://performance.netbeans.org/howto/jvmswitches/index.html](http://performance.netbeans.org/howto/jvmswitches/index.html).
Under "Options affecting graphic behavior" it mentiones the same openGL command
line switch (and some other switches I didn't know about) to speed up their IDE.
So you can definitely speed up Netbeans with this switch. :)

---

### Post by meho_r on 2009-04-20
It would be nice to have openGL for java enabled generally, so one doesn't have to tinker with particular apps. However, thanks a lot for these infos, Patrick :)

---

### Post by sandy8925 on 2009-04-20
Yeah meho_r is right. Is there any way to enable opengl for all Java applications ? And what about Flash applications ? Do Pidgin and openoffice also use java ?

---

### Post by Patrick Metz on 2009-04-20
> **meho_r said:**
> It would be nice to have openGL for java enabled generally, so one doesn't have to tinker with particular apps. However, thanks a lot for these infos, Patrick :)

Yes, that would be nice. The only thing I found in this direction is
the file /etc/java-6-sun/jvm.cfg. I found out that it contains the
default properties of the Java Virtual Machine. But adding the command
line switch there did not make any differences...:-k

---

### Post by Nano on 2009-04-21
> **Patrick Metz said:**
> I have not tested it with Eclipse yet, but someone who read my tutorial pointed
me to this page of the Netbeans documentation: [http://performance.netbeans.org/howto/jvmswitches/index.html](http://performance.netbeans.org/howto/jvmswitches/index.html).
Under "Options affecting graphic behavior" it mentiones the same openGL command
line switch (and some other switches I didn't know about) to speed up their IDE.
So you can definitely speed up Netbeans with this switch. :)

Thanks, mate, for your answer.
I'll definitely try this out and let you know the results.

Cheers!

---

### Post by Nano on 2009-04-21
I have tried the tuning switch described above and I, indeed, experienced some performance improvements using Netbeans 6.5 with php plugins.

In order to do this you have to edit the file

"yourNetbeansInstallPath/etc/netbeans.conf"

As described in the link posted by Patrick Metz, you have to edit the 6th line and add there your switches.
Mine now looks like this:
```

netbeans_default_options="-J-client -J-Xverify:none -J-Xss2m -J-Xms32m -J-XX:PermSize=32m -J-XX:MaxPermSize=200m -J-Dapple.laf.useScreenMenuBar=true -J-Dsun.java2d.noddraw=true -Dsun.java2d.opengl=true -Dsun.java2d.d3d=false"

```
(I added the last two switches to the string.)

After that just save the file and start again Netbeans from your regular launch script.


Thanks for the tips, Patrick

---

### Post by cb951303 on 2009-04-21
as far as I see this is only valid for java 2d: [http://java.sun.com/docs/books/tutorial/2d/index.html](http://java.sun.com/docs/books/tutorial/2d/index.html)

I don't see how it affects GUI resposiveness. Are you sure it's not a placebo effect :)

---

### Post by Nano on 2009-04-21
> **cb951303 said:**
> as far as I see this is only valid for java 2d: [http://java.sun.com/docs/books/tutorial/2d/index.html](http://java.sun.com/docs/books/tutorial/2d/index.html)

I don't see how it affects GUI resposiveness. Are you sure it's not a placebo effect :)

Considering what coffee makes to me, this could also be a placebo effect, indeed. However, I'd swear there's a change :)
It's also reported on Netbeans page under [http://performance.netbeans.org/howto/jvmswitches/index.html](http://performance.netbeans.org/howto/jvmswitches/index.html)

---

### Post by Patrick Metz on 2009-04-21
> **cb951303 said:**
> as far as I see this is only valid for java 2d: [http://java.sun.com/docs/books/tutorial/2d/index.html](http://java.sun.com/docs/books/tutorial/2d/index.html)

I don't see how it affects GUI resposiveness. Are you sure it's not a placebo effect :)

Well, it's software rendering vs. hardware rendering ... it should be faster... at least in theory ;)
But you cannot speed up all apps. Freemind for example just crashes when 
you enable the OpenGL switch... at least when I enable it... :-s

---

### Post by cb951303 on 2009-04-21
> **Patrick Metz said:**
> Well, it's software rendering vs. hardware rendering ... it should be faster... at least in theory ;)
But you cannot speed up all apps. Freemind for example just crashes when 
you enable the OpenGL switch... at least when I enable it... :-s

yes but it's hardware rendering when *only* using java 2d api. I don't think most of the applications you tried (such as vuze) uses java 2d api at all.

---

### Post by brdokoky on 2009-04-21
What about ,,JDownloader,,. Would you give some tutorial.

---

### Post by Nano on 2009-04-22
> **brdokoky said:**
> What about ,,JDownloader,,. Would you give some tutorial.

Hi there.
Funny you mention jDownloader since I didn't hear of it until two days ago, when my brother told me about its great features.
So I wanted to try it out and this is what I saw:

It comes packed in a zip file, right? So you have to unzip it somewhere and then you usually double-click on the .jar file and it loads just correctly. Well, in order to apply these switches it seems that what you have to do is to execute this line:
```

java -Dsun.java2d.opengl=true -Dsun.java2d.d3d=false -jar /WhereverYouUnzippedIt/JDownloader.jar

```
Or use the same string to create a launcher.

At least according to this page:
[http://java.sun.com/j2se/1.5.0/docs/guide/2d/flags.html](http://java.sun.com/j2se/1.5.0/docs/guide/2d/flags.html)


Let us know, please, if you feel any difference.
Thanks

---

### Post by brdokoky on 2009-04-22
It seems like same. Thanks anyway.

---

### Post by Patrick Metz on 2009-04-29
> **sandy8925 said:**
> Do Pidgin and openoffice also use java ?
OpenOffice uses Java too, but you don't need to mess with its startup script. It has an option in its preferences that you can tick to enable OpenGL rendering.

---

### Post by ScottFur on 2009-05-15
This does work with Eclipse 3.4.
There is a little bit of speed improvement.
Edit the eclipse.ini file as shown below.
Note that the directives need to be placed after the [-vmargs] directive

```

-vmargs
-Dsun.java2d.opengl=true
-Dsun.java2d.d3d=false
-Xms...

```For OpenOffice3, goto Tools->Options
Under OpenOffice.org->view you will see the settings on the right side to enable openGL.

Cheers

---

### Post by ubunxpm on 2009-06-22
Hello,

Would openGL option can be used to speed up java games in browsers? Don`t know if possible. Just curious.

---

### Post by KaliVoid on 2009-12-08
It's speeding up Tuxguitar 1.2
from 20sec to 10sec launch time

```
${JAVA} ${VM_ARGS} -cp :${CLASSPATH} -Dtuxguitar.share.path="/usr/share/tuxguitar/" **-Dsun.java2d.opengl=true** -Djava.library.path="${LD_LIBRARY_PATH}" ${MAINCLASS} "$1" "$2"
```

---

### Post by kemsiro on 2010-02-20
doesn't make any changes for jDownloader

Thanks aniwaiz.

---

### Post by carthmen on 2010-05-18
You sir, are a hero!!
Thank You.
ThinkOrSwim runs like a charm now!

---

### Post by fuzzylogic25 on 2010-10-18
I cant do this. when it try i get this:


Could not find the main class:  -Dsun.java2d.opengl=true. Program will exit.



So has there been some updates in java which make this unavailable? This is my azureus script:

===================================================

 #!/bin/sh
  2 
  3 # Include java-wrappers
  4 . /usr/lib/java-wrappers/java-wrappers.sh
  5 
  6 JAVA_CLASSPATH="/usr/lib/jni:/usr/lib/java"
  7 VUZE_BIN="/usr/bin/vuze"
  8 
  9 find_java_runtime openjdk sunmin5
 10 
 11 find_jars Azureus2 log4j-1.2 commons-cli swt
 12 
 13 if [ ! -x $VUZE_BIN ]; then
 14   UI=-Dforce.ui=az2
 15 fi
 16 
 17 run_java -Dazureus.install.path="$HOME/.azureus" $UI \
 18     org.gudy.azureus2.ui.common.Main "$@"

==================================================================

---

### Post by MaxIBoy on 2010-10-19
Wow, that really helps playing Minecraft. Good work!

---

### Post by JohnnyC35 on 2010-10-27
> **fuzzylogic25 said:**
> I cant do this. when it try i get this:


Could not find the main class:  -Dsun.java2d.opengl=true. Program will exit.



So has there been some updates in java which make this unavailable? This is my azureus script:

===================================================

 #!/bin/sh
  2 
  3 # Include java-wrappers
  4 . /usr/lib/java-wrappers/java-wrappers.sh
  5 
  6 JAVA_CLASSPATH="/usr/lib/jni:/usr/lib/java"
  7 VUZE_BIN="/usr/bin/vuze"
  8 
  9 find_java_runtime openjdk sunmin5
 10 
 11 find_jars Azureus2 log4j-1.2 commons-cli swt
 12 
 13 if [ ! -x $VUZE_BIN ]; then
 14   UI=-Dforce.ui=az2
 15 fi
 16 
 17 run_java -Dazureus.install.path="$HOME/.azureus" $UI \
 18     org.gudy.azureus2.ui.common.Main "$@"

==================================================================

same issue here

---

### Post by mister_playboy on 2010-10-29
This worked great for me... Vuze is quite a bit more responsive now! :guitar:

Here's my Vuze startup script:
```
#!/bin/bash

######## CONFIGURATION OPTIONS ########
SCRIPT_NOT_CHANGED=0	# change this to 1 if you don't want your script overwritten!
JAVA_PROGRAM_DIR=""	# use full path to java bin dir, ex. "/usr/java/j2sdk1.4.2/bin/"
#PROGRAM_DIR="/home/username/apps/azureus"	# use full path to Azureus bin dir
JAVA_ARGS="-Xmx128m"

#export MOZILLA_FIVE_HOME="/path/to/gre"	# Full path to GRE/Mozilla. When commenting out this line, also comment out the next line
#if [ "$LD_LIBRARY_PATH x" = " x" ]; then export LD_LIBRARY_PATH=$MOZILLA_FIVE_HOME; else export LD_LIBRARY_PATH=$MOZILLA_FIVE_HOME:$LD_LIBRARY_PATH; fi
#######################################



######## YOU PROBABLY DO NOT WANT TO TOUCH ANYTHING BELOW! ########

SCRIPT_VERSION=2
START_CLASS="org.gudy.azureus2.ui.swt.Main"

MSG_LOADING="Loading Azureus:"
MSG_STARTING="Starting Azureus..."
MSG2="Java exec found in "
MSG3="OOPS, your java version is too old "
MSG4="You need to upgrade to JRE 1.4.x or newer from http://java.sun.com"
MSG5="Suitable java version found "
MSG6="Configuring environment..."
MSG7="OOPS, you don't seem to have a valid JRE "
MSG8="OOPS, unable to locate java exec in "
MSG9=" hierarchy"
MSG10="Java exec not found in PATH, starting auto-search..."
MSG11="Java exec found in PATH. Verifying..."
MSG_AZEXIT="Exit from Azureus complete"
MSG_TERMINATED="Azureus TERMINATED."
MSG_RECHECK="Re-checking with GCJ (Sun Java recommended).."
MSG_ISGCJ="Java is GCJ.. looking for Sun Java.."
MSG_JAVABORK="Java appeared to have crashed:"

SKIP_GCJ=1

look_for_java()
{
	if command -v java &>/dev/null; then
		if check_version ; then
			echo $MSG11
			return 0
		fi
	fi

	echo $MSG10


	JAVA_CHECK_DIRS="/usr/java/latest /usr/java /usr/lib/jvm/latest /usr/lib/jvm"
	for JAVADIR in $JAVA_CHECK_DIRS; do
		IFS=$'\n'
		potential_java_dirs=(`ls -1 "$JAVADIR" | sort | tac 2>/dev/null`)
		IFS=
		for D in "${potential_java_dirs[@]}"; do
			if [[ -d "$JAVADIR/$D" && -x "$JAVADIR/$D/bin/java" ]]; then
				JAVA_PROGRAM_DIR="$JAVADIR/$D/bin/"
				echo $MSG2 $JAVA_PROGRAM_DIR
				if check_version ; then
					return 0
				else
					return 1
				fi
			fi
		done
	done
	
	if [ $SKIP_GCJ ] ; then
		echo $MSG_RECHECK
		SKIP_GCJ=
		if look_for_java ; then
			return 0
		else
			return 1
		fi
	else
		echo $MSG8 "${JAVADIR}/" $MSG9 ; echo $MSG4
	fi
	return 1
}

check_version()
{
	if [ $SKIP_GCJ ] ; then
		JAVA_ISGCJ=`"${JAVA_PROGRAM_DIR}java" -version 2>&1 | grep "gcj"`
		if [ ! "$JAVA_ISGCJ x" = " x" ] ; then
			echo $MSG_ISGCJ
			return 1
		fi
	fi

	JAVA_HEADER=`"${JAVA_PROGRAM_DIR}java" -version 2>&1 | head -n 1`
	JAVA_IMPL=`echo ${JAVA_HEADER} | cut -f1 -d' '`
	if [ "$JAVA_IMPL" = "java" ] ; then
		VERSION=`echo ${JAVA_HEADER} | sed "s/java version \"\(.*\)\"/\1/"`
		if echo $VERSION | grep "^1.[0-3]" ; then
			echo $MSG3 "[${JAVA_PROGRAM_DIR}java = ${VERSION}]" ; echo $MSG4
			return 1
		else
			echo $MSG5 "[${JAVA_PROGRAM_DIR}java = ${VERSION}]" ; echo $MSG6
			return 0
		fi
	elif [ "$JAVA_IMPL" = "#" ] ; then
		echo $MSG_JAVABORK
		${JAVA_PROGRAM_DIR}java -version 2>&1
		exit 1
	else	
		echo $MSG7 "[${JAVA_PROGRAM_DIR}java = ${JAVA_IMPL}]" ; echo $MSG4
		return 1
	fi
}

runJavaOutput()
{
	# assume we can write to the user's home..

	${JAVA_PROGRAM_DIR}java "${JAVA_ARGS}" \
		-cp "${CLASSPATH}" \
		-Djava.library.path="${PROGRAM_DIR}" \
		-Dsun.java2d.opengl=true \
		-Dazureus.install.path="${PROGRAM_DIR}" \
		-Dazureus.script="$0" \
		$JAVA_PROPS \
		"$@" > ~/azScript
	if [ -f ~/azScript ]; then
		chmod +x ~/azScript
		. ~/azScript
		rm ~/azScript
	fi
}

echo $MSG_STARTING

# locate and test the java executable
if [ "$JAVA_PROGRAM_DIR" == "" ]; then
	if ! look_for_java ; then
		exit 1
	fi
fi

# get the app dir if not already defined
if [ -z "$PROGRAM_DIR" ]; then
		PROGRAM_DIR=`dirname "$0"`
		PROGRAM_DIR=`cd "$PROGRAM_DIR"; pwd`
else
	if [ "$(echo ${PROGRAM_DIR}/*.jar)" = "${PROGRAM_DIR}/*.jar" ]; then
		echo "You seem to have set an invalid PROGRAM_DIR, unable to continue!"
		exit 1
	elif [ ! -f "${PROGRAM_DIR}/Azureus2.jar" ]; then
		echo "Unable to locate Azureus2.jar in $PROGRAM_DIR, aborting!"
		exit 1
	fi
fi

# Change path here so we can do for loop on program dirs with spaces
cd "${PROGRAM_DIR}"

# build the classpath
for FILE in ./*.jar; do
	CLASSPATH="${CLASSPATH:+${CLASSPATH}:}$FILE"
done

# setup Java System Properties (no spaces in values)
JAVA_PROPS="-Dazureus.script.version=${SCRIPT_VERSION}"
if [ ! "$JAVA_ISGCJ x" = " x" ] ; then
	JAVA_PROPS="$JAVA_PROPS -Dgnu.gcj.runtime.VMClassLoader.library_control=never"
fi

# some distros symlink application level plugins into the users's plugin directory..
# remove all symlinks in user's plugin directory
find ~/.azureus/plugins -maxdepth 1 -type l -xtype d  -exec rm {} \;

runJavaOutput "org.gudy.azureus2.platform.unix.ScriptBeforeStartup" "$@";

echo $MSG_LOADING

echo "${JAVA_PROGRAM_DIR}java ${JAVA_ARGS} -cp \"${CLASSPATH}\" -Djava.library.path=\"${PROGRAM_DIR}\" -Dazureus.install.path=\"${PROGRAM_DIR}\" -Dazureus.script=\"$0\" $JAVA_PROPS $START_CLASS $@"
# Don't use "exec -a Azureus ..." here as exec quits this script after completion,
# preventing ScriptAfterShutdown from running, which installs updates and does
# restarts
${JAVA_PROGRAM_DIR}java "${JAVA_ARGS}" \
	-cp "${CLASSPATH}" \
	-Djava.library.path="${PROGRAM_DIR}" \
	-Dazureus.install.path="${PROGRAM_DIR}" \
	-Dazureus.script="$0" \
	$JAVA_PROPS \
	$START_CLASS "$@"

echo $MSG_AZEXIT

runJavaOutput "org.gudy.azureus2.platform.unix.ScriptAfterShutdown" "$@";

echo $MSG_TERMINATED

```

Here's my JDownloader script.  Startup is still ugly compared to the Windows version, but it seems more responsive when minimizing/maximizing or switching to and from the JD window.
```
#!/bin/bash
#JD Installer/Starter Version 0.2
#by Jiaz(JD-Team), jiaz@jdownloader.org
#You need at least:
#1.) bash (its a bash script ;) )
#2.) wget 
#3.) Java Version >= 1.5 (OpenJDK works also in latest Version)

#How to use this?
#1.) chmod +x jd.sh
#2.) Place it anywhere you want
#3.) Running jd.sh for the first time will install and setup JD into JDDIR folder
#4.) Running jd.sh after the first time will start JDownloader directly

#Parameters
# update (will perform an update)

#JD Installation folder (adjust to your needs)
JDDIR=~/.jd
#default path to our install/update tool (DO NOT Change this)
JDINSTALLER=http://update0.jdownloader.org/jdupdate.jar

if [ -e $JDDIR ]
then
if [ "$1" = "update" ]
then
if [ -e $JDDIR/jdupdate.jar ]
then
cd $JDDIR
echo "Start JD-Updater"
java -Xmx512m -jar jdupdate.jar
exit
else
echo "Cannot start JD-Updater: Download/Start JD-Installer"
cd $JDDIR
wget $JDINSTALLER
java -Xmx512m -jar jdupdate.jar
exit
fi
fi
if [ -e $JDDIR/JDownloader.jar ]
then
echo "JD Installation found: Starting JD now"
cd $JDDIR
#java -Xmx512m -jar JDownloader.jar --add-links $1 $2 $3 $4 $5 $6 $7 $8 $9
java -Dsun.java2d.opengl=true -Dsun.java2d.d3d=false -Xmx512m -jar JDownloader.jar
exit
else
echo "JD Installation found: No valid JDownloader.jar exist!"
fi
if [ -e $JDDIR/jdupdate.jar ]
then
cd $JDDIR
echo "Start JD-Updater"
java -Xmx512m -jar jdupdate.jar
else
echo "Cannot start JD-Updater: Download/Start JD-Installer"
cd $JDDIR
wget $JDINSTALLER
java -Xmx512m -jar jdupdate.jar
exit
fi
else
echo "Download/Start JD-Installer"
mkdir $JDDIR
cd $JDDIR
wget $JDINSTALLER
java -Xmx512m -jar jdupdate.jar
exit
fi

```

---

### Post by mer0090 on 2011-03-19
Hi,

I tried to add to the vuze script "-Dsun.java2d.opengl=true \" but uze started and almost immediately shut down, here is the log:


seba@seba-laptop:~$ ~/azureus/vuze/azureus 
Starting Azureus...
Suitable java version found [java = 1.6.0_20]
Configuring environment...
Java exec found in PATH. Verifying...

** (SWT:2671): CRITICAL **: giop_thread_request_push: assertion `tdata != NULL' failed
GRE/XULRunner automatically found
Loading Azureus:
java -Xmx128m -cp "./Azureus2.jar:./swt.jar" -Djava.library.path="/home/seba/azureus/vuze" -Dazureus.install.path="/home/seba/azureus/vuze" -Dazureus.script="/home/seba/azureus/vuze/azureus" -Dazureus.script.version=2 org.gudy.azureus2.ui.swt.Main 
file:/home/seba/azureus/vuze/Azureus2.jar ; file:/home/seba/azureus/vuze/swt.jar ; file:/home/seba/azureus/vuze/
UIFunctions/ImageLoad took 0ms
new shell took 176ms
new shell setup took 81ms
skin init took 120ms
MainMenu init took 126ms
pre skin widgets init took 50ms
WARNING: already added UIUpdatable com.aelitis.azureus.ui.swt.views.skin.sidebar.SideBar@221e9e
skin widgets (1/2) init took 228ms
skin widgets (2/2) init took 211ms
pre SWTInstance init took 0ms
Init Core Columns took 103ms
SWTInstance init took 0ms
shell.layout took 50ms
---------SHOWN AT 1300549644972;2880ms
---------DONE DISPATCH AT 1300549646483;4391ms
---------READY AT 1300549646508;4424ms
shell.open took 1553ms
processStartupDMS took 0ms
vuzeactivities init took 0ms
Locale Initializing took 8ms
16462:    Core: 76ms for activity between 'Loading Plugin: mlab' and 'Loading Plugin: xmwebui'
16508:    Core: 25ms for activity between 'Loading Plugin: xmwebui' and 'Loading Torrents'
16539:    Core: 35ms for activity between 'Loading Plugin: azupnpav' and 'Loading Plugin: aefeatman_v'
16717:    Core: 168ms for activity between 'Loading Plugin: aefeatman_v' and 'Loading Plugin: azupdater'
16738:    Core: 30ms for activity between 'Loading Plugin: azupdater' and 'Loading Plugin: azsmrc'
16821:    Core: 76ms for activity between 'Loading Plugin: azsmrc' and 'Loading Plugin: news'
16871:    Core: 46ms for activity between 'Loading Plugin: news' and 'Loading Plugin: azupnpav'
16922:    Core: 50ms for activity between 'Loading Plugin: azupnpav' and 'Loading Plugin: azplugins'
16980:    Core: 76ms for activity between 'Loading Plugin: azplugins' and 'Loading Plugin: azrating'
17013:    Core: 25ms for activity between 'Loading Plugin: azrating' and 'Loading Plugin: Start/Stop Rules'
17075:    Core: 50ms for activity between 'Loading Plugin: Start/Stop Rules' and 'Loading Plugin: Torrent Removal Rules'
17136:    Core: 61ms for activity between 'Loading Plugin: Plugin Update Checker' and 'Loading Plugin: UPnP'
17165:    Core: 42ms for activity between 'Loading Plugin: UPnP' and 'Loading Plugin: DHT'
17252:    Core: 68ms for activity between 'Loading Plugin: DHT Tracker' and 'Loading Plugin: Magnet URI Handler'
17276:    Core: 25ms for activity between 'Loading Plugin: Magnet URI Handler' and 'Loading Plugin: Core Update Checker'
17319:    Core: 26ms for activity between 'Loading Plugin: Platform Checker' and 'Loading Torrent  4 of 73 : 8CF92B159513D5A50A68D81037651A5E807478FE.torrent'
17346:    Core: 25ms for activity between 'Loading Plugin: External Seed' and 'Loading Plugin: Local Tracker'
17370:    Core: 25ms for activity between 'Loading Plugin: Local Tracker' and 'Loading Plugin: Network Status'
17444:    Core: 70ms for activity between 'Loading Plugin: Buddy' and 'Loading Plugin: RSS'
18097:    Core: 656ms for activity between 'Loading Plugin: RSS' and 'Loading Torrent  5 of 73 : 634D46B4FF9C0D237B4AEA7DFAF1E22CEE3152E0.torrent'
19871:    Core: 1763ms for activity between 'Initialising Global Torrent Manager' and 'Initialising Plugin: Measurement Lab (M-Lab)'
19921:    Core: 36ms for activity between 'Initialising Plugin: Vuze Web Remote' and 'Initialising Plugin: Vuze Feature Manager'
19989:    Core: 77ms for activity between 'Initialising Plugin: Vuze Feature Manager' and 'Initialising Plugin: Azureus Update Support'
20025:    Core: 50ms for activity between 'Initialising Plugin: AzSMRC' and 'Initialising Plugin: NEWS'
DEBUG::Sat Mar 19 16:47:30 CET 2011::org.gudy.azureus2.pluginsimpl.local.PluginInitializer::initialisePlugin::1594:
  java.lang.IllegalArgumentException: Empty key
	at javax.crypto.spec.SecretKeySpec.<init>(SecretKeySpec.java:96)
	at lbms.azsmrc.plugin.main.XMLConfig.loadConfigFile(XMLConfig.java:76)
	at lbms.azsmrc.plugin.main.Plugin.initialize(Plugin.java:148)
	at org.gudy.azureus2.pluginsimpl.local.PluginInitializer$8.run(PluginInitializer.java:1571)
	at org.gudy.azureus2.pluginsimpl.local.utils.UtilitiesImpl.callWithPluginThreadContext(UtilitiesImpl.java:951)
	at org.gudy.azureus2.pluginsimpl.local.PluginInitializer.initialisePlugin(PluginInitializer.java:1561)
	at org.gudy.azureus2.pluginsimpl.local.PluginInitializer.access$400(PluginInitializer.java:59)
	at org.gudy.azureus2.pluginsimpl.local.PluginInitializer$2.run(PluginInitializer.java:1318)
	at org.gudy.azureus2.pluginsimpl.local.PluginInitializer.initialisePlugins(PluginInitializer.java:1497)
	at com.aelitis.azureus.core.impl.AzureusCoreImpl.start(AzureusCoreImpl.java:847)
	at com.aelitis.azureus.ui.swt.Initializer.run(Initializer.java:533)
	at org.gudy.azureus2.ui.swt.mainwindow.SWTThread$7.runSupport(SWTThread.java:274)
	at org.gudy.azureus2.core3.util.AERunnable.run(AERunnable.java:38)
	at java.lang.Thread.run(Thread.java:636)

[alert] Alert:3:Error initializing plugin 'AzSMRC'
DEBUG::Sat Mar 19 16:47:30 CET 2011::org.gudy.azureus2.pluginsimpl.local.PluginInitializer::initialisePlugin::1598:
  java.lang.IllegalArgumentException: Empty key
	at javax.crypto.spec.SecretKeySpec.<init>(SecretKeySpec.java:96)
	at lbms.azsmrc.plugin.main.XMLConfig.loadConfigFile(XMLConfig.java:76)
	at lbms.azsmrc.plugin.main.Plugin.initialize(Plugin.java:148)
	at org.gudy.azureus2.pluginsimpl.local.PluginInitializer$8.run(PluginInitializer.java:1571)
	at org.gudy.azureus2.pluginsimpl.local.utils.UtilitiesImpl.callWithPluginThreadContext(UtilitiesImpl.java:951)
	at org.gudy.azureus2.pluginsimpl.local.PluginInitializer.initialisePlugin(PluginInitializer.java:1561)
	at org.gudy.azureus2.pluginsimpl.local.PluginInitializer.access$400(PluginInitializer.java:59)
	at org.gudy.azureus2.pluginsimpl.local.PluginInitializer$2.run(PluginInitializer.java:1318)
	at org.gudy.azureus2.pluginsimpl.local.PluginInitializer.initialisePlugins(PluginInitializer.java:1497)
	at com.aelitis.azureus.core.impl.AzureusCoreImpl.start(AzureusCoreImpl.java:847)
	at com.aelitis.azureus.ui.swt.Initializer.run(Initializer.java:533)
	at org.gudy.azureus2.ui.swt.mainwindow.SWTThread$7.runSupport(SWTThread.java:274)
	at org.gudy.azureus2.core3.util.AERunnable.run(AERunnable.java:38)
	at java.lang.Thread.run(Thread.java:636)

Error initializing plugin 'AzSMRC' : java.lang.IllegalArgumentException: Empty key
20053:    Core: 26ms for activity between 'Initialising Plugin: NEWS' and 'Initialising Plugin: UPnP Media Server'
20160:    Core: 100ms for activity between 'Initialising Plugin: UPnP Media Server' and 'Initialising Plugin: Tracker Static Pages'
20226:    Core: 67ms for activity between 'Initialising Plugin: Tracker Static Pages' and 'Initialising Plugin: Rating'
20250:    Core: 23ms for activity between 'Initialising Plugin: Start/Stop Rules' and 'Initialising Plugin: Download Remove Rules'
20268:    Core: 11ms for activity between 'Initialising Plugin: Share Hoster' and 'Initialising Plugin: PluginUpdate'
20294:    Core: 14ms for activity between 'Initialising Plugin: Universal Plug and Play (UPnP)' and 'Initialising Plugin: Distributed DB'
20328:    Core: 11ms for activity between 'Initialising Plugin: Distributed Tracker' and 'Initialising Plugin: Magnet URI Handler'
20336:    Core: 19ms for activity between 'Initialising Plugin: Magnet URI Handler' and 'Initialising Plugin: CoreUpdater'
20352:    Core: 14ms for activity between 'Initialising Plugin: External Seed' and 'Initialising Plugin: LAN Peer Finder'
Core Initializing took 4149ms
psDMS 0ms
Analysing /home/seba/azureus/vuze/hs_err_pid990.log
#
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x02a795a0, pid=2701, tid=2744982384
#
# JRE version: 6.0_20-b20
# Java VM: OpenJDK Server VM (19.0-b09 mixed mode linux-x86 )
# Derivative: IcedTea6 1.9.7
# Distribution: Ubuntu 10.10, package 6b20-1.9.7-0ubuntu1
# Problematic frame:
# C  [libGL.so.1+0x6d5a0]  XF86DRIQueryExtension+0x8e
#
# An error report file with more information is saved as:
# /home/seba/azureus/vuze/hs_err_pid2701.log
#
# If you would like to submit a bug report, please include
# instructions how to reproduce the bug and visit:
#   [https://bugs.launchpad.net/ubuntu/+source/openjdk-6/](https://bugs.launchpad.net/ubuntu/+source/openjdk-6/)
# The crash happened outside the Java Virtual Machine in native code.
# See problematic frame for where to report the bug.
#
/home/seba/azureus/vuze/azureus: line 190:  2701 Aborted                 ${JAVA_PROGRAM_DIR}java "${JAVA_ARGS}" -cp "${CLASSPATH}" -Djava.library.path="${PROGRAM_DIR}" -Dsun.java2d.opengl=true -Dazureus.install.path="${PROGRAM_DIR}" -Dazureus.script="$0" $JAVA_PROPS $START_CLASS "$@"
Exit from Azureus complete
No shutdown tasks to do
Azureus TERMINATED.
seba@seba-laptop:~$ ~~~~~~


Any idea?

---

### Post by mer0090 on 2011-03-19
Hi,

I tried to add to the vuze script "-Dsun.java2d.opengl=true \" but uze started and almost immediately shut down, here is the log:


seba@seba-laptop:~$ ~/azureus/vuze/azureus 
Starting Azureus...
Suitable java version found [java = 1.6.0_20]
Configuring environment...
Java exec found in PATH. Verifying...

** (SWT:2671): CRITICAL **: giop_thread_request_push: assertion `tdata != NULL' failed
GRE/XULRunner automatically found
Loading Azureus:
java -Xmx128m -cp "./Azureus2.jar:./swt.jar" -Djava.library.path="/home/seba/azureus/vuze" -Dazureus.install.path="/home/seba/azureus/vuze" -Dazureus.script="/home/seba/azureus/vuze/azureus" -Dazureus.script.version=2 org.gudy.azureus2.ui.swt.Main 
file:/home/seba/azureus/vuze/Azureus2.jar ; file:/home/seba/azureus/vuze/swt.jar ; file:/home/seba/azureus/vuze/
UIFunctions/ImageLoad took 0ms
new shell took 176ms
new shell setup took 81ms
skin init took 120ms
MainMenu init took 126ms
pre skin widgets init took 50ms
WARNING: already added UIUpdatable com.aelitis.azureus.ui.swt.views.skin.sidebar.SideBar@221e9e
skin widgets (1/2) init took 228ms
skin widgets (2/2) init took 211ms
pre SWTInstance init took 0ms
Init Core Columns took 103ms
SWTInstance init took 0ms
shell.layout took 50ms
---------SHOWN AT 1300549644972;2880ms
---------DONE DISPATCH AT 1300549646483;4391ms
---------READY AT 1300549646508;4424ms
shell.open took 1553ms
processStartupDMS took 0ms
vuzeactivities init took 0ms
Locale Initializing took 8ms
16462:    Core: 76ms for activity between 'Loading Plugin: mlab' and 'Loading Plugin: xmwebui'
16508:    Core: 25ms for activity between 'Loading Plugin: xmwebui' and 'Loading Torrents'
16539:    Core: 35ms for activity between 'Loading Plugin: azupnpav' and 'Loading Plugin: aefeatman_v'
16717:    Core: 168ms for activity between 'Loading Plugin: aefeatman_v' and 'Loading Plugin: azupdater'
16738:    Core: 30ms for activity between 'Loading Plugin: azupdater' and 'Loading Plugin: azsmrc'
16821:    Core: 76ms for activity between 'Loading Plugin: azsmrc' and 'Loading Plugin: news'
16871:    Core: 46ms for activity between 'Loading Plugin: news' and 'Loading Plugin: azupnpav'
16922:    Core: 50ms for activity between 'Loading Plugin: azupnpav' and 'Loading Plugin: azplugins'
16980:    Core: 76ms for activity between 'Loading Plugin: azplugins' and 'Loading Plugin: azrating'
17013:    Core: 25ms for activity between 'Loading Plugin: azrating' and 'Loading Plugin: Start/Stop Rules'
17075:    Core: 50ms for activity between 'Loading Plugin: Start/Stop Rules' and 'Loading Plugin: Torrent Removal Rules'
17136:    Core: 61ms for activity between 'Loading Plugin: Plugin Update Checker' and 'Loading Plugin: UPnP'
17165:    Core: 42ms for activity between 'Loading Plugin: UPnP' and 'Loading Plugin: DHT'
17252:    Core: 68ms for activity between 'Loading Plugin: DHT Tracker' and 'Loading Plugin: Magnet URI Handler'
17276:    Core: 25ms for activity between 'Loading Plugin: Magnet URI Handler' and 'Loading Plugin: Core Update Checker'
17319:    Core: 26ms for activity between 'Loading Plugin: Platform Checker' and 'Loading Torrent  4 of 73 : 8CF92B159513D5A50A68D81037651A5E807478FE.torrent'
17346:    Core: 25ms for activity between 'Loading Plugin: External Seed' and 'Loading Plugin: Local Tracker'
17370:    Core: 25ms for activity between 'Loading Plugin: Local Tracker' and 'Loading Plugin: Network Status'
17444:    Core: 70ms for activity between 'Loading Plugin: Buddy' and 'Loading Plugin: RSS'
18097:    Core: 656ms for activity between 'Loading Plugin: RSS' and 'Loading Torrent  5 of 73 : 634D46B4FF9C0D237B4AEA7DFAF1E22CEE3152E0.torrent'
19871:    Core: 1763ms for activity between 'Initialising Global Torrent Manager' and 'Initialising Plugin: Measurement Lab (M-Lab)'
19921:    Core: 36ms for activity between 'Initialising Plugin: Vuze Web Remote' and 'Initialising Plugin: Vuze Feature Manager'
19989:    Core: 77ms for activity between 'Initialising Plugin: Vuze Feature Manager' and 'Initialising Plugin: Azureus Update Support'
20025:    Core: 50ms for activity between 'Initialising Plugin: AzSMRC' and 'Initialising Plugin: NEWS'
DEBUG::Sat Mar 19 16:47:30 CET 2011::org.gudy.azureus2.pluginsimpl.local.PluginInitializer::initialisePlugin::1594:
  java.lang.IllegalArgumentException: Empty key
	at javax.crypto.spec.SecretKeySpec.<init>(SecretKeySpec.java:96)
	at lbms.azsmrc.plugin.main.XMLConfig.loadConfigFile(XMLConfig.java:76)
	at lbms.azsmrc.plugin.main.Plugin.initialize(Plugin.java:148)
	at org.gudy.azureus2.pluginsimpl.local.PluginInitializer$8.run(PluginInitializer.java:1571)
	at org.gudy.azureus2.pluginsimpl.local.utils.UtilitiesImpl.callWithPluginThreadContext(UtilitiesImpl.java:951)
	at org.gudy.azureus2.pluginsimpl.local.PluginInitializer.initialisePlugin(PluginInitializer.java:1561)
	at org.gudy.azureus2.pluginsimpl.local.PluginInitializer.access$400(PluginInitializer.java:59)
	at org.gudy.azureus2.pluginsimpl.local.PluginInitializer$2.run(PluginInitializer.java:1318)
	at org.gudy.azureus2.pluginsimpl.local.PluginInitializer.initialisePlugins(PluginInitializer.java:1497)
	at com.aelitis.azureus.core.impl.AzureusCoreImpl.start(AzureusCoreImpl.java:847)
	at com.aelitis.azureus.ui.swt.Initializer.run(Initializer.java:533)
	at org.gudy.azureus2.ui.swt.mainwindow.SWTThread$7.runSupport(SWTThread.java:274)
	at org.gudy.azureus2.core3.util.AERunnable.run(AERunnable.java:38)
	at java.lang.Thread.run(Thread.java:636)

[alert] Alert:3:Error initializing plugin 'AzSMRC'
DEBUG::Sat Mar 19 16:47:30 CET 2011::org.gudy.azureus2.pluginsimpl.local.PluginInitializer::initialisePlugin::1598:
  java.lang.IllegalArgumentException: Empty key
	at javax.crypto.spec.SecretKeySpec.<init>(SecretKeySpec.java:96)
	at lbms.azsmrc.plugin.main.XMLConfig.loadConfigFile(XMLConfig.java:76)
	at lbms.azsmrc.plugin.main.Plugin.initialize(Plugin.java:148)
	at org.gudy.azureus2.pluginsimpl.local.PluginInitializer$8.run(PluginInitializer.java:1571)
	at org.gudy.azureus2.pluginsimpl.local.utils.UtilitiesImpl.callWithPluginThreadContext(UtilitiesImpl.java:951)
	at org.gudy.azureus2.pluginsimpl.local.PluginInitializer.initialisePlugin(PluginInitializer.java:1561)
	at org.gudy.azureus2.pluginsimpl.local.PluginInitializer.access$400(PluginInitializer.java:59)
	at org.gudy.azureus2.pluginsimpl.local.PluginInitializer$2.run(PluginInitializer.java:1318)
	at org.gudy.azureus2.pluginsimpl.local.PluginInitializer.initialisePlugins(PluginInitializer.java:1497)
	at com.aelitis.azureus.core.impl.AzureusCoreImpl.start(AzureusCoreImpl.java:847)
	at com.aelitis.azureus.ui.swt.Initializer.run(Initializer.java:533)
	at org.gudy.azureus2.ui.swt.mainwindow.SWTThread$7.runSupport(SWTThread.java:274)
	at org.gudy.azureus2.core3.util.AERunnable.run(AERunnable.java:38)
	at java.lang.Thread.run(Thread.java:636)

Error initializing plugin 'AzSMRC' : java.lang.IllegalArgumentException: Empty key
20053:    Core: 26ms for activity between 'Initialising Plugin: NEWS' and 'Initialising Plugin: UPnP Media Server'
20160:    Core: 100ms for activity between 'Initialising Plugin: UPnP Media Server' and 'Initialising Plugin: Tracker Static Pages'
20226:    Core: 67ms for activity between 'Initialising Plugin: Tracker Static Pages' and 'Initialising Plugin: Rating'
20250:    Core: 23ms for activity between 'Initialising Plugin: Start/Stop Rules' and 'Initialising Plugin: Download Remove Rules'
20268:    Core: 11ms for activity between 'Initialising Plugin: Share Hoster' and 'Initialising Plugin: PluginUpdate'
20294:    Core: 14ms for activity between 'Initialising Plugin: Universal Plug and Play (UPnP)' and 'Initialising Plugin: Distributed DB'
20328:    Core: 11ms for activity between 'Initialising Plugin: Distributed Tracker' and 'Initialising Plugin: Magnet URI Handler'
20336:    Core: 19ms for activity between 'Initialising Plugin: Magnet URI Handler' and 'Initialising Plugin: CoreUpdater'
20352:    Core: 14ms for activity between 'Initialising Plugin: External Seed' and 'Initialising Plugin: LAN Peer Finder'
Core Initializing took 4149ms
psDMS 0ms
Analysing /home/seba/azureus/vuze/hs_err_pid990.log
#
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x02a795a0, pid=2701, tid=2744982384
#
# JRE version: 6.0_20-b20
# Java VM: OpenJDK Server VM (19.0-b09 mixed mode linux-x86 )
# Derivative: IcedTea6 1.9.7
# Distribution: Ubuntu 10.10, package 6b20-1.9.7-0ubuntu1
# Problematic frame:
# C  [libGL.so.1+0x6d5a0]  XF86DRIQueryExtension+0x8e
#
# An error report file with more information is saved as:
# /home/seba/azureus/vuze/hs_err_pid2701.log
#
# If you would like to submit a bug report, please include
# instructions how to reproduce the bug and visit:
#   [https://bugs.launchpad.net/ubuntu/+source/openjdk-6/](https://bugs.launchpad.net/ubuntu/+source/openjdk-6/)
# The crash happened outside the Java Virtual Machine in native code.
# See problematic frame for where to report the bug.
#
/home/seba/azureus/vuze/azureus: line 190:  2701 Aborted                 ${JAVA_PROGRAM_DIR}java "${JAVA_ARGS}" -cp "${CLASSPATH}" -Djava.library.path="${PROGRAM_DIR}" -Dsun.java2d.opengl=true -Dazureus.install.path="${PROGRAM_DIR}" -Dazureus.script="$0" $JAVA_PROPS $START_CLASS "$@"
Exit from Azureus complete
No shutdown tasks to do
Azureus TERMINATED.
seba@seba-laptop:~$ ~~~~~~


Any idea?

---

### Post by Nixblicker on 2011-03-31
Hey guys, 

all of you having trouble to apply this switch, should probably better first check the JRE you are actually using. It doesn't make too much sense to start a deviating environment with a sun JRE specific switch, does it?

@mer0090

This  for example indicates, you are using OpenJDK instead of sun JRE

> **mer0090 said:**
> 
Analysing /home/seba/azureus/vuze/hs_err_pid990.log
#
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x02a795a0, pid=2701, tid=2744982384
#
[B]# JRE version: 6.0_20-b20
# Java VM: OpenJDK Server VM (19.0-b09 mixed mode linux-x86 )
# Derivative: IcedTea6 1.9.7[/B]
# Distribution: Ubuntu 10.10, package 6b20-1.9.7-0ubuntu1
# Problematic frame:
# C  [libGL.so.1+0x6d5a0]  XF86DRIQueryExtension+0x8e
#
# An error report file with more information is saved as:
# /home/seba/azureus/vuze/hs_err_pid2701.log
#
# If you would like to submit a bug report, please include
# instructions how to reproduce the bug and visit:
#   [https://bugs.launchpad.net/ubuntu/+source/openjdk-6/](https://bugs.launchpad.net/ubuntu/+source/openjdk-6/)
# The crash happened outside the Java Virtual Machine in native code.
# See problematic frame for where to report the bug.
#


So better install Sun JRE in order to use this tweak.
For example, you could execute these commands in a console:
```
sudo add-apt-repository "deb http://archive.canonical.com/ lucid partner"
sudo apt-get update
sun-java6-bin & sun-java6-jre
```

If you already did, and still having  OpenJDK taking over, you can change the default JRE choice of Ubuntu with the command:
"sudo update-alternatives --config java"

Hope that helps,
Cheers, Nix

---

### Post by OzzyFrank on 2012-03-07
Hi all. I see things have great changed since this thread started, so I'd like to check what the latest instructions would be, using Vuze 4.7.0.2 in Ubuntu 11.10 (64-bit), with both Sun Java (just before the very latest version) and OpenJDK (latest) installed, with the script looking like:

#!/bin/sh

# Include java-wrappers
. /usr/lib/java-wrappers/java-wrappers.sh

JAVA_CLASSPATH="/usr/lib/jni:/usr/lib/java"
VUZE_BIN="/usr/bin/vuze"

find_java_runtime openjdk sunmin5

find_jars Azureus2 log4j-1.2 commons-cli swt

if [ ! -x $VUZE_BIN ]; then
	UI=-Dforce.ui=az2
fi

run_java -Dazureus.install.path="$HOME/.azureus" $UI \
    org.gudy.azureus2.ui.common.Main "$@"


Many thanks in advance - this unresponsiveness in Vuze that started recently with an update (I assume to Java) is driving me nuts. [EDIT: OK, turns out I only have OpenJDK, so Sun's Java was obviously uninstalled at some point, probably the last upgrade. Sun's website just told me a later version was available, not that it wasn't installed on my system. So do I uninstall OpenJDK, and will that have unwanted consequences with programs relying on it?]

---

