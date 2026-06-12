---
title: "Problems after today's system update: no System Settings, Messaging and more"
date: 2015-10-20
forum: Ubuntu Phone and Tablet
---

### Post by Ivan_Sebastiani on 2015-10-20
Today  (20.10.2015) I have updated my Aquaris E4.5 Ubuntu Edition phone. Ever since I have serious issues with my phone.

System Settings crash immediately when I try to open it. The same with Messaging as it crashed immediately and I neither cannot access old messages nor write&send new ones. Also cannot cancel the call in a usual way (need to close the phone scope and re-launch it). Also in Terminal I cannot write a dash (this one - ). There might be other issues down the line....

All of these is pretty urgent and would really really appreciate some support.

Thanx
Ivan

---

### Post by howefield on 2015-10-20
Have you tried hard rebooting the phone, holding both the power and volume up buttons for several seconds...

---

### Post by Ivan_Sebastiani on 2015-10-20
Yes. Several times. Problem remains. /also on a side note...as far as I can tell it there is no difference if I hold just the power button...I get the same option to shut down; restart; cancel/

Oh...and I just realized that Browser does not work as well + I cannot access the number/symbols panel on the keyboard. Really not looking good...

---

### Post by howefield on 2015-10-20
Is there something you are not telling us, perhaps you have been exploring the phone with the terminal and carried out some non standard procedure that may or may not be reversible ?

Might be quicker to reset the image to factory default (ensuring of course you have important data backed up) ?

---

### Post by Ivan_Sebastiani on 2015-10-20
Definitely have not done anything with/through the terminal. The only supposedly unusual thing today (besides browsing the web through wi-fi and sending one text message) was that I have put in a second SIM card. It might be that the installation of the system update was taking place exactly at the time when I put the second sim card in....and this might have affected the updating process? Besides going for factory reset...are there other ways I should explore before that? 

If not...is there a way to back up contacts without doing it via gmail sync? What about archiving the messages and then restoring them? 

Would appreciate a detailed step-by-step guide on doing the factory reset. And I am not really fluent in these kind of things...

---

### Post by KanedaSan on 2015-10-20
"If not...is there a way to back up contacts without doing it via gmail  sync? What about archiving the messages and then restoring them?"
Interested in knowing how to do this too.

---

### Post by raminzeb on 2015-10-20
cant you do a factory reset by holding both the volume up button and the power button on start up. then from the menu select recovery. once the screen with the large round ubuntu logo appears you can use your volume up and down to select factory reset I think.

---

### Post by howefield on 2015-10-20
> **Ivan_Sebastiani said:**
> ...I have put in a second SIM card. It might be that the installation of the system update was taking place exactly at the time when I put the second sim card in....and this might have affected the updating process? Besides going for factory reset...are there other ways I should explore before that? 

I'd say it was good practice to leave the phone alone whilst in the middle of an upgrade or update. Can't imagine trying to use the phone far less plug something into it whilst carrying out such an invasive process as upgrading the underlying image, that's not to say that that caused your issues, though it most certainly wouldn't have helped ;)

> If not...is there a way to back up contacts without doing it via gmail sync? What about archiving the messages and then restoring them? 

I'd connect the phone (with developer mode enabled & "lock when idle" set to never) to an Ubuntu computer that had adb and ssh installed and available, then use adb shell to scp files from the phone to the computer. 

> Would appreciate a detailed step-by-step guide on doing the factory reset. And I am not really fluent in these kind of things...

I have only ever reset the phone via System Settings > Reset phone > Erase & Reset Everything.

---

### Post by KanedaSan on 2015-10-20
"then use adb shell to scp _files from the phone to the computer_"
Obviously yes, but, which files in which folder(s), [edit : please ^^]?

---

### Post by howefield on 2015-10-20
> **kaneda3 said:**
> "then use adb shell to scp _files from the phone to the computer_"
Obviously yes, but, which files in which folder(s), [edit : please ^^]?

For contacts..

```
~/.local/share/evolution/
```

within that folder, you'll find addressbook, calendar, mail, memos and tasks folders - addressbook contains the contacts.db file but it probably makes sense to have a copy of all them, you only need to restore the files that you wish to.

For messages,

```
~/.local/share/history-service/history.sqlite
```

I take a full copy from the phone, it's quick to do and can copy back whatever is needed. Shrug :)

---

### Post by KanedaSan on 2015-10-20
Thank you very much!
By the way it's possible to access those files with the file explorer app (user files, choose "show hidden files" in prefs), so they can be saved easily without any uDesktop/ssh/adb (i'm still a poor windows 7 user... and yes i could install VM but prefer simple ways).

---

### Post by Ivan_Sebastiani on 2015-10-21
[QUOTE=howefield;13376307] I'd connect the phone (with developer mode enabled & "lock when idle" set to never) to an Ubuntu computer that had adb and ssh installed and available, then use adb shell to scp files from the phone to the computer. 

How do I connect the phone in "developer mode enabled" if I don't have access to System Settings?

---

### Post by Ivan_Sebastiani on 2015-10-21
Well...I went for the factory reset and it is all fine now. Other options seemed too complicated and time is not exactly on my side these days. Thanx for the effort!

---

