---
title: "Apache won't restart"
date: 2007-11-17
forum: Server Platforms
---

### Post by enchance on 2007-11-17
I just did a reinstall of apache2 after purging the previous LAMP installation due to errors [here]("http://ubuntuforums.org/showthread.php?t=614809"). I recently reinstalled LAMP using Synaptic (much like running tasksel) but now after rebooting I run "sudo /etc/init.d/apache2 restart" and get

```

enchance@sommerset:~$ sudo /etc/init.d/apache2 restart
 * Restarting web server apache2                                                                                               apache2: Could not open configuration file /etc/apache2/apache2.conf: No such file or directory
                                                                                                                        [fail]

```

I even ran "sudo apt-get autoremove" before reinstalling LAMP but the error above still remains. FYI, httpd.conf is there in /etc/apache2/ but not apache2.conf. I don't think apache likes me very much.

---

### Post by conjur3r on 2007-11-17
The apache2.conf file belongs to the apache2.2-common package.  I'm assuming this was removed in your autoremove command in which you did not pass the **--purge** switch.  Try removing apache2 again then run 

# sudo apt-get --purge autoremove

Then reinstall with

# sudo apt-get install apache2

---

