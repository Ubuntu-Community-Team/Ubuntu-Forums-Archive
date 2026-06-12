---
title: "[Server 12.04] 368 broken packages after a fresh install"
date: 2012-06-03
forum: Server Platforms
---

### Post by RadomE on 2012-06-03
Hello everyone!
I've pasted below my aptitude screen
I've got this situation just after a fresh install of 12.04 (x86_64) server.

What should I do?


```
Actions  Undo  Package  Resolver  Search  Options  Views  Help
C-T: Menu  ?: Help  q: Quit  u: Update  g: Download/Install/Remove Pkgs
aptitude 0.6.6                                                                                   #Broken: 368 Will use 426 MB of disk space  DL Size: 148 MB
--\ Installed Packages (465)
  --\ admin - Administrative utilities (install software, manage users, etc) (64)
    --\ main - Fully supported Free Software. (63)
iB    acpid                                                                                                                      1:2.0.10-1ubun 1:2.0.10-1ubun
i     adduser                                                                                                                    3.113ubuntu2   3.113ubuntu2
iB    apparmor                                                                                                                   2.7.102-0ubunt 2.7.102-0ubunt
iB    apt                                                                                                                        0.8.16~exp12ub 0.8.16~exp12ub
iB    apt-transport-https                                                                                                        0.8.16~exp12ub 0.8.16~exp12ub
iB    apt-utils                                                                                                                  0.8.16~exp12ub 0.8.16~exp12ub
i A   apt-xapian-index                                                                                                           0.44ubuntu5    0.44ubuntu5
i A   aptitude                                                                                                                   0.6.6-1ubuntu1 0.6.6-1ubuntu1
iB    at                                                                                                                         3.1.13-1ubuntu 3.1.13-1ubuntu
iB    base-files                                                                                                                 6.5ubuntu6     6.5ubuntu6    
iB    base-passwd                                                                                                                3.5.24         3.5.24        
i     command-not-found                                                                                                          0.2.46ubuntu6  0.2.46ubuntu6
iB    command-not-found-data                                                                                                     0.2.46ubuntu6  0.2.46ubuntu6 
iB    cron                                                                                                                       3.0pl1-120ubun 3.0pl1-120ubun
i     debconf                                                                                                                    1.5.42ubuntu1  1.5.42ubuntu1
i     debconf-i18n                                                                                                               1.5.42ubuntu1  1.5.42ubuntu1
iB    dmsetup                                                                                                                    2:1.02.48-4ubu 2:1.02.48-4ubu
Advanced Configuration and Power Interface event daemon
Some dependencies of acpid are not satisfied:                                                                                                                &#9618;
                                                                                                                                                             &#9618;
                                                                                                                                                             &#9618;
  * acpid conflicts with acpid:i386                                                                                                                          &#9618;
                                                                                                                                                             &#9618;
                                                                                                                                                             &#9618;
The following packages conflict with acpid:                                                                                                                  &#9618;
                                                                                                                                                             &#9618;
                                                                                                                                                             &#9618;
  * acpid:i386 conflicts with acpid                                                                                                                          &#9618;
                                                                                                                                                             &#9618;
                                                                                                                                                             &#9618;
                                                                                                                                                             &#9618;
                                                                                                                                                             &#9618;
                                                                                                                                                             &#9618;
                                                                                                                                                             &#9618;
                                                                                                                                                             &#9618;
                                                                                                                                                             &#9618;
                                                                                                                                                             &#9618;
                                                                                                                                                             &#9618;
                                                                                                                                                             &#9618;
Unable to resolve dependencies.

```

---

### Post by Paddy Landau on 2012-06-03
Ubuntu tends to use apt-get rather than aptitude (I realise that there is some overlap).

Try the following commands to repair and update.
```
sudo apt-get --fix-broken install
sudo dpkg --configure --pending
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by RadomE on 2012-06-05
Thank you for your advice Paddy, but it did not work :(

```
10:59:17 cuda:~ > sudo apt-get --fix-broken install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
11:00:01 cuda:~ > sudo dpkg --configure --pending  
11:00:25 cuda:~ > sudo apt-get update

"" Mirror list ""

11:00:48 cuda:~ > sudo apt-get dist-upgrade        
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

