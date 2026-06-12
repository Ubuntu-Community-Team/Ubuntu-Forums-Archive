---
title: "What are your most used CLI Commands"
date: 2008-04-15
forum: The Cafe
---

### Post by saphil on 2008-04-15
I am working on a new project comparing Linux (Ubuntu is my choice there) with OpenSolaris.  There are a whole lot of similarities, but as a new user of Solaris, I can attest that there are enough differences to make starting a new Solaris implementation a run to the instruction manuals.  

On Ubuntu, I use the following commands pretty regularly, and I want to have a small notebook of the commands that would do what I am used to doing in Linux and some man-page detail and the commands in Solaris as well.  I want to de-geek the man pages a little, since most of the people I am working with right now are students, and the shorthand we know and love is confusing for newbies.  I would like to be able to hand this out to a 1st-year IT student and have them be able to get a little more out of it than they do from man pages.  I had a lot of trouble in the beginning, sorting out which parts of the commands are which, and I see this tendency in others as well.

I know, for instance, that the application package manager for Solaris is called packageadd, and that correlated to dpkg.  Solaris zfs has some features that are not available in ext3.  I have heard there is an ext4 file system out there, but I have not seen it yet (I read it was going to appear in Fedora9).  If you were going to do this project, what would your top 25 commands be?  I know some of these below are not core-utils, but they are the things I use.  

```
wolf@prospero:~$ [Tab][Tab] #lists all available man pages 
Display all 3067 possibilities? (y or n)
```OpenSolaris has only 1645 possible choices.  To get all of these listed and (slightly) de-geeked would be way too big a scope.


```
ls   # for directory reading
cd   # changing directories
mkdir # to make directories
rm # to remove files and empty directories
rm -R # to remove non-empty directories (this is one of the dangerous commands
touch # to make files and update the "last accessed" point
./ #to run executables (like 'configure')
echo # to write something to display
uname -a # to check on what kernel I am running, so I can tell the forum support my details (if something were to go wrong.
chmod # change permissions on files
vi # text editing (it is ugly, but it is available on all unmodified unices that I have ever seen)
/usr/bin/bash # to run scripts
locate # to find files anywhere in the whole filesystem
which # to see 'which' application is the default.  You could have several copies of an application on the machine, but there is one that is used by default.
perl # to run perlscripts
grep # to search for files
cat # to search for contents of files
sudo # to act as root (or a sudoer)
ping # to check if an IP or domain name is live (or at least accepting ICMP Packets)  I know it's old-fashioned, but ping is more useful that a browser message "page cannot be found."
reboot # to reboot the machine
startx # to open a GUI session from TTY1 Terminal-only mode.
sudo dpkg --configure -a # to fix broken packages.  
dpkg -i # to install downloaded debian packages.
alien # to change rpm packages to debian ones so I can use dpkg -i to install them.
apt-get # to download application packages from a repo
aptitude # to download application packages from a repo, too.  Aptitude does a better job than apt-get solving dependency problems, AND has an ncurses graphical control panel that is useful when you are in a CLI-only situation.
valgrind # to run debugging traces on unhappy applications.
ssh # to connect to non-local servers securely.

```Since I am an alpha-tester by inclination, and I like the challenge of running a system that is "not all there." I may encounter more challenges at keeping a system running than sane people who wait for Stable releases.  I definitely find myself looking at the cli login more than most desktop users do.  Since YMMV, I am interested in what your top-used commands are and why.

Transparency Disclaimer: My plan with this project is to license the output as as creative commons license similar to [http://www.gp-field-guide.org.uk/](http://www.gp-field-guide.org.uk/) or with some other license that is in line with the GPL, and the spirit of Open-Source, so people who are interested can download it for free and Print-on-Demand copies can be purchased at a nominal fee.  If you are interested in being part of this documentation project, let me know. My email is [EMAIL="Wolf@HSI-US.com"]Wolf@HSI-US.com[/EMAIL]

---

### Post by aeiah on 2008-04-15
apart from what you've mentioned, i use python for running python scripts (much like your inclusion of perl) and i also use [awk](http://www.gnu.org/software/gawk/manual/gawk.html)

---

### Post by jbulcher on 2008-04-15
I don't see head nor tail in there ;)
```
head # to view the top lines in a file
tail # to view the last lines in a file - so useful for logs!
```

also useful:
```
apt-cache # search through application packages
sed # to replace text in a file
watch # to view the periodically updated contents of a file
```

---

### Post by LinuX-M@n1@k on 2008-04-15
I use everything you've mentioned without `alien`, `valgrind`, `perl` and `aptitude`
PS: Oh, and I use `vim` instead of `vi`

Edit: and `find` too :)

---

### Post by saphil on 2008-04-15
I have put a note on the OpenSolaris site to check interest level there.

I guess I use 

```
top # to watch the processes occasionally as well
```

---

### Post by Tom Mann on 2008-04-15
At the moment I'd say... man :)

---

