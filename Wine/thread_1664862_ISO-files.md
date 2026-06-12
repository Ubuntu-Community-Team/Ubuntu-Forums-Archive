---
title: "ISO-files"
date: 2011-01-11
forum: Wine
---

### Post by DjIceman on 2011-01-11
Hi everybody, 

I just started using Ubuntu, so I am a noob at this. I was wondering how you guys open an *.iso file? Do you do it with wine? PlayOnLinux? Because these things didn't work out for me..

If you can offer me any help, I would be very grateful.

Grtz, Iceman

---

### Post by Simian Man on 2011-01-11
What are you trying to do?  Install illegally pirated Windows games?

---

### Post by spydeyrch on 2011-01-11
Well, what is it your are trying to do with the.iso?

-Spydey

---

### Post by BbUiDgZ on 2011-01-11
right click > extract here

you might want to [read up](http://en.wikipedia.org/wiki/ISO_image) on what an "iso" file is

---

### Post by Barrucadu on 2011-01-11
Heh, I remember the first time I extracted an ISO file a self-named "computer expert" told me off rather vehemently, saying that doing so would break Windows and I was very lucky it did not.

To mount an ISO you can use the following command:
```
sudo mount /path/to/file.iso /path/to/mountpoint -t iso9660 -o loop
```

---

### Post by DjIceman on 2011-01-11
> **Simian Man said:**
> What are you trying to do?  Install illegally pirated Windows games?

No, no illegal software. I don't like putting the cdrom in my drive every time I need to install something and I have a home storage server so everything I have is on that. If I was trying to install illegal software, I wouldn't be posting it here :-)

> **spydeyrch said:**
> Well, what is it your are trying to do with the.iso?

-Spydey
See above. Just install my programs. 

> **BbUiDgZ said:**
> right click > extract here

you might want to [read up](http://en.wikipedia.org/wiki/ISO_image) on what an "iso" file is
So I would have to extract it first and then use the extracted install.exe? 


> **Barrucadu said:**
> Heh, I remember the first time I extracted an ISO file a self-named "computer expert" told me off rather vehemently, saying that doing so would break Windows and I was very lucky it did not.

To mount an ISO you can use the following command:
```
sudo mount /path/to/file.iso /path/to/mountpoint -t iso9660 -o loop
```
Thanks, I'll try this later.

---

### Post by Simian Man on 2011-01-11
> **DjIceman said:**
> No, no illegal software. I don't like putting the cdrom in my drive every time I need to install something and I have a home storage server so everything I have is on that. If I was trying to install illegal software, I wouldn't be posting it here :-)

Cool, you'd be surprised how much illegal stuff people post here.  Barrucadu gave you the correct answer, I just didn't want to post it if you'd use the info for questionable purposes :).

---

### Post by marin123 on 2011-01-11
right-click -> open with archive MOUNTER or something like that saves you typing... then it acts like cd-rom, and later on, you can of course eject it :)

---

### Post by ppv on 2011-01-11
> **DjIceman said:**
> 
So I would have to extract it first and then use the extracted install.exe? 

Thanks, I'll try this later.


You mean you wanting to run install.exe on Ubuntu. If yes, then it is not going to run. .exe files are meant for Windows.

---

### Post by DjIceman on 2011-01-11
> **ppv said:**
> You mean you wanting to run install.exe on Ubuntu. If yes, then it is not going to run. .exe files are meant for Windows.

I read about some people who had MS Office 2007 installed on Ubuntu.. An .exe file was used to make this install possible, so I think it is possible actually? :-)

---

### Post by cgroza on 2011-01-11
> **Barrucadu said:**
> Heh, I remember the first time I extracted an ISO file a self-named "computer expert" told me off rather vehemently, saying that doing so would break Windows and I was very lucky it did not.

To mount an ISO you can use the following command:
```
sudo mount /path/to/file.iso /path/to/mountpoint -t iso9660 -o loop
```

Why do we have to do it this way, there is software for this in the Ubuntu Software Centre!

---

