---
title: "Intel 520 Series AES encryption?"
date: 2012-09-24
forum: System76 Support
---

### Post by justinwiley on 2012-09-24
Hi,

I noticed the Intel 520 Series does whole-disk AES encryption...assuming its the newer, non-recalled version that had a controller bug that prevented it.  I'm wondering:

 - does the version of Intel 520 sold by System76 support AES (i.e. it works)

 - how hard it is to enable this with Ubuntu (simple BIOS setting? kernel drivers?)

Thanks!

Justin

---

### Post by Welly Wu on 2012-09-24
The Intel 520 Cherryville does support AES-256 bits encryption and you will need the System76 Gazelle Professional in order for the BIOS to support the password. The Lemur Ultra Thin does not support self-encrypting drives.

---

### Post by justinwiley on 2012-09-24
Thanks Welley.  Do you have any experience with self-encrypting drives or Intel520 personally?  Any downsides, wonkiness?

---

### Post by Welly Wu on 2012-09-25
It is best to use self-encrypting drives with Microsoft Windows 7 64 bit Enterprise or Ultimate Edition. You can also use them with Microsoft Windows 8 Pro 64 bit. The reason is that some notebook PCs like Dell Precision and Latitude and HP Elitebook come with multi-factor authentication including biometrics such as a fingerprint scanner or a facial recognition software application and they come with Trusted Platform Modules. Usually, they support self-encrypting drives within their UEFI or BIOS for older models. It simply works by prompting you to enter in the unique password every time you boot your PC. Make sure that you choose a pass phrase instead of a password and it is at least 15 characters long including upper and lower case letters, numbers, and special symbols. From there, it unlocks the SED and you boot your OS and log in.

SEDs simplify security because it is a self-contained unit. The processor, RAM, keys, and everything are stored inside the SED. Using a TPM enhances security because the keys can be sealed inside the TPM and it has additional features such as the ability to allow for PINs to be used and you can also use an external USB thumb drive for an additional form of multi-factor authentication.

In Ubuntu, I have not tried out a SED. You would be limited to single factor authentication at boot time when the BIOS loads up and prompts you for your password. You can not use a finger print scanner to unlock a SED at boot time using Ubuntu yet. It may be supported in the future, but not now. The Ubuntu OS has to boot up before you can use a finger print scanner.

You're better off with a SED that complies with the Trusted Computing Group's OPAL standard. This guarantees that hardware and software based attack vectors will fail to compromise the data on the SED under duress for now. There may be new attack vectors that weaken OPAL SEDs, but none are known right now.

I am a CISSP and CompTIA Security+ security specialist.

---

### Post by juwiley on 2012-10-12
Hey Welly,

Great background on TPM and SED, I've always been confused as to how all that integrates.  Unfortunately Windows is not an option for me, since my development toolchain relies on *nix environments, and I choose not to support any MS product when I can avoid it.

I wonder: how does the Intel 520 store the password?  I assume (hope!) in hashed form using SHA-512 or the like.

I went ahead and ordered the Gazelle Professional and Intel 520.  It did not come with the BIOS settings enabled by default, after contacting System 76 support they sent a new BIOS image, which I used to flash the BIOS, and the options showed up.  Seems to be working after enabling user/drive password...although I'm not sure how to verify since I can't boot the system without entering in the user bios password, and I don't want to crack open the system and pull the harddrive.

Justin

---

### Post by Welly Wu on 2012-10-12
The Intel 520 Cherryville SSD stores the password set in the BIOS on the SSD itself. It is stored in a separate area from the rest of the storage area and it is protected from tampering. You don't need to worry about it anymore now that System76 sent you the proper BIOS to support AES encryption on the Gazelle Professional.

---

### Post by Welly Wu on 2012-10-12
The Intel 520 Cherryville SSD is not TCG OPAL compliant. It does provide hardware enabled AES 256 bits encryption with a supported BIOS password. This means that you get whole drive encryption capability, but you are not protected against hardware and software based attack vectors since it is not TCG OPAL compliant. You will need to wait until Intel ships TCG OPAL compliant SSDs sometime next year and replace your Intel 520 Cherryville SSD at that time if you want full protection.

In your case, this may not be necessary unless you work at a job that is in a highly regulated industry that mandates that you use mobile workstations for enterprise customers including HDDs and SSDs that are TCG OPAL compliant. System76 does not fall into this category and I assume that you don't work in such an industry that requires it.

