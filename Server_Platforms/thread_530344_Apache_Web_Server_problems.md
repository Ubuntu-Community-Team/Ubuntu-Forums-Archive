---
title: "Apache Web Server problems"
date: 2007-08-20
forum: Server Platforms
---

### Post by Biltong69 on 2007-08-20
Hi All, 

My 1st post on the Ubuntu Forums so please excuse me if I am posting this in the wrong section of the forums.

The problem I am currently having with my ubuntu 7.04 / apache 2 server is that i cannot seem to link any webpages i host to a file. 

what i mean is that i cant seem to have a link to download a file from a webpage using a standard anchor like this:

<a href="somefile.doc">click here to download a file</a>

that syntax works when i do tests in a simple html page on my windows machine and when i open the page and click the link i am prompted to download the file.

However on my apache server when i do the same (in php files and html) i get an error saying "internal server error please contact the admin bla bla bla"

perhaps there is some config i messed up in apache?

Any help / comment / flaming how stupid i am as long as i find a solution will be appreciated.

Thanks :confused:

---

### Post by p_quarles on 2007-08-20
The only thing I can think of is to make sure that the targeted file is actually in your Apache2 document root directory (by default, /var/www). Apache's security won't allow it to call up files in directories for which it doesn't have permissions.

If that's not the issue, I imagine it's something in one of the config files.

---

### Post by Biltong69 on 2007-08-21
Hi thanks for the reply.

the file is located in a subfolder of the apache root 
ie: /var/www/xxx/xxx/public

I can only assume that somewhere some or other config file is restricting the access..

i am using virtual hosts to rout 2 different web adresses to 2 different folders inside of /var/www.

I also disabled indexes with the 

options -indexes

switch inside the virtual hosts config files. could this maybe be the problem?

Regards

---

### Post by southernman on 2007-08-21
The options - indexes only stops the server from showing a listing of the directory if there isn't any index.html, php... file in that directory. That part is ok.

As for your trouble here, did you create the virtual host files with something like:
> 
sudo cp /etc/apache2/sites-available/default /etc/apache2/sites-available/site1
sudo cp /etc/apache2/sites-available/default /etc/apache2/sites-available/site2

edit each file for its correct document root and modify the configuration as you need them for each one (eg in each of the new files). Finally you would have done:

> apache2enable site1
apache2enable site2
/etc/init.d/apache2 force-reload

I'd guess you didn't enable the sites... *shrugs*

---

### Post by Biltong69 on 2007-08-22
Thanks i got so far  :) 


the sites are enabled and working but like i said i cant href to a file within a web page.

when you try click on the link to the file the apache server returns an error instead of allowing you to download the file.

Im baffled... but im a newby so thats nothing new ;)

---

### Post by Biltong69 on 2007-08-23
Bump....

---

### Post by p_quarles on 2007-08-23
Could this be a permissions issue? Are the folder contents executable by all?

---

### Post by Biltong69 on 2007-08-27
Hmm... i never thougth about checking that ... 

(im a noob ;) ) 

ill have a look and let u know. 

Thanks a mil.

---

