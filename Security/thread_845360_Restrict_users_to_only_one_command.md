---
title: "Restrict users to only one command"
date: 2008-06-30
forum: Security
---

### Post by Tsucasa13 on 2008-06-30
O.K., first off, I couldn't find anything that was similar to what I was looking for on the forums.  If there is something, please point me in the right direction.

What I am trying to accomplish is to make a script (I was using python) to take what was typed into Bash and then filter it so that it would only accept one command.  However, I was also trying to filter out any characters that would allow for multiple commands such as the pipe (|) or double ampersand (&&) or the input and output carrots.  Unfortunately for me, bash would only send the first command to the script and would then proceed with the second one, which made sense.  (I typed as ./script command && command)  Is there anyway if I can make Bash either ignore those characters or if I can have it send the entire string to the script without using quotes (because I am planning to have it be built into the bash startup files, and people normally won't type quotation marks).  Any help would be very much appreciated.

---

### Post by milosz.galazka on 2008-06-30
something like that: [http://ghantoos.org/limited-shell-lshell/](http://ghantoos.org/limited-shell-lshell/) ?

---

### Post by Tsucasa13 on 2008-07-01
Wow, I wasn't expecting such a fast response.  Thank you very much.  Yes, that does look like the answer to my problem.  I'm about to look at the code and see how they scripted it.  Thanks ever so much, and I'll be sure to tell you when I get everything working.

---

