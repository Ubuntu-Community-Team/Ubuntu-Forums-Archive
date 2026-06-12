---
title: "Linux user-friendlyness or unfriendlyness???"
date: 2007-07-08
forum: The Cafe
---

### Post by altgrrr on 2007-07-08
Yeah, I know, user-friendlyness might not be a word, it is now anyway :D


I've been into Linux for a few years now (still maintain a dual boot with windows though) and it's been more than 15 years since I first started programming in Pascal (yes, I have moved on to more complicated stuff since :D )... Enough of bragging about my computer experience, let's get to the point.

Take the man page for pipe as an example.

```
man pipe
```

Are Richard Stallman and Linus Torvalds the only ones supposed to read theese? Who understands them?

What I'm trying to say is, Linux will never come close to windows usability with this kind of krypto-language (Windows still sucks, but at least you know what you're doing to make it suck). Check this out (from man pipe):

> Pipes  and  FIFOs  (also known as named pipes) provide a unidirectional
       interprocess communication channel.  A pipe has a read end and a  write
       end.  Data written to the write end of a pipe can be read from the read
       end of the pipe.

...

A pipe is created using pipe(2), which creates a new pipe

WHAT THE HELL???

Someone tell me: did these people ever mean for someone to understand???

The same problem face me now as I am trying to learn some python. I'm trying to have python log in to a webpage and download some url:s. I constantly come across the kind of language as in the example above... Anyone get my point? Sometimes you really just want to know what something does, how to use it (the way most people would want to use it) and just a tiny bit about why it works. Are you with me? I want *man* for dummies. Call it *stupidman* or something, I don't care.

Someone tell me what the output from this would be:

```
stupidman pipe
```

I never want to sacrifice the Linux way of thinking for the windows way of... not thinking I guess :D ..but still, does it have to be this way? We've come from compiling source code to downloading dpk packages, can someone pleeeeaaaase take the next step like that NOW!!! 

Thanks for your super-valuable time (I know mine is ;) ) ...comments?

---

### Post by maniacmusician on 2007-07-08
Sure, documentation is tough stuff. At the beginning, it was written by hardcore programmers for other hardcore programmers. Some of it has been since 'dumbed down', but some hasn't. What can be done to fix this? Re-write the documentation. Contact the project to which it belongs, and ask them if you can rewrite their man-file to make them simpler and have them incorporate it in the project. They will almost always accept, because they hate writing it themselves.

Open source can still be community driven (and often is); we as users just have to start taking more responsiblity. Some of do bug triaging on launchpad (something anyone can do!), some of us write wiki's and articles, some of us develop programs, others upload patches. So, erm, what I'm trying to say is, find someone who understands that document and start an initiative to make the documentation better. you're part of the community, after all.

and by the way, the example you gave is understandable, just badly written.

---

### Post by jyba on 2007-07-08
I like the terseness of man pages. Once I've learnt a command I only use the man pages to refresh my memory on some detail or other; in that case there would be nothing more annoying than to have to wade through some rambling, folksy, tutorial style man page to find the small detail I'm looking for. If I want a tutorial it's easy enough to google for one.

---

### Post by init1 on 2007-07-08
> **altgrrr said:**
> Yeah, I know, user-friendlyness might not be a word, it is now anyway :D


I've been into Linux for a few years now (still maintain a dual boot with windows though) and it's been more than 15 years since I first started programming in Pascal (yes, I have moved on to more complicated stuff since :D )... Enough of bragging about my computer experience, let's get to the point.

Take the man page for pipe as an example.

```
man pipe
```

Are Richard Stallman and Linus Torvalds the only ones supposed to read theese? Who understands them?

What I'm trying to say is, Linux will never come close to windows usability with this kind of krypto-language (Windows still sucks, but at least you know what you're doing to make it suck). Check this out (from man pipe):



WHAT THE HELL???

Someone tell me: did these people ever mean for someone to understand???

The same problem face me now as I am trying to learn some python. I'm trying to have python log in to a webpage and download some url:s. I constantly come across the kind of language as in the example above... Anyone get my point? Sometimes you really just want to know what something does, how to use it (the way most people would want to use it) and just a tiny bit about why it works. Are you with me? I want *man* for dummies. Call it *stupidman* or something, I don't care.

Someone tell me what the output from this would be:

```
stupidman pipe
```

I never want to sacrifice the Linux way of thinking for the windows way of... not thinking I guess :D ..but still, does it have to be this way? We've come from compiling source code to downloading dpk packages, can someone pleeeeaaaase take the next step like that NOW!!! 

Thanks for your super-valuable time (I know mine is ;) ) ...comments?
Try the info page
```
info pipe
```
I am using Slax, so it is not installed for me
as for
```
stupidman pipe
```
> 
A pipe is a thing that does stuff, complicated stuff, communication stuff. 


---

### Post by koenn on 2007-07-08
> **jyba said:**
> I like the terseness of man pages. Once I've learnt a command I only use the man pages to refresh my memory on some detail or other; in that case there would be nothing more annoying than to have to wade through some rambling, folksy, tutorial style man page to find the small detail I'm looking for. If I want a tutorial it's easy enough to google for one.

