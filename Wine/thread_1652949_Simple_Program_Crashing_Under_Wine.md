---
title: "Simple Program Crashing Under Wine"
date: 2010-12-25
forum: Wine
---

### Post by le sigh on 2010-12-25
Hi everyone! I am a new lover of Ubuntu and am currently experiencing difficulties trying to get a program I need for school running via Wine. I currently run WoW from Wine and it works flawlessly, but yet this simple logic program will consistently crash, and being new to Ubuntu I have no idea where to start troubleshooting. 

[http://logic2k.humnet.ucla.edu/download.cfm](http://logic2k.humnet.ucla.edu/download.cfm) This is the website in which the logic program is downloaded, although in order to actually run the program a name and password assigned by the prof. is needed. The program needs Java Virtual Machine to run, which I downloaded from here [http://logic2k.humnet.ucla.edu/remote/msjavx86.exe](http://logic2k.humnet.ucla.edu/remote/msjavx86.exe)

I can install and open the program fine, but when I choose problems to work on the program seizes and I have to force quit. I NEED this to work on my laptop, I have no idea how to start looking for the problem let alone fixing it. If anyone could offer me any advice it would be much appreciated! 
[]("http://logic2k.humnet.ucla.edu/remote/msjavx86.exe")

---

### Post by flakzeus on 2010-12-26
Is there any reason you can't run it via Java instead of through wine->java->program?

---

### Post by le sigh on 2010-12-26
No, I was actually unaware that it existed until you mentioned it haha. The only reason I downloaded JVM was because the website mentioned it. Does this come with wine? Do I have to uninstall JVM or can I just reinstall the one you mentioned? I can't seem to find an uninstall file for JVM.

---

### Post by dino99 on 2010-12-26
[http://wiki.jswindle.com/index.php/Java](http://wiki.jswindle.com/index.php/Java)

[http://forum.winehq.org/viewtopic.php?p=47908](http://forum.winehq.org/viewtopic.php?p=47908)

---

### Post by le sigh on 2010-12-31
Thank you for the help. After reading the links I downloaded the .bin version of Java referenced in the information provided, but my program is still crashing although only when I try to select a problem to derive. 

It seems the program is freezing only when asked to retrieve information which strikes me as a Java issue, although as we've already covered I'm far from an expert. Could it be the version of Java I installed initially with Wine? Maybe I have to remove it? All instructions I can find online for uninstalling JVM involve the Run command, and I can't seem to find that within Wine. Can anyone offer me more suggestions?

---

### Post by le sigh on 2011-01-01
On the suggestion of a friend, I removed all Windows programs from Wine and reinstalled the Logic program without JVM. The program refuses to open at all now, a step back from JVM in which it would open but stop responding once the program was prompted to retrieve information. *edit* I still have the version of Java installed that was recommended in the links above.

---

