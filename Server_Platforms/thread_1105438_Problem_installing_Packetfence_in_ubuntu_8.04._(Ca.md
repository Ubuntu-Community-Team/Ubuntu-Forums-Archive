---
title: "Problem installing Packetfence in ubuntu 8.04. (Can't locate  Readonly.pm in @INC..."
date: 2009-03-24
forum: Server Platforms
---

### Post by esp171 on 2009-03-24
I`m trying to install Packetfence software in an ubuntu server and an error message keeps me annoying. The error is:

-----------------------------------------------------------
francaserver@ubuntuserver:/usr/local/pf/bin$ sudo /etc/init.d/packetfence start
/etc/init.d/packetfence: line 14: /etc/rc.d/init.d/functions: No such file or directory
Starting PacketFence...Can't locate Readonly.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/local/pf/bin/pfcmd line 22.
BEGIN failed--compilation aborted at /usr/local/pf/bin/pfcmd line 22.
-----------------------------------------------------------

Please someone help me. I`m new using ubuntu.
thanks for any cooperation.

---

### Post by johnnyguns on 2009-05-02
Do you have all the perl modules installed?

---

### Post by Mach1US on 2009-07-28
Has anybody have successfully installed Packetfence ,ZEN or can point me to some good how-to tutorials as the one on PF page does not explain everything in detail .:confused:

---

### Post by wojox on 2009-07-28
Did you download the .pdf?

[http://www.packetfence.org/en/download/documentation.html](http://www.packetfence.org/en/download/documentation.html)

---

### Post by druhboruch on 2009-07-28
I tried this guide with very limited success:

[http://techrepublic.com.com/2415-1035_11-179743.html](http://techrepublic.com.com/2415-1035_11-179743.html)

---

### Post by Mach1US on 2009-07-28
Thanks guys for quick reply.
I have downloaded pdf but it does not explains the whole concept in detail,there is no configs of the switch and limited explanation on VMware configuration .
This is the guide i have followed but it's closely based on the PDF itself.
 [http://hi.baidu.com/d_o_g/blog/item/34b335dd2eec3ede8d102920.html](http://hi.baidu.com/d_o_g/blog/item/34b335dd2eec3ede8d102920.html)
Can you point me to something little less advanced than the PDF document on the PF site or maybe cook up a little how-to?

---

### Post by AhYup on 2009-08-05
I'm working on it right now and it is a pain. Among other things some of the Hardy libraries are to old to be used. 

There is a file call packetfence.spec written for Fedora/CentOS compilation in the main pf directory that does list the requirement including the Perl libraries. I've been compiling them from cpan but even that is proving to be a pain because at least one, Thread::Pool, has failed due to complicated dependency problems. It is definetly written with Fedora packages in mind.

---

### Post by timunrue on 2009-08-18
I just spent a good amount of time on it and i got it to install and work.
I'm trying to put together a guide:
[http://blog.nervousnetwork.com/?p=18]("http://blog.nervousnetwork.com/?p=18")

Right now it is more like a dump of all the websites and commands I ran to get it to work. I'm going through my terminal logs now to try to get some idea of the progression that I took to reach my final result.

---

### Post by Mach1US on 2009-08-18
Thats awesome, cant wait to see it.

---

### Post by timunrue on 2009-08-18
I've finished writing up the initial guide.
I still have to cover a lot of the errors I encountered.  Most importantly I need to describe the process I had to use to get SSL working.  If you have any questions or problems please let me know.

---

### Post by Mach1US on 2009-08-19
Thanks a lot, I'm sure i will need help with some issues.

---

### Post by codenameodr on 2009-12-14
Well I followed all the guidelines mentioned in the letter, and so far I could not boot the system successfully, one could? :(

---