I fully agree. 'man' is a reference manual. It serves to look up commands, options, syntax, ... when you already have a rough idea of what you need, but are not sure how to do it.

---

### Post by Tomosaur on 2007-07-08
> **altgrrr said:**
> Yeah, I know, user-friendlyness might not be a word, it is now anyway :D


I've been into Linux for a few years now (still maintain a dual boot with windows though) and it's been more than 15 years since I first started programming in Pascal (yes, I have moved on to more complicated stuff since :D )... Enough of bragging about my computer experience, let's get to the point.

Take the man page for pipe as an example.

```
man pipe
```

Are Richard Stallman and Linus Torvalds the only ones supposed to read theese? Who understands them?

What I'm trying to say is, Linux will never come close to windows usability with this kind of krypto-language (Windows still sucks, but at least you know what you're doing to make it suck). Check this out (from man pipe):



WHAT THE HELL???

Someone tell me: did these people ever mean for someone to understand???

The same problem face me now as I am trying to learn some python. I'm trying to have python log in to a webpage and download some url:s. I constantly come across the kind of language as in the example above... Anyone get my point? Sometimes you really just want to know what something does, how to use it (the way most people would want to use it) and just a tiny bit about why it works. Are you with me? I want *man* for dummies. Call it *stupidman* or something, I don't care.

Someone tell me what the output from this would be:

```
stupidman pipe
```

I never want to sacrifice the Linux way of thinking for the windows way of... not thinking I guess :D ..but still, does it have to be this way? We've come from compiling source code to downloading dpk packages, can someone pleeeeaaaase take the next step like that NOW!!! 

Thanks for your super-valuable time (I know mine is ;) ) ...comments?

I'm sorry to tell you this, but I don't find anything wrong with man pages. The man page for pipe describes exactly what it does. Yes, it would be 'nicer' to say "pipe takes the output of the preceding command and makes it the input of the next command, i.e: command1 | command2", but this doesn't ACCURATELY describe what pipe does, and doesn't give you the technical information which many may need. If you have anything like a decent vocabulary, however, you should be able to understand the man page fairly easily, even if some of the individual terms aren't fully understood. Sometimes you will come across 'technical' stuff when using things like pipe - that's just how it goes. While I accept that things COULD be more 'dumbed down', that doesn't necessarily mean they SHOULD be dumbed down.

---

### Post by aysiu on 2007-07-08
I also find *man* pages to be cryptic and hard-to-understand.

That's why I do Google searches to find human-readable documentation.

---

### Post by init1 on 2007-07-08
> **aysiu said:**
> I also find *man* pages to be cryptic and hard-to-understand.

