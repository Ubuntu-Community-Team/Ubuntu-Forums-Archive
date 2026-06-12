---
title: "What should my setup look like for company NAS?"
date: 2017-08-08
forum: Server Platforms
---

### Post by webmiester on 2017-08-08
Hi everyone,

I am tryiing to setup a NAS for our company.  I checked out some websites about setting up NFS and SAMBA (I installed SAMBA on the server already).  However this is what I would like to do:

1) I want to have all our windows computers linked to the NAS so that all their files are backup up at the NAS
2) Each computer belongs to a particular department.  I need to keep the files of each particular department confidential from other departments.  For instance:

a) The CEO using the computer in his office can put all his files in the NAS
b) The sales clerk using his computer from his room can put all his files into the NAS

however, the sales clerk should not be able to view the files of the CEO.

When I checked out some sites regarding this and I read about "sharing", but it didnt seem to answer my question on how to control this sharing to particular computers only.  I think, most of the sites I've seen discusses using the NAS for a home network where this kind of confidentiality between users isn't as delicate.  

Aside from your opinions, I would also appreciate links and/or even just suggestions on "key words" for me to search for to find a solution to this.

Thank you so much.

Charles
Thanks so much.

---

### Post by mastablasta on 2017-08-09
if this is only a backup server, why do you need samba?

install OpenSSH and use sFTP to transfer files for each user to the server. files can be encrypted and you can also separate what user can see/access using permissions.: 
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

See also (in terminal)
```
man chmod
man chown
man chgrp

```
have you looked at things like zentyal or openmediavault?

i server admin will still have access to all files unless they are encrypted (e.g. before upload).

---

### Post by SeijiSensei on 2017-08-09
The usual solution for this problem is to put all the files on a central server and control access by passwords and user groups.  Letting people save to their individual computers is a recipe for chaos and data loss as organizations grow.  Plus you're left with one server to back up rather than trying to manage backups of multiple users' machines.  Use RAID for short-term crash protection along with nightly backups.

You can use Samba for this task.

---

### Post by webmiester on 2017-08-13
Thank You Seiji, you have been very helpful even with my other thread.

Yes, to clarify what I would like to do.  I would like everyone to save to a common NAS from their windows based computers.  We wont be saving to their individual computers, but rather, we will be saving FROM their individual computerws.  The NAS is already on RAID, so it helps make the data more reliable.  Your inputs on controlling access by passwords and user groups is exactly what I would like to do.

From what I read from your reply, please correct me if these steps are correct:

1) Ill setup different users in the OS (not in Samba)
2) Ill make passwords for each user
3) Ill assign different home folders for each user.
4) Ill connect the NAS to the network.

What I am expecting is that the NAS should appear in everyone's computers as another drive in the network.  When they clock it, they will be asked a username and password.  If they enter their user name and password, they can now access the contents of their portion of the NAS.  Is this correct?  Thanks so much.

Thank you mastablasta,

Openmediavault looks promising.  I dont want to pay for zentyal.  What is the advantage of using openmediavault as against using SAMBA with individual user passwords?  Thanks

BTW,

As root user, can I change the passwords of other users without their consent?  I mean, I would hate it if a disgruntled employee decided to lock up his data by changing the password then leave the company.  We won't have any access to any of the company files in his/her part of the system. Just a thought that came into my mind "re:disgruntled employees", is there something I can put that can prevent them from wiping out their data in case of this event?  Thanks.

---

### Post by SeijiSensei on 2017-08-13
The root user can change anyone's password, both at the OS level and within Samba.

Yes, the model you present is generally what's needed.  Set up Unix and Samba accounts for the users.  If there are users who need common access to a set of files, you'll probably want to create a few user groups as well.  By default Samba exports each person's home directory after requiring a login. You can then use "map a network drive" to assign the share a drive letter, like "H:\" for the person's remote home directory.  I believe there are ways in Samba to make those assignments automatic using what's called "roving profiles."

---

### Post by webmiester on 2017-08-19
Thank you Seiji,

In this case, If I assign different home directories per person (or department), can they all have the same drive letter (like H:\), or will each person have a different drive letter (person A has H:\, and person B has I:\).  If in case its the second option (each person will have an individual drive letter), what happens when I reach "Z:\" and still need some more drives?

---

