---
title: "Running autorun.exe from mounted (or copied) iso"
date: 2010-11-08
forum: Wine
---

### Post by lonegreyride on 2010-11-08
Hi guys,

I apologize for the beginner's question, but I've done a lot of searching and I'm still not sure as to whether the problem I'm having is fixable or not.

I have a lynda.com disc that I've had around for quite a while now, and I'm trying to install it (the course) under Wine. I first converted the .uif file to .iso, then mounted it and copied the contents to a folder inside my home folder. After that, I changed the permissions to allow autorun.exe to be executed as a program.

However, when I try to run the autorun.exe file with Wine, I get the message "bad format". As I said, I've done a fair bit of searching for this, but can't find any threads not related to a specific game or application. I'm really just wondering if this error means that I won't be able to run this at all under Wine, or if there is in fact something that I may be able to do to get this to run.

Again, I apologize if you guys see this type of question all the time. If someone could quickly direct me to a thread which answers my question, I'd appreciate that just as much as a direct answer. Thanks for your time,

John

---

### Post by ajgreeny on 2010-11-08
Could the .exe file be an executable zip file?  I have no idea whether or not they will even run in wine, but just put this to you as a possibility.

---

### Post by lonegreyride on 2010-11-08
Hmm, it almost seems like it would be, but when trying to open with Archive Manager, I get an error telling me that it's not a zip file. I'm a bit of a noob about certain things though, so I'm not sure if this would have been the right way to check this out or not. Thanks for the reply.

---

### Post by lonegreyride on 2010-11-08
I figured it out, and feel like a bit of an idiot. I just ended up mounting the .iso with AcetoneISO. I guess I thought that mounting the iso in Ubuntu would be the same as having it run on a virtual drive, but obviously I was wrong. Now that the .iso is mounted as a virtual drive under AcetoneISO, I can see all the content (.mov files) that I couldn't before. The autorun.exe was actually just to install Quicktime, which I obviously don't need, as the default movie player can play those files just fine.

Thanks for taking the time to check out  my post though. I appreciate it.

---

