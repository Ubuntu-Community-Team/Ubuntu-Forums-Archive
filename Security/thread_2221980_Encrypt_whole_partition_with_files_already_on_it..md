---
title: "Encrypt whole partition with files already on it."
date: 2014-05-04
forum: Security
---

### Post by Durkslag on 2014-05-04
Hi!

We've got a server with large 6 TB partition formatted with ext4 and we already have a lot of files on it.

We would like to encrypt the whole partition so when we boot up the computer we can login over SSH and type a command that decrypts/mounts the encrypted partition (in this case /media/work). And it's kept decrypted until reboot. OS is on a separate disk, so only files on this one. Running Ubuntu Server 14.04.

What is the best and simplest solution for this? Love how the decryption of the home folder with ecryptfs works (even though it gets encrypted again when logging out).

Thanks in advance!

Edit: Or is it much better to buy some external drives and format before encryption? (Rather not but maybe it's easier...)

---

### Post by bashiergui on 2014-05-04
I'm sure it can be done- I'll let someone more experienced tell you how. 

But an important question first: Why? A server should be up and running nearly all the time. Encryption only protects data when it's not mounted or running. So what is the point of encrypting the 6 TB drive if the data will always be unencrypted? Maybe buy some physical security instead.

---

### Post by HermanAB on 2014-05-05
Encryption protects data at rest.  So it protects your data against physical theft of the server.  It also protects your data one day when the HDD is decommissioned and tossed away or sold on Ebay.

---

### Post by Durkslag on 2014-05-05
It's more of a policy here, that we try to have most of our stuff encrypted. We don't have any sensitive data but a lot of our work is saved on the server and we'd prefer the encryption.

The 6 TB is built with a couple of disks with hardware raid so only one large partition. It actually seems to be easier to wipe everything and start with a fresh partition after all.

Ecryptfs seems to be the best choice because we can use the whole 6 TB. Unfortunately we have to format first.

---

### Post by bashiergui on 2014-05-10
I get it's a policy, but the policy doesn't really accomplish anything.

What's the goal of encryption? Where is it most vulnerable to attack? If your data center is in the ghetto, then disk encryption is probably the way to go. But if you are concerned about unauthorized eyes seeing your data, then disk encryption is going to get you bupkis.

If it were me I would use encrypted containers to store the unused data. Then to access the data I would use an encrypted protocol like ssh or ssl. I don't know the details of your architecture so I can only give vague advice, which is "end to end encryption." The price you pay is in performance- encryption slows access.

---

