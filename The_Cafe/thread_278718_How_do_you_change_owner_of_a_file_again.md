---
title: "How do you change owner of a file again?"
date: 2006-10-16
forum: The Cafe
---

### Post by user1397 on 2006-10-16
i'm having a mind blank!  i forgot how to chown something, man chown didn't help me much.  for example, i have a file on my desktop thats owned by root (dont worry i made the file myself, its perfectly safe).  so i want to do a chown with 777 permissions, what's the correct format for that?

---

### Post by ComplexNumber on 2006-10-16
> **erik1397 said:**
> i'm having a mind blank!  i forgot how to chown something, man chown didn't help me much.  for example, i have a file on my desktop thats owned by root (dont worry i made the file myself, its perfectly safe).  so i want to do a chown with 777 permissions, what's the correct format for that?

you use chmod and chown for that. first put sudo chown erik1397:erik1397 MyFile. then use chmod 777 MyFile. the 1st changes the perssions so that you're the owner. the second changes the permissions.

---

### Post by user1397 on 2006-10-16
o alright thanks, that worked for me.

---

### Post by ComplexNumber on 2006-10-16
> **erik1397 said:**
> sorry if i made a stupid comment, but actually i wanted to change ownership of the file.
thats what the above does. you first need to change the owner of the file. i'm assuming that you want to change  the ownership of it too. if not, just put "sudo" before chmod instead of doing both.

---

### Post by user1397 on 2006-10-16
> **ComplexNumber said:**
> thats what the above does. you first need to change the owner of the file. i'm assuming that you want to change  the ownership of it too. if not, just put "sudo" before chmod instead of doing both.yea sorry, i did not see your edit above fast enough.

---

### Post by ComplexNumber on 2006-10-16
> **erik1397 said:**
> yea sorry, i did not see your edit above fast enough.
thats ok :). let me know if it does what you want. 777 will make it readable, writable, and executable for everyone.

---

### Post by user1397 on 2006-10-16
> **ComplexNumber said:**
> thats ok :). let me know if it does what you want. 777 will make it readable, writable, and executable for everyone.i did what i wanted
i just made it read & write for me, read only for everyone else, non -executable.  i dont know what number that translates to, i just used the gui to do it.

---

### Post by ComplexNumber on 2006-10-16
> **erik1397 said:**
> i did what i wanted
i just made it read & write for me, read only for everyone else, non -executable.  i dont know what number that trnslates to, i just used the gui to do it.
use 700 for that. 

EDIT: sorry, no its not. 700 is to make it readable, writable, and executable only for the owner. i would have to work it out, but i only use permissions 700 and 755

---

### Post by Bloodfen Razormaw on 2006-10-16
It is 644.

Learn binary, at least just up to 7, and it is easy.  7 is three digits in binary, 111.  Each digit corresponds to read, write, and execute, respectively.  If it is one, it is on, if it is zero, off.  Change it to 6, 110, and you only have a 1 on read and write.  So it is read/write but not executable.  4 is 100, so it is read, but not write or execute.

Then do that three times.  The first number for the owner, second for the group, third for everyone.  So 644 becomes 110 for owner, 100 for group, and 100 for everyone.  So you get:

[FONT="Lucida Console"]
_____ |_ r w e_
Owner | 1 1 0
Group | 1 0 0
All__ | 1 0 0
[/font]

---

### Post by ComplexNumber on 2006-10-16
> **Bloodfen Razormaw said:**
> It is 644.

Learn binary, at least just up to 7, and it is easy.  7 is three digits in binary, 111.  Each digit corresponds to read, write, and execute, respectively.  If it is one, it is on, if it is zero, off.  Change it to 6, 110, and you only have a 1 on read and write.  So it is read/write but not executable.  4 is 100, so it is read, but not write or execute.

Then do that three times.  The first number for the owner, second for the group, third for everyone.  So 644 becomes 110 for owner, 100 for group, and 100 for everyone.  So you get:

[FONT=Lucida Console]
_____ |_ r w e_
Owner | 1 1 0
Group | 1 0 0
All__ | 1 0 0
[/FONT]
permissions are octal (base 8 ), not base 2. although its easy to convert between the 2 by taking each group of 3 binary digits. don';t forget that the last bit determines if its a file or a directory.

---

### Post by user1397 on 2006-10-17
yes i knew about how the file permission system worked, i just forgot the conventions for the chown and chmod commands, or in other words, i forgot how to write them correctly.
\thanks for all the help tho.

---

