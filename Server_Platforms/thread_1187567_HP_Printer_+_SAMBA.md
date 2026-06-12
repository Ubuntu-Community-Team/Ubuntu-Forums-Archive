---
title: "HP Printer + SAMBA"
date: 2009-06-14
forum: Server Platforms
---

### Post by Vegan on 2009-06-14
Any headaches to move an old HP Deskjet 648C printer to the Linux machine? It supports PCL 3 so its got a real print engine and is not one of those crappy Windows printers.

I wanted to make it a shared resource via SAMBA. At present I have SAMBA as a file server working fine. So I would like to enhance services with a printer.

Thoughts to install the printer and SAMBA?

---

### Post by HermanAB on 2009-06-14
Uhmmm, printers are handled by CUPS, so you got to install that and configure Samba to use CUPS.

All HP printers have Linux drivers.

---

### Post by cariboo on 2009-06-15
You could also just use cups to share the printer. Open the cups web interface:

```
http://localhost:631
```

then click the administration tab, then make sure that Share published printers connected to this system is checked. See the screenshot.

---

### Post by Vegan on 2009-06-15
I just use the user friendly CLI with nano to do all the work. So can SAMBA manage without the need for CUPS?

I assume that given the printer works fine plugged into the Linux USB port.

So why can't I just use a SAMBA share as I do with a folder.

---

### Post by mhgsys on 2009-06-15
```
[printers]
comment = All Printers
browseable = no
path = /var/spool/samba
printable = yes
guest ok = no
read only = yes
create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
comment = Printer Drivers
path = /var/lib/samba/printers
browseable = yes
read only = yes
guest ok = no
# Uncomment to allow

```

I always assumed it was this standard setting in smb.conf.
Isn't it?

I did not try it yet, but that's one thing I also still need to do.

---

### Post by HermanAB on 2009-06-15
The thing is that for printing, CUPS is required, but Samba is optional.

---

### Post by mhgsys on 2009-06-15
ok, CUPS is required for printing, but are the smb.conf lines enough to get the printer shared over a windows network?

f.e Printer already is working like a charm on the ubuntu pc which it is connected to.

---

### Post by cariboo on 2009-06-16
I personally find it easier to use cups to share printers. You can use samba with very few changes needed. Have a look at this [document]("https://help.ubuntu.com/8.10/serverguide/C/samba-printserver.html").

---

### Post by Vegan on 2009-06-21
Well based on that link, then I can simply plug in the printer, restart SAMBA and have a shared printer.

I looked at the /etc/samba/smb.conf closely and the defaults seem fine.

I prefer not to have yet another package if I can leverage what I have already.

---

### Post by HermanAB on 2009-06-21
There are two ways to share a printer with Windows machines:
a. Samba
b. Internet Printing Protocol (IPP)

CUPS supports IPP, so Samba is optional.

---

### Post by Vegan on 2009-06-21
All clients are either Linux or Windows. So says the SAMBA manual that even a Mac can participate. So I use SAMBA as its the official tool for making a Linux file server.

I use SAMBA so I can use my Windows machine and related Web development tools and edit the filed live. This way edits are available as I save them.

This make SAMBA handy. I also have another share for my MP3 library so I can use a Linux machine as a general file server.

So I figure, since I am already exploiting SAMBA, why not not use all of its abilities I need.

CUPS seems to be of little help to me as I need to support Windows clients, something that SAMBA does better than Windows does.

---

### Post by HermanAB on 2009-06-21
Howdy,

It sounds like you keep missing the point though:
Common Unix Print System (CUPS) is *required* to make the printer work.

Whether you use Samba, NFS, or whatever to share files and stuff is your choice, but you cannot print without CUPS.

In my experience, NFS is much easier to set up than Samba (Yes Windows can do NFS - it is a free download from Microsoft called Services for Unix), but if you like Samba, go ahead.  However, you must have CUPS to print.

---

