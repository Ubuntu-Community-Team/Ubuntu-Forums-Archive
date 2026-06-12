---
title: "My tool to log installs and remoces ... other system stuff"
date: 2015-06-13
forum: Ubuntu, Linux and OS Chat
---

### Post by lawrence_hickey on 2015-06-13
I do  maintenance stuff from linux with the usual sudo ....
and sometimes lots is output to the screen, and then the utiility asks 
Ok to continue(Y,n)     like with a uninstall or install.
and whatever I decide to do, I want the entire ouptut session captured. 
I am very good at C and unix, but new to linux, so this problem might have a 
comon solution already, so as emily litella used to say "never mind"
but anyway this may work out. You get to see all you see now and get
to answer proceed now questions, but still you get to log the whole mess in 
case something bad happens, OR just to keep a history of these encounters
in a directory somewhere for reference. 
Well here goes. 
Suppose my program called "fake" will write to stdout, and ask periodic questions
do you want to proceed ... This is the idiom i use to embed this call to "fake".
ksh -c "(fake 5 6 7)"|tee fake.log

you can use sh instead of ksh, but I like ksh.  fake 5 6 7 will ask 5 times proceed or not(Y/n)
and each time deliver 6 lines of line length 7.
There are lots of other ways to try to do this, using tee etc, and none work except this idiom.
save the fake.log's 
Might have to use sudo in front of the fake call in the real case of a system install etc. I have it 
set up so that sudo itself does not require a password, but otherwise I believe you could enter
the sudo password as usual at the command line, and it would get logged. Not sure cause I have
sudo tricked up do not bother me about a password.
can use "fake 5 6 7 2>&1)" instead of "(fake 5 6 7)" so you can capture any messages written to
stderr too. And in another separate window one can edit site.log as it is being created before
the "do you want to continue" question is answered.

---

### Post by Habitual on 2015-06-13
Is there a question?

---

### Post by lawrence_hickey on 2015-06-13
no question. Just an offering of a solution to a problem. The problem being: doing those system calls and capturing the output
into a file- and allowing response to questions(proceed or not) and allowing another terminal window to scan the possibly large output volume just presented to the screen to wisely answer the proceed or not question. And saving the log files in a directory to keep track of what was done
to modify your system.

---

