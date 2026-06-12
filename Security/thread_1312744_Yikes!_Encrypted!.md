---
title: "Yikes! Encrypted!"
date: 2009-11-03
forum: Security
---

### Post by Aviendha09 on 2009-11-03
Ok so I decided to try encryption (because I'm Curious!!) but since I dual-boot with all kinds of OSs I realised this is not practical. I posted on this thread: [http://ubuntuforums.org/showthread.php?t=1134121]("http://ubuntuforums.org/showthread.php?t=1134121") But it's old, So no-one saw it. :-k

---

### Post by Aviendha09 on 2009-11-05
Bump!

---

### Post by cariboo on 2009-11-05
> PRIVATE=`cat ~/.ecryptfs/Private.mnt 2>/dev/null || echo $HOME/Private`

Just type or copy the above command in a terminal and press enter, then follow the instructions in the original thread

---

### Post by Aviendha09 on 2009-11-05
Did you follow the thread to the other post? 

I did put in the command. I got no output. Shouln't cat *show me* something? I stopped because I don't understand the commands and I'm scared to proceed. Can you break it down for me?

Also: When I boot in jaunty, why am I not simply asked my passphrase to access the folder? I'm locked out! That's why I want out of encryption. (No states secrets anyway). 

thx for your help.

---

### Post by Aviendha09 on 2009-11-10
Ok I followed the instructions and they worked! Phew! Learned something the hard way today!! Thx for the help....
eh...can someone break down the meaning of the first command to execute...  the one with the cat? It has all kinds of weird magic words I don't get (i.e.: 2>, ||, etc...) ?? :cool:

---

### Post by Agent ME on 2009-11-10
> **Aviendha09 said:**
> Ok I followed the instructions and they worked! Phew! Learned something the hard way today!! Thx for the help....
eh...can someone break down the meaning of the first command to execute...  the one with the cat? It has all kinds of weird magic words I don't get (i.e.: 2>, ||, etc...) ?? :cool:
Sure.
```
PRIVATE=`cat ~/.ecryptfs/Private.mnt 2>/dev/null || echo $HOME/Private`
```
This sets the value of a variable "PRIVATE" to the results of the command "cat ~/.ecryptfs/Private.mnt 2>/dev/null || echo $HOME/Private". The backticks (` `) mean to run the command enclosed and return the output - so you don't see any output because it's funneled straight into the PRIVATE variable.

"cat ~/.ecryptfs/Private.mnt" makes it read from one of EcryptFS's files to find where the private directory is mounted. "2>/dev/null" means to send any error messages to /dev/null (things sent here are simply forgotten about). "|| "... means to execute the next command if the first part fails. In this case, it echoes your home folder location following by "/Private" as a sort of default guess to where your Private folder probably is or should be.

All this works to set the PRIVATE variable to a piece of text that for example could look like "/home/someuser/Private", which I figure is then used by some other program.

---

### Post by Aviendha09 on 2009-11-11
Hey! Thanks a bunch! It's not obvious to get a good grasp of command line "grammar". Is this part of bash-scripting? I have to get me a book (or should I call it a "grimoire"), soon!

---

### Post by Rayve on 2009-11-11
Here are some helpful links on the command line (and bash, though I stayed away from ones that were heavy on the scripting - you can Google those if you'd like, of course!):

[http://www.linuxcommand.org/learning_the_shell.php](http://www.linuxcommand.org/learning_the_shell.php)
[http://bash.cyberciti.biz/guide/Main_Page](http://bash.cyberciti.biz/guide/Main_Page)

Some common commands in alphabetical list:

[http://www.howtoforge.com/useful_linux_commands](http://www.howtoforge.com/useful_linux_commands)

From the beginner's guide here on the forums, with a link to a free ebook:

[http://ubuntuforums.org/showthread.php?t=1052065](http://ubuntuforums.org/showthread.php?t=1052065)


And, of course

```

man

```is your friend!  If you try a "man" command but don't get anything back, try "man -k" to do a search for what you want, for example, if you only remember it had something to do with wireless networking, you could type:

```

man -k wireless

```and then peruse the list to find the command you were looking for.  For ones you will use often, such as "fstab" (filesystem tables), or even simpler ones such as "cat" (concatenate), I suggest putting them into their own files so you can read them any time you want without having to scroll through a page at a time in the terminal. 

You can do this by typing:

```

man cat > /home/user/Desktop/cat

```Which will take the output of the command "man cat" and essentially copy/paste the entire thing into a file at the location you tell it to - in this case, the file "cat" on user's Desktop (fill in your name for "user").  I created a folder called "Man_Pages" in my Documents so I could keep them all in one place. [Note that this will overwrite any text file you already have named "cat" on your Desktop, so change the name/location as needed... or look up the ">>" command which will append instead of overwrite.]

Alternately, the ubuntu.com site has all the man pages as well, for various versions of Ubuntu in case they differ:

[http://manpages.ubuntu.com/manpages/jaunty/en/man1/cat.1posix.html](http://manpages.ubuntu.com/manpages/jaunty/en/man1/cat.1posix.html) 

Hope this wasn't too much information for you!  Getting started with the command line can seem overwhelming, but it's enjoyable and fairly intuitive (for the simpler things anyhow) once you get the hang of it.  :)

---

### Post by Aviendha09 on 2009-11-11
Wow! Thx for the links and especially for the > and >> for man pages, that will sure be useful! ;)

---

