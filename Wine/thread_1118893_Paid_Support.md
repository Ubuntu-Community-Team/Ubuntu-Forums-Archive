---
title: "Paid Support?"
date: 2009-04-07
forum: Wine
---

### Post by thebbxx on 2009-04-07
I have been trying to run an application called Encompass(Mortgage Origination Software) in wine and I think I'm really close, but no cigar.  Anyway, it's worth $200 to me and I'm thinking someone who knew what they were doing could do it in an hour or less.  Here are some details:

Program can be downloaded here:
[http://download.elliemae.com/encompass/install/sepro/3.5.0/netbranch.exe](http://download.elliemae.com/encompass/install/sepro/3.5.0/netbranch.exe)

I installed on windows, then copied the encompass folder from program files, the encompass data folder, and exported the keys from the registry.  I put all of this on my wine partition.

I installed .net using winetricks

I set rasapi32 to native.

The program runs and shows a login screen, but after pressing login, I get a dialog that says:

"Unknown login error: Error creating the Web Proxy specified in the 'system.net/defaultProxy' configuration section."

I think it may be related to using https

Anyway, if you think you can help, please let me know.

Thanks!

---

### Post by ajackson on 2009-04-07
I doubt very much it could be solved in an hour, from what you say it uses .NET. At the moment .NET support is sketchy in Wine, yes it now installs but that is only half the battle, the harder half is getting the bugs out.

A bug report would help, especially since there is a downloadable version to test with but it won't get fixed in an hour then either. There are thousands of bugs in the wine bug tracker, some are caused by missing functionality in wine (ie missing library functions), some are just plain bugs in the existing implementation.

---

### Post by cogadh on 2009-04-07
It would also be helpful if you actually installed the application in Wine, instead of shoehorning it in there with a bunch of copy/pastes and reg merges.

---

### Post by asdfoo on 2009-04-08
$200 probably won't get you far if there is a real problem, can you include the full output of what happens when you try to run it?

---