### Post by SeijiSensei on 2017-08-19
The drive letter assignments are handled by the Windows clients.  Everyone can have a drive H:\.  In some Samba configurations, you can force this assignment from the server: [https://wiki.samba.org/index.php/User_Home_Folders](https://wiki.samba.org/index.php/User_Home_Folders)

I'm a bit surprised you're still asking such elementary questions.  Have you not yet set up at least a testbed?

---

### Post by webmiester on 2017-08-27
Hi SeijiSensie,

No I havent actually setup a testbed yet.  I am not actually an "It person".  I am a doctor trying to setup our hospital system.  I havent been able to put up a testbed yet since I have gotten really bust still trying to setup the workstations and networking stuff.  I enrolled in a linux administration course to understand more things but wasnt able to finish it because I had emergencies at the hospital during the last few days of the course.  I recently erased my NAS setup and will reinstall it once I get more of the hospital system up and running.

I really want to thank you for your inputs.

I would like to ask about ransomware and users and their home folders (Its still related to this thread).  Since a windows computer can only see his portion of the NAS (because it is the only part he has access to), if the windows computer gets attacked by a ransomware (or other dangerous virus), will it only affect the portion of the NAS that the said computer have access to, or can it diasable the entire drive?  Thanks

---

### Post by SeijiSensei on 2017-08-27
More likely the ransomware will spread from one Windows machine to another if people connect to the same Samba share where the ransomware was installed.  But, really, this is a human relations problem more than a technical one.  People should be trained not to click on links in messages unless they are sure they came from a trusted sender.  If you're running your own email system, then you might want to look into something like [MailScanner](http://mailscanner.info/) to filter out malware and spam.  If you've outsourced your email, do you trust your provider to clean your mail effectively?

To be honest, I think you're overextending yourself if you are trying to fulfill your responsibilities as a physician and build a secure network in your "spare time."  At some point, you should consider hiring a Linux professional to help with this.

---

### Post by webmiester on 2017-10-17
Hi Everyone,

After considering the suggestion of using FTP for the backup server, my IT technician tells me that it can be dangerous because the ftp server is frequently the first thing that hackers look for and thus make the data vulnerable to hacker attacks.  My concern is that by using Samba (instead of FTP), My linux-based NAS can be vulnerable to viruses specially ransonmware...  My IT guy suggested that I run my NAS on windows server then run an antivirus such as kaspersky on it to protect it from viruses.  I still want Linux, so I figured: how about if I run Ubuntu on it, and run an ubuntu-based anti-virus on the system.  What do you guys think of this idea?  I am thinking of using clamAV or Sophos, or perhaps something else you guys can recommend.  What do you guys think of this suggestion?  Will it (ubuntu with samba and ClamAV or Sophos) hold up against running the NAS with windows server with antivirus?  How good are these linux anti-viruses against their Windows counterparts?  As an added bonus, can the ubuntu NAS see the hard disks of the windows computers connecting to it?  If yes, can I use the anti-virus on the NAS to scan for viruses on the windows systems? Thanks so much.

webmiester

> **SeijiSensei said:**
> To be honest, I think you're overextending yourself if you are trying to fulfill your responsibilities as a physician and build a secure network in your "spare time."  At some point, you should consider hiring a Linux professional to help with this.

Yes, I think so too.  Think of it as somewhat like some sort of a hobby :)

---

### Post by slickymaster on 2017-10-18
Thread moved to **Server Platforms** for a better fit

---

### Post by mastablasta on 2017-10-18
> **webmiester said:**
> Hi Everyone,

After considering the suggestion of using FTP for the backup server, my IT technician tells me that it can be dangerous because the ftp server is frequently the first thing that hackers look for and thus make the data vulnerable to hacker attacks.  My concern is that by using Samba (instead of FTP), My linux-based NAS can be vulnerable to viruses specially ransonmware... 

FTP yes it's vulnerable, sFTP no. you would use keys and can block access like that. keys are very very hard to decrypt.
if you have internal network only, then i am not sure what hackers could do with that sFTP. if you are opening it to internet and would like access to your NAS from the other side of the world, then the secure thing is to setup a VPN connection.

> 
 My IT guy suggested that I run my NAS on windows server then run an antivirus such as kaspersky on it to protect it from viruses.  I still want Linux, so I figured: how about if I run Ubuntu on it, and run an ubuntu-based anti-virus on the system.  What do you guys think of this idea?  I am thinking of using clamAV or Sophos, or perhaps something else you guys can recommend.  What do you guys think of this suggestion?  Will it (ubuntu with samba and ClamAV or Sophos) hold up against running the NAS with windows server with antivirus? How good are these linux anti-viruses against their Windows counterparts?

