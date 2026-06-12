---
title: "C: doesn't exist"
date: 2010-05-02
forum: Wine
---

### Post by toji on 2010-05-02
So i just installed wine and was trying to browse the c:\ drive....
but when i click on it in the K-menu it says that

Unable to run the command specified. The file or folder file:///home/jayne/Documents/.wine/dosdevices/c: does not exist.

when i use, wine c:

it says invalid handle..

any help??

---

### Post by hikaricore on 2010-05-02
How did you install wine?  Source, packages, other?

Try this from a terminal:
> wineprefixcreate

---

### Post by toji on 2010-05-09
Note: wineprefixcreate is deprecated and shouldn't be needed anymore.
      WINEPREFIX creation and updates now happen automatically when needed.

fixme:system:SetProcessDPIAware stub!
fixme:dwmapi:DwmIsCompositionEnabled 0x33cfd4
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:advapi:SetNamedSecurityInfoW L"C:\\windows\\system32\\gecko\\1.0.0\\wine_gecko\\components\\xpti.dat" 1 536870916 (nil) (nil) 0x1dbf54 (nil)
fixme:iphlpapi:NotifyAddrChange (Handle 0x2f0e8d8, overlapped 0x2f0e8e0): stub
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:advapi:SetNamedSecurityInfoW L"C:\\windows\\system32\\gecko\\1.0.0\\wine_gecko\\components\\compreg.dat" 1 536870916 (nil) (nil) 0x1cfdc94 (nil)
wine: configuration in '/home/pritoj/.wine' has been updated.


after running "wineprefixcreate"

and c: still doesn't exist

---

### Post by cogadh on 2010-05-09
On Kubuntu there is a flaw in the shortcut path. The default shortcut command is this:

xdg-open .wine/dosdevices/c:

Which for some reason, Kubuntu assumes means you are looking for something in /home/<username>/Documents. You can fix it by making a minor edit to the shortcut command:

xdg-open **~/**.wine/dosdevices/c:

Adding the "~/" defines the path as /home/<username>/.wine... so you will no longer get that error.

---

### Post by toji on 2010-05-12
Yup got it... thanks maite:)

---

