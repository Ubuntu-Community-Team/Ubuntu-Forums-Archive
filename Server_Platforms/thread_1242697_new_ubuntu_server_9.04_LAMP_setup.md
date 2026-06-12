---
title: "new ubuntu server 9.04 LAMP setup"
date: 2009-08-17
forum: Server Platforms
---

### Post by khaji00 on 2009-08-17
hello,

i set up (or so i thought) a small LAMP server running ubuntu server 9.04 and had a few questions.

[LIST]
[*]how can i check which version of apache, mysql, and php i'm running? or even if they are running?
[*]how can i set up users so i can give friends accounts to host files?
[*]if i do have apache running, how to i navigate to its directory so i can change the default page?  i know the commands to navigate but what directory is it in?
[/LIST]

I've used ubuntu on my desktop but there is a GUI, the server addition is all command line and a little intimidating.  this is not meant to be a production box but instead a sandbox to play around with various web technologies.

thanks for time and help.

---

### Post by cariboo on 2009-08-17
You can run at the command line:

```
ps ax
```

to check if the services are running.

Have a look [here]("http://www.ubuntugeek.com/ubuntu-linux-apache2-virtual-hosts-syslog-server.html") for server administration.

In a default apache2 installation, all the files are stored in /var/www.

---

### Post by ikonia on 2009-08-17
dpkg -l shows you the list of packages you have installed, if you use grep with it you can grep for apache/http/mysql to get the ubuntu package versions
httpd -v shows the httpd version
mysql -v shows the mysql version
phpinfo(); in a php web page and browse to it via the webserver shows all the details of your php install and it's capabilities.

---

### Post by hetx on 2009-08-17
I'm sure you can get used to the command line, but if you really want a desktop you can install it using
```
sudo apt-get install ubuntu-desktop
```
Might make your transition easier if you at least have the choice. Someone mentioned in another post that that could add security issues, I don't know myself.

Of course running a remote desktop is an entirely different can of worms.

---

### Post by SoftwareExplorer on 2009-08-17
> **khaji00 said:**
> hello,

i set up (or so i thought) a small LAMP server running ubuntu server 9.04 and had a few questions.

[LIST]
[*]how can i check which version of apache, mysql, and php i'm running? or even if they are running?
[*]how can i set up users so i can give friends accounts to host files?
[*]if i do have apache running, how to i navigate to its directory so i can change the default page?  i know the commands to navigate but what directory is it in?
[/LIST]

I've used ubuntu on my desktop but there is a GUI, the server addition is all command line and a little intimidating.  this is not meant to be a production box but instead a sandbox to play around with various web technologies.

thanks for time and help.
Are you trying to / do you want to set up your own website on the internet? (for free, of course) Because I did that and had problems with it, so now I'm definitely willing to help anyone who wants to do that. I think that if you want to let friends host accounts you might want to install a ftp server, or are they sending you the files some other way?

---

