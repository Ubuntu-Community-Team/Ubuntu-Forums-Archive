---
title: "proftpd config - virtual directory's.."
date: 2007-04-22
forum: Server Platforms
---

### Post by tiger.woods on 2007-04-22
I'm trying to set up my server to allow multiple users to ftp into only thier respective directory's and I'm a bit confused on how to setup proftpd for that.

From what I'm reading if I set the directive " DefaultRoot ~" this will jail the users into their directory's, exactly what I want. 

For instance if I have 3 virtual web hosting sites ([www.site1.com](www.site1.com) - user: TW1, [www.site2.com](www.site2.com) user: TW2, [www.site3.com](www.site3.com) user:TW3) each with their web directory's in /var/www/site1,  /var/www/site2,  /var/www/site3. 

Do I just need to create the users TW1, TW2 and TW3 and add them to an FTPGroup for permissions then link their respective /home directory's to their individual sites [www.site1.com1](www.site1.com1), [www.site2.com](www.site2.com), [www.site3.com](www.site3.com) and away we go?

Could someone explain the process a little bettor for me... I've been searching and really haven't found a good "How to" that explains all the pieces.

TW,

---

### Post by strixy on 2007-04-22
You can manually configure the users home directory (and therefore set it to wherever you like) when you create/modify their accounts. I wouldn't want to do that for more than about 20 users though.

---

### Post by tiger.woods on 2007-04-23
So, how do most people handle it?

I mean if Linux is the prefered choice foe webhosting I don't see a lot of intuitiveness here for adding a bunch of users and domains, etc.

I'm still prety much in the dark as far as setting this up. Any advice on exactly how to pull this off?

TW,

---

### Post by tiger.woods on 2007-04-24
Is this really this obscure of a request? Did I ask the question incorrectly? I mean it's FTP, a common protocol for transferring files, how do you set it up?

Does anyone on the forum use proftpd with virtual hosts that can shed some light on how to actually set this up  for multiple users, jailing them in their own directory's.

I've been googling and questioning but it seems there aren't any real answers or guides to help with this. How is everyone doing this?

---

### Post by strixy on 2007-04-24
I think it's that you're asking about a specific piece of software. Never having used proftp (I used vsftp) I can assure you that if there is a user forum for proftp specifically, you would have better luck.

Have you read through this page yet?

