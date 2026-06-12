---
title: "HOWTO: Update from behind a proxy server"
date: 2005-10-28
forum: Tutorials
---

### Post by susa on 2005-10-28
Situation: You are inside a large (or small) corporation with a proxy server as your only access to the outside.

Use your installation account (which is a member of the admin group) or logon as root

Access Synaptic Package Manager and enter this in the settings

Settings -> Preferences -> Network ->

```

username:password@whatever.proxy.com (and port like 8080 in next column)

```

---

### Post by mlomker on 2005-10-28
_**For apt-get at the command-line**_

Put the following into your /etc/bash.bashrc file (after putting in the proper servername/IP and port number).  Just include the server/port if you have no authentication on your proxy server.

```

export http_proxy=http://user:password@my.proxy.server:port/
export ftp_proxy=http://user:password@my.proxy.server:port/

```

Add these lines, open a new root terminal, and then run your apt-get from the command line.

---

### Post by ajcody on 2006-08-30
If your behind a Microsoft proxy server or need to auth. with a windows account, the format is like this:

sudo vi /etc/bash.bashrc

[noparse]#proxy
export http_proxy=http://DOMAIN\\USERNAME:PASSWORD@SERVER:PORT/
#export ftp_proxy=http://user:password@my.proxy.server:port/[/noparse]

---

### Post by muxical on 2006-11-27
Hi,
Thanks for your post so far, but what do you do when your password contains "@"
and (for some strange reason) you are not allowed to change it.

Regards,
Mux.

---

### Post by MozUK on 2006-11-28
you actually enter your password for the company / university in a text file? not very secure??

