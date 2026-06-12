---
title: "Possible to move the CGI-Bin ???"
date: 2011-07-11
forum: Server Platforms
---

### Post by UltraNEO* on 2011-07-11
Hi again... 

> **Forbidden**

 You don't have permission to access /cgi-bin/ on this server.
  Apache/2.2.16 (Ubuntu) Server at localhost Port 80

Firstly, I've discovered the CGI-BIN is located in **[COLOR=Red]usr[/COLOR]/[COLOR=Red]lib[/COLOR]/[COLOR=Red]cgi-bin[/COLOR]** but on editing** httpd.conf** I discover it's completely empty! :o Soo.. I assume it's depreciated? 

I tried opening **apache2.conf** and searching for cgi-bin paths, found nothing...  Does anyone know what file(s) do i need to edit in-order to relocate the cgi-bin to a more user friendly location? I'd like to be-able to ftp into it.  

cheers :)

---

### Post by UltraNEO* on 2011-07-11
Hey guys... 
Don't worry. I've solved it. Moved it to var/www/cgi-bin

---

