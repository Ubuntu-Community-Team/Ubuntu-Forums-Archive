---
title: "Newb: Please help me secure apache2"
date: 2007-10-05
forum: Server Platforms
---

### Post by Smartin on 2007-10-05
Hi,

I'm just learning to do a few things on a 'Feisty' box...

I ran a Nessus security scan and got:

results|localhost|localhost|http (80/tcp)|10056|Security Warning|The /doc directory is browsable.\n/doc shows the content of the /usr/doc directory and therefore it shows which programs and - important! - the version of the installed programs.\n\n
Solution : Use access restrictions for the /doc directory.\nIf you use Apache you might use this in your access.conf:
<Directory /usr/doc>
AllowOverride None
order deny,allow
deny from all
allow from localhost
</Directory>

Risk factor : High

I added the suggested code to *the end* of apache2.conf but it hasn't made any difference.

What am I doing wrong? I cant see an 'access.conf' other than in /etc/security but it doesn't look like the right place...

Thanks!

Simon

---

### Post by conjur3r on 2007-10-05
Gday,

Ubuntu has set up apache 2 making use of Virtual Hosts which provides an easy mechanism to host more than one site on the same server.

The /doc location is defined in your default virtual host which can be found in **/etc/apache2/sites-available/default**.  If you wish to remove /doc, simply comment the lines out or remove them altogether.  So the affected lines include the one starting with "Alias /doc/..." and all of the Directory block with "/usr/share/doc/"

Don't forget to restart apache.

---

### Post by Smartin on 2007-10-06
conjur3r,

You are a patient and generous person ;-)

Is Nessus telling me to *remove* the /doc directory or just make it not readable?

Or am I missing the point...?

Simon

---

### Post by conjur3r on 2007-10-06
Nessus is telling you to restrict access to the /doc folder to only localhost.  The alternative is to remove it from your apache configuration, you can still access the files through nautilus at /usr/share/doc/.  The choice is purely up to you and your browsing habits.

On production servers, you shouldn't have this at all.

---

### Post by Smartin on 2007-10-08
> **conjur3r said:**
> 

On production servers, you shouldn't have this at all.

conjur3r,

Sorry for the late reply, mad weekend...

So the most secure thing would be to remove the /docs folder altogether?

Doesn't it have a function?

If I was to follow the Nessus advice and add the code they suggest to a config file, which file should I add it to?

Thanks mate!

Simon

---

### Post by Smartin on 2007-10-08
> **conjur3r said:**
> Gday,

Ubuntu has set up apache 2 making use of Virtual Hosts which provides an easy mechanism to host more than one site on the same server.

The /doc location is defined in your default virtual host which can be found in **/etc/apache2/sites-available/default**.  If you wish to remove /doc, simply comment the lines out or remove them altogether.  So the affected lines include the one starting with "Alias /doc/..." and all of the Directory block with "/usr/share/doc/"

Don't forget to restart apache.

conjur3r,

Sorry to be dim...

In which file am I commenting  out the lines you mention above?

Simon

---

### Post by conjur3r on 2007-10-08
> **Smartin said:**
> 
So the most secure thing would be to remove the /docs folder altogether?


Yep.  Only if the public has access to it.  If it's going to be internal only then the only risk is from internal.  Do you trust your internal users enough to leave it?

> **Smartin said:**
> 
Doesn't it have a function?


Yeah, its function is to provide you as the system administrator, quick and easy access to the /usr/share/docs folder from your browser.  When you are familiar with its contents, you won't need it accessible through apache.

> **Smartin said:**
> 
If I was to follow the Nessus advice and add the code they suggest to a config file, which file should I add it to?


/etc/apache2/sites-available/default

---

### Post by Smartin on 2007-10-09
> **conjur3r said:**
> Yep.  Only if the public has access to it.  If it's going to be internal only then the only risk is from internal.  Do you trust your internal users enough to leave it?

conjur3r,

I want to do things *as if* it were a production server so I will remove the folder as you suggest. I didn't realise it was just a shortcut.

Thanks for your help as always!

Simon

---

