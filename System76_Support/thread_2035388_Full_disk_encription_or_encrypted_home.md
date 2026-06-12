---
title: "Full disk encription or encrypted home"
date: 2012-07-30
forum: System76 Support
---

### Post by feydrutha on 2012-07-30
I have just ordered a new Lemur Ultra. From what I have read so far, it seems it comes with neither full disk encryption nor home directory encryption out of the box. Since some level of encryption is a hard requirement for me (company policy, and a reasonable one in my opinion since laptops are easy to lose/steal), I would like to know what is the recommended way to achieve this.

I read in another thread that full disk encryption is not recommended, but not a lot of detail on why. I can probably live with only encrypting the home directory. How can I set that up? 

Also, I would possibly need to either encrypt or disable swap as well. Since I specced it with 16GB of RAM, disabling swap would be an option, but I would like to have hibernate-to-disk which I presume requires swap. Is it possible to get hibernate-to-disk working with encrypted swap? Or is full-disk encryption the only option if I am this paranoid?

---

### Post by isantop on 2012-07-30
> **feydrutha said:**
> I have just ordered a new Lemur Ultra. From what I have read so far, it seems it comes with neither full disk encryption nor home directory encryption out of the box. Since some level of encryption is a hard requirement for me (company policy, and a reasonable one in my opinion since laptops are easy to lose/steal), I would like to know what is the recommended way to achieve this.

I read in another thread that full disk encryption is not recommended, but not a lot of detail on why. I can probably live with only encrypting the home directory. How can I set that up? 

Also, I would possibly need to either encrypt or disable swap as well. Since I specced it with 16GB of RAM, disabling swap would be an option, but I would like to have hibernate-to-disk which I presume requires swap. Is it possible to get hibernate-to-disk working with encrypted swap? Or is full-disk encryption the only option if I am this paranoid?

When you set up your computer during First-Run, you can choose to have your home folder encrypted.

Also, full-disk encryption isn't [currently] supported because it requires a lot of tweaking to get everything working properly. It also breaks support for certain functions and can cause conflicts with some hardware.

---

### Post by Welly Wu on 2012-07-30
I purchased my System76 Lemur Ultra (lemu4) on June 26th, 2012. I have Corsair Vengeance PC3-12800 16.00 GB DDR3 dual-channel SODIMM RAM.

When you get your System76 Lemur Ultra, you can elect to encrypt your home partition and your swap partition by checking off the box where you create your Administrator account and password. The standard cipher is Advanced Encryption Standard in CBC ESSIV:SHA-256 mode of operation at 256 bits 14 rounds cipher strength and it uses SHA-512 hash algorithm. Both the Intel Core i5-3210M and Intel Core i7-3610QM support AES-NI which stands for Advanced Encryption Standard New Instructions. I have the Intel Core i5-3210M CPU. It provides up to 5 times hardware acceleration for AES.

The other option is to download and burn a blank 700 MB CD-R disk containing the Ubuntu 12.04 64 bit Long Term Service Alternative Install .ISO file. Here, you can enable Linux Unified Key System and Logical Volume Mapper for full-disk encryption. I spoke with System76 about the differences between the standard LiveCD and Alternative Install CD and they said that there is no difference except one has a graphical installation and the other is a text based installation method.

If you work in an industry that mandates the use of strong cryptography, then I would recommend that you stick with the defaults and encrypt your /home and /swap partitions as I mentioned how to do so in my opening paragraph. Full-disk encryption is mandatory for US government, military, and law enforcement along with intelligence agencies, bureaus, departments, and units. If this does not describe you or your case usage, then I recommend that you stick with the default settings and do not re-install Ubuntu 12.04 64 bit LTS using the Alternative Install CD-R method.

You seem to be new to this so you can send me a private message if you need further help. I used to be the Help Desk and Support Technician at New Jersey Institute of Technology in Newark, New Jersey 07102. I am a cryptography expert.

