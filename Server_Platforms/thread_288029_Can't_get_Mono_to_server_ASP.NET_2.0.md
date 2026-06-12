---
title: "Can't get Mono to server ASP.NET 2.0"
date: 2006-10-29
forum: Server Platforms
---

### Post by digeratess on 2006-10-29
I've been trying for days to get Apache serving ASP.NET 2.0 pages, and I'm just out of ideas. ASP.NET 1 pages work great. I followed the instructions at [https://help.ubuntu.com/community/ModMono](https://help.ubuntu.com/community/ModMono) and have been over them again and again. It seems the only requirement to use 2.0 is to have the mono-server2 installed, which I do; and to comment/uncomment the proper lines in /etc/apache2/mods-available/mod_mono.conf, which I have. Of course, I've restarted the server (the machine for that matter) after chaging the config, but it seems like the mono-server2 is just not serving the pages because the simplest, confirmed supported, use of 2-only features like Master Pages, causes errors. This is true both for my own pages and for the samples the come with XSP server.

Can anyone point me in the right direction or give me some ideas? Does anyone have ASP.NET 2.0 working on Dapper with the directions provided in the above referenced how-to?

Thanks.

Dig

---

### Post by Jabran Asghar on 2006-11-08
Hi,

Just wondering if you found any clue, I am having the same issue. It was working fine, before, but on a new server its not!

Thanks for any feedback.

Jabran

---

### Post by digeratess on 2006-11-11
I was able to get ASP.NET 2.0 pages served with Mono after 1) upgrading mono, xsp and mod-mono to 1.1.18, which were until a couple days ago the latest stable sources. (Ubuntu packages contain 1.1.13.) and 2) Downloading the mono-provided SLED VM preconfiged with mono 1.1.17 so I could see how a working .NET 2.0 server is configured, given the lack of good documentation. To install mono from source I followed the instructions in [this thread]("http://www.ubuntuforums.org/showthread.php?t=225454&highlight=mono").

Once I got it working, I tried it again from scratch in a VM and took notes that time, then I blew my whole machine away and did it all again on Edgy. I've done it three times now. Still, I don't consider myself to have a command of the configuration process. I can tell you a few things, and a few things I don't know or don't remember.

1. The process of building per the thread referenced above was the same for both Dapper and Edgy. I have already upgraded from mono 1.1.18 to mono 1.2, and those same instructions worked perfectly yet again.

2. After getting 1.1.18 working on the original machine on which I had first installed the Ubuntu mono packages, I had to go through all the various config files and change lots of paths, etc. I don't remember exactly what all of that was. I don't bother with the Ubuntu mono packages anymore.

3. Mono as installed from source does not set up all the necessary configs for you. I tried to mirror the way the Ubuntu Mono packages set the configs up, since they work well with the Ubuntu Apache package config scheme. Here's what I do after installing Mono from source to work with the Ubuntu Apache package.
[LIST]
[*]Create /etc/apache2/mods-available/mod_mono.load
```
LoadModule mono_module /usr/lib/apache2/modules/mod_mono.so
```
[*]Create /etc/apache2/mods-available/mod_mono.conf
```
AddType application/x-asp-net .aspx .ashx .asmx .ascx .asax .config .ascx
DirectoryIndex index.aspx

#include /usr/lib/mono/1.0/mono-server-hosts.conf
include /usr/lib/mono/2.0/mono-server2-hosts.conf
```
[*]Create /usr/lib/mono/2.0/mono-server2-hosts.conf
```
<IfModule mod_mono.c>
  MonoUnixSocket /tmp/.mod_mono_server2
  MonoServerPath /usr/lib/mono/2.0/mod-mono-server2.exe
  AddType application/x-asp-net .aspx .ashx .asmx .ascx .asax .config .ascx
  MonoApplicationsConfigDir /usr/lib/mono/2.0 
  MonoPath /usr/lib/mono/2.0:/usr/lib
</IfModule>
```
[*]Create a virtual host file for the ASP.NET 2.0 website. Before I upgraded to 1.2, this is what I had for my virtual host:
```
<VirtualHost *>
	ServerName gnuton 
	ServerAdmin webmaster@localhost
	DocumentRoot /var/webapps/gnuton/www
	DirectoryIndex index.html index.aspx
	MonoAutoApplication enabled
	MonoApplications gnuton "/:/var/webapps/gnuton/www"
	MonoServerPath gnuton "/usr/bin/mod-mono-server2"
	MonoDocumentRootDir "/var/webapps/gnuton/www"
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/webapps/gnuton/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
		SetHandler mono
		MonoSetServerAlias gnuton 
	</Directory>
<Location /mono>
  SetHandler mono-ctrl
  Order deny,allow
  Deny from all
  Allow from 127.0.0.1
</Location>
</VirtualHost>
```
I don't believe that configuration is as efficient as it could be, but it worked fine. After upgrading to 1.2, I started tweaking, and below is what I currently have working for the exact same site. It's a little cleaner. I am not at all sure this would work in 1.1.18 because one of the improvements of mod-mono 1.2 is auto-hosting. I don't have time at the moment to set up a VM just to test directive requirement differences between 1.1.18 and 1.2.
```
<VirtualHost *>
	ServerName gnuton 
	ServerAdmin webmaster@localhost
	DocumentRoot /var/webapps/gnuton/www
	DirectoryIndex index.html index.aspx
	MonoApplications "/:/var/webapps/gnuton/www"
	MonoServerPath "/usr/bin/mod-mono-server2"
	MonoDocumentRootDir "/var/webapps/gnuton/www"
	<Directory /var/webapps/gnuton/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
		SetHandler mono
		DirectoryIndex index.aspx 
	</Directory>

	<Location /mono>
		SetHandler mono-ctrl
		Order deny,allow
		Deny from all
		Allow from 127.0.0.1
	</Location>
</VirtualHost>
```
[/LIST]

Finally, I'd like to point out to you that IMO, the Ubuntu Community page on mod-mono is all but useless. Just ignore it. The documentation at [http://mono-project.com/Mod_mono]("http://mono-project.com/Mod_mono") is somewhat more helpful. As far as I can tell, the current "authoritative" documentation on configuring mod_mono is a combination of the mod_mono man page and the xsp man page. However, at least the MonoAutoApplication directive is not documented in the no-doubt old doc. Note that most of the mod_mono directives are passed through as arguments to xsp, so you have to read the xsp doc to understand fully what a directive does.

I hope this is somewhat helpful.

---

### Post by Jabran Asghar on 2006-11-17
Hi,

Sorry for replying late. Thanks a lot for the details. Definitely, these were helpful. I will be trying upgrade to Mono 1.2 a,d hope these will help a lot :-).

Jabran

---

### Post by digeratess on 2006-12-03
Just wanted to post a quick update. I've been building Mono 1.2.1 from source on Dapper Drake today. Configuring mono produced a warning that glib-devel was not available. It took me a little while to find the right package name for Ubuntu, which is zlib1g-dev. Downloading that seemed to do the trick.

---

