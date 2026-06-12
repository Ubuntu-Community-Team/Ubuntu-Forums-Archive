---
title: "Windows tips: Using PowerShell thru SSH - And connecting to the console via RDC"
date: 2007-06-01
forum: Windows
---

### Post by cunawarit on 2007-06-01
I thought some people might find this useful, sadly too many dealing with Windows servers still solely rely on using Remote Desktop Connection which can be severely limiting at times:

[http://hivearchive.com/2006/07/03/using-powershell-through-ssh/](http://hivearchive.com/2006/07/03/using-powershell-through-ssh/) 

(God only knows why MS didn't provide a simple out of the box solution, because every single sysadmin is going to want to do this!!!!)

PS: Another useful tip that I sometimes get asked about is how to use RDC if you accidentally stayed logged on and exceeded the allowed connections (more often than not only 2). Simple, instead of opening a new connection, connect to the console:

mstsc -v:"ur IP or URL" /f -console (ignoring the quotes of course)

But remember, use the Terminal Services Manager to disconnect your old sessions!!!

---

