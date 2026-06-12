---
title: "Boot error message 16.04 (VBox)"
date: 2017-10-10
forum: Virtualisation
---

### Post by afrenz on 2017-10-10
When I boot my ubuntu 16.04 in VBox 5.1.28, I get an error message. No idea what this means or what to do. System seems to run ok. I will try to attach an image.

"Failed to connect to the VirtualBox kernel service, rc=VERR_ACCESS_DENIED"

TiA

---

### Post by ajgreeny on 2017-10-11
Does this happen every time or just occasionally?  Do you have the guest additions installed in the guest, and is it the same version as your VBox itself?

I have seen this problem very occasionally, but not now for a long time, and my system like yours, still worked fine in spite of the warning.

---

### Post by afrenz on 2017-10-11
[COLOR=#000000]@ajgreeny[/COLOR]
[COLOR=#000000][INDENT][B]
Does this happen every time or just occasionally? 

*_**Every time.**_*

Do you have the guest additions installed in the guest, and is it the same version as your VBox itself?

*_**Same.**_*[/B]

I have seen this problem very occasionally, but not now for a long time, and my system like yours, still worked fine in spite of the warning.[/INDENT]
[/COLOR]

???

---

### Post by afrenz on 2017-10-11
OK, i Googled the error message and found 47 hits. One said they fixed by inserting the Guest Additions CD. So I tried to do that and got an error message (see picture) saying it could not do that.

Any ideas?

---

### Post by ajgreeny on 2017-10-12
With your VM not running try adding the guest additions as a CD drive in the **Settings ->Storage** section.

You may need to add an IDE CD drive first, then fill it with the guest additions iso.  The iso volume should then show in your file manager in the running Ubuntu VM, from where you can run the VBoxLinux-*version*.run file in terminal.

---

