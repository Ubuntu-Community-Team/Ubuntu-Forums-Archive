---
title: "My Ubuntu 12.10 desktop OS has crashed"
date: 2012-11-21
forum: Security
---

### Post by Arpitbhai on 2012-11-21
I have installed Ubuntu 12.10 desktop OS on VMware workstation 9.0 about  35 days back, seance then I was using it with no problem at all and  stored, downloaded, created a lot of data in it, but suddenly 3 days ago  when I try to start it, it stuck  on a message which says "The system  is running in low-graphic mode, your screen, graphics card and input  device settings could not be detected correctly. you will need to  configure these yourself." and dose not boot from then, it gives some  solutions regarding the issue but none of these solution works at all.  Seance then this problem is persistent with the OS and it was not able  to boot from then onwards. I have tried all the tricks I know to solve  this problem from adjusting the screen resolution of the virtual machine  and of the host operating system(Which is Windows 7 ultimate service  pack one) to make a clone of the virtual machine and try to run it on  the same P.C. as well as on another P.C. but the same issue of low  graphics mode arises always. I also tried to repair the virtual P.C. running ubuntu by booting it through ubuntu installation iso image file but for no avail. It is worth to tell that other Virtual  machines of VMware workstation (Windows 8 Enterprise, Vista, Fedora core 4) are  working perfectly and as I had menstioned earlier the I had stored,  downloaded and created lot of data through and in that virtual machine  (Ubuntu 12.10 desktop) so it is very important for me to redeme that OS  and with it the virtual machine. If any body has the solution or even a  clue about what has happen to my virtual machine kindly post about it  and help me in resolving the above mention issue.
I also like to draw your attention on another issue that when I was trying to repair Ubuntu virtual P.C. by booting it with OS installation iso image its gives me two option try it now and install now, when I select the try now option the fullfleg operating system started with full functionality of Ubuntu desktop but the most wired thing I noticed was that it has mounted the hard disk and I was easily able to see and copy all the contents of the hard disk because by default ubuntu hides the super user root and gives us the rights and priviliges of a standrad user, so the files and folders we create are open for everybody to see, as was the case with me. It is worth to understand that because the file system of ubuntu is ext4 all the file systems that every linux distribution uses (ext4,3,2) are compatible with ubuntu os and their H.D.Ds. can be mounted through ubuntu installation image or cd. Later I tested this theory with my fedora core 4 and the test was successful but with one major exception and it was that because fedora and all the other major ubuntu distributions except ubuntu dose not restrict the use of root so the we cant see the content of root user through this way but i was still able to see the data of the standred users of my fedora v.p.c. Because of these aforementioned flaws of ubuntu it become less attractive for a serious user like me to even install it as a virtual P.C. even though it is free and has a good and user friendly G.U.I. and in my the developers of ubuntu themself should take these issues seriously and should read this post and suggest me to solve the low graphic mode problem of my ubuntu v.p.c. 
And at last sorry for my poor grammar.

---

### Post by Old_Grey_Wolf on 2012-11-21
Moved back to security discussions.

Buried in the wall of text is a concern about using the live cd and reading files on the systems hard drive.

---

### Post by CharlesA on 2012-11-21
Physical access = root access. That is how a liveCD works, so you can use it to pull the data off a dead computer without having to take the hard drive out and put it in another PC.

As for your graphics issue, it sounds like there might have been a kernel update or something. Have you reinstalled vmware tools?

---

### Post by Arpitbhai on 2012-11-21
> **CharlesA said:**
> Physical access = root access. That is how a liveCD works, so you can use it to pull the data off a dead computer without having to take the hard drive out and put it in another PC.

As for your graphics issue, it sounds like there might have been a kernel update or something. Have you reinstalled vmware tools? 

No not at all, as I have written earlier graphic mode issue arises suddenly without a clue.

---

### Post by Arpitbhai on 2012-11-21
[QUOTE=Arpitbhai;12366622]No not at all, as I have written earlier graphic mode issue arises suddenly without a clue. Anyway thanks for reply.

---

### Post by cariboo on 2012-11-21
You have asked two separate questions here, it may be best to start a new thread about your live CD concerns here, and the problem with vmware may be better answered in the [Virtualiztion]("http://ubuntuforums.org/forumdisplay.php?f=308") section of the forum.

---

