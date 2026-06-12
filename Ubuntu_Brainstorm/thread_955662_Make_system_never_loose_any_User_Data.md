---
title: "Make system never loose any User Data"
date: 2008-10-22
forum: Ubuntu Brainstorm
---

### Post by shstmoed on 2008-10-22
Many users experience data loss when something unexpected happens. For example when you write a forum message in your internet browser and you have a power outage. Next time you restart your computer the internet browser may come up again but your input data is lost. The best experience would be that the computer comes up in the exact same state it was before, with an open browser and the text you started to write. The same should work with every application, you shouldn't have to worry to loose your data. In my opinion, this would greatly increase user experience. 

(sometimes i have had a crash with openoffice, then it comes up again and tries to recover your data...i think the idea is right but users shouldn't have to _recover_ anything, their data should just come up again, for experienced users there could be an option where they can choose to fall back to older states of their application but i have never felt the need to _not recover_ (why should i?) )

---

### Post by cdenley on 2008-10-22
You can write to computer memory something like 1000x faster than you can a hard drive. However, memory is volatile, which means that if you don't keep it powered, you lose the data on it. If you want your state maintained consistently, even after an unexpected power outage, you would have to write everything to the hard drive instead of memory, which would make any desktop unusable because it would be too slow.

---

### Post by gnomeuser on 2008-10-22
> **cdenley said:**
> You can write to computer memory something like 1000x faster than you can a hard drive. However, memory is volatile, which means that if you don't keep it powered, you lose the data on it. If you want your state maintained consistently, even after an unexpected power outage, you would have to write everything to the hard drive instead of memory, which would make any desktop unusable because it would be too slow.

and how would you guard against that harddrive being corrupted.. filesystems are fragile in the face of sudden power loss, the harddrive ages often to a sudden and ungraceful death.. 

100% insurance against dataloss is frankly put 100% impossible.

---

### Post by shstmoed on 2008-10-22
> **gnomeuser said:**
> 100% insurance against dataloss is frankly put 100% impossible.

If someone tells you something is 100% impossible, he is probably wrong :)
I hope you agree that the idea of safe data is desirable, i am sure you are right that it is impossible to do with todays hardware. In my opinion this should change. Solid state disks promise to be a lot faster in the future, maybe it could be possible to write everything to the hard disk at once and at the same time have a very usable desktop for normal users. Everyone who wants to have maximum performance can switch this feature off. Maybe there should be a more elegant solution implemented on the hardware side, or maybe it is possible to implement something on the software side which doesn't save my date 100% of the time but maybe 95% of the time...i think this would be an improvement over the current state. It's just that i have had experiences of data loss where it was not necessary to happen. My example with the input box in the browser shows this, the data doesn't have to be written at once to be safe, it could be saved maybe some seconds later and most of the stuff i have written would still be there even when an power outage interrupts my writing.

---

### Post by smartboyathome on 2008-10-22
> **shstmoed said:**
> If someone tells you something is 100% impossible, he is probably wrong :)
I hope you agree that the idea of safe data is desirable, i am sure you are right that it is impossible to do with todays hardware. In my opinion this should change. Solid state disks promise to be a lot faster in the future, maybe it could be possible to write everything to the hard disk at once and at the same time have a very usable desktop for normal users. Everyone who wants to have maximum performance can switch this feature off. Maybe there should be a more elegant solution implemented on the hardware side, or maybe it is possible to implement something on the software side which doesn't save my date 100% of the time but maybe 95% of the time...i think this would be an improvement over the current state. It's just that i have had experiences of data loss where it was not necessary to happen. My example with the input box in the browser shows this, the data doesn't have to be written at once to be safe, it could be saved maybe some seconds later and most of the stuff i have written would still be there even when an power outage interrupts my writing.

Solid state disks don't have good write times though. They are very fast at reading, but writing is their weak point. SSDs are also more expensive than hard drives and are not nearly as big as regular ones. They may not be in the future, but right now thats the case, and we should be looking at stuff which can be done right now.

By the way, if you want this, you could always get rid of your RAM and run totally off swap. How slow this would be I do not know, but its possible already.

---

### Post by panda726 on 2008-10-22
Correct me if I am wrong here, but I believe that even if SSDs could write quickly enough, there is still the problem with extensive re-writing to them.  I believe distros designed for use with SSD computers either turn off of minimize swap usage and set logging to a less intensive or less frequent level in order to protect the disk from premature death.

Tor

---