By the way, the Alternative Install CD-R method allows you to choose the Serpent cipher if you want extreme safety, privacy, and security and you don't mind a greater impact on speed and performance. Otherwise, AES CBC ESSIV:SHA-256 at 256 bits 14 rounds and SHA-512 hash algorithm is the default cipher. Mind you, CBC ESSIV:SHA-256 is not approved by Department of Defense, National Security Agency, or National Institute of Standards and Technology. CBC Plain is approved and authorized and certified, but it has known weaknesses and flaws such as the watermark attack. The Alternative Install CD-R allows you to choose the cipher's mode of operation and the cipher strength at 128, 192, 256 bits.

System76 is a good company. They stand behind their customers and their products and services 100 percent. They have been in business for 6.5 years.

---

### Post by ufugu on 2012-07-30
@Welly Wu:  In another post you mentioned your tweaks (trim, noatime, discard etc) for the Crucial SSD.

I've seen instructions on various webpages for additional tweaks that need to be performed on SSDs with encryption. Did you do anything special with yours? 

I don't mean to hijack the thread but this actually seems like the perfect place for it and I know you are an expert on cryptography. Thx.

---

### Post by feydrutha on 2012-07-30
> **isantop said:**
> When you set up your computer during First-Run, you can choose to have your home folder encrypted.

Also, full-disk encryption isn't [currently] supported because it requires a lot of tweaking to get everything working properly. It also breaks support for certain functions and can cause conflicts with some hardware.

Thanks. I have full disk encryption on my current laptop, but I'm happy to go with home+swap encryption if that is better supported and easy to do.

---

### Post by feydrutha on 2012-07-30
> **Welly Wu said:**
> 
When you get your System76 Lemur Ultra, you can elect to encrypt your home partition and your swap partition by checking off the box where you create your Administrator account and password. 


Thanks, that's what I was hoping for.

> 
The other option is to download and burn a blank 700 MB CD-R disk containing the Ubuntu 12.04 64 bit Long Term Service Alternative Install .ISO file. Here, you can enable Linux Unified Key System and Logical Volume Mapper for full-disk encryption. 


Yeah, I used the alternate installer to set up my previous laptop with lvm and full disk encryption, but since I am buying a pre-installed ubuntu I will try to avoid re-installing from scratch...

---

### Post by Welly Wu on 2012-07-30
The optimizations for SSDs are applicable for full-disk encryption or just encryption for both the /home and /swap partitions.

System76 does not recommend and support full-disk encryption. You are putting your new computer at risk if you do re-install Ubuntu 12.04 64 bit LTS with full-disk encryption. I have never done this myself as I value System76 and their support and warranty. I recommend that you stick with the default configuration as it will present you with no problems.

It's your /home and /swap partitions that contain confidential user data. If you encrypt both the /home and /swap partitions, then you wind up with a performance penalty of just 3 percent. If you do full-disk encryption with LVM/LUKS, you pay a 6 percent performance penalty. It may not sound like much, but those are the facts.

Stick with the defaults and you won't wind up with problems down the road.

---

### Post by isantop on 2012-07-31
> **Welly Wu said:**
> The optimizations for SSDs are applicable for full-disk encryption or just encryption for both the /home and /swap partitions.

System76 does not recommend and support full-disk encryption. You are putting your new computer at risk if you do re-install Ubuntu 12.04 64 bit LTS with full-disk encryption. I have never done this myself as I value System76 and their support and warranty. I recommend that you stick with the default configuration as it will present you with no problems.

It's your /home and /swap partitions that contain confidential user data. If you encrypt both the /home and /swap partitions, then you wind up with a performance penalty of just 3 percent. If you do full-disk encryption with LVM/LUKS, you pay a 6 percent performance penalty. It may not sound like much, but those are the facts.

Stick with the defaults and you won't wind up with problems down the road.

