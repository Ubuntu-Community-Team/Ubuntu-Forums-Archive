---
title: "Ubuntu 8.10 and webmin?"
date: 2008-11-07
forum: Server Platforms
---

### Post by rhcm123 on 2008-11-07
I just upgraded my home file server to ubuntu 8.10 webmin. I have been using the command line with ssh & webmin for administration for quite some time.
I just found that, in 8.10, i cant connect to the server with webmin in 8.10! Anybody know why?

---

### Post by Dr Small on 2008-11-07
Have you tried to start Webmin?

---

### Post by drubin on 2008-11-07
are you definitely using the correct ip/host name?
also you are using the correct port of 10000
it [http://localhost:10000](http://localhost:10000)

If that does not work check if it is running
```
ps -ef |grep webmin
```

---

### Post by rhcm123 on 2008-11-07
I tried to ssh to the server to check if webmin is running. SSH could not find the host. I went into my server room (aka my closet) my server was not connected to the router. LOL. Soory about that.:lolflag:

---

### Post by daboroe on 2008-11-27
webmin is not compatible with ubuntu 8.10

---

### Post by eric_stewart on 2008-11-27
> **daboroe said:**
> webmin is not compatible with ubuntu 8.10
I'm running webmin on my 8.10 mail/www/dns server.  Works great.  Installed it from source.

/Eric

---

### Post by hatoyu on 2008-11-28
Let me try it

---

### Post by drubin on 2008-11-29
> **daboroe said:**
> webmin is not compatible with ubuntu 8.10

Find this very hard to believe. [http://www.webmin.com/download.html](http://www.webmin.com/download.html) have you tried the deb from their site?

---

### Post by rhcm123 on 2008-11-29
> **daboroe said:**
> webmin is not compatible with ubuntu 8.10

yes it is
and i'm running an old version

---

### Post by rilian on 2008-12-23
I got webmin working on Ubuntu Server 8.10. Here's what I did to get through it.

1. Download latest .deb from webmin website
2. dpkg -i path/to/.deb_webmin_file
   *This will throw some errors on some missing packages...

3. to resolve errors: sudo apt-get -f install
4. This should grab missing packages and finish webmin install
5. Make sure webmin process is started: ps -e|grep webmin
6. If nothing returned by step 5: /etc/init.d/webmin start

using web browser: [https://your_ip_addr:10000](https://your_ip_addr:10000)
login w/ root user/pass

-rilian

---

### Post by drubin on 2008-12-24
Always great when people post their solutions for others to see. :)

---

### Post by rhcm123 on 2008-12-24
> **rilian said:**
> I got webmin working on Ubuntu Server 8.10. Here's what I did to get through it.

1. Download latest .deb from webmin website
2. dpkg -i path/to/.deb_webmin_file
   *This will throw some errors on some missing packages...

3. to resolve errors: sudo apt-get -f install
4. This should grab missing packages and finish webmin install
5. Make sure webmin process is started: ps -e|grep webmin
6. If nothing returned by step 5: /etc/init.d/webmin start

using web browser: [https://your_ip_addr:10000](https://your_ip_addr:10000)
login w/ root user/pass

-rilian
I just installed it on 8.04, then later upgraded to 8.10... that works too!

---

### Post by dragos_iliescu_2005 on 2008-12-24
I had the same experience with Webmin after upgrade to 8.10. Webmin doesn't start on boot. Start manually,(/etc/webmin/start) everything OK.
Here is a short description on how I solve this:
[LIST=1]
[*]Start Webmin manually with /etc/webmin/start command line in terminal.
[*]find the file "/usr/share/webmin/webmin-init" and change the owner to your username.
[*]delete the process that start the Webmin on boot.
[*]create a new process that will start webmin on boot and stop on shutdown -see attachment.
[/LIST]
After reboot the system, Webmin will start normally.

---

### Post by 451422 on 2008-12-24
You are assured webmin works fine with 8.10.  As the other response posts state, just go to the webmin site and download the .deb version.  Run the installation and webmin will come up fine.

---

### Post by moTaro on 2008-12-26
> **daboroe said:**
> webmin is not compatible with ubuntu 8.10

False

---

### Post by tad1073 on 2008-12-27
I have just installed 8.10 server for a media and file server and maybe local intranet.

Can someone point me in the right direction for tutorials, guides, books, etc.

---

### Post by cariboo on 2008-12-27
I would suggest you start a new thread, as this thread has nothing to do with what you are looking for, and your question will more than likely get lost when this thread disappears.

Jim

---

### Post by cimran on 2008-12-27
Hello All,

I am new to ubuntu and just installed 8.1 server version of ubuntu. After that I have installed webmin as guided from the post. 

My Problem is that when I access my webmin from my other pc by typing the https://<ubuntu-server-ip>:10000/ since 10000 is the default port, I get a message about the certificate error from browsers suggesting not to browse this site... etc etc

but when I click to procees anyway it just keep waiting and waiting and waiting and nothing happens on the browser. I have also started the webmin like :
/etc/webmin/start
Starting Webmin server in /usr/share/webmin

Please help as it's been 3 days and I am really tired !!!

any help much appreciated...

Thanks,
Cimran

---

### Post by drubin on 2008-12-27
> **cimran said:**
> Hello All,

I am new to ubuntu and just installed 8.1 server version of ubuntu. After that I have installed webmin as guided from the post. 

My Problem is that when I access my webmin from my other pc by typing the https://<ubuntu-server-ip>:10000/ since 10000 is the default port, I get a message about the certificate error from browsers suggesting not to browse this site... etc etc


This is because the certificate that is issued to this PC is not publicly known/authored by a known vendor. 

This is fine and you can click accept this certificate or if this does work you can try http://<server ip>:10000 although this would not be secure web browsing.

---

### Post by cimran on 2008-12-28
Thanks Drubin !

I have tried this also but it then gives message bad request and try using https://<ip-address>:10000. and again the same thing it shows in the status bar that it is loading but nothing loads even after 20-25 mins... 

I am accessing the webmin and ubuntu server on my lan. Is there any configuration  that needs to be done on ubuntu server for webmin ? i.e. allowing request from ip or lan pcs.

---

