---
title: "Pwauth and slow directory listing"
date: 2011-09-23
forum: Server Platforms
---

### Post by silexh on 2011-09-23
Hey,

After accessing a password-protected directory in my webserver, I suddenly noticed a very long loading time before I could see the directory listing. Now normally I don't access that directory (it's my home server, so usually I just go to the page I want directly)

Now at first I thought it had to do with 'pwauth', when I access any item that is protected by a password this error shows up in the 'auth.log' file:
```
pwauth: pam_smbpass(pwauth:auth): Cannot access samba password database, not running as root.
```
But there does not seem to be a great delay (there is 155ms between the GET and the HTTP OK package)
If I want to access the directory listing the delay is about 14.8 seconds. I get this as well:
```
pwauth: last message repeated 95 times
```

Because 155ms x 96 ~= 14.8s, I thought this would probably be the cause of the delay.
The error first appeared on the 13th (creepy right?). I've looked through the apt logs for that day and I did do a reinstall of apache2 (first purging it, and then installing it again).

I've tried to Google the error, but I came up empty. Any help would be very much appreciated.




PS:
I'm still running Lucid, because I also use the server as Mediacenter (I had some issued with a blank tv after upgrading).
Here is the appropriate piece of my httpd.conf file:
```
# Authentication with local users
AddExternalAuth pwauth /usr/sbin/pwauth
SetExternalAuthMethod pwauth pipe

# Secure folder
<Directory "/share/web/secure">
AuthType Basic
AuthName "Password-Protected Files"
AuthBasicProvider external
AuthExternal pwauth
AuthzUnixgroup on
Require group webaccess
</Directory>
```

---

### Post by Ryan Dwyer on 2011-09-24
You seem to have some sort of bizarre PAM configuration. I think your PAM is trying to auth using Samba, then if/when it fails it uses another method (probably the passwd file) which passes the auth check. It's probably the case that your Samba auth has never worked from Apache and it has always been falling back to the passwd auth.

The reason it's taking so long might be related to your browser (or antivirus software on your computer, if you're using Windows) prefetching the URLs on that page as it's loading.

I would considering removing the Samba auth method from PAM if you don't use it.

---

### Post by silexh on 2011-09-24
Hey,

I commented the optional pam_smbpass bits in /etc/pam.d/common-auth and /etc/pam.d/common-password
The error has gone away, but the directory still takes about 14s (I checked the packages with Wireshark - so I don't think it's because of my browser).

Any idea where to look for clues?

---

### Post by Ryan Dwyer on 2011-09-24
Is /share/web/secure physically stored on the same computer as the webserver, or is that a mounted network share? If it's a mounted share, I can see it taking ages due to network latency. It might have to make a separate Samba request for each file to get the information it needs in the directory listing (eg. last modified timestamps).

If it's stored on the same computer, then I don't see any reason why it would be slow. Check the output of "top" to see that it has enough RAM and isn't using 100% CPU.

---

### Post by silexh on 2011-09-24
I tested, and I changed it to:
```
<Directory "/share/web/secure">
AuthType Basic
AuthName "Password-Protected Files"
AuthUserFile /share/web/.htpasswd
require valid-user
</Directory>
```
With this the directory listing only takes 100ms.
Which makes me thinking it's still pwauth.

/share/web/secure is stored on the server. But when I looked at the system usage with top (while opening the listing) I noticed pwauth appears and jumps to 4 percent CPU usage for about 14 seconds.
Which would confirm it's pwauth. (other CPU usage and RAM usage is negligible)

When I run:
```
time sudo -u www-data pwauth && echo $?
```
User+Sys ~= 150ms

So apparently apache checks the authentication 96 times, why would it do this while creating the directory listing? (I don't have even close to 96 items in the folder)

---

