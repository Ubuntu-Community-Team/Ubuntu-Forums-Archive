---
title: "Startup script to run python script"
date: 2011-02-10
forum: Server Platforms
---

### Post by Manaughl on 2011-02-10
I am rather new to Ubuntu server but have long time experience in Microsoft server admin world. 
I need to run a python script once at boot.
I am not clear on how to do this and have been looking for good examples for Ubuntu server 10.10

My python script will listen for traffic coming in on a particular port. It works fine if I start it manually in a ssh session. But I need it to run as though it were a service and start at boot.

How do I do this on an Ubuntu 10.10 server? I would like the crayola crayon version of the instructions.
If I have to create a bash script that goes into rc.local I will need a bit of guidance on that as well.

Any information would be greatly appreciated.
thanks

---

### Post by mymiasma on 2011-03-29
Quick answers:
[http://ubuntuforums.org/showthread.php?t=1046139](http://ubuntuforums.org/showthread.php?t=1046139)
[http://embraceubuntu.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/](http://embraceubuntu.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/)

Treat your Python script the same as if it were a bash script and don't forget to include the shebang, > #!/usr/bin/python as the first line of your python scripts to run on *nix platforms.

Even if your question is answered by the above links you should also read the following longer answers:
[http://catb.org/~esr/faqs/smart-questions.html](http://catb.org/~esr/faqs/smart-questions.html)
[http://www.chiark.greenend.org.uk/~sgtatham/bugs.html](http://www.chiark.greenend.org.uk/~sgtatham/bugs.html)

If you are asking such a basic question and basically asking to be spoon fed with a crayon level of help you may want to refrain from mentioning any long time experience as a Micro$oft server admin. The open source community has a very different culture from those surrounding proprietary systems and since all the source code is freely available the code itself is considered the ultimate reference material. The community generates revenue mostly through the sale of bundled systems and various forms of technical support and not by selling the code itself. Folks capable of answering your question may tend to view it as going out of their way to tutor a potential rival. That said, there is still plenty of higher level documentation available through a well crafted Google search.

Please don't take the above comments the wrong way. The open source community is generally very welcoming of anyone turning away from the dark side. However, they do generally expect anyone joining it to do their homework before asking them to take their time and trouble answering.

Good luck, may the source be with you.:)

---

