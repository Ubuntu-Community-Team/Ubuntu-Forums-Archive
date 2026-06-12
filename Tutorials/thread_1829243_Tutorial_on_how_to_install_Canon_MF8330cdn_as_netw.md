---
title: "Tutorial on how to install Canon MF8330cdn as network printer for ubuntu 64bit."
date: 2011-08-20
forum: Tutorials
---

### Post by oappi on 2011-08-20
Why:

I wrote this tutorial because canon´s instructions don't define how to install printer to 64bit ubuntu and i wasted countless hours on trying to build the installation from source, which i was never able to do. I suspect automake or some other tools syntax  has changed so that canon scripts wont work and that prevents running the later source files install script. Also after finding out that you can convert rpm packages to deb i didn't know that it was dpkg´s fault that i wasn't able to install these files. GUI versio will alert you on scripts dont remember what terminal dpkg said, but it didnt work. So i hope that i will save someone else's time by posting tutorial on how to install mf8300 printer. Most likely it will work on some other canon printers but i can only test it to my own. It is a pity that canon wont offer any assistance or decent package to **ubuntu** users for their otherwise fine printers. Fortunately installing the printer is very easy when you know how it is done.

_______________
Files needed:
-canon´s zip file :  (from zip file)
cndrvcups-common-2.20-1.x86_64.rpm
cndrvcups-ufr2-uk-2.20-1.x86_64.rpm
-alien
-GDebi
____________

How to:

first download linux drivers from canon´s web site. I installed drivers V2.2.

after you have downloaded drivers you can just unzip the whole package.

search for 64 driver folder (under uk folder).

you will find that there are only RPM files.


You need alien to convert these files to .deb files.

it can be obtained from software center.


You should now have files  cndrvcups-common-2.20-1.x86_64.rpm and cndrvcups-ufr2-uk-2.20-1.x86_64.rpm unzipped on known location

Open terminal and go to files location.

do this to both files

use sudo alien -k -c -d <filename>     
(im not sure if you need -k it has something to do with version numbers, -c will keep scripts intact i haven't tested, but i would imagine that canon uses at least some scripts at least if source files are any indication. So you probably need that. -d simply tells to convert to debian package).

it should generate .deb files. It gave me warning but it should still work (at least mine did).

now you can't use dpkg -i for some reason, or at least my installation failed. Same goes with default gui equivalent.

I was able to install packages with GDebi.. so just install GDebi through software center.

after installing GDebi you should be able to right click on the packages and choose open with Gdebi...
you should install cndrvcups-common-2.20-1.x86_64.deb first and then cndrvcups-ufr2-uk-2.20-1.x86_64.deb


When you have installed both packages start browser (ie firefox) and type localhost:631.

press administaration tab

press add printer (username & password are same as ubuntu logins)

Choose Appsocket/HP Jetdirect

then just give it your printers address, as shown in example like: socket://192.168.1.2:9100 where 192.168.1.2 is ip address
and unless you have changed printer settings port should be 9100 then continue. // btw it is very good idea to set static ip address for your printer from your printers network settings if you haven't already done that.

name/desc you can choose what ever, but name can't be empty

then it will present a list

choose canon from there and continue 


it gives another list search for canon mf8300 series ufrii... 

then it will ask default setting for printing... i changed only page size since i only print on a4 sized paper.

then press set defaults...


Now with any luck you should have your canon printer working. 

I tested this method successfully on ubuntu 10.04(lts) and 11.04.  11.04 was on virtualbox since i didn't want to screw my default ubuntu installation. This method doesn't seem to work on live version of ubuntu. Only installed one.

---

### Post by eniac3 on 2012-12-17
Using your tutorial I was trying install my Canon MF8330CDN as network driver in Debian Wheezy AMD64. 

I've spend few hours to get working my printer, issue was, packages cndrvcups-common-2.20-1.x86_64.deb and cndrvcups-ufr2-uk-2.20-1.x86_64.deb create folder /usr/lib64 and put there few files. But Debian don't use above folder and finally each of installation step was successful, but printer wasn't print without any errors.

Solution: before installing above packages please create /usr/lib64 symlink to /usr/lib
that is the clue :)
works fine :):):)

---

