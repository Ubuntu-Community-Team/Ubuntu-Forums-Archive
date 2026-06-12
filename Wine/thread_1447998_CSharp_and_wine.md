---
title: "CSharp and wine"
date: 2010-04-06
forum: Wine
---

### Post by satimis on 2010-04-06
Hi folks,

CSharp (C#) and wine

Can CSharp run on wine ?
[Download and Install C# Express 2008 at C# Online.NET (CSharp-Online.NET)](http://en.csharp-online.net/Download_and_Install_CSharp_Express_2008)

If YES which Linux distro will be more suitable?  Debian or Ubuntu?

TIA

B.R.
satimis

---

### Post by sxmaxchine on 2010-04-06
none of the visual studio or basic products will work on wine sorry and i tried it with c# and vb.net

---

### Post by sxmaxchine on 2010-04-06
also ubuntu is basically debian as it is based on debian so i assume it would run the same on either

---

### Post by satimis on 2010-04-06
> **sxmaxchine said:**
> also ubuntu is basically debian as it is based on debian so i assume it would run the same on either

Thanks

satimis

---

### Post by thebigob on 2010-04-06
Use mono.

This will compile c# natively to linux and it runs perfectly.

[http://www.mono-project.com/Main_Page](http://www.mono-project.com/Main_Page)

---

### Post by satimis on 2010-04-06
> **thebigob said:**
> Use mono.

This will compile c# natively to linux and it runs perfectly.

[http://www.mono-project.com/Main_Page](http://www.mono-project.com/Main_Page)

Hi thebigob,

Thanks for your advice and URL.


Mono for Ubuntu
Official Packages
[http://mono-project.com/DistroPackages/Ubuntu](http://mono-project.com/DistroPackages/Ubuntu)```

The following official versions are available in the standard Ubuntu repositories:
Ubuntu Dapper (6.06 LTS): 	1.1.13.6
Ubuntu Hardy (8.04 LTS): 	1.2.6
Ubuntu Intrepid (8.10): 	1.9.1
Ubuntu Jaunty (9.04): 	2.0.1
Ubuntu Karmic (9.10): 	2.4.2.3
Ubuntu Lucid (10.04 LTS): 	2.4 branch snapshot 

Dependencies are automatically tracked for applications in the archive such as Tomboy and F-Spot. Ubuntu comes with these two applications by default, and therefore comes with Mono installed by default.

To compile your own software, install mono-devel on Dapper (6.06 LTS), Jaunty (9.04), Karmic (9.10), or Lucid (10.04 LTS) 

```

$ apt-cache policy mono-devel```

mono-devel:
  Installed: (none)
  Candidate: 2.4.2.3+dfsg-2
  Version table:
     2.4.2.3+dfsg-2 0
        500 http://hk.archive.ubuntu.com karmic/main Packages

```

I suppose this is the package which I need?


Download CSharp_Express_2008
============================
[http://en.csharp-online.net/Download_and_Install_CSharp_Express_2008](http://en.csharp-online.net/Download_and_Install_CSharp_Express_2008)```

When you choose to install C# Express from the Offline Install, you will download a 900MB ISO file. Either extract this file using Winrar to a temporary directory and/or burn the ISO to a DVD.

Once you have the files extracted to either a temporary folder or on a DVD, run the setup file. 

```

Whether to download the ISO image?   Do I need to extract it?  If YES which software to be used?  Winrar?  It runs on Windows and I'm going to install C# on Ubuntu 9.10 64bit

Please advise.  TIA


B.R.
satimis

---

### Post by asdfoo on 2010-04-06
> **satimis said:**
> Hi thebigob,

Thanks for your advice and URL.


Mono for Ubuntu
Official Packages
[http://mono-project.com/DistroPackages/Ubuntu](http://mono-project.com/DistroPackages/Ubuntu)```

The following official versions are available in the standard Ubuntu repositories:
Ubuntu Dapper (6.06 LTS): 	1.1.13.6
Ubuntu Hardy (8.04 LTS): 	1.2.6
Ubuntu Intrepid (8.10): 	1.9.1
Ubuntu Jaunty (9.04): 	2.0.1
Ubuntu Karmic (9.10): 	2.4.2.3
Ubuntu Lucid (10.04 LTS): 	2.4 branch snapshot 

Dependencies are automatically tracked for applications in the archive such as Tomboy and F-Spot. Ubuntu comes with these two applications by default, and therefore comes with Mono installed by default.

To compile your own software, install mono-devel on Dapper (6.06 LTS), Jaunty (9.04), Karmic (9.10), or Lucid (10.04 LTS) 

```

$ apt-cache policy mono-devel```

mono-devel:
  Installed: (none)
  Candidate: 2.4.2.3+dfsg-2
  Version table:
     2.4.2.3+dfsg-2 0
        500 http://hk.archive.ubuntu.com karmic/main Packages

```

I suppose this is the package which I need?


Download CSharp_Express_2008
============================
[http://en.csharp-online.net/Download_and_Install_CSharp_Express_2008](http://en.csharp-online.net/Download_and_Install_CSharp_Express_2008)```

When you choose to install C# Express from the Offline Install, you will download a 900MB ISO file. Either extract this file using Winrar to a temporary directory and/or burn the ISO to a DVD.

Once you have the files extracted to either a temporary folder or on a DVD, run the setup file. 

```

Whether to download the ISO image?   Do I need to extract it?  If YES which software to be used?  Winrar?  It runs on Windows and I'm going to install C# on Ubuntu 9.10 64bit

Please advise.  TIA


B.R.
satimis

where did you get the second URL from?  It has nothing to do with what was suggested.

Note:  You cannot install C#.  C# is a language specification, Visual C# is produced by Microsoft, Mono is a free implementation of C#.

Microsoft Visual Studio is still being worked on with Wine, maybe it will work in the future.

Mono is a reasonable alternative, it includes a compiler to compile programs written in C#, however it does not have support for WPF currently.

As your post has nothing to do with Wine now, please use another section of the forum for asking further questions about mono.

---

### Post by peteraugusts on 2010-04-07
Use Mono if you are interested in C# development. Mono and mono develop is all you need on Ubuntu  or Debian to get a really good C# development environment. They have their own IDE that is reasonable and provide tools for Eclipse.

---

### Post by satimis on 2010-04-07
> **peteraugusts said:**
> Use Mono if you are interested in C# development. Mono and mono develop is all you need on Ubuntu  or Debian to get a really good C# development environment. They have their own IDE that is reasonable and provide tools for Eclipse.

Hipeteraugusts,

I have following packages installed.```

monodevelop
libmono-corlib2.1-cil
asp.net-examples
asp.net2-examples

```

How to start mono?  Thanks


satimis

---

