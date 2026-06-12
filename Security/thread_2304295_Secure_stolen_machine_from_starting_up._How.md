---
title: "Secure stolen machine from starting up. How?"
date: 2015-11-25
forum: Security
---

### Post by Janiporo on 2015-11-25
Ubuntu 14.04 32 bit.

I would like to secure my computer, so if it gets stolen, the operating system will not start up.

One way is to install thumb-drive (or NAS) and move one key file there, and make a symlink (??) to it.

My computer has many wires everywhere, and I can easily hide a thumb drive there with extension usb cord.

The file I would move there should be accessed after the os mounts drives.

 Question is, what file should I choose? It should not be one that is accessed all the time, since it would slow system down.

 Is there such files, or is it too late to make this happen after the point where drives are mounted?

 I am using a headless machine, and if I remember correctly, I can not write login password at startup since I control it via VNC-remote desktop, and when computer starts to login screen, vnc can not yet connect to it and show me the desktop. I am currently using it with auto login for this reason. I do not mind writing password when computer starts, if it just would be possible to do that. (There is some workaround for that, but I did not understand the guides that I found) 

 Any ideas how I should make this happen? :roll:

---

### Post by grahammechanical on 2015-11-25
Why don't you do this through the BIOS/UEFI boot system. It is usually possible to set passwords for both accessing the BIOS/UEFI and for booting the machine.

---

### Post by kurt18947 on 2015-11-25
> **grahammechanical said:**
> Why don't you do this through the BIOS/UEFI boot system. It is usually possible to set passwords for both accessing the BIOS/UEFI and for booting the machine.

I first thought BIOS as well but if the machine is stolen, couldn't the machine be opened and the BIOS reset via a jumper? UEFI might be a possibility, I have no experience there. I wonder if encryption - either /home or whole disk - might be a better solution if the concern is data security.  Maybe both? If the thieves get the machine to start via resetting the BIOS/working around UEFI, they still wouldn't have anything of value except the hardware.

---

### Post by neil36 on 2015-11-25
There are computer cases (boxes) with front loading hard drive slots. I know because I have one. I don't have it with me, it is in storage, but I think it is a Gateway. 

If security and concern of theft is really so important, simply remove the hard drive. If you can't find or get a box with quick release HD slots, just take the side panel off and remove the HD that way. I mean after all you have wires everywhere anyway and the HD sitting out side the box wont make any difference.

Anyone capable of stealing your computer and getting past standard password protection, is probably going to start the machine before stealing it. What makes you think they will leave the USB behind? No, they will take the whole lot...wires and all...But at least you will still have the hard drive !!

---

### Post by mastablasta on 2015-11-26
just encrypt the hard disk. they can start it up but that's about it. no OS, no data is accessible.

also physical access is access, so the only remaining way to prevent people reading what is on the disk is to encrypt it.

