---
title: "Virus UNIX.Penguin Detected in Repository"
date: 2009-03-25
forum: Security
---

### Post by tlutz on 2009-03-25
I recently used apt-mirror to grab the repositories for Dapper (6.06 LTS) and for Intrepid (8.04 LTS).  I ran a virus scan on the entire 80 gigs of stuff and Symantic found a security risk known as "Unix.Penguin" inside the Cappuccino package (version 0.5.something).  Supposedly this security risk is a shell script that attempts to e-mail password databases etc.  Can someone confirm that this threat exists or provide a reasonable explanation as to why this was detected as a threat?

Thank you,
Tom

---

### Post by mikewhatever on 2009-03-26
Could be a false positive for example. Try a couple of online scanners on that package to confirm.
As an after thought, I wonder what virus scanner did you use, and are there any with data bases for Linux.

---

### Post by aos101 on 2009-03-26
> **tlutz said:**
> Can someone confirm that this threat exists or provide a reasonable explanation as to why this was detected as a threat?

Thank you,
Tom
I think as said above it is a false positive.  Line 25 of compileline.grm in the source package for the program contains this command which is probably what causes Symantec to complain:
```
cat /etc/passwd | mail president@whitehouse.gov
```
But I don't think it executes that code at all. The compileline.grm file contains lots of possible commands and parts of commands that are then put together to come up with random commands, which the program then displays on the screen to make it look like you are doing work (as you can see in the attached screenshot).

I assume Symantec just searches files for commands similar to the one above, and just assumes it's a virus regardless of context (it doesn't understand that the command is just a text string that doesn't get executed).

---

### Post by tlutz on 2009-03-26
Thanks for the prompt responses.  Symantec did detect the 'risk' in the 'compileline.grm' file, so I think you are right about line 25.

Cheers,
Tom

---

### Post by koenn on 2009-03-26
> **aos101 said:**
> 
I assume Symantec just searches files for commands similar to the one above, .
Your assumption is correct. Symantec defines Unix.Penguin as "a shell script that mails out the passwd file". A text file probably qualifies as shell script, so it fits their definition.

Their recommended cure is "delete the shell script"  :)

[http://www.symantec.com/security_response/writeup.jsp?docid=2001-041803-0917-99](http://www.symantec.com/security_response/writeup.jsp?docid=2001-041803-0917-99)

---