ClamAV is really not that good. other, commercial products, will do the same as they do on windows.

> 
 As an added bonus, can the ubuntu NAS see the hard disks of the windows computers connecting to it?  If yes, can I use the anti-virus on the NAS to scan for viruses on the windows systems? Thanks so much.

it can see the disks, i would use it to scan the PCs. although this is probably possible it doesn't make sense. better way would be to install scanners on windows PC and then enforce the scan policy. althought many scanners now scan continuously in the background or on access on the PC, so you won't even notice the scan is made. 

since you are in the windows world perhaps a good idea would be to explore office 365 options. you get many tools, including cloud.

---

### Post by LHammonds on 2017-10-18
Greetings.  I work for physicians like yourself.  I appreciate what you do for your community.

Are all of your Windows PCs in individual workgroups?  No central Active Directory server?

If using Windows clients and you do not have a professionally-trained IT support staff, it would be best to use a Windows server for authentication and managing the PCs (policies) by joining them to the local domain.

However, if you just want a Linux-only solution for authentication, you might want to setup an OpenLDAP server so you can manage users and groups in one location and have the Windows PCs join that domain.

But as you have said, Windows PCs tend to get nasty viruses which can affect anything they have access to...including the files on a Linux OS.  Linux may not get infected by the virus but it can help spread it if other machines connect to the infected files...unless you have some sort of anti-virus on your PCs and your server(s).

To help guard against data encrypting/corrupting malware, the main thing you can do is to create multiple, versioned backups.  You never want to just have 1 backup (such as syncing 2 locations) because if damage is done in one location, it can be replicated to the other.  This is why it is important to have multiple backups over time.  If you get infected on Monday but do not notice the damage until Friday, any backups done during the week are useless and you would need to have a good backup from the weekend or earlier.

It's also important to have backups at an offsite location in case of natural disaster or malware that specifically targets backups.

Regarding your file share, I would recommend having just one single share.   Then control access to the various department folders via permissions based on groups.  When managing user accounts, do so via group membership.  That way you configure permissions on shares/files and only specify group permissions.  After the initial design of the file system and permissions, you should never need to man-handle permissions again and just manage what groups people belong to in order to grant them necessary access.

Example:

S:\Dept\Admin\
 - Set access for an admin group here
S:\Dept\HR\
 - Set access for an HR group here
S:\Dept\Marketing\
 - Set access for a marketing group here
S:\Users\Jon.Doe\
 - Set access for this specific user as their "private" location and  re-direct their "My Documents" and their applications default save  location here.
S:\Users\Jane.Doe\
 - Set access for this specific user as their "private" location and  re-direct their "My Documents" and their applications default save  location here.
S:\Users\Mary.Jane\
 - Set access for this specific user as their "private" location and  re-direct their "My Documents" and their applications default save  location here.

LHammonds

---

### Post by vasa1 on 2017-10-18
> **webmiester said:**
> ...  My IT guy suggested that I run my NAS on windows server then run an antivirus such as kaspersky on it to protect it from viruses.  ...
Very minor point but isn't Kaspersky [in the doghouse]("https://arstechnica.com/tech-policy/2017/09/kaspersky-software-banned-from-us-government-agencies/")?

---

### Post by QIII on 2017-10-18
Or, with less potential for this going off on a political tangent:  There are those who would question Kaspersky's integrity, independence and intentions.

---

### Post by SeijiSensei on 2017-10-18
I've used ClamAV for years to scan inbound mail with [MailScanner]("http://www.mailscanner.info/").  At one client where I maintain a Squid web proxy, we scan all objects downloaded from the web via [SquidClamAV]("http://squidclamav.darold.net/").  In situations like this I prefer the daemonized version, clamd.  That approach has much better performance since all the data is loaded just once at boot.  

Of course, it's also important to block all incoming executables, scripts, and lately, MS Office documents with embedded macros.  Don't make the AV scanner do more work than it needs to.

I've encountered the occasional false positive from ClamAV, especially with it comes to "[Potentially Unwanted Applications](https://www.clamav.net/documents/potentially-unwanted-applications-pua)."

---

### Post by mastablasta on 2017-10-20
> **QIII said:**
> Or, with less potential for this going off on a political tangent:  There are those who would question Kaspersky's integrity, independence and intentions.

