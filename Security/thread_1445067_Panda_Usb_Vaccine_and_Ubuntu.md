---
title: "Panda Usb Vaccine and Ubuntu"
date: 2010-04-02
forum: Security
---

### Post by jsnjack on 2010-04-02
Currently i am running two OS: Windows XP SP3 and Ubuntu 9.10. In  Windows, Panda USB Vaccine vaccinated my usb flash pen(by replacing autorun.inf with specific attributes). But Ubuntu  remove vaccinating and malware could infect my Windows system. What can i do with it?

---

### Post by cariboo on 2010-04-02
Ubuntu doesn't use autorun.inf, so it wouldn't change the file.

---

### Post by jsnjack on 2010-04-02
But it happens! When i boot Windows XP and insert my pen-drive, Panda USB Vaccine (PUV)  window is appear (I configure PUV to vaccinate non-vaccinated pen-drive  automatically). Please, take a look at attached image panda.png. PUV has  created another one autorun-file: *autorun_.inf*.

---

### Post by CharlesA on 2010-04-02
Sounds like a problem with this Panda USB Vaccine program, not Ubuntu.

---

### Post by jsnjack on 2010-04-03
> **CharlesA said:**
> Sounds like a problem with this Panda USB Vaccine program, not Ubuntu.
I not think so. It seems that Ubuntu change some attributes of autorun.if (maybe it permission attributes?). Take a look at panda_2.png. Autorun.inf - its original Panda USB Vaccine (PUV) file, Autorun_.inf - after Ubuntu.

---

### Post by CharlesA on 2010-04-03
The only thing that has changed is that the archive bit has been set on Autorun_.inf.

That doesn't have anything to do with permissions.

Stupid question, but why do you even have an autorun.inf on a pen drive?

---

### Post by jsnjack on 2010-04-03
> **CharlesA said:**
> The only thing that has changed is that the archive bit has been set on Autorun_.inf.

That doesn't have anything to do with permissions.

Stupid question, but why do you even have an autorun.inf on a pen drive?
Info from Panda's blog:
> The free Panda USB Vaccine can be used on individual USB drives to disable its AUTORUN.INF file in order to prevent malware infections from spreading automatically. When applied on a USB drive, the vaccine permanently blocks an innocuous AUTORUN.INF file, preventing it from being read, created, deleted or modified. Once applied it effectivelly disables Windows from automatically executing any malicious file that might be stored in that particular USB drive. The drive can otherwise be used normally and files (even malware) copied to/from it, but they will be prevented from opening automatically. Panda USB Vaccine currently only works on FAT & FAT32 USB drives. Also keep in mind that USB drives that have been vaccinated cannot be reversed except with a format.For Windows OS its really necessary. It prevent infection of my machine over and over again...

---

### Post by CharlesA on 2010-04-03
That doesn't exactly explain *why* you need an autorun.inf on a pen drive.

Maybe I am doing something wrong, since none of the pen drives I have, even bootable ones, have an autorun.ini file.

It would be stupid (and unsafe) to have a program launch when the thumb drive is inserted, which by default doesn't happen unless you have one of those U3 drives.

Does this "virus" that you are so worried about, create an autorun.inf or just modify it?

---

### Post by DrMelon on 2010-04-03
Not to mention, why would you keep re-infecting your Windows machine (if you didn't have Panda) anyway? Surely one infection is enough to teach you not to download dodgy stuff?

---

### Post by jsnjack on 2010-04-03
> **DrMelon said:**
> Not to mention, why would you keep re-infecting your Windows machine (if you didn't have Panda) anyway? Surely one infection is enough to teach you not to download dodgy stuff?
:) I'm don't download dodgy stuff. Currently at my work our administrator installed to all computers NOD32, which can't detect some viruses. So, almost everyone PC at work is infected. My work data i keep at pen-drive. So, if i copy in/out my pen-drive some data, it become infected. That is why I need PUV - to disable automatically load virus to my machine (through modified autorun.inf ).

---

### Post by jsnjack on 2010-04-03
> **CharlesA said:**
> That doesn't exactly explain *why* you need an autorun.inf on a pen drive.

Maybe I am doing something wrong, since none of the pen drives I have, even bootable ones, have an autorun.ini file.

It would be stupid (and unsafe) to have a program launch when the thumb drive is inserted, which by default doesn't happen unless you have one of those U3 drives.

Does this "virus" that you are so worried about, create an autorun.inf or just modify it?
Usually, that virus **create** (**or modify**) autirun.inf. So, that is why i need PUV - to disable ability to **create** (**modify**) autorun.inf.

---

### Post by CharlesA on 2010-04-03
> **jsnjack said:**
> :) I'm don't download dodgy stuff. Currently at my work our administrator installed to all computers NOD32, which can't detect some viruses. So, almost everyone PC at work is infected. My work data i keep at pen-drive. So, if i copy in/out my pen-drive some data, it become infected. That is why I need PUV - to disable automatically load virus to my machine (through modified autorun.inf ).

That would be something to talk to the system admin about then.

