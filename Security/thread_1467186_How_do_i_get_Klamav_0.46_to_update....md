---
title: "How do i get Klamav 0.46 to update...?"
date: 2010-04-30
forum: Security
---

### Post by liviococcia on 2010-04-30
Hello Members
After giving some thought as to whether i should install any antivirus on Ubuntu 9.10, or not, i decided to choose KlamAV 0.46, this is due still having to use files from email attachments and USB storage devices.

The first problem i encountered was trying to get it to scan all the files on the computer, the problem was i kept getting notices from Klamav saying 'Access Denied' while it scanned the system, i found out this was a permission problem, i used the 'Run Application' box and typed 'gksu klamav' to open the application in 'Root' account mode.

What i'm now finding is the 'Update' button under the update tab of KlamAv seems permanently grayed out, it seems i can only choose the check box to run an update the number of times in a day which i have left unchecked.

How do i get the 'Update' button to allow me to download updates for KlamAV when i wish.

Any help and guidance would very grateful.

Kind regards
Livio

---

### Post by mikewhatever on 2010-04-30
> **liviococcia said:**
> Hello Members
After giving some thought as to whether i should install any antivirus on Ubuntu 9.10, or not, i decided to choose KlamAV 0.46, this is due still having to use files from email attachments and USB storage devices.

Don't quite see the logic in that decision, after all, whatever malware you might find in those attachments will most likely be for Windows.

> The first problem i encountered was trying to get it to scan all the files on the computer, the problem was i kept getting notices from Klamav saying 'Access Denied' while it scanned the system, i found out this was a permission problem, i used the 'Run Application' box and typed 'gksu klamav' to open the application in 'Root' account mode.

Even less logic here. Since when are files from usb devices and email attachments are stared under root? On Windows, scanning all the files would make sense, but not on Ubuntu.

> What i'm now finding is the 'Update' button under the update tab of KlamAv seems permanently grayed out, it seems i can only choose the check box to run an update the number of times in a day which i have left unchecked.

How do i get the 'Update' button to allow me to download updates for KlamAV when i wish.

Any help and guidance would very grateful.

Kind regards
Livio

Dear Livio, you are not in Windows, so it shouldn't feel like 'Western Beirut in the 80s' any more, relax, explore, enjoy. :P

---

### Post by liviococcia on 2010-05-01
Thanks mikewhatever for the help, i'm thinking that the protection was more for friends who have a windows OS that i might share any files with, and so could pass viruses onto them which may have passed through me, even though i don't risk suffering any ill effects myself.

Ask you can tell i'm a complete newbie to Ubuntu, and have just started out on it's learning curve.

As with regards to getting KlamAV to update, i found if i put a check in the 'Update database automatically' and chose 1, and if i then was to cancel any updating it might be in the process of doing only then would the 'Update' button be ready to be used again.

What i'm now finding this morning when i start the program up as a 'root' user is that i keep getting the message below..

WARNING: Can't download daily.cvd from database.clamav.net

..i've tried a number of times with no luck so far, can anyone offer any advice to this, my internet connection is ok, so again, members help would be great.

regards

---

### Post by liviococcia on 2010-05-03
Just to let members know...

I gave up with KlamAV, as i initially wanted to use Avast Home Edition, i'd heard it was actually highly regarded for it's simplicity.

I did install Avast HE at first, as a virtual os install of Ubuntu 9.10, on a windows xp computer using VMware player, and thats where Avast first showed the error box "An error occured in avast! engine: Invalid argument", when this happened i lost faith with it there and then, and thats when i decided to give KlamaAV a go, and installed in onto my Ubuntu laptop computer.

Still having problems with KlamaAV updating, i decided to remove it and give Avast a go on my laptop, thinking maybe it won't have this 'Invalid argument' problem, but after Avast's first definitions update it did.

That's when i thought i do more web searching for a permanent solution, i had tried one solution which i managed to find on the Avast Linux forum, and it did work, trouble was i found i had to invoked the instructions every time the computer was restarted.

I did finally find some info regarding another problem someone else was having, but this was not to do with any Avast product, and manage to use this bit of info to complete the fix for me.

If anyone is a newbie to Ubuntu, and experiencing the same problem, with the same set of circumstances, maybe it will work for you, link below...

