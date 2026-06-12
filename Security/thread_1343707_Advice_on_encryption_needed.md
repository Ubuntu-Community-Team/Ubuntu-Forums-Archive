---
title: "Advice on encryption needed"
date: 2009-12-02
forum: Security
---

### Post by bailout on 2009-12-02
I have a laptop and a netbook and at the moment they don't have any encryption. I want to start using some and have done some reading but I am still a bit unsure which way to go.

My computers are dual boot with Windows XP and have a seperate shared data partition mounted at boot and formatted as ntfs. I don't store state secrets on them or anything illegal but just want to protect personal data if they are stolen. I want to keep the system as easy and quick to use as possible while providing reasonable scurity.

My thoughts so far are to use the ubuntu standard mehod to encrypt /home and then some way of encrypting the data partition. The data partition would have to be accesable from windows as well as linux. I was thinking of using truecrypt for that but then I saw that dmcrypt can be accessed from windows via FreeOTFE [http://en.wikipedia.org/wiki/FreeOTFE](http://en.wikipedia.org/wiki/FreeOTFE) Also I saw this thread [http://ubuntuforums.org/showthread.php?t=864556](http://ubuntuforums.org/showthread.php?t=864556) claimig that dmcrypt was faster and more reliable.

Any thoughts or experiences on truecrypt vs dmcrypt? I was also thinking I might encrypt my windows partition as well.

Also any comments on my general plan? Will just encrypting home give me reasonable security for hat I want? Does the ubuntu encrypted /home use normal user login? I use a simple password for this as it is a pain to type in a complex one each time I want to do something needing sudo. I wondered if I could use another more complex one for the ncryption a it would only be entered once a session.

thanks

---

### Post by bailout on 2009-12-03
Anyone?

---

### Post by hofstra14 on 2009-12-03
I currently use TrueCrypt on both Windows and Linux.  I have encrypted flash drives and removable USB storage and moved the devices back and forth without and issues.  I currently have a 1TB encrypted volume on my desktop where I store everythng of value.  Just pick a strong passphrase and it should provide you with a solution that is more than adequate to protect data at rest.

---

### Post by shaggy999 on 2009-12-03
Truecrypt is a really great product as long as you're not a license-nazi (although TC is "open source" it is still fairly restrictive compared to most open source licenses). As far as product functionality, there isn't much that can compare with Truecrypt. It would work great for a data partition shared between windows and linux because it's available for both with the same user interface for both. Also truecrypt can be used to encrypt the Windows OS if you wanted to.

As for ubuntu, there are two main methods for encrypting home: dm-crypt & ecryptfs. dm-crypt encrypts the entire partition that you choose, but it does require using the alternate CD to set it up unless you want to do some fiddling of installing packages and setting up the partition manually and bootstrapping the installed OS from the LiveCD. Not recommended to do that, use the alternate CD. The ecryptfs option simply encrypts the directories per user and is easily enabled through a checkbox during installation of either the liveCD or alternate CD.

I should also add that if you're installing netbook remix your options are to do the easy ecryptfs method or install dm-crypt manually as there is no alternate CD for netbook remix.

I myself have a netbook and wanted a dm-crypted netbook remix and had to set it up manually. It took a bit of work, but it works great.

Unlocking encrypted drives is easy. If you use dm-crypt then you will be asked for the password to the /home partition when you boot up. If you use ecryptfs then your home directory is automatically decrypted using your login password when you log into the system.

---

### Post by bailout on 2009-12-13
Thanks for the replies. I decided to go with truecrypt. I have now encrypted my shared partition and have got access from both windows and linux. The only problem was I couldn't create the partition from linux as it didn't offer me the option of formatting a ntfs. I had to do the setup from windows and then access from linux.

Not sure why theis is but I also noticed that gparted wouldn't let me format as ntfs either although the ntfs driver was installed and working fine. Anyway, it wasn't important as setting it up from windows was just as easy.

---

### Post by Dr Small on 2009-12-13
> **bailout said:**
> I don't store state secrets on them or anything illegal but just want to protect personal data if they are stolen. I want to keep the system as easy and quick to use as possible while providing reasonable scurity

Are you a scientist working for the IPCC? :p <insidejoke/>

---