Be happy with what you have got.

Software based full disk encryption is less safe and secure, but it is widespread and it can be installed and easily configured on almost any Ubuntu certified PC or server. I used dm-crypt and LUKS for my encryption needs and it suffices for me.

---

### Post by regency on 2012-12-30
> **Welly Wu said:**
> The Intel 520 Cherryville does support AES-256 bits encryption

Intel 520 Cherryville does NOT support AES-256 bit encryption as it uses Sandy Force's SF-2281 controller.

---

### Post by regency on 2012-12-30
> **Welly Wu said:**
> regency: you're a god damn moron.

First, I wish to state in no uncertain terms that you have been very rude to me and your behaviour is most un-called for, especially for someone who aspires to eventually work as an adjunct professor of English in some local community college.

> **Welly Wu said:**
> http://communities.intel.com/message/167092

Second, the very article that you referenced provides solid proof that my assertion is correct: Intel 520 SSDs do NOT support AES-256 bit encryption as it uses Sandy Force's SF-2281 controller. I should know it very well because I bought a couple of Intel 520 SSDs from my friend who works for that company.

Below are extracts of the article that you quoted that support my claim:

> Intel has published a specification update for the Intel SSD 520 Series product, updating the specification [COLOR=Blue]from AES 256-bit encryption to AES 128-bit encryption.[/COLOR]  Other Intel Solid-State Drives with data encryption, such as Intel SSD 320 Series, also feature AES 128-bit encryption.[COLOR=Blue]

> In the Intel SSD 520 Series, the key length is 128 bits. [/COLOR]> The higher the number of bits in a key, the stronger the level of encryption.[COLOR=Blue]> If, however, our customers are not satisfied with the 128-bit encryption in an Intel 520 Series SSD purchased before July 1, 2012, they can contact Intel customer support prior to October 1, 2012 to return their product and Intel is offering to provide a full refund of the purchase price. [/COLOR]

---

### Post by Welly Wu on 2012-12-31
I do apologize to you for being so rude. That was not necessary.

I have an Intel Cherryville 520 120 GB model and it does support AES-256. It will work if your PC supports encryption at the BIOS level.

Legally, all US OEMs can only ship storage devices that support AES-128 to be exported outside the United States. The PC must support encryption at the BIOS level in order for it to be utilized. If you purchase a new notebook PC with a SED or SSD that supports AES-256 and it has a TPM, then it will work. If the storage device also meets TCG's OPAL standard, then it will support AES-256. The Intel Cherryville 520 does not meet OPAL.

It all depends upon which application that you want to use it for and if the PC supports it at the BIOS level or not.

Why do you care?

I need it because I have a HP Elitebook 8760w with Microsoft Windows 8 Pro 64 bit. I turned on AES-256 using the HP UEFI and the TPM seals the encryption keys. This enables Microsoft Bitlocker with multi-factor authentication. I checked Microsoft Bitlocker and I enabled AES-256 bit encryption. I do this because I provide help and technical support to a friend who works for a US defense contractor and they authorize me to connect to their AD server at his company via their VPN.

You'll have to find a reason why it matters to you to be useful to you. Otherwise, this is all academic.

---

### Post by regency on 2012-12-31
> **Welly Wu said:**
> I have an Intel Cherryville 520 120 GB model and it does support AES-256.

As you still insists that your SSD in question supports AES-256 bit encryption, **could you tell us the brand and version number of the host controller that it uses?**

If yours is using LSI SandForce 2281 host controller, then you have ONLY AES-128 bit encryption, NOT AES-256 bit encryption.

Please click on the following link for more info: [http://www.intel.com/content/www/us/en/solid-state-drives/ssd-520-spec-update.html](http://www.intel.com/content/www/us/en/solid-state-drives/ssd-520-spec-update.html)

To the best of my knowledge and based on what my friend who is working for Intel told me, **ALL** Cherryville 520 series SSDs sport LSI SandForce 2281 controllers. [B]No exception.

[/B]I have 3 Intel Cherryville 520 series SSDs of different capacities: 240GB, 480GB, 480GB and they **ALL** use LSI SandForce 2281 controllers.They were all bought in the US of A through my Intel friend.

---

