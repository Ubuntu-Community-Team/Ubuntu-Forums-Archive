---
title: "VMware server problem..."
date: 2008-03-06
forum: Virtualisation
---

### Post by niko123 on 2008-03-06
i was able to install the vmware server console....
but when i went and tried to install the managment interface....i ran into this error....can anyone tell me what it means...??

root@xtwoface:/tmp/vmware-mui-distrib# ./vmware-install.pl
A previous installation of VMware software has been detected.

Failure

Execution aborted.

root@xtwoface:/tmp/vmware-mui-distrib#

how...would i remove the previous installation of VMware software....


And how come when i go to my Applications>system tools?VMware console...
and i click to open the vmware console a error pops up saying...
Could not launch menu item. Failed to execute child process "vmware"
__________________

---

### Post by {BzF}~JOKesTER on 2008-03-06
This Should Work:

apt-get remove vmware-server --purge

Now Run:

apt-get autoremove

And:

apt-get autoclean

And Re-install VMware Server

Hope This Helps!

---

### Post by niko123 on 2008-03-06
hrm...thanks for the reply....but it looks like it didt work for me... 

i think i must have done something wrong with the installation....i dont know where i went wrong...the vmware server icon is there...the files are present....but ....i dont know..

root@xtwoface:/home/xtwoface# sudo apt-get remove vmware-server --purge
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package vmware-server
root@xtwoface:/home/xtwoface#   

my package isit even found.... ::sigh::

How would i completly remove the vmware server console....so i can just re-install the whole thing...?

---

### Post by {BzF}~JOKesTER on 2008-03-06
Try Removing The /etc/vmware Folder And Than Run The Code.

:)

---

### Post by niko123 on 2008-03-06
would it be...weird if i didt even find the file in /etc/vmware

:confused:

i have no idea where i went wrong now....

---

### Post by {BzF}~JOKesTER on 2008-03-06
No Delete The Folder vmware In /etc

:)

---

### Post by stevegarriques on 2008-03-06
Did that fix the problem for you? Yeah I had some issues getting the mui working as well. Bit tricky at first. Make sure you open the ports

---

### Post by {BzF}~JOKesTER on 2008-03-06
Also Niko,

If We Can't Correct The Problem With VMware Server - I Highly Recommend Innotek Virtual Box - Found In The "Add Remove" Tab Under "Applications" -It's Much Easier To Install As It Is A Complete Debian Package.

If Your Still Set On Using VMware Server Please Ask Away - And I Will Help You To The Best Of My Ability.:):)

---

### Post by niko123 on 2008-03-06
thanks for the info...i was planning to use Virtual Box...just i figured that vmware would be best..just because...when i figure all this out...i will be able to run my severs on this...and yea...ubuntu is not new new to me...just its extremely different..and i greatly appreciate you guys for the help!

but the only folder that i found in /etc/ would be the vmware-mui and i had no permission to remove it...

[o_0] what ports....lol

---

### Post by niko123 on 2008-03-07
how come...when i go search for vmware files....i find 148 files....but when i try to delet the files...i either get a "cant move file to trash" or "file doesent exist" ( a quarter of the files was file doesent exist)

So i have no idea...what im doing wrong here....or how i can fix it....i wanted to know...how i can completely remove vmware...knowing that the files itself.."doest exist" but they ARE there...so i can start with a fresh install....

---

