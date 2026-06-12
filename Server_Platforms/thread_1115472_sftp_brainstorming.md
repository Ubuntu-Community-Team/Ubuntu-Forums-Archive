---
title: "sftp brainstorming"
date: 2009-04-03
forum: Server Platforms
---

### Post by Mykle87 on 2009-04-03
I will be setting an ubuntu server box soon that will serve several lan (printer, file server, upnp) and internet (sftp, proxy) functions. I have been in several situations where I needed to send large files to friends and family over the internet (over the 300mb [sendspace ]("http://www.sendspace.com")limit). I would like to set up a permanent method to allow several users (one guest account is fine) to send and receive large files. Most recently, I sent a file to a friend over sftp. They were using filezilla windows client. It worked out really well. Basically, my thoughts are should I just simply use ftp or sftp? If sftp, should I set up a RSA key? How would I securely send that key to someone? How can I keep 2 accounts (mine + guest) separate? I essentially want this to be as simple as possible for the end user as well as most secure for my network. Your thoughts are greatly appreciated.

---

### Post by BkkBonanza on 2009-04-03
Depends on the tech competence of your friends. If the level is low and you want ANY of them to be able to use then I'd set up a web server and use http for transfers. They just use their browser same way as always just like if they were downloading from other sites. Use passwords and ssl if you need security.

---

### Post by Mykle87 on 2009-04-05
I have considered this but the last time I played with apache2 I had no idea what I was doing. It may be easier for me to set up an ftp server with ssl and different users to restrict who can access certain files. Since ftp can be accessed using most if not all browsers natively that may work best. A web server is certainly a great alternative though. Just out of curiosity, how would I set up a website to look like [this]("http://cdimage.ubuntu.com/")?

---

### Post by hyper_ch on 2009-04-05
(1) install openssh-server

(2) install mysecureshell

(3) edit your /etc/ssh/sftp_config to something like this:

```

## MySecureShell Configuration File ##
#Default rules for everybody
<Default>
        GlobalDownload          0       #total speed download for all clients
                                        # o -> bytes   k -> kilo bytes   m -> mega bytes
        GlobalUpload            0       #total speed download for all clients (0 for unlimited)
        Download                0       #limit speed download for each connection
        Upload                  0       #unlimit speed upload for each connection
        StayAtHome              true    #limit client to his home
        VirtualChroot           true    #fake a chroot to the home account
        LimitConnection         100     #max connection for the server sftp
        LimitConnectionByUser   10      #max connection for the account
        LimitConnectionByIP     20      #max connection by ip for the account
        Home                    /home/$USER     #overrite home of the user but if you want you can use
                                                #       environment variable (ie: Home /home/$USER)
        IdleTimeOut             300     #(in second) deconnect client is idle too long time
        ResolveIP               true    #resolve ip to dns
#       IgnoreHidden            true    #treat all hidden files as if they don't exist
#       DirFakeUser             true    #Hide real file/directory owner (just change displayed permissions)
#       DirFakeGroup            true    #Hide real file/directory group (just change displayed permissions)
#       DirFakeMode             0400    #Hide real file/directory rights (just change displayed permissions)
                                        #Add execution right for directory if read right is set
#       HideFiles               "^(lost\+found|public_html)$"   #Hide file/directory which match
                                                                #this extented POSIX regex
#       HideNoAccess            true    #Hide file/directory which user has no access
#       MaxOpenFilesForUser     20      #limit user to open x files on same time
#       MaxWriteFilesForUser    10      #limit user to x upload on same time
#       MaxReadFilesForUser     10      #limit user to x download on same time
        DefaultRights           0756 0756       #Set default rights for new file and new directory
        MinimumRights           0700 0700       #Set minimum rights for files and dirs

#       PathDenyFilter          "^\."   #deny upload of directory/file which match this extented POSIX regex

        ShowLinksAsLinks        false   #show links as their destinations
#       ConnectionMaxLife       1d      #limits connection lifetime to 1 day

        Charset                 "ISO-8859-15"   #set charset of computer
#       GMTTime                 +1      #set GMT Time (change if necessary)
</Default>

#Rules only for group ftp
#<Group ftp>
#       Download        25 k/s
#       LogFile         /var/log/sftp-server_ftp.log    #Change logfile
#       ExpireDate      "2007-02-28 18:31:01"
#</Group>

#<Group sftp_administrator>
#       IsAdmin         true            #can admin the server
#       VirtualChroot   false           #you must disable chroot to have a full support of admin
#       StayAtHome      true
#       IdleTimeOut     0
#</Group>

#<Group old_client>
#       SftpProtocol            3       #force protocol SFTP
#       DisableAccount          true    #disable account
#</Group>

#Rules only for group ftpnolimit
#<Group ftpnolimit>
#       Download                0       #0 = unlimited
#       IdleTimeOut             0       #no timeout
#       DirFakeUser             false   #show real user on file/directory
#       DirFakeGroup            false   #show real group on file/directory
#       DirFakeMode             0       #show real rights on file/directory
#       HideFiles               ""      #show all files
#       MaxReadFilesForUser     0       #0 = unlimited but still have the restriction MaxOpenFilesForUser
#</Group>

#<IpRange 192.168.0.1-192.168.0.5>
#       ByPassGlobalDownload    true    #bypass GlobalDownload restriction
#       ByPassGlobalUpload      true    #bypass GlobalUpload restriction
#       Download                0
#       DisableAccount          false   #enable account
#       IdleTimeOut             0       #disable timeout
#       LimitConnectionByIP     0       #no limit
#</IpRange>

#<Group trusted_users>
#       Shell           /bin/tcsh       #give a shell access to TRUSTED clients !!!
#</Group>

<User USERNAME>
        Home    /home/USERNAME
</User>

#<VirtualHost *:22>
#       DirFakeUser     false   #show real user on file/directory
#       DirFakeGroup    false   #show real group on file/directory
#       DirFakeMode     0       #show real rights on file/directory
#       HideNoAccess    false
#       IgnoreHidden    false
#</VirtualHost>

#Include /etc/my_sftp_config_file       #include this valid configuration file

```
alter USERNAME to the real username you want to use.

