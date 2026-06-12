---
title: "Why the Ubuntu team do not update their repo ?"
date: 2015-03-20
forum: Ubuntu, Linux and OS Chat
---

### Post by walker17x on 2015-03-20
Hi ! , i'm a  new ubuntu user and i wanna understand why the ubuntu team are updating only firefox , chromium and some other software , there is a lot of packages in the repo , and updating them will not affect the system stability.

for exemple i want to use the last version of inkscape , gimp and libreoffice with my 14.04 lts version , but i can't without installing a lot of PPA.

so why they don't update the entire repo ? like in manjaro linux , why firefox , chromium and some others only ?

thanks

---

### Post by mastablasta on 2015-03-20
> **walker17x said:**
> ..., there is a lot of packages in the repo , and updating them will not affect the system stability.



and you are absolutely 100% sure of that? did you do the extensive testing to make sure it all works as it should? you see you do not update only inkscape but various other libraries (packages) that inskcape is using and that are being shared with other programs in the repo.

besides if all works as it should then using PPA shouldn't be an issue. I mean after all the PPA source is open and you checked it for any possible security holes and such before installing it. ;)

by the way there is ubuntu development version which should always have newer packages available. not sure if they are all the latest. but in any case you could use that since you say the packages won't affect system stability and all that.

by the way stability means that system has known bugs for the most part it is well tested and stays more or less unchanged in it's known state. major and also some smaller bugs are then resolved on that stable state.in any case it has been tested more and bugs are less likely to occur. even those that cause crashes. to keep it that way you need to keep packages stable not add untested or fresh development packages where things are cooked.

---

### Post by buzzingrobot on 2015-03-20
Ubuntu packages originate in the Debian repos, from where they are pulled at certain intervals in the release cycle.  

Building the very latest software can often also require updating and rebuilding many of the core components of a distributions.  That can, in turn, require updating and rebuilding many of the applications in use. Each updated package introduces the chance of bugs or new incompatibilities.

If you really want or need the latest software across the board you should look at rolling release distributions like Arch.  No distribution that releases on a fixed schedule can do that.

A small minority of Linux software contain all or almost all of supporting code they require within their executable file.  Firefox, etc., are among them.  That greatly simplifies their update.

---

### Post by d-cosner on 2015-03-20
The most practical ways of having up to date apps in Ubuntu are ppa repos or being patient and upgrading to the next release. I have always had success using both of these methods. As for rolling releases, in my opinion, PCLinuxOS and Manjaro are the best as far as ease of use and stability. I could go on about these choices and my conclusions but you can research that for yourself if you choose to take that route.

---

### Post by sandyd on 2015-03-20
If you want to get the latest versions, rolling your own packages is quite easy

Some non-direct steps:
```

apt-get source packagename
```
Rip out the debian folder, and download new sources.

Rename sources file to packagename.orig.tar.gz

Extract packagename.orig.tar.gz and place debian folder inside extracted folder

Edit debian/changelog to reflect an updated version and your GPG key details (name, email)

Use debuild -D to do a test build of software, if there are any patch failures, remove them, but keep in mind that it is now** _your_ job to keep the package updated against security vulnerabilities, both existing, future, and previous.** A lot of work goes into keeping security patches done by the Ubuntu Security Team.

Use debuild -S after debuild -D succeeds to upload to your own launchpad PPA.

---

### Post by grahammechanical on 2015-03-20
The purpose of a Long Term Support release is to provide an operating system and applications that do not get changed frequently and so forcing business users to re-train their employees and also increase the work load of support staff.

With Ubuntu we get a six month release cycle. Each new release has the latest stable improvements from Linux developers upstream to Ubuntu. That is one way to get the latest when using Ubuntu. But there is another way, and that is through PPAs.

Software in the Ubuntu repositories is code audited to make sure that it does not contain any malicious code. Can you imagine the time it takes to do that? I do not think that you can. I cannot because I have never done that work. PPAs are a way of by-passing that process but we the user accept responsibility.

Remember also that different FOSS projects have different development schedules. They all work at their own speed. The releasing of new versions is not coordinated with the release schedules of Linux distributors.

Regards.

---