Just wanted to point out that while we don't support full-disk encryption, we will continue to support a normal copy of Ubuntu. It won't void a warranty or your support plan.

---

### Post by 3Miro on 2012-07-31
I do run full disk encryption on Ubuntu 12.04 and System76 Pangolin 8. I have experienced no issues or whatsoever. On Ubuntu 11.10, you had to disable hibernation to avoid having type separate passwords to decrypt / and swap, however, on 12.04 hibernation was disabled by default and I moved to using a swap file.

Other than that, I simply used the alternative CD to set my machine and I have no loss of functionality. There is a potential risk in losing all data on a fully encrypted partition (if the sector with the key gets corrupt), but I have backup on everything important and people should backup important files with or without encryption. Some files are backed up on UbuntuOne, others are backed up on my unencrypted desktop.

---

### Post by PGScooter on 2012-08-03
> **isantop said:**
> 
Also, full-disk encryption isn't [currently] supported because it requires a lot of tweaking to get everything working properly. It also breaks support for certain functions and can cause conflicts with some hardware.

What are the potential problems? Hibernate (as someone else mentioned in this thread)? Anything else?

thanks

---

### Post by isantop on 2012-08-03
> **PGScooter said:**
> What are the potential problems? Hibernate (as someone else mentioned in this thread)? Anything else?

thanks

Encrypted partitions can often be impossible to recover in the event of a reinstall.

---

### Post by 3Miro on 2012-08-03
> **PGScooter said:**
> What are the potential problems? Hibernate (as someone else mentioned in this thread)? Anything else?

thanks

If you are using encryption, make sure to have an unencrypted backup copy of everything important (like an external HDD that you keep at home).

---

### Post by PGScooter on 2012-08-03
> **isantop said:**
> Encrypted partitions can often be impossible to recover in the event of a reinstall.

Ah, good point. Thank you.

---

### Post by PGScooter on 2012-08-03
> **3Miro said:**
> If you are using encryption, make sure to have an unencrypted backup copy of everything important (like an external HDD that you keep at home).

I don't understand this. I agree that a back up is good, but why can't the backup be encrypted?

---

### Post by 3Miro on 2012-08-03
> **PGScooter said:**
> I don't understand this. I agree that a back up is good, but why can't the backup be encrypted?

You can read about the details of encryption and how it works, I am no expert, but for an encrypted HDD there are several crucial sectors that hold the key. If those sectors get corrupted, then you lose absolutely everything. Encrypted folders would hold a similar idea.

Every encrypted HDD, partition or folder runs the risk of total loss. On the other hand, if a sector of a regular HDD gets damaged then you will lose a file or two, but not everything. Thus it is highly advisable to have a unencrypted copy of everything, you are running a mush lower risk.

---

### Post by jerome1232 on 2012-08-03
> **3Miro said:**
> You can read about the details of encryption and how it works, I am no expert, but for an encrypted HDD there are several crucial sectors that hold the key. If those sectors get corrupted, then you lose absolutely everything. Encrypted folders would hold a similar idea.

Every encrypted HDD, partition or folder runs the risk of total loss. On the other hand, if a sector of a regular HDD gets damaged then you will lose a file or two, but not everything. Thus it is highly advisable to have a unencrypted copy of everything, you are running a mush lower risk.

Keeping an unencrypted copy almost nullifies the benefit of having encryption in the first place.Someone breaks into your house and steals the external for example. 

It's a good idea to backup the header information for the encrypted partition just in case something does happen to the header. I believe some methods of encryption use redundant header information as well.

---

### Post by 3Miro on 2012-08-03
> **jerome1232 said:**
> Keeping an unencrypted copy almost nullifies the benefit of having encryption in the first place.Someone breaks into your house and steals the external for example. 

I am encrypting my laptop so that I don't lose it or someone doesn't get it from on the street. Mobile devices are a lot more vulnerable than desktops.

