---
title: "wine: import_dll Library not found"
date: 2010-07-29
forum: Wine
---

### Post by michael__p on 2010-07-29
Hi,
I tried to install EndNote (.exe) file via wine. But I get:
fixme:actctx:p****_depend_manifests Could not find dependent assembly L"Microsoft.VC90.CRT" (9.0.21022.8)

and then several errors: import_dll Library (...) not found

Could anyone tell me how to get those / what to do? I tried googling for it, but I´m a newb and didn´t understand anything of what people are talking there..
Cheers!

---

### Post by Bachstelze on 2010-07-29
Install vcrun2008 in winetricks.

```
sudo apt-get install winetricks
winetricks vcrun2008
```

---

### Post by loell on 2010-07-29
moved thread to the Wine subforum.

perhaps Endnote is and was never compatible with Wine?

---

### Post by michael__p on 2010-07-29
Thanks,
it seems
winetricks vcrun2008
installed some of the libraries.
But I still need xqilla22.dll, xerces_3_0.dll, PDFNetC.dll, LIBMYSQLD.dll, Omnivis.dll, ENWebRegistration.dll and SSCE5432.dll.
plus I get:
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\home\\michael\\EndNote X4 Bld 4845\\EndNote.exe" failed, status c0000135

---

### Post by asdfoo on 2010-07-29
it looks like you haven't installed the program correctly.  You need to run the installer to install the program in Wine.

Your posts show that you're running it from your home directory rather than the default installation path.

---

### Post by michael__p on 2010-07-29
I´m trying to install it from the folder where the .exe is located
What else do you mean by running the installer than typing
wine EndNote.exe
?

---

### Post by Bachstelze on 2010-07-29
> **michael__p said:**
> I´m trying to install it from the folder where the .exe is located
What else do you mean by running the installer than typing
wine EndNote.exe
?

Are you sure that the EXE is really the installer, not the actual program?

---

### Post by michael__p on 2010-07-29
Yes

---

