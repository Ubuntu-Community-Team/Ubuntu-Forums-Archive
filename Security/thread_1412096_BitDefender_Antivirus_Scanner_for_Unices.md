---
title: "BitDefender Antivirus Scanner for Unices"
date: 2010-02-20
forum: Security
---

### Post by Richiegs on 2010-02-20
Hi, I am using Ubuntu 9.10 and I want to download BitDefender Antivirus Scanner for Unices. Nevertheless, BitDefender Antivirus Scanner for Unices has many different versions, such as 
1. BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.amd64.deb.run
2. BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.amd64.deb.run.md5
3. 	BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.i586.deb.run
4. BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.i586.deb.run.md5
5. 	BitDefender-Antivirus-Scanner-nogui-7.6-4.linux-gcc3x.i586.deb.run
6. 	BitDefender-Antivirus-Scanner-nogui-7.6-4.linux-gcc3x.i586.deb.run.md5

Which one should I download?

Thank you

---

### Post by uRock on 2010-02-20
Are you using 64bit or 32bit? If using [COLOR="Red"]64bit[/COLOR], then get the one with ADM64 in it and [COLOR="Blue"]vice versa[/COLOR].

> **Richiegs said:**
> 
1. [COLOR="Red"]BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.amd64.deb.run[/COLOR]
3. [COLOR="Blue"]BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.i586.deb.run[/COLOR]

---

### Post by Richiegs on 2010-02-20
I am using 32 bit.

---

### Post by Ozymandias_117 on 2010-02-20
Then you want:

BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.i586.deb.run

---

### Post by Richiegs on 2010-02-20
> **Ozymandias_117 said:**
> Then you want:

BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.i586.deb.run
My PC can't run that version.

---

### Post by uRock on 2010-02-20
There's always Ubuntu.

---

### Post by Richiegs on 2010-02-21
> **iRock said:**
> There's always Ubuntu.

Is there a Debain version for Ubuntu 9.10?

---

### Post by uRock on 2010-02-21
The 32 bit version you were trying to install works with 32bit Debian.

---

### Post by Richiegs on 2010-05-07
> **uRock said:**
> The 32 bit version you were trying to install works with 32bit Debian.

After I downloaded Bitedefender, how do I run it? It would not run by double clicking it.

---

### Post by CharlesA on 2010-05-07
It should have asked if you wanted to install a GUI package.

---

### Post by cariboo on 2010-05-07
You have to make the file executable, cd into the directory the file is in for example if you have the file on your desktop:

```
cd ~/Desktop
```

them make the file executable:

```
chmod +x ./*run
```

then run the file:

```
sudo ./*run
``` 

The above commands may just extract the .deb, so once it is extracted, just double click it, gdebi should open up and allow you to install it.

---

### Post by nanohead on 2010-05-07
If Bit defender doesn't work, I've had really good luck using Avast Linux.  Its not a real time resident filter driver, but you can keep it running and make it do a scan on schedule.....

---

### Post by Soul-Sing on 2010-05-07
it is self extracting, so when you have extract the .deb file
```
sudo dpkg -i BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.i586.deb
```

---

### Post by Richiegs on 2010-05-07
> **cariboo907 said:**
> You have to make the file executable, cd into the directory the file is in for example if you have the file on your desktop:

```
cd ~/Desktop
```them make the file executable:

```
chmod +x ./*run
```then run the file:

```
sudo ./*run
```The above commands may just extract the .deb, so once it is extracted, just double click it, gdebi should open up and allow you to install it.

Thank you so much for your help. I finally was able to install it successfully. My 5-year-old PC is a 32-bit Intel-based. For unknown reason  I could not install BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.i586.deb.run.  Nevertheless, installing BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.amd64.deb.run was fine. Anyone knows why I had to use AMD 64 bits Bitdefender?

---

### Post by cariboo on 2010-05-07
Probably because you are running the 64-bit version of Ubuntu. To check, open a terminal and type:

```
uname -a
```

the output should look something like this:

```
Linux alexis 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 **x86_64** GNU/Linux
```

I've bolded the important part.

---

