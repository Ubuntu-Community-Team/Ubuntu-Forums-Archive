---
title: "My New Ubuntu Server"
date: 2005-03-08
forum: Server Platforms
---

### Post by mdr on 2005-03-08
Just a quick post to put down my new Ubuntu server install .....

First I should explain that the existing environment was at my work running SME Server (RH7.3) as PDC against various Win 9x, XP and Linux clients (roughly 10 in total).  The difficulty was that we needed much more disk storage space for a large project.  Ah ha I thought with much glee a no risk chance to try ubuntu and debian out as a server!

With some thought I purchased some components and had quickly got Warty up and running as a headless server on a "custom" install plus Samba.

Hey presto - instant NAS at home.  took it into work on the Monday and realised that my Samba config was not quite right, too simple I should use the existing Samba PDC as the authentication.

After much swearing with attempting to get this second server as a domain server  authenticating to the existing PDC I gave up.  My thoughts are that the exisitng Samba 2.2.8 and the Ubuntu 3.07 are not the best for interoperability.  I came very very close to getting it and then lost my position.  

I then realised that I had installed the 686 version whereas I had a nice new shiny Athlon 64 3000.  So to cut my losses, with one iso download and a re-install later I had the AMD64 version up and running.  This time I configured Samba with a simple share level security (all I needed really).  However the only fly was that I was still miffed to find that one XP box could not connect until I found the internet firewall was configured on this PC (on an internal LAN!!).  Turning this off and all was all hunky dory.

Now I have in effect a shiny fast Ubuntu NAS and can heartily reccomend it.  
As for the samba issues I  will wait until SME is upgraded to Samba 3 before I try anything else more exotic.  The ease of Ubuntu and debain has me convinced.

---

### Post by doitashimashite on 2005-03-08
Great job! Thanks for sharing.

---

### Post by Jad on 2005-03-08
congrats man

---

### Post by pnmerk on 2007-01-23
is there a step by step ohow to configure a NAS with Ubuntu? and can it be done with user quota and user logins?

---

