---
title: "Cannot enable dhcp3-server"
date: 2017-05-15
forum: Ubuntu/Debian BASED
---

### Post by asktolearn on 2017-05-15
Dears , 

   I searched & spent time trying to find how to enable dhcp3-server but still cannot find any real solvent .

After typing " apt-get install dhcp3-server -y"
I get that error :

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package dhcp3-server

& That is my source list :



#deb [arch=i386,amd64,armel,armhf] [http://http.kali.org/kali](http://http.kali.org/kali) kali-dev main/debian-installer

#deb-src [http://http.kali.org/kali](http://http.kali.org/kali) kali-dev main contrib non-free

#deb [arch=i386,amd64,armel,armhf] [http://http.kali.org/kali](http://http.kali.org/kali) kali main contrib non-free

#deb [arch=i386,amd64,armel,armhf] [http://http.kali.org/kali](http://http.kali.org/kali) kali main/debian-installer

#deb-src [http://http.kali.org/kali](http://http.kali.org/kali) kali main contrib non-free

#deb [arch=i386,amd64,armel,armhf] [http://security.kali.org/kali-security](http://security.kali.org/kali-security) kali/updates main contrib non-free

#deb-src [http://security.kali.org/kali-security](http://security.kali.org/kali-security) kali/updates main contrib non-free

#deb [http://repo.kali.org/kali](http://repo.kali.org/kali) kali-bleeding-edge main

#deb-src [http://repo.kali.org/kali](http://repo.kali.org/kali) kali-bleeding-edge main

#deb [http://http.kali.org/kali](http://http.kali.org/kali) kali main non-free contrib

#deb [http://security.kali.org/kali-security](http://security.kali.org/kali-security) kali/updates main contrib non-free

#deb-src [http://http.kali.org/kali](http://http.kali.org/kali) kali main non-free contrib

#deb-src [http://security.kali.org/kali-security](http://security.kali.org/kali-security) kali/updates main contrib non-free

#deb cdrom:[Debian GNU/Linux 7.0 _Kali_ - Official Snapshot i386 LIVE/INSTALL Binary 20130425-11:12]/ kali contrib main non-free

#deb cdrom:[Debian GNU/Linux 7.0 _Kali_ - Official Snapshot i386 LIVE/INSTALL Binary 20130425-11:12]/ kali contrib main non-free


#deb [http://security.kali.org/kali-security](http://security.kali.org/kali-security) kali/updates main contrib non-free


#deb [http://http.kali.org/kali](http://http.kali.org/kali) kali-rolling main contrib non-free


#deb cdrom:[Debian GNU/Linux 2016.1 _Kali-rolling_ - Official Snapshot amd64 LIVE/INSTALL Binary 20160830-11:29]/ kali-rolling contrib main non-free

#deb cdrom:[Debian GNU/Linux 2016.1 _Kali-rolling_ - Official Snapshot amd64 LIVE/INSTALL Binary 20160830-11:29]/ kali-rolling contrib main non-free


#deb [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org)



So if you can help me I`d be really grateful , Cuz I started to be hopless to solve that problem .

Thank You

---

### Post by howefield on 2017-05-15
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by asktolearn on 2017-05-17
Is it no solvent !! :(

---

### Post by howefield on 2017-05-17
Your question might be better asked in the Kali linux forums but looking at your first posting, all the sources in your sources.list file appear to be commented out.

The error you are seeing with the  dhcp3-server package generally means that it doesn't exist in the sources that you are querying or that you have the wrong package name.

Just to see if you have any non commented out repositories can you post the output of 

```
egrep -v '^#|^ *$' /etc/apt/sources.list /etc/apt/sources.list.d/*
```

even if it outputs nothing.

---

