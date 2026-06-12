---
title: "Add encryption to new disk."
date: 2014-10-13
forum: Server Platforms
---

### Post by Drew_Simrin on 2014-10-13
Hello, I am unsure how the encryption was setup when I setup the server, but I want to add full disk encryption to another disk in my system. When I setup Ubuntu Server 14.04LTS I opted for full disk encryption on the one drive that I had in the machine at the time. I have since added another hard drive and I would like to know how I can encrypt that drive too with the same passphrase and have it decrypt upon boot like my "main" disk. I am kinda new to Ubuntu server and I am just wanting to learn more. I tried looking around and I am having trouble finding how to do it. Thanks for your help. I would be happy to provide any additional information that is needed.

---

### Post by tinker_make on 2014-10-20
As far as I know when you encrypt 2 separate HDDs (maybe even 2 separate partitions) the bootup decryption needs to be done twice i.e. you can use same password, but you'll need to enter it twice.

As far as encrypting the second drive, you can try this guide [https://help.ubuntu.com/community/FullDiskEncryptionHowto](https://help.ubuntu.com/community/FullDiskEncryptionHowto)

---

