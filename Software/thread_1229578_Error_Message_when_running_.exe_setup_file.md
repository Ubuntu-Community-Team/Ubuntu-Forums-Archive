---
title: "Error Message when running .exe setup file"
date: 2009-08-02
forum: Software
---

### Post by maryfay on 2009-08-02
[FONT=Comic Sans MS][SIZE=2]I need to run MYOB but have removed Windows and installed Ibuntu on my laptop and also downloaded Win4Lin Pro, as I really need to run executable (.exe) files but want to keep Ibuntu as it is so fast. When I try to run myob.exe I get the following error message:

cannot find zipfile directory in one of /home/mf/Desktop/MYOB Premier v12 Test Drive.exe or
          /home/mf/Desktop/MYOB Premier v12 Test Drive.exe.zip, and cannot find /home/mf/Desktop/MYOB Premier v12 Test Drive.exe.ZIP, period.

Is there a way to be able to run my .exe files with Ibuntu.

thanks in anticipation[/SIZE][/FONT]
[FONT=Comic Sans MS][SIZE=3]Mary[/SIZE][/FONT]

---

### Post by imbjr on 2009-08-02
You need to install wine first, but you may find that your windows software will not work as well.

---

### Post by Marlonsm on 2009-08-02
There is a way, but it's not perfect yet.

It's called Wine.
Go to Applications > Add/Remove...
look for Wine and install "Wine Microsoft Windows Compatibility Layer"
After it's installed, right click the file and you'll have the option to run it with Wine.

As I've said, it's not perfect yet, so it won't run everything flawlessly, but it's worth a try.

---

### Post by ljerabek on 2009-08-02
Mary,

You will not be able to run the exe natively in Linux. Linux is not Windows and has a different executable format. However there are a few way around that using WINE. You can use "Synaptic Package Manager" and do a quick search for "wine". Install the wine package after you have wine installed you can run many windows\dos exe files. For additional wine information you can go to  [http://www.winehq.org/](http://www.winehq.org/) . You should be able to fine more usage information for wine. 

Regards,

Lu

---

### Post by maryfay on 2009-08-02
Thank you so much, have found the download and installed.  Mary

---

### Post by maryfay on 2009-08-02
Thank you Lu, much appreciated.  Mary

---

### Post by maryfay on 2009-08-02
Your reply is much appreciated, I am totally new to Ibuntu but really loving it.  If I can successfully get exe files to work then my laptop is more valuable to me as Windows just crashes continually.  Mary

---

### Post by steveneddy on 2009-08-02
You know - just FYI - there is always running ''windows in a Virtual Machine.

VirtualBox is a good alternative to either dual booting or Wine.

I use Wine and VirtualBox and find myself preferring Vbox.

---

### Post by dark_religion on 2009-11-13
Thank you for useful replies.

---

### Post by nopersona on 2009-11-13
[Ubuntu Forums]("http://ubuntuforums.org/index.php")  	> [The Ubuntu Forum Community]("http://ubuntuforums.org/forumdisplay.php?f=130")   	> [Other Community Discussions]("http://ubuntuforums.org/forumdisplay.php?f=125")   	> [Ubuntu LoCo Team Forums]("http://ubuntuforums.org/forumdisplay.php?f=183")   	> [International LoCo Teams]("http://ubuntuforums.org/forumdisplay.php?f=246")   	> **[COLOR=Red][Chile Team]("http://ubuntuforums.org/forumdisplay.php?f=362")[/COLOR]****[COLOR=Red] [/COLOR]**  	> [Software]("http://ubuntuforums.org/forumdisplay.php?f=365")

:P

---