### Post by gnomeuser on 2008-10-22
> **shstmoed said:**
> If someone tells you something is 100% impossible, he is probably wrong :)
I hope you agree that the idea of safe data is desirable, i am sure you are right that it is impossible to do with todays hardware. In my opinion this should change. Solid state disks promise to be a lot faster in the future, maybe it could be possible to write everything to the hard disk at once and at the same time have a very usable desktop for normal users. Everyone who wants to have maximum performance can switch this feature off. Maybe there should be a more elegant solution implemented on the hardware side, or maybe it is possible to implement something on the software side which doesn't save my date 100% of the time but maybe 95% of the time...i think this would be an improvement over the current state. It's just that i have had experiences of data loss where it was not necessary to happen. My example with the input box in the browser shows this, the data doesn't have to be written at once to be safe, it could be saved maybe some seconds later and most of the stuff i have written would still be there even when an power outage interrupts my writing.

we already do 95% of the time, through journalling and good design. If you lose data it is a bug but we cannot make it to 100%. Could applications do better with autosaving, sure.. most important apps already do this though.

You hold up SSDs as you messiah but even those break, those have wear down, even those have filesystem bugs or unexpected outcome in the event of a power outage.

Now in the interest of being productive here are some things that will make this better.

Wizbit - [http://live.gnome.org/Wizbit](http://live.gnome.org/Wizbit) - think of this as revision control for your files, applications will be able to do advanced rollback, and they can keep a autosave branch which would make it easy to rely on and hopefully easy to implement. This gets you a bit of the way towards never losing data, it also hopefully will give application developers a nice API so they will actually use it.

btrfs - [http://btrfs.wiki.kernel.org/index.php/Main_Page](http://btrfs.wiki.kernel.org/index.php/Main_Page) - think of this as the next generation filesystem, it's copy on write which ensures certain data loss scenerios can't happen, it also lets you do snapshotting giving you the ability to recover from many problems.

Aside this we can (and on Red Hats dime and innovation are) integrating SMART and other hardware monitoring into the desktop, this way when bad stuff(tm) is about the happen you will hopefully be forewarned. 

Aside this, to avoid hardware failure, install a UPS, do RAID1, have a NAS at home for reachable backups, do backups of the backup to something like Amazon S3 on a regular basis. This will all cut down on your risks, it will cost you money, probably serious money but it will bring you closer to a situation where your data is 100% safe and recoverable. Oh and applications could also benefit from being implemented in a high level language such as C# which offers a lot of good functionality to keep stability, added to this Mono now comes with tools to check source code for common mistakes and problem areas (not to mention performance issues), having such tests integrated with the build system would help us catch many problems before they become potential data corruptors.

That being said, where we are now, saying we aren't even reaching 95% data security would be plain wrong. If we lost data that often it would be a considerable problem, and we could easily forget about enterprise users. We are not this unsafe, we can do better but we can never reach 100% making the original request unreasonable. It doesn't mean we can't do nice things to make it easier to avoid problems and recover from them.

---

### Post by shstmoed on 2008-10-22
> **gnomeuser said:**
> we already do 95% of the time, through journalling and good design. If you lose data it is a bug but we cannot make it to 100%. Could applications do better with autosaving, sure.. most important apps already do this though.

Ok, you are right i also do think that the current state is not _that_ bad. This is why the original idea was to be safe all the time. Now you changed my mind and i agree that it may be impossible to be safe all the time, nevertheless it should be the goal to be safe whenever possible. 
What i had in mind is to protect users from data loss when it would be technical possible but where it just isn't implemented on the software side. 
I am not even sure anymore if my example with the browser input is valid anymore, maybe firefox does this already and also restores my input in case of a power outage. I just know that in the past this wasn't the case. 
Another example i have in mind: The user makes a new document in openoffice, but doesn't save it. When he ends the application, he gets a prompt if he wants to save or discard his changes, now the user accidentally discards his changes. There is no way to undo this, his data is lost, even though it would haven been technically possible to save it.
(this is maybe not even a technical but a privacy question, but i would love such a feature) 

The positive example is nautilus and the trash bin, whenever you accidentally delete files you can restore them.
Also, when you move files and interrupt the transfer, i think i never experienced file lost. Don't know if i have been lucky or how this is done, but i think it works very well. I can remember that when i used windows, this wasn't the case, i never moved files, i always copied them an deleted the old ones because i feared that something goes wrong.

Another example: When i normally work in openoffice, i can undo my changes. Now when i close the file and open it again, i can not undo the changes i did before i closed it. Why? Maybe there are not a lot of people who want to do this, but there may be some. 

Ok, all in all I am really not unhappy with my data safety, I think this was misunderstood. In fact i am really happy, i just think it could also be even better. Above all for normal users who don't know how to make backups or who make often mistakes and could use a helping hand.

---

### Post by kdorf on 2008-10-22
What the other users are saying is that if you understood how the machine actually worked (the differences between volatile RAM and the non-volatile hard disk) you'd understand that with current technology what you're asking for is impossible. If you are that worried about power outages, buy a UPS.

---

### Post by tgalati4 on 2008-10-22
Quality hardware, UPS, linux=reliability

---

### Post by shstmoed on 2008-10-23
> **kdorf said:**
> What the other users are saying is that if you understood how the machine actually worked (the differences between volatile RAM and the non-volatile hard disk) you'd understand that with current technology what you're asking for is impossible. If you are that worried about power outages, buy a UPS.

I think i didn't express myself clear enough, i'm sorry for that. Now, in the meanwhile i came off the idea to make the system _never_ loose any data. But i still think there are scenarios where the computer could act more intelligent and avoid mistakes the user would make or avoid situations where the computer could have saved data but just didn't because no one has thought of it. 
I can think of 2 scenarios:

1. something unexpected like a power outage happens, data is lost because it wasn't saved in any way. I understand that it is not possible to _always_ safe to the harddisk, but i do think it could happen more often. For example, when you start editing a new text in your word processor or editor and you didn't click the safe button, when something happens your data is away. Technically not all data must be lost because the computer could have saved it earlier then you thought of. 
I give you an example for this:
when you edit a new text in gedit, when gedit is killed, your data is away. maybe gedit did even safe a copy of your text and you can retrieve it on the command line, but this is not possible for normal users.
On the other hand if you write a note in tomboy, if tomboy gets killed, your data isn't lost. Because tomboy as i understand it tries to write the data to disk as soon as possible, we don't need non-volatile ram for this, it already works in some applications. 

2. the user makes a mistake and his data is lost, even when the computer could have saved it. I gave an example for this in my last post. I think when there is the decision to make if the computer should save or not save, he should always save, people have enough disk space and privacy issues can be solved with encryption. Then you always will be able to go back to an earlier state of your document. As mentioned by gnomeuser earlier this is already being worked on, so I'm quite happy there. I just think the applications have to be made just a tiny little bit more intelligent in making decisions, because very often the user is not right.

And as i understand it, this is what computers are about: to help you.

---

### Post by gnomeuser on 2008-10-23
> **shstmoed said:**
> I think i didn't express myself clear enough, i'm sorry for that. Now, in the meanwhile i came off the idea to make the system _never_ loose any data. But i still think there are scenarios where the computer could act more intelligent and avoid mistakes the user would make or avoid situations where the computer could have saved data but just didn't because no one has thought of it. 
I can think of 2 scenarios:

1. something unexpected like a power outage happens, data is lost because it wasn't saved in any way. I understand that it is not possible to _always_ safe to the harddisk, but i do think it could happen more often. For example, when you start editing a new text in your word processor or editor and you didn't click the safe button, when something happens your data is away. Technically not all data must be lost because the computer could have saved it earlier then you thought of. 
I give you an example for this:
when you edit a new text in gedit, when gedit is killed, your data is away. maybe gedit did even safe a copy of your text and you can retrieve it on the command line, but this is not possible for normal users.
On the other hand if you write a note in tomboy, if tomboy gets killed, your data isn't lost. Because tomboy as i understand it tries to write the data to disk as soon as possible, we don't need non-volatile ram for this, it already works in some applications. 

2. the user makes a mistake and his data is lost, even when the computer could have saved it. I gave an example for this in my last post. I think when there is the decision to make if the computer should save or not save, he should always save, people have enough disk space and privacy issues can be solved with encryption. Then you always will be able to go back to an earlier state of your document. As mentioned by gnomeuser earlier this is already being worked on, so I'm quite happy there. I just think the applications have to be made just a tiny little bit more intelligent in making decisions, because very often the user is not right.

And as i understand it, this is what computers are about: to help you.

I will once again direct you to Wizbit, it does exactly what you want. You would need it integrated into every app, probably through some glib/gtk API but aside that it should make it easy to keep an autosave branch of every file that is opened, you can commit changes at timed intervals (as a bonus you here also get unlimited very flexible undo). You also gain the ability to be file path agnostic which is very helpful.

Video demo of Wizbit integration in Tomboy, should show a little of what Wizbit can do for us: [http://www.wine-doors.org/screens/wizbit.ogg](http://www.wine-doors.org/screens/wizbit.ogg)

Full blog entry detailing the above demo: [http://www.qdh.org.uk/wordpress/?p=242](http://www.qdh.org.uk/wordpress/?p=242)

---

