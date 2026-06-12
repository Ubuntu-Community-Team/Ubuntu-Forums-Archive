---
title: "QuakeLive in Wine 1.1.15"
date: 2009-02-26
forum: Wine
---

### Post by Filmorependrgn on 2009-02-26
QuakeLive works now fullscreen, but disconnects after a few mins...

Be sure to set your game to play in fullscreen. It disconnects me before the practice match can end.


Old post is below
______________________________________


Well, I managed to get 95% of QuakeLive working.

Here's the brief rundown:

I grabbed a bunch of [winetricks]("http://wiki.winehq.org/winetricks")
(EDIT: It now works without DX9)

```
 $sh winetricks msxml3 dotnet20 gdiplus riched20 riched30 vcrun2005sp1
```


And copied the following from a windows XP installation of mine (EDIT: no longer needed?):

* secur32.dll
* dnsapi.dll
* rpcrt4.dll

and stuck them in my .wine/drive_c/windows/system32 directory. You also have to go into winecfg and set library overrides for secur32, dnsapi, and rpcrt4 (`native then builtin' will do)


Then I installed Firefox 3.0.6 and Flash Player 10. Then installed the QuakeLiveNP.msi with the following command:

```
wine msiexec.exe /i QuakeLiveNP.msi
```

I also had to nab an [update for PunkBuster]("http://www.evenbalance.com/index.php?page=dl-ql.php").

Viola!
[IMG]http://web.ics.purdue.edu/~crallen/QuakeLiveLinux.png[/IMG]

The game grabs the mouse, and the sound works (you can hear mouse-over effects)... but the video isn't coming through yet...

---

### Post by binbash on 2009-02-26
I have same problem.Video is not coming

---

### Post by Pfiffer on 2009-02-27
> **Filmorependrgn said:**
> 
...


Have you tried running Firefox under wine? I'd be interested in seeing this work. Good info, btw.

Edit: I think I mis-read. IGNORE ME.

---

### Post by whoop on 2009-02-27
That's a good attempt there. Thank you for this information. You can follow vanilla wine developments concerning quake live here:
[http://bugs.winehq.org/show_bug.cgi?id=17458](http://bugs.winehq.org/show_bug.cgi?id=17458)

---

### Post by Filmorependrgn on 2009-03-16
Seems to work now if you use Fullscreen. But I keep getting disconnected before the practice match can end.:(

---

### Post by loganp82 on 2009-03-17
that whole disconnecting before the match is over was fixed with an update to there site.

---

### Post by aleb on 2009-05-08
> **loganp82 said:**
> that whole disconnecting before the match is over was fixed with an update to there site.

Still happens for me (May 2009, Wine 1.1.20). I cannot finish the training game because it interrupts.

I followed the instructions here: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=15796](http://appdb.winehq.org/objectManager.php?sClass=version&iId=15796)

---

