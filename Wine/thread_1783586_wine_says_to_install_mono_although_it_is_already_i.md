---
title: "wine says to install mono although it is already installed"
date: 2011-06-15
forum: Wine
---

### Post by n-alexander on 2011-06-15
trying to run an installed that uses C#:

```
/media/cdrom0/RAF: wine RAFHelperInstaller.exe 
wine: Install the Windows version of Mono to run .NET executables

```

used winetricks mono28 to install Mono, per [http://wiki.winehq.org/Mono](http://wiki.winehq.org/Mono), and Mono 2.8.2 is now in Wine menu, but still get the same results.

What's wrong?

```
/media/cdrom0/RAF: wine --version
wine-1.2.2
/usr/lib/mono: ls
1.0  2.0/  3.5/  compat-2.0/  gac/
```

Thanks
Alex

---

### Post by directhex on 2011-06-16
Wine cannot use Mono for Linux.

Wine can only use Mono for Windows.

You need to download the Windows version of Mono, and install it in Wine. Then you might be able to run 'wine "c:\program files\mono\mono.exe RAFHelperInstaller.exe" or something like that

---

### Post by n-alexander on 2011-06-16
> **directhex said:**
> Wine cannot use Mono for Linux.

Wine can only use Mono for Windows.

You need to download the Windows version of Mono, and install it in Wine. Then you might be able to run 'wine "c:\program files\mono\mono.exe RAFHelperInstaller.exe" or something like that

I did install Mono for windows.

---

### Post by curmudgeon38 on 2012-03-11
I have the same problem.

---

### Post by rob_l_f on 2012-06-05
Did anyone manage to solve this issue?  I have exactly the same problem; used winetricks to install the Windows version of Mono, still getting the error.  How does wine check for Mono's existence?

---

### Post by cogadh on 2012-06-06
Mono is not quite a 100% fully functional alternative to .NET, so you could just be running up against a missing function of some kind. Wine is probably just spitting out a default error message for .NET related errors. You could try installing actual .NET in Wine, but depending on the version, you might not have any better luck: [http://appdb.winehq.org/objectManager.php?sClass=application&iId=2586](http://appdb.winehq.org/objectManager.php?sClass=application&iId=2586)

---

