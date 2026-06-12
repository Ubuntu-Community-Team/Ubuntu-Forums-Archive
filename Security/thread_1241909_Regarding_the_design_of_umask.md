---
title: "Regarding the design of umask"
date: 2009-08-16
forum: Security
---

### Post by glitch83 on 2009-08-16
I recently came across the idea of umask for a shared directory and frankly I disagree with the design of the system in general and hopefully someone can describe a) why it is the case and b) how I can achieve what I want. 

umask was designed to restrict permissions on file creation as a safe way of working in groups in shared directories.(it seems) I also find that the umask is set (I have found) in two major places; 1) the umask command and 2) the fstab. For the fstab - this makes sense, at a filesystem level, we should be able to set global umask and have it work globally regardless of the child process. But the umask command doesn't make sense to me - its affects only exist for the lifetime of the process. This means that most people hack their way through umask using the bashrc or profile etc. Sometimes we get lucky and scp and other siblings pay attention to our particular preferences file but what happens if a user decides to use korn or heaven forbid scsh? Would their umask requests be honored? 

The default case and the common use of umask
It seems like the default settings for umask are 022 which means that files I create are not writable by the group. One of the most common reasons people come across umask are to give users write access to fellow group members on file creation. This is all well and good but that means that for the sysadmin - every new user that gets added to that group needs to get a "umask 002 /dir/" in their bashrc... that just seems counterintuitive. Shouldn't there be a more persistent solution? It seems like that kind of access should exist - I mean the functionality is there if fstab can do it.. On the other hand, hacking the fstab to do a umask on a filesystem seems like the way to go but if you are on a more flexible system - you don't want to repartition and re-umask everytime the managers ask for something new. 

I guess my main question here is that chmod/chgrp are such wonderful tools, it seems like umask should have similar functionality (be more persistent). What say you? Have I solved my problem wrong (adding umask to the bashrc)? Is there a better solution? Maybe a more persistent tool I have missed? 

Thanks :-)

---

### Post by jeffathehutt on 2009-08-16
Check out [http://ubuntuforums.org/showthread.php?t=1238769]("http://ubuntuforums.org/showthread.php?t=1238769") for a (somewhat) simple way to share directories with ACL's.

There is also a way to change the default umask in /etc/login.defs but that would apply to every new file created, not just the ones in the shared folder.  To share just one folder, I think ACL's would be a better solution (just my opinion)

---

### Post by movieman on 2009-08-16
> **glitch83 said:**
> But the umask command doesn't make sense to me - its affects only exist for the lifetime of the process. This means that most people hack their way through umask using the bashrc or profile etc.

Umask is intended to protect the user (e.g. ensuring they don't accidentally create files they don't want others to access), not control them.

---

### Post by koenn on 2009-08-16
there's a default umask in /etc/login.defs, that would cover all login shells, and is pretty persistent.  Oher entry points to the system (eg files created through samba) have their own solutions for this.
 
If you think 0022 is not right, you change it. 

umask is mostly a relic of the times when all access to a system woud be through login shells, and even then, it's no substitute for chmod and chown, they complement each other

/etc/login.defs has some info on possible alternatives

---

### Post by koenn on 2009-08-16
> **jeffathehutt said:**
> 
There is also a way to change the default umask in /etc/login.defs but that would apply to every new file created, not just the ones in the shared folder.  To share just one folder, I think ACL's would be a better solution (just my opinion)
sorry, overlooked your post.

Yes, POSIX ACL is pretty ganular aand an adequate solution for this sort of problems.

---

### Post by glitch83 on 2009-08-17
Well my question was more on the DESIGN of umask. It seems you can set it "per machine", "per user" but not "per directory". What is the logic behind this? Sure I could set it in /etc/... but that would set it for all users. Sure I could set it somewhere in ~/... but that would set it for a user. It seems logical that you want different behavior in different directories on occasion. Why is this not the case? Umask seems like a hack... 

Also its imperative that the solution works for ssh so samba isn't part of the solution. 

Any thoughts or solutions? I mean I could set it per user but if I have a different directory where I want a "group read only" mentality, then I'm SOL... ?

---

### Post by glitch83 on 2009-08-17
Nevermind. Give me a moment, ACLs are probably what I want. I skimmed the answers poorly.

---

### Post by glitch83 on 2009-08-17
Alright I spoke too soon, this was the solution for me: 

[http://ubuntuforums.org/showthread.php?t=145741](http://ubuntuforums.org/showthread.php?t=145741)

Thanks everyone for your help! :-)

---