There has to be more valuable things in your house then your HDD, buy a safe, enforced doors or home security system.

> 
It's a good idea to backup the header information for the encrypted partition just in case something does happen to the header. I believe some methods of encryption use redundant header information as well.

Your data, your risk, your decision. I am just giving an advice here.

---

### Post by jerome1232 on 2012-08-03
I was giving an alternate view point, not debating with you.

---

### Post by PGScooter on 2012-08-04
Thanks for the advice and opinions guys! A little friendly debate is always welcome. I still don't understand why having two encrypted copies (the original on my laptop and an external HD) isn't a foolproof backup plan. If the laptop fails or is stolen, I can just plug-in the HD into a computer and I've got my data back. The only problem I see is if both fail/are stolen.

So the only advantage I see to not encrypting the HD is the case that your laptop is lost/stolen/damaged and at the same time somehow the header information got corrupted on the HD (whereas with an unencrypted HD if a little bit of info is corrupted the rest is still recoverable).

Did I get that right?

---

### Post by Welly Wu on 2012-08-04
I have a safety deposit box at PNC Bank in down town West Orange, New Jersey 07052 in the USA. I put my valuables inside my safety deposit box since PNC Bank has a much higher insurance policy against theft, disaster, and losses than owning a safe at home.

I use TrueCrypt 7.1a. It allows you to backup the header volume including the key. I keep my digital keys and certificates stored inside a 7-zip .7z file that I have backed up to my CrashPlan+ account and my TrueCrypt AES XTS 256 bits 14 rounds SHA-512 encrypted Western Digital My Passport 2.0 TB USB 3.0 Portable hard disk drive. I also uploaded that .7z file to my Google account which has two factor authentication to my Google Drive and to Ubuntu One. For key management, I use KeePass2 and LastPass Premium. I also have a Yubico Yubi Key for strong two-factor authentication. I also backup my keys to my Kingston DataTraveler HyperX 128 GB USB 3.0 thumb drive which is also protected with TrueCrypt 7.1a AES XTS 256 bits 14 rounds SHA-512 hash algorithm.

What I just told you cost me a small fortune. This means that almost all of my data is fully encrypted including all of my confidential and private user data. There is a significant cost structure involved and I have to pay PNC Bank $42.80 USD per year for my safety deposit box.

In the event of a disaster, theft, or loss, my data is safe and secure. I have made multiple copies and data backups to multiple destinations among multiple storage devices and formats.

Most people don't need full-disk encryption. Think about it. You want your private and confidential data to remain that way. You want to encrypt your user data. Your software applications and your operating system can be re-installed from scratch. This is why full-disk encryption is mandated if you work for a bank, 3 letter government agency dealing with national security or defense, military, certain federal law enforcement agencies, intelligence agencies, healthcare, payment card services, etc. Most end users that are classified as home users don't need full-disk encryption.

It is dangerous to leave a plain text copy of your data on any storage device if it requires confidentiality and integrity. Easy availability means that anyone can get access to it. If you must do this, then get a safety deposit box at your local bank. Do not store that data and the device in a safe at your home because burglars target safes especially if they break into your home while you are at home. I do not recommend that you leave a plain text copy of your confidential data on any device. The risks are too high. Most storage devices and formats are transportable. How do you think that the device manufacturer shipped the product to your home or business? Even external hard disk drives designed for desktops can be transported and they contain up to 4 terabytes of storage capacity at USB 3.0 or Thunderbolt speeds. This means that if you leave the data in plain text format, someone can make a duplicate copy of your data in a short period of time if it is stolen or lost.

You put your identity, reputation, job, and data at greater risk by not encrypting your confidential data. Most identity theft and fraud or financial crimes are perpetuated against victims because they did not encrypt their confidential data with strong passwords and they did not have a good credentials management system including key management.

