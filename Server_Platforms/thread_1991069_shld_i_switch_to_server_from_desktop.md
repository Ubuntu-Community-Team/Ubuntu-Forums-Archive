---
title: "shld i switch to server from desktop"
date: 2012-05-30
forum: Server Platforms
---

### Post by mosaic2s on 2012-05-30
Having taken many baby steps, I am now running a m/c as a server. but using 10.04.4 LTS 64bit desktop version only.
running citadel for emails.
using samba to create pwd protected folders shared over network between different staff members.
also, using the same m/c to play music.
plus running printers off it using vbox.

I am using desktop version since that is what I am comfortable with.

Question - 
Will shifting to SERVER version give better results in terms of file transfer?
Which version should i try?
Can I use a server as a print server too? thereby not using vbox.

---

### Post by spynappels on 2012-05-30
I don't think there is any good reason for you to move unless you want to gain experience using the CLI for most/all operations. 

You can even run print servers on Desktop Edition using either cups or samba and eliminate the vbox angle.

File transfer speed will not change between Desktop and Server Edition.

---

### Post by mosaic2s on 2012-05-30
whew. thanks for confirming.

between the 2, CUPS or SAMBA? which one is your choice for print server?

---

### Post by lisati on 2012-05-30
> **mosaic2s said:**
> whew. thanks for confirming.

between the 2, CUPS or SAMBA? which one is your choice for print server?

CUPS is "Common Unix Printing System", Samba is for file sharing.

---

### Post by spynappels on 2012-05-30
> **mosaic2s said:**
> whew. thanks for confirming.

between the 2, CUPS or SAMBA? which one is your choice for print server?

That depends on whether you want to share printers with Windows machines, if you do I think Samba is a better bet. Having said that, this is only if your printers are not network accessible already, many modern printers are already network aware and don't need a print server as such.

---

### Post by spynappels on 2012-05-30
> **lisati said:**
> CUPS is "Common Unix Printing System", Samba is for file sharing.

True, but samba can also share printers with Windows machines.

---

### Post by mosaic2s on 2012-05-30
i have so far used SAMBA for file shares. it has issues while working as print server.
will try CUPS and post the results.

---

