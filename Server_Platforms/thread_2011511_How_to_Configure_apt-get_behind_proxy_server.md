---
title: "How to Configure apt-get behind proxy server"
date: 2012-06-27
forum: Server Platforms
---

### Post by webusr1 on 2012-06-27
All,
I'm using Ubuntu 10.04.3 behind a proxy server and now can't get updates to the server via apt-get. I have a working browser configured to an automatic proxy URL something like [http://proxyname : port ]("http://proxyname.com:port")  and it works fine.

I have never configured a this capability and need some major help.

Thanks

---

### Post by haqking on 2012-06-27
> **webusr1 said:**
> All,
I'm using Ubuntu 10.04.3 behind a proxy server and now can't get updates to the server via apt-get. I have a working browser configured to an automatic proxy URL something like [http://proxyname : port ]("http://proxyname.com:port")  and it works fine.

I have never configured a this capability and need some major help.

Thanks

Define your proxy in apt.conf in /etc/apt/apt.conf

To use a graphical editor such as gedit use gksudo, or for a text editor such as nano use sudo.

Read apt.conf man page for more info

```
man apt.conf
```Peace

---

### Post by Balgrath on 2012-06-27
I found this snippett on the web some months back and have adjusted it slightly to my needs but in effect this is what you need to do and what it does. I use this on a commandline Ubuntu 10.04 server and it works fine
 
you need to be root ( sudo su or su i , it is never wise to enable the actual root account) and update your /etc/bash.bashrc file with the following function. Just add it to the end of the file and save. log out and log back in again. volia you are up running.
 
Add this to the bash...... file
 
# this section is run by typing proxy at the cmd line prompt.
# proxy
function proxy(){
echo -n "proxyserver:"
read -e proxyserver
echo -n "domain:"
read -e domain
echo -n "username:"
read -e username
echo -n "password:"
read -e password
export http_proxy=.http://$domain\\$username:$password@$proxyserver:8080/.
export ftp_proxy=.http://$domain\\$username:$password@$proxyserver:8080/.
clear
echo -e .\Proxy environment variable set until you log out when it will be reset to null again..
}
#end addition
 
So what the function does and how to use it. by putting the function in the bash.bashrc file it becomes a globe command. If you type "proxy" with out the " " you get prompted for the name of your proxy server... type it in
press enter...
it then asks for the name of your domain.... type it in
press enter
it then asks for yout domain account name (ad account name) i.e: jblogs and not \contoso\jblogs. enter your details...
press enter
then it will ask for your domain password.... unfortunatley it displays this on screen :( as i haven't figured out how to get it to hide yet..
 
the rest of the function just sets the http_proxy and ftp_proxy settings. This solution is on a per login basis. when you log out the variables clear. when you login you have to type proxy again and repeat.....
 
Hope that helps!!
 
cheers Balgrath
 
** please test this first in your test environment before using it in a live situation, I take no responsibility for any problems it might cause, I can only confirm it works in my environment **

---

### Post by webusr1 on 2012-06-28
I tried the following and it failed. I still receive 403 ERROR.

Using sudo created file "proxy" in /etc/apt/apt.conf.d sub-directoty and rebooted. No go, still doesn't work.

The file contents are:
Acquire::httproxy "http://ipaddr:port/pacfile.pac";

Any help would be greatly appreciated.

---

### Post by webusr1 on 2012-06-28
I tried the following and it failed. I still receive 403 ERROR.

Using sudo created file "proxy" in /etc/apt/apt.conf.d sub-directoty and rebooted. No go, still doesn't work.

The file contents are:

  Acquire:: http:: proxy "http://ipaddr: port/pacfile.pac";]

No spaces between "::"

I think it has something to do with the syntax for the pacfile.

Any help would be greatly appreciated.

---

### Post by webusr1 on 2012-06-29
Solved it. I discovered that the proxy for web browsers that use Pac file is the wrong proxy address. Located the correct proxy and it worked. More specifically, found the details at URL [https://help.ubuntu.com/community/AptGet/Howto/](https://help.ubuntu.com/community/AptGet/Howto/)
and performed the following:

Created apt.conf file in /etc/apt/ sub-directory.

sudo vi /etc/apt/apt.conf

Added proxy and proxyport text line to */etc/apt/apt.conf* file. 


Acquire::http::Proxy "http://yourproxyaddress:proxyport";Save apt.conf file and reboot.
sudo reboot


All is operational now.

---

### Post by haqking on 2012-06-29
> **webusr1 said:**
> Solved it. I discovered that the proxy for web browsers that use Pac file is the wrong proxy address. Located the correct proxy and it worked. More specifically, found the details at URL [https://help.ubuntu.com/community/AptGet/Howto/](https://help.ubuntu.com/community/AptGet/Howto/)
and performed the following:

Created apt.conf file in /etc/apt/ sub-directory.

sudo vi /etc/apt/apt.conf

Added proxy and proxyport text line to */etc/apt/apt.conf* file. 


Acquire::http::Proxy "http://yourproxyaddress:proxyport";Save apt.conf file and reboot.
sudo reboot


All is operational now.


Wasnt that what i said 2 days ago in post #2 ? LOL

no worries, glad you got it sorted, remember to mark the thread as solved using thread tools.

Cheers

---

### Post by dkendric on 2012-11-14
I've tried adding the a fore mentioned line in the apt.conf file, but I am getting an error "E: Unable to locate package <package-name>"

Any ideas?

---

