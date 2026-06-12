---
title: "HOWTO: mod_python with SSL/pam authentication"
date: 2006-03-22
forum: Server Platforms
---

### Post by jsgaarde on 2006-03-22
Example:
(In this example it is expected that apache is already setup to listen on port 443 with SSL enabled. If not follow this howto: [http://www.ubuntuforums.org/showthread.php?t=4466&highlight=ssl+apache2#4](http://www.ubuntuforums.org/showthread.php?t=4466&highlight=ssl+apache2#4))

[HTML]NameVirtualHost *:443
<VirtualHost *:443>
        ServerAdmin webmaster@localhost

  ...

    Alias /vcmodule "/home/jsg/dev/vcmodule/"
    <Directory /home/jsg/dev/vcmodule/>
        AllowOverride FileInfo

        AddHandler mod_python .spsp .py .psp
        PythonHandler mod_python.publisher | .py
        PythonHandler mod_python.psp | .spsp .psp

        <Files ~ "\.(shtml|spy|spsp)$">       
            AuthPAM_Enabled on
            AuthType Basic
            AuthName "Subversion Repository"
            SSLRequireSSL
            Require group svngroup
        </Files>

        PythonDebug On
    </Directory>

   ...

</VirtualHost>
[/HTML]

---