That's why I do Google searches to find human-readable documentation.
What if you can't find it on Google/Don't have internet? I think that an alternative system should be made, like simple english, for those who would benefit from it. 
This is what simple english looks like. 
[http://simple.wikipedia.org/wiki/Ubuntu]("http://simple.wikipedia.org/wiki/Ubuntu")

---

### Post by koenn on 2007-07-09
```
FIREFOX(1)                    Linux User’s Manual                   FIREFOX(1)

NAME
       firefox - a Web browser for X11 derived from the Mozilla browser

SYNOPSIS
       firefox [OPTIONS] [URL]

       /usr/lib/firefox/firefox-bin [OPTIONS] [URL]

DESCRIPTION
       Firefox  is  an open-source web browser, designed for standards compli&#8208;
       ance, performance and portability.

USAGE
       firefox is a simple shell script that will set up the  environment  for
       the  actual  executable,  firefox-bin.   If  there is a Firefox browser
       already running, firefox will arrange for it to create  a  new  browser
       window; otherwise it will start the Firefox application.

OPTIONS
       A summary of the options supported by irefox is included below.
```

Is that cryptic ?

---

### Post by aysiu on 2007-07-09
> **koenn said:**
> ```
FIREFOX(1)                    Linux User’s Manual                   FIREFOX(1)

NAME
       firefox - a Web browser for X11 derived from the Mozilla browser

SYNOPSIS
       firefox [OPTIONS] [URL]

       /usr/lib/firefox/firefox-bin [OPTIONS] [URL]

DESCRIPTION
       Firefox  is  an open-source web browser, designed for standards compli&#8208;
       ance, performance and portability.

USAGE
       firefox is a simple shell script that will set up the  environment  for
       the  actual  executable,  firefox-bin.   If  there is a Firefox browser
       already running, firefox will arrange for it to create  a  new  browser
       window; otherwise it will start the Firefox application.

OPTIONS
       A summary of the options supported by irefox is included below.
```

Is that cryptic ?
Isn't that an exception?

And how many people read the Firefox *man* page anyway?

---

### Post by koenn on 2007-07-09
> **aysiu said:**
> Isn't that an exception?
don't know. I wanted to see if man is really that cryptic if you look for something you know, but need specifics. It's a reference manual, remember ?  I just took the first program that came to mind  - firefox. 

> **aysiu said:**
> And how many people read the Firefox *man* page anyway?
I do. Like, if you're setting up a computer that has to run unattended and show a web page in a browser, you'd  start firefox from a shell script and pass some  command options, say, a display size, or an url to open - and the man page tells you how to do that. 

Who would look at the pipe man page anayway ? You dont "man pipe" unless you already know what a pipe does, and need to know some details.

---

### Post by Hex_Mandos on 2007-07-09
It shows that cryptic stuff gets cryptic explanations. Do you expect normal desktop users to read the man page for, say,  ifconfig?

---

### Post by qamelian on 2007-07-09
I have no problem with man pages as they are. The man pages were one of the things that lured me away from Windows almost 10 years ago. They include more useful information than anything in the Windows help system. Yes, some of the man pages appear "cryptic", but the difficulty of a given man page tends to be directly proportional to the complexity of the command being referenced. Personally, I find man pages to be incredibly user-friendly and, when used appropriately, very educational.

---

### Post by Jimmy_r on 2007-07-09
Ok, how about cp. That is one of the first commands a newbie will encounter:

```
CP(1)                            User Commands                           CP(1)

NAME
       cp - copy files and directories

SYNOPSIS
       cp [OPTION]... [-T] SOURCE DEST
       cp [OPTION]... SOURCE... DIRECTORY
       cp [OPTION]... -t DIRECTORY SOURCE...

DESCRIPTION
       Copy SOURCE to DEST, or multiple SOURCE(s) to DIRECTORY.

       Mandatory  arguments  to  long  options are mandatory for short options
       too.

       -a, --archive
              same as -dpR

       --backup[=CONTROL]
              make a backup of each existing destination file

       -b     like --backup but does not accept an argument

       --copy-contents
              copy contents of special files when recursive

       -d     same as --no-dereference --preserve=link

       -f, --force
              if an existing destination file cannot be opened, remove it  and
              try again

       -i, --interactive
              prompt before overwrite

       -H     follow command-line symbolic links

       -l, --link
              link files instead of copying

       -L, --dereference
              always follow symbolic links

       -P, --no-dereference
              never follow symbolic links

       -p     same as --preserve=mode,ownership,timestamps

       --preserve[=ATTR_LIST]
              preserve   the   specified   attributes   (default:  mode,owner&#8208;
              ship,timestamps) and security contexts, if  possible  additional
              attributes: links, all

       --no-preserve=ATTR_LIST
              don’t preserve the specified attributes

       --parents
              use full source file name under DIRECTORY

       -R, -r, --recursive
              copy directories recursively

       --remove-destination
              remove  each existing destination file before attempting to open
              it (contrast with --force)

       --sparse=WHEN
              control creation of sparse files

       --strip-trailing-slashes remove any trailing slashes from each SOURCE
              argument

       -s, --symbolic-link
              make symbolic links instead of copying

       -S, --suffix=SUFFIX
              override the usual backup suffix

       -t, --target-directory=DIRECTORY
              copy all SOURCE arguments into DIRECTORY

       -T, --no-target-directory
              treat DEST as a normal file

       -u, --update
              copy only when the SOURCE file is  newer  than  the  destination
              file or when the destination file is missing

       -v, --verbose
              explain what is being done

       -x, --one-file-system
              stay on this file system

       --help display this help and exit

       -Z, --context=CONTEXT
              set security context of copy to CONTEXT

       --version
              output version information and exit

       By  default,  sparse SOURCE files are detected by a crude heuristic and
       the corresponding DEST file is made sparse as well.  That is the behav&#8208;
       ior  selected  by  --sparse=auto.   Specify --sparse=always to create a
       sparse DEST file whenever  the  SOURCE  file  contains  a  long  enough
       sequence  of  zero  bytes.   Use  --sparse=never to inhibit creation of
       sparse files.

       The  backup  suffix  is  ‘~’,  unless  set  with   --suffix   or   SIM&#8208;
       PLE_BACKUP_SUFFIX.   The version control method may be selected via the
       --backup option or through the  VERSION_CONTROL  environment  variable.
       Here are the values:

       none, off
              never make backups (even if --backup is given)

       numbered, t
              make numbered backups

       existing, nil

       simple, never
              always make simple backups

       As  a  special  case,  cp  makes  a backup of SOURCE when the force and
       backup options are given and SOURCE and DEST are the same name  for  an
       existing, regular file.

AUTHOR
       Written by Torbjorn Granlund, David MacKenzie, and Jim Meyering.

REPORTING BUGS
       Report bugs to <bug-coreutils@gnu.org>.

COPYRIGHT
       Copyright © 2006 Free Software Foundation, Inc.
       This  is  free  software.   You may redistribute copies of it under the
       terms      of      the      GNU      General       Public       License
       <http://www.gnu.org/licenses/gpl.html>.   There  is NO WARRANTY, to the
       extent permitted by law.

SEE ALSO
       The full documentation for cp is maintained as a  Texinfo  manual.   If
       the  info and cp programs are properly installed at your site, the com&#8208;
       mand

              info cp

       should give you access to the complete manual.

```

Ok, let us say I have no clue how to use cp..
I want to copy directory A to location B.

       cp [OPTION]... [-T] SOURCE DEST

Hmm... lemme see. I understand source is the one i copy, and dest is where I copy it. Now what is that -T? Lets look it up:
       -T, --no-target-directory
              treat DEST as a normal file

Treat DEST as a normal file? Huh?
I think I will stay away from that one... Next.

       cp [OPTION]... SOURCE... DIRECTORY

Ok, this one is quite clear. Lets try:
```

jimmy@jimmy-desktop:~$ cp A B
cp: utesluter katalog "A"
```

Huh? I cannot copy a directory?

It must be that OPTION thing... Lets look through the options:

-a, --archive
              same as -dpR

What?? Arrgh, my head hurts.
Looking at more options... Here is something:

-R, -r, --recursive
              copy directories recursively

That seems to be what I want. But... What is the difference between -R, -r and --recursive? Will it matter? Will the wrong one break something? Help... :confused::cry:

But wait, at one of the last lines it mentions
```
 info cp

       should give you access to the complete manual.
```

jimmy@jimmy-desktop:~$ info cp 
```
File: cpio.info,  Node: Top,  Next: Introduction,  Prev: (dir),  Up: (dir)



GNU cpio is a tool for creating and extracting archives, or copying
files from one place to another.  It handles a number of cpio formats as
well as reading and writing tar files.  This is the first edition of the
GNU cpio documentation and is consistant with GNU cpio 2.5.

* Menu:

* Introduction::
* Tutorial::                    Getting started.
* Invoking `cpio'::             How to invoke `cpio'.
* Media::                       Using tapes and other archive media.
* Concept Index::               Concept index.

 --- The Detailed Node Listing ---

Invoking cpio

* Copy-out mode::
* Copy-in mode::
* Copy-pass mode::
* Options::
```

What is cpio? And how do I navigate this thing? OOOOHHH.

Ok, I find "Tutorial"

```
File: cpio.info,  Node: Tutorial,  Next: Invoking `cpio',  Prev: Introduction, \
 Up: Top

Tutorial
********

GNU cpio performs three primary functions.  Copying files to an
archive, Extracting files from an archive, and passing files to another
directory tree.  An archive can be a file on disk, one or more floppy
disks, or one or more tapes.

   When creating an archive, cpio takes the list of files to be
processed from the standard input, and then sends the archive to the
standard output, or to the device defined by the `-F' option.  *Note
Copy-out mode::.  Usually find or ls is used to provide this list to
the standard input.  In the following example you can see the
possibilities for archiving the contents of a single directory.

     % ls | cpio -ov > directory.cpio

   The `-o' option creates the archive, and the `-v' option prints the
names of the files archived as they are added.  Notice that the options
can be put together after a single `-' or can be placed separately on
the command line.  The `>' redirects the cpio output to the file
`directory.cpio'.

   If you wanted to archive an entire directory tree, the find command
can provide the file list to cpio:

     % find . -print -depth | cpio -ov > tree.cpio

   This will take all the files in the current directory, the
directories below and place them in the archive tree.cpio.  Again the
`-o' creates an archive, and the `-v' option shows you the name of the
files as they are archived.  *Note Copy-out mode::.  Using the `.' in

Omitted a lot of blaha...
```

Long before this point, any newbie would have given up long ago.

It would be great if there could be a good Examples section for every commonly used command like this:

```
CP(1)                            User Commands                           CP(1)

NAME
       cp - copy files and directories

EXAMPLES
       cp file location
              copy file to location

       cp -r directory location
              copy directory to location

SYNOPSIS
       cp [OPTION]... [-T] SOURCE DEST
       cp [OPTION]... SOURCE... DIRECTORY
       cp [OPTION]... -t DIRECTORY SOURCE...
```

---

### Post by ltk5 on 2007-07-09
I agree that man pages are a bit difficult, but still it's a manual. It should be written objective, as it is.
For friendliness there are tens, hundreds of tutorials, topics on ubuntuforums, webpages...

Personally, the complexity of man pages drove me away from them, and here. to the ubuntuforums community, where people are friendly, and pure nice:-D

---

### Post by koenn on 2007-07-09
> **Jimmy_r said:**
> Ok, how about cp. That is one of the first commands a newbie will encounter 
is it ? 
newbies don't do the drag and drop thing in a file manager ?

---

### Post by Jimmy_r on 2007-07-09
Well, of the command line commands it is probably one of the first...
Or do you have other ones?

---

### Post by koenn on 2007-07-09
The first ones I learned where probably 

apt-get update

dpkg-reconfigure

cd

cat

startx


and please don't go looking for the man pages. when you're new, your first attempts at command lines will be copied from a website, a howto or a forum.
Later, when you need to solve a specific problem, you go looking in the man pages for specific options to handle your probem. By then, "recursive' and 'target' won't be cryptic anymore.

---

### Post by runningwithscissors on 2007-07-09
Uh..
From the help pages on Windows Server 2003
```
Copy
Copies one or more files from one location to another. 
 
Syntax 
copy [/d] [/v] [/n] [{/y | /-y}] [/z] [{/a | /b}] Source [{/a | /b}] [+ Source [{/a | /b}] [+ ...]] [Destination [{/a | /b}]] 
 
Parameters 
/d  
Allows the encrypted files being copied to be saved as decrypted files at the destination.  
/v  
Verifies that new files are written correctly.  
...

```
And people manage to copy files on Windows without ever looking at that.

My point is... documentation is supposed to be full of all kinds of information. It will usually be overwhelming, not just for new users but for everyone.

Howver, I do agree that a few examples should be provided and in fact, a lot of man pages do provide examples. 

Also, check the man pages on FreeBSD. Excellent and a lot easier to follow than the ones for GNU tools.

---

### Post by rodo-&gt;dave on 2007-07-09
first place I look :)

