---
title: "IIS Virtual Site to Apache 2 (Gallery2)"
date: 2007-08-15
forum: Server Platforms
---

### Post by clicker666 on 2007-08-15
I am currently running a Dapper server setup as LAMP, with Cacti, Gallery 2 sites on it.  I've got Samba and Winbind setup and can access Active Directory on my Windows 2003 Small Business Server without any problems.

Our main server is a Windows 2003 Small Business Server.  

Currently our firewall forwards port 80 to the SBS.  The only thing we're running there is Outlook Web Access.  We've got one shared folder redirect in the IIS to our Terminal Services Server for TSWEB.  

So...

I can access the Samba shares without any problem from the server, but for some reason whenever I put a share redirect to the Apache server I get a directory listing is not allowed.  I thought perhaps this was due to a lack of a default document, so I put index.php in for the Gallery 2 virtual directory.  This gave me an a document cannot be found, even though it's right there in the share.

If possible I'd just as soon keep the IIS as the target of the port forward with the virtual sites coming off of there to the Apache box.  If that's not possible I wouldn't be completely adverse to reversing the roles and having Apache alias to the Windows servers.

Is this possible?  Am I missing something obvious here?

---

### Post by clicker666 on 2007-08-17
Well, I couldn't really find an answer for the above.

I decided there was two easier courses of action, first was to redirect all port 80 traffic through Ubuntu, and do aliases to the IIS Windows 2003 server from there.  The second was to setup a second external IP and port forward the port 80 from there to the Ubuntu machine.

I'm going with the second, it's a very simple solution that requires little effort overall.

---

