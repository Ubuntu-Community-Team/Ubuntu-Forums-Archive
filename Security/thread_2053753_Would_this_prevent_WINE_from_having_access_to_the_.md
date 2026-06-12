---
title: "Would this prevent WINE from having access to the internet?"
date: 2012-09-06
forum: Security
---

### Post by aligator12 on 2012-09-06
Hay, I have some programs I want to run in WINE and I don't want them calling home. If I create a separate user account and disable the internet connection for it, would WINE be able to access the internet at all?

---

### Post by Stonecold1995 on 2012-09-07
If Wine is running under an account that has no internet access, then you are correct, Wine will be unable to connect to the internet.  You could create a user called "safewine" or something, and then if you ever want to run a Windows program just run:
```
sudo -u safewine wine cool_program.exe
```

If there's a specific IP you don't want the program to phone home to, you can use iptables to block it (see [here]("https://help.ubuntu.com/community/IptablesHowTo")).  For example, if you don't want Adobe Photoshop to phone home, run this in terminal:
```
iptables -A INPUT -s 192.150.16.117 -j DROP
```
That would block all connections to 192.150.16.117, which is adobe.com (so it would prevent Photoshop from communicating with Adobe, but it would also prevent you from going to adobe.com yourself).

Do you want the program to avoid phoning home because it may be malicious (e.g. a RAT or bot), or because you don't want the creators to know (e.g. a cracked application) or because it causes errors (e.g. some program that freezes under Wine if it tries to update itself, and you have no way to turn automatic updates off)?  If it's potentially malicious, run it in VirtualBox because you don't want any chance that it infects your system.  If it's warez or something illegal like that, I doubt you'll get much help from Ubuntu Forums, so try something like [SuperBay]("http://forum.suprbay.org") instead (you may get an expired SSL certificate warning, but the site is safe).  If the program has problems when it tries to connect to the internet, then block the IP with iptables if you know what that IP is, otherwise yes, using a user account without internet would work.

---

### Post by jerome1232 on 2012-09-07
> **Stonecold1995 said:**
> If Wine is running under an account that has no internet access, then you are correct, Wine will be unable to connect to the internet.  You could create a user called "safewine" or something, and then if you ever want to run a Windows program just run:
```
sudo -u safewine wine cool_program.exe
```If there's a specific IP you don't want the program to phone home to, you can use iptables to block it (see [here]("https://help.ubuntu.com/community/IptablesHowTo")).  For example, if you don't want Adobe Photoshop to phone home, run this in terminal:
```
iptables -A INPUT -s 192.150.16.117 -j DROP
```That would block all connections to 192.150.16.117, which is adobe.com (so it would prevent Photoshop from communicating with Adobe, but it would also prevent you from going to adobe.com yourself).


Slight correction, blocking INPUT won't stop an application from calling home, you would need to block OUTBOUND connections.

---

### Post by Stonecold1995 on 2012-09-07
> **jerome1232 said:**
> Slight correction, blocking INPUT won't stop an application from calling home, you would need to block OUTBOUND connections.

Oh my mistake, sorry.

```
iptables -A INPUT -s 192.150.16.117 -j DROP
iptables -A OUTPUT -s 192.150.16.117 -j DROP
/sbin/service iptables save
```

---

### Post by aligator12 on 2012-09-08
Thanks for the replies. The reason I don't want it to phone home is because it is known to have adware, but I heard it doesn't really matter if it is run in Wine. And my computer is not powerful enough to run anything in vb.

I have thought about dual booting and not connecting windows to the internet, I might do that. But the application in question gets a platinum rating at the appdb.

So I created an another account and installed wine in that one, but apparently wine installed system wide. Is there any way to prevent a system wide install?

---

### Post by jerome1232 on 2012-09-08
> **aligator12 said:**
> Thanks for the replies. The reason I don't want it to phone home is because it is known to have adware, but I heard it doesn't really matter if it is run in Wine. And my computer is not powerful enough to run anything in vb.

I have thought about dual booting and not connecting windows to the internet, I might do that. But the application in question gets a platinum rating at the appdb.

So I created an another account and installed wine in that one, but apparently wine installed system wide. Is there any way to prevent a system wide install?

  Downloadthe source code, compile yourself and install it to a location in that users home. I'm not sure if winehq supplies pre-compiled binaries that you can simply copy to that users home or not, you'd have to poke around their page a bit.

---

### Post by aligator12 on 2012-09-09
> **jerome1232 said:**
> Downloadthe source code, compile yourself and install it to a location in that users home. I'm not sure if winehq supplies pre-compiled binaries that you can simply copy to that users home or not, you'd have to poke around their page a bit.
I don't know how to compile.

Is there a step by step tutorial on how to disable internet access in wine anywhere?

---