Still have 300+ broken packages.

---

### Post by Paddy Landau on 2012-06-05
> **RadomE said:**
> Still have 300+ broken packages.
Sorry, I'm a bit confused. Your commands ran fine and showed no problem.

What specifically makes you think that you have broken packages?

---

### Post by RadomE on 2012-06-05
> **Paddy Landau said:**
> Sorry, I'm a bit confused. Your commands ran fine and showed no problem.

What specifically makes you think that you have broken packages?

Look at my first post: the aptitude screen shows a lot of packages marked with "iB" like ```
iB    acpid
``` "iB" means Installed with broken dependencies.

In addition aptitude states: 
```
Some dependencies of acpid are not satisfied:                                                                                                                


  * acpid conflicts with acpid:i386
```

Last:
```
#Broken: 368 Will use 426 MB of disk space  DL Size: 148 MB
--\ Installed Packages (465)
```

What have I done wrong? :(

---

### Post by IanCBray on 2012-06-05
*** UBUNTU-NOOB ALERT ***
Hello, Ev'body... 
I'm having some strangeness happen with aptitude too...  I guess it's more precise to say I find aptitude strange... 
Don't get me wrong-- I'm sure once I get used to it... I'll MUCH prefer apt to source-downloading, compiling, waiting... waiting... grabbing a sandwich... waiting... but for NOW... I'M stuck.  Moderators-- please forgive me if I digress, I've read and re-read posts on apt to try to learn the package installer but I can't figure out what -I- have done in order to -undo-.

HW:  Dell Inspiron 1100  512MB Ram 20GB HD  A32 Bios Updated
  ( CRAZY--I KNOW )
SERVER 12.04 Installed AND works pretty well!!!
   I don't -need- X-windows which is why I chose SERVER
   I'm -VERY- vision-impaired and would rather use my cmdline.

I'm trying to get DOSBOX installed on this LT because I need an
OldSchool environment for testing...  LONG STORY...

when I do:

sudo apt-get install -f dosbox

I am told I have incomplete dependancies and/or held packages.
Here:
ian@puck:~$ sudo apt-get install -f dosbox
[sudo] password for ian:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 dosbox : Depends: libsdl-sound1.2 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
ian@puck:~$

Ok... I'm fine with installing libsdl-sound1.2 but when I try... I get yet MORE depend flags...

ian@puck:~$ sudo apt-get install -f libsdl-sound1.2
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libsdl-sound1.2 : Depends: libmikmod2 (>= 3.1.10) but it is not installable
                   Depends: libsmpeg0 but it is not installable
                   Depends: libspeex1 (>= 1.1.8) but it is not installable
                   Depends: libvorbisfile3 (>= 1.1.2) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
ian@puck:~$

OK... so I look at HELD pkgs:

ian@puck:~$ sudo aptitude search ~ahold

I have to " >> bigheldpkgs.list " cause I gt 575 lines of pkgs that I don't know what to do with.  Did skroo-up the install??  

I've tried '--fix-broken install' and 'update' flags and I guess I... no... I know I don't know what to do now.  I'm not used to aptitude yet... I'm just used to Old Slackware & Mandrake & Gentoo... This is my first UBUNTU Box...  Where do I go?  What do I look at?  Suggestions?  

Thanks in advance!
Respecftully,  Ian

---

### Post by Paddy Landau on 2012-06-05
> **IanCBray said:**
> *** UBUNTU-NOOB ALERT ***
Ian, you have hijacked someone else's thread. Please start your own.

> **RadomE said:**
> Look at my first post...
Well, Radom, I am not an expert; but I see that the commands I gave you finished fine. So, as far as I can tell, there is no problem.

Are you experiencing any problems that made you refer to aptitude? If so, please let me know, so I can understand better. If not, then frankly I wouldn't worry about it.

---

### Post by RadomE on 2012-06-05
> **Paddy Landau said:**
> 
Well, Radom, I am not an expert; but I see that the commands I gave you finished fine. So, as far as I can tell, there is no problem.

Are you experiencing any problems that made you refer to aptitude? If so, please let me know, so I can understand better. If not, then frankly I wouldn't worry about it.

Well, in fact I'm not experiencing any problem so far.
Ok then, if something strange will happen I'll report it. :)
Thank you very much!

---

### Post by Paddy Landau on 2012-06-06
> **RadomE said:**
> I'm not experiencing any problem so far.
Excellent. Please [mark the thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").

I just had a thought: how did you get the Aptitude screen in your first post? Let me know, and I'll try it on my machine to see what happens.

---

### Post by LHammonds on 2012-06-06
> **Paddy Landau said:**
> how did you get the Aptitude screen in your first post? Let me know, and I'll try it on my machine to see what happens.
Simply type "aptitude" and it will bring up an ASCII menu that you can navigate.

My servers look just like his screen except without the "B"

LHammonds

---

### Post by Paddy Landau on 2012-06-06
Hmm, aptitude is not even installed by default. It has a funny description:
> aptitude is also Y2K-compliant, non-fattening, naturally cleansing,
and housebroken.I don't have broken packages listed in aptitude, but again I wouldn't worry about it if apt-get is happy.

---

### Post by RadomE on 2012-06-12
I got the solution! :)

```
sudo apt-get purge aptitude
sudo apt-get install aptitude
```

There was something wrong in aptitude's package list.
In fact the :i386 packages were not installed but somehow aptitude were marking them as broken.
After a complete aptitude reinstall the package list got fixed.

---

### Post by Paddy Landau on 2012-06-12
> **RadomE said:**
> I got the solution! ...
Fantastic! Who would have thought reinstalling a package would fix it? The *purge* option must have been the important bit.

---

### Post by IanCBray on 2012-06-12
> **Paddy Landau said:**
> Fantastic! Who would have thought reinstalling a package would fix it? The *purge* option must have been the important bit.

Whoa... isn't that a chapter out of Microsoft's How Too? 
LOL!  
Congrats!  Wish I'd thought of it! LOL

Cheers!

---

### Post by Paddy Landau on 2012-06-12
> **IanCBray said:**
> Whoa... isn't that a chapter out of Microsoft's How Too?LOL, I was thinking of that, too. "Have you turned it off and on? Have you reinstalled the program?"

---

### Post by RadomE on 2012-06-12
> **Paddy Landau said:**
> LOL, I was thinking of that, too. "Have you turned it off and on? Have you reinstalled the program?"

You can imagine my surprise when, trying to remove a useless conflicting package (...:i386) using apt, I got: "Package ... is not installed, so not removed".
Then I realized that the problem was somewhere in aptitude's file set.

It is still hard to believe how this could happen just after a fresh install, anyway, use apt and don't trust aptitude! :D

---

### Post by Paddy Landau on 2012-06-13
> **RadomE said:**
> It is still hard to believe how this could happen just after a fresh install, anyway, use apt and don't trust aptitude! :D
Well, apt-get, not aptitude, is the supported method in Ubuntu, so that makes sense.

---

### Post by LHammonds on 2012-06-13
> **Paddy Landau said:**
> Fantastic! Who would have thought reinstalling a package would fix it? The *purge* option must have been the important bit.
When you use the "purge" option, it not only uninstalls the application but it also removes configuration / data files that it normally would leave.  So it probably was not an aptitude program issue as much as it was a data file (corrupted) issue.

I have installed 10.04 and 12.04 many times and have not had a single problem with aptitude.  However, I have also been running all of them in a VERY stable virtual environment.  I'm sure other factors can come into play when installing on bare-metal or using not-so-stable virtual software.  By that, I am referring to VirtualBox.  I had all kinds of quirky issues just getting a 10.04 server setup and running.  It would break in different ways after a dozen different installs.  Granted, it was on a version several revisions back from the current version of VirtualBox and the current version seems fairly stable now with Ubuntu.

**EDIT:** RadomE, thanks for share the solution.

LHammonds

---

### Post by Paddy Landau on 2012-06-14
> **LHammonds said:**
> When you use the "purge" option, it not only uninstalls the application but it also removes configuration / data files that it normally would leave.
As a clarification, *purge* removes only system-wide settings (which are, of course, applicable for aptitude). It does not reset user-level settings, which is applicable for most applications (e.g. GIMP, Firefox, Ubuntu One).

That confuses many ex-Windows users, who expect reinstallation to reset everyone's settings to default.

---

