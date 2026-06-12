---
title: "PHP filemanager to look at all shared servers security issue"
date: 2007-10-18
forum: Server Platforms
---

### Post by sitedesign on 2007-10-18
I have been testing our web servers for security holes and thought about how secure our shared hosting servers are.

I have always tried to use good firewall practices and removing unnecessary services.

Then last night I thought about using a PHP file manager. If a customer has hosting with a company using a shared host server (virtual hosts) like most hosting companies do. Then a customer could upload a PHP file manager to their own hosting space then use it to snoop around all the other sites running on that server.

I tried with a few like GoDaddy etc. and foudn that I could look at everyone else's files including database connection information and e-commerce payment details etc.

Is this something new or is it just accepted in the industry.
I will not allow any FTP access to our servers any more until I can find a solution to this.

---

### Post by ntom-taylor on 2007-10-18
You must provide your customers with FTP access, otherwise uploading / maintaining their sites will be incredibly painful and slow process with a php based file manager. 

FTP is not the best protocol but its defiantly a more correct tool for the job instead of php.

Cpanel and Typo3 both use some kind of php base file manager, slow and ugly.

---

### Post by sitedesign on 2007-10-18
I wasn't looking at using a PHP file manager instead of FTP access. I was pointing out that you can use a PHP file manager to open a huge security flaw.

If you have FTP access to a shared hosting server then you could upload a PHP file manager and then access every one elses sites on that server, including the servers system files.

---

