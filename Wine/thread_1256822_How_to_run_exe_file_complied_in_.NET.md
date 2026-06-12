---
title: "How to run exe file complied in .NET"
date: 2009-09-03
forum: Wine
---

### Post by lidengdeng on 2009-09-03
Hi,

The file Demo.exe is developed in .NET with C#. When I am trying to run it in Ubuntu8.04 with command "wine Demo.exe", met the msg:

install the Windows version of Mono to run .NET executables

So did it imply I should install mono? But when I run the command "sudo apt-get install mono", met the msg:
Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mono: Depends: mono-common (= 1.1.13.6-0ubuntu3.3) but 1.2.6+dfsg-6ubuntu3.1 is to be installed
        Depends: mono-jit (= 1.1.13.6-0ubuntu3.3) but 1.2.6+dfsg-6ubuntu3.1 is to be installed
E: Broken packages


So what should I do to run the Demo.exe successfully?

Thanks.

---

### Post by hikaricore on 2009-09-03
> install the Windows version of Mono to run .NET executables

I think it's pretty obvious what you need to do.

---

### Post by gradinaruvasile on 2009-09-03
> **lidengdeng said:**
> Hi,

The file Demo.exe is developed in .NET with C#. When I am trying to run it in Ubuntu8.04 with command "wine Demo.exe", met the msg:

install the Windows version of Mono to run .NET executables

So did it imply I should install mono? But when I run the command "sudo apt-get install mono", met the msg:
Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mono: Depends: mono-common (= 1.1.13.6-0ubuntu3.3) but 1.2.6+dfsg-6ubuntu3.1 is to be installed
        Depends: mono-jit (= 1.1.13.6-0ubuntu3.3) but 1.2.6+dfsg-6ubuntu3.1 is to be installed
E: Broken packages


So what should I do to run the Demo.exe successfully?

Thanks.

Maybe u have some ppa s in ur apt list?

Anyways dont get ur hopes high cause even if u install mono it is likely wont work for .NET executables. Mono only has a limited amount of .NET functions AFAIK.

---

### Post by directhex on 2009-09-03
> **lidengdeng said:**
> Hi,

The file Demo.exe is developed in .NET with C#. When I am trying to run it in Ubuntu8.04 with command "wine Demo.exe", met the msg:

install the Windows version of Mono to run .NET executables

So did it imply I should install mono? But when I run the command "sudo apt-get install mono", met the msg:
Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mono: Depends: mono-common (= 1.1.13.6-0ubuntu3.3) but 1.2.6+dfsg-6ubuntu3.1 is to be installed
        Depends: mono-jit (= 1.1.13.6-0ubuntu3.3) but 1.2.6+dfsg-6ubuntu3.1 is to be installed
E: Broken packages


So what should I do to run the Demo.exe successfully?

Thanks.

The "mono" binary package is NOT in 8.04 - your error suggests you have both 6.06 and 8.04 sources in your sources.list

Generally, I'd suggest the [mono-runtime](apt:mono-runtime) package as a starting point, whereupon it'll probably complain that you're missing some libraries needed by your app - they're split into separate packages & can be installed via apt

Also consider that Mono in 8.04 is antique. I have backports up to 1.9.1 which is still pretty ancient.

---