if we start questioning in one, we could question in them all. and let's not even start with the data collection on the OS level. bottom line, unless someone independent can confirm maliciousness of the tool,  it is only an alternative fact and not worth being bothered by.

on the other hand the fact is Kaspersky, BitDefender, Norton and maybe McAfee have consistent good (best?) detection rates. Others fluctuate. in certain periods they are ok and in certain ones they are not that good.

if we use consistency (as in constant good performance over time), best free options are probably Avast and Avira.

I know Avira and Bitdefender have linux versions, because their rescue disks actually run linux.  I think Kapsersky has it as well. i haven't explored these options (linux+AV) much. 

ClamAV will detect plenty but still much less than the commercial options. on the other hand it is better than nothing and it should at least pickup the big & common ones.


also [COLOR=#000000]**LHammonds** is 100% right - good backups trump all Antivirus + they can prove to be a cheaper option in the long run. of course Antivirus + backup combo will protect not only your organisation, but others that are in contact with you.

EDIT: AV review with links to AV performance testing websites: [/COLOR]https://www.pcmag.com/article2/0,2817,2372364,00.asp

---

### Post by webmiester on 2017-11-21
Wow everyone, thank you for all your replies.  I really really appreciate it.  I think it will take me sometime to read on many of the stuff you guys mentioned and will get back if I do have further questions.  I really appreciate this as it helps bring my research to a direction I never thought of before.

---

### Post by webmiester on 2017-11-21
> **LHammonds said:**
> Greetings.  I work for physicians like yourself.  I appreciate what you do for your community.

Are all of your Windows PCs in individual workgroups?  No central Active Directory server?

If using Windows clients and you do not have a professionally-trained IT support staff, it would be best to use a Windows server for authentication and managing the PCs (policies) by joining them to the local domain.

However, if you just want a Linux-only solution for authentication, you might want to setup an OpenLDAP server so you can manage users and groups in one location and have the Windows PCs join that domain.

But as you have said, Windows PCs tend to get nasty viruses which can affect anything they have access to...including the files on a Linux OS.  Linux may not get infected by the virus but it can help spread it if other machines connect to the infected files...unless you have some sort of anti-virus on your PCs and your server(s).

To help guard against data encrypting/corrupting malware, the main thing you can do is to create multiple, versioned backups.  You never want to just have 1 backup (such as syncing 2 locations) because if damage is done in one location, it can be replicated to the other.  This is why it is important to have multiple backups over time.  If you get infected on Monday but do not notice the damage until Friday, any backups done during the week are useless and you would need to have a good backup from the weekend or earlier.

It's also important to have backups at an offsite location in case of natural disaster or malware that specifically targets backups.

Regarding your file share, I would recommend having just one single share.   Then control access to the various department folders via permissions based on groups.  When managing user accounts, do so via group membership.  That way you configure permissions on shares/files and only specify group permissions.  After the initial design of the file system and permissions, you should never need to man-handle permissions again and just manage what groups people belong to in order to grant them necessary access.

Example:

S:\Dept\Admin\
 - Set access for an admin group here
S:\Dept\HR\
 - Set access for an HR group here
S:\Dept\Marketing\
 - Set access for a marketing group here
S:\Users\Jon.Doe\
 - Set access for this specific user as their "private" location and  re-direct their "My Documents" and their applications default save  location here.
S:\Users\Jane.Doe\
 - Set access for this specific user as their "private" location and  re-direct their "My Documents" and their applications default save  location here.
S:\Users\Mary.Jane\
 - Set access for this specific user as their "private" location and  re-direct their "My Documents" and their applications default save  location here.

LHammonds

Hi LHammond, as of the moment, the PCs arent sharing any data.  They are just connected to the internet.  As per active directory, Ive talked to some IT students regarding this and they say it can only be done in windows and not Linux.  Instead of Active Directory, can I use Active Control Lists?  Will they do the same thing?

---

### Post by mastablasta on 2017-11-22
> **webmiester said:**
> As per active directory, Ive talked to some IT students regarding this and they say it can only be done in windows and not Linux.  Instead of Active Directory, can I use Active Control Lists?  Will they do the same thing?

students are not quite right. there is OpenLDAP. there is also Samba AD. in fact AD in some form probably existed on linux/unix before it even came to windows.

if you look at Zentyal, they will have such a thing implemented in GUI. I believe Nethserver should have it as well (in case you prefer CentOS/RedHat base).

---

