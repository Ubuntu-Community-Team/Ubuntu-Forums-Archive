---
title: "Create a non- Admin account"
date: 2009-06-19
forum: Security
---

### Post by emeraldgirl08 on 2009-06-19
I'm dealing with a pretty huge security dilemma on my cousins computer. She didn't update as needed or do any program maintenance on her desktop. You know- the type that just turns it on, uses it, and then shuts it off. I'm still working on it and it's got me wondering. 

How do I configure Ubuntu so I can add a second non-administrative (don't know the linux term) account?

On Windoze I have my admin account and my limited account. I use the limited account to get on the internet, browse, download, and pretty much everything- except installing programs and making changes to my comp. I scan the things I download and run my virus scan and spybot scan on a consistent basis. I like this setup and don't mind having to log in to a different account to do my updates (I don't auto update by choice) and install the programs I want. I just want to avoid problems like a computer that seems possessed and requires huge amounts of time to diagnose and repair.

---

### Post by HermanAB on 2009-06-19
On Ubuntu, the first account is an Admin account.  So just create another account.

---

### Post by wojox on 2009-06-19
It depends

From Graphical :
Go to System > Administration > Users and Groups
Press +Add User button
This opens the User Account Editor. Minimum requirements are Username and Password.

From Command-line :
sudo adduser emeraldgirl
sudo passwd emeraldgirl

---

### Post by rookcifer on 2009-06-19
> **emeraldgirl08 said:**
> I'm dealing with a pretty huge security dilemma on my cousins computer. She didn't update as needed or do any program maintenance on her desktop. You know- the type that just turns it on, uses it, and then shuts it off. I'm still working on it and it's got me wondering. 

What exactly is the "security dilemma?"  If she didn't update, then tell her to start updating.  It's pretty simple.  If she's behind a NAT router or is using IPtables locally, then I doubt that her PC has been exploited regardless of its update status.  Do you have a specific reason to believe the machine has been compromised?

> How do I configure Ubuntu so I can add a second non-administrative (don't know the linux term) account?

You don't have to.  The account created initially *is* a limited account (where superuser privileges are granted as needed by providing a password).  You are thinking in Windows terms here, where M$ leaves its users out to dry by automatically putting them on an administrative account by default.  Ubuntu (and no Linux distro I know of) does that.  

Sure, you can create another account for her and not allow it sudo access, but what good is that?  She wont be able to update the machine, thus leaving you with the initial problem.

---

### Post by emeraldgirl08 on 2009-06-19
> What exactly is the "security dilemma?" If she didn't update, then tell her to start updating. It's pretty simple. If she's behind a NAT router or is using IPtables locally, then I doubt that her PC has been exploited regardless of its update status. Do you have a specific reason to believe the machine has been compromised?

Forgot to mention that her OS is Vista Premium. She does everything from her admin account and had her auto updates turned completely off! 

:lolflag:

I had to give her a quick 2-minute schooling on why updates are SO IMPORTANT! Her symptoms are a repeating split second flash of a wuauclt DOS box. I also could not enable her automatic updates to work! Her GUI interface is all mostly blank on Auto Updates settings. Meaning I can't tick or untick the little circle for On, Off, and I'll update on my own.

On top of that she's got some major cleaning and disposing of bloatware excised from her comp.

> You don't have to. The account created initially is a limited account (where superuser privileges are granted as needed by providing a password). You are thinking in Windows terms here, where M$ leaves its users out to dry by automatically putting them on an administrative account by default. Ubuntu (and no Linux distro I know of) does that.

Sure, you can create another account for her and not allow it sudo access, but what good is that? She wont be able to update the machine, thus leaving you with the initial problem

Thanks that makes a whole lot of sense :D

Yeah I've been dealing w/ Windows alot lately! She doesn't use my machine! U nuts??!!! lol. Thanks guys and Rookcifer!

---