Tbh you are being terribly paranoid. No virus scanner catches all viruses but it does catch a significant majority of them. You would be fine if you just ran a virus scan on the pen drive whenever you put it in a machine, not by using some BS "autorun.inf fix." A normal data pendrive does not have an autorun.inf, since it doesn't run anything on startup. If there **is** an autorun.inf and it is not a U3 pen drive, then you need to look into it.

If you assume that because an antivirus doesn't catch some viruses, it means that **all** the machines at work are infected, you are sorely mistaken. That sounds like propaganda used to sell crap.

Your best bet would be to talk to your system admin and bring your concerns to him/her. If all the machines on a network are infected, then the sys admin is doing a **** poor job.

> **jsnjack said:**
> Usually, that virus **create** (**or modify**) autirun.inf. So, that is why i need PUV - to disable ability to **create** (**modify**) autorun.inf.

See above.

---

### Post by jsnjack on 2010-04-03
> No virus scanner catches all viruses but it does catch a significant majority of them. You would be fine if you just ran a virus scan on the pen drive whenever you put it in a machine, not by using some BS "autorun.inf fix."
Yes, you are right. But incompletely. I'm note sure, that next few words sounds correctly in English, but I try: It's easier to prevent threat, than fight with consequences. That's why I using PUV. It's really helpful.  

> ...it means that **all** the machines at work are infected, you are sorely mistaken.
Why? Anyone can use other kind of software, not only NOD32.. AVG, for example, catch this virus. If virus spread through pen-drive, why you are so sure?

Last week i copy some materials from university PC, and after that, pen-drive was infected... It is easier to secure my own PC, than ALL PC around me...

> If all the machines on a network are infected, then the sys admin is doing a **** poor job.
Yes, you are right. Completely right! But this doesn't solve my problem :(

---

### Post by CharlesA on 2010-04-03
I still don't understand ***why*** you are using an autorun.inf file on a pen drive. There is no need for one if all you have on it is data.

If you are that concerned about this "virus" then tell your network admin and show proof that NOD32 isn't detecting it.

---

### Post by Akita on 2010-04-03
1) Autorun sould be disabled for ALL removable media on a Windows system.
2) Autorun can be disabled via local or domain group policies.
3) Being convinced that you need to run some unknown application full-time that messes with autorun in order to stop something from happening that can be done easily with tools provided by the operating system (been there sine Windows 2000) sounds like social engineering at its finest to me. I would venture a guess that the reason you need Panda to protect your computer is because of Panda.
4) I also suggest staying away from web sites that "autoscan" your hard drive for viruses or the highly dubious places that claim to make your PC faster simply by letting them install and run some software via the web.

---

### Post by jsnjack on 2010-04-04
> **CharlesA said:**
> I still don't understand ***why*** you are using an autorun.inf file on a pen drive. There is no need for one if all you have on it is data.
Again and again... I use Panda's autorun.inf because it can't be modified in Windows machine. So virus can't add some strings in autorun.inf... And as final, virus can't autorun when i plug pen drive.

**Akita**, I think I understood what you mean. You suggest to me manually(because panda do it automatically - and for me it simple) remove autorun ability? I will try this :).

> I would venture a guess that the reason you need Panda to protect your  computer is because of Panda.
No, only because I like it. And Ubuntu I use because I like it too.

---

### Post by cascade9 on 2010-04-04
Hmm...one autorun.inf is the 10th of *I cant read russian* 2009, the other is the the 3rd of *I still cant read russian* 2010. 

I'm guessing the 2nd date is april? Its possible that panda has just been updated, and created a new autorun.inf file, and then archived the old version. 


> **Akita said:**
> 1) Autorun sould be disabled for ALL removable media on a Windows system.
2) Autorun can be disabled via local or domain group policies.


Theres your solution- just disable autorun for removable media on your windows system. (I sort of agree on points 3+4 as well). 

Its probably a good idea to scan any removable media with an antivirus anyway, even if you have panda (and trust it)

---

### Post by jsnjack on 2010-04-04
> **cascade9 said:**
> Its probably a good idea to scan any removable media with an antivirus anyway, even if you have panda (and trust it)
Yes. And I do it. 

> Its possible that panda has just been updated, and created a new  autorun.inf file, and then archived the old version. 
Unfortunately, no.

&#1072;&#1087;&#1088;&#1077;&#1083;&#1103; = April
&#1089;&#1077;&#1085;&#1090;&#1103;&#1073;&#1088;&#1103; = September

---

### Post by cprofitt on 2010-04-04
-- background --
The process being used by Panda is called 'cratering'.

/* [cratering]("http://www.liebsoft.com/block_unauthorized_applications/") */
Make a copy of a file that malware creates, change the permissions to deny rights to the file from every account but a special account. This makes it more difficult for malware to create the specified file.

In this cause the autorun.inf would be blocked. The archive and hidden attributes are unimportant for this process.

You should be able to do this yourself and not depend on Panda.

---

### Post by jsnjack on 2010-04-04
**cprofitt**, thank you for interesting link.

More info about topic: If using NTFS pen-drive, vaccination is not removed. So, it removes only on FAT32 pen-drives.

---

### Post by marcini on 2010-12-01
Hi,