[http://ubuntuforums.org/showthread.php?t=1469741&highlight=Avast+invalid+argument](http://ubuntuforums.org/showthread.php?t=1469741&highlight=Avast+invalid+argument)

regards

---

### Post by cariboo on 2010-05-03
I'm not sure about updating Klamav, but if you are just updating the virus definitions, open a terminal and type:

```
sudo freshclam
```

the above command will create a cron job that looks for signature updates once an hour.

---

### Post by joeman225 on 2010-05-12
I've had the exact same problems with klamav and avast.   

I've been reading through the forum and am finding more and more that there's alot of dismissive-ness and pontification in people's replies to certain questions, and it's not helpful (Such as with mikewhatever's answer to your question).  

Obviously, there is a growing need for functioning antivirus programs for Ubuntu and similar OS's, either to protect the user, or to prevent the spread to other types of operating systems.   

I say: Don't post a subjective opinion when all someone needs is an objective answer.  (I just thought I had to say this about the much of the unhelpful attitude in this forum.)

---

### Post by cariboo on 2010-05-13
The op did get advice that is helpful. The big problem is that most anti-virus scanning programs are pretty close to useless. Viruses as we know them hardly exist any more, it is other forms of malware that are the big problem, from personal experience they don't seem to be doing a very good job of stopping it.

When someone brings a computer to my shop, they are mostly pretty useless, because of malware, most of them have up-to-date anti-virus scanners, but in many cases the malware disables them.

My questions is what's the use of having an av-scanner if it doesn't work?

---

### Post by faargenwelsh on 2010-05-16
> **mikewhatever said:**
> Don't quite see the logic in that decision, after all, whatever malware you might find in those attachments will most likely be for Windows.
(...)
Even less logic here. Since when are files from usb devices and email attachments are stared under root? On Windows, scanning all the files would make sense, but not on Ubuntu.
(...)
Dear Livio, you are not in Windows, so it shouldn't feel like 'Western Beirut in the 80s' any more, relax, explore, enjoy. :P

dear mikewhatever, you are by far the most friendly, helpful and open-minded ubuntu user i've ever seen. =D>

> **cariboo907 said:**
> 
When someone brings a computer to my shop, they are mostly pretty  useless, because of malware, most of them have up-to-date anti-virus  scanners, but in many cases the malware disables them.

My questions is what's the use of having an av-scanner if it doesn't  work?

that's precisely the interest of using ubuntu to remove windows viruses & crapware. when you mount a windows partition to analyse it with an ubuntu-installed AV-program, the malware can not disable anything because it is not executed, in the first place.

---

### Post by Joe of loath on 2010-05-16
Regarding why ClamAV didn't update, all ClamAV pre 0.95 has reached end of life, and is no longer being supported. You'll need to upgrade to a newer version of ClamAV.

---

### Post by cariboo on 2010-05-16
There are a number of Live CDs from AV makers, I recommend them.

[AVG]("http://www.avg.com/us-en/avg-rescue-cd")

[Kaspersky]("http://devbuilds.kaspersky-labs.com/devbuilds/RescueDisk/")

[BitDefender]("http://download.bitdefender.com/rescue_cd/")

[Avira]("http://dl.antivir.de/down/vdf/rescuecd/rescuecd.iso")

[F-Secure]("http://www.f-secure.com/en_EMEA/security/tools/rescue-cd/")

---

### Post by DJonsson2008 on 2010-11-21
While I had problems with the KDE KlamTK front end,
GTK ClamTK frontend worked much better on 10.10. I
believe they both wrap the same engine.

After updating the definitions current to the day,
I scanned the wine drive that houses Eudora. Clam
found 2 phishing hookings and 1 exploit1.iFrame.gen.

The software did not provide me an option to clean 
the file, but rather to delete or quarantine it.
Being that Eudora places all messages in one long
file neither were a good option. 

In any case it did seem effective in altering me
to a virus.

I don't see any reason for the false security many here
mention regarding not needing virus scan or malware 
vigilance of some sort on Linux. Its just a matter of
probability and time, as well there are many
users on shared environments who need some solution to this.

---

### Post by cariboo on 2010-11-21
There is malware for Linux that has been around for years. In order for it to be installed it has to rely on social engineering. Due to the Linux permission system, it is much harder for malware to take hold and propagate.

The fallacy that once Linux gains in popularity, there will be more malware that affects us, is just plain wrong. Linux is running on so many devices, that I would venture to say that it is even more widely used than Windows. Linux is popular on embedded devices, everything from cell phones to set-top cable boxes. If sheer numbers were a reason for more malware, then we should have been overwhelmed years ago.

---