I recommend TrueCrypt for most people especially if you plan to encrypt the entire volume or drive. It's free and open source software that is compatible with Windows, Macintosh, and GNU/Linux. It gives you three ciphers AES, TwoFish, and Serpent and three hash algorithms RIPEMD160, SHA-512, and Whirlpool. It allows you to make a backup of the header volume including the key so you can restore it in case of disk corruption.

I also recommend LastPass Premium for key management and credentials management. It is compatible on Windows, Android, iOS, Macintosh, GNU/Linux and BlackBerry. It has two factor authentication especially if you purchase a pair of Yubico Yubi Keys for strong two-factor authentication. You can create and store secure notes which contain your user IDs and passwords and other critical confidential information and data.

It costs a significant amount of money, but it is affordable since most banks and LastPass charge a low affordable annual price for their services and products.

If you must use full-disk encryption, contact System76 directly to get specific instructions on how to proceed on one of their computers. If you use a PC or Macintosh, then you are on your own to provide support and help in case something goes wrong. Full-disk encryption will slow down your computer by about 5 - 6 percent. If you have an Intel Core i7 or Xeon CPU with AES-NI, a SATA-III 6GB /s Solid State Drive that supports AES-NI at AES-128 or AES-256, and at least 4 GB of DDR3 RAM, then the performance impact is reduced to as little as 3 percent because of the encryption hardware acceleration. If you stick with just encrypting your home and swap partitions, then the performance impact is as little as 1.5 percent or less.

Remember, use two strong complex and unique passwords to enable full-disk encryption and your administrator password. This means that you will have to remember at least two passwords every single time you turn on your computer. Then, you will have to remember a third password for your LastPass master password. Beyond that, it is up to you. I have to also remember my GnuPG password so that makes it four for me, but I don't enable full-disk encryption so I have to remember 3 passwords.

Look into TrueCrypt more closely. It is easier and better than LUKS/LVM and it is compatible across multiple platforms.

---

### Post by 3Miro on 2012-08-04
Reading this thread means I should do better to protect my nuclear launch codes.

Look if you have information worth billions of dollars, you would be a fool to take advice from a random person on an on-line forum.

What information are you actually trying to protect? Credit card number? Personal Bank information? Everything that I have on the HDD thieves can get if they break into my house anyway. Get a safe in your house and put an unencrypted copy of the data in it. Then you will be safe if you lose your laptop or if someone steals it when you travel and you will be safe if the encryption breaks you are also safe.

If your information is that much more valuable, then pay a professional to give you real advice.

---

### Post by Welly Wu on 2012-08-04
Most insurance companies do not recommend that people purchase and keep a safe in their homes. Most insurance policies do not cover losses in excess of $500.00 USD. If you purchase a premium insurance policy, then it will only cover up $2,500.00 USD worth of losses and you can only make one claim. Everything must be well documented and up to date and your insurance provider must have copies of your documentation including photographs of your valuables. This is why it is much safer to store your valuables inside a safety deposit box at your local bank. They have much better security mechanisms in place and they have better insurance to protect their customers against losses. Did you know this fact to be true or not?

This is why you should not own a safe in your own home. If an armed burglar intrudes while you are at home, you are putting your life and your valuables at risk with a safe inside your home.

The purpose of this thread is to learn industry standard best practices. I am a CISSP and Security+ certified professional. So, I do know better than most people about information assurance. I also have a lot of other IT certifications. Do you have certifications?

Data leakage and losing devices happens every single day. People forget their belongings. Laptops are commonly lost items. USB thumb drives get lost more frequently. Portable external hard disk drives get lost as well. Smartphones are a gold mine of valuable data and they get stolen or lost frequently. The statistics are well documented.

This is why you want to encrypt as much of your confidential data as possible especially in data in motion scenarios. A combination of file containers, full-disk encryption, encrypted home and swap partitions, and individual file encryption makes sense because people are creating and accessing more data every single day. Most of our data is unique like our own fingerprints and it can be used against us in a targeted attack. I also have my Certified Ethical Hacker certification so I know. Your data is used to track and monitor your behavior. It identifies who you are and where you work or live or travel. It identifies your family, friends, co-workers, and colleagues.