From Truecrypt wiki site (now Verycrype to Cyphershed): [https://en.wikipedia.org/wiki/TrueCrypt](https://en.wikipedia.org/wiki/TrueCrypt)

> [h=3]Operation Satyagraha[[edit]("https://en.wikipedia.org/w/index.php?title=TrueCrypt&action=edit&section=27")][/h]In July 2008, several TrueCrypt-secured hard drives were seized from Brazilian banker [Daniel Dantas]("https://en.wikipedia.org/wiki/Daniel_Dantas_(entrepreneur)"), who was suspected of financial crimes. The Brazilian National Institute of Criminology (INC) tried unsuccessfully for five months to obtain access to his files on the TrueCrypt-protected disks. They enlisted the help of the [FBI]("https://en.wikipedia.org/wiki/FBI"), who used [dictionary attacks]("https://en.wikipedia.org/wiki/Dictionary_attack") against Dantas' disks for over 12 months, but were still unable to decrypt them.[SUP][[SIZE=2][86][/SIZE]]("https://en.wikipedia.org/wiki/TrueCrypt#cite_note-Dantas-88")[/SUP][SUP][[SIZE=2][87][/SIZE]]("https://en.wikipedia.org/wiki/TrueCrypt#cite_note-89")[/SUP]
[h=3]United States v. John Doe[[edit]("https://en.wikipedia.org/w/index.php?title=TrueCrypt&action=edit&section=28")][/h]In 2012 the [United States 11th Circuit Court of Appeals]("https://en.wikipedia.org/wiki/11th_Circuit_Court_of_Appeals") ruled that a *[John Doe]("https://en.wikipedia.org/wiki/John_Doe")* TrueCrypt user could not be compelled to decrypt several of his hard drives.[SUP][[SIZE=2][88][/SIZE]]("https://en.wikipedia.org/wiki/TrueCrypt#cite_note-90")[/SUP][SUP][[SIZE=2][89][/SIZE]]("https://en.wikipedia.org/wiki/TrueCrypt#cite_note-91")[/SUP][SUP][[SIZE=2][90][/SIZE]]("https://en.wikipedia.org/wiki/TrueCrypt#cite_note-92")[/SUP] The court's ruling noted that FBI forensic examiners were unable to get past TrueCrypt's encryption (and therefore were unable to access the data) unless Doe either decrypted the drives or gave the FBI the password, and the court then ruled that Doe's Fifth Amendment right to remain silent legally prevented the Government from making him or her do so.[SUP][[SIZE=2][91][/SIZE]]("https://en.wikipedia.org/wiki/TrueCrypt#cite_note-93")[/SUP][SUP][[SIZE=2][92][/SIZE]]("https://en.wikipedia.org/wiki/TrueCrypt#cite_note-94")[/SUP]
[h=3]David Miranda[[edit]("https://en.wikipedia.org/w/index.php?title=TrueCrypt&action=edit&section=29")][/h]Further information: [Glenn Greenwald § Detention of David Miranda]("https://en.wikipedia.org/wiki/Glenn_Greenwald#Detention_of_David_Miranda")
On 18 August 2013 [David Miranda]("https://en.wikipedia.org/wiki/David_Miranda"), partner of journalist [Glenn Greenwald]("https://en.wikipedia.org/wiki/Glenn_Greenwald"), was detained at London's [Heathrow Airport]("https://en.wikipedia.org/wiki/Heathrow_Airport") by [Metropolitan Police]("https://en.wikipedia.org/wiki/Metropolitan_Police_Service") while en route to [Rio de Janeiro]("https://en.wikipedia.org/wiki/Rio_de_Janeiro") from [Berlin]("https://en.wikipedia.org/wiki/Berlin"). He was carrying with him an [external hard drive]("https://en.wikipedia.org/wiki/External_hard_drive") said to be containing sensitive documents pertaining to the [2013 global surveillance disclosures]("https://en.wikipedia.org/wiki/Global_surveillance_disclosures_(2013%E2%80%93present)") sparked by [Edward Snowden]("https://en.wikipedia.org/wiki/Edward_Snowden"). Contents of the drive were encrypted by TrueCrypt, which authorities said "renders the material extremely difficult to access."[SUP][[SIZE=2][93][/SIZE]]("https://en.wikipedia.org/wiki/TrueCrypt#cite_note-mirandaReuters-95")[/SUP] Detective Superintendent Caroline Goode stated the hard drive contained around 60 gigabytes of data, "of which only 20 have been accessed to date." She further stated the process to decode the material was complex and "so far only 75 documents have been reconstructed since the property was initially received."[SUP][[SIZE=2][93][/SIZE]]("https://en.wikipedia.org/wiki/TrueCrypt#cite_note-mirandaReuters-95")[/SUP]
*[Guardian]("https://en.wikipedia.org/wiki/The_Guardian")* contributor Naomi Colvin concluded the statements were misleading, stating that it was possible Goode was not even referring to any actual encrypted material, but rather deleted files [reconstructed]("https://en.wikipedia.org/wiki/Data_recovery") from unencrypted, unallocated space on the hard drive, or even [plaintext]("https://en.wikipedia.org/wiki/Plaintext") documents from Miranda's [personal effects]("https://en.wikipedia.org/wiki/Personal_property").[SUP][[SIZE=2][94][/SIZE]]("https://en.wikipedia.org/wiki/TrueCrypt#cite_note-96")[/SUP] Glenn Greenwald supported this assessment in an interview with *[Democracy Now!]("https://en.wikipedia.org/wiki/Democracy_Now!")*, mentioning that the [UK]("https://en.wikipedia.org/wiki/United_Kingdom") government filed an [affidavit]("https://en.wikipedia.org/wiki/Affidavit") asking the court to allow them to retain possession of Miranda's belongings. The grounds for the request were that they could not break the encryption, and were only able to access 75 of the documents that he was carrying, which Greenwald said "most of which were probably ones related to his school work and personal use."[SUP][[SIZE=2][95][/SIZE]]("https://en.wikipedia.org/wiki/TrueCrypt#cite_note-97")[/SUP]
[h=3]James DeSilva[[edit]("https://en.wikipedia.org/w/index.php?title=TrueCrypt&action=edit&section=30")][/h]In February 2014, [IT]("https://en.wikipedia.org/wiki/Information_technology") department employee James DeSilva was arrested on [charges]("https://en.wikipedia.org/wiki/Indictment") of [sexual exploitation of a minor]("https://en.wikipedia.org/wiki/Child_pornography") through the sharing of explicit images over the [Internet]("https://en.wikipedia.org/wiki/Internet"). His computer, encrypted with TrueCrypt, was seized, and DeSilva refused to reveal the password. [Forensics]("https://en.wikipedia.org/wiki/Computer_forensics") detectives from the [Maricopa County Sheriff's Office]("https://en.wikipedia.org/wiki/Maricopa_County_Sheriff%27s_Office") were unable to gain access to his stored files


you can read more about how and why they stopped on wiki site. also looks like Linux edition had no issues at all.

---

### Post by Bucky Ball on 2015-11-26
*Thread moved to **Security**.*

---

### Post by Janiporo on 2015-11-26
I can not enter bios password since it is headless (has no monitor and no keyboard). I can put monitor , mouse and keyboard there for installing purposes, but will not keep them there all the time.

Removing hard drive is not an option, computer is always on.

I have 2 hard drives, one main (OS), and one storage, storage drive I will change to be encrypted. I can not encrypt main drive, since it has OS on it. I think I would have to format it and start all over again. I MIGHT do that, but am looking for other solutions for now.

Or is it possible somehow to encrypt my home folder without reinstalling OS?

There is SO many wires from time period of 10 years (some connected, some not), that it is impossible to find this usb-drive from there, especially if you do not know there is one. There is 50-100 meters on wires.

Truecrypt sounds nice :D

---

### Post by neil36 on 2015-11-26
> **Janiporo said:**
> Ubuntu 14.04 32 bit.

I would like to secure my computer, so if it gets stolen, the operating system will not start up....There is SO many wires from time period of 10 years...Ubuntu 14.04 32 bit...Removing hard drive is not an option, computer is always on....

Right...So you have a 32 bit machine that has not been turned off in 10 years. You have 100 meters of "wires" coming out of it. You want to know how to put vital files onto a USB drive that you can hide. 

Sounds to me like this 32 bit machine is a server hosting a web site. Maybe if you gave us the URL or IP address, we might be able to come up with a solution for you.

---

### Post by howefield on 2015-11-26
Thread cleaned.

Please keep it civil.

---

### Post by neil36 on 2015-11-26
> **howefield said:**
> Thread cleaned.

Please keep it civil.

Thank you. Acknowledged. ;)

---

### Post by Janiporo on 2015-11-26
Ok ;)

