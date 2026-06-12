---
title: "Oblivion won't install"
date: 2009-04-11
forum: Wine
---

### Post by Mikeybz2 on 2009-04-11
I've Downloaded Wine from the add/remove applications and i'm now trying to install Oblivion. I'm able to install and run other programs but it won't install Oblivion. It won't bring up an installer or anything i right click on ther launcher and the setup to install in wine but nothing at all happens. Its like i did nothing at all any help would be grateful

---

### Post by RaiCoss on 2009-04-11
I'm guessing your using WINE 1.01. You may want to post your Ubuntu version (8.04, 8.10 etc...) and your system specs.

---

### Post by Mikeybz2 on 2009-04-11
im using ubuntu intrepid i have an amd sempron 3000+ 1gb ram nvida 6600 256mb

---

### Post by RaiCoss on 2009-04-11
Do you click setup.exe on the Oblivion disc?

---

### Post by Simian Man on 2009-04-11
cd to the cd drive and type
```
wine setup.exe
```

And see if gives you any useful output.

---

### Post by Mikeybz2 on 2009-04-11
this is what i got although i'm not sure what cd to cd the drive is. I'm super new to Ubuntu like 5 days old so you might have to be very descriptive until i get the hang of it.
wine: could not load L"C:\\windows\\system32\\setup.exe": Module not found

---

### Post by RaiCoss on 2009-04-11
setup.exe in system 32??

Ok try this.

Insert the Oblivion DVD. Right click on the Oblivion icon and choose "Open"
You should see a bunch of files. Find one called "setup.exe" and double click it, see what happens.

---

### Post by Mikeybz2 on 2009-04-11
before nothing at all would happen now since I've been on different sites and tried different things the default wine desktop opens up but it just stays on a blue screen... sorta like the blue screen of death(i like ubuntu i don't like blue screens of death) when i installed dx it opened up in there but oblivion does nothing

---

### Post by Mikeybz2 on 2009-04-14
I am still stuck in the same spot any help would be great.....come on guys plz don't force me to keep using winxxxx

---

### Post by Therion on 2009-04-14
Read your PM.  

Also read this:  [http://www.uesp.net/wiki/Oblivion:Linux](http://www.uesp.net/wiki/Oblivion:Linux)

---

### Post by Simian Man on 2009-04-14
> **Mikeybz2 said:**
> when i installed dx it opened up in there but oblivion does nothing

You shouldn't install dx under wine, it has its own implementation.  And read the link Therion posted and follow it line by line.

---

### Post by el Tedward on 2009-05-02
I'm having the same issue as well.. I tried running the setup.exe through the terminal and just got this:

```
fixme:ntdll:NtQueryInformationProcess (0xffffffff,info_class=34,0xeda520,0x00000004,0xeda51c) Unknown information class
```

---

