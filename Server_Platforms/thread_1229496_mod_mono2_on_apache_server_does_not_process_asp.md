---
title: "mod_mono2 on apache server does not process asp"
date: 2009-08-02
forum: Server Platforms
---

### Post by silentIm on 2009-08-02
Hi all,

i installed both mod_mono and mod_mono2 for apache from a tutorial. I only modified etc/apache2/site_enabled/mod_mono.conf as suggested by the included comment to enable .net 2.0

AddType application/x-asp-net .aspx .ashx .asmx .ascx .asax .config .ascx
DirectoryIndex index.aspx

Include /etc/mono-server2/mono-server2-hosts.conf

and commented out the 1.0 .net module.  I don't edit the default /etc/mono-server2/mono-server2-hosts.conf

<IfModule mod_mono.c>
  MonoUnixSocket default /tmp/.mod_mono_server2
  MonoServerPath default /usr/bin/mod-mono-server2
  AddType application/x-asp-net .aspx .ashx .asmx .ascx .asax .config .ascx
  MonoApplicationsConfigDir default /etc/mono-server2
  MonoPath default /usr/lib/mono/2.0:/usr/lib
</IfModule>

Apparently, when I try to access the index.aspx, the module does not parse the document. My firefox just download it, not displaying it. The apache knows that it is a default page of the directory. And if I use phpinfo(), the loaded module is mod_mono.

Apache version: Apache/2.2.11 (Ubuntu) mod_mono/2.0 PHP/5.2.6-3ubuntu4.1 with Suhosin-Patch

 Do I need to compile it first before deploy it? How to fix this?

P.S : I am sorry for the title. I mean asp.net (.aspx) not the old asp(.asp).

---

### Post by directhex on 2009-08-02
Check your apache error log

---

### Post by slakkie on 2009-08-02
Asking the obvious, you did restart apache after you've made the change?

---

### Post by silentIm on 2009-08-02
error log, sorry, for long reply. it is midnight here.

[Sun Aug 02 20:16:15 2009] [warn] (2)No such file or directory: Failed to destroy the '/tmp/mod_mono_dashboard_XXGLOBAL_1' shared memory dashboard
[Sun Aug 02 20:16:15 2009] [warn] (2)No such file or directory: Failed to destroy the '/tmp/mod_mono_dashboard_default_2' shared memory dashboard
[Sun Aug 02 20:16:15 2009] [warn] (2)No such file or directory: Failed to destroy the '/tmp/mod_mono_dashboard_XXGLOBAL_1' shared memory dashboard
[Sun Aug 02 20:16:15 2009] [warn] (2)No such file or directory: Failed to destroy the '/tmp/mod_mono_dashboard_default_2' shared memory dashboard
[Sun Aug 02 20:16:16 2009] [warn] module mono_module is already loaded, skipping

and yeah, I know I already restart it.

---

### Post by directhex on 2009-08-02
Okay then.

As standard, the document root will not be processed by mod-mono. Webapps must be defined, and the easiest way to do that is to create a folder in /etc/mono-server2/conf.d/ and put a file inside like the following:
```
path = /some/place/containing/webapp
alias = /subfolderofyourwebservertobeinchargeof
```

With this file in place, run mono-server2-update

e.g. this works:

```
$ cat /etc/mono-server2/conf.d/panda/panda 
path = /tmp/foo
alias = /foo
```

---

### Post by silentIm on 2009-08-03
are there any mistake in this config?

/etc/apache2/mods_enabled/mod_mono.load
```

LoadModule mono_module /usr/lib/apache2/modules/mod_mono.so

```/etc/apache2/mods_enabled/mod_mono.conf
```

AddType application/x-asp-net .aspx .ashx .asmx .ascx .asax .config .ascx
DirectoryIndex index.aspx

Include /etc/mono-server2/mono-server2-hosts.conf

#Include /etc/mono-server/mono-server-hosts.conf

```

my localhost site for mono is mono.localhost

/etc/apache2/sites-enabled/003-mono (create by myself)
```

    <VirtualHost *:80>
        DocumentRoot /var/www/mono
        ServerName mono.localhost
        ServerAlias mono.localhost
        Alias /mono /var/www/mono
        AddMonoApplications default "/mono:/var/www/mono"

        <Directory /var/www/mono/>
            Options all
            AllowOverride all
            Order allow,deny
            allow from all
        </Directory>
        <Location /mono>
            SetHandler mono
        </location>
    </VirtualHost>

```

---

### Post by directhex on 2009-08-03
> **silentIm said:**
> are there any mistake in this config?

No idea. Using apache's sites-enabled stuff for mod-mono on Ubuntu isn't "supported" because, well, I don't know how to make it behave properly (and hence can't offer support), and anything requiring a config file more than 2 lines long makes my head spin.

---

