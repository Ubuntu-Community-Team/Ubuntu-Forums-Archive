---
title: "A suspicious files found"
date: 2021-07-12
forum: Security
---

### Post by Gnusboy on 2021-07-12
Hello

I was told to post here for information about 15 suspicious files I found on my system.

I hope you don't mind, but I want to find out if these files are as curious as they look. I found these in what was supposed to be a receipt from a local business for a set of fingerprints taken for a job. The store offered to send a receipt via email. Then I forgot about it. When I found and opened it, the simple receipt was in a folder with 15 other items - none of which were labeled "receipt." What was supposed to be a simple emailed receipt, seems to have much more information than expected.

I didn't think anything about the receipt until I saw a folder that was labeled "Fingerprints." in my home system. I didn't get around to looking at it until 3 days ago and I was truly surprised to see there were 15 files inside the folder - none of which were labeled as "receipt."

In addition to the files inside the "fingerprints" folder, I also found 2 separate ".cvs" files labeled as spreadsheets. They are older and out of date but show logins and passwords in plain text and no security. They look like spreadsheet forms, but I have never used a spreadsheet or a ".cvs" for anything.
 
I realize that unless they came to my house and injected these into my computer, email is likely the only way the files could get on my system. 

However, I don't recall receiving the "fingerprints" receipt, nor moving it to a different place on my system. Apparently, I did. 

Maybe I'm being alarmist with this. But when there are readable files in open text and numerous unexpected files where they should not be located, I am concerned, and I don't know how to interpret the issue. 

The one's I'm most curious about [B]are the 
".sudo_as_admin_successful", logins.json, "permissions," and "password" f[/B]iles. Maybe these are benign, but if so, why are they here? It seems like a lot of data for a simple receipt. 

I would like to know if any of the files are as dangerous as they look.

Thank you for your help.


Maybe these are benign, but if so, why are they here? It seems like  a lot of data for a simple receipt.
Here is what I found: Any clarity would be appreciated.

These are the files included:

Key4.db
Logins-backup.json
signed in user.json
Profiles.ini
unnamed.jpg
Fingerprint.html
.Profile
.sudo_as_admin_successful
Logins.csv
Places.sqlite
Permissions.sqlite
Logins.json
Flogins & Passwords.html

Cleardot_002.gif/home/gnus2me

Documents/fingerprint_files

csv logib=ns-3&datatables.csv
Text/home/gnus2me/documents/config2/floter

---

### Post by TheFu on 2021-07-13
You should never trust filenames to get information.  Filenames can be anything, even unrelated to what the contents of those files may be.
For example, a proper CSV file would be ASCII text with .... "comma separated values".  It isn't a spreadsheet, but someone could put a proprietary, binary, spreadsheet file with extra VBS inside knowing that typical users would be on MS-Windows, blindly double click on the file, have MS-Excel open it and completely pwn their computer.

Don't trust filenames to actually say what is inside a file.

Use the 'file' command and have the computer look at the files and report what they are truly holding. Then you can decide how dangerous each file might be.

On Linux, extensions don't mean a thing. They are for humans. The computer just doesn't care.

---

### Post by Gnusboy on 2021-07-13
Thanks Fu,
I get the labeling thing. I've seen it used before. But I only use the Writer in the Libre Office suite and don't know much about the rest.
 What tweaked me were the things inside of the folder marked "fingerprints" that just didn't mesh with it being a "receipt" for the service.

When I saw "sudo_as_admin_successful," "logins.json,"  "permissions," and password" I don't get under the hood of Ubuntu much and rely on the limited security of Linux. 

I'm a skeptic by nature and a cynic by experience, and it was the aggregate of those 15 items in the receipt for services that made me curious. 
I appreciate your help.

BTW - Early Cuyler says "gimme your money. I need some party liquor."

Jess

---

### Post by CharlesA on 2021-07-13
Did you download or execute the attached file? Seems kind of odd that those files would exist.

Did it come in a zip file or as a shell files or something else?

When you were working with it, did you enter your sudo password at any time?

Places.sqlite, Permissions.sqlite, and Profile.ini are probably related to Firefox, but it's very strange.

---

### Post by Gnusboy on 2021-07-14
Hey Charles

