---
title: "Samba issues ubuntu server 14.04"
date: 2014-06-08
forum: Server Platforms
---

### Post by Dale_Whitnall on 2014-06-08
Ok, I've been trying to solve this for some time but not getting anywhere.
I have 2 virtual ubuntu guests running on a ubuntu server.
Both ubuntu guests have the same file system passed to them from the host.  13tb media directory managed by the host.
The first one that has been working for some time is ubuntu 13.04 running samba 3.6.9-1ubuntu1.2, now I go to a shared folder from my windows 7 machine and can see all the files in the directory, a backup directory 2312 files.  But from the second guest that is running ubuntu 14.04 and samba 4.1.6+dfsg-1ubuntu2.14.04.1 the windows 7 machine only sees 1625 files.  I can access the files that are not listed, there is a couple of directories which I can open so it to me dosn't seem like a permission problem.  I don't know what else to try.

Does anyone have any other ideas.

---

### Post by TheFu on 2014-06-08
Only 1 OS should have 'control' of a file system at a time.  Having both at the same time could/should screw with file locking and could/should cause file system corruption.
Run fsck on the unmounted file system.
Choose 1 OS to manage the storage (perhaps the hostOS?)
Have all clients access the storage over the best, most efficient file sharing method available - usually NFS, but CIFS can work if Windows must be involved.

Does this make sense?

---

### Post by Dale_Whitnall on 2014-06-08
I only have the host manage the filesystem, but its pushed through to the guests using virtFS 9p passthrough. one guest at a time is how I was testing it but like I said before.  The older install, ubuntu 13.04 running samba 3.6.9 when it lists the filesystem to my windows machine it will show all the files but the 14.04 running samba 4.1.6 doesn't show all the files but I can access them if I put their name in the windows explorer toolbar.
I just wanted to let you all know that the base filesystem is the same, it for whatever reason doesn't seem to work correctly on the later version, but I'm unsure on how to fix it.  I was thinking of downgrading the samba version to match the older system, as I really would like to run the 14.04 LTS but I'm unsure on how to downgrade it if that would be the best way of resolving this issue.
I didn't really want my virtual host, which manages the filesystem to also run samba, the only thing my host does is manage the virtual guests.  It is only a very base install of 13.04 which I'm going to upgrade also to 14.04 LTS

---

### Post by kjertil on 2014-06-09
This might be a unhelpful reply but since no one wants to answer my own questions regarding why Samba 4 seems broken on Ubuntu 14.04 my suggestion is going back to Ubuntu 12 if you rely heavily on Samba to work properly. I reinstalled Ubuntu 12.10 and Samba 3.6 and at least things work again.

---

### Post by TheFu on 2014-06-09
As I understand it, Samba4 is a completely different animal from all prior versions.  On 14.04, I'm still running samba3 - actually did an OS migration last week and the samba settings migrated 100% and work. Given it isn't a complex environments and definitely is NOT using a plan9 file system.

BTW - there is a difference between wanting to answer the question and knowing an answer. ;)

---

### Post by kjertil on 2014-06-09
My big question is, and sorry for hijacking the thread, why did they decide to go with Samba 4 in Ubuntu 14.04 if it's not ready for production yet and considered "experimental"?

---

### Post by bab1 on 2014-06-09
> **kjertil said:**
> My big question is, and sorry for hijacking the thread, why did they decide to go with Samba 4 in Ubuntu 14.04 if it's not ready for production yet and considered "experimental"?