### Post by pbhj on 2008-04-15
> **LinuX-M@n1@k said:**
> I use everything you've mentioned without `alien`, `valgrind`, `perl` and `aptitude`

Same here - also like $() and {}, eg.

```
head $(ls | grep foto)
```

Do head on the results of grepping the ls of the current directory. Oh, yeah did you mention pwd (particularly when using ssh, so there's another one)?

```
mv fotowall.{pro,pro2}
```

Great for moving and copying, also  find myself doing "nano !$" alot (open the last attribute on the previous command in nano, in fact all the history commands are pretty useful).

---

### Post by macogw on 2008-04-15
Please see the [top 10 used terminal commands thread](http://ubuntuforums.org/showthread.php?t=472090)

---

### Post by Mateo on 2008-04-15
fairly certain "ls", "cd", and "exit" would be the main 3 for most users.

---

### Post by LaRoza on 2008-04-15
> **Mateo said:**
> fairly certain "ls", "cd", and "exit" would be the main 3 for most users.

make, gcc, rm are up on my list.

---

### Post by GrueTamer on 2008-04-15
ls, cat, and grep are my biggest.  I don't even use cd, since my .zshrc has autocd enabled :guitar:

---

### Post by Mateo on 2008-04-15
> **LaRoza said:**
> make, gcc, rm are up on my list.

so, how do you make, gcc, and rm files if you first don't cd into the directory where they are and ls?  you just guess? ;)

---

### Post by LaRoza on 2008-04-15
> **Mateo said:**
> so, how do you make, gcc, and rm files if you first don't cd into the directory where they are and ls?  you just guess? ;)

I have aliases in my .bashrc.

For my code directory, "code" brings me there.

Also, when I cd to the specific directory, I do so once, whereas I make many times.

---

### Post by macogw on 2008-04-15
> **Mateo said:**
> so, how do you make, gcc, and rm files if you first don't cd into the directory where they are and ls?  you just guess? ;)

If you know where your files are...
I could 
rm /home/maco/Documents/tex/myresume.pdf
to delete my resume. I know where it is without cd'ing or ls'ing

---

### Post by Mateo on 2008-04-15
> **macogw said:**
> If you know where your files are...
I could 
rm /home/maco/Documents/tex/myresume.pdf
to delete my resume. I know where it is without cd'ing or ls'ing

if you're deleting 1 file.  and you know exactly where it is.  if you're deleting multiple files this becomes a pain (unless it's a complete directory of course).  much easier to just cd around.  prevents have to reenter commands if you get something wrong.

---

### Post by klange on 2008-04-15
I hit tab repeatedly to find out what files are in a particular directory most of the time. Tab completion is the greatest thing ever.

Probably grep and cat, followed by make and sudo *.

---

### Post by blithen on 2008-04-15
ls
cd
install - Alias for 'sudo apt-get install

---

### Post by swoll1980 on 2008-04-15
apt-get (remove, install, -f,  autoremove )
apt-cache search
nano (for command line text editing)
the obvious (ls, cd, exit, rm, mv, cp)
shutdown now (-r now)
chmod

---

### Post by saphil on 2008-04-16
> **macogw said:**
> Please see the [top 10 used terminal commands thread]("http://ubuntuforums.org/showthread.php?t=472090")

Thanks for this.  I especially like the 
history | awk '{print $2}' | awk 'BEGIN {FS="|"} {print $1}'|sort|uniq -c | sort -n | tail | sort -nr 
command that can tell you your top 5 things.  I suspect that will change daily, as new things appear on a persons plate to do.  I had 97 instances hidden under sudo, for instance, and running the line above as sude gave me a response "sudo: history: command not found."  I use sudo in favour of switching to root for the logging capability.

---

### Post by macogw on 2008-04-16
> **saphil said:**
> Thanks for this.  I especially like the 
history | awk '{print $2}' | awk 'BEGIN {FS="|"} {print $1}'|sort|uniq -c | sort -n | tail | sort -nr 
command that can tell you your top 5 things.  I suspect that will change daily, as new things appear on a persons plate to do.  I had 97 instances hidden under sudo, for instance, and running the line above as sude gave me a response "sudo: history: command not found."  I use sudo in favour of switching to root for the logging capability.

What you do with sudo goes in your own history, not root's.  if you want to see what command you ran with sudo, change that $2 to $2 $3 (i think) and it should print "sudo apt-get" and "sudo vim" and all that separately.  You could even | grep sudo before the sort to get just sudo stuff.

---

### Post by saphil on 2008-04-17
[http://lsc.hsi-us.com/tiki-index.php](http://lsc.hsi-us.com/tiki-index.php) is the project Wiki.  This was suggested by Sean Sprague  a couple of days ago to make responses easier.  
There is much and much to do to make this all make any sense.  Much fun to be had though!.

---

### Post by der_joachim on 2008-04-17
history -c --> Clears your command history. Just being paranoid. :)

---

### Post by hessiess on 2008-04-17
'make' and 'cd'

---

