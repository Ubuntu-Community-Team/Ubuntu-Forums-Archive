---
title: "Maya users"
date: 2007-06-02
forum: The Cafe
---

### Post by tocky on 2007-06-02
I was wondering what kind of distribution Maya users use, since at least I feel that Maya doesn't work properly under Ubuntu, so i wonder if you got it working flawlessly or you use other distributions in order to satisfy Maya. Other distributions that I'm thinking about trying is, PCLinux OS, OpenSuse and Fedora. Do they have better compability with Maya?

---

### Post by v8YKxgHe on 2007-06-02
When I run Maya in Ubuntu it seems to work great, better than on Windows I'd say. What is it that doesn't work?

---

### Post by mech7 on 2007-06-02
It does run ok with me on Ubuntu some bugs though.. but i suspect it has more to do with my ATI card.. I think best bet if you are going to use it allot is to grab a supported distro like RedHat or SUSE. Something which can install RPM nativly.

---

### Post by tocky on 2007-06-02
Well, the shelfs are missing which is very bad. But most of all, the performance is outrageous, even though my pc isn't in fact an monster, still Maya does perform a lot better in Windows XP with the same hardware.

Don't you have these problems?

---

### Post by Engnome on 2007-06-02
> **tocky said:**
> I was wondering what kind of distribution Maya users use

Windows XP 64bit   = /

Tried with ubuntu, not worth the effort IMHO. (YMMV)

EDIT: The big maya thread: [http://ubuntuforums.org/showthread.php?t=66859](http://ubuntuforums.org/showthread.php?t=66859)

---

### Post by mech7 on 2007-06-02
> **tocky said:**
> Well, the shelfs are missing which is very bad. But most of all, the performance is outrageous, even though my pc isn't in fact an monster, still Maya does perform a lot better in Windows XP with the same hardware.

Don't you have these problems?

Shelves work with me.. but indeed i run under XP x64 too.. performance is not less with me under ubuntu if any it's faster.  but the interface in linux is buttugly :(

---

### Post by Engnome on 2007-06-02
> **mech7 said:**
> but the interface in linux is buttugly :(

Yes, uses OpenMotif IIRC.

---

### Post by tocky on 2007-06-02
> **mech7 said:**
> Shelves work with me.. but indeed i run under XP x64 too.. performance is not less with me under ubuntu if any it's faster.  but the interface in linux is buttugly :(

Well how did you install Maya, I did exactly as the tutorial shows on these forums, and I got Maya to work, but the speed and my shelfs are missing. I'm now downloading Fedora, as it should be compatible with Maya.

---

### Post by mech7 on 2007-06-02
> **tocky said:**
> Well how did you install Maya, I did exactly as the tutorial shows on these forums, and I got Maya to work, but the speed and my shelfs are missing. I'm now downloading Fedora, as it should be compatible with Maya.

Yup just installed it same way as in the tut.. i did need to change something in the .env file for the cursor and i had to set a dir to writable for mentalray.

---

### Post by mech7 on 2007-06-02
Btw to add.. use proper drivers the default ones have crap 3d support, and also the Shelves where hidden by me at default show i had to turn them on ;)

---

### Post by tocky on 2007-06-02
If you mean the nvidia drivers, then I do use them, but I'll check into the shelfs.

---

### Post by tocky on 2007-06-03
I've now got it to work much faster, I reinstall ubuntu 7.04 from scratch, and then installed maya again, and now it works fast, plus that I got the shelfs (thanks for the tip!).

One more question though, when I use maya, my cursor changes to an ugly black X, which stays until I reboot or restart the x-server. Do you have the same problem, can it be fixed somehow?

Cheers

---

### Post by tocky on 2007-06-03
And also how to you rotate the view? Alt + rmb doesn't work

---

### Post by mech7 on 2007-06-03
> **tocky said:**
> And also how to you rotate the view? Alt + rmb doesn't work

Set the alt key System -> Preferences -> Windows and change alt to Super (windows key) for example..

For the black cursor edit Maya.env and put in: MAYA_MMSET_DEFAULT_XCURSOR=1

Also you need to chmod a tmp dir to 777 for maya for mental ray don't remember which one but it is in the manuel :)

---

