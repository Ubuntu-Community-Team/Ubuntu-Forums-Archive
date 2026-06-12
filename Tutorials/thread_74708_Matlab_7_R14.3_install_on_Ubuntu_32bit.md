---
title: "Matlab 7 R14.3 install on Ubuntu 32bit"
date: 2005-10-12
forum: Tutorials
---

### Post by hangfire on 2005-10-12
0. Insert Matlab disk one.

1. Create installation directories, copy license. Note- what directory you run in matters!

  [INDENT][B] mkdir ~/matinst
   cd ~/matinst
   sudo mkdir /opt/matlab7
   sudo cp license.dat /opt/matlab7[/B]
[/INDENT]
2. Copy installation CD to install directory

  [INDENT]**  (cd /media/cdrom0; tar cvf - .) | tar xvf - **[/INDENT]


3. Edit install (kate install, emacs install, vi install). 

[INDENT]**emacs ./install&**[/INDENT]

4. Go to line 697 (**Ctrl-X G 697**) Comment line 697, Add line with kernel version number. When done it should  look like this:
[B]
#                ver=`/lib/libc.so.6 | head -n 1 | sed -e "s/^[^0-9]*//" -e "s/[ ,].*$//"`
		ver="2.6.10"
[/B]
5. Run install. Install to /opt/matlab. Let install script create links
   in /usr/local.
   
   [INDENT]**sudo sh -c ./install**[/INDENT]

6. Edit /opt/matlab7/bin/util/oscheck.sh

  [INDENT] [B]sudo chmod 755 /opt/matlab7/bin/util/oscheck.sh
   emacs /opt/matlab7/bin/util/oscheck.sh&[/B][/INDENT]

   Make the same change as step #3.


7. Run:

   [INDENT]**/opt/matlab7/etc/lmstart**[/INDENT]

8. If license manager starts OK, run matlab.

9. Clean-up install directory:

   [INDENT] **rm -fr ~/matinst**[/INDENT]

10. Enjoy!

HF

---

### Post by WW on 2005-10-14
Thanks for posting this.  I just installed matlab *before* I found this!  I followed the standard instructions, and matlab seems to work.  I'm guessing that if I first made the changes you described, I wouldn't get the error "/opt/matlab_rel14_sp3/bin/util/oscheck.sh: line 134: /lib/libc.so.6: Permission denied" that occurs each time I start matlab.  I had this problem in warty, too, but matlab seemed to work anyway, so I ignored it.  Is the problem just cosmetic?

The kernel in breezy is 2.6.12, so should your change now be ver="2.6.12"?

Also, I haven't (yet) installed java, but matlab seems to be working.  Why do you say to install java first?

---

### Post by hangfire on 2005-10-18
Thanks, I'm glad someone is reading my HOWTO.

To answer your questions,

My install bombed out completely before I fixed the oscheck line. I think all it wants out of "ver" is a number bigger than 2.4.Something. Heck, it might not even be a kernel number but a library version number. I just swagged something and it worked.

Java is supposed to be a requirement of Matlab. I happened to already have Sun Java installed. Perhaps Ubuntu already has java, or its a psuedo-requirement held over from the Windows version. If I have a chance to look at it or re-install it on Breezy, (or someone else can shed light) I'll update the HOWTO.

HF

---

### Post by Mandor on 2005-10-31
Thanks for the howto. I'll try it out and if it works with BreezyI'll be twice as thankful :)

---

### Post by n0ah420 on 2005-11-10
MATLAB uses its own built-in java so an external jvm is not required.  As for the libc error you can just ignore it.  It has no affect on the running of MATLAB, it is only a glibc check on startup which fails becuase of the debian permission schema.

---

### Post by kingsidy on 2005-11-10
I just want to mention that I also installed MATLAB R14 on my ubuntu laptop. as far as the lib.so.6 error i got rid of it by rignt clinking on the library and enabling all the permissions. Now it starts without a single error.

---

### Post by hangfire on 2005-11-16
Thanks for the feedback!

[QUOTE=n0ah420]MATLAB uses its own built-in java so an external jvm is not required.[/QUOTE]

