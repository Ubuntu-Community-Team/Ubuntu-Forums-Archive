---
title: "&quot;Speech engine not found&quot; error"
date: 2010-07-01
forum: Wine
---

### Post by sarthorks on 2010-07-01
My aim is to get a software called Vocaboly running on wine.
Heres the download link: [http://www.vocaboly.com/download.php](http://www.vocaboly.com/download.php). 

If someone could get it running for me under wine (im on ubuntu 10.04 and wine-1.2-rc4), i'd appreciate it very much. 

It installs fine, but on running is giving me an error of "Speech engine not installed", and then it pops open a dialogue box saying there was a serious error in the exe file.

In one of the configuration files for the software, in its installation directory, i noticed the phrase "speech engine not found" under FATAL error messages. SO i guess the problem maybe is getting a speech engine to work in wine.

For that I tried msttss22L.exe from this link : [http://www.microsoft.com/downloads/details.aspx?displaylang=en&FamilyID=5e86ec97-40a7-453f-b0ee-6583171b4530#Instructions](http://www.microsoft.com/downloads/details.aspx?displaylang=en&FamilyID=5e86ec97-40a7-453f-b0ee-6583171b4530#Instructions). 
I double click it, i see some progression bars for a second, and then its back to the desktop.
i also tried Sp5TTIntXP.exe (on the same page), but that opens up an unzipper, and on unzipping it gives me a .msm file, and i dont know what to do with it.

Can anyone report similar problems? can anyone help me? Thanks in advance.

---

### Post by sarthorks on 2010-07-01
My aim is to get a software called Vocaboly running on wine.
Heres the download link: [http://www.vocaboly.com/download.php](http://www.vocaboly.com/download.php).

If someone could get it running for me under wine (im on ubuntu 10.04 and wine-1.2-rc4), i'd appreciate it very much.

It installs fine, but on running is giving me an error of "Speech engine not installed", and then it pops open a dialogue box saying there was a serious error in the exe file.

In one of the configuration files for the software, in its installation directory, i noticed the phrase "speech engine not found" under FATAL error messages. SO i guess the problem maybe is getting a speech engine to work in wine.

For that I tried msttss22L.exe from this link : [http://www.microsoft.com/downloads/details.aspx?displaylang=en&FamilyID=5e86ec97-40a7-453f-b0ee-6583171b4530#Instructions](http://www.microsoft.com/downloads/details.aspx?displaylang=en&FamilyID=5e86ec97-40a7-453f-b0ee-6583171b4530#Instructions)
I double click it, i see some progression bars for a second, and then its back to the desktop.
i also tried Sp5TTIntXP.exe (on the same page), but that opens up an unzipper, and on unzipping it gives me a .msm file, and i dont know what to do with it.

Can anyone report similar problems? can anyone help me? Thanks in advance.

---

### Post by sarthorks on 2010-07-01
anyone?

---

### Post by cogadh on 2010-07-01
First of all, you need to be a bit more patient. It can take 24-48 hours before someone comes along with a potential answer to your question and even then, they might only need to ask you for more details. 

As for your problem, chances are, Vocaboly is looking for the built-in speech functions of Windows (i.e. "Microsoft Mike"), which are not at all present in Wine. Installing the speech SDK was a good idea, but I don't think it actually includes the speech engine, since that is already part of every current version of Windows by default. Additionally, I believe Microsoft's speech engine works as a device driver in Windows (I know for certain it does when converting text to speech), so it will never work in Wine anyway, since Wine will never support Windows drivers.

---

### Post by cariboo on 2010-07-01
I have merged your two threads, that were probably created due to database problems.

---

### Post by sarthorks on 2010-07-03
Yes thanks. 

Yes that day, I would create a new thread, but later would not find it at all. Thats why i posted multiple times with no success that day.

---

### Post by dino99 on 2010-07-03
if you search "vocaboly" into winehq base, there is no thread at all

but report exist:
[http://www.pubbs.net/201006/wine/43582-bug-23339-new-application-does-not-run-vocabolyexe.html](http://www.pubbs.net/201006/wine/43582-bug-23339-new-application-does-not-run-vocabolyexe.html)

have you search "speech" into synaptic ? and tried some apps to know if they work like you need ?

---

