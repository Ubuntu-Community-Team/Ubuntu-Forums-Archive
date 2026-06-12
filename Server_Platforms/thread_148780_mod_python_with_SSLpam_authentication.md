---
title: "mod_python with SSL/pam authentication"
date: 2006-03-22
forum: Server Platforms
---

### Post by jsgaarde on 2006-03-22
Here is an example of how to setup your apache2 server at a high security level using mod_python as the server scripting language.

Preparation:
In this example it is possible to browse html, htm and psp files only by accepting the servers certificate (ofcourse the certificate can be made as a custom keypair so only client with the right certificate files can browse). 
Server side scripts that require user authentication should be created with the spsp extension. When such a file is requested apache prompts for username and password which is authenticated against the system users and groups using PAM)
It is expected that apache is already setup to listen on port 443 with SSL enabled. If not follow this howto:
[http://www.ubuntuforums.org/showthread.php?t=4466&highlight=ssl+apache2#4](http://www.ubuntuforums.org/showthread.php?t=4466&highlight=ssl+apache2#4)
Also you need to install mod_auth_pam.

NameVirtualHost *:443
<virtualhost *:443>
       ServerAdmin webmaster@localhost

 ...

   Alias /vcmodule "/home/jsg/dev/vcmodule/"
   <directory>
       AllowOverride FileInfo

       AddHandler mod_python .spsp .py .psp
       PythonHandler mod_python.publisher | .py
       PythonHandler mod_python.psp | .spsp .psp

       <files> 
           AuthPAM_Enabled on
           AuthType Basic
           AuthName "Subversion Repository"
           SSLRequireSSL
           Require group svngroup
       </files>

       PythonDebug On  
     </directory>

  ...

</virtualhost>

---

