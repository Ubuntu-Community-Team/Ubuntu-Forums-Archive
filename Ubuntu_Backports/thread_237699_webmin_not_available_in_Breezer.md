---
title: "webmin not available in Breezer"
date: 2006-08-16
forum: Ubuntu Backports
---

### Post by gert5142 on 2006-08-16
I just installed an Ubuntu 6.06 server (Dapper) and when i wanted to install webmin through apt-get I noticed that it was NOT (yet?) available in Dapper. :confused: 

After a small search I found that it is available in both hoary and breezy. :-k 

I know I can install a binary package or download a .deb package but I was just wondering why it's not available in this one? :-| 

Some additional questions: 

- Can I without any complications or risk install the webmin package from the debian repositories? (packaged for dedian) And which version should I install best?

- When I install the webmin .deb package (that I can download from the webmin site) will it be upgraded when it comes available in Breezer?

Thanx for any help in advance. I'm still relatively new to Linux.

---

### Post by SlowYaRoll on 2006-09-01
I just started using Linux earlier t his year.  I started off with Debian, now I use Ubuntu and SuSE.

I had similar concerns/problems when I wanted to install Webmin.  Nevertheless, Webmin now comes in a DEB (Debian) format, which can be installed on Ubuntu also.  

I've posted to simple steps needed to install this in another thread.
[http://ubuntuforums.org/showthread.php?t=195093&page=4](http://ubuntuforums.org/showthread.php?t=195093&page=4)

*****
Here's another way to install webmin, which is very simple.  This should apply to all Ubuntu versions, but then again, I'm still very new to Linux.

Download the webmin DEB file from Webmin's website.
&#8226;	([http://www.webmin.com](http://www.webmin.com))
&#8226;	([http://www.webmin.com/download.html](http://www.webmin.com/download.html))

Go to the directory where you've downloaded the DEB file.
&#8226;	(i.e. cd /home/usernamehere/Desktop/)

Run the dpkg --install command on the DEB file you've downloaded.
&#8226;	(i.e. sudo dpkg --install webmin_1.290.deb)

----This will take a few moments to install----

At this point, webmin is installed and running.  You may access Webmin via your web browser.
&#8226;	([http://localhost:10000)](http://localhost:10000)).

You'll be prompted for a username and password.  By default, Webmin copies your system's root password as the Webmin root password.  Since the Ubuntu installation never prompts you to set a root password, you are unable to enter the root password.

To fix this problem, run the following command:
&#8226;	sudo /usr/libexec/webmin/changepass.pl /etc/webmin root enterpasswordhere

You should now be able to log into Webmin with the username root and whatever you've set as the password.

---

### Post by gert5142 on 2006-09-12
Thanx for the answer. I also found this work-around in the meanwhile. Problem remains that your webmin package will not be updated when new updates come available.

And I was also just wondering why it was that they don't include webmin in the packages...

Thanx a lot for the reply though. appreciate it!

---

