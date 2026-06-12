---
title: "I have question regarding Disk Encryption"
date: 2008-10-17
forum: Security
---

### Post by thenetduck on 2008-10-17
Hi
I just got my Lenovo back from IBM (some fixes were needed) and I am going to be install Ubuntu as my main os. I have some important financial information on my computer and would like to keep is safe, not only from random users, but if it was taking and tried to crack. Ulimantely I know anything can be cracked, but I want to make sure if it is, it will take 8 months to do it.

I am downloading the Alternative CD on Hardy, but am a little troubled. Do I only need to encrypt swap /home /tmp and /opt ? Can I encrypt /tmp if it's not it's own partition? I plan on setting my system up like this Paritions: Windows Vista (bios updates and such) /  /home /opt  Also, it is necessary to encrypt everything? I would like to install 8.10, will I be able to do this without reformatting everything? Will have have to use the 8.10 alternative cd to install it again? or will the normal one be fine? 

Thanks for any help, this is the first time I have atempted to encrypt my hard drive. 
The Net Duck

---

### Post by Sarmacid on 2008-10-17
If you only want to encrypt some files, it's not really necessary to do a full disk encryption. You can do symmetrical(Password) and asymmetrical(Private/public keys) encryption with pgp.

---

### Post by thenetduck on 2008-10-17
Ok so I can just encrypt certain sensitive data without the hassle of a full encrypted harddrive? What is the advantage of a fully encrypted hard drive? Who would use it and is it nessasary? I still want good performance on my computer.

---

### Post by Dr Small on 2008-10-17
> **thenetduck said:**
> Ok so I can just encrypt certain sensitive data without the hassle of a full encrypted harddrive? What is the advantage of a fully encrypted hard drive? Who would use it and is it nessasary? I still want good performance on my computer.
The advantage of a fully-encrypted hard drive is that the [attacker] would need to gain the keyfile or passphrase to unlock the system to boot, whereas a single encrypted file can be accessed without booting the system, collected and then attempted to be cracked.

Decrypting a single file also possess the threat of temporary files that could be found and retrieved, whereas with a full-disc encryption, the entire system is encrypted, so who cares if there are temporary files.

---

### Post by jerome1232 on 2008-10-17
Using full disk encryption the only thing I was ever able to notice performance wise was copying huge amounts of data took a bit longer.

---

### Post by hyper_ch on 2008-10-18
if you don't want to have to worry much about what and where you encrypt it, use full disk encryption.

8.10 however has an option to encrypt just your home folder. That might also be interesting but I have not looked "deeply" into that.

---

