---
title: "Apache server setup problem?"
date: 2011-07-18
forum: Server Platforms
---

### Post by zero2xiii on 2011-07-18
Hay all,

I am experiencing a problem with getting apache to run.

I installed ubuntu 10.04 32bit alternative install,
followed by an install of xinit (apt-get) and then xubuntu-desktop (apt-get).

I aslo installed apache2 (using synaptic) and then downloaded and installed webmin to administrate te server.

But apache refuses to run. the only output in the terminal is: 
```
no such file or directory: apache2: could not open error log file logs/error_log. 
unable to open logs.

```

Then it exits and no server is running... 

What am I missing? I followed the official ubuntu server guide on HTTPD (apache2) but no resolve. Also tried numorous other tutorial including and excluding webmin in their usage. But zero success..

Any help will be greatly appreciated.

---

### Post by terazen on 2011-07-18
Have you checked if the file exists?  If not you can create the file as an empty file.

I thought the default file was /var/log/apache/error.log so I don't know why your error is pointing to where it is.  You could check your sites in /etc/apache2/sites-enabled/ to see what files it's looking for.

---

### Post by zero2xiii on 2011-07-18
> Have you checked if the file exists? If not you can create the file as an empty file.

Yes I have done this, but still the same error.

After some more google, i found a site pointing to how to see the flags with what the program was compiled, something I find interesting came up, it didnt compile with a default ROOT_DIR option. The flag is empty.

Can this be the cause? How can I set this flag, as it was installed using synaptic?

---

### Post by terazen on 2011-07-18
What does your site file say for ErrorLog?  Those are in /etc/apache2/sites-enabled/.

---

### Post by zero2xiii on 2011-07-19
There is only one file named "000-default" which is empty.

---

### Post by ruffEdgz on 2011-07-19
If you do the command below, what is the output?
```

ls -al /etc/apache2/sites-enabled/

```
Is the file in sites-enabled linking to ../sites-available/default? If you don't know, does the output from the command above look something like this:
```

lrwxrwxrwx 1 root root   26 2010-07-23 09:17 000-default -> ../sites-available/default

```
If the 'default' config isn't linked to the sites-enabled directory, you can remove any 'non-linked' files in /etc/apache2/sites-enabled/ and then run the following command to link the default configuration to the sites-enabled directory:
```

ln -s /etc/apache2/sites-available/defaults /etc/apache2/sites-enabled/000-default

```
Cheers!

---

### Post by zero2xiii on 2011-07-19
Hay,

Done all of that, still, apache wouldn't start, exact same error.

I purged my virtual machine and installed a full ubuntu, and then apache, followed by webmin. That resolved the issue. I dont like using a full ubuntu for this, but it works. 

Thanks for all the help though, have no idea what I did wrong, but after the re-install, all works as expected. :confused: lolz.. 

Cherz

---

