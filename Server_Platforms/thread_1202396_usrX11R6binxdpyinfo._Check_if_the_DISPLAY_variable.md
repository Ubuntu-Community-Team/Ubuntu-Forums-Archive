---
title: "/usr/X11R6/bin/xdpyinfo. Check if the DISPLAY variable is set. Failed"
date: 2009-07-02
forum: Server Platforms
---

### Post by dragos2 on 2009-07-02
I am using fresh install of Ubuntu Server 8.04 64 bit, then added
xorg and ubuntu-desktop packages, then NX server and is now working correct.

But when I try to install oracle 11 g enterprise it fails with this error:

$/oracle/database# ./runInstaller 

Starting Oracle Universal Installer...

Checking Temp space: must be greater than 120 MB.   Actual 304979 MB    Passed
Checking swap space: must be greater than 150 MB.   Actual 7632 MB    Passed
Checking monitor: must be configured to display at least 256 colors
    >>> Could not execute auto check for display colors using command /usr/X11R6/bin/xdpyinfo. Check if the DISPLAY variable is set.    Failed <<<<

Some requirement checks failed. You must fulfill these requirements before

continuing with the installation,at which time they will be rechecked.

Continue? (y/n) [n] n

User Selected: No

Exiting Oracle Universal Installer, log for this session can be found at /tmp/OraInstall2009-07-02_12-32-15PM/installActions2009-07-02_12-32-15PM.log

---

### Post by faizan_comsian on 2009-08-01
i am facing the same problem ...what is the solution plz help me out

---

### Post by arie_prs on 2009-08-03
i have similar problem too...
what should i do..

---

### Post by cariboo on 2009-08-03
What is the default color depth set to in /etc/X11/xorg.conf?

---

### Post by dragos2 on 2009-08-04
I am kind today :P

The solution is using ssh X forwarding like
ssh -X host -l user

and if the error keeps displaying then use xhost+
then run again ./runInstaller

Btw you should ./runInstaller --ignoreSysPrereqs
if you want to be able to install.

Ps: It took me around 2 weeks to get Oracle Enterprise 64 bit to
work on Ubuntu 8.04 64 bit. If I have to do it again I will
most probably do it in a few hours but there was almoust no
information available on how to pass common problems.
If anyone interested I will write a small tutorial on this.

---

### Post by Kango on 2009-10-07
You may very well need to install an X Windows client on your windows machine. You are probably accessing your Linux box via ssh or putty, or suchlike from a windows box.
 
You need to download Exceed, or Cygwin, or a utility that will enable you to display x windows thingys.
 
After installing x windows client (search 'x windows client download' ) you will have to set yr dot-profile ( .profile ) DISPLAY variable to the ip address of yr windows client. 
This will be yr ip address with a 'colon zero' after it ( e.g. 20.20.20.20:0 ). This way the x windows output will know where to display itself.
 
-kango

---

### Post by Kango on 2009-10-07
Kango you are my hero!

---

### Post by nando64 on 2009-10-28
Hi,

I got the same problem and I am trying to install it not from a windows client, i am on a Ubuntu OS Graph mode... :( pls help, i am trying to intall Oracle 11g R2.

Regards.

---

### Post by Wincewand on 2011-03-09
Dear All, 

I had the same problem with installing Oracle 11gR2 on  Red Hat 5.5. The issue was that there is a package missing. Please install ( for 32-bit RHEL) the package xorg-x11-libs-compat-6.8.2-1.EL.33.0.1.i386.rpm or the respective one for x86_64. 

Greetings,
Vassil

---

### Post by su27sushka on 2011-10-05
I got the same problem when running the runInstaller in Red Hat 5.6 on the host itself, not from the client machine. 
The problem was that I switched to oracle user as "su - oracle" from root. The solution is to log out completely from the machine, and log-in as oracle user. Then make sure that the DISPLAY variable is set as :0.0 Again: NOT DISPLAY=hostname:0.0 BUT DISPLAY=:0.0 
Then I just typed xdpyinfo at the prompt, and it showed me all the information it supposed to show. Then executed runInstaller and it started without any problem.

---

### Post by nelsonboo on 2012-04-09
1) login into root user( su -l root)

2) execute this command : xhost +SI:localuser:oracle

3) login to the oracle user

4) execute ./runInstaller

Now, it will work fine.

Nelson ):P

---