---

### Post by 23meg on 2007-07-09
Manual pages are fine as they are; they're just what they should be. But since Ubuntu owes a lot of its success to lowering the barriers of entry to different areas of free software, a comprehensive beginner's command line reference wouldn't be out of place for Ubuntu contributors to create and maintain, and the implementation the original poster suggested will work quite fine. 

Does such a thing like "stupidman" already exist? If positive, some people who share and/or understand the OP's frustration here may want to contribute to it, and the result can be shipped with Ubuntu.

If negative, it won't be too hard to create it. There's already an abundance of good command line documentation intended for beginners, and it's safe to assume most (if not all) of it is licensed suitably for inclusion in such a project. It can easily be improved, and more can be added by contributors from the forums. The source for man-db and groff are of course available to be utilized, thus the development part would be trivial; we'd just need good quality documentation that's well standardized.

If anyone knows of a project that aims to do this, please point to it. If there's interest in getting this done, we can start a thread in the development forum,  write a blueprint, and get in touch with the documentation team to get the ball rolling.

---

### Post by Jimmy_r on 2007-07-09
> **koenn said:**
> The first ones I learned where probably 

apt-get update

dpkg-reconfigure

cd

cat

startx



I took the cp command because that was the first I could think about...
The cat manpage has some examples already, but the problem is they are near the bottom. Why not move them towards the beginning?

