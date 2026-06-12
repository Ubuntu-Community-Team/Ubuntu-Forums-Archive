---
title: "ALEKS will work on Ubuntu"
date: 2007-08-17
forum: Tutorials
---

### Post by 56phil on 2007-08-17
Hi all,

Many of you are headed to school this month. Some portion of you will be asked to use a CBI program for math called ALEKS. ALEKS does not support Linux, but the program will work on Ubuntu. 

ALEKS requires a Java plug-in called aleksPack10.jar which must be manually downloaded and installed on Linux. The page describing the process on ALEKS is barely helpful. Here's what worked for me:
```

sudo cp aleksPack10.jar /usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/ext/

```

Hope this will save you a few hours looking for the right directory.

---

### Post by wombatbob on 2007-08-30
You just saved me from installing Windows just for my accounting class.  Thank you.:):):)

---

### Post by holmes85 on 2008-01-16
still didn't work for me i copied the .jar to that folder only its version .03 not .00

any help? please

---

### Post by holmes85 on 2008-01-16
i'm using kazehakase to access aleks it works. i guess.

---

### Post by jagler1234 on 2008-02-07
I have moved the plugin and Aleks runs, but the keyboard imput is not always taken.  If I try to enter a number sometime the information does not go in.

Can any one help?

On a Dell Otiplex 260 P-4 at 2.4 1 gig and Ubuntu 7.10.

---

### Post by NWcustomcode on 2008-03-25
Thanks for posting this tip! I have aleks up and working now. The only other thing I had to do was reboot firefox and clear my browser cache.

The browser cache is under edit -> preferences-> advanced -> network-> clear now

---

### Post by shanerdaner on 2008-04-08
what folder do I put the file in I get the error 
cp: target `/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/ext/' is not a directory: No such file or directory

thanks!!

---

### Post by NWcustomcode on 2008-04-26
> **jagler1234 said:**
> I have moved the plugin and Aleks runs, but the keyboard imput is not always taken.  If I try to enter a number sometime the information does not go in.

Can any one help?

On a Dell Otiplex 260 P-4 at 2.4 1 gig and Ubuntu 7.10.


To solve the problem of being unable to input answers open the java console and clear the classpath by hitting x.

Have fun!!

---

### Post by NWcustomcode on 2008-04-26
I posted a thread for those who are upgrading to 8.04 and need to use Aleks
[http://ubuntuforums.org/showthread.php?t=768874&referrerid=537709]("http://ubuntuforums.org/showthread.php?t=768874&referrerid=537709")

---

### Post by NWcustomcode on 2008-04-26
> **shanerdaner said:**
> what folder do I put the file in I get the error 
cp: target `/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/ext/' is not a directory: No such file or directory

thanks!!

Open a shell and type 

locate lib/ext

Here is my some sample output that you may see

/usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/ext
/usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/ext/aleksPack10.jar
/usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/ext/dnsns.jar
/usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/ext/localedata.jar
/usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/ext/meta-index
/usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/ext/sunjce_provider.jar
/usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/ext/sunpkcs11.jar

replace java-6-sun-1.6.0.00 with what shows on your system.

---

### Post by OmikronZeta on 2009-04-29
> **NWcustomcode said:**
> Open a shell and type 

locate lib/ext

Here is my some sample output that you may see

/usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/ext
/usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/ext/aleksPack10.jar
/usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/ext/dnsns.jar
/usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/ext/localedata.jar
/usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/ext/meta-index
/usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/ext/sunjce_provider.jar
/usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/ext/sunpkcs11.jar

replace java-6-sun-1.6.0.00 with what shows on your system.

When I type   locate lib/ext   I get this:

```
/usr/lib/python2.5/idlelib/extend.txt
```What does that mean?

---

### Post by undeadboe on 2009-06-28
thanks a lot! I almost had to go back to using windows. Saved me quite a bit of trouble.:p

---

### Post by dgriffin on 2009-08-06
> **56phil said:**
> Hi all,

Many of you are headed to school this month. Some portion of you will be asked to use a CBI program for math called ALEKS. ALEKS does not support Linux, but the program will work on Ubuntu. 

ALEKS requires a Java plug-in called aleksPack10.jar which must be manually downloaded and installed on Linux. The page describing the process on ALEKS is barely helpful. Here's what worked for me:
```

sudo cp aleksPack10.jar /usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/ext/

```

