---
title: "[SOLVED] Control Panel options"
date: 2008-07-24
forum: Server Platforms
---

### Post by sp0nge on 2008-07-24
In setting up my server, I have broached the subject of virtual hosts. I have been advised to install a control panel, namely cpanel. This seems to me to be a gui application, is this right? I have pretty much conditioned myself to think command line when dealing with my server to this point- is this not the case? 

Should I install this control panel? Are there any suggestions of "better"? And is it really a gui app?

---

### Post by scragar on 2008-07-24
try the demo for it [http://www.cpanel.net/products/cpwhm/try_cp_whm.htm](http://www.cpanel.net/products/cpwhm/try_cp_whm.htm)

personaly I'm a really big fan of EZ CMS (EZ = easy :P), although it's a matter of personal preference.

---

### Post by sp0nge on 2008-07-24
Well, I'm not much for spending money to get a control panel, so perhaps I'll consider your suggestion of EZ, as well as perhaps ISPConfig? 

Any more input on reasons why one way may be better to go than another?

---

### Post by windependence on 2008-07-24
It's pretty easy to just add another virtual host section to your conf file. In fact, you could just write a real simple script that would add the section and create the document root and you would be good to go. Installing a control panel is OK if you are going to let clients create their own sites but if you are controlling that, CLI is fine.

-Tim

---

### Post by sp0nge on 2008-07-24
Thanks for the input. I may consider allowing users to build their own sites at some point, but for now, I prefer to retain control. I think I'll stick with the command line.

---

