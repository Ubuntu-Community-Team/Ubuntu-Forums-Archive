---
title: "Microsoft Office 2010"
date: 2010-09-01
forum: Wine
---

### Post by SEECo on 2010-09-01
Can anyone out there tell me that how to install Microsoft office 2007 in ubuntu of kubuntu.

---

### Post by Elfy on 2010-09-01
You need wine. 

[https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

---

### Post by SEECo on 2010-09-01
This is not the problem. The problem is that i have installed wine and microsoft office but when i try to run any of the program it doesn't starts. Do you know about it.

---

### Post by jtarin on 2010-09-01
[MSWord 2007 Wine Guide]("http://mediakey.dk/~cc/howto-office-2007-on-linux-with-wine/")

---

### Post by Elfy on 2010-09-01
moved to wine

---

### Post by 4ebees on 2010-09-01
> **SEECo said:**
> Can anyone out there tell me that how to install Microsoft office 2007 in ubuntu of kubuntu.

I'm curious - what is in Office 2007 that you need?

Just curious :D

---

### Post by SEECo on 2010-09-01
The thing in microsoft office i need is Word, Powerpoint and Excel.

---

### Post by NoNameWill on 2010-09-01
> **SEECo said:**
> The thing in microsoft office i need is Word, Powerpoint and Excel.


Have you not used open office? I use the open office "word" and "excel" but not "power point" under open office. OO is cross platform so you can save in MS extentions.

---

### Post by jtarin on 2010-09-01
I agree about OO being all it can be and use it myself, but my business has some forms that only format well in MS, so I have both on my install. Sometimes necessity overrides principles.

---

### Post by ayllu on 2010-09-23
I had to installed, because y need to share some files in my office, so use play on linux

sudo apt-get install playonlinux 

There, you can find a easy way to install it, 

But is better to work with Open Office because you save time working with long documentes, and another features that MS dosnt have.

---

### Post by beew on 2010-09-24
Many people use MS2003 so they cannot read the format in MS2007 anyway (but Open Office can save to docx and xlsx etc) These people are probably too clueless or don't have admin privilege to install the plugin for MS2003 to read MS2007 formats. So even though we have MS2007 at work but the default is to save everything in MS2003 format.  

I heard that MS2010 can read open formats, so if you assume the people you deal with are up to date in their MS office suite you should just send them open documents.

MS wants its format to be the default standard and yet wants to keep it closed, they can't have it both ways. Can you imagine having to pay a fee everytime you use the metric system?

---

### Post by Stratok on 2010-11-12
Indeed, office 2010 can save in open document formats

office 2007 +servicepacks I&II  can also work with open document formats


So far Ive only been able to run office 2010 in virtual-box, in a lightweight windows xp version. boots in just 10 seconds, so it is usable.

As for office 2007, word excel and powerpoint seem to run very well in wine using playonlinux, but I have been not able to  install the service packs.

---

### Post by SEECo on 2010-11-13
Thanx everyone for reply i have solved my problem a month ago and using msoffice2007 happily

---

### Post by Notnerdyenoughyet on 2010-11-15
-I saw that the title includes 2010 but it talked about 2007...
- I have been reading in the forums for 2 hours, changing stuff with seemingly progessing, but not being able to setup.
I downloaded wine and mic office 2010 (i use it by the way, since it has less errors than open office! which magically changes titles and has problems with more than a couple files open at the same time) 
and changed wine settings ([http://www.junauza.com/2010/04/how-to-install-microsoft-office-on.html](http://www.junauza.com/2010/04/how-to-install-microsoft-office-on.html)) put office to the desktop; changed the properties to trusted, then tried to run the setup.exe with wine, but it just told me that i need WINDOWS!

note: i am quite helpless and actually have no real computer knowledge!
Since I already tried it for hours (the first time i tried, i had a original cd, but then my cd-drive was ****ed up and i didnt think about that as an error), it would be great, if somebody can explain me what to do in an easy way, so i dont have to first look up all the terminology and co! I am really close to switch to windows again, but i dont wanna give up to easily!

---

### Post by jtarin on 2010-11-15
> **Notnerdyenoughyet said:**
> -I saw that the title includes 2010 but it talked about 2007...
- I have been reading in the forums for 2 hours, changing stuff with seemingly progessing, but not being able to setup.
I downloaded wine and mic office 2010 (i use it by the way, since it has less errors than open office! which magically changes titles and has problems with more than a couple files open at the same time) 
and changed wine settings ([http://www.junauza.com/2010/04/how-to-install-microsoft-office-on.html](http://www.junauza.com/2010/04/how-to-install-microsoft-office-on.html)) put office to the desktop; changed the properties to trusted, then tried to run the setup.exe with wine, but it just told me that i need WINDOWS!

note: i am quite helpless and actually have no real computer knowledge!
Since I already tried it for hours (the first time i tried, i had a original cd, but then my cd-drive was ****ed up and i didnt think about that as an error), it would be great, if somebody can explain me what to do in an easy way, so i dont have to first look up all the terminology and co! I am really close to switch to windows again, but i dont wanna give up to easily!

Office 2010 is not supported by WINE yet to the best of my knowledge. If you want to run 2010 I would suggest doing as above.> So far Ive only been able to run office 2010 in virtual-box, in a lightweight windows xp version. boots in just 10 seconds, so it is usable.Virtual box can be found in the repositories, but you will need a Windows installation disk to complete the process.

---

### Post by Notnerdyenoughyet on 2010-11-16
;-(....
downloaded virtual box yesterday, assumed that i will need some windows, but hoped for it not be the case. not having windows at home made me install ubuntu in the first place. arrgh, this sucks.

thank you for your quick reply!

ps: is there any use for wine than? (rhetorical) so far i couldnt do anything with it.

---