I would like to refresh the topic, because I noticed similar problem on two vaccinated pendrives and it's very interesting behavior. After mounting vaccinated pendrive in Ubuntu 10.10 vacination is removed. In Windows Panda creates unremovable Autorun.inf, but after mounting pendrive in Ubuntu, file created by Panda still exists on pendrive, but it can be easily deleted on any system with normal delete command.

For me it looks like Ubuntu does some kind of filesystem scan after mounting the pen and it fixes some errors which Panda creates in filesystem to prevent malware from deleting autorun.inf. Is that possible? Does the Ubuntu fix pendrive filesystem without any message for the user?

---

### Post by cariboo on 2010-12-01
The reason you're seeing that, is that Windows permissions don't work in Linux, just as Linux permissions don't work in Windows. Permissions on the two systems are incompatible. The files only have the same permissions as the mount-point.

---

### Post by jago25_98 on 2010-12-01
I haven't noticed this behaviour but I will look out for it.

---

### Post by claracc on 2010-12-02
I also have a hidden an not movable folder named autorun.inf in my usb pen drive to avoid malicious software in windows to infect the pen drive with an exact name component (autorun.inf), and in this way, to prevent infection and propagation of virus through pen drive ( [http://rinconlinfocitario.wordpress.com/2009/03/15/previniendo-infecciones-en-dispositivos-usb/](http://rinconlinfocitario.wordpress.com/2009/03/15/previniendo-infecciones-en-dispositivos-usb/), the link is in spanish).

When I plug the usb in my ubuntu lucid lynx system, it doesn't change anything in the folder, I can see the autorun.inf in the pen drive. Returning to windows the folder is unaltered.

I think the problem is the kind of autorun.inf panda vaccine creates.

---

### Post by cariboo on 2010-12-02
> When I plug the usb in my ubuntu lucid lynx system, it doesn't change anything in the folder, I can see the autorun.inf in the pen drive. Returning to windows the folder is unaltered.

check the ownership and permissions in both Windows and Ubuntu, you'll see a difference.

---

### Post by marcini on 2010-12-02
> **cariboo907 said:**
> The reason you're seeing that, is that Windows permissions don't work in Linux, just as Linux permissions don't work in Windows. 

Yes, I know that. But after mounting pendrive in Linux, I can easily delete autorun.inf on Windows too, so I think permissions aren't the cause of that. Linux changes something in the filesystem and it does it automatically, without even noticing the user. Even when pendrive on Linux is used only for reading and no data is written to it.

> I think the problem is the kind of autorun.inf panda vaccine creates.I don't know exactly, what Panda does with this file to make it unremovable. I suppose it uses some kind of hack to cause filesystem error if someone tries to delete the file. And I suppose Linux fixes this automatically after mounting.

---

### Post by claracc on 2010-12-03
I have check my usb pen drive autorun.inf folder in lucid and these are the results:
It has 4 files, three of them: changelog.txt, readme.txt, and desktop.ini are locked, I am the owner and I can create and delete files in this folder, group and others cannot access the folder. In running, it is selected allowing to run the file as a program.

The checking in windows vista is:

Propierties of autorun.inf folder: only read, the owner of the folder is all. Inside the folder I only can see two files: changelog.txt and readme.txt, the attributes for both of them are RA, ie. only read and storing

So really permissions and owners os files are different in one system and in other.

Anycase, I understand the way of preventing the automatic infection by malware of computer through pen drive is assured in windows system by the autorun.inf folder..., or am I wrong?

---

### Post by marcini on 2010-12-03
> **claracc said:**
> Anycase, I understand the way of preventing the automatic infection by malware of computer through pen drive is assured in windows system by the autorun.inf folder..., or am I wrong?

I don`t think ordinary folder can prevent malware from creating it`s own autorun.inf. Do you have sufficient privileges to delete this folder? If so, then malware running on your account also can do it and create new autorun. I think better solution is file, which you can`t normally delete using operating system API. But of course nothing is 100% secure.

---

### Post by claracc on 2010-12-03
> I don`t think ordinary folder can prevent malware from creating it`s own autorun.inf. Do you have sufficient privileges to delete this folder? If so, then malware running on your account also can do it and create new autorun

I am not sure about this since the author of the autorun.inf folder to inmunize usb pen drive says this folder is write protected and it has files inside in order to prevent deletion or edition by malicious folder. I don't think autorun.inf is an ordinary folder despite of owners are all in win vista.

He says this method to immunize pen drives is safe if the infectious files are not oppened manually.

Anycase, I tried to delete the folder and I could do it without any problem. Now, I don't know what to think.

---

### Post by CharlesA on 2010-12-03
Can I point out that you can get around this problem by disabling Autorun?

Also: In Vista and 7, you are prompted if you want to run someprogram.exe if there is an autorun.inf

IMHO: Autorun should be disabled in a corporate environment.

---

### Post by juancarlospaco on 2010-12-03
Hold down SHIFT when plugin it, disable autorun.

---

### Post by claracc on 2010-12-03
Thankyou. 

I will remember to disable the autorun (shift key) when I plug the pen drive in any computer.

---

