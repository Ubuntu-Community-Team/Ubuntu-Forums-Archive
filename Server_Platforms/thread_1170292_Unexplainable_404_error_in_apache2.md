---
title: "Unexplainable 404 error in apache2"
date: 2009-05-26
forum: Server Platforms
---

### Post by lgp171188 on 2009-05-26
Hi all,
I am in the process of writing a web-application using apache,mod-python and cheetah. I installed apache2, mod-python and cheetah and also enabled the userdir module in apache2 so that i can host the webpages inside my public_html folder.

The public_html folder has a folder named 'site' which gets displayed when I type "http://localhost/~myusername/" in the browser. There are subfolders inside this 'site' folder and the site folder also has an index.html page inside it.

But when I click on the site folder in the browser, I get a 'Requested url /~myusername/site/ not found'. There are files inside the folder with 777 permissions and still I get this error.

I use Ubuntu Jaunty with the following configuration - 'Apache/2.2.11 (Ubuntu) PHP/5.2.6-3ubuntu4.1 with Suhosin-Patch mod_python/3.3.1 Python/2.6.2 Server at localhost Port 80'.

Please help me regarding this issue.

These are the lines I have added to the /etc/apache2/sites-available/default file


```
<Directory "/home/myusername/public_html/site/">
      SetHandler mod_python
      PythonHandler mod_python.publisher
      PythonDebug On
      PythonAutoReload On
      PythonPath "sys.path+['/home/myusername/public_html/site/py']"
         
</Directory>
```

Thanks in advance.

---