This is why it is very risky not to encrypt your confidential data. Leaving your data in plain text format is very risky. It places your life at risk and it is unnecessary and it is preventable.

Almost everybody has secrets. Today, more people are storing and accessing their secrets using a device that connects to the Internet and the world wide web which are not trustworthy networks. This is an additional risk factor that most people deem to be necessary and acceptable. Anyone on the Internet can identify you based on your data and your patterns and they can launch a targeted advanced persistent threat against you. They can hold your data hostage or for a ransom against you.

For the most part, encryption in a data at rest scenario stops most attackers and attack vectors. This is when your data is the most secure. It also means that your devices are vulnerable to theft and loss when they are being transported from one location to another location.

I have seen people lose their entire life savings and they have been sued in court because they were the victims of an attack either physical or cyber in nature. Had they encrypted their data, it would have been a different outcome for their business and their personal lives. Cryptography is powerful and it is classified as a munition in the USA.

I think that you are being naive and foolish by discounting the importance of cryptography and confidential data. Until you become the victim of an attack, you will never know how expensive and time consuming it can be to recover. Sometimes, recovering from an attack is not possible.

---

### Post by Welly Wu on 2012-08-04
Do you even realize that connecting to the Internet and the world wide web is considered to be a high risk behavior according to certain federal agencies? Anyone in the world can target and attack your identity, reputation, business, assets, and data and they can destroy hardware and software and data. They can deny availability of your own computer and data from you. Encryption does not protect against these threat vectors, but it does slow down an attacker from gaining unauthorized access to your valuable confidential data. In most cases, it mitigates the destructiveness of an targeted attack.

Isantop does not recommend full disk encryption, but System76 engineers will tell you that there is no difference between a fully-encrypted System76 computer and one with encryption for just the home and swap partitions. Who do you believe? For me, balance is important. Balancing confidentiality, integrity, and availability is crucial. I want the full speed and performance of non encrypted data for my operating system and my software applications because I can re-install it from scratch. I want confidentiality and integrity for my home and swap partitions because that is where I store my critical data. It really is the best of both worlds. Ubuntu 12.04 64 bi LTS runs at full speed and performance on my System76 Lemur Ultra (lemu4) while keeping my critical data confidential. This is why it is an option with the default LiveCD installation media. This is why it is supported by System76.

Remember, full-disk encryption does not protect you against boot sector attacks. The boot sector must remain non encrypted. If you store your boot sector and boot loader on the hard disk drive, solid state drive, or solid state hybrid hard disk drive, then it can be attacked by anyone who gains physical access to your computer. If you store your boot sector and boot loader on a USB thumb drive, then you effectively give yourself two-factor authentication, but you must never lose your USB thumb drive or else you will lose access to your operating system and your software and your data.

For me, the hassles of remembering my LUKS password and inserting my USB thumb drive to boot up my computer were not worth the hassles. It made using my previous ASUS N61JV-X2 notebook PC cumbersome and inconvenient. Most importantly, it does nothing to protect me against advanced persistent threats and targeted attacks once I logged into my computer and connected to the Internet.

I highly recommend that you encrypt your /home and /swap partitions and leave it at that. Store your confidential data in your /home partition and make copies and data backups onto the appropriate storage devices and formats. Use TrueCrypt and AES XTS 256 bits 14 rounds SHA-512 as much as possible. Make a header volume backup for each storage device and format using TrueCrypt. Use LastPass Premium and KeePass2 for credentials management and key management. Go to your local bank branch and get a safety deposit box. If you do these things, then you assure yourself a reasonable amount of security against most attackers and local physical attack vectors.

