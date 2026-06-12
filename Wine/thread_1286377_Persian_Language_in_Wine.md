---
title: "Persian Language in Wine"
date: 2009-10-08
forum: Wine
---

### Post by rostamiani on 2009-10-08
Hi everybody

I want to use Microsoft Office 2003 with wine, But all of the persian characters are shown as square !:confused:

Should I install persian language somewhere or somthing else ?

Thanks

---

### Post by asdfoo on 2009-10-09
> **rostamiani said:**
> Hi everybody

I want to use Microsoft Office 2003 with wine, But all of the persian characters are shown as square !:confused:

Should I install persian language somewhere or somthing else ?

Thanks

sounds like missing fonts, use winetricks to install corefonts maybe?

wget kegel.com/wine/winetricks
sh winetricks corefonts

---

### Post by rostamiani on 2009-10-10
Thanks a lot. I copied all fonts fro, Windows/Font 
Now I can type in persian but in a wrong way !

For example It displays this:

&#1587; &#1604; &#1575; &#1605;

Instead of :

&#1587;&#1604;&#1575;&#1605;

What can I do ?
Thanks

---

### Post by asdfoo on 2009-10-10
> **rostamiani said:**
> Thanks a lot. I copied all fonts fro, Windows/Font 
Now I can type in persian but in a wrong way !

For example It displays this:

&#1587; &#1604; &#1575; &#1605;

Instead of :

&#1587;&#1604;&#1575;&#1605;

What can I do ?
Thanks

uhm, for a start you can read what I said first.
where did I say "copy all your fonts from windows"

I said to use winetricks to install corefonts.

---

### Post by rostamiani on 2009-10-11
> **asdfoo said:**
> uhm, for a start you can read what I said first.
where did I say "copy all your fonts from windows"

I said to use winetricks to install corefonts.

Thanks a lot
I removed copied fonts and installed corefonts
But still no Persian characters are shown :(

---

### Post by ebrahim on 2010-08-06
Salaam,
This is a known issue with Wine. The BiDi functionality is not completely implemented yet. So there is nothing on your side to do to fix this problem.
Maybe by installing a native usp10.dll you get it to work.

---

