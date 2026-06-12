---
title: "Your kernel was built with &quot;gcc&quot; version &quot;4.3.2&quot;, you're using &quot;4.3.3&quot;"
date: 2009-08-09
forum: Virtualisation
---

### Post by nikku.jain on 2009-08-09
[SIZE=3]Hi Freinds,

I m having Ubuntu 9.04. Tpday i m trying to install vmware on my ubuntu but I got some serious error, due to which installation is not possible. The error was showing as follows...         :( :( :confused: :confused:

-------------------

Your kernel was built with "gcc" version "4.3.2", while you are trying to use 
"/usr/bin/gcc" version "4.3.3". This configuration is not recommended and 
VMware Player may crash if you'll continue. Please try to use exactly same 
compiler as one used for building your kernel. Do you want to go with compiler 
"/usr/bin/gcc" version "4.3.3" anyway? [no] 

----------
pls anybody help me out...
[/SIZE]

---

### Post by darco on 2009-08-09
What happens if you answer "yes"?

darco

---

### Post by DesiBabu on 2010-07-16
Was this issue resolved for you?

I am having the same issue but with version 4.3.3 of GCC for the kernel while my compiler is at 4.4.3?

I too am trying to reinstall my VMWare Server after upgrading ubuntu to 10.04.

Should I be rebuilding the kernel against the new cmpiler or downgrade my gcc to the lower version?

And how do I do either one of them?

Thanks

---

### Post by dcstar on 2010-07-25
> **DesiBabu said:**
> Was this issue resolved for you?

I am having the same issue but with version 4.3.3 of GCC for the kernel while my compiler is at 4.4.3?

I too am trying to reinstall my VMWare Server after upgrading ubuntu to 10.04.

Should I be rebuilding the kernel against the new cmpiler or downgrade my gcc to the lower version?

And how do I do either one of them?

Thanks

There already massive threads discussing this ages ago, basically it make no difference whatsoever.

---