Do not buy a safe and store it inside your home. It is a magnet for burglars and thieves. It will put your life at risk if you are attacked while you are at home. You can wind up getting killed at home by an attacker if you have a safe in your home. It has happened to many victims in the past. Do your research.

---

### Post by PGScooter on 2012-08-05
Thank you very much for the in-depth replies Welly Wu and 3Miro!

> **3Miro said:**
> Look if you have information worth billions of dollars, you would be a fool to take advice from a random person on an on-line forum.

I disagree (well, ok maybe if billions of dollars). People on these forums often give more than just unsupported advice. They explain the logic behind their answers. This can help you make your own decision. This is why I appreciate the answer of Welly Wu. Welly Wu gave many details and explanation to back up the recommendation.

I am now convinced that encrypting swap and home is the way to go. Now I need to do some research on how to encrypt swap on install. From what I remember you can either encrypt home on the normal install or do LUKS on alternate install. But I don't think there was an option for encrypt swap. I'll check this out.

Thanks again to both of you for your advice and explanations. In the end, it's not just a matter of being informed, it's also a preference. You have to weigh your personal preferences of being hassled by the extra security measures with your personal risk aversion preferences. And you have to throw in the probability of your home being broken into, which is also specific to the individual.

Thanks!

---

### Post by Welly Wu on 2012-08-05
When you encrypt the /home partition, you also encrypt the /swap partition automatically. When you change your Administrator password, it also changes the password for your encrypted /home and /swap partitions automatically.

Ubuntu makes it really easy to encrypt your /home and /swap partitions automatically during the installation. I recommend that you stick with the defaults like I did myself. Fewer things will break and fail as a result.

---

### Post by PGScooter on 2012-08-06
> **Welly Wu said:**
> 
Ubuntu makes it really easy to encrypt your /home and /swap partitions automatically during the installation. I recommend that you stick with the defaults like I did myself. Fewer things will break and fail as a result.

Sounds good to me! Thanks for your help Welly Wu.

---

### Post by feydrutha on 2012-08-16
Just to follow up on this: in the end I went for encrypted home+swap, so I did not have to reinstall. 

In any case, the hibernate option is disabled (as it is now by default in ubuntu). I tried manually hibernating with:

```
sudo pm-hibernate
``` 

...but it did not work (when I turned it back on it just booted normally).

My swap is 16GB according to parted, which is maybe enough to hibernate my 16GB RAM... I'm not 100% sure if the swap was already encrypted when I did this test. Is hibernate supported by system76, with and/or without encrypted swap?

---

### Post by feydrutha on 2012-08-16
> **3Miro said:**
> I am encrypting my laptop so that I don't lose it or someone doesn't get it from on the street. Mobile devices are a lot more vulnerable than desktops.

There has to be more valuable things in your house then your HDD, buy a safe, enforced doors or home security system.



Your data, your risk, your decision. I am just giving an advice here.

Personally, I backup to an encrypted external drive... but the drive is a little case connected by usb with 2 hard disks in raid1, so it is quite unlikely that both get corrupted at the same time.

I don't have any nuclear launch codes but I prefer not to have to worry what someone may find there, if it were to be lost or stolen.

---

### Post by feydrutha on 2012-08-16
> **feydrutha said:**
> 
My swap is 16GB according to parted, which is maybe enough to hibernate my 16GB RAM... 

Actually according to the system monitor application, I have 14.9 GiB Swap vs 15.6 GiB RAM, so I may have to resize some partitions to be able to hibernate. But i'd like to know if others have had luck getting hibernate to work,, and if it's possible with encrypted swap, before I start doing that.

---

### Post by isantop on 2012-08-16
> **feydrutha said:**
> Just to follow up on this: in the end I went for encrypted home+swap, so I did not have to reinstall. 

In any case, the hibernate option is disabled (as it is now by default in ubuntu). I tried manually hibernating with:

```
sudo pm-hibernate
``` 

