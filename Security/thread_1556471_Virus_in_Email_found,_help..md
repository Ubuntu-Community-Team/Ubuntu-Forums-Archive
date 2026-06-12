---
title: "Virus in Email found, help."
date: 2010-08-19
forum: Security
---

### Post by Camilia on 2010-08-19
Unable to send mail thus adjust protocol port and it worked. Things moving slow on computer. Thus ran clamtk virus scanner. It found a virus. Tried to quarantine it but not successful.Have GUI version 4.15 Antivirus engine .95.3. Virus is located at /home/kim/.mozilla-thunderbird/zrlm4cOj.default/Mail/LocalFolders/Inbox Phishing.Heristics.Email.SpoofedDomain

What do I do to get rid of it?

---

### Post by realzippy on 2010-08-19
delete it?

---

### Post by uRock on 2010-08-19
What is the name of the infected file?

---

### Post by Camilia on 2010-08-19
I thought the file name was in info I gave, otherwise don't know.

I am unable to get the scanner to delete it. It says select and right click. I left click and right click. Seems I have to remove thunderbird. What a pain to reset it for I have 7 email address.

Still need to know how to prevent this from happening again. I didn't open any unknown email.

Could the scanner be missing something for on it have
antivirus engnine ---(minus sign with red circle) 0.95.3
GUI version----------(minus sign with red circle) 4.15

I completely removed thunderbird, including hidden files.  Now it is in
/home/kim/.local/share/Trash/files.mozilla-thunderbird/zrlm4cOj.default/Mail/Localfolders/Inbox Phising.Heristics.Email.SpoofedDomain

Went back into hidden files and found 2 items that didn't look like they belonged. They were 2 globes that I have seen previously when I save email to desktop. Removed them and now no virus. 

Feel need better security for mail. 
Had:
Clamav-base, libclamav6, Clamav-fresh, Clamav-daemon
Added today:
mailscanner, sanitizer, clamsmtp, viruskiller

Will any of these conflict? Anything better to do to prevent this from happening?

---

### Post by uRock on 2010-08-19
I apologize for not seeing that there was a space in the location of the corrupt file between "Inbox Phishing," so I thought something may have been missing.

ClamAV is good. In the future when it shows the location of the file, you can remove it with the rm command in a terminal. Example; ```
sudo rm /home/kim/.mozilla-thunderbird/zrlm4cOj.default/Mail/LocalFolders/Inbox[COLOR=Red]\ [/COLOR]Phishing.Heristics.Email.SpoofedDomain
```
Do notice that whenever there is a space in the filename of a command that a [COLOR=Red]\[/COLOR] has to be entered into the command to tell the terminal to ignore the space.

---

### Post by Camilia on 2010-08-19
I don't see anything different since I adding virus protection for email. Is there something I need to do to activate it?

---

### Post by uRock on 2010-08-19
Have you read the Ubuntu Security sticky thread written by bodhi.zazen? Even though you did find a legitimate Windows virus in your Inbox, it will not effect your Linux system. Please read this clip from bodhi.zazen's thread and check out the links that he included.

[COLOR=blue]> [COLOR=blue][CENTER][SIZE=6]**The Windows Mindset **[/SIZE][/CENTER]
[/COLOR]


[COLOR=Black]If you are coming from a Windows background you are used to terms like  antivirus, spyware, and firewalls. Linux is different and these are not  as important. They are discussed first because these are FAQ on the  forums. Unfortunately, it is sometimes difficult for new users to wade  through some of the FUD (some of which is produced by anti-virus  companies) ...[/COLOR]


[COLOR=Black]**[SIZE=4]_Viruses_[/SIZE]**

The fact of the matter is: viruses/worms take advantage of flaws or  holes in the code. At this time of this writing, there are no  significant Linux viruses "in the wild". Linux boxes are no less targets  than any other OS, many of the large (ie valuable) Internet sites run  on *nix so there is no lack of motivation to crack into *nix. 

