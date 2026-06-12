---
title: "problem installing scalix-server/libical"
date: 2007-05-14
forum: Server Platforms
---

### Post by greymoose58 on 2007-05-14
Hi, I'm in the process of installing scalix-server to simplify our  home business set up and I can't seem to get past ```
 scalix-server depends on libical (>= 0.24.RC4.20050413); however:
  Package libical is not installed.
``` when I try to configure it.
I have spent hours looking up libical and have installed it from source twice following the README file's instructions to the letter. It all seems to go as expected until I try to configure scalix-server again.

Hang on - I just realised  that I haven't rebooted the server,,,,,  have now and it didn't make any difference.

The server is running Dapper and was set up with Apache2, MySQL, Dan's Guardian and Squid before I set off on this project. I have followed [these instructions]("http://www.scalix.com/wiki/index.php?title=Manual_Installation#Applicable_Environments") to get where I am up to. 

I know there are people running scalix-server on Ubuntu so I'm obviously doing something wrong here. This being the first time I've set up anything more complicated than a web server I can't say I'm that surprised. 

Can anyone point out the error of my ways?

Thanks.

---

### Post by gfowler on 2007-05-14
I think there is a tweaked copy of libical in the distribution under 3rdparty software.  You might try installing that to see if it makes any diffenence.  I have scalix running on 6.06 under VMware so it is possible.  I did not encounter your issue (used the same manual install).  On the scalix wiki a script to download and install scalix on 6.10 was conftributed by an individual.  No I don't remember the name, but the time frame was early 07 (Feb/Mar).  I doing this all with out a net (read: don't have access to my sources :-) )  Hope this helps!

Jerry

---

### Post by greymoose58 on 2007-05-14
That was exactly what I needed. I saw the copy of libical in the package when I first looked through it but it completely slipped my mind later on. 

Thanks a heap for your help.

Ok, so I spoke too soon. Once the configuration was done I tried to run omakeom as instructed and it says *bash: ommakeom: command not found* I can't find Omake anywhere on my system and can't seem to locate instructions or source code for installing it. Any ideas?

---

### Post by greymoose58 on 2007-05-14
Right. I found the deb for Omake but I seem to have had my first visit to dependency hell. In order to install Omake I appear to need to remove initrd.tools. Doing that means I have to downgrade my kernel which in turn may break the whole box! 
Is there an alternative way to set up Scalix a message store or am I going to have to run Scalix on a completely different machine? ](*,)

---

### Post by gfowler on 2007-05-15
> **greymoose58 said:**
> Right. I found the deb for Omake but I seem to have had my first visit to dependency hell. In order to install Omake I appear to need to remove initrd.tools. Doing that means I have to downgrade my kernel which in turn may break the whole box! 
Is there an alternative way to set up Scalix a message store or am I going to have to run Scalix on a completely different machine? ](*,)

I would hazard a guess that your echo $PATH doesn't contain /opt/scalix/bin because ommakeoem is located in /opt/scalix/bin  Note the "The following assumes you have added /opt/scalix/bin to your PATH.... " just above the paragraph where you initialize the message store.   :) 

You will also run into an error (if my gray cells are working today) about a bad link to libcrypto.so.0.9.7 as libcrypto.so.0.9.8 is installed.  You will need to do a symblolic link of 0.9.7 to 0.9.8 or you are going to get ldap errors (IIRC).  In /usr/lib/    ln -s libcrypto.so.0.9.7 /usr/libcrypto.so.0.9.8
   

If you are trying to install this on 6.10 server you will want to redo the link for bin/bash /bin/sh etc.
   rm /bin/sh
   ln -s /bin/bash /bin/sh

Again hope this gets you 'cookin on the front burner, with gas' :) 
Jerry

---