...but it did not work (when I turned it back on it just booted normally).

My swap is 16GB according to parted, which is maybe enough to hibernate my 16GB RAM... I'm not 100% sure if the swap was already encrypted when I did this test. Is hibernate supported by system76, with and/or without encrypted swap?

We don't do any testing with hibernate now that it isn't an Ubuntu-supported option. Using hibernate won't void your warranty, but it's problematic at best. 

Hibernate has never played nice with encrypted partitions. I would recommend not using them if you need hibernate. If you do want to use them, then you need to avoid hibernate.

---

### Post by feydrutha on 2012-08-16
> **isantop said:**
> We don't do any testing with hibernate now that it isn't an Ubuntu-supported option. Using hibernate won't void your warranty, but it's problematic at best. 

Hibernate has never played nice with encrypted partitions. I would recommend not using them if you need hibernate. If you do want to use them, then you need to avoid hibernate.

Ok, thanks. Then I guess the question goes to other users: has anyone had luck doing hibernate on the lemur ultra? If so, I might give it a try.

---

### Post by Welly Wu on 2012-08-18
I have not turned on hibernate because I knew that it had problems in Ubuntu 11.10 64 bit with my previous ASUS N61JV-X2 notebook PC. I had full disk encryption and it never worked properly specifically resuming from hibernation mode.

I use suspend to RAM feature sporadically. It is much faster than resuming from hibernation.

Try to stick with the default configuration as much as possible and make customized changes only where and when necessary. This way, you will have a reliable and secure Ubuntu.

---

### Post by Welly Wu on 2012-08-29
If you do choose to use full-disk encryption, then make sure that you select Advanced Encryption Standard in Cipher Block Chaining Encrypted Salted Sector Initialization Vector : Secure Hash Algorithm 256 bits at 256 bits 14 round cipher strength and Secure Hash Algorithm 512 bits. This is especially true if you purchased a System76 notebook or desktop PC with the latest generation Intel Core i5 or i7 or Intel Xeon with vPRO Central Processor Units. You will get 4X faster hardware acceleration for AES encryption speed and 10X faster hardware acceleration for AES parallel decryption speed. AES 128 is FIPS PUB 197 certified while AES 256 is FIPS 140-2 validated and certified.

Do not choose Serpent cipher for your primary boot or system drive. It is very very slow and it does not receive the benefit of AES-NI hardware support or acceleration. The only time that you should consider using the Serpent cipher is if you have leeway to choose it for extremely unique and confidential data on a data drive.

Twofish is no longer available as an option as an alternative cipher. Blowfish has been eliminated as an available cipher for quite some time.

Canonical plans to eliminate the Alternative Install .ISO with the release of Ubuntu 12.10 32 and 64 bit. In fact, they plan to integrate the Debian installation process including the capability to use full-disk encryption and AES or Serpent ciphers into the LiveCD .ISO with Ubuntu 12.10 32 or 64 bit. This makes life simpler for Canonical and the end user in my opinion.

Remember, AES is the industry standard cipher of choice by academia, corporations, military, intelligence, law enforcement, government, and security industries in both the public and private sectors worldwide. In terms of its engineering, it is usually one of the best choices available to the public as a general purpose cipher. For example, the latest generation Intel Core i5 or i7 CPU with AES-NI turned on can process up to 400 MB/s of AES encrypted data per thread. This means that my Intel Core i5-3210M CPU which supports AES-NI can process up to 1.60 GHz of AES encrypted data since it is a dual-core with Hyper Threads and it offers up to 4 processing threads. An Intel Core i7-3610QM has four cores and Hyper Threads which offers up to 3.20 GHz of AES encrypted processing or 8 processing threads. The faster the base core frequency, the faster the AES-NI processing speed and performance which works in tandem with the number of available cores and threads per CPU.

For most people, a dual-core with Hyper Threads CPU is sufficient to handle most multi-tasking digital work flows.

---

