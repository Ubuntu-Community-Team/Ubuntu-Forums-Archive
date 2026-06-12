---
title: "Avast vs Clam AV"
date: 2010-02-26
forum: Security
---

### Post by Richiegs on 2010-02-26
Every time I run Clam AV to scan for viruses, Clam AV never detects any viruses. However, when I run Avast, it always detects viruses. I suspect they are mostly false positives. Because as soon as I delete them and restart the computer, I won't be able to log in.

1. Is Clam AV not a good software to detect viruses?
2. Is it true that Avast always detects a lot of false positive viruses?
3. Which anti-virus software do you recommend?
Thanks

---

### Post by zeroseven0183 on 2010-02-26
Although most people will normally say 99.9% of your Linux use won't need an antivirus, it's always good and safe to have one. I don't use antivirus that often and haven't fully used ClamAV (or ClamTK if you will, currently installed on my machine) and Avast but I would say, both are good softwares.

To help you decide which of the two, or maybe some other, antivirus programs is better, this article from TuxRadar can help you: [Get the best virus scanner for Linux.]("http://www.tuxradar.com/content/get-best-virus-scanner-linux")

Among the 7 programs in their list, BitDefender and Avast ranked the highest, both got 9 out of 10.

---

### Post by cdenley on 2010-02-26
> **Richiegs said:**
> 
I suspect they are mostly false positives. Because as soon as I delete them and restart the computer, I won't be able to log in.


I'm not sure which is better, but just because a file detected as a virus is required for you to login doesn't mean it was a false positive. Was this Windows that wouldn't let you login?

---

### Post by Richiegs on 2010-02-26
> **cdenley said:**
> I'm not sure which is better, but just because a file detected as a virus is required for you to login doesn't mean it was a false positive. Was this Windows that wouldn't let you login?


As soon as I detect a virus found by Avast and restart the PC, I won't be able to log in Ubuntu.

---

### Post by Richiegs on 2010-02-26
> **zeroseven0183 said:**
> Although most people will normally say 99.9% of your Linux use won't need an antivirus, it's always good and safe to have one. I don't use antivirus that often and haven't fully used ClamAV (or ClamTK if you will, currently installed on my machine) and Avast but I would say, both are good softwares.

To help you decide which of the two, or maybe some other, antivirus programs is better, this article from TuxRadar can help you: [Get the best virus scanner for Linux.]("http://www.tuxradar.com/content/get-best-virus-scanner-linux")

Among the 7 programs in their list, BitDefender and Avast ranked the highest, both got 9 out of 10.
 I want to try Bitdefender too. It has many different versions and I don't know which version I should download.

---

### Post by cdenley on 2010-02-26
> **Richiegs said:**
> As soon as I detect a virus found by Avast and restart the PC, I won't be able to log in Ubuntu.

What file is being detected as a virus which when removed prevents you from logging into ubuntu?

---

### Post by Richiegs on 2010-02-26
> **cdenley said:**
> What file is being detected as a virus which when removed prevents you from logging into ubuntu?

I don't remember the exact file name, but it usually includes the word Win. Most of the files are located in Ubuntu directory within Windows.

---

### Post by Martin Marshalek on 2010-02-26
There is an Ubuntu directory within Windows? Do you mean you are using Wubi? If yes than that could be the problem. By having Ubuntu on Wubi it is subject to the health of the Windows install i.e. if you have a virus and Windows is damaged, so is Ubuntu.

---

### Post by gallifrey on 2010-02-26
> **Richiegs said:**
> I want to try Bitdefender too. It has many different versions and I don't know which version I should download.

BitDefender for Linux and Unices is the one to go for if you want it for a home desktop system. Obviously, there is a server edition if you are running a server.

I have to warn you though, the BitDefender for Linux and Unices needs a reg key, which expires after 90 days.

---

### Post by Richiegs on 2010-02-26
> **Martin Marshalek said:**
> There is an Ubuntu directory within Windows? Do you mean you are using Wubi? If yes than that could be the problem. By having Ubuntu on Wubi it is subject to the health of the Windows install i.e. if you have a virus and Windows is damaged, so is Ubuntu.

Yes, I installed Ubuntu within Windows using Wubi. I guess when Avast scans, it will scan for viruses in the entire hard drive including Windows & Ubuntu.

---

### Post by Richiegs on 2010-02-26
> **gallifrey said:**
> BitDefender for Linux and Unices is the one to go for if you want it for a home desktop system. Obviously, there is a server edition if you are running a server.

I have to warn you though, the BitDefender for Linux and Unices needs a reg key, which expires after 90 days.

But there are many versions of BitDefender for Linux and Unices . I am using Ubuntu 9.10 in a 32-bit computer. Which version should I choose? Thanks

---

### Post by zeroseven0183 on 2010-02-26
Hi! Once you have the link sent to your e-mail, 

1. Click EN_FR_BR_RO/ then Linux/
2. And since you're using 32-bit, choose and download **BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.i586.deb.run** (40MB)
     *Note: You also have the option to download a non-GUI version.*
3. Open a Terminal and go to the directory where you downloaded the file
4. Type ```
sudo sh BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.i586.deb.run
```5. Enter your password
6. You will have to scroll down a bit until you reach the end of the License Agreement and type **accept**
7. When asked "Do you want to install BitDefender Antivirus Scanner GUI package? (Y/N)", type **y**

After the installalation, you will see **BitDefender Scanner** in **System Tools** < **Applications**.
Download the latest update, set a new key and you're good to go.

---

