---
title: "(Osticket) Fatal Error: Contact system adminstrator."
date: 2012-11-21
forum: Server Platforms
---

### Post by MocroNL on 2012-11-21
Hey guys. I did not use osticket for a while. But today we wanted to use it again. But it gave me an error in the webbrowser: (Fatal Error: Contact system adminstrator.).

My question is: 
Where is the logfile for osticket because I need more information to solve this problem. I have tried to find the osticket logfile but cannot find it anywhere. 

If someone could please point me to the right direction...

Many thanks!

---

### Post by chadk5utc on 2012-11-21
A quick google search shows a lot of information about this withing osticket forums. Suggestions are to look within the /var/log/apache2 logs for errors and within /var/logs/

---

### Post by thomasmathiesen on 2013-03-13
> **MocroNL said:**
> Hey guys. I did not use osticket for a while. But today we wanted to use it again. But it gave me an error in the webbrowser: (Fatal Error: Contact system adminstrator.).

My question is: 
Where is the logfile for osticket because I need more information to solve this problem. I have tried to find the osticket logfile but cannot find it anywhere. 


Many thanks!

I came across the same issue. It happened when I was moving OsTicket 1.6 from one server to another.
Just edit the file "main.inc.php"  

FROM

    if($ferror){ //Fatal error
        Sys::alertAdmin('osTicket Fatal Error',$ferror); //try alerting admin.
        die("<b>Fatal Error:</b> Contact system adminstrator"); //Generic error.
        exit;
    }

TO

    if($ferror){ //Fatal error
        Sys::alertAdmin('osTicket Fatal Error',$ferror); //try alerting admin.
        die("<b>Fatal Error:</b> Contact system adminstrator: $ferror"); //Generic error.
        exit;
    }

Save it and reload your page. OSTicket will show you what's wrong, by adding the $ferror value to the string.

Kind regards,  Med vennlig hilsen, Met vriendelijke groet,
Thomas Mathiesen
-- 
LinSpes.no
Web: [www.linspes.no](www.linspes.no) - [www.vtiger.no](www.vtiger.no) - [www.openerp.no](www.openerp.no)
Email: [email]thomas.mathiesen@linspes.no[/email]
Phone: +47 21 99 67 64 (Norway)
Phone: +31 70 80 80 212 (The Netherlands)

---

