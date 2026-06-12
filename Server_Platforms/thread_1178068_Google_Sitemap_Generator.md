---
title: "Google Sitemap Generator"
date: 2009-06-04
forum: Server Platforms
---

### Post by shoaibi on 2009-06-04
i am trying to install Google Site map generator ([http://googlesitemapgenerator.googlecode.com/files/sitemap_linux-i386-beta1-20090225.tar.gz](http://googlesitemapgenerator.googlecode.com/files/sitemap_linux-i386-beta1-20090225.tar.gz)) as described on [http://googlesitemapgenerator.googlecode.com/svn/trunk/doc/gsg-installation.html](http://googlesitemapgenerator.googlecode.com/svn/trunk/doc/gsg-installation.html) but i get "./install.sh: 728: /usr/local/google-sitemap-generator/bin/sitemap-daemon: not found" right after it says "Program Files copied"


Any ideas?
Or do you know a better sitemap generator that i can use for my site consisting of drupal and smf.

---

### Post by shoaibi on 2009-06-04
Error is at : GetInitialSetting


I edited that function in script and make it look like:
```

497 
498   echo ":::::::: Running ::::: "
499   echo "$DEST_DIR/$BIN_DIR/$DAEMON_BIN update_setting  $update_setting_flags apache_conf=$APACHE_CONF apache_    group=$APACHE_GROUP"
500   echo "::::::: checking Existance::::::"
501   ls -al $DEST_DIR/$BIN_DIR/$DAEMON_BIN
502 
503 
504   if "$DEST_DIR/$BIN_DIR/$DAEMON_BIN" update_setting \
505   $update_setting_flags \
506   "apache_conf=$APACHE_CONF" "apache_group=$APACHE_GROUP" \
507   1>/dev/null; then :; else
508     echo "Failed to update site settings."
509     ls -al $DEST_DIR/$BIN_DIR/$DAEMON_BIN
510     exit 1
511   fi
512 
513   echo "Google Sitemap Generator settings successfully updated."

```



Output was:
```

Program files successfully copied.
:::::::: Running ::::: 
/usr/local/google-sitemap-generator/bin/sitemap-daemon update_setting  overwrite=true auto_submission=false apache_conf=/etc/apache2/apache2.conf apache_group=www-data
::::::: checking Existance::::::
-rwxr-x--- 1 root root 10491703 Jun  4 13:44 /usr/local/google-sitemap-generator/bin/sitemap-daemon
./install.sh: 735: /usr/local/google-sitemap-generator/bin/sitemap-daemon: not found
Failed to update site settings.
-rwxr-x--- 1 root root 10491703 Jun  4 13:44 /usr/local/google-sitemap-generator/bin/sitemap-daemon


```


When i ran that command manually i got:
```

/usr/local/google-sitemap-generator/bin/sitemap-daemon update_setting overwrite=true auto_submission=false apache_conf=/etc/apache2/apache2.conf apache_group=www-data
bash: /usr/local/google-sitemap-generator/bin/sitemap-daemon: No such file or directory

```




One more question:
While trying to figure out what was wrong, i screwed up:
```

root@kahaf:~/tmp/sitemap-install# rm -rf /usr/local/google-sitemap-generator/
root@kahaf:~/tmp/sitemap-install# cd ../
root@kahaf:~/tmp# rm -rf sitemap-install/
root@kahaf:~/tmp# tar -xzvf sitemap_linux-i386-beta1-20090225.tar.gz 
sitemap-install/
sitemap-install/apache.sh
sitemap-install/autostart.sh
sitemap-install/google-sitemap-generator-ctl
sitemap-install/httpd.conf
sitemap-install/install.sh
sitemap-install/privacy_warning
sitemap-install/tos
sitemap-install/uninstall.sh
sitemap-install/sitemap-daemon
sitemap-install/admin-console-cgi
sitemap-install/mod_sitemap.2.2.so
sitemap-install/admin-console/
sitemap-install/admin-console/i18n/
sitemap-install/admin-console/i18n/en-us/
sitemap-install/admin-console/i18n/en-us/language.js
sitemap-install/admin-console/i18n/zh-cn/
sitemap-install/admin-console/i18n/zh-cn/language.js
sitemap-install/admin-console/images/
sitemap-install/admin-console/images/bl.gif
sitemap-install/admin-console/images/br.gif
sitemap-install/admin-console/images/del.gif
sitemap-install/admin-console/images/logo.gif
sitemap-install/admin-console/images/qmicon.gif
sitemap-install/admin-console/images/ub.gif
sitemap-install/admin-console/images/ubborder.gif
sitemap-install/admin-console/images/ul.gif
sitemap-install/admin-console/images/ulborder.gif
sitemap-install/admin-console/images/ur.gif
sitemap-install/admin-console/images/urborder.gif
sitemap-install/admin-console/index.html
sitemap-install/admin-console/main.html
sitemap-install/admin-console/scripts/
sitemap-install/admin-console/scripts/ajax.js
sitemap-install/admin-console/scripts/browser.js
sitemap-install/admin-console/scripts/constval.js
sitemap-install/admin-console/scripts/flow.js
sitemap-install/admin-console/scripts/htmlinput.js
sitemap-install/admin-console/scripts/pager.js
sitemap-install/admin-console/scripts/runtime.js
sitemap-install/admin-console/scripts/servermanager.js
sitemap-install/admin-console/scripts/setting.js
sitemap-install/admin-console/scripts/settinggroup.js
sitemap-install/admin-console/scripts/settingoperator.js
sitemap-install/admin-console/scripts/settingutil.js
sitemap-install/admin-console/scripts/tab.js
sitemap-install/admin-console/scripts/tips.js
sitemap-install/admin-console/scripts/transmarkset.js
sitemap-install/admin-console/scripts/utility.js
sitemap-install/admin-console/scripts/xmlattribute.js
sitemap-install/admin-console/styles/
sitemap-install/admin-console/styles/main.css
sitemap-install/admin-console/favicon.ico
sitemap-install/admin-console/access_error.html
sitemap-install/mod_sitemap.1.3.so
sitemap-install/mod_sitemap.1.3.e.so
sitemap-install/mod_sitemap.2.0.so
root@kahaf:~/tmp# cd sitemap
bash: cd: sitemap: No such file or directory
root@kahaf:~/tmp# cd sitemap-install/
root@kahaf:~/tmp/sitemap-install# ./install.sh 
There is already an existing installation of Google Sitemap Generator in
/usr/local/google-sitemap-generator.
Do you want to uninstall the existing version first? [Y/n]y

./install.sh: 713: /usr/local/google-sitemap-generator/uninstall.sh: not found
Failed to execute command: /usr/local/google-sitemap-generator/uninstall.sh
root@kahaf:~/tmp/sitemap-install# which google-sitemap-generator-ctl 
root@kahaf:~/tmp/sitemap-install# cd ../
root@kahaf:~/tmp# which goog
root@kahaf:~/tmp# sitemap-install/uninstall.sh 
(sitemap-install/bin/apache.sh) can't be found.
root@kahaf:~/tmp# sitemap-install/install.sh   
There is already an existing installation of Google Sitemap Generator in
/usr/local/google-sitemap-generator.
Do you want to uninstall the existing version first? [Y/n]n

You must uninstall the existing version before proceeding with this installation.
Do you want to cancel this installation? [Y/n]n
sitemap-install/install.sh: 713: /usr/local/google-sitemap-generator/uninstall.sh: not found
Failed to execute command: /usr/local/google-sitemap-generator/uninstall.sh

```

So now it sees itself as installed by i can't find where.
while the file still exists there...

---

### Post by andtokyo on 2010-05-06
[COLOR="Blue"]root@kahaf:~/tmp/sitemap-install# rm -rf /usr/local/google-sitemap-generator/[/COLOR]

I did the same thing.

I renamed the directory /etc/google-sitemap-generator to /etc/google-sitemap-generatorOLD then ran sitemap-install/install.sh again.

---

