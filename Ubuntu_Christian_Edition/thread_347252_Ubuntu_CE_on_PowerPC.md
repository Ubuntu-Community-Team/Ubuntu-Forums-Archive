---
title: "Ubuntu CE on PowerPC"
date: 2007-01-27
forum: Ubuntu Christian Edition
---

### Post by Ptero-4 on 2007-01-27
Hi. I'm interested in getting ubuntu CE, but I have a PowerPC box (a.k.a a Mac) and wanted to know if ubuntu CE (or it's components) can be installed on the ppc arch or if they're x86 only?

---

### Post by mhancoc7 on 2007-01-27
Thanks for your interest in Ubuntu CE.

There is not currently a iso for the PPC. However, there have been some reports that the x86 iso will work. This can not be verified and has not been officially tested. There is also the option of using the convert_me script on a default install of Ubuntu. This should work regardless of architecture since the script uses apt-get and other basic commands to make the changes.

If you have any question just let me know.

Jereme

---

### Post by mips on 2007-01-27
> **mhancoc7 said:**
> Thanks for your interest in Ubuntu CE.

There is not currently a iso for the PPC. However, there have been some reports that the x86 iso will work. This can not be verified and has not been officially tested. There is also the option of using the convert_me script on a default install of Ubuntu. This should work regardless of architecture since the script uses apt-get and other basic commands to make the changes.

If you have any question just let me know.

Jereme

Jereme,

I find it highly unlikely (actually impossible) that the x86 iso will work on a PPC machine. You might be able to read the disc from it but you will not be able to do much with it.

Maybe post a link to the convert_me script here if it resides on your website or elsewhere. That way others would know where to find it.

---

### Post by mhancoc7 on 2007-01-27
> **mips said:**
> Jereme,

I find it highly unlikely (actually impossible) that the x86 iso will work on a PPC machine. You might be able to read the disc from it but you will not be able to do much with it.

Maybe post a link to the convert_me script here if it resides on your website or elsewhere. That way others would know where to find it.

Like I said, I have not tested it. I have just had PPC users report that it worked.

The convert_me scripts can be found on the Ubuntu CE download page.

[http://mirror.christianubuntu.com](http://mirror.christianubuntu.com)

Jereme

---

### Post by Ptero-4 on 2007-02-05
Thanks the convert_me script did it (partially) only issues were

1) needed to get the ppc version of libsword5c2a off the Dapper repos.

2) had to put the ichthux usplash since the ubuntu CE one is compiled for x86.

3) The dansguardian GUI seems to be broken on PPC.

P.d: Do you have by chance the source code for the usplash theme.

---

### Post by mhancoc7 on 2007-02-05
> **Ptero-4 said:**
> Thanks the convert_me script did it (partially) only issues were

1) needed to get the ppc version of libsword5c2a off the Dapper repos.

2) had to put the ichthux usplash since the ubuntu CE one is compiled for x86.

3) The dansguardian GUI seems to be broken on PPC.

P.d: Do you have by chance the source code for the usplash theme.

Thanks for letting me know how it went. I am not sure why the dansguardian GUI is broken. :confused:

I do not have the source for the usplash, but you can check this post out to build one. This is exactly how the Ubuntu CE (Edgy) usplash was built.

[http://www.ubuntuforums.org/showpost.php?p=1796269&postcount=6](http://www.ubuntuforums.org/showpost.php?p=1796269&postcount=6)

God Bless, Jereme

---

