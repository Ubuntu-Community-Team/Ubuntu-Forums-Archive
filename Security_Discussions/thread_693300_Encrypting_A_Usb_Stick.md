---
title: "Encrypting A Usb Stick"
date: 2008-02-10
forum: Security Discussions
---

### Post by synd7 on 2008-02-10
I have a new USB stick that i plan to use for transporting some sensitive information, is there any way to encrypt it in a way that will let me use it both at home on my ubuntu box and on windows boxes on which i DONT have administrator access?

I was thinking of using gpg and having a portable decrypting program for windows on the usb stick for decrypting on the windows boxes, but AFAIK i would need administrator access for all of these.

Is it possible to have an encrypted partition and a non-encrypted one, with the decryption software on the non-encrypted one that would work on both windows and linux?

---

### Post by faulkes on 2008-02-10
I believe [http://www.trucrypt.org](http://www.trucrypt.org) will do what you are looking for.

Faulkes

---

### Post by synd7 on 2008-02-10
I had thought of TrueCrypt but i would need admin privilages

> TrueCrypt can run in so-called 'traveler' mode, which means that it does not have to be installed on the operating system under which it is run. However, there are two things to keep in mind:

    * You need administrator privileges in order to able to run TrueCrypt in 'traveler' mode.
    * After examining the registry file, it may be possible to tell that TrueCrypt was run (and that a TrueCrypt volume was mounted) on a Windows system even if it is run in traveler mode.


---

### Post by euler_fan on 2008-02-11
If you have PGP/GPG on all the machines you can encrypt them to yourself using PGP/GPG. I want to say there's a FF plug-in which does GPG in gmail (but it might be generally) and so you could go back and forth using email and GPG.

I'd suggest getting a USB stick designed for security like the IronKey but I'm not sure if it works with anything but Windows.

EDIT: [Use 7zip with a strong password and the encryption flag set]("http://www.7-zip.org/7z.html").

Hope it helps.

---

### Post by Biochem on 2008-02-11
Seem to me like freeotfe is what your looking for.
[http://www.freeotfe.org/](http://www.freeotfe.org/)

I haven't try it yet but it seem promising. The only draw back would probably be mounting the encrypted partition on linux. the only way I know, is manually through the terminal with admin privileged. But since the Ubuntu box is your but not the windows one, it is manageable.

---

### Post by Coombabah on 2008-02-11
Would keepass(windows) and keepassx(Linux) do what you want?
It's mainly for account info and passwords but it also supports attachments.
It's simple, secure, keepassx is in the universe repositories and keepass is on sourceforge.net
If you are a bit security paranoid like me you can use a passphrase and a keyfile and don't have the keyfile on the usb key.

---

### Post by synd7 on 2008-02-11
Unfortunately FreeOTFE needs admin privilages on windows just like TrueCrypt
Keepass looks good but as far as i can tell it doesnt do files.

I don't mind the solution not being an on-the-fly type deal, the loading of drivers to acheive this is what seems to require admin privilages. 7z with encryption seems like a good solution, though i'd like to hear if anyone else has found a more elegant solution

---

### Post by euler_fan on 2008-02-11
> **synd7 said:**
> Unfortunately FreeOTFE needs admin privilages on windows just like TrueCrypt
Keepass looks good but as far as i can tell it doesnt do files.

I don't mind the solution not being an on-the-fly type deal, the loading of drivers to acheive this is what seems to require admin privilages. 7z with encryption seems like a good solution, though i'd like to hear if anyone else has found a more elegant solution

The unfortunate part here is it would even take admin privileges to install the 7zip software.

I think what you'll need to do is twofold:
1) Assess just how badly you need to move data around by USB Key. It sounds like you're moving files back and forth between work and home (most students don't need to encrypt term papers). I would bet your IT people would be much happier with--if you really need it--setting up something like secure webDAV or paying for a swissdisk account or the like. These are more secure in that there is no USB key to lose, etc.
2) If you still need to move it by USB key, get with your admin folks and get them to install TrueCrypt or some equivalent piece of software they can live with.

I'm afraid you really don't have any good options on this one without admin rights on all the boxes.

---

### Post by Coombabah on 2008-02-11
> **synd7 said:**
> Unfortunately FreeOTFE needs admin privilages on windows just like TrueCrypt
Keepass looks good but as far as i can tell it doesnt do files.


I have a few files encrypted in my keepass database file as attachments. Keepass does sort of do files to a limited extent if you have documents with sensitive information but it wouldn't be as good or fast as 7z if you had lots or files or used them frequently.

Keepass or 7z might be an option until you find something better.

---

### Post by Irihapeti on 2008-02-11
Using TrueCrypt with a USB stick has limitations, I understand, due to the way that these media try to minimise writes. I was reading about it on the TrueCrypt site the other day. If you aren't worried about the possibility of recovering unencrypted deleted copies of the files from your drive, it may not matter.

---

### Post by bluewraith on 2008-02-11
From the truecrypt website:
> 
**Wear-Leveling**

Some storage devices (e.g., some USB flash drives) and some file systems utilize so-called wear-leveling mechanisms to extend the lifetime of the storage device or medium. These mechanisms ensure that even if an application repeatedly writes data to the same logical sector, the data is distributed evenly across the medium (logical sectors are remapped to different physical sectors). Therefore, multiple "versions" of a single sector may be available to an attacker. This may have various security implications. For instance, when you change a volume password/keyfile(s), the volume header is, under normal conditions, overwritten with a re-encrypted version of the header. However, when the volume resides on a device that utilizes a wear-leveling mechanism, TrueCrypt cannot ensure that the older header is really overwritten. If an adversary found the old volume header (which was to be overwritten) on the device, he could use it to mount the volume using an old compromised password (and/or using compromised keyfiles that were necessary to mount the volume before the volume header was re-encrypted). Due to security reasons, we recommend that TrueCrypt volumes are not stored on devices (or in file systems) that utilize a wear-leveling mechanism. To find out whether a device utilizes a wear-leveling mechanism, please refer to documentation supplied with the device or contact the vendor/manufacturer.

Good luck finding out if the USB has wear-leveling or not. I've never seen any documentation on it, nor had I even heard of it before using TrueCrypt. 
I'd be more worried about the unencrypted data being stored in the page file on the windows box, myself... but that depends on how valuable the data is. (Not to you, but to the person whos willing to sort through that mutha to get it)

---

### Post by kevdog on 2008-02-14
I posted a similar question about this exact same topic about 6 months ago and never found an elegant solution.  TrueCrypt requires admin priviledges. As far as gpg I believe you at least need the ability to run executables on the windows machine -- some admins lock out the dos prompt.  To use gpg you would have to do the encrypting at the command line, since installation of a GUI based gpg like GpG4win or GPGee requires admin rights to install and creates a registry setting.  You have to also be careful if any temporary files are created.  If using gpg at the command line, you need to set an environment variable that specifies the temp file on the USB stick, rather than on the c: driver.  Also you would most likely want to adjust the path statement at the same time so that the executable is looked for first on the usb drive.  (these two things are really easy to do, if you need help I can send you the code).  To my knowledge, its impossible as a user without admin rights to actually flush anything from RAM, so its possible things would be left in RAM -- if you are super paranoid.  

I like the TrueCrypt solution better, however the bad part about this solution is that it needs to be installed on both machines.  

Again no good solutions if you ask me.

---

