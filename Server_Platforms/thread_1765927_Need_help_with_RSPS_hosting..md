---
title: "Need help with RSPS hosting."
date: 2011-05-23
forum: Server Platforms
---

### Post by Ghatii on 2011-05-23
Okay, so I'm new to Ubuntu or linux in general. I have no idea how to get my runserver.bat to work. 

What I have tried:

1.) Using Wine to right click and say open with windows program loader. 
All this does is show a black screen (the windows cmd screen). 
It doesn't show "loading server" or any of the messages.

2.) I have also tried copying it and changing it into a .sh file.. 

Am I doing something wrong, or is there more to it? Please help me. 
I really need my server back online. :(

Codes in Executables:
Run.bat
```
@echo off 
color 0a 
title Project Insanity 
java -Xmx800m -cp bin;deps/poi.jar;deps/mysql.jar;deps/mina.jar;deps/slf4j.jar;deps/slf4j-nop.jar;deps/jython.jar;log4j-1.2.15.jar; server.Server 
pause
```run.sh
```
#!/bin/bash
title "Ghatii Pkz"
java -Xmx800m -cp bin;deps/poi.jar;deps/mysql.jar;deps/mina.jar;deps/slf4j.jar;deps/slf4j-nop.jar;deps/jython.jar;log4j-1.2.15.jar; server
read
```

---

