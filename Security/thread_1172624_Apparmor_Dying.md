---
title: "Apparmor Dying ???"
date: 2009-05-28
forum: Security
---

### Post by mihalisla on 2009-05-28
Hello to all of you....
Intro
I have been an apparmor fun from it's birth.I was delightful 
when I heard that it would ship with ubuntu a priori because 
it provides a simple end user security framework and throws the glove to SElinux through simplicity and high security.

Main Question
Crispin Cowan (the main developer of Apparmor) got hired from MS and got away from Apparmor development (when he got laid off from novel).Will Apparmor be developed for linux or it will be a dead promising project because of Crispin's leaving?
In addition novel ships with SElinux.This fact MAY take two explanations :
1.Appamor is abandoned
2.novel is trying to get in the us market because the government has as an obligation that linux systems that want  
to get into government's systems should have SElinux by default

PS: COWAN  said that abandoning apparmor would make his job easier for security in windows vs linux OSes because solutions as SElinux are not favourable from end users.In the other hand, simple security solutions will rule....(That is very logical)

So what it would be for Apparmor ???

---

### Post by rookcifer on 2009-05-28
Crispin is just wrong on the Selinux issue.  Sure, in the old days it was a monster to configure, but that has really changed in recent years.  Look at all of the GUI front-ends for configuration (setroubleshoot, etc.).

And not only that but RHEL/Fedora is enabling SElinux out of the box with a targeted policy (it locks down all network daemons and confines most system/root processes to a specific domain).  The end user has a fairly high degree of security out of the box without having to touch one configuration option.  And those that need more can configure it (and people who need more will usually be experts anyway).

And then there's the technical merits of SELinux when compared to AppArmor.  SELinux relies on inodes for file labeling and not on path names.  Thus if one were to create a hard link to a binary, AppArmor would allow access where SeLinux wouldn't.  

Overall, though, SELinux is easy as long as the distro in question maintains the policies and tests them against the default install.  This means the end user has to do almost nothing.

P.S.  Both AppArmor and SELinux rely on the LSM framework in the kernel.  There have been some [security developers]("http://www.grsecurity.net/lsm.php") who say that LSM in itself is insecure.

---

### Post by mihalisla on 2009-05-29
I do not have any objections to your opinion.
I just try to have a clear view of what's going on with one 
of the top arguments about linux vs windows statement.
In my point of view the main arguments to convince someone to switch over ubuntu are :
1.Opensource system
2.Stability and good management of memory
3.SECURITY
4.Every program you need it's there in the repos
5.On going support from companies that some years ago did not
support us with their hardware (See HP notebooks) 

Thank you for this discussion

---

### Post by bodhi.zazen on 2009-05-29
Out of the box, Ubuntu is, IMO, more secure then Windows out of the box, without any additional hardening.

The biggest security risk on any OS remains under the users control - use strong passwords, do not install applications from untrusted sources, learn to secure servers before you install them, etc.

In terms of ease of use, selinux is much much easier for the end user then apparmor. I suggest you try it out for yourself - Install Fedora 11.

Apparmor, however, out of the box has minimal profiles. You the user then has to write a profile for each process / user you wish to confine. You then need to manually update your profiles as new versions of applications or libraries are installed.

In terms of syntax, yes the syntax of apparmor is easier to learn. However selinux is not that difficult and the tools available to detect, debug, and manually re-write selinux policies are much much easier to use then they were even a year ago.

As you say the apparmor community has undergone some changes, but just because one person leaves the project (Crispin Cowan) and other changes does not mean the project is dead. It does seem to be a severe blow however ... Anything beyond that would be speculation.

In terms of personal preferance, anter running both, I personaly prefer selinux, but that is just my opinion and I know many who prefer apparmor.

If you are interested I suggest you at least try selinux (assuming you have not done so recently).

---

### Post by mihalisla on 2009-05-29
I will give it a try ,but not right away due to lots of obligations having now.
By the way do u use an hids ?I have difficulties to choose between samhain and ossec

Thanks for your helping notes on the subject!

---

### Post by bodhi.zazen on 2009-05-29
either is fine.

---

