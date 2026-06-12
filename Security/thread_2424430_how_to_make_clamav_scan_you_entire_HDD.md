---
title: "how to make clamav scan you entire HDD"
date: 2019-08-08
forum: Security
---

### Post by jedi123 on 2019-08-08
Hi Folks, 

-How do I make clamAV scan my entire HDD ?  

 -As well, in  ubuntu 18.04. If I  accidentally open a malicious file, and then close my computer, _does the threat stay persistent in Ubuntu  18.04_  , like a metasploit ceafted file? 




I feel like a bit of a fool. I am not that handy with linux, and I  may have opened a malicious file, but then only scanned the  dektop, did not know how to scan whole computer.  Finally wiped HDD, like 2  weeks later  after pontificating my possible mistake.

---

### Post by SeijiSensei on 2019-08-08
[https://help.ubuntu.com/community/ClamAV](https://help.ubuntu.com/community/ClamAV)

In particular

"Use clamscan to check nearly all files on the computer, and report only warnings and infections:"

```
sudo clamscan --max-filesize=3999M --max-scansize=3999M --exclude-dir=/sys/* -i -r /
```

---

### Post by jedi123 on 2019-08-08
Thanks ,  for the response. 

Are all Ubuntu trojan horses like metasploit persistent or do they stop once you reboot? 

Thanks.

---

### Post by SeijiSensei on 2019-08-08
I have no idea. I never have had any of that kind of stuff on any machine I've used.

I suggest posting a separate thread in the Security forum on just that issue.

---

### Post by jedi123 on 2019-08-09
Ok, thats fine. Can you tell me though: , 

-Can Windows trojan Horses or malware effect Linux systems ? 
-Can  Mac OS  trojan Horses  or malware efect Linux systems? 

Thanks.

---

### Post by sevendogs1337 on 2019-08-09
As far as windows, no - different binaries. Mac OS is unix-like but the binaries are different so I would also say no. Metasploit creates exploits, not viruses, FYI.

---

### Post by jedi123 on 2019-08-09
I know , that is why I used language like malicious file malware . 

Typically if a metasploit exploit is disguised as a torrent file or a .part file . It ( the malicious crafted metasploit file that target opens ) has to be for a specific OS , meaning the exploit crafter is forced to make a choice  windows , Mac  or Linux  correct ?



I am asking because I have 2 computers computer #1 banking email serious stuff 

computer #2 : torrent etc . Both are Ubuntu, 
But seldom run clamav because download issues version issue update issues confit etc.
I accidentally did banking on computer 2 realized my mistake  then wipe HDD 2 weeks after .i feel stupid because I pride myself on security.

---

### Post by sevendogs1337 on 2019-08-09
I use metasploit to find exploits, not create them for distribution.

---

### Post by jedi123 on 2019-08-09
> **sevendogs1337 said:**
> I use metasploit to find exploits, not create them for distribution.


But you must know as a security researcher or it worker if the crafter has to make a choice on which OS the exploit will work on when building malicious files right

---

### Post by sevendogs1337 on 2019-08-09
Yes, sorry, forgot to include that part - target OS needs to be specified, if it is an OS exploit.

---

### Post by jedi123 on 2019-08-09
> **sevendogs1337 said:**
> Yes, sorry, forgot to include that part - target OS needs to be specified, if it is an OS exploit.


If one deletes the offending exploit  file, that was clicked on,  does the malware still persist on your computer ---in a linux environment ? I know in windows it persists and moves around. 

Thanks.

---

### Post by jedi123 on 2019-08-10
bump

---

### Post by dagmann on 2019-10-11
some clamav information here

[https://kifarunix.com/how-to-install-and-use-clamav-antivirus-on-ubuntu-18-04/](https://kifarunix.com/how-to-install-and-use-clamav-antivirus-on-ubuntu-18-04/)

---

### Post by uRock on 2019-10-11
> **jedi123 said:**
> If one deletes the offending exploit  file, that was clicked on,  does the malware still persist on your computer ---in a linux environment ? I know in windows it persists and moves around. 

Thanks.

Since it is a Windows virus, it is nothing but a dormant file on Linux. Deleted means deleted in Linux.

---

