---
title: "CGI files in DOS format error"
date: 2010-04-10
forum: Server Platforms
---

### Post by three-eared-jack on 2010-04-10
Hi,
I'm just replacing my old Ubuntu LAMP server with a new one using 8.04.
 
Something I've noticed that is different from any other server I'm using (Ubuntu or otherwise) is that cgi files that have been saved in DOS format give the error 
 
[FONT=Courier New, monospace][SIZE=2]"(2)No such file or directory: exec of '/.../../x.cgi' failed"[/SIZE][/FONT]

In other servers the DOS format file is executed anyway.
 
Does anyone know where sensitivity to this is configured, or is it an immutable change? 
Obviously I realise I could change any cgi files to unix format, but this is a test server and I want to duplicate the behaviour of other sites for debugging purposes.
Any info welcome.
J

---

### Post by three-eared-jack on 2010-04-10
This happens when the shebang line (#!/usr/bin/perl) has a DOS CRLF at the end instead of just newline. Anyone know what happens to the shebang line?

---

### Post by EndorphinE on 2010-08-15
You will be able to prevent this issue if you will add the incorrect parameter to the Shebang line for example:

#!/usr/bin/perl -w

Then in DOS format it will be like the following:

#!/usr/bin/perl -w^M
but the script will still work because -w parameter is not correct :D

---

