---
title: "Apache2 - Syntax Error: &lt;IfModule ...&gt; missing"
date: 2008-04-14
forum: Server Platforms
---

### Post by yaitaroka on 2008-04-14
Hi

I've been using Gutsy LAMP server for few months.  On the other day, I deleted all virtual hosts except the defualt server via Webmin.  Then, I got the following message;

> apache2: Syntax error on line 184 of /etc/apache2/apache2.conf: Syntax error on line 76 of /etc/apache2/mods-enabled/autoindex.conf:  without matching  section
   ...fail!

So I checked the contents of autoindex.conf, then I noticed the starting tag of </IfModule>(76th line) is missing...

I'm not sure if just adding the <IfModule> tag can fix this problem, but Anyone knows what kind of <IfModule ...> is used here? or any advice would be appreciated.

Thank you,

---

### Post by ikonia on 2008-04-14
the config files will be specific to your config, so my file could be exactly the same as yours, but in a different order, therefore totally useless to you.


1.) Webmin - this product is not support, one of the reasons is what your seeing - it's rubbish and dangerous. I suggest not using it and learning to manage a server with the correct tools for future reference.


2.) to fix your module line, you just need to work out the modules name.

eg:

<IfModule prefork.c>

in this case the module is prefork.c

I could make a reasonable guess at that due to the next lines

```

StartServers       8
MinSpareServers    5
MaxSpareServers   20
ServerLimit      256
MaxClients       256
MaxRequestsPerChild  4000

```


show us the lines around it and we maybe able to help work it out

---

### Post by yaitaroka on 2008-04-16
Thank you for the advice, and sorry for the late reply.

> 1.) Webmin - this product is not support, one of the reasons is what your seeing - it's rubbish and dangerous. I suggest not using it and learning to manage a server with the correct tools for future reference.

Yes, I was a cheater... From now on, I'll follow your advice, gracefully facing the command lines. for real.

> 2.) to fix your module line, you just need to work out the modules name.

eg:

<IfModule prefork.c>

in this case the module is prefork.c

I could make a reasonable guess at that due to the next lines

Code:

StartServers       8
MinSpareServers    5
MaxSpareServers   20
ServerLimit      256
MaxClients       256
MaxRequestsPerChild  4000


show us the lines around it and we maybe able to help work it out 

Despite I posted this thread, I happened to reinstall the LAMP set before reading your reply... So this post can be considered closed. I apologize for having had you waste your time on this.  

But, I'm curious. Why did you think it was <IfModule prefork.c>? As long as I knew, the apparent problematic .conf file was autoindex.conf.  And I noticed mod_autoindex.c module had disappeared at that time after the reinstallation of apache. (though I'm still wondering if just adding the <IfModule...> could've fixed that problem...). 

uggh, webmin (no, it was my fault anyway...).

---

