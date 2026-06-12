---
title: "My first Wine app cannot find dlls, which are there."
date: 2010-12-21
forum: Wine
---

### Post by XEtedBear on 2010-12-21
Firstly, I have read and tried to follow YokoZar's directives in his 'Please read before posting' post.

I have installed Wine 1.2.2 under Ubuntu 10.10, using the Ubuntu Software Centre. I am using 64 bit Ubuntu - but I can't exactly remember if I had to do anything special to install WINE in this version.

For my first test I have installed the application "3D Home Architect V.6". Installation completed successfully - after I followed the instructions correctly! I can see, from winefcg, that it is installed. However, it cannot be invoked successfully. The terminal output has a large number of messages (too many to reproduce here) about 90% of which are of the form:
```
err:module:import_dll Library MSVCP71.dll (which is needed by L"C:\\Program Files\\3D Home Architect\\Home Design Deluxe 6\\Bin\\CsClassReg.dll") not found

```

However I see that most of these dlls are present in ~/.wine/dosdevices/c: - so why can't the application see them?

I have made just 1 modification to winecfg which is to add an override in the libraries tab for MSVCP71.dll with a 'loadorder' of 'builtin then native' - in an attempt to solve the problem. It made no difference.

I am using WinXP.

Versions 3 and 4 of this app. appear in the WINE application database with a 'Gold' classification, so I do have some confidence that Version 6 should run too.

Any suggestions on how to solve the problem?

---

### Post by dino99 on 2010-12-21
You may use the latest release: 1.3.9

[https://launchpad.net/~ubuntu-wine/+archive/ppa](https://launchpad.net/~ubuntu-wine/+archive/ppa)

then use winetricks to install your missing dll: vcrun2003

[http://appdb.winehq.org/objectManager.php?bIsQueue=false&bIsRejected=false&sClass=application&sTitle=Browse+Applications&iItemsPerPage=25&iPage=1&sOrderBy=appName&bAscending=true](http://appdb.winehq.org/objectManager.php?bIsQueue=false&bIsRejected=false&sClass=application&sTitle=Browse+Applications&iItemsPerPage=25&iPage=1&sOrderBy=appName&bAscending=true)

---

### Post by XEtedBear on 2010-12-21
> **dino99 said:**
> 
then use winetricks to install your missing dll: vcrun2003

[http://appdb.winehq.org/objectManager.php?bIsQueue=false&bIsRejected=false&sClass=application&sTitle=Browse+Applications&iItemsPerPage=25&iPage=1&sOrderBy=appName&bAscending=true](http://appdb.winehq.org/objectManager.php?bIsQueue=false&bIsRejected=false&sClass=application&sTitle=Browse+Applications&iItemsPerPage=25&iPage=1&sOrderBy=appName&bAscending=true)

Thanks. I installed wine1.3 from PPA through the software centre, but I'm afraid I'm too old and stupid to appreciate the signiifcance of your reference to the application databse. It takes me to the first of 931 pages, allowing me to search. A search on either 'winetricks' or 'vcrun2003' returns zero hits.

What am I looking for?

---

### Post by XEtedBear on 2010-12-21
> **dino99 said:**
> 

then use winetricks to install your missing dll: vcrun2003



```

tony@advent:~$ sh winetricks
sh: Can't open winetricks
tony@advent:~$ 

```

A search in Nautllus fails to find any file with name starting with 'winetricks' anywhere on my system.

An examination of installed software through Ubuntu Software Centre shows that winetricks is installed.

Huh?

---

### Post by dino99 on 2010-12-22
before using something, you have to install it first of course :)

open synaptic and install winetricks

---

### Post by XEtedBear on 2010-12-22
> **dino99 said:**
> before using something, you have to install it first of course :)

open synaptic and install winetricks

Yes, of course - but, having been told by Ubuntu Software Centre that winetricks was already installed (green check mark included!), I didn't think it needed to be installed a second time. Obviously it does - because that fixed the problem.

Thanks.

---

