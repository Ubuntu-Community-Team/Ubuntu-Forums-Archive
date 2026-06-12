---
title: "Mod_mono issues"
date: 2009-01-06
forum: Server Platforms
---

### Post by brianhenson on 2009-01-06
I installed mod_mono and the mono-apache-server2 along with the required packages for mono and such and I cannot get mono to work.  when running a simple hello world in vb.net I get this error in the apache error.log

```
[Tue Jan 06 18:39:01 2009] [error] Failed running '/usr/bin/mod-mono-server --filename /tmp/mod_mono_server_global --nonstop --master (null) (null) (null) (null) (null) (null) (null) (null)'. Reason: No such file or directory

```

I have it set to use the mod-mono-server2 in the mono.conf file but it is still trying to use the version 1 witch is not installed.  Anyone have a solution or can point me in the right direction?

edit:  forgot to say I am running intrepid on x86

---

### Post by directhex on 2009-01-07
Sorry, which file exactly are you editing?

---

### Post by brianhenson on 2009-01-08
I followed the guide located here [http://frugalcoder.us/post/2008/02/Setting-up-mod_mono-(ASPNet-20)-on-Ubuntu-710-(Gutsy-Gibbon).aspx](http://frugalcoder.us/post/2008/02/Setting-up-mod_mono-(ASPNet-20)-on-Ubuntu-710-(Gutsy-Gibbon).aspx) and made a auto_mono_hosting.conf

---

### Post by directhex on 2009-01-08
> **brianhenson said:**
> I followed the guide located here [http://frugalcoder.us/post/2008/02/Setting-up-mod_mono-(ASPNet-20)-on-Ubuntu-710-(Gutsy-Gibbon).aspx](http://frugalcoder.us/post/2008/02/Setting-up-mod_mono-(ASPNet-20)-on-Ubuntu-710-(Gutsy-Gibbon).aspx) and made a auto_mono_hosting.conf

The guide is wrong.

Unfortunately, MonoAutoApplication does not permit you to override MonoServerPath - it is hard-coded to use /usr/bin/mod-mono-server

I filed a bug on this here: [https://bugzilla.novell.com/show_bug.cgi?id=440415](https://bugzilla.novell.com/show_bug.cgi?id=440415)

Oh, and the guide is wrong for another reason - use "a2dismod" and "a2enmod", don't symlink things in /etc/apache2 manually

---

### Post by brianhenson on 2009-01-11
Do you have any sujections on how to get this up and running? I am up for anything and not afraid of the command line :lolflag:

---

### Post by directhex on 2009-01-12
I HATE to suggest it, but ln -s /usr/bin/mod-mono-server2 /usr/bin/mod-mono-server

---

### Post by brianhenson on 2009-01-12
ok now I have done that it is asking me to download the file.  at least we are getting somewhere now.

---

### Post by directhex on 2009-01-12
> **brianhenson said:**
> ok now I have done that it is asking me to download the file.  at least we are getting somewhere now.

Restart apache

---

### Post by brianhenson on 2009-01-12
I did that with the same results and just to make sure I wasn't to tired to work on it I did it again just now with the same result, it asking me to download the file

---

### Post by directhex on 2009-01-14
Check your apache log then, mod_mono isn't being used properly

---

### Post by brianhenson on 2009-01-15
ok i checked the error.log and here is what i am getting

> [Wed Jan 14 23:06:43 2009] [error] [client 192.168.1.20] Invalid method in request \x16\x03\x01

---

### Post by directhex on 2009-01-15
Paste your config file

---

### Post by directhex on 2009-01-15
Oh, and make sure you have libmono-i18n{1,2}.0-cil installed

---

### Post by brianhenson on 2009-01-15
Ok i had those installed and here is my mod_mono_auto.conf file
> MonoServerPath "/usr/bin/mod-mono-server2"
MonoAutoApplication enabled
AddType application/x-asp-net .aspx
AddType application/x-asp-net .asmx
AddType application/x-asp-net .ashx
AddType application/x-asp-net .asax
AddType application/x-asp-net .ascx
AddType application/x-asp-net .soap
AddType application/x-asp-net .rem
AddType application/x-asp-net .axd
AddType application/x-asp-net .cs
AddType application/x-asp-net .config
AddType application/x-asp-net .dll
DirectoryIndex index.aspx
DirectoryIndex Default.aspx
DirectoryIndex default.aspx

and the directory that hosts the files
> </Directory>
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
SetHandler mono
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>


---

### Post by directhex on 2009-01-16
> **brianhenson said:**
> Ok i had those installed and here is my mod_mono_auto.conf file

> **directhex said:**
> Unfortunately, MonoAutoApplication does not permit you to override MonoServerPath - it is hard-coded to use /usr/bin/mod-mono-server

One day people might listen to me. One day...

---

### Post by brianhenson on 2009-01-16
Yes I remember and I asked how to fix it.  Those are the files i have configured the rest is stock from the package.  I don't know anything about mono so I am just relying on help. once i screwed up with it once i didnt want to do anything else that would hinder the troubleshooting process

---

### Post by directhex on 2009-01-17
> **brianhenson said:**
> Yes I remember and I asked how to fix it.  Those are the files i have configured the rest is stock from the package.  I don't know anything about mono so I am just relying on help. once i screwed up with it once i didnt want to do anything else that would hinder the troubleshooting process

You cannot combine ANY settings starting with "Mono" with "MonoAutoApplication" - you need to remove your MonoServerPath setting.

---

### Post by brianhenson on 2009-01-17
Ok I removed that line and i get this from the error.log and it askes me to download the file.  > [Sat Jan 17 15:22:23 2009] [warn] long lost child came home! (pid 14689)
[Sat Jan 17 15:22:23 2009] [warn] long lost child came home! (pid 14691) if I have to we can work from scratch and purge and reinstall mono and start over if you feel that is needed.

---

### Post by directhex on 2009-01-17
> **brianhenson said:**
> Ok I removed that line and i get this from the error.log and it askes me to download the file.   if I have to we can work from scratch and purge and reinstall mono and start over if you feel that is needed.

Purging libapache2-mod-mono2 and installing it again might help, as long as you're certain that all the config files are gone. Then use "a2dismod mod_mono" and "a2enmod mod_mono_auto"

---

### Post by brianhenson on 2009-01-17
Ok i purged it.  i removed the autohosting file i created using the howto.  I now have a clean mono and mod-mono install.  I did not enable the auto hosting so I can use the mod_mono.conf file.  If i am wrong please let me know.  I want to set it up the right way not the fast way.

---

### Post by MaedMaex on 2010-10-01
Hi. I'm stuck on the same Problem. Did you solve it?

---

### Post by brianhenson on 2010-10-01
nope never did had to switch to suse :(

---