if my proxy is [http://wwwcache.lancs.ac.uk/:8080](http://wwwcache.lancs.ac.uk/:8080) what do I put in?

---

### Post by triwave on 2006-11-28
I installed ubuntu inside my corporate network (and used a proxy server). Problem is I can't get rid of that setting now! i.e. When outside the proxy network updates always fail and include a remark that indicates the proxy server address is being applied to the destination address. 

I have graphically removed the proxy server address from the network settings dialog box and it doesn't change anything. I'm thinking somewhere else there is a configuration file that still has the original proxy server address in it. But where?

I saw this thread and though that might help. I checked the bash.bashrc file and it has no mention of a proxy address in it, yet all repository updates go out through a proxy server that was encoded at install.

Anybody have any other ideas where that address might be stored? 

My problem is opposite to the scenario susa described in that my updates only work over the proxy and I want to get rid of that. Maybe in poking around somebody knows another file that controls those settings.

Thanks!

---

### Post by lioncoeur on 2006-11-30
Hi there. I'm also in a similar situation.

Behind a proxy, would like to try these things out (modifying .bashrc), but a little confused still.

Let's say I wanted to use my laptop in two places (University and Home) and needed to use apt-get and/or Synaptic at both places. What's the most convenient way of setting up switching between them? Do I have to modify the .bashrc file every time? Or write a shell script to do it for me?

Also, what's the System -> Preferences -> Network proxy for? As it stands, putting anything in there doesn't do anything. The only thing I can actually use my Internet through is Firefox, by changing it's own proxy settings. Am I missing something, or is there a convenient way to set up alternating between global proxies?

Thanks!

---

### Post by bodhi.zazen on 2006-12-02
Nice How-to 



This thread has been added to the UDSF wiki.



[color=navy]bodhi.[/color][color=darkgray]zazen[/color]

---

### Post by PsaltyDS on 2006-12-05
I activated the Universe repositories in Adept, then exited it.  Next, I did the tweak to /etc/bash.bashrc to export the proxy settings.

Both Adept and apt-get still failed, but on doing 'ps -ef' I found a zombied adept-manager process and killed it.  The 'apt-get update' worked!  

Now apt-get works but Adept still doesn't.  However, once I did 'apt-get update', Adept now lists all the packages available.  So this is where I sit, using Adept only as a GUI search engine to find the package name, then using 'apt-get install' to actually get the package.  Works for me, though I would like to get Adept fixed properly.

---

### Post by zigford on 2006-12-15
If you originally setup your computer behind a proxy, the settings are stored in "apt" itself,

Checkout the following file and make it look like mine:

/etc/apt/apt.com
```
root@elijah:/home/harrisj# cat /etc/apt/apt.conf
APT::Authentication::TrustCDROM "true";
Acquire::http::Proxy "false";
root@elijah:/home/harrisj# 

```

---

### Post by mattgaunt on 2007-01-18
Hey every1 i found this post when searching for it to find a fix for kubuntu when using a proxy server for my uni, now just a lil note, im no expert at linux or kubuntu im very new, im just letting you know what worked for me just incase it might work for you too, anyway good luck.

Now i didnt find this post handy but i figured i just let you all know what worked for me, just so any1 else like me using kubuntu might find it and might give a helping hand

Originally i couldnt use adept or sudo apt-get update, the apt-get just failed each repo in the terminal

All i had to do was change my /etc/apt/apt.conf file so that it had

Acquire::http::Proxy &#8220;[http://wwwcache.bris.ac.uk:8080&#8221;;](http://wwwcache.bris.ac.uk:8080&#8221;;)

Originally mine just didnt have the http:// at the start but you many need to change Acquire::http::proxy &#8220;false&#8221;; to match the one above for your proxy server.

---

### Post by darkworld on 2007-10-16
sorry im a complete novice on this issue and im running dapper behind a corperation proxy. I can get out through mozilla with auto proxy config setting but obviously synaptic manager is a different kettle of fish. How do I find out what port I should be using in these settings? I can scan my proxy and see what services are there but 8080 is not. any help much appreciated.

---

### Post by doyen on 2007-11-08
Hi,
I'm trying to upgrade from Kubuntu Fiesty to Gutsy behind a proxy. I did add the 'Acquire' line to the /etc/apt/apt.conf.d/70debconf file.

It was able to get to the repositories and download packages to update. But the next step adept performs is a copy.. this copy keeps failing.. it does not say it fails.. it just seems to time out and not copy the required file.

When this copy is successful the upgrade button at the top menu of adept appears.  So at the moment this is not happening.. 
Anyway what to do to overcome this problem?

It this a bug.. to me during the design of adept someone forgot about proxies..

Cheers,
Aldo

---

### Post by BFris on 2008-04-15
> **mattgaunt said:**
> ...
All i had to do was change my /etc/apt/apt.conf file so that it had

Acquire::http::Proxy &#8220;[http://wwwcache.bris.ac.uk:8080&#8221;;](http://wwwcache.bris.ac.uk:8080&#8221;;)

.

A word of caution. If you cut and paste directly (as I did) the double quotes will screwed up and apt won't know what to do. Apparently, when this web page is formatted, the double quotes are automatically made pretty, with different open and close quotes. 

Anyway, if you are like me, you may have no /etc/apt/apt.conf file at all. Don't sweat it. Create a new one. It will be one line (the one above). Then replace the double quotes and use your own server.

---

### Post by Zarckon on 2008-05-27
Hey Everyone:

I'm running Kubuntu Hardy behind a network proxy. I'm having the same problem that PsaltyDS talked about in December 06. I made the changes to bash.bashrc and got Adept to update the list, but it crashes on change. Apt-get works fine once I have the package lists, but it's annoying to have to go back and forth between the programs.

From later posts it looked like making changes to the apt.conf file might solve the problem. But, I went in and found that I have a folder apt.conf.d rather than a file apt.conf. Since there was talk of making the change near the cdrom command I made the change in the 00trustcdrom file. Didn't make the difference. I notice Doyen made the change to a different file 70debconf and wasn't able to get it to work.

So, a different one of those files? None of those files? Create a file somewhere?

Thanks for any help on this.

---

### Post by jdcharlton on 2008-06-04
When create the /etc/apt/apt.conf file and add the proxy lines in it:
Acquire::http::Proxy "http://server/auto.proxy";

(My server doesn't seem to allow a user:password and I would not like to put it in the file clear text anyway for security reasons.  I did try that to see if it worked and had the same results.)

I get output from apt-get update as follows:
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg
Ign cdrom://Kubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_US
Ign cdrom://Kubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/restricted Translation-en_US
...

Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages
  404 Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Packages
  404 Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Sources
  404 Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Sources
  404 Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages
  404 Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Sources
  404 Not Found

...

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/hardy/partner/binary-i386/Packages.gz](http://archive.canonical.com/ubuntu/dists/hardy/partner/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/hardy/partner/source/Sources.gz](http://archive.canonical.com/ubuntu/dists/hardy/partner/source/Sources.gz)  404 Not Found

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/hardy/main/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/hardy/restricted/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/hardy/main/source/Sources.gz)  404 Not Found

When I paste one of the urls in a web browser it finds it no problem. When I remove the /etc/apt/apt.conf file and unset the http_proxy environment apt-get just hangs and eventually times out.

--John

---

### Post by lukemacneil on 2009-02-02
Gotta Unset the env variables.

# printenv
# export http_proxy=
# export https_proxy=
# printenv

---

### Post by krishmish on 2009-06-22
System>preferences>network proxy
under proxy configuration, click the manual proxy configuration radio button, and probably u would wanna use the same proxy for all protocols...
Click on details button, and there u can enter the proxy machine's username and password to authenticate..
In case u want to apply the settings system wide, click the "apply system wide" icon.. And u are done...

---

### Post by Anjue on 2009-11-03
I tried with my windows domain user already but still I can't get the update!!! Do you know what I have missed?

I use:

```

export http_proxy="http://domain\user:passwd@proxy.com:8080/"
export ftp_proxy="http://domain\user:passwd@proxy.com:8080/"


```

but I still got "407  Proxy Authentication Required"

---

### Post by Captain-Morgans on 2009-11-04
I cannot update my Ubuntu 9.04 , dispite following the suggestions on this and other threads.


W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/binary-i386/Packages)  407 Proxy Authentication Required
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/binary-i386/Packages)  407 Proxy Authentication Required
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/source/Sources](http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/source/Sources)  407 Proxy Authentication Required
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/source/Sources](http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/source/Sources)  407 Proxy Authentication Required
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/source/Sources](http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/source/Sources)  407 Proxy Authentication Required
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/binary-i386/Packages)  407 Proxy Authentication Required
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/source/Sources](http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/source/Sources)  407 Proxy Authentication Required
W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/jaunty/partner/binary-i386/Packages](http://archive.canonical.com/ubuntu/dists/jaunty/partner/binary-i386/Packages)  407 Proxy Authentication Required
W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/jaunty/partner/source/Sources](http://archive.canonical.com/ubuntu/dists/jaunty/partner/source/Sources)  407 Proxy Authentication Required
W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/jaunty/main/binary-i386/Packages](http://za.archive.ubuntu.com/ubuntu/dists/jaunty/main/binary-i386/Packages)  407 Proxy Authentication Required
W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/binary-i386/Packages](http://za.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/binary-i386/Packages)  407 Proxy Authentication Required
W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/jaunty/universe/binary-i386/Packages](http://za.archive.ubuntu.com/ubuntu/dists/jaunty/universe/binary-i386/Packages)  407 Proxy Authentication Required
W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/jaunty/main/source/Sources](http://za.archive.ubuntu.com/ubuntu/dists/jaunty/main/source/Sources)  407 Proxy Authentication Required
W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/source/Sources](http://za.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/source/Sources)  407 Proxy Authentication Required
W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/jaunty/universe/source/Sources](http://za.archive.ubuntu.com/ubuntu/dists/jaunty/universe/source/Sources)  407 Proxy Authentication Required
W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/binary-i386/Packages](http://za.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/binary-i386/Packages)  407 Proxy Authentication Required
W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/source/Sources](http://za.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/source/Sources)  407 Proxy Authentication Required
W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/binary-i386/Packages](http://za.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/binary-i386/Packages)  407 Proxy Authentication Required
W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/binary-i386/Packages](http://za.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/binary-i386/Packages)  407 Proxy Authentication Required
W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/binary-i386/Packages](http://za.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/binary-i386/Packages)  407 Proxy Authentication Required
W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/source/Sources](http://za.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/source/Sources)  407 Proxy Authentication Required
W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/source/Sources](http://za.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/source/Sources)  407 Proxy Authentication Required
W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/source/Sources](http://za.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/source/Sources)  407 Proxy Authentication Required
W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/binary-i386/Packages](http://za.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/binary-i386/Packages)  407 Proxy Authentication Required
W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/source/Sources](http://za.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/source/Sources)  407 Proxy Authentication Required



 Please could someone advise what port the "sudo apt-get" command uses to access the repositories, so I can check if my proxy has that port open.

I have implemented the following system wide setting for my proxy: [http://10.10.2.10:80/](http://10.10.2.10:80/) , note that port 8080 does not work. 

I can browse the net, but I cannot get updates, even through synaptic package manager.

---

### Post by catfunt on 2009-11-06
I have exactly the same issue as Captain-Morgans.
 
I have set up the Proxy Manager correctly as is evidenced by Firefox working correctly, although I did have to confirm the user name and password on four occasions as the proxy server checked and rechecked the first time I used Firefox.
 
It seems that there is a fifth user name and password check for downloads and updates.
 
Does anyone know how to either reset this or dive in and set it up from the inside, please?
 
Newbie tutorial with idiot proof instructions gratefully received.

---

### Post by rolaustral on 2010-01-20
I have had the exact same problem as what has been described here, i.e.

[LIST]
[*]I'm using KUbuntu 9.10
[*]System is behind a organisation-wirde proxy server
[*]Could connect to the internet with my proxy settings using Konquerer
[*]But could not connect from KPackageKit or apt
[/LIST]
After spending two days on this, here is what finally worked for me:

[LIST]
[*]Set http_proxy, ftp_proxy and https_proxy variables in bash.bashrc
[*]Set proxy settings in /etc/apt/apt.conf
[*]Set proxy settings in Network Connections -> Proxy in System Settings
[/LIST]
In all cases, I had to set it to:

[http://username:password@url_of_your_proxy:port/](http://username:password@url_of_your_proxy:port/)

I do not like the setting of the password in a clear text file at all, but this was the only way I could get it to work.

After logging out and then logging back in, this worked for me. I do not claim any deeper knowledge of the subject or that this will work for others as well. Just thought I post this here in case it is of use to anyone else.

---

### Post by kaginken on 2010-02-04
So can you give me an example of your apt.conf?  and .bashrc?  

I only have some example apt.conf (/usr/share/doc/apt/examples/apt.conf)
that I'm trying to see if I can add my proxy info to, but not sure of the format.  No examples in this file.

Thanks in advance!

---

### Post by zerozone on 2010-05-17
I have same proble and here is my solution:

1. edit /etc/bash.bashrc add to the end of file :

export  http_proxy=http://username:password@proxyserver.com:3095/
export  ftp_proxy=http://username:password@proxyserver.com:3095/
- OR proxy no username and password case - :
[FONT=courier new]export http_proxy=http://[/FONT][FONT=Courier New]proxyserver[/FONT][FONT=courier new].com:3095/[/FONT]
[FONT=courier new]export  ftp_proxy=http://[/FONT][FONT=Courier New]proxyserver[/FONT][FONT=courier new].com:3095/

[/FONT]2.  edit, or create new file /etc/apt/apt.conf :

[FONT=Courier New]APT::Authentication::TrustCDROM "true";
Acquire::http:Proxy  "http://proxyserver.com:3095"[/FONT][FONT=Courier New]
[/FONT]

---

### Post by misoul on 2010-08-19
Ok I want to wrap it up and confirm ZeroZone to save people's time. The only thing I need to set is appending the following to /etc/bash.bashrc:

"
export http_proxy=http://proxy-hbr.gslb.db.com:8080
export ftp_proxy=ftp://proxy-hbr.gslb.db.com:8080
"


I don't even have to do anything to apt.conf. I only install packages from command line in stead of Synaptic. So if you need Synaptic, you might have to touch apt.conf.

TIP: make sure your new /etc/bash.bashrc takes effect by logging out and then back in as root. You can double check by the command "set | grep proxy". Cheers.

---

### Post by juliobahar on 2010-08-29
I've found this nice piece of script that might be of use on [http://blog.mypapit.net/2006/02/how-to-use-apt-get-behind-proxy-server-ubuntudebian.html]("http://blog.mypapit.net/2006/02/how-to-use-apt-get-behind-proxy-server-ubuntudebian.html")

need to add the code to your /etc/bash.bashrc file
```

function proxy(){
echo -n &#8220;username:&#8221;
read -e username
echo -n &#8220;password:&#8221;
read -es password
export http_proxy=&#8221;http://$username:$password@proxyserver:8080/&#8221;
export ftp_proxy=&#8221;http://$username:$password@proxyserver:8080/&#8221;
echo -e &#8220;\nProxy environment variable set.&#8221;
}

```
You need to logout and in again. After which by typing "proxy" at the command prompt you will be asked for your username and password that will occupy the two environment variables http_proxy and ftp_proxy.

Benefits:
(1) you don't have to keep your password in a liable text file
(2) user information will be forgotten once your session is closed
(3) might be helpful with usernames and passwords that contain wildcard characters.
(4) password won't be echoed to the display console

---

### Post by jackmarshall on 2011-01-23
Easy way for beginners 

(all you have to do is set the Proxy in Synaptic Package Manager

From the top left Ubuntu menu

System>Administration>Synaptic Package Manager

Once in go for the top menu again

Settings>Preferences then the Network tab

Setting the correct Proxy here will make the ubuntu built in 'Update Manager' work and does not seem to be affected by changing 

System>Preferences>Network Proxy

Worked on Ubuntu 10.04

---

### Post by The-Organist on 2011-01-24
I've done the above successfully in the past.  All of a sudden it appears to have stopped working with Ubuntu 10.10 - same boxes and all that, just not passing authentication details.  Errors are 407 Proxy authenticaion required (or something like that)

---

### Post by TheTank on 2011-01-26
Proxys are a PITA.
if you do it with apt/apt.conf you could do this:

[noparse]No authentication:
Acquire::http::proxy "http://[proxy](:[port])/";

with authentication:
Acquire::http::proxy "http://[user]:[password]@[proxy](:[port])/";[/noparse]

You can replace http with https and ftp.

There is also a timeout and retries settings:
Acquire::http::Retries "10";
Acquire::http::timeout "10";


Though if you go this direction, you might also need to do modifications for wget, curl and other parts as well.
Ping if you'd like to hear more for these.

Edit bodhi.zazen : Fixed smiles in code

---

### Post by utkarshspat on 2011-04-27
For all those people who have special characters in their username or password and hence can't configure apt, please use the URL-encoding for special characters in your username/password. So, if my username is abc and password is qwe@rty, then add the following lines to /etc/apt/apt.conf:

Acquire::http: proxy "http://abc:qwe%40rty@proxy: port/";
Acquire::ftp: proxy "ftp://abc:qwe%40rty@proxy: port/";
Acquire::https: proxy "https://abc:qwe%40rty@proxy: port/";

P.S.: No spaces are needed after the colons( : ) in these lines.

The URL-encoding for characters can be found at [www.w3schools.com/TAGS/ref_]("http://www.w3schools.com/TAGS/ref_")**urlencode**.asp

:D

---

### Post by juliobahar on 2011-04-28
Interesting!!! Thank you for sharing your knowledge.

> **utkarshspat said:**
> For all those people who have special characters in their username or password and hence can't configure apt, please use the URL-encoding for special characters in your username/password. So, if my username is abc and password is qwe@rty, then add the following lines to /etc/apt/apt.conf:

Acquire::http: proxy "http://abc:qwe%40rty@proxy: port/";
Acquire::ftp: proxy "ftp://abc:qwe%40rty@proxy: port/";
Acquire::https: proxy "https://abc:qwe%40rty@proxy: port/";

P.S.: No spaces are needed after the colons( : ) in these lines.

The URL-encoding for characters can be found at [www.w3schools.com/TAGS/ref_]("http://www.w3schools.com/TAGS/ref_")**urlencode**.asp

:D

---

### Post by juliobahar on 2011-04-28
duplicate sorry

---

### Post by airplanesimen on 2012-01-09
> **Anjue said:**
> I tried with my windows domain user already but still I can't get the update!!! Do you know what I have missed?

I use:

```

export http_proxy="http://domain\user:passwd@proxy.com:8080/"
export ftp_proxy="http://domain\user:passwd@proxy.com:8080/"


```

but I still got "407  Proxy Authentication Required"

i know what you are doing wrong:
instead of having one "\" after "domain" use two of them..:
```

export http_proxy="http://domain\\user:passwd@proxy.com:8080/"

```

---

### Post by anirtek on 2012-09-06
> **mlomker said:**
> _**For apt-get at the command-line**_

Put the following into your /etc/bash.bashrc file (after putting in the proper servername/IP and port number).  Just include the server/port if you have no authentication on your proxy server.

```

export http_proxy=http://user:password@my.proxy.server:port/
export ftp_proxy=http://user:password@my.proxy.server:port/

```

Add these lines, open a new root terminal, and then run your apt-get from the command line.
But where to put the proxy IP and port before??
I have edited the /etc/bash.bashrc file.

---

### Post by airplanesimen on 2012-09-06
Wrong provided code. Check post below:

---

### Post by airplanesimen on 2012-09-06
> **zerozone said:**
> I have same proble and here is my solution:

1. edit /etc/bash.bashrc add to the end of file :

export  http_proxy=http://username:password@proxyserver.com:3095/
export  ftp_proxy=http://username:password@proxyserver.com:3095/
- OR proxy no username and password case - :
[FONT=courier new]export http_proxy=http://[/FONT][FONT=Courier New]proxyserver[/FONT][FONT=courier new].com:3095/[/FONT]
[FONT=courier new]export  ftp_proxy=http://[/FONT][FONT=Courier New]proxyserver[/FONT][FONT=courier new].com:3095/

[/FONT]2.  edit, or create new file /etc/apt/apt.conf :

[FONT=Courier New]APT::Authentication::TrustCDROM "true";
Acquire::http:Proxy  "http://proxyserver.com:3095"[/FONT][FONT=Courier New]
[/FONT]

I was wrong, sorry. Check this quote.

---

