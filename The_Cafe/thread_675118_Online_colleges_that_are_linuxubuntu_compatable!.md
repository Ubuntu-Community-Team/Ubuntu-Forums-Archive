---
title: "Online colleges that are linux/ubuntu compatable?!?"
date: 2008-01-22
forum: The Cafe
---

### Post by EmilyRose on 2008-01-22
So... I'm trying to figure out where I want to go back to school at.. I'm pretty much limited to online schools due to location and inability to move. So, as I go through, like, all of them say that you have to have windows xp/vista. Which just blows and pisses me off. I mean, why? I'm looking at trying to get a degree in computer programming (either associates or bachelors)... has anyone found a place where I can do this and *NOT* have to install windows?!?!? I mean, seriously. I just really, raelly, really don't want to have to do that!!

---

### Post by compiledkernel on 2008-01-22
Ive heard that [University of Phoenix]("http://www.phoenix.edu/") isnt so bad to deal with. [AIU]("http://www.aiuniv.edu/") is also a consideration. I dont believe either instituions require you to have a windows machine to use their programs states. 

Course that be said, if they did, you could also use [ie4linux]("http://www.tatanka.com.br/ies4linux/page/Main_Page") to get the job done.

---

### Post by Dark Hornet on 2008-01-22
From my experience with online colleges, usually the reason why they want you to have some form of windows is due to the "posting forum" they use for posting your assignments is designed to be used with Outlook.  I took some classes with University of Phoenix, and I used Thunderbird, etc with no issues...so they may "SAY" you have to use windows, but I have found that there are easy ways around it.

---

### Post by rosegarden78 on 2008-01-22
Don't worry!  Web servers and browsers are designed to serve content in compliant web standard and format.  A PHP script served from a Windows server can be read on an Ubuntu box with Firefox and vice versa.  That is: Unless the Windows servers is serving content is some proprietary format.

In my experience with community college Ubuntu accessed web content from a Windows server but it just as easily could have been LAMP server.  The problem used to be encountering .EXE programs but since you can download WINE to run Windows programs (especially simpler ones from schools) there shouldn't be a problem.

P.S.  Just make a symlink to Common Files in your /home/user/.wine/...../windows/Program\ Files/ directory so WINE knows where to look for Common Files instead of copying them twice.  You should be able to run many legacy graphics and multimedia authoring programs designed for Windows as long as your Windows partition is fully functional.

---

### Post by EmilyRose on 2008-01-22
Very cool, thanks guys;) Thats what I figured... they just kept/keep saying that windows was 'required' which I really don't get :D Course, it turns out that what they mean is that they just don't "support" anything else - so if you have issues, your screwed;)

---