The folder was not zipped or compressed. It was in my home section under [COLOR=#000000] "Fingerprints." It was sent from a local business where I had taken my fingerprints for a job application. She got the prints and said she would sent ne a receipt via email.
When I saw the [/COLOR][COLOR=#000000] "Fingerprints." file in my home folder, I didn't think about it. I thought it would a receipt for services - like any other receipt. I finally got to it and then saw the odd contents. I did not understand why all that sub-information was inside it. I have not contacted the business yet, because I want to know more about it and to find out if other similar receipts had the same information. [/COLOR]
[COLOR=#000000]I just now scrolled down the fingerprint company's [/COLOR][COLOR=#000000]disclaimer:[/COLOR]

[FONT=Arial]**BIOMETRIC PRIVACY INFORMATION** In accordance with several biometric information privacy laws, including the Biometric Information Privacy Act in Illinois (BIPA), we are providing to you information about the collection, storage, use and purge of your biometric information, including fingerprints. Accordingly, you can find that information at the following links:[HR][/HR][TABLE="width: 643"]
[TR]
[TH="colspan: 6"][/TH]
[/TR]
[TR]
[TD]Terms & Conditions[/TD]
[TD]Fieldprint Privacy Policy[/TD]
[TD]FBI Privacy Act Statement[/TD]
[TD]FBI Noncriminal Justice Applicants Privacy Rights[/TD]
[TD]eConsent[/TD]
[TD]Biometric Disclosure[/TD]
[TD][/TD]
[/TR]
[/TABLE]
Please do not hesitate to contact us if you have further questions about your biometric privacy.[/FONT]
[COLOR=#000000] 
I would guess that the disclaimer is for the old comment of "If you don't have anything to worry about, unless you did something wrong. Fortunately, I don't have anything to worry about.
As it is, I don't have the skills needed to dig deeper into the "receipt" to see if there are other similar issues worth investigating further. 
I think it's worth asking the fingerprint business about it, but they probably don't know about it.
If you dig into it, I'd sure like to know if you find anything.
Thanks for your help.
Jess

[/COLOR]Files:

[COLOR=#000000]K[/COLOR][COLOR=#000000]ey4.db[/COLOR]
[COLOR=#000000]Logins-backup.json[/COLOR]
[COLOR=#000000]signed in user.json[/COLOR]
[COLOR=#000000]Profiles.ini[/COLOR]
[COLOR=#000000]unnamed.jpg[/COLOR]
[COLOR=#000000]Fingerprint.html[/COLOR]
[COLOR=#000000].Profile[/COLOR]
[COLOR=#000000].sudo_as_admin_successful[/COLOR]
[COLOR=#000000]Logins.csv[/COLOR]
[COLOR=#000000]Places.sqlite[/COLOR]
[COLOR=#000000]Permissions.sqlite[/COLOR]
[COLOR=#000000]Logins.json[/COLOR]
[COLOR=#000000]Flogins & Passwords.html[/COLOR]

---

### Post by CharlesA on 2021-07-15
I was expecting a PDF or something to be attached to the email since they said it was a receipt of some sort.

The part I don't understand is where this "fingerprints" folder came from since you said it wasn't zipped or compressed.

In any case, those files shouldn't be there and if they were attached to the email, contact the company and let them know you recieved an email with a suspicious attachment and see what they say.

Some companies will have you forward the email to [email]abuse@company.whatev[/email]er or have other procedures in place.

---

### Post by TheFu on 2021-07-15
Well, the first step I would have taken after receiving files is to place them into the /tmp/ directory to take a closer look.  /tmp is usually mounted with some added protections in the mount options to prevent really nasty things from being possible.  Mount options like nosuid, noexec, nodev are there to protect us from this sort of foolishness. A little more description: [https://www.oreilly.com/library/view/network-security-hacks/0596006438/ch01s02.html](https://www.oreilly.com/library/view/network-security-hacks/0596006438/ch01s02.html)

Any data-only file system mount should have those options set.  I wouldn't do that for HOME directories, since most power users would have a ~/bin/ directory for their personal scripts and noexec wouldn't stop that, but it would just make running them a little more hassle.

---

### Post by danielperez81 on 2021-08-15
If the files appeared out of nowhere, you may have a backdoor, see what ports you have open with netstat -putna

---

