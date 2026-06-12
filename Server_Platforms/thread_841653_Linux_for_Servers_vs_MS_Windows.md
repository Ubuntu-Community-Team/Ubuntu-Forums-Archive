---
title: "Linux for Servers vs MS Windows"
date: 2008-06-26
forum: Server Platforms
---

### Post by oceanfirehawk on 2008-06-26
I have a question:

Which is better for large enterprise server - linux or microsoft?

Is it true that MS server is easier to use that redhat or ubuntu server?

Why is the terminal needed so very much for server administration in linux where in microsoft you dont really need it?

---

### Post by tamoneya on 2008-06-26
It depends a little be on how you define better but in my opinion a linux server is superior here are my reasons:
1. More stable
2. Free
3. I like the support from communities like ubuntu forums

However at my office I use Windows server and im sure you are curious why.  The reason is because while I am familar with linux and personally find it easier most of my co workers are not the same.  In this case linux would be harder not because of how it is designed but because I would be the only one who could manage it.  I personally think that neither one is harder than the other.

As for you command line question you can manage a server in command line in windows and you can manage a server through a gui in linux.  It is mostly a matter of preference but personally I am much quicker with a command line in linux than anything with a gui on windows or linux. If you are curious there is a new package being made called rapache which you may want to look into that makes a nice apache GUI.

[https://launchpad.net/rapache](https://launchpad.net/rapache)

---

### Post by hyper_ch on 2008-06-26
> **oceanfirehawk said:**
> Which is better for large enterprise server - linux or microsoft?
Linux

> **oceanfirehawk said:**
> Is it true that MS server is easier to use that redhat or ubuntu server?
No

> **oceanfirehawk said:**
> Why is the terminal needed so very much for server administration in linux where in microsoft you dont really need it?
what do you need a full-fledged gui for that adds overhead and additional weaknesses for just editing config files?

And don't forget the super-cool new feature of VISTA: The POWERSHELL ;)

---

### Post by koenn on 2008-06-26
> **oceanfirehawk said:**
> I have a question:

Which is better for large enterprise server - linux or microsoft?

Is it true that MS server is easier to use that redhat or ubuntu server?

Why is the terminal needed so very much for server administration in linux where in microsoft you dont really need it?

server administration often involves repetitive tasks or bulk processing : create 2000 user accounts, create a couple of thousend mailboxes, set or change  permissions on hundreds of files and directories, ....
A gui might be easier if you need to do only one of those or don't know very well how (so you just click OK on whatever the dialogs suggest), but thousands ? 
Thats were you want scripts to automate things. A shell ("the command line") is an excellent tool for this. The GUI makes things easy for a novice, but for real work by professionals, it's actually a flaw if a system doesn't have a programmable shell.

---

### Post by wlee on 2008-06-26
> **oceanfirehawk said:**
> Which is better for large enterprise server - linux or microsoft?

In reality, you'll find a mix of many breeds in a large enterprise based on the purpose of the servers needed; database, email, authentication, webs, apps, and etc.  You won't find too many large enterprises running only Windows or only *NIX.

It's not always about which is better.  If there is an executive preference specifically for MSSQL, Active Directory, Exchange, Sharepoint, LCS and etc., and not the *NIX equivalent of these products you can only run Windows.  Most of the time the decision is based on ease of integration/interoperability, requirements of the application(s), and availability of enterprise class support for the product you want to implement.  Additionally, if your organization started with Windows 3.51, you're probabaly on 2003 and AD now.  Migrating large enterprises can be complex, time consuming, and costly.

Where I work, we have AIX, Windows, and a Mainframe.  No live Linux deployment - yet.

---

### Post by wlee on 2008-06-26
> **wlee said:**
> Most of the time the decision is based on ease of integration/interoperability, requirements of the application(s), and availability of enterprise class support for the product you want to implement.

Notice how I didn't mention cost.

That's because staffing skilled *NIX employees can cost more that M$ employees (of course having specialty skills can level the field a little). Hardware is not really cheaper nor is enterprise class support. The major savings is probably licensing, but that's a one time hit at the time of purchase, the killer is still the cost of annual maintenance, and again, not that much cheaper for large enterprises.

---

### Post by windependence on 2008-06-27
> **wlee said:**
> Notice how I didn't mention cost.

That's because staffing skilled *NIX employees can cost more that M$ employees (of course having specialty skills can level the field a little). Hardware is not really cheaper nor is enterprise class support. The major savings is probably licensing, but that's a one time hit at the time of purchase, the killer is still the cost of annual maintenance, and again, not that much cheaper for large enterprises.

There have been studies done showing that it takes 10 Windoze admins to admin the same number of machines as Unix/Linux.

This is mostly political and as such isn't really answering what the OP asked. He asked which is better. Hands down Linux. I have NEVER in the 4 years I have been working at this enterprise much like wlee, been asked to reboot a Linux/Unix sever. Not once. We have servers that spit out an "error" message saying the server has been up for 880 days without a reboot, maybe you might want to consider rebooting. It's actually funny. 

Windoze is used in our enterprise because we have a Systems Engineer who came from Micro$oft. Executive decisions are made like wlee said when they see that Windoze admins cost less. they don't consider that it takes less of them or consider dowmtime in terms of money, or how about patch Tuesdays? That interrupts our business in a very intrusive way as ALL the machines have to be rebooted, including the servers. You would think Micro$oft would have figured this out by now.

-Tim

---