> and please don't go looking for the man pages. when you're new, your first attempts at command lines will be copied from a website, a howto or a forum.
Later, when you need to solve a specific problem, you go looking in the man pages for specific options to handle your probem. By then, "recursive' and 'target' won't be cryptic anymore.

You intend the 'you' as an indirect reference to new users in general, and not a direct reference to me right?
Remember I tried to think and act as a newbie in my example, does not mean I am one :)

Anyway, does it in any way harm you that manpages get a few examples, placed so they will be easy to find?
Or should new users have to learn the hard way, so it will be fair?

---

### Post by original_jamingrit on 2007-07-09
I agree with most of the responses to the first post.  The man pages seem to be for quick reference for people who already have a basic understanding of what the command does, although they may inconvenient and sometimes frustrating for the casual user.

Although, a stupidman project would be a good idea, since Ubuntu is geared more to casual users than it is to linux hackers.  Jimmy_r is brings up a good point, we _do_ want to make it easier for new users.  Although as I understand it, each man page is usually written by the person/people from whom the command/program comes.  The stupidman could be generated by a sort of wiki project.

---

### Post by 23meg on 2007-07-09
And it would be a huge job to get your documentation accepted by every upstream project for every package, and/or add such documentation to every Universe package, and if that job were to be done, it would be best done within Debian. Perhaps "stupidman" would best be limited to the most commonly used shell commands and executables, along with a selection of popular Universe command line tools.

But would that make it a non-universal, half-baked product? Thinking out loud..

---

### Post by original_jamingrit on 2007-07-09
Well, you're right, casual users probably would not need use "stupidman" for information on emacs or svn stuff.  They would just need simple explanations for A) often used commands like "cp" and "mv", and B) commands that could kill your system like "rm" or any permission/password changing commands.

---

### Post by koenn on 2007-07-09
> **Jimmy_r said:**
> Or should new users have to learn the hard way, so it will be fair?
Let's not go there.

If I need to look up rsync because I want to remote-copy a directory over a secure link with deletion of files that exist on the target but don't exist in the source directory, with exlusion of specific files, and specifics on how remote filesystems mounted to the source directory should be treated during the copying, 
then it's convenient that the rsync man page explains these options **accurately**. Leaving out  "unfriendly" words such as recursive, I/O, checksum or sparse file would make the man page incomplete and inaccurate. 

One of Linux' strong ponts are its powerful commands. Dumming down the documentation will only weaken that position. "fair" or "the hard way' has nothing to do with it. 

That said, I have no problem with someone else creating simplified documentation. There's an audience  for "Linux for Dummies" as well as for  "The Unix System Administration Guide", and I've read both.

---

### Post by Jimmy_r on 2007-07-09
> **koenn said:**
> Let's not go there.

If I need to look up rsync because I want to remote-copy a directory over a secure link with deletion of files that exist on the target but don't exist in the source directory, with exlusion of specific files, and specifics on how remote filesystems mounted to the source directory should be treated during the copying, 
then it's convenient that the rsync man page explains these options **accurately**. Leaving out  "unfriendly" words such as recursive, I/O, checksum or sparse file would make the man page incomplete and inaccurate. 

One of Linux' strong ponts are its powerful commands. Dumming down the documentation will only weaken that position. "fair" or "the hard way' has nothing to do with it. 

That said, I have no problem with someone else creating simplified documentation. There's an audience  for "Linux for Dummies" as well as for  "The Unix System Administration Guide", and I've read both.

Ah, that is the general reaction on something like this.
Unix elites are afraid it will be so simple it will hinder... Ok, I will not go there :)

