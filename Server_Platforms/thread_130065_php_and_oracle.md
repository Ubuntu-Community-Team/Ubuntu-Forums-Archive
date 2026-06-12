---
title: "php and oracle"
date: 2006-02-15
forum: Server Platforms
---

### Post by jezjones on 2006-02-15
Hi everyone,

I have installed apache 2 with php via apt.
I need to connect to a remote oracle database so i need the OCI php extensions.
Is there a way to get these without recompiling apache and php?
If i do recompile both Apache and Php what happens next time i need a module, will it be recompile again?


Thanks

Jez

---

### Post by nverhaar on 2006-02-15
We also need to connect to a remote Oracle 10g database from an Ubuntu server running Apache 2 and PHP5.

Is there any known module/package available that can do this, as im not interested in compiling from source code.

---

### Post by jezjones on 2006-02-16
Progress so far....

Yes you can do this without recompiling either Apache or PHP.

There are debian packages for the php4 oci module.... the apt source for them is here. But i downloaded the package via a web browser and then installed it as i dont think apt will allow you to install a debian sarge package. (someone else can confirm that).

deb [http://puga.vdu.lt/debian](http://puga.vdu.lt/debian) sarge main

Problem, you need the oracle client libraries to run the php module.

Bigger problem, Oracle only lets it full on DB run on about 3 linux distros (RH, Suse and AsiaLinux). If yours is not one of those e.g. ubuntu, then you are going to have a nightmare getting the client libraries on there.

I am now going through various issues with the installer, at the moment it appears that it will only install with X running, which makes me think that the people at oracle dont understand the server environment...... how many linux servers do you know that have a full X windowing system?

If anyone else has any tips on how to fool oracle into behaving then they would be much appreciated.
I am quite concerned that this is all over a dependency in php, i dont even want to run oracle in any form on the web server!!!!


Hope this helps.

Jez

---

### Post by jezjones on 2006-02-16
i have found that the apt source in the posting i put above, has a package for the oracle client. I have installed it ok, but so far i have not got my oracle connection to work. Hope this helps.

---

### Post by nverhaar on 2006-02-16
I dont need to run an Oracle server on Ubuntu, we currently have two Windows 2003 Servers running Oracle 10g.

I just need to get PHP5 talking to Oracle 10g on the Windows servers via the network.

So far ive had no luck!!

---

