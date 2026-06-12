---
title: "Buffalo TerraStation NAS Permission trouble"
date: 2006-02-22
forum: Server Platforms
---

### Post by 1oki on 2006-02-22
Is anyone useing a TeraStation as a NAS with their server? I am and I seem to be running into some trouble with permissions... If anyone else is using a TerraServer and is having trouble feel free to share with me so we can compaire and contrast! thanks all!

-Luke

---

### Post by 1oki on 2006-02-22
Oh and to clear things... I am running Ubuntu as a PDC and the Terrastation is the network Drive. Its mounted as the whole /Home path.  ;)

---

### Post by 1oki on 2006-02-24
Nobody? sheesh...

---

### Post by aerials on 2006-02-24
I own a Terastation and I just mount 2 shares to /media without problems.
I made me a script to mount the shares, containing this line:

mount -t smbfs -o credentials=<path to password file>,uid=<username>,codepage=cp850,iocharset=utf8 //<ip terastation>/<sharename> /media/<mountpoint>

Where <path to password file> is the path to a file containing the lines 
> username=<username>
password=<password>

The rest speaks for itself I guess. I execute the script via sudo. 
Mounted that way, I have all the rights with my normal useraccount.

---

### Post by 1oki on 2006-03-01
[QUOTE=aerials]I own a Terastation and I just mount 2 shares to /media without problems.
I made me a script to mount the shares, containing this line:

mount -t smbfs -o credentials=<path to password file>,uid=<username>,codepage=cp850,iocharset=utf8 //<ip terastation>/<sharename> /media/<mountpoint>

Where <path to password file> is the path to a file containing the lines 


The rest speaks for itself I guess. I execute the script via sudo. 
Mounted that way, I have all the rights with my normal useraccount.[/QUOTE]


are you using Ubuntu as a Domain controller? If so how did you tell samba to use those shares? thats the only issue that i have. I had to mount the terrastation at /home because i didnt know how to tell Samba to look elsewhere... Pretty much what Im trying to do is change the location for a users default samba share... Sambas default share is /home/username  I would like to change this to somthing else but keep the profiles in the same place! Change the location of the share but keep the rest of samba (configurations and profile files) at default.

---