Do not believe the suggestion that the Linux community is complacent or  "behind the times" in terms of viruses, or any other security issue.  Linux developers have not "ignored" viruses, rather the OS is built to  be highly resistant to them and since the code is "Open" there are  literally thousands of eyes watching ... 

This is an example of what it would take to install malware on an Ubuntu box : 

[Install evilmalware]("http://www.gnu.org/fun/jokes/evilmalware.html")

(Don't worry, that link will NOT install anything :twisted: )

For the most part, Linux anti-virus programs scan for Windows viruses  which do not run on Linux. There are increasing reports, however, that  Windows malware may run in wine, as such I added a section reviewing  what I feel you should know about security if you choose to install and  run wine (see below).

Please understand, anti-virus programs, and in fact most [HIDS]("http://en.wikipedia.org/wiki/Host_based_intrusion_detection_system"), are "reactive" in that they can only protect you from known viruses. They can only protect you against malware *after* it is developed and incroporated into HIDS, not before. Furthermore the "fix" will be to close any hole(s) in the code, *these fixes will be available through security updates* (which are more frequent in Linux then your previous OS if you are coming from Windows). 

Reasons **AGAINST** antivirus on Ubuntu:[/COLOR][/COLOR]
[LIST=1]
[*][COLOR=Black]They scan primarily for Windows viruses.[/COLOR]
[*][COLOR=Black]There is a high rate of false positives.[/COLOR]
[*][COLOR=Black]Isolation/inoculation is poor.[/COLOR]
[*][COLOR=Black]And currently there are no known active Linux viruses (so there is essentially nothing to detect).[/COLOR]
[/LIST]
[COLOR=Black]
Reasons **FOR** antivirus on Ubuntu:[/COLOR]
[LIST]
[*][COLOR=Black]You are running a file or mail server with Windows clients.[/COLOR]
[*][COLOR=Black]You wish to scan files before transferring them, by email, flash drive, etc., to a Windows machine.[/COLOR]
[/LIST]
[COLOR=Black]
Running antivirus can make some sense if you are intending to "protect"  Windows users, however, IMO, for a variety of reasons, it is best if  Windows users learn to protect themselves.

_Note_[/COLOR]  [COLOR=Black]: There have been many documented cases in Windows and Linux  that a buffer overflow in an antivirus product has been an attack  vector!

If you would like to run an antivirus program on Ubuntu you have several choices :[/COLOR] 

[LIST]
[*][Antivirus]("https://help.ubuntu.com/community/Antivirus")
[*][ClamAV]("https://help.ubuntu.com/community/ClamAV")
[*][http://www.avast.com/eng/avast-for-l...rkstation.html]("http://www.avast.com/eng/avast-for-linux-workstation.html")
[*][http://www.pandasoftware.com/download/linux.htm](http://www.pandasoftware.com/download/linux.htm)
[*][http://www.centralcommand.com/linux_server.html](http://www.centralcommand.com/linux_server.html)
[*][http://www.f-prot.com/products/home_use/linux/](http://www.f-prot.com/products/home_use/linux/)
[/LIST]


---

### Post by Camilia on 2010-08-19
> **uRock said:**
> Even though you did find a legitimate Windows virus in your Inbox, it will not effect your Linux system. 

So my virus was a windows virus? I got it while using ubuntu thus confused. Mail only comes in on ubuntu side. Windows I only use to view netflix and haven't done that for a long time.

---

### Post by uRock on 2010-08-19
> **Camilia said:**
> So my virus was a windows virus? I got it while using ubuntu thus confused. Mail only comes in on ubuntu side. Windows I only use to view netflix and haven't done that for a long time.
It would have been received from another system, unless you sent the email to yourself. It was most likely an attachment to an email. Thunderbird automatically downloads everything in the email to the Inbox. ClamAV doesn't search for any Linux viruses.

---

### Post by OpSecShellshock on 2010-08-19
It's also probably important to note that a Windows email virus or phishing message or whatever the detection was for would not have caused the performance issues that had initially caused you to run the scan (as it would not have been able to run).

---

### Post by uRock on 2010-08-20
hero_hont, Linux doesn't need AV unless it is serving files to Windows systems.

---

