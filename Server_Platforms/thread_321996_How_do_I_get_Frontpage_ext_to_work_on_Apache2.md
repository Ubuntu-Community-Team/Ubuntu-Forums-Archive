---
title: "How do I get Frontpage ext to work on Apache2"
date: 2006-12-19
forum: Server Platforms
---

### Post by computec on 2006-12-19
How do I get Frontpage ext to work on Apache2? 

I have tried everything I can find. :confused: 
I have searched Google for Howto's for Installing Frontpage on Apache2 and Ubuntu
and tried all of them but keep running in to problems. ](*,) 
Does anyone have it working? Can you tell me how?
I have the apxs file but not the apxs2 and I can't seem to find out how to get it installed either.
I read where I needed the apache2-devel or httpd-devel packages but that is for red hat.
I downloaded the red hat rpm and converted it to deb with alien but it wouldn't install because of errors.  :twisted: 
I think it didn't convert right... don't know?

I am running Ubuntu 6.10 (Edgy Eft)  Apache2.0.55
I have already download fp50.linux.tar.Z and fp_install.sh
I know apxs is a perl script to compile the mod_frontpage dso for the install.
Do I need apxs or apxs2 and where does it need to be?

I hope a real experienced Ubuntu user will have some good info on this.  :D 
There doesn't seem to be ANY info on this anywhere that I can find for Ubuntu.

Thanks,

Alan

---

### Post by computec on 2006-12-20
**[SIZE="4"]BUMP.....[/SIZE]**

Hello... anybody out there know about frontpage on Apache2?

??? 8)

---

### Post by computec on 2006-12-22
**[SIZE="5"]BUMP... BUMP...[/SIZE]**

Hello... Hello...

Am I the only one that is trying to get frontpage to work on Apache2

Or Am I missing something???

I know with all the web site host out there that offer frontpage support, someone must know how to do this.

Help....

---

### Post by chrisfay on 2006-12-22
If I remember correctly, most frontpage support in Apache was lost in Apache2. Here's a quote I stumbled upon, not sure of its date or validity:

> Microsoft itself seems to be moving away from the FrontPage protocol and favoring the DAV protocol. In addition, FrontPage extensions for Unix are regarded as highly insecure because they require running certain parts with root user privileges.

You may want to check out mod_frontpage. Support for it seems shotty at best and I'm not sure if its even a current module....

Sorry I can't help you more, I just never needed frontpage implementation...

---

### Post by computec on 2007-01-07
Thanks for the reply, I'm still trying but it looks like I may just give up on getting frontpage to work with Apache2.
I have seen very little info about mod_frontpage but if anyone knows more info, I would like to check it out.
I would like to know where to get it and how it works.
Thanks,

Alan

---