[http://proftpd.org/localsite/Userguide/linked/c503.html](http://proftpd.org/localsite/Userguide/linked/c503.html)

Or visited

[http://justlinux.com/forum/archive/index.php/t-40916.html](http://justlinux.com/forum/archive/index.php/t-40916.html)

How about this virtual host example.

[http://www.proftpd.org/docs/configs/virtual.conf](http://www.proftpd.org/docs/configs/virtual.conf)

Failing those sources above, you may want to post your question in the proftp mailing list.

[http://www.proftpd.org/lists.html](http://www.proftpd.org/lists.html)

---

### Post by tiger.woods on 2007-04-24
So, is proftpd not the "standard" ftp application being used by most? I've seen vsftp come up a bit in my searches so I'm not opposed to switching since the forums are a great source of information and examples.

I'm green enough to need to some hand holding but willing to walk by myself if I can gather enough information to get going.

I've seen the majority of your links thanks for that. 

I think my biggest stumbling blocks are related not to the specific installation of proftpd but in how to establish users and set up their particular directories to "jail" them. 

For instance, I've seen suggestions on jailing users using 2 different processes:
1) DocumentRoot ~
2) DocumentRoot /var/www/defaultFTPsite

So my problem is what's the correct way to do it? There is a lot of information out there and really no definite=ives that I've seen.

Since most of the ftp programs I would assume are similar in nature is there a standard process for creating virtual (maybe not the correct terminology) users for access to ftp to their own websites?

Do you have some specific information on how to set up vsftp that might help a greenhorn such as myself?

Thanks,

---

### Post by strixy on 2007-04-24
1. Enable user web directories via apache phblic_html. This turns on public html directories for each user. The absolute path for those will be /home/username/public_html. You access them from [http://yourmaindomain.com/~username](http://yourmaindomain.com/~username)

Not really a nice way to display the URL, but if you're already using domain forwarding, it works like a charm.

This way, your users can register their own domain names (with whomever they like) and use the registers domain forwarding feature to forward to the accounts they created on your machine. You can often setup a domain resellers account with a register site and they will pay out a commission on your users registering with them.

More info on public_html options:
[http://httpd.apache.org/docs/2.0/howto/public_html.html](http://httpd.apache.org/docs/2.0/howto/public_html.html)


2. If you don't use domain forwarding, I would encourage you to look into it. If not, (ie. if you need subdomains) use Apache's mod_vhost_alias to dynamically redirect domains to users their public_html dir.

[http://httpd.apache.org/docs/2.0/mod/mod_vhost_alias.html](http://httpd.apache.org/docs/2.0/mod/mod_vhost_alias.html)

That is a lot harder than using your domain registers domain forwarding feature, but it does work once you get the hang of it. (I use it a lot). If you want to do a number of sites, look into Apache's mass dynamic virtual hosting - I love that stuff. 

3. use whatever ftp prog you like, but look for a way to "lock users to home directory" and use "authenticated mode". That home directory was setup when you created the user account on your system. Add the user to the FTP group.

4. create users however you like. Use the GUI in Gnome/KDE or check out the command "adduser" - #man adduser

That should give you an idea of what direction you need to go in.

5. Maybe look into installing SSH ... it's helpful, works like FTP, only it's easier to configure for your needs and more secure ... sort of.

---

### Post by nix4me on 2007-04-24
You can do it many ways.  It depends how you want your users to connect.  If you want them to connect to the same ip address, then just setup a default proftpd and use Defaultroot ~.  That will dump them into whatever you want their home dir to be.  If you want to setup virtual servers, and have them connect via their domain name, then setup proftpd using the virtual host instructions found here:

[http://www.proftpd.org/docs/configs/virtual.conf](http://www.proftpd.org/docs/configs/virtual.conf)
and
[http://www.proftpd.org/docs/configs/virtual_authuserfile.conf](http://www.proftpd.org/docs/configs/virtual_authuserfile.conf)

The proftpd documentation is excellent, check it out.  Also, the proftpd mailing list is excellent...the main developer usually answers questions personally within 12 hours.

nix4me

---

### Post by tiger.woods on 2007-04-24
Thanks for the posts guy's.

> 1. Enable user web directories via apache phblic_html. This turns on public html directories for each user. The absolute path for those will be /home/username/public_html. You access them from [http://yourmaindomain.com/~username](http://yourmaindomain.com/~username)

Interesting, I'll look into it.

> If you want them to connect to the same ip address, then just setup a default proftpd and use Defaultroot ~. That will dump them into whatever you want their home dir to be. If you want to setup virtual servers, and have them connect via their domain name

Some follow ups if you don't mind. I read in your comment that there are 2 options maybe more but the 2 I care about are DefaultRoot~ and Virtual Servers. Are they not used in conjunction with one another? or is it one or the other? If I'm doing virtual then I don't need the DefaultRoot~?

1) After creating the User do I then need to create the virtual server in proftpd.conf for them to login via ftp.theirdomain.com?

# First virtual server
<VirtualHost ftp.virtual.com>
  ServerName			"Virtual.com's FTP Server"

  MaxClients			10
  MaxLoginAttempts		1

  # DeferWelcome prevents proftpd from displaying the servername
  # until a client has authenticated.
  DeferWelcome			on

  # Limit normal user logins, because we only want to allow
  # guest logins.
  <Limit LOGIN>
    DenyAll
  </Limit>

  # Next, create a "guest" account (which could be used
  # by a customer to allow private access to their web site, etc)
  <Anonymous ~cust1>
    User			cust1
    Group			cust1
    AnonRequirePassword		on

    <Limit LOGIN>
      AllowAll
    </Limit>

    HideUser			root
    HideGroup			root

    # A private directory that we don't want the user getting in to.
    <Directory logs>
      <Limit READ WRITE DIRS>
        DenyAll
      </Limit>
    </Directory>
  </Anonymous>
</VirtualHost>

2) Since the user has been created I assume all theweb files are in their directory's do you simply create links to /var/www and the like?

Sorry for the green questions but their assumptions I guess that are left out in most of the readings I've found googling.

TW,

---

### Post by tiger.woods on 2007-04-25
Well I'm trying to take your advice and use the proftpd .conf supplied on the proftpd site. 

A couple of questions, my proftpd.conf file has a lot more options and information than is included in that file, how old is that setup?

Since I'm hosting virtually and my domain names are registered elsewhere as well as the DNS records are hosted how do I deal with the following in the setup? 

# First virtual server
<VirtualHost ftp.virtual.com>
  ServerName			"Virtual.com's FTP Server"

When I replace virtualdoamin.com with my domain name I get the error "No address associated with the hostname" when trying to start proftpd I'm assuming this is DNS related? Any thoughts...?

---

### Post by strixy on 2007-04-26
Sounds like you're using domain forwarding?

---

### Post by tiger.woods on 2007-04-26
I fixed the "No address associated with the hostname" error by changing the  ServerType from 'standalone' to 'inetd',  proftpd then restarted successfully without error.

Here is my conf, I don't know that it all makes sense to me, hopefully you guy's can tell me if I'm way off base or what.


#
# /etc/proftpd/proftpd.conf -- This is a basic ProFTPD configuration file.
# To really apply changes reload proftpd after modifications.
# 

# Includes DSO modules
Include /etc/proftpd/modules.conf

ServerName			"MyDomain"
ServerType			inetd
DeferWelcome			on

MultilineRFC2228		on
DefaultServer			on
ShowSymlinks			on

TimeoutNoTransfer		600
TimeoutStalled			300
TimeoutIdle			1200

DisplayLogin                    welcome.msg
DisplayFirstChdir               .message
ListOptions                	"-l"

DenyFilter			\*.*/
DefaultRoot			~
#IndentLookups			off
#ServerIndent			on	"FTP server Ready"

# Port 21 is the standard FTP port.
Port				21

# In some cases you have to specify passive ports range to by-pass
# firewall limitations. Ephemeral ports can be used for that, but
# feel free to use a more narrow range.
# PassivePorts                    49152 65534

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances			5

# Set the user and group that the server normally runs at.
User				nobody
Group				nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask				022  022
# Normally, we want files to be overwriteable.
AllowOverwrite			on

# Uncomment this if you are using NIS or LDAP to retrieve passwords:
# PersistentPasswd		off

# Be warned: use of this directive impacts CPU average load!
#
# Uncomment this if you like to see progress and transfer rate with ftpwho
# in downloads. That is not needed for uploads rates.
# UseSendFile			off

TransferLog /var/log/proftpd/xferlog
SystemLog   /var/log/proftpd/proftpd.log

<IfModule mod_tls.c>
TLSEngine off
</IfModule>

<IfModule mod_quota.c>
QuotaEngine on
</IfModule>

<IfModule mod_ratio.c>
Ratios on
</IfModule>


# Delay engine reduces impact of the so-called Timing Attack described in
# [http://security.lss.hr/index.php?page=details&ID=LSS-2004-10-02](http://security.lss.hr/index.php?page=details&ID=LSS-2004-10-02)
# It is on by default. 
<IfModule mod_delay.c>
DelayEngine on
</IfModule>

<IfModule mod_ctrls.c>
ControlsEngine        on
ControlsMaxClients    2
ControlsLog           /var/log/proftpd/controls.log
ControlsInterval      5
ControlsSocket        /var/run/proftpd/proftpd.sock
</IfModule>

<IfModule mod_ctrls_admin.c>
AdminControlsEngine on
</IfModule>

# First virtual server
<VirtualHost ftp.MyDomain.com>
  ServerName			"FTP Server"

  MaxClients			1
MaxLoginAttempts 3

  # DeferWelcome prevents proftpd from displaying the servername
  # until a client has authenticated.
  DeferWelcome			on

  # Limit normal user logins, because we only want to allow
  # guest logins.
  <Limit LOGIN>
    DenyAll
  </Limit>

  # Next, create a "guest" account (which could be used
  # by a customer to allow private access to their web site, etc)
  <Anonymous ~MyDomain.com>
    User			MyDomain.com
    Group			MyDomain.com
    AnonRequirePassword		on

    <Limit LOGIN>
      AllowAll
    </Limit>

    HideUser			root
    HideGroup			root

    # A private directory that we don't want the user getting in to.
    <Directory logs>
      <Limit READ WRITE DIRS>
        DenyAll
      </Limit>
    </Directory>
  </Anonymous>
RootLogin off
</VirtualHost>

---

### Post by tiger.woods on 2007-04-26
Well I think I've determined that virtual hosts won't work with proFTPd as the protocol doesn't support virtual hosts on a single IP address which is where the confusion comes in. I would need a separate IP for each user and that just doesn't make sense with apache and virtual hosting.

So, I think I have to go back to simply jailing the users using 'DocumentRoot ~'. Anyone have some simple directions for setting that up or a proftp.conf file that I can start with? Specifically ([http://www.castaglia.org/proftpd/doc/contrib/ProFTPD-mini-HOWTO-Chroot.html](http://www.castaglia.org/proftpd/doc/contrib/ProFTPD-mini-HOWTO-Chroot.html))



TW,

---

### Post by nix4me on 2007-04-26
post your question on the proftpd mailing list.

nix4me

---

### Post by tiger.woods on 2007-04-28
Well I finally got proftpd going loosley following this guide ([http://www.howtoforge.com/proftpd_mysql_virtual_hosting](http://www.howtoforge.com/proftpd_mysql_virtual_hosting)) but I have 3 final questions.

1) When logging in locally I see the following in a session:

[I][B]rocket02@dns1:~$ ftp mydomain.com
Connected to mydomain.com.
220 ProFTPD 1.3.0 Server ready.
Name (mydomain.com:rocket02): frank
331 Password required for frank.
Password:
230 User frank logged in.
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> ls
200 PORT command successful
150 Opening ASCII mode data connection for file list
-rw-r--r--   1 (?)      (?)           274 Apr 28 19:10 mydomain_access.log
-rw-r--r--   1 (?)      (?)            42 Apr 28 19:10 index.html
-rw-r--r--   1 (?)      (?)            43 Apr 28 19:09 index.html~
226 Transfer complete.
ftp> exit
221 Goodbye.
rocket02@dns1:~$[/B][/I]

2) I'm unable to login from the internet, slight problem. I think it might be a permissions problem but am unsure since I'm able to log in locally?


3) How can I test this for security? I just want to make sure it's safe to put out on the web.

Thanks.

TW,

---

### Post by tiger.woods on 2007-05-01
Nobody's got any suggestions... ????

---