Samba, as of 4.1 is in "stable release".  It is not experimental at all.  See: [http://www.samba.org/samba/history/]("http://www.samba.org/samba/history/")

It really doesn't matter at this point whether you use Samba 3.x or 4.1 as the smbd/nmbd daemon appears to function the same.  By default the Samba4 package for Ubuntu is configured as a "standalone" (member) server so it should work just as in Ubuntu 12.04 or 13.10.

I have no production Samba4 installs, but I have installed and successfully installed Ubuntu 14.04 with Samba4 for testing and it works correctly with no extraordinary configuration needed.

Most of the time I find the problems to be due to name services or other networking problems, not directly Samba4 problems.

---

### Post by bab1 on 2014-06-09
> **TheFu said:**
> As I understand it, Samba4 is a completely different animal from all prior versions.  On 14.04, I'm still running samba3 - actually did an OS migration last week and the samba settings migrated 100% and work. ...

I'll bet the Samba version is really 4.1 on this upgrade.  I'd be interested to know for sure.  Post the version number (Samba -V or smbd -V).

The smb.conf settings for the smbd and nmbd daemons should work as long as you don't need the server to be the DC in an AD environment.

---

### Post by kjertil on 2014-06-09
bab1, may i ask what result you get from samba-tool dbcheck or samba-tool user list?
And which Samba version do you have exactly?

---

### Post by bab1 on 2014-06-09
> **kjertil said:**
> bab1, may i ask what result you get from samba-tool dbcheck or samba-tool user list?

Samba is a suite of tools that can be used for file sharing and optionally, user management.  I only use the file sharing components and configure the smbd daemon by directly editing the smb.conf file.  Both samba-tool dbcheck or samba-tool user list query the LDAP database for information.  I don't use the AD components at all so I don't use the *samba-tool* at all.  
> 
And which Samba version do you have exactly?
4.1.6

The install is virtual and I don't leave it running.  It's only for testing.  I manage all the accounts at each local machine.  I manually keep all the user accounts matching (uid, gid, username and password).  This is a small test and home network.

It sounds like you are using the Samba install as an AD DC.  I can't help you with that aspect.

---

### Post by Dale_Whitnall on 2014-06-09
ok so given that I'm running 14.04 can anyone tell me how to replace the current version of samba with an older version like from 13.03 ?

---

### Post by bab1 on 2014-06-09
> **Dale_Whitnall said:**
> ok so given that I'm running 14.04 can anyone tell me how to replace the current version of samba with an older version like from 13.03 ?
You can't install an Ubuntu package of Samba 3.6 directly.  Your options are to find a pre-compiled version of Samba3 and match up all the dependencies yourself manually.  The other is to compile Samba3 yourself.  Neither of these are satisfactory IMO.  You will get NO UPDATES with these methods.

FYW -- The package name is the same for both Samba3 and Samba4 so you can't just add the 13.10 repos.  IIRC the version of python also changed from 2.n to 3.n.  Both of these are serious problems that will prevent you from downgrading Samba.

I'd use Ubuntu 12.04 (EOL is 2017) for Samba3 or Ubuntu 14.04 for Samba4.  Functionally both use the smbd daemon to do the same thing (share files via CIFS).  So either should work.  

No pushing or pulling.  The client requests and the server provides the needed share directory so the client can mount it.  The is classic client/server mounting of a remote file system to a local host.  The fact that your clients are VM's hosted on the machine that is also the Samba server is a complication but shouldn't be a deal breaker.  I however have no firsthand experience with this.  If you want to do some testing I'll try and help.

I hope this helps you make a decision.  Sorry I couldn't provide a complete solution.  :

---

### Post by Dale_Whitnall on 2014-06-09
Thanks bab1, I think i will start a new 12.04 for the samba side of things, the only thing that was concerning me was that no more updates for 13.04, and when I tried to get 14.04 samba working, it will hand out the files but for whatever reason all the files will not list. I guess there is still a few issues with samba4, but it does work for the most part.

---

### Post by cariboo on 2014-06-10
If you want to help yourself, as well as other, it may be an idea to submit a bug [here]("https://bugzilla.samba.org/"), sometimes bugs that appear in Ubuntu may already be solved upstream.

---

### Post by jim92 on 2015-02-02
For reference, i have the same issue, and have posted a bug report about this:
[https://bugzilla.samba.org/show_bug.cgi?id=10916](https://bugzilla.samba.org/show_bug.cgi?id=10916)

---

