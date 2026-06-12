---
title: "Biblemapper on wine"
date: 2008-09-25
forum: Ubuntu Christian Edition
---

### Post by refdoc on 2008-09-25
Would like to know if anyone had success to get Biblemapper going on Wine and Ubuntu?

Biblemapper is a programme to design excellently detailed and freely distributable maps. It is only available as a Windows programme and requires a (freely available) license key. You can download it from [http://www.biblemapper.com]("http://www.biblemapper.com")

What I got so far is

a) I can install the download file with 

```
wine msiexec /i BibMap30.msi
```

It installs fine.

b) when I start the programme with wine BibleMapper.exe I get the splsh screen and then an error message:
```
XIO:  fatal IO error 12 (Cannot allocate memory) on X server ":0.0"
      after 5829 requests (5826 known processed) with 0 events remaining.
```

I googled for the error message but could not make much sense with what I got. If someone can get past this I would be extremely gratefulf if you could pass this knowledge on.

*update* Updating Wine to the newest from winhq's repository did not improve the matter.

Thanks and God bless!

---

### Post by refdoc on 2008-09-27
I have created an entry in the application database of Wine. This is the first step of getting the wine developers involved in making this applicatin work.

Maybe there are others among you who feel this is a useful matter and you might want to get your voice heard (and vote counted)

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=8348](http://appdb.winehq.org/objectManager.php?sClass=application&iId=8348)

Thanks

---

