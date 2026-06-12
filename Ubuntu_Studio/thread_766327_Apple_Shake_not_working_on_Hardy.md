---
title: "Apple Shake not working on Hardy"
date: 2008-04-25
forum: Ubuntu Studio
---

### Post by affected on 2008-04-25
Hello, it seems Hardy breaks Shake support somehow. I have been able to run Shake 4 on Ubuntu previously, but since upgrading to Hardy, it no longer works. When I start the application up by running the startup script with csh via terminal, just as I have before, nothing much happens. The process is started, but no gui comes up, nor do I get any error messages.

Any ideas on how to find out what is going wrong?

edit: to clarify, the startup script sets a few environment variables and passes them as arguments to a binary executable, shkx.exe. (yes, it should work and has worked before, despite the .exe extension.) I believe it is the executable that fails somehow, but it gives me no information why.

---

### Post by fatblueduck on 2008-04-25
I am having the same problem. This is a shame. I am not getting any messages from the terminal.

***** UPDATE: solution, 4/28/08 **********
There is a [forum]("http:////www.vfxtalk.com/forum/shake-not-working-gentoo-t12163p2.html") on the net where this information comes from, but I'm re-presenting it here with a few original bits of information to guide ubuntu users. Credit to user 'gabrield'.

The problem is a missing x11 library that is not included with hardy, but is found in recent suse and fedora distros - and so we'll take the library from an extracted fedora *rpm file, [libX11-1.0.3-8.fc7.i386.rpm]("ftp://195.220.108.108/linux/fedora/releases/7/Everything/i386/os/Fedora")

[LIST=1]
[*]download the file [libX11-1.0.3-8.fc7.i386.rpm]("ftp://195.220.108.108/linux/fedora/releases/7/Everything/i386/os/Fedora/libX11-1.0.3-8.fc7.i386.rpm")
[*]install the 'alien' rpm conversion utility
[*]extract the rpm file
[*]locate libX11.so.6.2.0 and copy to the lib directory used by shake
[*]rename your moved copy of 'libX11.so.6.2.0' *to* 'libX11.so.6'
[LIST]
[*]if you are running shake from the original directory that was created from the software's extraction, then the lib directory is found in the shake directory
[*](~./shake*/lib/)
[/LIST]
[*]if you are using shake 4.1, then you should be able to run shake
[*]otherwise, enter shake's 'bin' directory
[*]open up shake's startup script './shake' with a text editor[/LIST]
change:
```

if ${?LD_LIBRARY_PATH} then
setenv LD_LIBRARY_PATH
/usr/lib:${NR_SHAKE_LOCATION}/lib:${NR_SHAKE_LOCATION}/lib/mesa:${LD_LIBRARY_PATH};
else
setenv LD_LIBRARY_PATH
/usr/lib:${NR_SHAKE_LOCATION}/lib:${NR_SHAKE_LOCATION}/lib/mesa;
endif
```
to:
```

if ${?LD_LIBRARY_PATH} then
setenv LD_LIBRARY_PATH ${NR_SHAKE_LOCATION}/lib:${NR_SHAKE_LOCATION}/lib/mesa:${LD_LIBRARY_PATH}:/usr/lib
else
setenv LD_LIBRARY_PATH ${NR_SHAKE_LOCATION}/lib:${NR_SHAKE_LOCATION}/lib/mesa:/usr/lib
endif
```

basically, remove /usr/lib: in the beginning and put it to the end as shown above. Save the file and start shake

---

### Post by affected on 2008-04-27
Thanks a ton! I was about to reinstall gutsy, but this solution worked, with the minor additional detail, found in the forum post you linked to, that the lib file must be renamed to libX11.so.6  . Your google skills must be superior to mine, I couldn't find any help elsewhere. Thanks again.

---

### Post by metanix on 2008-04-27
Thanks a lot for reporting this fine hack!

I just wanted to add that Fedora package is not really necessary.

If you can copy the library from your "old" Gutsy install into Shake library directory, it will work fine.


ciao,
 n.

---

### Post by wattana on 2008-04-28
Thanks. It works fine!!!

And yes, you must rename (or create a soft link to) the libX11.so.6.2.0 called libX11.so.6

thanks again!!

---

### Post by polygone on 2008-08-25
> 
locate libX11.so.6.2.0 and copy to the lib directory used by shake


I cannot, for the sake of my sanity, find this file.  I've acquired the rpm from the fedora site and extracted it.  It appears to be intact, but it does not contain that particular folder.  Am I missing something?

```

wget http://hany.sk/mirror/fedora/releases/7/Everything/source/SRPMS/libX11-1.0.3-8.fc7.src.rpm

```

*******Edit 
       I got it.  I had the wrong file.  :)

---

### Post by mgrajeshvkm on 2009-03-16
Hi friends,

if any one successfully installed shake plz tell me step by step..for the last one and half months i was searching for a solution

i have an AMD machine  and rpm cannot b extracted


PLZ HELP!!!!!!!!

and dear wattana plz tell me the procedure on installing shake plz

---

### Post by mgrajeshvkm on 2009-03-17
hi,

i cannot find /shake file too

and i got another shake method

1. Unpack shake and create dir. /usr/apple

2. gksu nautilus

3. Move upacked folder to /usr/apple

4. install csh and tcsh

5. chmod 755 * /usr/apple/shake-v4.00.0607/bin

6. csh shake-v4.00.0607

7. enjoy.



This process worked for me. You might need to copy your key.dat file into /var/flexlm to get it working.

i changed shake directory name..

but nothing happed!!!!!

why  plz help!!!

---

### Post by theadmira1 on 2009-06-29
I did all of the above in 8.04... but i still have a problem? nothing happens... terminal doesnt respond at all... 

[IMG]http://tinypic.com/view.php?pic=dmtd6r&s=5[/IMG]

anyone? my rig:

core i7
6gb dominator ram
asus 4870x2 gpu
asus rampage extreme II mobo
running ubuntu 8.04 64bit


im having the same problem with maya 2009? houdini works fine but maya and shake apparently dont like me very much... any help would be greatly appreciated... TIA

---

### Post by theadmira1 on 2009-06-30
> glenn@glenn-desktop:~$ sudo su
root@glenn-desktop:/home/glenn# apt-get install tcsh
Reading package lists... Done
Building dependency tree       
Reading state information... Done
tcsh is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@glenn-desktop:/home/glenn# apt-get install csh
Reading package lists... Done
Building dependency tree       
Reading state information... Done
csh is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@glenn-desktop:/home/glenn# chmod 755 * /usr/apple/shake-v4.10.0606/bin/
root@glenn-desktop:/home/glenn# cd /usr/apple/shake-v4.10.0606/bin/
root@glenn-desktop:/usr/apple/shake-v4.10.0606/bin# csh shake 





this all i get and nothing responds...

---

### Post by cariboo on 2009-06-30
Try:

```
csh ./shake
```

If you are running it from the programs directory. 

I don't know anything about shake, but does it need to be run as root?

It may help to move the directory to /usr/local, then you can run it from your home directory.

---