I never meant to remove the word "recursive". I meant to add a small section in the beginning of the manpage with examples of the most common usage.
Look at the manpage for tar, for example. That kind of Example section is what I meant, not to remove anything at all.
And that is what I mean by my "fair" and "hard way" sentence:
Make it easier for the newbie but: **No removal of anything, absolutely not! Do you read, over?**

<rant>Slightly off topic: That is the knee-jerk reaction to anything trying to make something a little easier. Be it an Examples section in a manpage or a gui for editing a config file:
Some of the experts always feel that it will take something away from them.</rant>

---

### Post by koenn on 2007-07-09
> **Jimmy_r said:**
> 
Unix elites ... 

Thanks for the compliment, 
and I'll refrain from replying so we don't have yet another discussion about Linux elitism. Been there, done that, and it wasn't interesting.

---

### Post by Jimmy_r on 2007-07-09
> **23meg said:**
> And it would be a huge job to get your documentation accepted by every upstream project for every package, and/or add such documentation to every Universe package, and if that job were to be done, it would be best done within Debian. Perhaps "stupidman" would best be limited to the most commonly used shell commands and executables, along with a selection of popular Universe command line tools.

But would that make it a non-universal, half-baked product? Thinking out loud..

I guess it wont be a picnic getting upstart jobs into upstream either...
Wait, I forgot. Ubuntu has the ability to keep their own patches if upstream does not accept them...

---

### Post by Jimmy_r on 2007-07-09
> **koenn said:**
> Thanks for the compliment, 
and I'll refrain from replying so we don't have yet another discussion about Linux elitism. Been there, done that, and it wasn't interesting.

Oh, It was only my sense of humor. Please forgive me, oh mighty 1337. Do not throw your flames of wrath upon meh.

But if we ignore that part, do you have anything against the addition to the manpages, except any practical problems about finding every upstream and let my sledgehammer discuss the situation with their legs? I guess they wont need them to code anyway:twisted:

---

### Post by 23meg on 2007-07-09
> **Jimmy_r said:**
> 
Wait, I forgot. Ubuntu has the ability to keep their own patches if upstream does not accept them...

Sure, but Ubuntu isn't an omnipotent entity with unlimited resources; it's made up of contributors who are actual people that have to put in actual extra work hours to maintain the delta with upstream. In other words, sure, it can be done independently from upstream, but since it has to be maintained, and since upstream moves ahead at such a fast pace, it will be a lot of work for whoever stands up to the job.

Concentrating on a basic set of mostly needed tools sounds like a good compromise.

---

### Post by 23meg on 2007-07-09
[QUOTE=Jimmy_r]do you have anything against the addition to the manpages,[/QUOTE]

I do. I want manpages to stay as they are, like others do. They should be technically to the point, and not be cluttered by the more plain documentation with lots of examples, *because that would detract from their present function and usefulness*. 

As far as I can see, nobody is going against the idea of having more accessible command line documentation meant for beginners; if they were, your "elitism" line would have a point. People only disagree about the way it should be implemented, and that entitles you to call their position *conservative*, not *elitist*.

---

### Post by altgrrr on 2007-07-09
> **Tomosaur said:**
> Yes, it would be 'nicer' to say "pipe takes the output of the preceding command and makes it the input of the next command, i.e: command1 | command2", but this doesn't ACCURATELY describe what pipe does, and doesn't give you the technical information which many may need.

That's beautiful, why not put that in there (eg man pages) as well??? Like a dummyline or something like that...


And about my man example, that's just one of the many things that still annoy me a little about Linux. If there was no community, how would I ever know to look in /etc/dhcp3/dhclient.conf to correct the problems I had with a faulty DNS??? "Well, there IS a community", you will surely say. You might even say that open source exists because there exists a community, hence the problem is solved. Well, it's not a too bad idea, I reeeeaaaaally prefer solving a linux problem to solving a windows problem. A search on eg a windows error returns hits from microsoft knowledge base or whatever it's called. Of course Microsoft hates communities so no quick responses there...

Anyway, I'm just saying that there still is some kind of old style GNU feeling here and there in Linux and I'm not sure I like it. Don't get me wrong, I love it that applications like vi still are around, I use emacs myself. Those are applications which are hard to learn, not very user friendly or appealing to the eye (think shiny see through colors and menus) .

I started with linux when nothing worked and just installing it took a lot of figuring out. I recently ereased the harddrive on my laptop and installed Ubuntu and Win XP on dual boot. On windows startup, I still had to install drivers to get the laptop thingies like volume control to work, my wifi card still doesn't work. Ubuntu just fixed everything, everything works. It's going in the right direction...

---

### Post by altgrrr on 2007-07-09
> **koenn said:**
> ```
FIREFOX(1)                    Linux User’s Manual                   FIREFOX(1)

NAME
       firefox - a Web browser for X11 derived from the Mozilla browser

SYNOPSIS
       firefox [OPTIONS] [URL]

       /usr/lib/firefox/firefox-bin [OPTIONS] [URL]

DESCRIPTION
       Firefox  is  an open-source web browser, designed for standards compli&#8208;
       ance, performance and portability.

USAGE
       firefox is a simple shell script that will set up the  environment  for
       the  actual  executable,  firefox-bin.   If  there is a Firefox browser
       already running, firefox will arrange for it to create  a  new  browser
       window; otherwise it will start the Firefox application.

OPTIONS
       A summary of the options supported by irefox is included below.
```

