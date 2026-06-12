---
title: "Disk driver not found"
date: 2009-06-08
forum: Server Platforms
---

### Post by KLStringer on 2009-06-08
I'm trying to install 9.04 on an HP Netserver LPr and when I get to the HDD detection it fails to find the HDD and prompts me to choose a driver from a list or install from removable media.  I have what I believe is the drivers on a USB stick but when I try to access it I can not and the installer tries to install 9.04 onto my memory stick instead.

Where do I find the right drivers if those aren't the right ones and how do I get them to install from an USB stick?

This is my first swing at working with Ubuntu so I'm on a learning curve, hope its not to steep.

---

### Post by KLStringer on 2009-06-08
One of the SCSI drivers from the list will detect 8.9 MB of the 18.2 GB of the drive but then I get an error that says its to small to install onto.

I also tried extracting the files from the .exe file I DL'd from HP and placing them on my USB stick but it still tries to install onto my USB stick instead on detecting any drivers for the HDD

---

### Post by Cheesemill on 2009-06-08
The .exe drivers are no good for you, exe files are for Windows only.
What SCSI card is in the machine?

Cheesemill

---

### Post by KLStringer on 2009-06-08
All I can say is its the card that comes with the sever, if you can point me to where I can find out I will work to get you a better answer. I've never worked with an actual server just MS Server 2003 OS in school and that was on a desktop.

---

### Post by KLStringer on 2009-06-08
The SCSi Configuration Utility comes up as Symbios SYM53C895 ver. 1.10 and it shows the drive there. The adapter has the following setup values:

SCAM Support =                                         off
Parity =                                                      on
Host SCSI ID =                                            7
Scan Order =                                              Low to High (0...Max)
Removable Media Support =                         None
CHS Mapping =                                           Alternate CHS Mapping
Spinup Delay (secs) =                                  2
Secondary Cluster Server =                         No
Termination =                                             Auto

The device settings are:

HP 18.2GST318406LC   HO05

Sync Rate =                                            80
Data Width =                                           16
Disc =                                                     On
Time Out =                                              10
Scan Bus =                                              Yes
Scan LUNS =                                            Yes
Queue Tags =                                          On
Init Boot =                                               No


Not sure if any of that helps any but figured I'd post it anyway

---

### Post by cariboo on 2009-06-08
The server edition, has a problem with scsi cd-rom drives, If you have one of those, that may be your problem.

Try an ide cdrom drive to see if that solves the problem.

---

### Post by KLStringer on 2009-06-08
CD-Rom is IDE only SCSI device we have is the HDD

---

### Post by zharmad on 2009-06-08
Check and make sure that your server mainboard isn't reporting the devices to the OS as SCSI. I know that my IBM x200 server shows all IDE devices as SCSI, e.g. my primary IDE HDD shows as /dev/sda instead of /dev/hda.

---

### Post by KLStringer on 2009-06-08
OK, I'll check that tomorrow once I'm back in the office.

---

### Post by KLStringer on 2009-06-09
We decided to use a different sever that 9.04 it was able to auto detect the drives on, instead of spending the dev time figuring out what was wrong with the other server. We'll worry about it later or just put M$ on it if we end up needing it.

Now we're trying to figure out how to set up a sftp sever on the alternate server we install 9.04 onto, if anyone can point us to a sftp setup walk through we'd really appreciate it.

---

### Post by wirelessmonkey on 2009-06-09
sftp is a function of ssh, just make sure you have openssh server installed.

```
sudo apt-get update && sudo apt-get install openssh-server

```

---

### Post by KLStringer on 2009-06-10
From the looks of it the latest openssh was installed during installation when I tried to install it I received a message that it was already installed and up to date.

---

### Post by wirelessmonkey on 2009-06-10
ok, so you should be able to
```
 sftp username@remoteipaddress 
```

---

### Post by KLStringer on 2009-06-11
When I use that command I get the message:

The authenticity of host 'hostname (ipaddress)' can't be established
RSA key fingerprint is <hexstring>
Are you sure you want to continues connecting (yes/no)

I've tried following the steps here: [clicky]("http://sial.org/howto/openssh/publickey-auth/") but I can't seam to create the keys. I tired to follow [clicky]("http://inside.mines.edu/%7Egmurray/HowTo/sshNotes.html") but get the same message as above. I've goggled "openssh set up" but can't figure out how I configure it, add users, create the keys, how to set up where the files go to be shared, how users connect to the sftp to access the file.

---