Thanks, I fixed the HOWTO.

[QUOTE=n0ah420]As for the libc error you can just ignore it.  It has no affect on the running of MATLAB, it is only a glibc check on startup which fails becuase of the debian permission schema.[/QUOTE]

It failed to start Matlab on my machine... As for changing its permissions, I read somewhere that this method of checking libraries is deprecated, and may go away soon. Recent distro's are shipping libs with execute turned off for that reason, to discourage the practice. So, I'm leaving the HOWTO that way to give it more staying power.

Besides, I hate error messages.

---

### Post by lmp3 on 2005-11-27
x

---

### Post by theFallen on 2005-12-10
When I try to instll Matlab I get following error message. I tried to find glibc 2.2.5 but to no avail. Perhaps someone here can provide some help. Or is it something else?
I also trie it with install* -t :(

> ----------------------------------------------------------------------------
Warning: glibc 2.2.4      - Your version
         glibc 2.2.5      - MATLAB built using this version
----------------------------------------------------------------------------


----------------------------------------------------------------------------
Warning: glibc 2.2.4      - Your version
         glibc 2.2.5      - MATLAB built using this version
----------------------------------------------------------------------------

/tmp/10855tmwinstall/update/install/main.sh: line 244: 10965 Speicherzugriffsfehler  "$xsetup" $arglist 2>$tmp_file
-------------------------------------------------------------------

    An error status was returned by the program 'xsetup',
    the X Window System version of 'install'. The following
    messages were written to standard error:


    Attempt to fix the problem and try again. If X is not available
    or 'xsetup' cannot be made to work then try the terminal
    version of 'install' using the command:

            install* -t    or    INSTALL* -t

-------------------------------------------------------------------
/tmp/10855tmwinstall/update/install/abort.sh: line 15: /tmp/10855tmwinstall/update/install/cleanup.sh: Datei oder Verzeichnis nicht gefunden


Speicherzugriffsfehler = Memory Access Failure
Datei oder Verzeichnis nicht gefunden = File Or Folder Not Found

---

### Post by neoflight on 2006-02-20
hi,

i tried to install matlab 7.01.r14.sp3

i got it installed all well.. but it doesnt work :(
i cant even find the matlab command in $matlab/etc.
no link was created in /usr/local/bin eventho i said 'ok' when i asked in the gui.

there is no lmstart script file in $matlab/etc either.... what is happening here?

i changed the file permissions for lib stuff using chmod 755 ans so i didnt get an error...

please help
thanks

---

### Post by n0ah420 on 2006-02-20
What versin are you running?  7.0.1 is R14SP1 and you refered to R14SP3 which is 7.1.  The executable script will be in $MATLAB/bin.  Run $MATLAB/install_matlab and accept all of the defaults (press enter).  See if that solves your script creation problem (stuff missing in bin and etc).

As for the xsetup error in the previous post, it means exactly what it says.  It was unable to execute xsetup.  Did you try with the -t flag?  You will want to run sudo install instead a su then install to get rid of that error.  Also make sure you are not executing directly on the cd-rom but from within the installation directory.

Hope that helps.

---

### Post by neoflight on 2006-02-22
[QUOTE=n0ah420]What versin are you running?  7.0.1 is R14SP1 and you refered to R14SP3 which is 7.1.  The executable script will be in $MATLAB/bin.  Run $MATLAB/install_matlab and accept all of the defaults (press enter).  See if that solves your script creation problem (stuff missing in bin and etc).

As for the xsetup error in the previous post, it means exactly what it says.  It was unable to execute xsetup.  Did you try with the -t flag?  You will want to run sudo install instead a su then install to get rid of that error.  Also make sure you are not executing directly on the cd-rom but from within the installation directory.

Hope that helps.[/QUOTE]


Thanks a lot. I manged to install matlab succesfully. the verison is 7.1 R14-SP3. it was a typo in my last post. 

Now when I am trying a simple plot command, it returns segmentation violation error. 
also i tried to start matlab using matlab -check_malloc as suggested somewhere in mathworks...but i still get eh segmentation violation error....

there are many commands missing from matlab too... one such is the command 'why' .... help ????

---

### Post by n0ah420 on 2006-02-22
It should not seg fault as I am running that version on my ubuntu laptop.  To get your command functionality back you may want to try this:

```
>> restoredefaultpath;matlabrc
>> save path
>> rehash toolboxcache
```

Also make sure you don't have any extra pathdef.m files on your path (as well as any modified start files).  if you are still having issues I would suggest contacting MATLAB support as they are very helpful in solving these issues.

---

### Post by neoflight on 2006-02-22
Thanks a lot.
That solved it.. however ;;;;;;;;;;;;;)

There were many other problems... no rehash command found, savepath was not working, matlabrc not found etc....

here is how i solved the problems....

1. matlabrc.m and pathdef.m were not in $matlab/toolbox/local
they were in 
```
$matlab/toolbox/local/template !!!
```
I copied those to 
```
$matlab/toolbox/local 
```

2. there was nothing in pathdef.m so i was getting error as to not able to set path and some colordef not working etc... but without failing to launch matlab. then i tried those (previous post). 

savepath could not be used because of permission error.

3. login as root. using su

and then lanuch matlab

```
>> restoredefaultpath ; matlabrc
>> savepath 
```

4. exit and relogin as user and lauch matlab.

warnings related to toolbox cache...this happens when a new verison is installed. so should appear only at the first launch. the data from this launch will be saved automatically for future sessions until a new version is installed. 

5. restart matlab and bingo. 

thanks

---

### Post by n0ah420 on 2006-02-23
No problem.  Looks like it was just a bad initial install as all of those actions should have been done for you by the installer.  Glad you are up and running.

---

### Post by neoflight on 2006-02-23
[QUOTE=n0ah420]No problem.  Looks like it was just a bad initial install as all of those actions should have been done for you by the installer.  Glad you are up and running.[/QUOTE]

Quite possibly !!

Now thats its working, how can i get a lshortcut/link on a menu or on the gnome panel? i tried giving it using application menu editor. But its only good for the splash screen... 
ideas?

---

### Post by n0ah420 on 2006-02-23
MATLAB needs to be attached to the terminal.  Just click the run in terminal checkbox and you should be all set when creating the launcher.  You can also give flags to MATLAB startup like:

```
/path/to/matlab -nodesktop -nosplash
```

This will launch MATLAB as a command prompt.  The you can type:

```
>> desktop 
```

if you need the gui.

---

### Post by neoflight on 2006-02-23
[QUOTE=n0ah420]MATLAB needs to be attached to the terminal.  Just click the run in terminal checkbox and you should be all set when creating the launcher.  You can also give flags to MATLAB startup like:

```
/path/to/matlab -nodesktop -nosplash
```

This will launch MATLAB as a command prompt.  The you can type:

```
>> desktop 
```

if you need the gui.[/QUOTE]

Thanks. that works !!! eventhough i have a terminal floating around....

---

### Post by neoflight on 2006-03-14
Hi,

I have a new [howto]("http://ubuntuforums.org/showthread.php?t=143826") in place with some information collected from this thread. This essentially explains how I managed to install matlab 7.1R13 SP-3 in breezy. 

I would like to acknowledge the info people have provided here and thanks a lot. please feel free to comment.

---

### Post by n0ah420 on 2006-03-14
I just wanted to make an additional comment.  I have learned that if you create a launcher with the following command:

```
$MATLAB/bin/matlab -desktop
```

You can launch the MATLAB without a terminal.  You can read the launch options right out of the $MATLAB/bin/matlab script.

---

### Post by neoflight on 2006-03-14
[QUOTE=n0ah420]I just wanted to make an additional comment.  I have learned that if you create a launcher with the following command:

```
$MATLAB/bin/matlab -desktop
```

You can launch the MATLAB without a terminal.  You can read the launch options right out of the $MATLAB/bin/matlab script.[/QUOTE]


Thanks a bunch ...that was nice..i will update the howto with it...

---

### Post by emamm on 2006-04-02
Hello

I followed your instructions but matlab installer returned

-------------------------------------------------------------------

    The following messages were written to standard error
    while running 'xsetup' the X Window System version
    of 'install'.

        sh: /media/cdrom0/update/install/backend: /bin/sh: bad interpreter: Permission denied

There is no matlab file under bin.  Matlab won't run.

I am running dapper

Thanks

Ed

---

### Post by n0ah420 on 2006-04-06
Ed,

You can't execute directly on the cd-rom.  Create a folder for MATLAB:

/usr/local/bin/MATLAB

Put your license.dat file in there.  While you are in your new directory call the installer:

pwd:/usr/local/bin/MATLAB$>/cdrom/install

That should take care of it.

---

### Post by emamm on 2006-04-07
Hello

I am not executing matlab from a cd.I have installed matlab on the hard disk. The problem is that there is no matlab script to be called. Somehow kubuntu wrecks the installation process.

Many thanks

Ed

---

### Post by n0ah420 on 2006-04-07
Ahh sorry about that.  Try running $MATLAB/bin/install_matlab.  Accept all defaults to recreate those scripts.

---

### Post by emamm on 2006-04-12
Great!  It worked.  Many many thanks

---

### Post by spockrock on 2006-06-29
I would like to point out one thing. I followed this guide a while back and it worked perfectly this time around on dapper lmstart wasnt in the etc folder, I dunno why, but I had to run /opt/matlab7/install_matlab (as sudo) and then follow along for it to work before I could run /opt/matlab7/etc/lmstart

---

### Post by Icarosaurus on 2006-10-07
Thank you for the HOWTO!

I followed you instructions, just ignored the error output in the terminal after the graphical installation concluded and executed ```
sudo matlab_install
```.

Almost everything goes fine, but Matlab crashes when i try to modify plots in their figure windows (i.e. rotate them). That's not an enormous problem for me at the moment.

My Matlab version is 7.0.0.19901 (R14).

I think it's better for who reads your HOWTO that you add the "matlab_install" detail ;) 

thank you again 
bye!

---

### Post by Icarosaurus on 2006-10-07
One more thing: I don't need to run lmstart to get Matlab running!

---

### Post by Eigenwert on 2006-11-24
Thanks for the HOWTO. It even works on Edgy!

EW

---

### Post by maarix on 2006-11-26
Hello

Could you use your symbolic toolbox as well? I could not find any solution to get it working.

thx
martin

---

### Post by n0ah420 on 2006-11-26
> **maarix said:**
> Hello

Could you use your symbolic toolbox as well? I could not find any solution to get it working.

thx
martin
Symbolic Math is only for 32-bit so if your arch is 64-bit it won't work.  If you are on 32-bit however, contact support.  They are pretty helpful and free for install issues.

---

### Post by christophe.hoel on 2006-12-11
> **hangfire said:**
> 0. Insert Matlab disk one.

1. Create installation directories, copy license. Note- what directory you run in matters!

  [INDENT][B] mkdir ~/matinst
   cd ~/matinst
   sudo mkdir /opt/matlab7
   sudo cp license.dat /opt/matlab7[/B]
[/INDENT]
2. Copy installation CD to install directory

  [INDENT]**  (cd /media/cdrom0; tar cvf - .) | tar xvf - **[/INDENT]


3. Edit install (kate install, emacs install, vi install). 

[INDENT]**emacs ./install&**[/INDENT]

4. Go to line 697 (**Ctrl-X G 697**) Comment line 697, Add line with kernel version number. When done it should  look like this:
[B]
#                ver=`/lib/libc.so.6 | head -n 1 | sed -e "s/^[^0-9]*//" -e "s/[ ,].*$//"`
		ver="2.6.10"
[/B]
5. Run install. Install to /opt/matlab. Let install script create links
   in /usr/local.
   
   [INDENT]**sudo sh -c ./install**[/INDENT]

6. Edit /opt/matlab7/bin/util/oscheck.sh

  [INDENT] [B]sudo chmod 755 /opt/matlab7/bin/util/oscheck.sh
   emacs /opt/matlab7/bin/util/oscheck.sh&[/B][/INDENT]

   Make the same change as step #3.


7. Run:

   [INDENT]**/opt/matlab7/etc/lmstart**[/INDENT]

8. If license manager starts OK, run matlab.

9. Clean-up install directory:

   [INDENT] **rm -fr ~/matinst**[/INDENT]

10. Enjoy!

HF

hello,
I try to run your method but it blocks in point 5.

I receive such a message : Permission denied (see below)

tof@tof-laptop:~$ sudo sh -c /home/tof/software/cd1/install
Password:
sh: /home/tof/software/cd1/install: Permission denied
tof@tof-laptop:~$ sudo -s
root@tof-laptop:~# sudo sh -c /home/tof/software/cd1/install
sh: /home/tof/software/cd1/install: Permission denied
root@tof-laptop:~# sudo sh /home/tof/software/cd1/install
-------------------------------------------------------------------

    The following messages were written to standard error
    while running 'xsetup' the X Window System version
    of 'install'.

        sh: /home/tof/software/cd1/update/install/backend: Permission deniedtof@tof-laptop:~$ sudo sh -c /home/tof/software/cd1/install
Password:
sh: /home/tof/software/cd1/install: Permission denied
tof@tof-laptop:~$ sudo -s
root@tof-laptop:~# sudo sh -c /home/tof/software/cd1/install
sh: /home/tof/software/cd1/install: Permission denied
root@tof-laptop:~# sudo sh /home/tof/software/cd1/install
-------------------------------------------------------------------

    The following messages were written to standard error
    while running 'xsetup' the X Window System version
    of 'install'.

        sh: /home/tof/software/cd1/update/install/backend: Permission denied

-------------------------------------------------------------------
exec: 301: /home/tof/software/cd1/install: Permission denied
root@tof-laptop:~# 


-------------------------------------------------------------------
exec: 301: /home/tof/software/cd1/install: Permission denied
root@tof-laptop:~# 

Do you have an idea ???
thanks, Chris:confused:

---

### Post by maarix on 2006-12-14
my solution was to replace the original libmaple.so with [http://www.mathworks.com/support/solutions/attachment.html?resid=1-32V31N&solution=1-1BDU5](http://www.mathworks.com/support/solutions/attachment.html?resid=1-32V31N&solution=1-1BDU5)

---

### Post by sumadartson on 2007-02-04
Hola,

Tried installing matlab today, but so far no succes. Got stuck on the the libc.so.6 error, changed the permissions to executable, but no succes. 

I still get:
```

/bin/sh: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory

```

Any suggestions?

---

### Post by platinummonkey on 2007-02-06
excellent how to

@suma - make sure the two files that you edit, that you comment **"ver=`/lib/libc.so.6 | head -n 1 | sed -e "s/^[^0-9]*//" -e "s/[ ,].*$//"`"** and then add another line under it with your version **" ver="2.6.10""**  mine was 2.6.17, type **uname -r** and only use the first 3 sets of digits.  on the second file I found **2** places where i had to do that, and only once on the first file. your just going to have to find them, they were about mid-way.

---

### Post by skywatcher on 2007-02-13
Please can someone help me with a Matlab installation? I'm trying to install Matlab R2006b using the guidelines given by hangfire on this thread in 2005. It doesn't work, nor do the installation instructions given on the Matlab CD case.

It would be much appreciated if someone could help me with this. I want to move completely away from Windows, but without Matlab this will not be possible.

Thanks

---

### Post by sumadartson on 2007-02-13
Skywatcher,

What exactly is going wrong? Do you get an error report? Does it die a horrible, silent death? Does the gui not show?

---

### Post by skywatcher on 2007-02-13
Hi sumadartson

Thanks for your response. This is what happens:

At step 4:
4. Go to line 697 (Ctrl-X G 697) Comment line 697, Add line with kernel version number. When done it should look like this:

# ver=`/lib/libc.so.6 | head -n 1 | sed -e "s/^[^0-9]*//" -e "s/[ ,].*$//"`
ver="2.6.10"

I use ' ver="2.6.15" '.

At step 5:
5. Run install. Install to /opt/matlab. Let install script create links
in /usr/local.

sudo sh -c ./install 

This is how far I get, with this message being returned:
"The installer cannot be run when your current directory is on the CD.
Change to the target MATLAB installation directory and rerun the installer."

Note that at this point I am still in ~/matinst

Any suggestions?

---

### Post by giuseppe.dem on 2007-04-19
If all previous instruction do not solve the problem,
maybe you have a conflict with some LANG pack,
Therefore, just try

export LANG=c; matlab

I solved the segmentation violation problem.

Giuseppe

---

### Post by skywatcher on 2007-04-20
Thanks for the reply, Giuseppe.

I have since successfully installed MATLAB by following the instructions on the MathWorks web site at
[http://www.mathworks.com/access/helpdesk/help/base/install/install.html]("http://www.mathworks.com/access/helpdesk/help/base/install/install.html")

---

### Post by Emunoz on 2007-05-27
Just in case is helpful for anybody

I have just installed matlab, and I was worried because at the end of the installing process (after change the 3 cd's)  I got a message:

The MATLAB installer program is finished.
blablabla......
exec: 301: /media/cdrom0/install: Permission denied

So I didn't know what to do, I thought it was a problem with the licence.lic file so I tried to modify it, but at the end I realized there was no any problem, and I just had to run another installer 

/usr/local/matlab7# install_matlab

and follow the instructions and that was all!!

good luck

bye

Eduardo

---

### Post by chaizak on 2007-05-28
sorry guys i am kind of a noob on linux i have a question i am stack on step 5 it says that 
Setup aborted . . .
The installer cannot be run when your current directory is on the CD.
Change to the target MATLAB installation directory and rerun the installer.

when i use the 
./install
command i tried assign  a directory like the following but nothing at all happens
./install [-</opt/matlab7>] [-x]

is there something i am missing? the think i haven't really managed to do is
Run install. Install to /opt/matlab. Let install script create links in /usr/local.
any help would be really appreciated as i need it sorted out soon

---

### Post by lumberjack on 2007-06-25
When you install matlab, you want to be in the directory that you want to install to.
for me, i wanted to install to the folder Matlab2007a on the drive sda7, so in a terminal i typed

       cd /media/sda7

then i created the directory matlab2007a using

       mkdir matlab2007a

now my terminal window looks like this:

       lumberjack@log: /media/sda7/matlab2007a$

lumberjack is my username and log is the name of my computer.
now copy the license.dat file into the installation directory.  You can do this in the terminal window or in your file browser

Okay, now that we're in the location we want to install in, we have to run the install script.   However, it's located in a different directory, so we have to tell the computer to run the file while staying in the current directory.  so you should type in 

      sudo ./cddirectory/install

replacing cddirectory with the directory of your cd drive.  The ./tells the computer to run the file install as a script.  You should have to enter your password to continue.

This should solve the problem you're having

---

### Post by skywatcher on 2007-06-26
The MATLAB installation instructions are correct in every detail except for one thing: On Ubuntu Linux your installation CD/DVD is automatically mounted in read-only mode, so the install script cannot run. What you have to do is this:

Insert the CD/DVD and let it mount, then unmount it manually:

```
umount /media/cdrom
```

Following this, re-mount it:

```
sudo mount -t iso9660 /dev/cdrom /media/cdrom
```

Check that the CD/DVD is mounted with execute permission:

```
cd /media/cdrom
ls -la
```

Then cd back to your install directory and continue with the installation. If you're installing from a DVD, you only have to carry out the above steps once -- if you're installing from CDs, you have to remount everytime you change the disk. Alternatively, you could change /etc/fstab to always mount in execute mode.

Hope this helps.

---

### Post by jw5801 on 2007-06-29
Has anyone got this working on 64bit? I couldn't see a howto anywhere so I figure that this one should work ok on both architectures?

---

### Post by shelzacat on 2007-09-10
I recently bought the student version of Matlab & Simulink R2007a, and have tried using their installation instructions to no avail. Then while searching I came upon this forum, which after using the advice here I have still been unable to install Matlab on my Ubuntu - Feisty Fawn 7.04 desktop... I'm rather frustrated...

my most frequent error message has been 
/bin/sh: bad interpreter: Permission denied

I've tried a number of things, even using sudo su to have root access...
any good ideas?? I would greatly appreciate the help so I can complete my homework at home instead of in a Windows lab at odd hours of the night...

Thank you,

-Shelz

---

### Post by skywatcher on 2007-09-10
Hi Shelzacat

Did you try my suggestions given in a previous post on this thread?

What desktop environment are you using?  If you're using Gnome or KDE your CD drive may mount without execute permission irrespective of what is in /etc/fstab. If this is the case, you have to first unmount the drive and then re-mount it again with

```
sudo mount -t iso9660 /dev/cdrom media/cdrom
```.

Please note the spaces between different parts of the command!

Other than this, I don't know what the problem might be. I have successfully installed different versions of MATLAB on Dapper Drake, including release 13 student version.

Good luck!

PS: If you still don't get it right, maybe you want to send us the exact steps and commands that you tried?

---

### Post by um204 on 2007-09-14
I have a problem with Launcher, please help.  

I created one with  'matlab -nodesktop'  and ticked it to run in terminal.  But I only got the splash screen without a terminal, nothing.    I use Xubuntu but I have installed E17 desktop.   This behaviour is the same in both Xfce and E17.    'matlab -desktop' works fine but I don't like the GUI.  

A while ago I installed matlab on another Xubuntu (with no E17) and made the same launcher, it works fine but sometimes two terminals started.  I think -nodesktop is by default with 'matlab' command in the launcher, does that cause two terminals to start if I use 'matlab -nodesktop'?   I'm quite a beginner here.

---

### Post by um204 on 2007-09-14
The above problem is solved .. by not using the 'run in termial' option

But instead use the command,  Terminal -e "matlab -nodesktop",  it works as I wanted

---

### Post by princeza on 2008-04-03
> **skywatcher said:**
> The MATLAB installation instructions are correct in every detail except for one thing: On Ubuntu Linux your installation CD/DVD is automatically mounted in read-only mode, so the install script cannot run. What you have to do is this:

Insert the CD/DVD and let it mount, then unmount it manually:

```
umount /media/cdrom
```

Following this, re-mount it:

```
sudo mount -t iso9660 /dev/cdrom /media/cdrom
```

Check that the CD/DVD is mounted with execute permission:

```
cd /media/cdrom
ls -la
```

Then cd back to your install directory and continue with the installation. If you're installing from a DVD, you only have to carry out the above steps once -- if you're installing from CDs, you have to remount everytime you change the disk. Alternatively, you could change /etc/fstab to always mount in execute mode.

Hope this helps.

Thank you very much. This did the trick.

---

### Post by useright on 2008-09-06
hi
I download matlab from mathwork to the fold on my ubuntu desktop. Which file should I choose to install matlab on ubuntu and what's the command?

thanks ahead
frank

---

### Post by jw5801 on 2008-09-06
Open a terminal and sudo to root:
```
sudo -i
```
Then change to the directory you're keeping the files and run the install script in the folder.
```
cd /home/<your-username>/Desktop/<foldername>/
./install
```

---

### Post by 3DRaven on 2009-04-06
Hello.
I am russian...bad english :)

Permission denied problem solved.
Symply install matlab to root file system (example /opt/matlab;/dev/sda1...root).
If i install matlab to user filesystem (/mnt/data; /dev/sda4), i recive "permission denied".

At all.
Best regards.

---

### Post by abhinav.p on 2009-04-08
ok with the help of another thread i was able to install matlab using an iso file.the installation was sucessful and a matlab folder was created in my home folder.the problem is i cannot find a way to launch it.googling did not help.can u help?is there no other graphical way i can launch an installed application?

---

### Post by HelderC on 2011-08-20
Hi folks.

I'm with problem at installation of Matlab 7 R14 on Ubuntu 11.04.
When in ask for the cd 2, I specified the dir where is the cd 2, but it ask again for de cd2. It doesnt reconize the cd2, and doesnt show any error!

Can anyone help me?

---

