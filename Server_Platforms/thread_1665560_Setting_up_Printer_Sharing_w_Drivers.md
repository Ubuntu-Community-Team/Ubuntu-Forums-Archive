---
title: "Setting up Printer Sharing w/ Drivers"
date: 2011-01-12
forum: Server Platforms
---

### Post by NessDan on 2011-01-12
Like the title says, I want to setup my print server to share drivers when Windows clients connect.

I've been working at this for almost a week now and I'm in a very unfortunate situation. My print server (running CUPS 1.4.4 and Samba) works fine. When adding the printer via CUPS, I chose a driver from the pre-installed list and I setup Samba to correctly share the printer.

I can see the printer and even print from it, but my problem is that I have to manually download and install the drivers for my printer for every computer that wants to print. I'd really like to setup a more professional environment where the server would serve out the driver files.

My smb.conf looks like this:
```

[global]
printer = Samsung
load printers = yes
printing = cups
printcap name = cups
public = yes
security = share

[printers]
comment = All Printers
path = /var/spool/samba
browseable = no
guest ok = yes
writable = no
printable = yes
printer admin = root, @ntadmins, @smbprintadm

[print$]
comment = Printer Drivers
browseable = yes
path = /var/lib/samba/printers
guest ok = yes
read only = yes

```

The only line up there that I think I don't need is the printer admin.

Anyways, inside of /var/lib/samba/printers are a whole bunch of folders (COLOR, IA64, W32ALPHA, W32MIPS, W32PPC, W32X86, WIN40, x64) and I've read around and tried a whole bunch of different things. I went into my Laptop's C:\Windows\System32\spool\DRIVERS\w32x86 and copied the folder titled "3" into the Samba print drivers folder "W32X86" - but to no avail.

When I print a test from my Windows machine, it says
Driver name: SSGB6.DLL
Data file: SSGB6pp.dll
Config file: SSGB6du.DLL

Then a large list of files starting with (SSGB6??.??? format), all of which are located in the "3" folder.

I'd really like this up and running so I can get started on other work so all help is greatly appreciated! And any in-depth explanations are welcome, I'm new to the world of servers and Linux (I've picked up a lot in the past few weeks) but I love to understand things 100% and I hate having such a powerful machine and not knowing what's going on under the hood.

Thanks!

---