Not running any website.

IS there files that will run after mounting, that are vital? I am now installing the OS again, because I messed it up somehow yesterday, and I will encrypt the OS, but when does it ask for password, is this after VNC starts? If not, I will not be able to enter this password. (I bet is asks it earlier).

 Any ideas how to achieve my goal?

---

### Post by Janiporo on 2015-11-26
Ok, I tested out, and when I crypt the whole drive, it actually asks the password way before booting anything. Well, this was expected, and logical.

If I tick the option to encrypt my home folder, it will automatically set the "login with password" -option to on. Logical still. 

So I am now reaching my goal. Question is, how do I start VNC-server when os is at login-page?

---

### Post by neil36 on 2015-11-27
I have just thought of another idea...Open the case and remove the audio jack. Then cut the power wire to the HD (it should be yellow). Using a small junction add wire to the HD power wire long enough to reach the back of the case. Solder on a new audio jack and insert. Then get a cheap (and make sure it looks cheap) speaker box. Open the speaker box and cut the two wires off the speaker and join them together. The HD will then simply not have power unless that speaker box is plugged in. Glue or screw the speaker box to the desk or floor or wall or whatever. 


No crook is going to bother with a cheap and nasty speaker that they cannot even pick up as it is screwed to the desk...It will be a zillion years before they realise the reason the computer wont start is because they left the kill switch behind !!


No thief is going to bother trying to access the HD externally. If it doesn't start, they can't sell it. They wont bother, it is 10 years old with no monitor or keyboard and wont start... Anyone that goes to the effort of removing the HD and accessing it externally, already knows what is on it and they don't need to steal it. They can just turn up with a warrant and take it ;)

---

### Post by Janiporo on 2015-11-28
Nice idea, thinking outside of the box there, I like! :D

---

### Post by Skaperen on 2015-11-28
> **kurt18947 said:**
> I first thought BIOS as well but if the machine is stolen, couldn't the machine be opened and the BIOS reset via a jumper? 

if they can do that then they can remove the HD and plug it into another computer. so as a minimum the hard drive needs to be encrypted if it has any personal/confidential/proprietary data.

as to detecting if it has been stolen ... many ways ... tough choices.

---

### Post by Bucky Ball on 2015-11-28
> **Janiporo said:**
> ... thinking outside of the box there ... :D

Literally! :)

---

### Post by HermanAB on 2015-11-28
Encrypt, encrypt, encrypt...

Or more specifically, use LUKS and do so called 'whole disk' encryption.  In reality the /boot partition is not encrypted, since it has to boot somehow, but encrypting everything else, makes it practically impossible for anyone to get at your data.

---

### Post by Habitual on 2015-11-28
1st Rule of Security: There is no Security w\out Physical Security.
Buy a Pitbull and a short leash.
Luks can be [p0wn3d]("https://twopointfouristan.wordpress.com/2011/04/17/pwning-past-whole-disk-encryption/"): see rule 1.

---

### Post by Janiporo on 2015-11-28
Thanks guys, I will figure something out of these posts, and combine ideas ):P

---

