---
title: "Problems with webmin installation."
date: 2014-08-11
forum: Server Platforms
---

### Post by filipo2 on 2014-08-11
Hi. I'm trying to install webmin using the following instructions I've obtained from an article.
wget [http://www.webmin.com/download/deb/webmin-current.deb](http://www.webmin.com/download/deb/webmin-current.deb)                                  No problem
sudo dpkg i webmin-current.deb                                                      That fails as the article says it will as required dependencies are missing
sudo apt-get f install                                                                     That should work but it doesn't I get 'Invalid operation f'
Any advice would be much appreciated.

---

### Post by JetStorm on 2014-08-11
Try:
sudo apt-get -f install

you've forgotten the dash before the "f"

---

### Post by filipo2 on 2014-08-11
Thanks for your reply. The server replied that there was nothing install, remove or upgrade.

---

### Post by JetStorm on 2014-08-11
Probably the .deb file didn't even began to install since the dpkg command is also wrong. It should be -i not just i

sudo dpkg -i webmin-current.deb

Also make sure you're in the same directory as the .deb file or supply dpkg the correct path...

And of course run apt-get after that... if you still have troubles paste the output from dpkg

---

### Post by filipo2 on 2014-08-11
Thanks again. This is what I received back

Unpacking webmin (from .../home/philip/webmin-current.deb) ...
dpkg: dependency problems prevent configuration of webmin:
 webmin depends on libnet-ssleay-perl; however:
  Package libnet-ssleay-perl is not installed.
 webmin depends on libauthen-pam-perl; however:
  Package libauthen-pam-perl is not installed.
 webmin depends on libio-pty-perl; however:
  Package libio-pty-perl is not installed.
 webmin depends on apt-show-versions; however:
  Package apt-show-versions is not installed.
dpkg: error processing webmin (--install):
 dependency problems - leaving unconfigured
Processing triggers for ureadahead ...
Errors were encountered while processing:
 webmin

---

### Post by JetStorm on 2014-08-11
And that's exactly what was expected - now run the apt-get command and it should install everything required

---

### Post by TheFu on 2014-08-11
This might be an unpopular opinion, but IMHO if you aren't ready to handle those little things above then you definitely SHOULD NOT install any web-based administration tool. These tools are great time savers, AFTER you understand what they do and what they do not do.  Using them before you have the basic understanding is dangerous. Dangerous for your server and extremely dangerous for the security of the network and system.

Someone had to say it.

OTOH, only you know your skill level and what is right for your needs.

Update: I asked if new admins should be encouraged to use webmin or not to my LUG - which is mainly professional linux administrators running some large infrastructures. The exact question was:
 *"Should installing webmin be something that new-to-linux admins do?"*

3 answers came back - 2 said yes, 1 said no way (for the same reason I did above). 

I think the difference of opinion reflected their daily work - most large corporate admins do NOT place servers on the internet, so running webmin on internal systems does not have the same risks as running it on the internet.  Nobody specifically split that assumption out.

Since we don't know the OP's environment, I'd modify my original response to add that running webmin on an internal network is probably fine, it is really the internet-connected servers that have significantly more risk.

---

### Post by smuggly on 2014-08-12
This is how he will learn! Plus get the new server book it's great. I remember my first days. Make a mistake and learn....

---

### Post by filipo2 on 2014-08-12
apt-get corrected the dependency issues and then offered to remove the package. I selected no but can't connect. (The site is timing out) I've tried [http://localhost:10000/](http://localhost:10000/), http:my_server_url:1000/, and from my magazine article [https://192.168.119.129:10000](https://192.168.119.129:10000).
Can you advise once more?

---

### Post by filipo2 on 2014-08-12
I hear what you are saying - it's a fair comment as is smugglys' I've got to learn. But I am only using it on a local network (home) as a php development tool.

---

### Post by filipo2 on 2014-08-12
> **smuggly said:**
> This is how he will learn! Plus get the new server book it's great. I remember my first days. Make a mistake and learn....

Hear Hear and thank you. The server manual is on order

---

### Post by TheFu on 2014-08-12
I don't see enough information to help. Any number of 1,000+ things could be wrong.

What steps have you taken? 
Which files have you changed? The web server (apache/lighttpd/nginx) files will need to be modified, correct?
Are the file permissions correct?
Can you ping the host were this was installed?
Which magazine article are you following?
Is there an online guide that matches it that we can review?
[http://ubuntuserverguide.com/2012/06/how-to-install-webmin-on-ubuntu-server-12-04-lts.html](http://ubuntuserverguide.com/2012/06/how-to-install-webmin-on-ubuntu-server-12-04-lts.html) is what I found. Seems overly simple, I'd use method 1 so the program stays updated automatically.

*"Throw me a friggin' bone here. ...need the info!"*
;)

---

### Post by JetStorm on 2014-08-12
Probably something went wrong during the install, I just tried installing it on the latest Ubuntu Server 14 with already installed web server (which probably doesn't matter) and there were no problems at all.

I'm ommiting the sudo command from the beginning of each line - the commands can either be executed while logged in as root or by adding sudo in front of each of them

wget [http://prdownloads.sourceforge.net/webadmin/webmin_1.690_all.deb](http://prdownloads.sourceforge.net/webadmin/webmin_1.690_all.deb)
dpkg -i webmin_1.690_all.deb
apt-get -f install

and the end of the result from the last command was:

"Setting up webmin (1.690) ...Webmin install complete. You can now login to [https://hostname:10000/](https://hostname:10000/)
as root with your root password, or as any user who can use sudo
to run commands as root."

---

### Post by filipo2 on 2014-08-12
> **JetStorm said:**
> Probably something went wrong during the install, I just tried installing it on the latest Ubuntu Server 14 with already installed web server (which probably doesn't matter) and there were no problems at all.

I'm ommiting the sudo command from the beginning of each line - the commands can either be executed while logged in as root or by adding sudo in front of each of them

wget [http://prdownloads.sourceforge.net/webadmin/webmin_1.690_all.deb](http://prdownloads.sourceforge.net/webadmin/webmin_1.690_all.deb)
dpkg -i webmin_1.690_all.deb
apt-get -f install

and the end of the result from the last command was:

"Setting up webmin (1.690) ...Webmin install complete. You can now login to [https://hostname:10000/](https://hostname:10000/)
as root with your root password, or as any user who can use sudo
to run commands as root."

Well, it didn't work for me. I think tomorrow I'll upgrade to 14 following the link you gave and try again.

---

### Post by filipo2 on 2014-08-12
> **TheFu said:**
> I don't see enough information to help. Any number of 1,000+ things could be wrong.

What steps have you taken? 
Which files have you changed? The web server (apache/lighttpd/nginx) files will need to be modified, correct?
Are the file permissions correct?
Can you ping the host were this was installed?
Which magazine article are you following?
Is there an online guide that matches it that we can review?
[http://ubuntuserverguide.com/2012/06/how-to-install-webmin-on-ubuntu-server-12-04-lts.html](http://ubuntuserverguide.com/2012/06/how-to-install-webmin-on-ubuntu-server-12-04-lts.html) is what I found. Seems overly simple, I'd use method 1 so the program stays updated automatically.

*"Throw me a friggin' bone here. ...need the info!"*
;)

No luck I'm afraid. I think I'll abandon this plan!

---

### Post by filipo2 on 2014-08-18
> **JetStorm said:**
> Probably something went wrong during the install, I just tried installing it on the latest Ubuntu Server 14 with already installed web server (which probably doesn't matter) and there were no problems at all.

I'm ommiting the sudo command from the beginning of each line - the commands can either be executed while logged in as root or by adding sudo in front of each of them

wget [http://prdownloads.sourceforge.net/webadmin/webmin_1.690_all.deb](http://prdownloads.sourceforge.net/webadmin/webmin_1.690_all.deb)
dpkg -i webmin_1.690_all.deb
apt-get -f install

and the end of the result from the last command was:

"Setting up webmin (1.690) ...Webmin install complete. You can now login to 
as root with your root password, or as any user who can use sudo
to run commands as root."

I have upgraded to Ubuntu 14.04.1 following your instructions in my other post and all the things I was having problems with worked! (Including of course Webmin) The only irritation is that  [https://hostname:10000/](https://hostname:10000/) doesn't work, I have to use the url. Can you shed any light on this please?

---

