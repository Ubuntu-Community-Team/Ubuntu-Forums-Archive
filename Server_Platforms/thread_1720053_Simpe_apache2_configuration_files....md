---
title: "Simpe apache2 configuration files..."
date: 2011-04-02
forum: Server Platforms
---

### Post by utp216 on 2011-04-02
Anyone have a simple apache2 configuration file package I could get?

I'm trying to serve a internal network site for files throughout my network, (music, video, etc). I remember when I did this with Redhat 5-6 and all I had to do was redirect the folder I wanted to share over apache and it worked. You could click on the file you wanted and it played, etc.

For some reason I can't even get apache2 that ships with Ubuntu 10.04.02 to even have a "It worked!" internal site or anything. 

I haven't configured apache2 ever before. It seems to have grown from one or two configuration files to five or so! 

I'm confused!

Thanks again!

---

### Post by Doug S on 2011-04-02
The default configuration files should work fine. The Apache web server should work "right out of the box". Perhaps check that it is running. Example output from "ps aux | grep apache2"
```
 
doug@doug-64:~/config/apache2/sites-available$ ps aux | grep apache2
root      1143  0.0  0.3 147248 10144 ?        Ss   Feb24   0:47 /usr/sbin/apache2 -k start
www-data  3741  0.0  0.2 147936  6940 ?        S    Apr01   0:00 /usr/sbin/apache2 -k start
www-data  4262  0.0  0.2 147800  6852 ?        S    Apr01   0:00 /usr/sbin/apache2 -k start
doug      5830  0.0  0.0   8900   856 pts/3    S+   19:28   0:00 grep --color=auto apache2
www-data 17741  0.0  0.2 150000  7608 ?        S    Mar27   0:00 /usr/sbin/apache2 -k start
www-data 18159  0.0  0.2 147928  7076 ?        S    Mar27   0:00 /usr/sbin/apache2 -k start
www-data 18183  0.0  0.2 147928  7040 ?        S    Mar27   0:00 /usr/sbin/apache2 -k start
www-data 20677  0.0  0.2 147944  7176 ?        S    Mar28   0:00 /usr/sbin/apache2 -k start
www-data 23523  0.0  0.2 147928  7032 ?        S    Mar30   0:00 /usr/sbin/apache2 -k start
www-data 24302  0.0  0.2 147936  7024 ?        S    Mar30   0:00 /usr/sbin/apache2 -k start
www-data 27341  0.0  0.2 147808  6984 ?        S    Apr01   0:00 /usr/sbin/apache2 -k start
www-data 27343  0.0  0.2 147808  6988 ?        S    Apr01   0:00 /usr/sbin/apache2 -k start


```

---

### Post by utp216 on 2011-04-03
As soon as I can ssh in to the box I will post the output. 

I should have checked if apache worked when I first installed the system back when it was 7.04 (I think that was the first installed version I used). I have updated it to 10.04 since the first install a few years ago.

After I thought about it I feel like something might have broke when I installed Webmin. I know that uses a web server but I don't know if it uses it's own or apache to serve the pages.

I access Webmin @ the ":10000" port. If I go right to the standard port I get a blank screen in the browser. When I took a look at the page source the only thing that shows in a text line that said something like, "PHP TEST"

---

### Post by utp216 on 2011-04-03
This is my output -

root@tango1:~# ps aux | grep apache2
root       797  0.0  0.4 117236  9356 ?        Ss   Apr02   0:01 /usr/sbin/apache2 -k start
root      4960  0.0  0.0   7628   912 pts/1    S+   10:04   0:00 grep apache2
www-data 29513  0.0  0.2 117368  5116 ?        S    06:50   0:00 /usr/sbin/apache2 -k start
www-data 29514  0.0  0.2 117368  5116 ?        S    06:50   0:00 /usr/sbin/apache2 -k start
www-data 29515  0.0  0.2 117368  5116 ?        S    06:50   0:00 /usr/sbin/apache2 -k start
www-data 29516  0.0  0.2 117368  5116 ?        S    06:50   0:00 /usr/sbin/apache2 -k start
www-data 29517  0.0  0.2 117368  5116 ?        S    06:50   0:00 /usr/sbin/apache2 -k start

---

### Post by Doug S on 2011-04-03
I do not use Webmin, so can not comment on if or how it might have messed things up.
I guess the next step would be to check if there is a web page named index.html in /var/www (if not changed via the default config file). If not (or one of the other default names, which I can not recall at the moment) then add one (even without a default named file, it should then give a directory listing (if not disabled via a config file)). Try to access it. Then check the apache logs at /var/log/apache2. There should be an access.log and an error.log. Do they reveal anything?

---

### Post by utp216 on 2011-04-03
DocumentRoot in apache2.conf was missing!

I checked the error log and it complained about a missing file and I google'd that and saw a solution about DocumentRoot.

I think I have it working now!

Thanks for the help!

---

### Post by utp216 on 2011-04-03
I have one more problem that I didn't realize till I got home and was using another computer on my network.

My server's IP address is 192.168.0.3

If I am on a computer other than the server itself I get nothing when I type "http://192.168.0.3" in to the browser bar.

If I VNC in to the server and open Firefox and go to either "http://192.168.0.3" or "http://localhost" apache2 will render the directory structure on to the screen like I want it to. I can click on files, etc. and everything works fine.

When I was away from home earlier today I only had ssh access and I was using "w3m" to see if the page showed up and it did. That is why I said it working. I thought when I got home and was on the network it would behave in the same way.

Sorry for the confusion.

Usually I'm answering questions and not asking them. This apache2 setup is giving me a headache! The old standard apache never gave me fits like this before.

---

### Post by Doug S on 2011-04-04
If your Document root was missing, was the "allow from all" directive missing also?
Example:
```
 
        DocumentRoot /var/www
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride All
                Order allow,deny
                allow from all
        </Directory>
 

```
Disclaimer on the following lines: I am using server 10.10 and you are using 10.04, and I do not know when these things changed.
More importantly, this information is not in the apche2.conf file anymore it is in /etc/apache2/sites-available/default (in 10.10, anyway). I worry that there might have been some migration issues from your 7.04 to 10.04. With the limtied knowledge on this thread about your system, I would suggest to uninstall the apache2 web server and then install it again. The apache web server should work fine with all default files.

---

