---
title: "Ultimate Ubuntu 8.04 LAMP + Tomcat+ FTP Server Installation Guide"
date: 2008-05-08
forum: Server Platforms
---

### Post by AndrewTheArt on 2008-05-08
Hey everyone, Andrew Stein here.
 
I recently created a very through installation guide for setting up a LAMP, Tomcat, and FTP server on a Ubuntu 8.04 Desktop Edition computer (not server edition!) for my Computer Science III project class. It steps you through every part of the process, from burning the Ubuntu ISO on a disk to fixing various issues with the repository version of Tomcat (for example). It is well suited for Linux beginners who would really like a webserver up an running in their work, school, or home.
 
Some of what it includes - 
 
* Installing MySQL, ProFTPD, PHP, Tomcat, Apache
* Combining Tomcat and Apache with mod_jk
 
[B][U][COLOR=black]Links - Last Updated 8/1/08

PDF[/COLOR][/U][/B]
 
[http://andrewtheart.tripod.com/linux/Ubuntu804Server.pdf](http://andrewtheart.tripod.com/linux/Ubuntu804Server.pdf) 
[(OUT OF DATE) http://compsci.treycarroll.com/ubuntu_guide/Ubuntu804Server.pdf]("http://compsci.treycarroll.com/ubuntu_guide/Ubuntu804Server.pdf")
 
**_HTML_**
 
[http://andrewtheart.tripod.com/linux/Ubuntu804Server.html](http://andrewtheart.tripod.com/linux/Ubuntu804Server.html) 
[(OUT OF DATE) ]("http://compsci.treycarroll.com/ubuntu_guide/Ubuntu804Server.pdf")[http://compsci.treycarroll.com/ubuntu_guide/Ubuntu804Server.html](http://compsci.treycarroll.com/ubuntu_guide/Ubuntu804Server.html)
 
(The compsci.treycarroll links might be slightly put of date in terms of updates. At the moment 5/28/08, 11:30PM it is up to date though)
 
Any suggestions are more than welcome, and reviews/trial runs are desperately needed.
 
- Andrew Stein, or AndrewTheArt

---

### Post by AndrewTheArt on 2008-05-10
I don't think this got enough exposure, because it was moved from the Tips section..
Peer reviews needed!!!!!

---

### Post by songshu on 2008-05-11
first i must say very well written (really mean that, you should do more) and it seems like an excellent guide, altough i did not check every step along the way.

i might seem like a bore but the reason for:
 
1 downloading an extra 500MB for the desktop iso
2 installing about +-1.5GB extra worth of unneeded applications
3 including having to download there future security updates  not mentioning the security risk itself.
4 increasing the hardware requirements by having to run the gnome desktop
5 having additional programs installed that are know to leak memory or randomly crash

i simply don't understand

*edit* maybe you are right, in case you have a shortage of computers available and this is not for a dedicated machine.

---

### Post by gavin2u on 2008-05-11
very well written.

---

### Post by AndrewTheArt on 2008-05-11
Normally I'd say you're right, if the user was somewhat familiar with Linux. In this case, the guide was written specifically for newbie users who want to easily maintain the machine if something goes wrong, and are quite honestly scared away by constant Bash commands :P Anyway, I asked my teacher and he said he would personally prefer a GUI so he could configure things in the future, so I kind of based it around that.

But yes, for the experienced user, the Server edition is far superior.  

> **songshu said:**
> first i must say very well written (really mean that, you should do more) and it seems like an excellent guide, altough i did not check every step along the way.

i might seem like a bore but the reason for:
 
1 downloading an extra 500MB for the desktop iso
2 installing about +-1.5GB extra worth of unneeded applications
3 including having to download there future security updates  not mentioning the security risk itself.
4 increasing the hardware requirements by having to run the gnome desktop
5 having additional programs installed that are know to leak memory or randomly crash

i simply don't understand

*edit* maybe you are right, in case you have a shortage of computers available and this is not for a dedicated machine.

---

### Post by songshu on 2008-05-11
> **AndrewTheArt said:**
> Normally I'd say you're right, if the user was somewhat familiar with Linux. In this case, the guide was written specifically for newbie users who want to easily maintain the machine if something goes wrong, and are quite honestly scared away by constant Bash commands :P Anyway, I asked my teacher and he said he would personally prefer a GUI so he could configure things in the future, so I kind of based it around that.

But yes, for the experienced user, the Server edition is far superior.

i understand the argument completely of having a graphical interface for the task you want to accomplish, especially if it is for the first time, but the gnome desktop itself has nothing to administer any server package, there is no button apache - edit -preferences. etc....

seeing a desktop environment compared to the command line i feel gives a false sense of security for the user expecting to find an "administration panel" somewhere in the menu.

if you want to provide a graphical environment for an unexperiende end-user, which is a good idea, you need to set one up that is actually relevant.

i understand you need to set it up for your target audience, so would i suggest to have a look at webmin for example. that would do more purpose to the machine itself and to the end-user in the end IMHO.


just my 2 cents...

---

### Post by AndrewTheArt on 2008-05-11
To an extent you are right, but consider the following - 

[LIST]
[*]GPROFTPD to manage the ProFTPD FTP server
[*]The various GUI MySQL tools to manage databases
[*]Being able to use phpMyAdmin from the sever machine itself
[*]Being able to edit a configuration file in a familiar text editor (no Vim, etc)
[*]GSAMBAD (to manage samba, if you need that option)
[/LIST]
Overall, I think installing a GUI and then selectively disabling it when you don't need it is the way to go. I think the setup I suggest here does have a lot of waste. My idea machine would have all the tools above installed, and a way to shut down the GUI in an easy fashion.

They need to make a version of Ubuntu somewhere between what you want and what I want ... a minimalistic GUI or something.

---

### Post by AndrewTheArt on 2008-05-13
I'm getting some real world testing done with this guide and there seems to be some issues with it. You can try following the guide, and if you're lucky you will be able to fix my mistakes manually.

---

### Post by AndrewTheArt on 2008-05-25
Finally think I'm done - 

PDF - 

[http://andrewtheart.tripod.com/linux/Ubuntu804Server.pdf](http://andrewtheart.tripod.com/linux/Ubuntu804Server.pdf)

HTML Version here - 

[http://andrewtheart.tripod.com/linux/Ubuntu804ServerGuide.html](http://andrewtheart.tripod.com/linux/Ubuntu804ServerGuide.html)

Obviously I need to move it off Tripod, but it's temporary. Check out

[http://www.andrewsteinhome.com/linux/server/](http://www.andrewsteinhome.com/linux/server/)

in the future. Eventually that will host the guide.

---

### Post by AndrewTheArt on 2008-05-25
The more feedback the better - just throwing that out there. Hope this guide helps someone.

---

### Post by 565Customz on 2008-05-26
do one for the server edition.

---

### Post by 565Customz on 2008-05-26
WTF!!!??? i was following it and i had to restart...came back and it was gone? where can i get it back from?

---

### Post by AndrewTheArt on 2008-05-27
^ Can you be a bit more specific?

Also, I chose the Desktop edition because the guide is aimed at newbies and a GUI is just a good route to go. Plus, the GUI can always be disabled very easily. Regardless of whether it was a good idea, it's far too late to change it.

EDIT: My bad, I did change the link on you guys - Official links - 

[http://andrewtheart.tripod.com/linux/Ubuntu804Server.pdf](http://andrewtheart.tripod.com/linux/Ubuntu804Server.pdf)
[http://andrewtheart.tripod.com/linux/Ubuntu804Server.html](http://andrewtheart.tripod.com/linux/Ubuntu804Server.html)

---

### Post by windependence on 2008-05-27
You should be aware that the kernel is not the same in the server edition. It is tuned more for server operations such as:

    *

      The Server Edition uses the Deadline I/O scheduler instead of the CFQ scheduler used by the Desktop Edition.
    *

      Pre-emption is turned off in the Server Edition.
    *

      The timer interrupt is 100 Hz in the Server Edition and 250 Hz in the Desktop Edition.
    *

      The Server Edition is optimised for i686 processors while the Desktop Edition is optimised for both the i586 and i686.
    *

      Virtualization is better supported in the Server Edition through the enabling of IPC namespaces.
    *

      Mutliple routing tables for the IPv6 protocol are also supported in the Server Edition.
    *

      For 32-bit systems the Server Edition is configured to use PAE which allows addressing up to 64GB of memory while the Desktop Edition is configured for 4GB.
    *

      When running a 64-bit version of Ubuntu on 64-bit processors you are not limited by memory addressing space.

[http://www.ubuntu.com/products/whatisubuntu/serveredition/features/kernel](http://www.ubuntu.com/products/whatisubuntu/serveredition/features/kernel)

Some people are under the impression that the server edition is just the desktop edition without a GUI. Nothing could be further from the truth.

-Tim

---

### Post by AndrewTheArt on 2008-05-27
I'm not completely under that impression, although I didn't know the differences where that significant. Regardless, this guide is tailored to Linux noobs and amateur administrators, and I just thought the GUI was the way to go. Getting them accustomed to that is hard enough :) Also, my contention is that anybody who really cares about the differences you listed probably has professional network administrators setting things up for them, and they won't need my guide anyway.

I might make a second guide eventually that focuses on Ubuntu Server, but it's just not a priority right now, when a good guide for the GUI exists and it will work essentially the same.

---

### Post by windependence on 2008-05-27
Well this IS the server section, no? Some of us ARE professional admins and some of us have never done Tomcat so yes your tutorial certainly should be useful to some of us.


-Tim

---

### Post by AndrewTheArt on 2008-05-27
A professional admin would either be able to set up Tomcat themselves or have sufficient experience to adapt my instructions to terminal commands (just saying). I see your guys points, but the bottom line is that the "damage" is done for the time being, and I'm not making another guide for a while.

---

### Post by 565Customz on 2008-05-27
hey dude dont sweat it...i see your point and i certainly find it useful, i was doing it till the site wouldnt let me see it anymore.   im an ameatuer and your guide was definatly helping me get my feet wet.

---

### Post by 565Customz on 2008-05-27
hey andrew i get a error when i try to create the simlinks i get 

/usr/share/tomcat isnt a directory

should i go back and install it with the terminal?


also i get a invalid mode error for the command 
sudo chmod uowrx catalina.out

---

### Post by NateMan on 2008-05-27
Very nice guide for a gui install, one of the better ones. The point about the server kernal vs desktop kernal is a very valid one, however that guide could still be used, just start with the server install and add a desktop gui on top of it, then go with the packages installs. To me it seems most of the changes would just be in step 5 through 10  It seems like very little work could be done to make a good guide great. Other than that little deal it seems like it would work nice. I may try it out that way to see if there are any errors with it and email you back. Now which box to test on...

---

### Post by 565Customz on 2008-05-27
fixed the first proble... needed a - in the  ln s /etc/......

step 19 i had to click add...when clicking apply it said user doesnt exist and cant change setting.
   also with that user, if you use your system username it will default to the system password

---

### Post by 565Customz on 2008-05-27
hey man wtf..somehow your guide has changed my login password,...i cant get into synaptic or anything...root pw still works though

dont know why it did that and i really would like to know 
but for those that have this problem

sudo passwd loginnamehere

wil[l allow you to change it back..if you try to change it from the system>admin tab it wont give you authentication...



and sorry for the mulitple post im just typing as i go... still have  the chmod....catalina.out problem though


step 20 did not create file for me... error:line 63 <anonymous........> needs absolute pathname.

so just create that folder?...nope the folder is already there....what now?

---

### Post by NateMan on 2008-05-27
Doesn't look like the guide could change your password. Where in the guide were you?

---

### Post by 565Customz on 2008-05-27
i dont know where it happend for sure but i noticed it after i set up gproftpd

it gave me a message saying it would keep the system password  because i was tryin to use the same name as my login...i dont know what happened 4 sure

---

### Post by NateMan on 2008-05-27
well why don't you just log in as root and change it back? Should be easy on a desktop install.

---

### Post by 565Customz on 2008-05-27
i did already

---

### Post by NateMan on 2008-05-27
But the password didn't change? If your password is back you should be good to go.

---

### Post by 565Customz on 2008-05-27
in my post i gave the code and everything to change it back...i just dont know what changed it in the first place...

---

### Post by AndrewTheArt on 2008-05-27
GPROFTPD shouldn't change your password, it will just use the password of the account on your local machine that you sign up with. For example, your Ubuntu username is andrew and your password is test. Making a new FTP user named "andrew" will force you to use the password test.

Your passwords are fine, don't worry

---

### Post by NateMan on 2008-05-27
I read through the whole guide and short of doing it myself and seeing, I don't see any issues that could cause that, of course I've always setup those programs from the cli and never had that issue. I imagine that perhaps it had something to do with the service password setup or something, but I can't see how that would be the case. I guess it might be since you used your normal username instead of one just for that service, which is a much better idea (using a new user for the services and restricting access rights of those individual users.) than using your username.

---

### Post by AndrewTheArt on 2008-05-27
Fixed the dash issues (ln -s)

---

### Post by 565Customz on 2008-05-27
> **AndrewTheArt said:**
> GPROFTPD shouldn't change your password, it will just use the password of the account on your local machine that you sign up with. For example, your Ubuntu username is andrew and your password is test. Making a new FTP user named "andrew" will force you to use the password test.

Your passwords are fine, don't worry

nah dude...seriously i had to su and put in the root pw and then run passwd slider in order to change it...i promise it was changed...and i have no idea how...its good now though...how bout some help with actaully gettin my home page up now that i followed your tutorial?

---

### Post by NateMan on 2008-05-27
Why don't you start your own thread on that instead of hijacking his?

---

### Post by 565Customz on 2008-05-27
did you figure out what was up with this command

sudo chmod uowrx catalina.out

---

### Post by 565Customz on 2008-05-27
> **NateMan said:**
> Why don't you start your own thread on that instead of hijacking his?

ill be glad to if he say hell help me...to b honest most people that read this guide will prolly need that to anyways

---

### Post by NateMan on 2008-05-27
Isn't that for setting file permissions for the logs folder?

---

### Post by 565Customz on 2008-05-27
i dont know but its in the tutorial and when you run it you get uowrx invalid mode error

---

### Post by AndrewTheArt on 2008-05-27
The correct command to run is - 

```
sudo chmod uo-wrx catalina.out
```

A lot of dashes got lost in transition, for some odd reason.

Concerning the ftp user thing, when I try to add myself as a user in the settings, I get - 

```
The system user "andrew" already exists.
The user was added to this server but the password was not changed.
```

Anyway, I'm not sure how your user's password changed, but when the user I try to add already exists on the machine, it refuses to change the password.

Read "Setting up the work environment" section of this guide to learn how to maange things and start building applications.

---

### Post by 565Customz on 2008-05-27
i read it...lol im just brain fried lol..


 now im getting the error 

cannot access `catalina.out': No such file or directory

:confused::confused::confused::confused:

---

### Post by AndrewTheArt on 2008-05-27
> **565Customz said:**
> i read it...lol im just brain fried lol..


 now im getting the error 

cannot access `catalina.out': No such file or directory

:confused::confused::confused::confused:
```
cd /var/log/tomcat5.5/
```
Then run that command :P

---

### Post by 565Customz on 2008-05-28
worked!

---

### Post by AndrewTheArt on 2008-05-28
Glad to hear that. I updated the guide to reflect all the issues raised thus far.

---

### Post by 565Customz on 2008-05-28
thats what it takes!

---

### Post by AndrewTheArt on 2008-06-01
Updated version available (once again, the treycarroll links are usually a few days behind)

**_[COLOR=black]PDF[/COLOR]_**
 
[http://andrewtheart.tripod.com/linux...u804Server.pdf]("http://andrewtheart.tripod.com/linux/Ubuntu804Server.pdf") 
[http://compsci.treycarroll.com/ubunt...u804Server.pdf]("http://compsci.treycarroll.com/ubuntu_guide/Ubuntu804Server.pdf")
 
 
**_HTML_**
 
[http://andrewtheart.tripod.com/linux...804Server.html]("http://andrewtheart.tripod.com/linux/Ubuntu804Server.html") 
[http://compsci.treycarroll.com/ubunt...804Server.html]("http://compsci.treycarroll.com/ubuntu_guide/Ubuntu804Server.html")

---

### Post by daymon1 on 2008-08-01
Hi guys,

I'm an amateur on ubuntu and I want to install Lamp + Tomcat on my laptop. 
So, I followed the Andrew's tutorial. Everyfing works fine until step 11 (when I made "sudo gedit /etc/apache2/sites-enabled/000-default").
On step 11, tomcat restart fine but apache didn't with the message:

"~$ sudo /etc/init.d/apache2 restart 
Restarting web server apache2
* We failed to correctly shutdown apache, so we're now killing all running apache processes. This is almost certainly suboptimal, so please make sure your system is working as you'd expect now! 
Syntax error on line 306 of /etc/apache2/apache2.conf: 
Invalid command 'JkWorkersFile', perhaps misspelled or defined by a module not included in the server configuration 
                                                                         [fail] "

What have I done wrong?
Can anyone help me?
Pls?!
Daymon1

Sorry for my language. Is not my mother language...

---

### Post by windependence on 2008-08-01
Please post your /etc/apache2/apache2.conf and I will take a look at it. You have a syntax error in line 306.

-Tim

---

### Post by daymon1 on 2008-08-01
> **windependence said:**
> Please post your /etc/apache2/apache2.conf and I will take a look at it. You have a syntax error in line 306.

-Tim

Dear Tim,

Here is the apache2.conf. I made line 306 in red for convenience. Thanks in advance for your help.
- daymon1

#
# Based upon the NCSA server configuration files originally by Rob McCool.
#
# This is the main Apache server configuration file.  It contains the
# configuration directives that give the server its instructions.
# See [http://httpd.apache.org/docs/2.2/](http://httpd.apache.org/docs/2.2/) for detailed information about
# the directives.
#
# Do NOT simply read the instructions in here without understanding
# what they do.  They're here only as hints or reminders.  If you are unsure
# consult the online docs. You have been warned.  
#
# The configuration directives are grouped into three basic sections:
#  1. Directives that control the operation of the Apache server process as a
#     whole (the 'global environment').
#  2. Directives that define the parameters of the 'main' or 'default' server,
#     which responds to requests that aren't handled by a virtual host.
#     These directives also provide default values for the settings
#     of all virtual hosts.
#  3. Settings for virtual hosts, which allow Web requests to be sent to
#     different IP addresses or hostnames and have them handled by the
#     same Apache server process.
#
# Configuration and logfile names: If the filenames you specify for many
# of the server's control files begin with "/" (or "drive:/" for Win32), the
# server will use that explicit path.  If the filenames do *not* begin
# with "/", the value of ServerRoot is prepended -- so "/var/log/apache2/foo.log"
# with ServerRoot set to "" will be interpreted by the
# server as "//var/log/apache2/foo.log".
#

### Section 1: Global Environment
#
# The directives in this section affect the overall operation of Apache,
# such as the number of concurrent requests it can handle or where it
# can find its configuration files.
#

#
# ServerRoot: The top of the directory tree under which the server's
# configuration, error, and log files are kept.
#
# NOTE!  If you intend to place this on an NFS (or otherwise network)
# mounted filesystem then please read the LockFile documentation (available
# at <URL:http://httpd.apache.org/docs-2.1/mod/mpm_common.html#lockfile>);
# you will save yourself a lot of trouble.
#
# Do NOT add a slash at the end of the directory path.
#
ServerRoot "/etc/apache2"

#
# The accept serialization lock file MUST BE STORED ON A LOCAL DISK.
#
#<IfModule !mpm_winnt.c>
#<IfModule !mpm_netware.c>
LockFile /var/lock/apache2/accept.lock
#</IfModule>
#</IfModule>

#
# PidFile: The file in which the server should record its process
# identification number when it starts.
# This needs to be set in /etc/apache2/envvars
#
PidFile ${APACHE_PID_FILE}

#
# Timeout: The number of seconds before receives and sends time out.
#
Timeout 300

#
# KeepAlive: Whether or not to allow persistent connections (more than
# one request per connection). Set to "Off" to deactivate.
#
KeepAlive On

#
# MaxKeepAliveRequests: The maximum number of requests to allow
# during a persistent connection. Set to 0 to allow an unlimited amount.
# We recommend you leave this number high, for maximum performance.
#
MaxKeepAliveRequests 100

#
# KeepAliveTimeout: Number of seconds to wait for the next request from the
# same client on the same connection.
#
KeepAliveTimeout 15

##
## Server-Pool Size Regulation (MPM specific)
## 

# prefork MPM
# StartServers: number of server processes to start
# MinSpareServers: minimum number of server processes which are kept spare
# MaxSpareServers: maximum number of server processes which are kept spare
# MaxClients: maximum number of server processes allowed to start
# MaxRequestsPerChild: maximum number of requests a server process serves
<IfModule mpm_prefork_module>
    StartServers          5
    MinSpareServers       5
    MaxSpareServers      10
    MaxClients          150
    MaxRequestsPerChild   0
</IfModule>

# worker MPM
# StartServers: initial number of server processes to start
# MaxClients: maximum number of simultaneous client connections
# MinSpareThreads: minimum number of worker threads which are kept spare
# MaxSpareThreads: maximum number of worker threads which are kept spare
# ThreadsPerChild: constant number of worker threads in each server process
# MaxRequestsPerChild: maximum number of requests a server process serves
<IfModule mpm_worker_module>
    StartServers          2
    MaxClients          150
    MinSpareThreads      25
    MaxSpareThreads      75 
    ThreadsPerChild      25
    MaxRequestsPerChild   0
</IfModule>

# These need to be set in /etc/apache2/envvars
User ${APACHE_RUN_USER}
Group ${APACHE_RUN_GROUP}

#
# AccessFileName: The name of the file to look for in each directory
# for additional configuration directives.  See also the AllowOverride
# directive.
#

AccessFileName .htaccess

#
# The following lines prevent .htaccess and .htpasswd files from being 
# viewed by Web clients. 
#
<Files ~ "^\.ht">
    Order allow,deny
    Deny from all
</Files>

#
# DefaultType is the default MIME type the server will use for a document
# if it cannot otherwise determine one, such as from filename extensions.
# If your server contains mostly text or HTML documents, "text/plain" is
# a good value.  If most of your content is binary, such as applications
# or images, you may want to use "application/octet-stream" instead to
# keep browsers from trying to display binary files as though they are
# text.
#
DefaultType text/plain


#
# HostnameLookups: Log the names of clients or just their IP addresses
# e.g., [www.apache.org](www.apache.org) (on) or 204.62.129.132 (off).
# The default is off because it'd be overall better for the net if people
# had to knowingly turn this feature on, since enabling it means that
# each client request will result in AT LEAST one lookup request to the
# nameserver.
#
HostnameLookups Off

# ErrorLog: The location of the error log file.
# If you do not specify an ErrorLog directive within a <VirtualHost>
# container, error messages relating to that virtual host will be
# logged here.  If you *do* define an error logfile for a <VirtualHost>
# container, that host's errors will be logged there and not here.
#
ErrorLog /var/log/apache2/error.log

#
# LogLevel: Control the number of messages logged to the error_log.
# Possible values include: debug, info, notice, warn, error, crit,
# alert, emerg.
#
LogLevel warn

# Include module configuration:
Include /etc/apache2/mods-enabled/*.load
Include /etc/apache2/mods-enabled/*.conf

# Include all the user configurations:
Include /etc/apache2/httpd.conf

# Include ports listing
Include /etc/apache2/ports.conf

#
# The following directives define some format nicknames for use with
# a CustomLog directive (see below).
# If you are behind a reverse proxy, you might want to change %h into %{X-Forwarded-For}i
#
LogFormat "%h %l %u %t \"%r\" %>s %b \"%{Referer}i\" \"%{User-Agent}i\"" combined
LogFormat "%h %l %u %t \"%r\" %>s %b" common
LogFormat "%{Referer}i -> %U" referer
LogFormat "%{User-agent}i" agent

#
# ServerTokens
# This directive configures what you return as the Server HTTP response
# Header. The default is 'Full' which sends information about the OS-Type
# and compiled in modules.
# Set to one of:  Full | OS | Minor | Minimal | Major | Prod
# where Full conveys the most information, and Prod the least.
#
ServerTokens Full

#
# Optionally add a line containing the server version and virtual host
# name to server-generated pages (internal error documents, FTP directory 
# listings, mod_status and mod_info output etc., but not CGI generated 
# documents or custom error documents).
# Set to "EMail" to also include a mailto: link to the ServerAdmin.
# Set to one of:  On | Off | EMail
#
ServerSignature On



#
# Customizable error responses come in three flavors:
# 1) plain text 2) local redirects 3) external redirects
#
# Some examples:
#ErrorDocument 500 "The server made a boo boo."
#ErrorDocument 404 /missing.html
#ErrorDocument 404 "/cgi-bin/missing_handler.pl"
#ErrorDocument 402 [http://www.example.com/subscription_info.html](http://www.example.com/subscription_info.html)
#

#
# Putting this all together, we can internationalize error responses.
#
# We use Alias to redirect any /error/HTTP_<error>.html.var response to
# our collection of by-error message multi-language collections.  We use 
# includes to substitute the appropriate text.
#
# You can modify the messages' appearance without changing any of the
# default HTTP_<error>.html.var files by adding the line:
#
#   Alias /error/include/ "/your/include/path/"
#
# which allows you to create your own set of files by starting with the
# /usr/share/apache2/error/include/ files and copying them to /your/include/path/, 
# even on a per-VirtualHost basis.  The default include files will display
# your Apache version number and your ServerAdmin email address regardless
# of the setting of ServerSignature.
#
# The internationalized error documents require mod_alias, mod_include
# and mod_negotiation.  To activate them, uncomment the following 30 lines.

#    Alias /error/ "/usr/share/apache2/error/"
#
#    <Directory "/usr/share/apache2/error">
#        AllowOverride None
#        Options IncludesNoExec
#        AddOutputFilter Includes html
#        AddHandler type-map var
#        Order allow,deny
#        Allow from all
#        LanguagePriority en cs de es fr it nl sv pt-br ro
#        ForceLanguagePriority Prefer Fallback
#    </Directory>
#
#    ErrorDocument 400 /error/HTTP_BAD_REQUEST.html.var
#    ErrorDocument 401 /error/HTTP_UNAUTHORIZED.html.var
#    ErrorDocument 403 /error/HTTP_FORBIDDEN.html.var
#    ErrorDocument 404 /error/HTTP_NOT_FOUND.html.var
#    ErrorDocument 405 /error/HTTP_METHOD_NOT_ALLOWED.html.var
#    ErrorDocument 408 /error/HTTP_REQUEST_TIME_OUT.html.var
#    ErrorDocument 410 /error/HTTP_GONE.html.var
#    ErrorDocument 411 /error/HTTP_LENGTH_REQUIRED.html.var
#    ErrorDocument 412 /error/HTTP_PRECONDITION_FAILED.html.var
#    ErrorDocument 413 /error/HTTP_REQUEST_ENTITY_TOO_LARGE.html.var
#    ErrorDocument 414 /error/HTTP_REQUEST_URI_TOO_LARGE.html.var
#    ErrorDocument 415 /error/HTTP_UNSUPPORTED_MEDIA_TYPE.html.var
#    ErrorDocument 500 /error/HTTP_INTERNAL_SERVER_ERROR.html.var
#    ErrorDocument 501 /error/HTTP_NOT_IMPLEMENTED.html.var
#    ErrorDocument 502 /error/HTTP_BAD_GATEWAY.html.var
#    ErrorDocument 503 /error/HTTP_SERVICE_UNAVAILABLE.html.var
#    ErrorDocument 506 /error/HTTP_VARIANT_ALSO_VARIES.html.var



# Include of directories ignores editors' and dpkg's backup files,
# see README.Debian for details.

# Include generic snippets of statements
Include /etc/apache2/conf.d/

# Include the virtual host configurations:
Include /etc/apache2/sites-enabled/
# Sample mod_jk configuration
# for Apache 2
#
# for all commands/options available see the manual 
# provided in libapache-mod-jk-doc package. 

# The location where mod_jk will find the workers definitions
[COLOR="Red"]JkWorkersFile	/etc/libapache2-mod-jk/workers.properties[/COLOR]

# The location where mod_jk is going to place its log file
JkLogFile 	/var/log/apache2/mod_jk.log

# The log level:
# - info log will contain standard mod_jk activity (default).
# - warn log will contain non fatal error reports.
# - error log will contain also error reports.
# - debug log will contain all information on mod_jk activity
# - trace log will contain all tracing information on mod_jk activity
JkLogLevel 	info


# Assign specific URLs to Tomcat. In general the structure of a 
# JkMount directive is: JkMount [URL prefix] [Worker name]

# send all requests ending in .jsp to ajp13_worker
JkMount /*.jsp ajp13_worker
# send all requests ending /servlet to ajp13_worker
JkMount /*/servlet/ ajp13_worker

# JkUnmount directive acts as an opposite to JkMount and blocks access 
# to a particular URL. The purpose is to be able to filter out the 
# particular content types from mounted context.

# do not send requests ending with .gif to ajp13_worker
#JkUnMount /servlet/*.gif ajp13_worker


# JkMount / JkUnMount directives can also be used inside <VirtualHost> 
# sections of your httpd.conf file.

---

### Post by AndrewTheArt on 2008-08-01
[COLOR=Black]Syntactically, that looks right - my file is the same. Are you sure you installed libapache2-mod-jk? First let's see if the worker.properties file is even there - 

[/COLOR]**[COLOR=Black]stat [/COLOR][COLOR=Black]/etc/libapache2-mod-jk/workers.properties[/COLOR]**

If that fails, try (re)installing the module - 

**[COLOR=Black]sudo apt-get purge libapache2-mod-jk[/COLOR]**
**[COLOR=Black]sudo apt-get install libapache2-mod-jk[/COLOR]**

---

### Post by daymon1 on 2008-08-01
> **AndrewTheArt said:**
> [COLOR=Black]Syntactically, that looks right - my file is the same. Are you sure you installed libapache2-mod-jk? First let's see if the worker.properties file is even there - 

[/COLOR]**[COLOR=Black]stat [/COLOR][COLOR=Black]/etc/libapache2-mod-jk/workers.properties[/COLOR]**

If that fails, try (re)installing the module - 

**[COLOR=Black]sudo apt-get purge libapache2-mod-jk[/COLOR]**
**[COLOR=Black]sudo apt-get install libapache2-mod-jk[/COLOR]**

It works. Apache started.

Thanks a lot Tim!

-daymon

---

### Post by windependence on 2008-08-01
You need to load the module first as JkWorkersFile is for mod_jk, not mod_jk2 which use jk2.properties
Put this line in right before line 306:


```
LoadModule jk2_module modules/mod_jk2.so
```

Don't forget to restart Apache.

-Tim

---

### Post by windependence on 2008-08-01
Scrap that if it's working, it probably added the laodmodule line when you reinstalled.

-Tim

---

### Post by AndrewTheArt on 2008-08-01
Just so were clear, there was no specific issue with my guide? I'd like to fix it if something needs to be added. I'm fuzzy on the differences between jk and jk2 - which one gets installed from the repositories?

---

### Post by windependence on 2008-08-01
Pretty sure it's jk2.

-Tim

---

### Post by AndrewTheArt on 2008-08-01
So should the JkWorkersFile line be scrapped if it's for the older version, and replaced with something else?

You said

> You need to load the module first as JkWorkersFile is for mod_jk, not mod_jk2 which use jk2.propertiesThen you gave a command to load the jk2 module, which would essentially obsolete the JkWokersFile line and my jk.properties file, no?

---

### Post by windependence on 2008-08-01
No, they are too different animals. 

LoadModule jk2_module modules/mod_jk2.so is a directive to load the module that uses the JkWorkersFile. I am more an Apache 1.3 guy so bear with me but I think those directives are supposed to go in a separate config module in Apache 2. They can be loaded fine from the main config file like I suggested, but that was just to see if it fixed the problem. Apache 2 uses modules and then symlinks them where they need to be. It's more complicated than Apache 1.3, but some say better because everything is in it's own module.

-Tim

---

### Post by AndrewTheArt on 2008-08-01
Makes sense - but I don't seem to have mod_jk2.so in the modules folder in my Apache install (I do, however, have mod_jk.so), so I think the repositories provide jk, not jk2 (unless that's change in the past few months?)

---

### Post by windependence on 2008-08-01
Hmmmm, I haven't messed with Tomcat in quite a while. I'll have to check that out.

-Tim

---

### Post by AndrewTheArt on 2008-08-01
Regardless, I see you were just trying to troubleshoot, so I appreciate your help. If the repositories ever start using jk2 (if they aren't already, and I have good reason to believe that), your command will potentially come in handy. Thanks!

---

### Post by windependence on 2008-08-01
> **AndrewTheArt said:**
> Regardless, I see you were just trying to troubleshoot, so I appreciate your help. If the repositories ever start using jk2 (if they aren't already, and I have good reason to believe that), your command will potentially come in handy. Thanks!

No problem, glad to help. Doing this stuff on the forums keeps my skills up on things like this that I set up and forget about.

-Tim

---

### Post by AndrewTheArt on 2008-08-01
Small update to this guide - (will update actual HTML/PDF later) - you might need to run

```
sudo chmod -R +x /usr/share/tomcat-webapps/ROOT
```to get rid of a permission denied error in your web browser after setting up the server.


[B][U][COLOR=black]Links - Last Updated 8/1/08

PDF[/COLOR][/U][/B]
 
[http://andrewtheart.tripod.com/linux/Ubuntu804Server.pdf](http://andrewtheart.tripod.com/linux/Ubuntu804Server.pdf) 
 
**_HTML_**
 
[http://andrewtheart.tripod.com/linux/Ubuntu804Server.html](http://andrewtheart.tripod.com/linux/Ubuntu804Server.html) [URL="http://compsci.treycarroll.com/ubuntu_guide/Ubuntu804Server.html"]
[/URL]

---

### Post by daymon1 on 2008-08-05
Hi,

I come back with some new beginner questions.

1. What must I see when open localhost? I see a list with some files and directories, but it seem did not recognize the .js and .war files. It's normal?

2. When I put a .war file in /usr/share/tomcat-webapps/ROOT did not unwrap automatically (not even I restart tomcat and apache). But if I put it in /usr/share/tomcat/webapps automatically unwrap the .war files. Again, it's normal?

But if I doubleclick the file index.js directly in /usr/share/tomcat-webapps/ROOT folder it open in browser the Tomcat home page...

sorry for my poor english but I'm working on it...

-Daymon

---

### Post by lextor08 on 2008-09-07
Hi,
I have do the work as it says but i can't see the welcome page of tomcat's page. When i put "localhost:8180" the browser finishes loading a white page. Even if i try to load a "jsp" file that i created the result is the same, a white page.

I will be very grateful if someone can help me and tell me what could be the problems.

Thanks.

---

### Post by k1008536 on 2008-09-12
Hi Andrew, first of I'd like to say that your guide is great, I'm a newbie Linux and LAMP and have followed itwithout too much trouble, everything seems to have worked so far!! 

I stated this install with the goal of serving a trial timesheet package, Actitime [http://www.actitime.com/](http://www.actitime.com/) follow their basic instructions at [http://www.actitime.com/installation_guide_unix.html#u1](http://www.actitime.com/installation_guide_unix.html#u1). I had already started my install before I found you guide, so have completed the install on 8.04 server, I hav also installed java-6-sun. My problem is that I am unable to see the login screen for actitime, at [http://localhost/actitime](http://localhost/actitime) I get 404 not found, at [http://localhost:8080/actitime](http://localhost:8080/actitime) I get Firefox failed to connect. I have tried placing the actitime directory in both usr/share/tomcat-webapps/ROOT (can see in in browser at [http://localhost/index.jsp](http://localhost/index.jsp)) and usr/share/tomcat-webapps/(as suggested in actitime setup) I have not completed any of step 5 of their guide, customising Tomcat. 

If someone has any ideas or would like to take a look at the actitime guide and see if I need to change anything for this particular LAMP/Tomcatinstall it would be much appreciated!

---

### Post by faith_me on 2008-09-12
Hi,
 thanks for your gr8 guide. But i am facing irritating problem on deploying any context. Suppose I am going to deploy 'mycontext' and create war file using existing archive engine and deploy it using tomcat manager. But after deployment it showing ok and run from manager page. I have to type localhost:8180/mycontext/mycontext to get that context. Will you please help my to sort out my problem. I have created war using both archive engine as well as "ar -cvf". I will be obliged for your response.

---

