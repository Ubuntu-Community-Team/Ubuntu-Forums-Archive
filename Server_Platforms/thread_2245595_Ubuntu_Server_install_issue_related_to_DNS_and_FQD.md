---
title: "Ubuntu Server install issue related to DNS and FQDN"
date: 2014-09-24
forum: Server Platforms
---

### Post by u-dan on 2014-09-24
Hello Ubuntu Community,
  I know how I created my problem, I just can't seem to fix it.
During installation of Ubuntu Server 14.04, I was prompted to select a Fully Qualified Domain Name (FQDN).
It said something to the affect of, if you want to access the internet, enter your FQDN.
Being a relative newbee, I followed the suggested format and entered a FQDN. I can't remember exactly what I entered, but I remember that it included a domain name (that I own), i.e. example.com, I also included "...host:8080".
I think I also included the brackets "[ ]" in it's example.
I realize now that I could have skipped the DNS completely, but I am trying to not have to reinstall from scratch.

Here are the symptoms:


When I try to do an update, it says:
>  0% [Connecting to ]host:8080] [Connecting to ]host:8080] 
I am pretty sure that the above is the BIGGEST CLUE OF ALL

When I run */etc/init.d/bind9* restart I get the following:
> 
no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory
sudo: /etc/init.d/bind9: command not found


I thought I fixed the leaking memory issue by running the following:
> 
pam-auth-update" and remove "SMB password synchronization

 but it seems to be back.

When I run *sudo nano /ect/resolve.conf* the file seems to be empty and I get the leaking memory error again.
* /etc/resolvconf/resolv.conf.d/head *  seems to be empty as well.
I am able to ping internal and external sites

  When I run a sudo apt-get update, I get a number of errors, including the following:
(many errors are similar, so I have only included a few
The important ones (related to my issue) seem to be the ones about ]host:8080
> 
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty InRelease
...
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty release.gpg
   Could not resolve ']host:8080'
...
W: Failed to fetch [http://us.archive.ubuntu.com/....etc](http://us.archive.ubuntu.com/....etc)..
...
W: Some index files failed to download, They have been ignored, or old ones used instead.
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


Here's are some of things that I have tried:
Uninstalling and re-installing Bind9
I have not hard booted because I am afraid of what that might do.
installed resolvconf
When I run * sudo rm /etc/resolv.conf* i get the error:
>  no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory 
When I run * sudo dpkg-reconfigure resolvconf * it runs without issue.

Conclusion:
I tried hours worth of other stuff, but I cannot remember what it all was. 

Can anyone help me resolve this issue which will allow me to do an apt-get update without errors?

Thank you all for your time and any suggestions.
Sincerely,
u-dan

---

### Post by slickymaster on 2014-09-24
*Moved to the ***Server Platforms*** sub-forum*

---

### Post by u-dan on 2014-09-24
Solved:

During the initial install, at the DNS setup, the */etc/apt/apt.conf* file was edited to contain the FQDN that I specified.
I opened the */etc/apt/apt.conf* file using > sudo nano /etc/apt/apt.conf and commented out (by adding "#") the only line in that file which was similar to the following: > Acquire::httpProxy "http://[[example][PASSWORD]@}host[:8080]/"; 

After saving and exiting I ran *sudo apt-get update* and all errors are gone and updates were completed successfully. 

Thank you to all that read this thread and considered the possibilities and I hope this helps anyone else that has the same issue.

Sincerely

u-dan

---

