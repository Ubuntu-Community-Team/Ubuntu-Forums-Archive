---
title: "Cannot print in ubuntu 17.10"
date: 2017-09-19
forum: Ubuntu Development Version
---

### Post by jsjpandey on 2017-09-19
I have recently updated my ubuntu 17.10 but after updating the printer stops working

---

### Post by kc1di on 2017-09-19
Hello jsjpandey And Welcome to Ubuntu Linux Forums, 

You'll need to gives us a little more information on the setup- So we can help you.
Which printer - What system is being used wireless - direct connect, ETC.

---

### Post by jsjpandey on 2017-09-19
I am using HP Deskjet 3830 connected to cpu through usb cable. I have checked it in windows and printer doesn't have any problem nor the cable.

---

### Post by slickymaster on 2017-09-19
Thread moved to **Hardware** for a better fit

---

### Post by jsjpandey on 2017-09-19
Its a software problem not hardware one and the most probably the  problem is with CUPS or HP-LIPS, these are the things I know but I don't  know how to solve this problem.

---

### Post by kc1di on 2017-09-19
Again more info so we can diagnose the problem  Which Hp printer is hplip installed, if so which version?
Which version of cups.  
how did you try to install the printer - is it wireless?
We can't be of much help without info.

you also may want to install hplip-gui and install your printer from there.

---

### Post by jsjpandey on 2017-09-19
My cups version is 2.2.4 and hplip version is 3.17.7, while my hp is connected by usb.

---

### Post by kc1di on 2017-09-19
That still doesn't tell us what you printer is.
Go to a terminal and type [HTML]sudo apt-get install hplip-gui[/HTML]
when it finishes go to menu and search for ```
hp tool box
```
install the printer via that tool. 
alternatively you can type the following in a terminal and install printer according to the prompts. 
```
hp-setup
```

---

### Post by slickymaster on 2017-09-19
> **jsjpandey said:**
> Its a software problem not hardware one and the most probably the  problem is with CUPS or HP-LIPS, these are the things I know but I don't  know how to solve this problem.

The Hardware sub-forum is for any type of issues relating problems getting your hardware to work with Ubuntu

---

### Post by jsjpandey on 2017-09-19
With Hp-toolbox even the printing is not working, although the scanning is working fine.

---

### Post by kc1di on 2017-09-19
You still haven't told us what printer you using?
Without that information it's hard to help you.

---

### Post by jsjpandey on 2017-09-19
I have told it earlier now again I am telling it is HP Deskjet 3830

---

### Post by slickymaster on 2017-09-19
Moving this one to the** Ubuntu Development Version** sub-forum now, as I didn't noticed earlier that the OP was using 17.10

---

### Post by Chanath on 2017-09-19
> **jsjpandey said:**
> My cups version is 2.2.4 and hplip version is 3.17.7, while my hp is connected by usb.

Have you had a look here, [http://hplipopensource.com/hplip-web/index.html?](http://hplipopensource.com/hplip-web/index.html?) The current version of 3.17.9.

---

### Post by kc1di on 2017-09-19
Sorry missed the printer in your other post. 
This is what I would do remove hplip and then install it again. 

the reinstall the printer using hplip-tool box.

see if that will work for you.

---

### Post by pdc on 2017-09-19
this printer; the **HP Deskjet Ink Advantage 3830 e-All-in-One Printer** ..... is an APPLE PRINT COMPATIBLE printer [https://support.apple.com/en-nz/HT201311](https://support.apple.com/en-nz/HT201311)

Apple Print Support was built into 17.04 Ubuntu; I don't know the details of its implementation but my understanding was this would save installing drivers; so one assumes it is also in 17.10 (the development issue)

________________________

**[SIZE=4]Which version of hplip is adequate?  [/SIZE]**         if one looks on the HP's hplip site, then 3.15.4 is fine [http://hplipopensource.com/hplip-web/models/deskjet_aio/deskjet_3830_series.html](http://hplipopensource.com/hplip-web/models/deskjet_aio/deskjet_3830_series.html) so what is installed already is fine:

____________________

two commands HP recommend are ```
hp-check
``` and ```
hp-setup
```

---

### Post by jbicha on 2017-09-19
Please see [bug 1718215]("https://launchpad.net/bugs/1718215").

---

### Post by jsjpandey on 2017-09-20
Please see [bug 1718215]("https://launchpad.net/bugs/1718215") is really the issue which is now solved.

---

### Post by rrnbtter on 2017-09-20
Greetings,
sudo apt-get app-install-data

Install your printer from the Gnome Print Manager.
Under Details choose Search for Driver.  
If it grays out after the search you are done.

---

