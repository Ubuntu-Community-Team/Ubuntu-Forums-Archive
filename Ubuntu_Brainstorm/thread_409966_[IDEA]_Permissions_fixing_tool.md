---
title: "[IDEA]: Permissions fixing tool"
date: 2007-04-15
forum: Ubuntu Brainstorm
---

### Post by aysiu on 2007-04-15
**Summary:**
An application or utility--even a command-line tool--to repair permissions on a broken Ubuntu system.

**Rationale:**
Sometimes new users get overzealous and *chown -R* or *chmod -R* their whole systems in a bad way (to user or 777, respectively). Sometimes even experienced users make a typo in a command and end up screwing up permissions or ownership on an entire directory.

**Scope and Use Cases:**
Lena accidentally changed permission on her entire Ubuntu installation to 777. Now she has a totally non-functional Ubuntu. The best advice she gets from other forum users is to reinstall Ubuntu.

**Implementation Plan:**
While there's no way to know what permissions and ownership personal files could have had, there is probably some kind of template or comparison a program could make on important system files (like /etc/sudoers) and general user files (like .dmrc). If the system is mostly borked, maybe it could be a simple command you run from Recovery Mode ```
sudo permrepair
``` If the system is completely borked, maybe it could be a few commands you run off a live CD.

This may be technically too difficult to implement, but I thought I'd just throw it out there as a suggestion.

**Blueprint**:
[https://blueprints.launchpad.net/ubuntu/+spec/permissions-repair-tool](https://blueprints.launchpad.net/ubuntu/+spec/permissions-repair-tool)

---

### Post by aidanr on 2007-04-15
good idea, as far as i know macs have a similar tool

---

### Post by aysiu on 2007-04-15
> **aidanr said:**
> good idea, as far as i know macs have a similar tool
Yes, Mac has it, and my wife has had to use it on more than one occasion on her Powerbook. It's handy.

---

### Post by tenn on 2007-04-15
So what stops people from typing another command.

---

### Post by =0verlord= on 2007-04-15
Good idea - shouldn't be *too* much work to document the permissions for system files.  Then it's just a matter of chmoding down the list :)

---

### Post by .t. on 2007-04-15
It's very, very difficult to know which files should have which permissions, and I'm unsure how OS X accomplishes it. Many services install their own users and groups, and their files are owned by those users and groups, and without a preconfigured list, it's very hard to guess which files are owned by which users, and a `chown -R root:root /` is not very safe; probably less safe than the initail ruining of the system. We should ask ourself why the user chose to do this, and perhaps implementing a confirmation into chmod is the better option.

---

### Post by =0verlord= on 2007-04-15
> **.t. said:**
> It's very, very difficult to know which files should have which permissions, and I'm unsure how OS X accomplishes it. Many services install their own users and groups, and their files are owned by those users and groups, and without a preconfigured list, it's very hard to guess which files are owned by which users, and a `chown -R root:root /` is not very safe; probably less safe than the initail ruining of the system. We should ask ourself why the user chose to do this, and perhaps implementing a confirmation into chmod is the better option.


I was talking about the core system which, while nontrivial, is still a defined set of packages that would already have the file permissions on hand in the debs.

I don't think this should be a high priority, but recovery systems are always nice especially if Ubuntu wishes to cater to casual users.

---

### Post by 23meg on 2007-04-15
A preconfigured list for default system folders, plus frequent system wide snapshots would be necessary, but may not be sufficient, and would be quite a job to implement. It may be a better idea to introduce a simple safety mechanism to chmod; even aliasing "chmod" to "chmod --preserve-root" would perhaps go a long way in preventing users from shooting themselves in the foot.

---

### Post by 3rdalbum on 2007-04-15
It's an okay idea, and I've actually chmodded my whole filesystem before now and wanted it to get back to the way it was before (I made it too permissive). I was actually trying to fix another problem.

But users really shouldn't play around with chmod and chown without being very careful. They also shouldn't use rm -rf without first double-checking their command. There are so many things that you can do to bork a Linux system; how many recovery programs would you need to write?

If users mistyping this particular command is a real issue, then by all means write the program. But I don't think this is a big enough problem to warrant a program being included with Ubuntu. For a system recovery Live CD, yep, sure. But not for Ubuntu.

For the record, OS X has a permissions resetting program because the OS plays awful tricks with its own security system, and frequently gets confused and messes up. On Ubuntu, I've only once had some incorrect permissions set, and this was due to filesystem damage. Chmodding didn't fix the problem, so a permissions-repair program wouldn't have helped.

---

### Post by PriceChild on 2007-04-15
As far as I know... doing this would require reading every single .deb to see what needs to be changed and set to defaults before changing them... basically going through a reinstall but with the possiblity of breakage by missing things.

If a user is going to execute commands like that without realising what they are doing then it is a very good lesson for them IMO.

---

### Post by =0verlord= on 2007-04-15
Upon a little investigating, I don't think that the benefits outweigh what the costs of creating and (especially) maintaining the list would be.  It's doable but just not worth the effort at this time - screwing up badly enough to need recovery but not totally borking the system is not what I'd call a common occurrence, as has been noted.

PriceChild, "lessons" just end up pissing people off, even when they're at fault.  Happens to the best of us and being sympathetic + suggesting a reinstall is our best option.

---

### Post by Jonne on 2007-04-15
how about just an easy 'reinstall' command? 
sudo aptitude dist-reinstall ;)

You'd normally have your .debs in your cache, so re-downloading them wouldn't be necessary. It would also help in other situations where you screwed up completely.

---

### Post by =0verlord= on 2007-04-15
I like the reinstall idea from a live CD, but would that try to save your /home data or would it be a redundant install?

---

### Post by jackmaninov on 2007-04-15
Why would anyone need to maintain a database of the default permissions on packaged files? APT rolls them out to the file system, it should be able to store the permissions its using as it does this in a database somewhere. AFAIK rpm does this.

This should probably be a feature request for apt.

---

### Post by PriceChild on 2007-04-15
> **jackmaninov said:**
> it should be able to store the permissions its using as it does this in a database somewhere. AFAIK rpm does this.They're in the .deb packages... and I still don't think it would be much easier to read these and apply them than reinstall the entire system.

---

### Post by Ric95 on 2007-04-15
I think it would be best to just R-click on the file and have shell options; permit once/permit always//password.
That would also avoid that bad habit of additive programing..

---

### Post by plb on 2007-04-15
Doesn't Suse have something where you can boot from the cd and repair the whole system?

---

