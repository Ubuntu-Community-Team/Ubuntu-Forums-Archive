---
title: "Continuation Lines in Batch Files"
date: 2007-12-03
forum: Windows
---

### Post by blackhole54 on 2007-12-03
Hi All,

I have a pretty basic question about MS batch files.  Do batch files support any kind of continuation line analogous to the way you can continue a line in a **bash** script (ending the line with a backslash)?  I've already verified that the command interpreter (cmd.exe) does not like backslash.  And I've not been able to find anything via a Google search.

Thanks in advance for any help/advice.

---

### Post by rickyjones on 2007-12-03
Not too my knowledge - should be easier to just keep one line to one line...

-Richard

---

### Post by blackhole54 on 2007-12-03
> **rickyjones said:**
> Not too my knowledge - should be easier to just keep one line to one line...

-Richard

Thanks for your response.

I was trying to keep the file readable.  I guess I will just have to let the lines wrap.

---

### Post by tom93 on 2008-05-27
You can use a carat character ("^" ; shift-6) as a line extension character in DOS batch files. Be sure to save them with CR/LF line endings - "textmode" in VIM.

---

### Post by blackhole54 on 2008-06-22
> **tom93 said:**
> You can use a carat character ("^" ; shift-6) as a line extension character in DOS batch files. Be sure to save them with CR/LF line endings - "textmode" in VIM.

Thanks a lot.  I apologize for my delay in responding; I wasn't in a position to test your suggestion until now.

For anybody else wanting to do this, I'll note that apparently the continuation line cannot have any leading blanks.  So that this works:

```

for /F "tokens=1,2,3,4,5" %%a in (%temp_lines%) ^
do call :sub2 %%a %%b %%c %%d %%e

```

but this does not:

```

for /F "tokens=1,2,3,4,5" %%a in (%temp_lines%) ^
   do call :sub2 %%a %%b %%c %%d %%e

```

(It may not be obvious from this posting but in each case the caret is the last character on the line.  I presume that is a requirement analogous to bash but I haven't tested it.)

---

