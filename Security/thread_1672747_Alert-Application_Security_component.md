---
title: "Alert-Application Security component"
date: 2011-01-21
forum: Security
---

### Post by lentejas1987 on 2011-01-21
Hello members,
I have recently installed ubuntu as a partitioned os but am having someproblems early on.Honestly feel somewhat inadequate with the operating system and perhaps would like to lower my frustrated bar level a couple o' notches.:confused:Well if it wasn't for vista i wouldn't be able to be communicating with this wonderful forum since after using ubuntu's teminal yesterday it started acting up.or so it seems. I really started to like firefox:( so its kinda sad.But the main issue is begotten when i double click on web browser icon and the following message comes up:
 
[b]Alert-
Could not initialize the application Security Component.The most likely cause is problems with files in your application profile directory.Please check if directory has no read/write restitutions and your hard disk is not full or close to full.[/b]
 
Now if I were to tell you that one of the things that get my dander up in annoyance undoubtly is an open ended statement such as "the most likely cause is problems with files in your application".Moreover the mere idea of checking my directory again and setting some >more<free space perhaps through the before input output syatem just gives me goosebumps.I am a novice for crying out loud.I don't want to go through the painstaking process of partitioning the harddrive once again.:popcorn:it takes this long....with all jokes asideany suggestions on what this application security prompt really means.And what is the shortest most conscise way to go about it.

---

### Post by stamoulohta on 2011-01-21
Try this:

```
cd /home/$USER/.mozilla/firefox
```

Once there, ```
ls -o
``` to see if the directory with the weirdest name, (randomly generated) has reed/write privileges and if it belongs to you. (it has to begin with "**drwx**" followed by dashes, a number, and **your username**)

If that is not the case, do:
```
chmod 700 [weird name]
```

and/or,
```
chown [your username] [weird name]
```

it will probably work.

---

### Post by oldos2er on 2011-01-21
How much disk space did you give your Ubuntu installation? Can you post the output of **df -h** ? Have you tried creating a new profile in Firefox?

---

### Post by lentejas1987 on 2011-01-21
dear members,
I believe  gave the installation the minumum required size of less than 10 gb. Installing a new mozilla firefox profile seems quite a challenge when the browser does let me load a basic profile.
The command prompts ;
 
cd /home/$USER/.mozilla/firefox + ls-o
 
No such file or directory was found then i went ahead and tried the second command;
 
chmod 700 [weird name]
 
invalid user name came up but terminal asked to try chmod--help so I did this command worked and it gave a listing of key words=
 
usage: chmod
or:       chmod     -c,--changes
or:       chmod     -f,--silent
or:       chmod     -v,--Verbose
or:       chmod     -r,--recruiter
 
The chown commad ;chown [your username] [weird name]
was labeled as an invalid user.
 
Good command though this is how you really learn by troubleshooting.
[B]Alert-
Could not initialize the application Security Component.The most likely cause is problems with files in your application profile directory.Please check if directory has no read/write restitutions and your hard disk is not full or close to full.[/B]
 
*window still shows*

---

### Post by cariboo on 2011-01-21
If you create a new Firefox profile:

```
firefox -P
```

do you still get the error? Run the above command in a terminal.

---

### Post by oldos2er on 2011-01-21
> cd /home/$USER/.mozilla/firefox + ls -o

Did you substitute your user name for the $USER variable?

---

### Post by lentejas1987 on 2011-01-21
yes I replaced the user name with mine and I tried it with the user name as well.Both ways
the message was:
No such file or directory was found .If its case sensitive i copied the name exactly as i named the directory.
So under the weird name bracets do we apply this same name.

---

### Post by stamoulohta on 2011-01-22
Bash (command line), is case sensitive! 

Try using the TAB key to complete the names.

so:

```
cd /ho #PRESS TAB KEY
```

will write "cd /home/"

where "$USER" is, you may leave it like that but in CAPITAL. (and TAB won't work! press enter to continue.)

then, ```
cd .mo #TAB enter
```

and ```
cd fi #TAB enter
```

Now you should be in the wright place

```
ls -o
``` has a space before the dash!

Then find the name of the weird directory I talked about and change "[weird name]" with its name without the ""s and the []s. You can use TAB for it's completion again.

If in any stage the prompt ask you to be root, retype the command adding the word "sudo" in the beginning and give your administrator password when asked for it. Be careful not to do anything else except the above procedure though and close terminal when done. ;)

good luck
g.

---

### Post by stamoulohta on 2011-01-22
Might also want to read this:
[http://www.linuxcommand.org/]("http://www.linuxcommand.org/")

Is fun and will prove really helpful ;)

---

### Post by lentejas1987 on 2011-01-29
Dear Stamoulohta after finding the pathname for mozilla firefow this was the putput of the terminal:
lentejas@lentejas-desktop:~$ cd /home/cd .mozilla/firefox/ls -o
bash: cd: /home/cd: No such file or directory
lentejas@lentejas-desktop:~$ ls -o
total 13424
drwxr-xr-x 2 lentejas     4096 2011-01-20 16:55 Desktop
drwxr-xr-x 2 lentejas     4096 2011-01-14 11:11 Documents
-rw------- 1 lentejas        0 2011-01-20 15:28 ETHBkh
-rw-r--r-- 1 lentejas      357 2011-01-14 11:06 examples.desktop
-rw-r--r-- 1 lentejas  1581499 2011-01-20 10:38 Firefox_wallpaper.png
-rw-rw-r-- 1 lentejas 12104180 2011-01-08 19:52 libflashplayer.so
-rw------- 1 lentejas        0 2011-01-20 15:27 LJumAj
drwxr-xr-x 2 lentejas     4096 2011-01-14 11:11 Music
drwxr-xr-x 2 lentejas     4096 2011-01-20 10:37 Pictures
drwxr-xr-x 2 lentejas     4096 2011-01-14 11:11 Public
drwxr-xr-x 2 lentejas     4096 2011-01-14 11:11 Templates
drwxr-xr-x 2 lentejas     4096 2011-01-14 11:11 Videos
lentejas@lentejas-desktop:~$ 


I don't see the "weird name" route

---

### Post by oldos2er on 2011-01-29
Your command syntax is incorrect. There are two separate commands: ```
cd ~/.mozilla/firefox
ls -o
```
"~" is shorthand for /home/user

If it's easier to use nautilus, Ctrl-h will show you all hidden files and folders, of which .mozilla is one.

---

### Post by stamoulohta on 2011-01-30
I see you typed :```
cd /home/cd .mozilla/firefox/ls -o
```
and right after that, the system said:```
bash: cd: /home/cd: No such file or directory
```

so this is not the wright directory... This is actually your "/home/$USER" directory.

"cd" is a command and you cant use it twice before pressing ENTER. Try again and type :```
pwd [ENTER]
``` Whenever you want to see in which directory you are presently in. when you get to :```
/home/$USER/.mozilla/firefox
``` you're in the wright place.

PS: where "$USER" is your USERNAME.

Cheers ;)

---

### Post by Calvin V on 2011-10-26
I have the same problem.  I'm a first time Ubuntu user but I've been using Unix and firefox for a long time.  On some other systems, I even go into the weird name directory and modify the files in there so I know what it is.
But the problem is not due to the file permission of that directory.  That was the first thing I checked when I ran into this problem on last Friday, after some automated updates were run on Thursday.  When the problem happens firefox cannot get to the internet so the system, which I set up to work from home using VPN became useless.  After fiddling with it for a while I gave up and reinstalled everything.
It worked fine again after I reinstalled everything. But right after I installed the automated updates the problem happens again so I'm sure this time that this is due to one of those automated updates.
One of the updates gave a prompt that in order to install it, some conflicting versions of some libraries will have to be removed (sorry, I don't remember the name of the libraries) and I answered Yes.  I don't know if that has anything to do with the problem.
Thanks for any idea.  If nobody knows then I will have to reinstall again and make sure to turn off all automated updates this time.
BTW, it's a fresh installation on an empty hard disk with over 320G so there is plenty of disk space left.

---

### Post by Calvin V on 2011-10-26
I misremembered some details.  The two removed libraries are libavcodec53 and libautil51 when I installed the restricted extras.  Since everything still worked fine after that, those could not be the problems.

---