### Post by Bloodfen Razormaw on 2006-10-17
> permissions are octal (base 8 ), not base 2. although its easy to convert between the 2 by taking each group of 3 binary digits. don';t forget that the last bit determines if its a file or a directory.
It is presented to the user as an octal number of three digits but the system handles it as a nine digit binary number.  Retrieving the status of r/w/e is a bit masking operation.  Thinking of permissions in binary makes it easy to find out what the octal representation until the octal becomes second nature.

---

### Post by ComplexNumber on 2006-10-17
> **Bloodfen Razormaw said:**
> It is presented to the user as an octal number of three digits but the system handles it as a nine digit binary number.  Retrieving the status of r/w/e is a bit masking operation.  Thinking of permissions in binary makes it easy to find out what the octal representation until the octal becomes second nature.
its a 10 digit number. the last bit defines if its a directory or a file.

---

### Post by Bloodfen Razormaw on 2006-10-17
The ls listings make it look like a bit, but it actually is not.  There are 12 standard POSIX bits.  The 3 beyond the standard permissions are for sticky, suid, and gid.

---

### Post by ComplexNumber on 2006-10-17
> **Bloodfen Razormaw said:**
> The ls listings make it look like a bit, but it actually is not.  There are 12 standard POSIX bits.  The 3 beyond the standard permissions are for sticky, suid, and gid.
they're additional 'special' bits. there are 10 bits in the standard file permissions value. the reason for your wrong info is because you're getting your info from konqueror(which doesn't give all the info).

---

### Post by Bloodfen Razormaw on 2006-10-17
I'm getting my information from the POSIX specifications.  I'm not sure who told you directories were a file permission, but they were wrong.  If you want further verification you can look at the Linux source code, or even the chmod() man page, which discusses file permissions.

---

### Post by ComplexNumber on 2006-10-17
> **Bloodfen Razormaw said:**
> I'm getting my information from the POSIX specifications.  I'm not sure who told you directories were a file permission, but they were wrong.  If you want further verification you can look at the Linux source code, or even the chmod() man page, which discusses file permissions.
thats because you arer misunderstanding it. 
> There are many ways by which Unix permission schemes are represented. The most common form is **symbolic notation**. This scheme represents permissions as a series of 10 characters.[http://en.wikipedia.org/wiki/File_system_permissions](http://en.wikipedia.org/wiki/File_system_permissions)

> 
The first column contains 10 bit positions which describe the permissions for the file.  The first bit is defined  as follows[http://www.usc.edu/its/doc/os/unix/commands/permfile_dir.html](http://www.usc.edu/its/doc/os/unix/commands/permfile_dir.html)



> 
When a long file listing is done, there are 10 characters that are shown on the left that indicate type and permissions of the file. File permissions are shown according to the following syntax example: drwerwerwe
There are a total of 10 characters in this example, as in all Linux files.
[http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilesp.html](http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilesp.html)





and many many other sources.






the syntax for file permissions is as follows:
drwxrwxrwx
FACT!
see screenshot below (list files by using "ls -l"):

---

### Post by Bloodfen Razormaw on 2006-10-17
Why reference Wikipedia when Wikipedia confirms you are incorrect?  It clearly states that the d in the ls listing is for showing file type, not permissions.  And your screenshot just proves I was right that you are just confused by the ls listing.  Are there bits for all of these? No.  POSIX states very clearly that in addition to the permission bits there are only S_ISUID, S_ISGID, and S_ISVTX.  This is confirmed in the Single UNIX Specification.

I want you to do something ComplexNumber.  Go to /dev and type ls -l.  See all those c's in the permissions display?  I want you to tell me how that fits into your 10-bit theory.  No make a symbolic link.  Type ls -l.  See that l?  How does that fit into your 10-bit theory?

---

### Post by ComplexNumber on 2006-10-17
> **Bloodfen Razormaw said:**
> Why reference Wikipedia when Wikipedia confirms you are incorrect?  It clearly states that the d in the ls listing is for showing file type, not permissions.  And your screenshot just proves I was right that you are just confused by the ls listing.  Are there bits for all of these? No.  POSIX states very clearly that in addition to the permission bits there are only S_ISUID, S_ISGID, and S_ISVTX.  This is confirmed in the Single UNIX Specification.

I want you to do something ComplexNumber.  Go to /dev and type ls -l.  See all those c's in the permissions display?  I want you to tell me how that fits into your 10-bit theory.  No make a symbolic link.  Type ls -l.  See that l?  How does that fit into your 10-bit theory?
there are 10 bits used to describe a file, and thats a fact. i have just gone to /dev...and lo and behold, there are 10 bits to describe the file. the 'c' indicates "c= character (unbuffered) device file special", and the 'l' is "l = symbolic link".
 see screenshot below. you need to wise up, fella.

---

### Post by Bloodfen Razormaw on 2006-10-17
> there are 10 bits used to describe a file, and thats a fact. i have just gone to /dev...and lo and behold, there are 10 bits to describe the file. the 'c' indicates "c= character (unbuffered) device file special".
Are you claiming that the characters "-", "d", and "c", AND "l" can ALL be referenced with ONE bit?  Please, explain to us how we can reference four things with only two different values.  According to your logic, in which file types are held in the permissions (even though your claim has already been countered by Wikipedia, the Linux source, and the POSIX and Single Unix Specifications), that would require 11 bits.  Add in "p" and you need 12 bits.  How many bits are you claiming there are now?

---

### Post by ComplexNumber on 2006-10-17
> **Bloodfen Razormaw said:**
> Are you claiming that the characters "-", "d", and "c", AND "l" can ALL be referenced with ONE bit?  Please, explain to us how we can reference four things with only two different values.  According to your logic, in which file types are held in the permissions (even though your claim has already been countered by Wikipedia, the Linux source, and the POSIX and Single Unix Specifications), that would require 11 bits.  Add in "p" and you need 12 bits.  How many bits are you claiming there are now?
i really have no idea what you are going on about there. i don't think anybody else does either. there seems to be a lot that you're misundderstanding about the facts, so maybe you'd better start at the beginning. and my claim has not been countered by wikipedia or any of the others - quite the opposite in fact. anyway, the facts and screenshots are there. its up to you to now understand them properly. there are 10 chars used to describe a file. FACT. see below. i'll now leave it up to you to come to terms with the fact that you're wrong.....
> Type field:  The first character in the field indicates a file type of one of the following:[LIST]
[*]d = directory
[*]l = symbolic link
[*]s = socket
[*]p = named pipe
[*]- = regular file
[*]c= character (unbuffered) device file special
[*]b=block (buffered) device file special[/LIST][http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilesp.html](http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilesp.html)

---

### Post by Bloodfen Razormaw on 2006-10-17
> my claim has been countered by wikipedia.
Even your quote shows that the first character is the file type, not the permissions.  It backs me up 100%.

You've done nothing but talk about what ls prints out, and completely ignored the issue of actual permissions, even after countless sources rebuke you (perhaps you should reread APUA?).  Allow me to educate you straight from the POSIX specs.  Each file type has a mode.  The mode is contained of two pieces of information.  One is the file type, which is four bits long.  In Linux 1100 is s, 1010 is l, 1000 is -, 0110 is b, 0100 is d, 0010 is c, and 0001 is p.  This is followed by file permissions.  File permissions are 12 bits, starting with suid, gid, then sticky, followed by the rwx bits for owner, then group, then world.  The security subsystem specifically only exposes the 12 permission bits as permissions.  chmod only exposes the 9 for the rwx, plus suid, gid, and sticky (read chmod(2) yourself if you like).  You are confused because ls prints out the mode, not just permissions.  *MODE* includes information on file type (in 4 bits, not 1; it makes no sense for you to claim there is one bit for file information that can hold more than 2 file types), while permissions does not.

---

### Post by ComplexNumber on 2006-10-17
you haven't read anything that i've said, or understood it. how many times do you need telling. in fact, i think i know why you have misunderstood all along. you must be thinking in terms of *binary* bits, whereas i'm not. thats not how it works. well, not in this case anyway.  in other words:
>                               The first column contains 10 bit positions which describe the permissions for the file.hopefully you understand now because its taken you long enough.

---

### Post by Bloodfen Razormaw on 2006-10-17
> in fact, i think i know why you have misunderstood all along. you must be thinking in terms of binary bits. that's not how it works
Uhh, yes, that is how it works.  You know how you can tell that permissions are based on binary bits?  *Because there is no other type of bit.*  Bit stands for "**binary** digit."  The idea of a non-binary binary digit is absurd.  I think a dictionary would have helped save you a lot of time arguing for the wrong position.  While looking up bit, look up "permission."  It is the right to do something.  File permissions are those switches which control your right to work with it.  File types don't affect that.  Which is why every piece of documentation on UNIX (and the source code) contradict you.

---

### Post by ComplexNumber on 2006-10-17
> Uhh, yes, that is how it works.if you say so. [SIZE=1][COLOR=White]*yawn*[/COLOR][/SIZE] [SIZE=1][COLOR=White]i may as well be speaking to a brick wall
[/COLOR][/SIZE]

---

