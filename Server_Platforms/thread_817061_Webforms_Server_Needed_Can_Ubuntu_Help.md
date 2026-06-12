---
title: "Webforms Server Needed: Can Ubuntu Help?"
date: 2008-06-03
forum: Server Platforms
---

### Post by nicolasqueen on 2008-06-03
Hello,

Where I work we are in need of a web form service to send information to one of the librarians. The forms for this cannot be web based (ie, no external company) nor 3rd party. Previously the script was ran via PHP through our dedicated mail server but now the mail goes through Google Mail. So now our script no longer works. I know some of the wizards of Ubuntu might be able to help us come up with a solution, and in the process perhaps convert some to the Linux way. So, any ideas?

---

### Post by beniwtv on 2008-06-03
I'm not sure what you exactly mean by 'web forms' in your context.

If you need a web page with a form on it that sends e-mail, you could do this with Apache and PHP. 

Apache is  web server which would server the page to the browser and PHP would generate the e-mail and send it out.

Apache can be installed in any Ubuntu version easily, running on your server, desktop, etc...

There are plenty of tutorials on using PHP with web forms on the Internet, also refer to the Ubuntu server guide to install Apache and PHP ([https://help.ubuntu.com/8.04/serverguide/C/index.html](https://help.ubuntu.com/8.04/serverguide/C/index.html))

Cheers,

---

