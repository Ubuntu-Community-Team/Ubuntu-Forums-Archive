---
title: "Securing a program that can update itself"
date: 2009-04-18
forum: Security
---

### Post by jeffbarish on 2009-04-18
I have encountered a security issue with a Python application I am writing for Ubuntu.  I am naive about such issues, so I would appreciate some advice about how to proceed.

Because it seems customary:

- I installed the program in /usr/share.
- The program is owned by root.root and permissions are 755.

The program runs fine except for one feature.  The difficulty has to do with the ability of the program to upgrade itself.  When an upgrade is available from a remote site on the Internet, the program runs rsync to copy new versions of the files over itself.  However, the program runs as a user (me, for example), so it lacks permission to write in the /usr/share hierarchy.

Only two possible solutions have occurred to me:

- I could give everyone permission to access the file hierarchy in /usr/share/my_program.  This solution works, of course, but I am uneasy about security issues that I don't know about.  The only security issue I can think of is that a user could tamper with the installation, but this program is intended for individual users, not corporate networks, so I figure that it is safe from self-imposed vandalism.

- I could set the setuid bit to give the program root privileges.  To minimize the obvious security issues with this solution, I was thinking that I could fork a process for performing the rsync, drop the privileges of the main program (by setting the euid to the uid), and then communicate with the rsync child process using a socket pair.  However, I think that Ubuntu will ignore the setuid bit because a Python program is a script.

I conclude that the only solution is to chmod 777 all the files comprising the program.  Is my conclusion correct?  Is there a security problem with this solution that I have missed?

---

### Post by lemming465 on 2009-04-19
In general 3rd party stuff not from your main OS vendor should be installed to /opt or /usr/local to keep it segregated from the main OS stuff.  This is a separate issue from the permissions problem.

If possible, an acceptable solution would be to have a separate update process intended to be run by root, rather than the end user.  You could notify the end-user when updates were available.

Note that doing auto-update infrastructure well is fairly hard; you really need digital certificates or ssh public keys or something that identifies the server, and digital signatures to validate the downloads.  Otherwise the bad guys can spoof updates to take over the clients.

The setuid problem can be solved by one level of indirection; you would have to use a C program that was setuid to invoke the script which was not.

If your plan it make the files world writable, keep looking for a better plan.  That would work, but it's too insecure to ship.

---

### Post by jeffbarish on 2009-04-19
> In general 3rd party stuff not from your main OS vendor should be installed to /opt or /usr/local to keep it segregated from the main OS stuff. This is a separate issue from the permissions problem.

Yes, but it's still an interesting issue.  I considered /opt, which seems appropriate too.  Actually, now that I reread the Debian File System Hierarchy Standard, I see that

> The /usr/share hierarchy is for all read-only architecture independent data files
 

A program is not what I would consider a data file, so /opt actually seems more appropriate.  I was misled by my observation that almost all programs installed on my system using apt-get wound up in /usr/share and none are in /opt.  Although the specification is vague on this point, I always reserved /usr/local for programs that I create locally to run locally.  I can't think of an instance of a large, multi-directory program installing itself in /usr/local, but perhaps it would not be wrong to do so.  Still, /opt seems better to me.

> If possible, an acceptable solution would be to have a separate update process intended to be run by root, rather than the end user. You could notify the end-user when updates were available.
 

I was hoping to make updates simple for unsophisticated users.  And I may wind up with a situation where the program is running on a headless machine, so that users don't actually have an opportunity to do things like run a separate update process.  In that situation I could, perhaps, use cron to run an update job periodically.

> Note that doing auto-update infrastructure well is fairly hard; you really need digital certificates or ssh public keys or something that identifies the server, and digital signatures to validate the downloads. Otherwise the bad guys can spoof updates to take over the clients.

I will research digital certificates and digital signatures.

> The setuid problem can be solved by one level of indirection; you would have to use a C program that was setuid to invoke the script which was not.


Yes.  And moreover I could put the call to rsync in the C program and communicate with it using a socket pair.

> If your plan it make the files world writable, keep looking for a better plan. That would work, but it's too insecure to ship.

Although this statement seems obvious, I actually don't get it.  I can see that the bad guys would be able to modify the code to do something, but if they are able to get to my Python code to modify it, they could just as easily write their own Python script.  So, what exactly is the problem?

Thanks for all the advice.

---

### Post by lemming465 on 2009-04-22
> I can see that the bad guys would be able to modify the code to do something, but if they are able to get to my Python code to modify it, they could just as easily write their own Python script. So, what exactly is the problem?

The short answer is that a defense in depth approach to security includes trying to minimize escalation risks.

As a general principle, clients of network services should not be able to rewrite the network service itself.  So apache web servers are typically run under a different user than the one owning the cgi-bin directories, for example.  If not, a minor bug which lets the user escape from the applications intended security model has a much higher risk of escalating to compromises of other applications, the entire service, or interactive shell abuse of the entire server.  If the server has unpatched OS vulnerabilities, interactive access might escalate further to root access, and complete loss of server integrity.

In addition to the risks from applications re-writing themselves, something with public write permissons has the additional risk that some other unrelated application with a flaw could be used to take it over.  Defense in depth wants applications sandboxed from each other; a failure of one should not imply an easy failure of another.

In a friendly environment where there is one console user and no network services, these don't matter much.  With multiple users or network services, things become more dire.

A good textbook on general security principles is Ross Anderson's *Security Engineering*.  The [OWASP group]("http://www.owasp.org") has a lot of good information about securing web applications.

---

### Post by SpyroViper on 2009-04-23
If you feel comfortable with it accessing root and there are no other users/not networked 24x7 then it should be okay.

---

