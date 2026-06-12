---
title: "Kolab 2.2 on Ubuntu 8.04"
date: 2008-06-10
forum: Server Platforms
---

### Post by Hazardr on 2008-06-10
Any1 try this yet? 

i managed to install it and configure, can access admin page to create users but cannot log onto horde. My domain doesnt create in Var/imapd/spool. Kolab supposed to create a Domain folder with my domain but it just doesnt. I suspect its postfix. I have Kolab installed on Impi Linux but theres a dummy mail transport agent which prevents postfix from being installed. Is there a way to do this in Kolab 2.2? i want to use Kolabs settings so that i can use the SMTP of my ISP.

Thankx

---

### Post by HermanAB on 2008-06-10
I have never managed to get Kolab to work.  It seems to be extremely immature.  I suggest you use Citadel instead.

---

### Post by Hazardr on 2008-06-11
ive installed citadel and played with it but i still feel that kolab is better or me... is there no way of making it work? i get it to compile perfectly...its just the part where i have to do apt-get install kolabd... that messes up kolab coz it installes postfix. is there no way to install all required packages except postfix. On impi, theres a mail transport agent dummy that prevents postfix from being installed. If i can do the same on Ubuntu, i can get Kolab to work.

---

### Post by HermanAB on 2008-06-11
You can either uninstall postfix or just disable the master daemon.  However, I think Kolab simply isn't mature enough for serious use. Citadel is prehistoric ancient and rock solid stable.  For a mail server, stability is very important else you can lose everybody's mail.

---

### Post by Hazardr on 2008-06-11
I have used Citadel and kolab and i am not happy with citadel. Kolab is quite stable and one installed it is so easy to use and configure. i cant uninstall postfix as it uninstalls other applications. Also, i cant stop the daemon as once it is installed, it overwrites settings for kolab. i need to be able to install kolabd without installing the actual postfix program like i have on Impi linux

---

### Post by ludda512 on 2008-09-03
I have managed to get kolab to work on 8.04 server.  However, I did not utilize the packages from Ubuntu.  I went directly to kolab and installed there package.  simple to do!  It utilizes openpkg and all is contained in a directory called kolab.  I have tried the packages before and never got it to work.  However, I have had much success with the openpkg option. I have never tried to install without postfix.

---

