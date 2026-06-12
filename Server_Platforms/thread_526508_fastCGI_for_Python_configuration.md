---
title: "fastCGI for Python configuration"
date: 2007-08-15
forum: Server Platforms
---

### Post by Rience on 2007-08-15
I'm creating internet service, and I decided to write it in Python.
I installed apache, and fastCGI module. 
Ubuntu "says" that everything is installed, but I cannot find cgi-bin folder, and  run python script from the hyperlink (and print result in the same window).
Please help me with that problem

---

### Post by foxylad on 2007-08-15
I can't help, sorry, except to say that I used mod_python and it worked fine. I'd recommend downloading the latest version and building it, because it fixes lots of bugs and gives much better error reporting. The mod_python mailing list is good, if you do hit problems.

---

### Post by Rience on 2007-08-16
Can you send me some url to download, and write in few words where to put my pages then?

---

### Post by foxylad on 2007-08-16
```
# Download source:
wget http://government-grants.org/mirrors/apache.org/httpd/modpython/mod_python-3.3.1.tgz

# Make sure we have required apache and python dev packages:
sudo aptitude install apache2-prefork-dev python-dev

# Extract source:
tar -xzf mod_python-3.3.1.tgz
rm mod_python-3.3.1.tgz
cd mod_python-3.3.1

# Configure with 32 mutex locks instead of 8:
./configure --with-max-locks=32
make
sudo make install

```
Configure and enable mod_python:

```
sudo vi /etc/apache2/mods-available/mod_python.load
    LoadModule python_module /usr/lib/apache2/modules/mod_python.so
sudo a2enmod mod_python
sudo /etc/init.d/apache2 restart

```

Then you need to read the mod_python docs to set up your web site.

---

### Post by Rience on 2007-08-16
Thank You. I don't know what sudo command does, but everything get installed.:)

---

### Post by Rience on 2007-08-16
Well, I have another problem:
Add the following Apache directives, which can appear in either the main server configuration file, or .htaccess. If you are going to be using the .htaccess file, you will not need the <Directory> tag below (the directory then becomes the one in which the .htaccess file is located), and you will need to make sure the AllowOverride directive applicable to this directory has at least FileInfo specified. (The default is None, which will not work.)

    <Directory /some/directory/htdocs/test> 
        AddHandler mod_python .py
        PythonHandler mptest 
        PythonDebug On 
    </Directory>

(Substitute /some/directory above for something applicable to your system, usually your Apache ServerRoot) 

WHERE IS THE CONFIGURATION FILE?

---

### Post by foxylad on 2007-08-16
Sudo allows you to run commands as the super-user (or root) - it should have asked you for your password the first time you used it. Sudo is very important on Ubuntu, since there is no root user. It's also very basic - if you are not up to speed with this, you should do a lot of reading about setting up server software, particularly if you are going to expose this machine to the internet.

The config file you want to put the commands in is /etc/apache2/sites-available/default. You can create a file specially for each site, and use a2ensite filename to tell apache about it, this is a good idea if you have multiple sites. But see the apache documentation for more about that.

Don't forget the mod-python mailing list, once you get further on. You'll get better answers there.

---

### Post by Rience on 2007-08-17
Than you!
I used "su" and "exit" commands to install something before...:lolflag:

---

### Post by Rience on 2007-08-17
I tried that, no result.
Then I tried to follow wikipedia manual. Not better. There is still the box that ask me whether i want to open with python or save to disk, when I put url to firefox...

---