Hope this will save you a few hours looking for the right directory.
I used this code and a message comes up "cannot stat 'aleksPack10.jar': No such file or directory"  I have the file on my desktop.  does it need to be somewhere else?  I pretty new at using the terminal, please help!

---

### Post by iiretepii on 2009-11-01
> **dgriffin said:**
> I used this code and a message comes up "cannot stat 'aleksPack10.jar': No such file or directory"  I have the file on my desktop.  does it need to be somewhere else?  I pretty new at using the terminal, please help!

if it is on your desktop type after cp type "~/Desktop/aleksPark10.jar"  The "~" is a shortcut for your home directory.  So the whole command line would be 
sudo cp ~/Desktop/aleksPack10.jar /usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/ext/ 
another thing that I ran into was that my java was a different version.  So find out the version of java that you're running and change the name of the directory.. for example I had to type "/usr/lib/jvm/java-6-sun-1.6.0.16/jre/lib/ext"

I'm running Karmic.  I thought I'd add something because it looked like you added this aug 09.  I hope I replied in time.  VIVA EL UBUNTU!
------------------------------------------
Gateway Intel Express Chipset 945, 4GB RAM, Ubuntu 9.10 Karmic Koala

---

### Post by jackechanprime on 2010-09-11
I've been making the rounds on the forums with my aleks related problem, here it is:

************
K, now i've got a new problem for you...

Aleks fully installed and "functional."
Program is loading and initializing smoothly, program comes online and is (apparently) completely operational... HOWEVER...

The actual problem interfaces (as it's a math homework program, it has interfaces where you input your final answer as well as "buttons," which are some form of script link, for getting explanations as well as other basic GUI functions within the program (back, next, done, etc.). THESE SCRIPTS ARE NOT RUNNING. The result is that when i attempt to actually perform the point of the program and solve a homework problem, I CANNOT ACTUALLY ANSWER IT. not only that, but even if i could answer it, without the "done" button rendering, i cannot actually submit my answer!

Ask anything you need to know, and i'll tell you.

ubuntu 10.04, firefox 3.--something (latest), jre6 (reinstalled literally yesterday, so should be the latest version, most importantly, jre IS working.)

Any help GREATLY appreciated. like everyone else who seems to be having this problem, if i cant get ALEKS running right, i automatically fail this math course.
***********

please and thank you!
obviously need help!

---

### Post by jackechanprime on 2010-09-13
Nevermind, whatever kink it was worked itself out. No idea what did it, but it works now. Didn't even do a system update and the glitch is gone. Totally stumped, but oh well.

thanks anyway.
~Q

---

### Post by PSmall04901 on 2011-01-26
For Ubuntu 10.04 I used the following line to get the Aleks Plugin to work:

sudo cp aleksPack10.jar /usr/lib/jvm/java-6-sun-1.6.0.22/jre/lib/ext/

---

### Post by Turmoyl on 2011-08-28
> **PSmall04901 said:**
> For Ubuntu 10.04 I used the following line to get the Aleks Plugin to work:

sudo cp aleksPack10.jar /usr/lib/jvm/java-6-sun-1.6.0.22/jre/lib/ext/

Thanks, PSmall04901! This was driving me batty, because java-6-sun-1.6.0.26 has two ext directories. Moving it to the one under jre/lib did the trick.

---

### Post by ainsaur on 2011-09-05
I tried these instructions but I get the following message:

cp: cannot create regular file `/usr/lib/jvm/java-6-sun-1.6.0.20/jre/lib/ext/': No such file or directory

I am using Ubuntu 10.10

Thanks, in advance, for your help!

---

### Post by WSiaB on 2011-11-14
Awesome, awesome, awesome!!!  One would think a college software company would know to support Linux, but whatever.  Works great on my Mint system.
```
sudo cp aleksPack10.jar /usr/lib/jvm/java-6-sun-1.6.0.26/jre/lib/ext/
```
Everyone should browse to /usr/lib/jvm/ to see what version of the JVM you are running to be sure you don't get the directory not found message.

Those who have commented on problems inputing answers, etc.  I was having the same problems with Windows, I think it is a problem with their Java coding (try clearing your cache, it seemed to help).

---