(4) add that USERNAME to your system and set the shell to be mysecureshell

```

sudo adduser --shell /bin/MySecureShell USERNAME

```

You'll then be asked for a password (and some other info that you can skip)

(5) Chmode that folder so that you can easily put stuff into:

```

sudo chmod 0756 /home/USERNAME

```

(6) Now you can use a sftp tool like filezilla or winscp and login with that username and password and you can simply copy stuff into there.

---

### Post by BkkBonanza on 2009-04-05
That's a plain regular directory index. Most web admins like to turn this off for security but you can control it with the IndexOptions directive. See this page for more,

[http://httpd.apache.org/docs/2.2/mod/mod_autoindex.html#indexoptions](http://httpd.apache.org/docs/2.2/mod/mod_autoindex.html#indexoptions)

If you start with a default apache install I think only 1 or 2 small changes would give you this. Apache has a lot of stuff but generally if you only need a simple config it's easy to alter the default just abit.

Another much more lightweight option is to use nginx. I've been using it for about a year now for several of my sites. It's simpler and easier to configure (in my opinion). I just find the conf file to be easy to read and sensible. And it only uses a small fraction of the resources of apache. Although I actually compiled mine it can be installed through apt-get. It's getting quite popular now - so you may want to check it out at [http://wiki.nginx.org//Main](http://wiki.nginx.org//Main)

Apache is far from the only web server. This could be a quick ftp setup for you.

---

### Post by Mykle87 on 2009-04-05
Interesting ideas. Thanks for the advice. I may go with a combination of options to cater to my end-users.

How do you feel about RSA keys for ssh? Are they necessary or would it just complicate my setup?

---

### Post by Mykle87 on 2009-04-12
I found this [tutorial]("http://www.howtoforge.com/setting-up-proftpd-tls-on-ubuntu-8.10"). This may be a good option. I'm pretty sure that Firefox, IE, and Safari do not support ftps:// sites which certainly isn't the end of the world but it just adds an extra step for my end users. My knowledge of security tells me that regular FTP would not be the best option.

---

### Post by SR_ELPIRATA on 2009-04-29
Excuse my moronity, please, as Im rather new to ubuntu :)

But why would anyone connect to an FTP server using a client rather than the provided "connect to server" option in the Places section (ubuntu desktop)?

ELP

---

### Post by Mykle87 on 2009-04-30
People on other operating systems (Windows and Mac OS X) do not have that luxury.

---

