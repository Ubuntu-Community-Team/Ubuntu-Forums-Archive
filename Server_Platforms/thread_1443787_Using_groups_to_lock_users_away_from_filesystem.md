---
title: "Using groups to lock users away from filesystem"
date: 2010-03-31
forum: Server Platforms
---

### Post by HellSpawneD on 2010-03-31
Hi, I'm currently running a small server using 9.10 and I wondered if using groups was a possible route in order to keep users away from the bulk of the file system and keep them in locked their home directories.

What I planned to do is use a group named 'allowsystemfiles' to be added to admin accounts, then to set parts of the file system to that group, along with the permissions 0760 to keep non-admin users out.

Is is a good idea or will this hose my system? 

My users access the server using ssh if that helps.

---

### Post by Bachstelze on 2010-03-31
> **HellSpawneD said:**
> then to set parts of the file system to that group, along with the permissions 0760 to keep non-admin users out.

You probably meant 0750, but anyway, which "parts of the file system" are we talking about here?

---

### Post by HellSpawneD on 2010-03-31
Yes, 0750 is a better idea.
I'd like to prevent access to /etc and /var foremost, but I don't know if this is possible without preventing applications as a side effect. 

Ideally I want them to only have access to their own directory.

---

### Post by cdenley on 2010-03-31
What kind of server? How do the users access it?

There may be some files in /etc and /var which processes not running as root need read access to.

---

### Post by HellSpawneD on 2010-03-31
> **cdenley said:**
> What kind of server? How do the users access it?

There may be some files in /etc and /var which processes not running as root need read access to.

I am a uni student and the server helps me access my own files remotely from the campus, while also allowing me to run processes on my own machine that the restricted uni network would deny access to. 

A good example of this was an end of term animation project that needed to be converted to a different file format; I was able to remotely install 'mencode' on my server, re-encode the video and download it at the campus. It would be advantageous to allow some of my friends to do this also, without allowing my system to be compromised accidentally/intentionally.

As I mentioned in my first post, users access my server via ssh. If I can prevent access using that instead of messing with groups, that would be a little easier.

---

### Post by Bachstelze on 2010-03-31
> **HellSpawneD said:**
> It would be advantageous to allow some of my friends to do this also, without allowing my system to be compromised accidentally/intentionally.

Just don't give them root access. ;) That's why we have a root acoount: so that normal users can't do things that would harm the system.

---

### Post by cdenley on 2010-03-31
> **HellSpawneD said:**
> I am a uni student and the server helps me access my own files remotely from the campus, while also allowing me to run processes on my own machine that the restricted uni network would deny access to. 

A good example of this was an end of term animation project that needed to be converted to a different file format; I was able to remotely install 'mencode' on my server, re-encode the video and download it at the campus. It would be advantageous to allow some of my friends to do this also, without allowing my system to be compromised accidentally/intentionally.

As I mentioned in my first post, users access my server via ssh. If I can prevent access using that instead of messing with groups, that would be a little easier.

Users need access to lots of stuff in /etc, and probably /var, in order to have a fully functional shell. The only real way to give users a full shell without giving them access to your whole filesystem would be to give them a chroot environment. If it were only file access, then you could chroot them to their home directory. You can try restricting access to specific files and directories within /etc and /var with permissions or ACL's, but that wouldn't be worth the trouble in my opinion.

---

### Post by HellSpawneD on 2010-03-31
> **cdenley said:**
> Users need access to lots of stuff in /etc, and probably /var, in order to have a fully functional shell. The only real way to give users a full shell without giving them access to your whole filesystem would be to give them a chroot environment. If it were only file access, then you could chroot them to their home directory. You can try restricting access to specific files and directories within /etc and /var with permissions or ACL's, but that wouldn't be worth the trouble in my opinion.

Hmm, it does sound like a lot more trouble than its worth at this point. I've taken a look at chroot but found nothing compelling enough to want to implement it.

Cheers for your help anyways folks ^^ :)

---

