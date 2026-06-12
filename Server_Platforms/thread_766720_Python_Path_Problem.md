---
title: "Python Path Problem"
date: 2008-04-25
forum: Server Platforms
---

### Post by Wamoc on 2008-04-25
Ok, I recently setup a LAMP server running Gutsy and am having some problems with python on it. My scripts are set as executable and I thought I had the python path set up correctly on the first line. I can invoke the scripts by calling python (filename) directly, but running them straight I get an error that says (path): bad interpreter: No such file or directory. 
I look at where the script says the path is and python is there. I might be having it look at the wrong spot, but can anyone tell me what my path should be? These scripts will be run as cgi scripts, so they have to be able to run without telling the interpreter to run it (I did install the apache module).

---

### Post by Wamoc on 2008-04-25
Just as a quick clarification, I have even tried /usr/bin/env python for the path.

---

### Post by godsmoke on 2008-04-25
Are you, by any chance, using another OS to edit the python files (such as Windows or Mac OS X)?  If so, it's likely that Linux is misinterpreting the carriage return from those operating systems, and causing a failure to find the interpreter.  Try editing the shebang line (that's the '#!/usr/bin/env python' line) and the line after it (to make sure that the carriage return isn't there) in a native Linux text editor such as nano or vi.

---

### Post by Wamoc on 2008-04-25
Ok, that was my problem. The file was originally on a windows machine. I was not thinking, thank you.

---

