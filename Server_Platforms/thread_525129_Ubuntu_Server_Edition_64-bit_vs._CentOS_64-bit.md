---
title: "Ubuntu Server Edition 64-bit vs. CentOS 64-bit?"
date: 2007-08-14
forum: Server Platforms
---

### Post by Monarchist on 2007-08-14
Hi. [I hope I posted this in the right forum.]

I am a webmaster of several websites and own my own dedicated servers. As my sites have been rapidly growing in popularity on the Internet, I now find the need to transfer to a newer, better server.

I've already found the company and server I want, but now it is time to decide what operating system I am going to use. This is a difficult task for me, as developing the specs of the server for what I wanted and needed took more than long enough.

Being that my server's processor will have 64-bit technology capablity (an Intel Core 2 Duo E6750), I want to use that technology in my operating system. I have narrowed it down to two:

**Ubuntu Server Edition 64-bit vs. CentOS 64-bit operating systems.**

1.) Which one is FASTER?
2.) Which one is more stable?
3.) Which of those two server operating systems would you recommend me?

I know the Ubuntu project was made primarily as a desktop PC operating system, and because of that Ubuntu is one of the most popular and easiest-to-use open source Linux operating systems for regular PC users. I am wondering how it's server operating system is though; if it's still fast, stable, and reliable.

I need to do a direct comparison to CentOS 64-bit operating system, which was a project made just for servers. A large majority 64-bit OS server-owners use CentOS 64-bit; I found very few using Ubuntu's.

Really looking for a direct comparison and hopefully answers to my questions.

Thanks.

---

### Post by Brazen on 2007-08-14
As a server admin, I personally prefer Ubuntu Server LTS (currently Dapper).  Really they are both going to be just as fast and just as stable.  The differences are going to be the install process (I prefer Ubuntu's), the defaults set by the installer (I prefer Ubuntu's), and the package manager (again, Ubuntu's is much better).  The upgrade between major versions is going to be something to consider, too.  I've done major version upgrades on both CentOS and Ubuntu and not had a problem with either, but I think Ubuntu's is a tad easier.

The thing that CentOS has going for it is it's RedHat compatibility.  We, for instance, have several proprietary applications that are only supported on Redhat.  I was able to get them to install and work somewhat on Ubuntu, but for whatever reason I could not get them to run reliably.  This isn't anything to do with the quality of Ubuntu, it's just that this application was probably expecting certain little things that are RedHat specific.  If you stick with the software int he repos, or software that is supported to run on Debian or Ubuntu, then you will be just as well.

The thing to check is if you want to install some website management software like zPanel, then check and see which distros it is supported to run on.  If you are sticking with major open source apps like apache, php, and ruby, then you will be just fine with whatever distro you use.

Also, keep in mind that this only applies to the LTS release of Ubuntu (Dapper) and if you go with any later versions (such as Feisty) then there is no question that you should NOT go with Feisty on a server.

---

### Post by Monarchist on 2007-08-14
> **Brazen said:**
> As a server admin, I personally prefer Ubuntu Server LTS (currently Dapper).  Really they are both going to be just as fast and just as stable.  The differences are going to be the install process (I prefer Ubuntu's), the defaults set by the installer (I prefer Ubuntu's), and the package manager (again, Ubuntu's is much better).  The upgrade between major versions is going to be something to consider, too.  I've done major version upgrades on both CentOS and Ubuntu and not had a problem with either, but I think Ubuntu's is a tad easier.

The thing that CentOS has going for it is it's RedHat compatibility.  We, for instance, have several proprietary applications that are only supported on Redhat.  I was able to get them to install and work somewhat on Ubuntu, but for whatever reason I could not get them to run reliably.  This isn't anything to do with the quality of Ubuntu, it's just that this application was probably expecting certain little things that are RedHat specific.  If you stick with the software int he repos, or software that is supported to run on Debian or Ubuntu, then you will be just as well.

The thing to check is if you want to install some website management software like zPanel, then check and see which distros it is supported to run on.  If you are sticking with major open source apps like apache, php, and ruby, then you will be just fine with whatever distro you use.

Also, keep in mind that this only applies to the LTS release of Ubuntu (Dapper) and if you go with any later versions (such as Feisty) then there is no question that you should NOT go with Feisty on a server.
What is Dapper and Fiesty? Are these releases of Ubuntu Server Edition?
I'm realy interested in the 64-bit version...are you telling me I shouldn't get the latest release of Ubuntu Server Edition?

---

### Post by ubuntu27 on 2007-08-15
Dapper Drake, Feisty Fawn, etc are release code names for Ubuntu. 

Ubuntu Dapper Drake (which is a LTS, Long Term Support) is Ubuntu 6.06

Ubuntu Edgy Eft = Ubuntu 6.10

Ubuntu Feisty Fawn = Ubuntu 7.04

More About [Ubuntu Release Code Names]("https://wiki.ubuntu.com/DevelopmentCodeNames")

---

### Post by foxylad on 2007-08-15
I've run an AMD64 production server on Ubuntu 6.06 LTS for a year, and have also admined Redhat servers (i386). I haven't had any problems with either OS, absolutely no unexplained crashes ever, so I can't comment about relative stability except to say that both are excellent. 

Vulnerabilities are patched quickly and are easy to deploy - the previous poster's comments about the package system are correct, apt is much better than rpm. But the best thing about the Ubuntu support is the "LTS" bit - I got caught with Redhat dropping support for my version, and as you will soon find out, moving apps to a new server is something you want to do as infrequently as possible. LTS means my server OS will be supported for 5 years, by which time I will be upgrading the hardware and moving to the next Ubuntu LTS release.

I don't know how long Centos supports it's versions for, but I'd check before you decide which way to go - this is a much bigger issue than speed, trust me!

---

### Post by vincent7q on 2007-09-09
*[Also, keep in mind that this only applies to the LTS release of Ubuntu (Dapper) and if you go with any later versions (such as Feisty) then there is no question that you should NOT go with Feisty on a server.]*

Could you let me know why don't you recommend Feisty? Is it unstable or any reason you think it is not good in comparing with Dapper? Thanks

---

### Post by jayson.rowe on 2007-09-09
Even though this IS an *buntu board, and I'm sitting here running Kubuntu on my desktop, with THOSE two choices I just have to recommend CentOS for a server platform. 

Basically what Cent does is recomplie RHES without the branding. Remember, as a whole Ubuntu/Kubuntu/Xubuntu/Edubuntu have really embraced Desktop Linux - Red Hat has shunned the desktop (giving only a buggy unstable step-child called Fedora up for offers, and RH Enterprise Workstation, which is nothing but the server, with a server optimized kernel with Workstation packages added) 

If you use Ubuntu on your desktop and want something similar on a server, don't forget Ubuntu's Daddy! Debian Stable is probably one of the most stable easiest to maintain servers OS'es you will find! As I said, I recommend Cent given your two choices, but Debian would be my choice.

---

