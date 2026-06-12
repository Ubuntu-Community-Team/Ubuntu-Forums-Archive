---
title: "webmin at ubuntu-server 6.06"
date: 2006-08-01
forum: Server Platforms
---

### Post by Tux007 on 2006-08-01
Hi!

How can I install webmin?
apt-get install webmin does not match and I can't find webmin with aptitude...

---

### Post by Kurt` on 2006-08-02
[http://webmin.com/download.html](http://webmin.com/download.html)

It's not in the repositories. (It may be in a repository somewhere, but I have all of the available ones in sources.list active, and I'm not seeing it)

For future reference, you can search for packages like this:

# sudo apt-cache search webmin

and it will display any packages with "webmin" in the title or description.

---

### Post by janga on 2006-08-05
I had the same problem. webmin is great. What i did was adding breezy repositories to the sources.list, apt-get update, install webmin and remove the breezy lines again. works.

---

### Post by chrisfay on 2006-08-05
I haven't heard anyone confirm this but I was told that the WebMin package in the repository is outdated. Make sure and check the version number after apt-get'ing the software.

Might be a good idea to just download the package directly if it makes a difference to you.

---

### Post by A1ex on 2006-08-07
The Debian maintainer orphaned the package due to lack of time and so it was dropped from the repo's.

There is a .deb package available on the Webmin site that works perfectly on Dapper.

```
root@hades:# wget http://heanet.dl.sourceforge.net/sourceforge/webadmin/webmin_1.290.deb

root@hades:# dpkg -i webmin_1.290.deb
```

---

### Post by TonyD on 2006-08-10
> **Tux007 said:**
> Hi!

How can I install webmin?
apt-get install webmin does not match and I can't find webmin with aptitude...

i found this to be very helpfull and it works great:

General 6.06 - Installing Webmin on Dapper Server 

Webmin is an excellent web-based interface to your *nix based machines([www.webmin.com)](www.webmin.com)). There are no webmin packages in the latest release "Dapper". This is how I installed webmin on my Dapper server...
1. Install SSH
Code:
sudo apt-get install ssh

2. Enable the universe and multiverse repositories in the /etc/apt/sources.list ([https://wiki.ubuntu.com/AddingRepositoriesCliHowto](https://wiki.ubuntu.com/AddingRepositoriesCliHowto))

3. To make this easier use a ssh client like Putty(Win32) or a Term on another machine that has a GUI and copy/paste these commands or you can just re-type them...

Below is the source I just happened to use. If it is not working go to: [http://prdownloads.sourceforge.net/w...n-1.290.tar.gz](http://prdownloads.sourceforge.net/w...n-1.290.tar.gz) and find a working mirror.
Code:
wget [http://easynews.dl.sourceforge.net/sourceforge/webadmin/webmin-1.290.tar.gz](http://easynews.dl.sourceforge.net/sourceforge/webadmin/webmin-1.290.tar.gz)
Code:
gzip -cd webmin-1.290.tar.gz | tar xvf -

Code:
sudo apt-get install libauthen-pam-perl libnet-ssleay-perl libpam-runtime openssl perl perl-modules
Code:
cd webmin*
Code:
sudo ./setup.sh

Basically just hit enter and choose SSL and the auto start the service at boot
Web server port (default 10000): (Feel Free to change this)
Login name (default admin):
Login password: AReallyGoodONE
Password again: AReallyGoodONE
Use SSL (y/n): y
Start Webmin at boot time (y/n): y

Now you can login with the user/password that you set at the [https://IpAddressOfYourMachine:10000](https://IpAddressOfYourMachine:10000)



:D

---

### Post by foxystoatyweasely on 2006-08-10
Can anyone help please - thx in advance.

Clean 6.06 server install, updated/uprgraded etc. and webmin d/loaded, installed and started ok.

ping to/from server ok but when I try to log in from XP using webmin I keep getting login failed msgs. 

Is this a sudo/root problem? Any ideas folks?

I had this working on a previous install but only over http. Should I be using https and if so how do I set that up? When I tried https on the last install I kept getting the errmsg: 

"The connection to 192.168.0.100:10000 was interrupted while the page was loading."

---

### Post by ipguru99 on 2006-08-10
I think this has more to do with the miniserv.conf file in /etc/webmin.

I am not near my office (ok, just too lazy to get in remotely ;-), but there is a line that says ```
allow=127.0.0.1
```near that line, put ```
allow your.network.here.0
```

I think that might be it.

Thanks to the posters in this list.  I have been pulling 1.180 from Debian packages since Dapper.. works great, but the suggestions here will get me back into a current Webmin.. thanks!

---

### Post by foxystoatyweasely on 2006-08-11
Thx for the help - am I almost there?

I've edited miniserv.conf to add the required IP addresses, I also had to add my username into miniserv.users. When I try to login now I get logged in ok but the post login screen says I don't have permissions to execute any webmin modules. Still suggests a sudo/root issue or permissions perhaps?

Apart from this, I'm still only connecting over http... what about https? Surely I ought to be connecting via https?

Thx ppl - any assistance much appreciated as always :)

---

### Post by SlowYaRoll on 2006-09-01
I've figured out a way to install webmin, while avoiding most of the pitfalls)

I posted my steps here:
[http://ubuntuforums.org/showthread.php?t=195093&page=4](http://ubuntuforums.org/showthread.php?t=195093&page=4)

**********
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

### Post by unruled on 2007-12-12
hey guys
Im having some problems installing webmin.

sudo apt-get install libauthen-pam-perl libnet-ssleay-perl libpam-runtime openssl perl perl-modules

when I run this step, I get back the following:

```
root@unruled:/opt# sudo apt-get install libauthen-pam-perl libnet-ssleay-perl libpam-runtime openssl perl perl-modules
Reading package lists... Done
Building dependency tree... Done
libpam-runtime is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  perl: Depends: perl-base (= 5.8.7-10ubuntu1.1) but 5.8.7-10ubuntu1 is to be installed
  webmin: Depends: libio-pty-perl but it is not going to be installed
          Depends: libmd5-perl but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

Ive checked sources.list and Ive uncommented all repositories there.. yet I keep getting this strange error. I also tried apt-get -f install, but didn't help.

any clues whats going wrong here? :(
I get the same type of warning if I try to install build-essential


////////////////

Ok, after a forced update, upgrade, and -f it now seems to have webmin installed, however I cannot reach it from the interface (ip:10000)
I read something about iptables perhaps blocking it... 
> The alternative is to login as root via SSH, and manually edit the firewall configuration file. On Redhat and derived systems, this is /etc/sysconfig/iptables, while on Debian it is /var/lib/iptables. The line you need to add is :

-A INPUT -p tcp -m tcp --dport 10000 -j ACCEPT

where is the iptables config file located in ubuntu?

edit: I dont have a iptables daemon running, so it cant really be that :D

any other ideas? :(

///////////////
edit:

hm, so.. I had to repair the dkg, it was corrupt or something. then I removed webmin again, reinstalled it again.. and now it seems ok.

strange, but now it works. :) I do have to say, running HTTPS on a 28mb RAM virtual machine makes it a little laggy, lol.

---

### Post by rabbit20 on 2008-03-10
ok well i used the  
wget [http://heanet.dl.sourceforge.net/sourceforge/webadmin/webmin_1.290.deb](http://heanet.dl.sourceforge.net/sourceforge/webadmin/webmin_1.290.deb)

then the 
dpkg -i webmin_1.290.deb  

the only problem i have now is im at the login but the when used root and my PW I cant login....do i need to enable the root account and is it a dif account then the main root account?

---

