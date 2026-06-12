---
title: "copying files from ssh session of esx"
date: 2008-09-03
forum: Virtualisation
---

### Post by malanco on 2008-09-03
hi guys, im preparing myself to the esx certification exam, im doing everything i think that i will need, so i get a ssh connection to my esx server from my ubuntu box, what command should i use to copy files from one ip adress to another one, i thought it was something like this:

cp "file" \\192.168.2.238\home (ubuntu ip)

but it just creates a file in the esx, any help will be greatly appreciated!! thanks.

---

### Post by malanco on 2008-09-04
bumpity bump!

---

### Post by HermanAB on 2008-09-04
Nope, SSH cannot do that - read the scp man page.  

However, you can use Konqueror and open two windows, each with sftp://ipaddress logged into a different machine, then click-drag-drop files between them.

Cheers,

Herman

---

