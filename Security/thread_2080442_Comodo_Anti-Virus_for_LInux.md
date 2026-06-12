---
title: "Comodo Anti-Virus for LInux"
date: 2012-11-04
forum: Security
---

### Post by aligator12 on 2012-11-04
Hey folks, I found this:
comodo.com/home/internet-security/antivirus-for-linux.php

It looks pretty good, I was just wondering if you guys could tell me if it is known to cause any bugs, serious slowdowns, etc.

---

### Post by aligator12 on 2012-11-04
I went ahead and installed it and works pretty good. But I was wondering if I use [http://en.wikipedia.org/wiki/EICAR_test_file](http://en.wikipedia.org/wiki/EICAR_test_file) is it safe?

---

### Post by KaosuX on 2012-11-04
> **aligator12 said:**
> Hey folks, I found this:
comodo.com/home/internet-security/antivirus-for-linux.php

It looks pretty good, I was just wondering if you guys could tell me if it is known to cause any bugs, serious slowdowns, etc.

Running anti-virus software on a GNU/Linux desktop is rather pointless. I mean, it can be useful if you're dual-booting and you would like to scan your Windows partition for malware. However, anti-virus products for Linux detect mostly Windows threats. You really only need anti-virus protection if you're acting as a gateway, mail server, etc. for Windows clients.

At the end of the day, I would not waste my resources running the software. However, if you're actively networking with Windows clients, have a Windows partition then at least you get the small benefit of being able to detect malware that would otherwise infect your Windows partition/clients. However, even then you're better off installing an anti-virus product on the Windows installation and allowing your GNU/Linux desktop to free up more resources for computing instead of running software it really does not require.

Also, yes. The EICAR test file is safe. It is literally just a string that is detected by every standard anti-virus to ensure it is working correctly.

Just create a new text file and place the following text in it: X5O!P%@AP[4\PZX54(P^)7CC)7}$EICAR-STANDARD-ANTIVIRUS-TEST-FILE!$H+H*

Now, save the file and try to scan it. If your anti-virus is correctly configured it will detect the test string.

It is technically executable code. However, you can simply save it as a text document and then it won't be executable by the system. However, your anti-virus is still capable of detecting the string.

---

### Post by sammiev on 2012-11-04
I use Bitdefender and had a hit about 6 months back in Linux. So I decided to test it with the string provided by the above post. It found it but I did not clear it to see what it would suggest if I tried to close the virus program down. I included some pics. :)

---

### Post by Abhinav Kumar on 2012-11-04
> **KaosuX said:**
> Running anti-virus software on a GNU/Linux desktop is rather pointless. I mean, it can be useful if you're dual-booting and you would like to scan your Windows partition for malware. However, anti-virus products for Linux detect mostly Windows threats. You really only need anti-virus protection if you're acting as a gateway, mail server, etc. for Windows clients.

At the end of the day, I would not waste my resources running the software. However, if you're actively networking with Windows clients, have a Windows partition then at least you get the small benefit of being able to detect malware that would otherwise infect your Windows partition/clients. However, even then you're better off installing an anti-virus product on the Windows installation and allowing your GNU/Linux desktop to free up more resources for computing instead of running software it really does not require.

Also, yes. The EICAR test file is safe. It is literally just a string that is detected by every standard anti-virus to ensure it is working correctly.

Just create a new text file and place the following text in it: X5O!P%@AP[4\PZX54(P^)7CC)7}$EICAR-STANDARD-ANTIVIRUS-TEST-FILE!$H+H*

Now, save the file and try to scan it. If your anti-virus is correctly configured it will detect the test string.

It is technically executable code. However, you can simply save it as a text document and then it won't be executable by the system. However, your anti-virus is still capable of detecting the string.
+1 for the reply of KaosuX.
The biggest advantage of using linux is that it saves a quite a bit of hardware resource ( as anti-virus programs are not needed) unless you are involved in networking. :)

---

