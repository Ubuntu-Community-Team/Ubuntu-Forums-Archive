---
title: "Installing DirectX"
date: 2011-04-19
forum: Wine
---

### Post by pqwoerituytrueiwoq on 2011-04-19
was following this guide
[http://www.dedoimedo.com/games/wine-directx.html](http://www.dedoimedo.com/games/wine-directx.html)
i ran into an error while installing direct x

---

### Post by cogadh on 2011-04-20
You don't need to and really shouldn't install DirectX as it can break Wine. Wine includes its own implementation of DirectX that is normally good enough to run anything up to DirectX 9. At most, you might need the d3dx9_##.dll files (which won't break Wine) and you can get them without installing the full DirectX by copying them from an existing Windows installation or by using [winetricks]("http://wiki.winehq.org/winetricks").

---

### Post by gradinaruvasile on 2011-04-20
> **cogadh said:**
> You don't need to and really shouldn't install DirectX as it can break Wine. Wine includes its own implementation of DirectX that is normally good enough to run anything up to DirectX 9. At most, you might need the d3dx9_##.dll files (which won't break Wine) and you can get them without installing the full DirectX by copying them from an existing Windows installation or by using [winetricks]("http://wiki.winehq.org/winetricks").

I beg to differ. I installed only the said dlls and i still had slow/non-working 3d apps in Wine.
Then i installed the full package and i have way faster apps and better/more effects in some games (LOTRO, Medieval 2 etc). I know the wine devs said this or that but in practice just this is the way it works.

Nothing is more broken than it was before...

---

### Post by pqwoerituytrueiwoq on 2011-04-20
I was trying to get this game to work
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=21544](http://appdb.winehq.org/objectManager.php?sClass=version&iId=21544)
it came free with my [processor]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819103727") i got off newegg and took me a few days to download
i figured i would give it a try

---

### Post by cogadh on 2011-04-21
> **pqwoerituytrueiwoq said:**
> I was trying to get this game to work
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=21544](http://appdb.winehq.org/objectManager.php?sClass=version&iId=21544)
it came free with my [processor]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819103727") i got off newegg and took me a few days to download
i figured i would give it a try
Well Considering that game is rated "bronze", it might not be worth trying yet. That rating is not simply poor performance, that means the app installs and might even run, but key parts of it simply won't work. Regardless of whether or not it is safe to do, installing DirectX won't fix that.

> **gradinaruvasile said:**
> I beg to differ. I installed only the said dlls and i still had slow/non-working 3d apps in Wine.
Then i installed the full package and i have way faster apps and better/more effects in some games (LOTRO, Medieval 2 etc). I know the wine devs said this or that but in practice just this is the way it works.

Nothing is more broken than it was before...
I said it CAN break Wine, not that it WILL break Wine. The fact is, installing DX replaces or adds so many files in Wine, most of which do not need to be replaced or added, that the risk of something eventually going wrong is pretty high (hence why the Wine devs recommend against it). Chances are, your problems were solved by just one of the DLLs that DX replaced or added, but now you have a lot more than just that file changed in your system. Basically, you fixed a problem with the "shotgun approach", blasting Wine with a flurry of DLL buckshot, when the more precise "sniper approach" would have solved it just as easily and much more safely with a single DLL bullet.

---

