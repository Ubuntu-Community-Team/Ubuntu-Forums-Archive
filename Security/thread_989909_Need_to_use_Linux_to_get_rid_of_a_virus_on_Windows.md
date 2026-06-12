---
title: "Need to use Linux to get rid of a virus on Windows."
date: 2008-11-22
forum: Security
---

### Post by Crazychicken on 2008-11-22
Yes, it finally happened, as I knew it would. Weirdly enough, while patching Spore(of all things!), Mc afee, firewall and all got turned off, and whack, I get a virus. I found my computer restarting, it did everything all right, there was a little notice saying "your computer has been infected with spyware, windows will get on the net and download an antivirus, click here" I ignored that, attempted to open Mc afee, it died again. So now I'm on my nice Linux partition, and I guess I'll have to
-mount my windows partition on linux
-run a scan on it.

And I don't quite know how... need step-to-step help ^.^ but you guys are so good with that!

---

### Post by duanedesign on 2008-11-22
does this thread help.

[http://ubuntuforums.org/archive/index.php/t-1886.html](http://ubuntuforums.org/archive/index.php/t-1886.html)

---

### Post by Crazychicken on 2008-11-22
you mean I should use this?


> su root
cd /media
mkdir windows
nano /etc/fstab
type or paste the line: /dev/hda1 /media/windows ntfs ro,dmask=0222,fmask=0333 0 0
mount /dev/hda1
then cd /media/windows
ls (all your windows files+folders will be listed)

It was hda1 for me, since the linux partition was hda2 (as listed in /etc/fstab) but it can be hdc, hdc1, hda, etc so you'll have to check what the other partitions are labeled as.

---

### Post by prshah on 2008-11-22
> **Crazychicken said:**
> 
 whack, I get a virus. 
and I guess I'll have to
-mount my windows partition on linux
-run a scan on it.


See: [Need Adware/Spyware app for Ubuntu]("http://ubuntuforums.org/showthread.php?t=981084")

You do not need to do anything to mount your Windows partition; if you just select the partition to scan, the anti-virus will take care of the rest of it.

If you still want to manually mount your partition, use gnome-mount, eg, if your partition is /dev/sda1, use```
sudo gnome-mount -d /dev/sda1
```

---

### Post by Kinstonian on 2008-11-22
Do **not** use anti-virus to delete malware yet, since you will be deleting evidence.  Recovering from an incident is more than an AV scan.  Instead, disconnect your computer from the network for now.

Then use [Process Explorer](http://technet.microsoft.com/en-us/sysinternals/bb896653.aspx) to look for suspicious processes.  Processes that aren't signed, or say they are from Microsoft but not digitally signed, processes that are purple meaning they are encrypted/packed, processes that have random names, or you don't recognize, etc. Then Google for them and see if you can find out what they are.

Once you find a suspicious process look at the modified/created timestamps and search your hard drive for all other files that were modified/created at that time, again looking for suspicious files.

Submit the suspicious processes to [VirusTotal](http://www.virustotal.com/) in order to use over 30 different AV vendors to find out what it is, and it's capabilities.

Search your Event Logs for all log entries that happened at the time of the incident to find out what the malware did.  Did it create a user account, start a service, disable your firewall, etc?

Use [Log Parser](http://www.microsoft.com/downloads/details.aspx?FamilyID=890cd06b-abf8-4c25-91b2-f8d975cf8c07&displaylang=en) to display all registry activity that happened during the incident.  You can create a file called regtime.sql that contains the below query.

```

SELECT
	KeyName,
	Value,
	LastWriteTime
FROM HKLM\
WHERE LastWriteTime BETWEEN TIMESTAMP('2008-08-27 00:00:00', 'yyyy-MM-dd hh:mm:ss') AND TIMESTAMP('2008-08-28 00:00:00', 

'yyyy-MM-dd hh:mm:ss')
ORDER BY LastWriteTime DESC
```

Just change the date and time to match your incident.  Then run Log Parser using the command prompt by typing:

```
logparser.exe file:regtime.sql -i:REG -rtp:-1
```

Again you can look for changes to your system's configuration, such as your firewall being disabled, services being added, programs being set to auto run, etc.  You also have to replace the HKLM in the SQL query with HKCU, HKCC, HKU, and HKCR to scan all of appropriate registry hives for changes during the incident.

In fact, I'd also use [AutoRuns](http://technet.microsoft.com/en-us/sysinternals/bb963902.aspx) in order to find code set to run when Windows loads.

Also look for suspicious network activity using [TCPView](http://technet.microsoft.com/en-us/sysinternals/bb897437.aspx).

Then you can use anti-virus/anti-spyware software, such as HiJackThis.

---

### Post by prshah on 2008-11-22
> **Kinstonian said:**
> 
Recovering from an incident is more than an AV scan.  

disconnect your computer from the network for now.

use [Process Explorer](http://technet.microsoft.com/en-us/sysinternals/bb896653.aspx) to look for suspicious processes.  

Then Google for them and see if you can find out what they are.

look at the modified/created timestamps 

search your hard drive for all other files that were modified/created at that time, 

Submit the suspicious processes to [VirusTotal](http://www.virustotal.com/)

Search your Event Logs for all log entries that happened at the time of the incident 

Use [Log Parser](http://www.microsoft.com/downloads/details.aspx?FamilyID=890cd06b-abf8-4c25-91b2-f8d975cf8c07&displaylang=en) to display all registry activity that happened during the incident.  


you can look for changes to your system's configuration,

You also have to replace the HKLM in the SQL query with HKCU, HKCC, HKU, and HKCR to scan all of appropriate registry hives for changes during the incident.

also use [AutoRuns](http://technet.microsoft.com/en-us/sysinternals/bb963902.aspx) in order to find code set to run when Windows loads.

Also look for suspicious network activity using [TCPView](http://technet.microsoft.com/en-us/sysinternals/bb897437.aspx).

Then you can use anti-virus/anti-spyware software, such as HiJackThis.

...or just remain in Ubuntu :lolflag:

Whew, that's a large and comprehensive list!

---

### Post by Kinstonian on 2008-11-22
Yet that just scratches the surface, there are entire books written on incident response.  Hopefully he got what he asked for.  :)

---

### Post by Crazychicken on 2008-11-22
I got rid of the virus(es) in windows' error mode, but it still reboots in full mode after a a minute or so. I suspect something in the system was messed up during the installation. I'll see if I can back up my files from Ubuntu, and reinstall XP. 

(I would stay- but I can't play Spore from Linux ^^). 

Ty for your help

---

### Post by prshah on 2008-11-22
> **Crazychicken said:**
> I got rid of the virus(es) in windows' error mode, but it still reboots in full mode after a a minute or so. 

Bad luck. I've been there; I had a horrible infection of VirtuMonde that just refused to go away inspite of NAV2006, Spybot S&D and some others. That's what [started my Ubuntu journey in earnest]("http://ubuntuforums.org/showthread.php?t=593446").

I'd still suggest you stay in Ubuntu, and virtualize your Windows; you can just save a state and restore to it everytime something goes wrong. However, I don't know if it will be workable to play spore, or whatever. EDIT: You may want to see [Spore on Linux Howto]("http://linuxoutlaws.com/spore"), Note the disclaimers; they apply to this piece of advice as well.

Good luck, looks like you need it!

---

