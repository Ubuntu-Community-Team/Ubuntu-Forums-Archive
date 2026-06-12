---
title: "Help with proftpd.conf"
date: 2005-11-27
forum: Server Platforms
---

### Post by Centrist on 2005-11-27
I'm setting up an FTP server using ProFTP. I've been to a lot of websites, but I can't figure out to set up FTP access the way I want it. Most setups seem to be focused on downloading/uploading from the ftp user's home directory. I want to use FTP *only* for uploading to my website.

I will have other users with their own subfolders on the site. I don't want anyone to be able to access anything outside of /var/www for reading. Only my account will be able to write to /var/www. Each user will be able to read and write to his /var/www/subdir.

I tried setting this up using something like this for my account:

<Anonymous /var/www>
    User ftpadmin
    Group ftpadmin
    MaxClients 2
    # other stuff
    # no limits
</Anonymous>

As I understand it, this would allow me (ftpadmin) to log in with /var/www being my root directory. I would be able to change anything inside the directory. But when I set this up, I'm in my home directory after I log in. I can even do "cd /".

So what am I doing wrong here? Is there a better way to do this?

---

### Post by nagilum on 2005-11-27
I'm not familiar with ProFTPd but the DefaultRoot option seems to be what you are looking for: [http://www.proftpd.org/docs/directives/linked/config_ref_DefaultRoot.html](http://www.proftpd.org/docs/directives/linked/config_ref_DefaultRoot.html)

---

### Post by Centrist on 2005-11-27
I've tried using that, but it doesn't do anything. In my config I had *DefaultRoot /var/www* OR *DefaultRoot /var/www ftpadmin* placed just above the Anonymous tag.

But I shouldn't have to use DefaultRoot, right? Because I already have the root folder specified in the Anonymous tag.

---

### Post by hostile on 2005-11-27
[QUOTE=Centrist]I've tried using that, but it doesn't do anything. In my config I had *DefaultRoot /var/www* OR *DefaultRoot /var/www ftpadmin* placed just above the Anonymous tag.

But I shouldn't have to use DefaultRoot, right? Because I already have the root folder specified in the Anonymous tag.[/QUOTE]


Nagilum is right, the "DefaultRoot" directive is what you are looking for, and it is a Global directive.

Perhaps you could post your proftpd.conf file, and maybe we could see where you're going wrong...

---

### Post by em3rald on 2005-11-28
I only want to add that I am also interested in setting up a proftpd server with precisely the same settings as Centrist.  All of the how-tos out there seem to overlook the use of proftpd as a webserver administration server.  My setup would be slightly different:

ftpadmin = access to everything in the /var/www/ directory.
User1 = access to everything in /var/www/ but a distinctly different user.
User2+ = access to a collective folder as well as a private folder.

This server will be to administer a Rock band's website, where one of their members will occasionally act as ftp and web admin, but not as system admin; only *I* will have system administration access.  The rest will have access to a collective directory, and a directory for their own personal use.

I have read helpfile after helpfile, but I guess I am not a linux/proftpd pro yet because I cannot figure this out for the life of me!  I have my Apache server running smooth, so you'd think I could figure out Proftpd!

Anyhoo ... I type too much.  Sorry folks.  Thanks in advance for the help ... 

The only thing I can offer as thanks is to tell you to check out the band I server-administrate: ** [www.anxietyofinfluence.ca](www.anxietyofinfluence.ca)** ... there are 4 songs you can listen to and download.  They sound similar to bands like Evanescence and FingerEleven, and they are as-yet unsigned (though they are getting plenty of sniffs from a few labels).  That's all I can offer :( ... but hey, maybe they'll be huge rockers one day and you can say you heard it before they were big! :D  Oh ... and the singer is a very hot red-head ... she's very pleasant on the eyes ;) :cool:

---

### Post by Centrist on 2005-11-28
I've been trying out different accounts, and I can only log on with my user account. I'm using the ftp account now, and I can't log on at all. I reset the password, and tried using UserPassword, but I still couldn't log on.

Here's my proftpd.conf:

```
ServerName			"FTP Server"
ServerType			standalone
DeferWelcome			off
MultilineRFC2228		on
DefaultServer			on
ShowSymlinks			on
TimeoutNoTransfer		600
TimeoutStalled			600
TimeoutIdle			1200
DisplayLogin                    welcome.msg
DisplayFirstChdir               .message
ListOptions                	"-l"
DenyFilter			\*.*/
#PersistentPasswd		off
#TLSEngine 			on
#Quotas				on
#Ratios				on
Port				21
MaxInstances			30
User				nobody
Group				nogroup
Umask				022  022
AllowOverwrite			on
#DelayEngine 			off

DefaultRoot /var/www

<Anonymous /var/www>
User ftp
Group ftp
MaxClients 2
</Anonymous>
```

Just realized that when I connect to my FTP server, it doesn't say "FTP Server." Instead it says "ProFTPD 1.2.10 Server (Debian) [127.0.0.1]." I don't think it's ignoring my config file because *sudo proftpd -td5* does check my config.

---

### Post by hostile on 2005-11-28
How many users do you plan on having write access for?

Have you entered those users into your ftpusers file?

I think I understand what you're trying to accomplish, but I'm not sure you're going about it in the most secure manner... perhaps with more info, we can come up with a much better set up for you.

---

### Post by Centrist on 2005-11-29
Well right now, I'm only planning on having two users. One user with write access for /var/www/ and another with access to /var/www/subdirx. Neither of these users is in /etc/ftpusers.

Should my configuration work? Is there anything else I need to configure to make proftpd use it?

---

### Post by jg123 on 2005-11-29
[QUOTE=em3rald]...
The only thing I can offer as thanks is to tell you to check out the band I server-administrate: ** [www.anxietyofinfluence.ca](www.anxietyofinfluence.ca)** ...[/QUOTE]
The image links are all broken.

---

### Post by Centrist on 2005-12-03
I am leaving in two days for a one-week business trip, and I'd like to have this fixed before then.

---

### Post by Centrist on 2005-12-04
Anybody?:(

---