Is that cryptic ?

No, that's actually very good. Thumbs up... :D

---

### Post by altgrrr on 2007-07-09
> **koenn said:**
> Who would look at the pipe man page anayway ? You dont "man pipe" unless you already know what a pipe does, and need to know some details.

In my case, a friend told me about a way to solve a problem with pipe, he showed me and when I decided to try it out a few days later, I had forgot exactly how he saidf to do it... hence the man pipe... That's actually when I started this thread.

Of course, the man pipe did not help me at the time :D

---

### Post by altgrrr on 2007-07-09
> **Hex_Mandos said:**
> It shows that cryptic stuff gets cryptic explanations. Do you expect normal desktop users to read the man page for, say,  ifconfig?

Well... yeah!

Because in Linux (even easy to use distros like ubuntu) it might not be as straightforward to solve a problem as in windows.

---

### Post by altgrrr on 2007-07-09
And in general about the discussion: let's not get hung up on the man pages, I meant to discuss the concept of linux distros, not the concept of man pages.

---

### Post by original_jamingrit on 2007-07-09
> **altgrrr said:**
> And in general about the discussion: let's not get hung up on the man pages, I meant to discuss the concept of linux distros, not the concept of man pages.

I thought it was about the man pages.  But this is just about usability in general?

What kind of usability where you looking for?  More GUIs?  The terminal is a powerful tool, although it's not very intuitive.  Is that the main issue here?

Or are you talking about a new distro of the Linux kernel, along with a simple set of GUI toolkits and applications?  If that is the case, I'm sorry to say that's what Ubuntu is supposed to, and will eventually be.

---

### Post by Jimmy_r on 2007-07-10
> **23meg said:**
> I do. I want manpages to stay as they are, like others do. They should be technically to the point, and not be cluttered by the more plain documentation with lots of examples, *because that would detract from their present function and usefulness*. 

As far as I can see, nobody is going against the idea of having more accessible command line documentation meant for beginners; if they were, your "elitism" line would have a point. People only disagree about the way it should be implemented, and that entitles you to call their position *conservative*, not *elitist*.

Oh noes!!!11!
Three extra lines in a manpage makes old 23meg unable to find anything.
Well I guess we have to kick the tar manpage out, cause ole 23meg get confused by teh examples.
And drop that "elitism" line, it was a joke.

> Sure, but Ubuntu isn't an omnipotent entity with unlimited resources; it's made up of contributors who are actual people

I am very well aware of that.

> In other words, sure, it can be done independently from upstream, but since it has to be maintained, and since upstream moves ahead at such a fast pace, it will be a lot of work for whoever stands up to the job.

Wow, upstream manpages move forward at a breakneck pace. There aint no patch that wont break within a few days.

I thought Ubuntu would be a good channel for getting changes into upstream...
Making documentation is boring and if someone sent me an improved manpage for any of my projects, I would be glad to accept it as long as it is correct.

I guess every upstream aint like that. They are conservative and wont change their manpa... Wait, go 2 paragraphs up. Keep reading till both statements are true.
We have made ourselves an infinite loop... How cool. That should keep the conservatists out of the way for some time.

---

### Post by saulgoode on 2007-07-10
> **Jimmy_r said:**
> I thought Ubuntu would be a good channel for getting changes into upstream...

Upstream would be a good channel for getting changes into upstream -- why pawn off changes on Ubuntu?

> **Jimmy_r said:**
> Making documentation is boring and if someone sent me an improved manpage for any of my projects, I would be glad to accept it as long as it is correct.

Have you sent your "improved manpage" to the GNU project that they might "improve" their CP documentation? If so, why don't you share the experience that we might all benefit?

---

### Post by argie on 2007-07-10
Manpages for the novice. Have we all gone crazy? I thought novices don't touch the omgscary CLI because it bites.

It's interesting though, the man pages are cryptic sometimes. I remember trying to get something working only using the manpages and it was hell because I just couldn't understand it. I've got an idea though, why not add another section to the Ubuntu Help Center, The Terminal. Don't forget to add the horror music when the user clicks on that section. Within this section you can have your user-readable command manuals, with examples, and then I suppose maintenance will be much simpler than modifying the manpages themselves. Frankly examples rule, nothing to beat a manpage with examples.

Also, the point being I expect someone who needs help to click Help, not to go to the command line and type man whatever.

---

### Post by steven8 on 2007-07-10
> **argie said:**
> 
Also, the point being I expect someone who needs help to click Help, not to go to the command line and type man whatever.

Uh Oh!  I can't find any entries for Man whatever!!!!  Now what do I do!!!!????!!!
:popcorn:

---

### Post by argie on 2007-07-10
> **steven8 said:**
> Uh Oh!  I can't find any entries for Man whatever!!!!  Now what do I do!!!!????!!!
:popcorn:

Oh, that would be because bash is case-sensitive. :D

---

### Post by stepan2 on 2007-07-10
in truth , I never want linux to reach the user-friendlyness that windows achieved. The only reason they achieved this is by compromising their security.

---

### Post by nyvalbanat on 2007-07-10
So what's the windows equivalent documentation for pipes?

I agree that the documentation should be less geek-oriented, but I'm not sure if your example was representative of that. FIFOs and other ipc's are not intended for end-users (or, can you think of a scenario when my grandma would need to create a pipe?). IPCs are tied to the core OS functionality and by definition require a certain amount of expertise.

---

### Post by stepan2 on 2007-07-10
and again , if we make it to user-friendly , it will compromise security.

---

### Post by Jimmy_r on 2007-07-10
> **saulgoode said:**
> Upstream would be a good channel for getting changes into upstream -- why pawn off changes on Ubuntu?

Well, since it would benefit Ubuntu, and Ubuntu has a documentation team...

> Have you sent your "improved manpage" to the GNU project that they might "improve" their CP documentation? If so, why don't you share the experience that we might all benefit?

No, I have not, since I suck at documentation. My time is better spent coding.
Plus, if their attitude is anything like the ones in this discussion, it will be wasted time...
It probably will... If you improve a manpage, the conservatists yell.
If you write a gui to edit some config files, some people whine too. Everything should be as it has always been.

> Manpages for the novice. Have we all gone crazy? I thought novices don't touch the omgscary CLI because it bites.

It's interesting though, the man pages are cryptic sometimes. I remember trying to get something working only using the manpages and it was hell because I just couldn't understand it. I've got an idea though, why not add another section to the Ubuntu Help Center, The Terminal. Don't forget to add the horror music when the user clicks on that section. Within this section you can have your user-readable command manuals, with examples, and then I suppose maintenance will be much simpler than modifying the manpages themselves. Frankly examples rule, nothing to beat a manpage with examples.

Also, the point being I expect someone who needs help to click Help, not to go to the command line and type man whatever.

Yes, not only for novices. Although I have in a few places seen people tell newbies:"write man programname to see how to use it"

Even experienced people might need a quick example at times.

> in truth , I never want linux to reach the user-friendlyness that windows achieved. The only reason they achieved this is by compromising their security.

A lot of the people here thought that(at least subconsciously), I think. You were the one to tell it out loud.

> So what's the windows equivalent documentation for pipes?

Why does windows always come up in these kinds of discussions?
Windows cli sucks hard, we do not want to compare to it.

> I agree that the documentation should be less geek-oriented, but I'm not sure if your example was representative of that. FIFOs and other ipc's are not intended for end-users (or, can you think of a scenario when my grandma would need to create a pipe?). IPCs are tied to the core OS functionality and by definition require a certain amount of expertise.

Perhaps cp was a better example?

```
and again , if we make it to user-friendly , it will compromise security.
```

Oh come on. If adding a few lines to a few manpages compromises security, I am Mahatma Gandhi's grandfather.
We are not turning on auto login as root or anything.

---

### Post by 23meg on 2007-07-10
> **Jimmy_r]
Three extra lines in a manpage makes old 23meg unable to find anything.
Well I guess we have to kick the tar manpage out, cause ole 23meg get confused by teh examples.[/QUOTE]

No, three extra lines wouldn't hurt old 23meg at all, but it's not what we're talking about either said:**
>  There aint no patch that wont break within a few days.

What I'm talking about is that as the software changes, the documentation will have to as well; it would be a huge burden for an Ubuntu / Debian initiative to pull this task off. If we stuck to a set of often used commands, however, it would be much easier both because those commands don't change much, and because they're few in number.

[QUOTE=Jimmy_r]
I thought Ubuntu would be a good channel for getting changes into upstream...
Making documentation is boring and if someone sent me an improved manpage for any of my projects, I would be glad to accept it as long as it is correct.[/QUOTE]

Me too, but not everyone will accept the kind of documentation we're talking about as an improvement over the "cryptic" documentation, which many people are happy with, for good reason. For providing a consistent and near-complete documentation intended for beginners, standard manual pages aren't the way to go. 

[QUOTE=Jimmy_r]
If you improve a manpage, the conservatists yell.
If you write a gui to edit some config files, some people whine too. Everything should be as it has always been.[/QUOTE]

Speak for yourself, and let those who think so speak for themselves. That's not the overall attitude in this thread, and certainly isn't mine.

---

### Post by Jimmy_r on 2007-07-10
Well... Sorry, 23meg and the rest. I have not been serious more than half the time in this thread.

I have been acting that way at times lately.
It could be because I have not had more than one week vacation in the last three years... Some kind of burnout, i guess. Well, after friday I will be getting four weeks off, so perhaps I will go back to normal then :)

You know what, lets start this over.
Stupidman, you say? I think the users might like Easyman better.

Anyone found some project that does this already?

---

### Post by argie on 2007-07-11
Jimmy_r, wow, you seem to have one hell of a tough job.

In any case, anything against putting it in the System » Help bit? I'd think that would be ideal.

---

### Post by altgrrr on 2007-07-12
> What kind of usability where you looking for?  More GUIs?  The terminal is a powerful tool, although it's not very intuitive.  Is that the main issue here?

I love the terminal, keep it, otherwise Linux will end up being just another windows :D

I did'nt really mean anything, just sharing my opinion, people seem interested though :D

---

### Post by Celegorm on 2007-07-12
Isn't info already a sort of "easyman"?

---

