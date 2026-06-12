---
title: "server newb needs help"
date: 2009-09-11
forum: Server Platforms
---

### Post by woodsonoversoul on 2009-09-11
Hello, I'm trying to set up my first server and these are the components I have set up so far: XAMPP, under System>Administration>Network Tools when I preform a port scan port 80 comes back open to www, a domain name hosted with dyndns.com, and my wireless router connecting to dyndns.com. When I try to connect to the domain they gave me the browser times out before anything loads. What am I missing?/What can I double check? Thanks to all in advance. Dan

---

### Post by talsemgeest on 2009-09-12
> **woodsonoversoul said:**
> Hello, I'm trying to set up my first server and these are the components I have set up so far: XAMPP, under System>Administration>Network Tools when I preform a port scan port 80 comes back open to www, a domain name hosted with dyndns.com, and my wireless router connecting to dyndns.com. When I try to connect to the domain they gave me the browser times out before anything loads. What am I missing?/What can I double check? Thanks to all in advance. Dan
Go into the router settings, and set up port forwarding for port 80 to your server. If your router allows for a DMZ host, all the better, as that will automatically forward all ports to your server. Take a look [here.](http://www.portforward.com/english/routers/port_forwarding/routerindex.htm)

---

### Post by TuckLive on 2009-09-12
> **talsemgeest said:**
> Go into the router settings, and set up port forwarding for port 80 to your server. If your router allows for a DMZ host, all the better, as that will automatically forward all ports to your server. Take a look [here.](http://www.portforward.com/english/routers/port_forwarding/routerindex.htm)

From my router:
> The Port Forwarding feature is more secure because it only opens the ports you want to have opened, while DMZ hosting opens all the ports of one computer, exposing the computer so the Internet can see it.

So while DMZ has it's advantages, forwarding all of your ports is not always the best idea.

---

### Post by talsemgeest on 2009-09-12
> **TuckLive said:**
> From my router:


So while DMZ has it's advantages, forwarding all of your ports is not always the best idea.
It is brilliant if all you are doing is hosting a web site, but if you want ssh, web administration, https, ftp, vmware server... you would have to set up a port forwarding rule for each. And, as long as you keep your computer up to date there is nothing to worry about.

---

### Post by woodsonoversoul on 2009-09-12
I am trying to set up a server for a single website. I believe I already have the port forwarded. When I go to my router's admin page and it's port forwarding options I see this set as the only port forwarded...
 # 	Service Name 	Start Port 	End Port 	Server IP Address
 1	HTTP	        80	        80	        192.168.*.*

---

### Post by woodsonoversoul on 2009-09-12
So my router says it is forwarded. Is there a way to check?

---

### Post by volkswagner on 2009-09-12
A few simple steps can help troubleshoot:
[LIST]
[*]From a second local machine on the network enter the local ip address of the server in the web browser to see if apache is working locally?
[*]Is dynDns forwarding to your ISP (external) ip address?  You should be able to compare it with your external ip from your router page or canyouseeme.org
[*]Try accessing your web address from a machine outside your LAN to see if it is an issue with NAT redirection.
[*]Enter your external ip address directly in the browser window locallay and outside the LAN to see if it is a DNS issue.
[/LIST]

---

### Post by woodsonoversoul on 2009-09-12
Thanks volkswagner. In response to your first point, which ip address do I use, My Internet Port IP Address, My Internet Port Domain Name Server Addresses (my router list two), or my LAN port IP Address?

---

### Post by talsemgeest on 2009-09-12
> **woodsonoversoul said:**
> Thanks volkswagner. In response to your first point, which ip address do I use, My Internet Port IP Address, My Internet Port Domain Name Server Addresses (my router list two), or my LAN port IP Address?
That would be your LAN port ip address.

---

### Post by hessiess on 2009-09-12
> **talsemgeest said:**
> It is brilliant if all you are doing is hosting a web site, but if you want ssh, web administration, https, ftp, vmware server... you would have to set up a port forwarding rule for each. And, as long as you keep your computer up to date there is nothing to worry about.

Its still better to only forward the ports you actually need, all it would take is a a security vonribility in one of the servers running and you could be compromised. Always open as few ports as possible.

Run one of the online port scanners like the one at GRC [https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2), click on the proceed button then common ports, this will show your public IP(try accessing your site with this) and your open ports, 80 should show up as being open.

---

### Post by talsemgeest on 2009-09-12
> **hessiess said:**
> Its still better to only forward the ports you actually need, all it would take is a a security vonribility in one of the servers running and you could be compromised. Always open as few ports as possible.

Run one of the online port scanners like the one at GRC [https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2), click on the proceed button then common ports, this will show your public IP(try accessing your site with this) and your open ports, 80 should show up as being open.
However, chances are you will be forwarding the open ports anyway, so it doesn't really make a lot of difference.

---

### Post by woodsonoversoul on 2009-09-12
Accessing the LAN IP Address given by my router (on a laptop connected to my wireless network) just connects my back to my router admin page. Is that right? how does that test apache?

---

### Post by volkswagner on 2009-09-12
> **woodsonoversoul said:**
> Accessing the LAN IP Address given by my router (on a laptop connected to my wireless network) just connects my back to my router admin page. Is that right? how does that test apache?

This does not make sense.  Your router should have it's own local address.  Each machine on the LAN should have all unique addresses.  

If you enter the LAN ip address of your server and get the router page, it could be a NAT thing.

On the server what is the output of

```
ifconfig
```

---

### Post by woodsonoversoul on 2009-09-12
ipconfig returns:

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:89 errors:0 dropped:0 overruns:0 frame:0
          TX packets:89 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7022 (7.0 KB)  TX bytes:7022 (7.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:14:a5:cc:47:5a  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:a5ff:fecc:475a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2632688 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4119927 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:224953610 (224.9 MB)  TX bytes:1311141000 (1.3 GB)

wmaster0  Link encap:UNSPEC  HWaddr 00-14-A5-CC-47-5A-37-35-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


Does it say which ip address I should be using to test the server from my laptop? I want to be sure I'm using the right one...

---

### Post by volkswagner on 2009-09-12
Yes the ip address is present.  I see you are using a wireless adapter.

> 192.168.1.3

To clarify is the server separate from your laptop?

I see you wrote "ipconfig" (typo?), this is a linux server, correct?

When you visit canyousee.org, it should display your external ip address.  What happens when you enter that address in a browser from a machine other than your server?

---

### Post by woodsonoversoul on 2009-09-12
Thanks again volkswagner. When I type the address you quoted in the laptop's browser it tries to connect to local host (it's running an xampp server also). So that seems kind of legit. The website you posted doesn't show me anything about my IP address. Yes it's a linux server and yes that's a typo on my part.

---

### Post by volkswagner on 2009-09-12
Odd.  Here is a screen shot of my system when going to [canyouseeme.org]("http://www.canyouseeme.org/")

So did your apache page load when you entered the "192.168.1.3"?  What happened?

Notice my external ip in the top left corner?

You must have a firewall blocking the function.

Your router status page must also list your external ip.

What type of router are you using?

Do you have a second machine on the LAN to do testing with?

---

### Post by woodsonoversoul on 2009-09-12
When I tried to connect to that address with my laptop it tried to load the localhost page on it's own server (I also have xampp installed on my laptop). I was able to get to canyouseeme.org. It gave me a different ip address than the one you quoted earlier. When I tried to access that from my laptop I got a page that was continually loading...

---

### Post by volkswagner on 2009-09-13
Can you post your apache config files?  

Are you able to connect to your server from you laptop, via ssh?  

How are you connecting to your server for administration?

Is your server connecting to the net?

On your server run:

```
host google.com
```

Do you see the name servers listed?

To clear things up....you are running XAMMP on your server and your laptop?

---

### Post by woodsonoversoul on 2009-09-13
Alright! Using '192.168.1.3' In my router controls, I was able to successfully forward port 80 (Or at least that's what canyouseeme.org says...) One question I have is, why does canyouseeme.org show a different address than '192.168.1.3'? It shows some 68.52.***.* number. And when trying to load '192.168.1.3' in my laptop's browser it loads it's local 'localhost' page. I've never set a firewall up, so unless one is installed by default in Ubuntu 9.04, then I shouldn't have one. My router is a Netgear WGR614v8. I'll plug my laptop into the router and see if that gives me different results than wirelessly...Thanks for all the advice/suggestions

---

### Post by woodsonoversoul on 2009-09-13
Running Xampp software on both laptop and desktop/server. When I enter 'host google.com' into my desktop/server I get :

google.com has address 74.125.127.100
google.com has address 74.125.67.100
google.com has address 74.125.45.100
;; connection timed out; no servers could be reached
google.com mail is handled by 10 smtp3.google.com.
google.com mail is handled by 10 smtp2.google.com.
google.com mail is handled by 100 google.com.s9a2.psmtp.com.
google.com mail is handled by 10 smtp1.google.com.
google.com mail is handled by 10 google.com.s9a1.psmtp.com.

httpd.config is kind of long, but: 

```
#
# This is the main Apache HTTP server configuration file.  It contains the
# configuration directives that give the server its instructions.
# See <URL:http://httpd.apache.org/docs/2.2> for detailed information.
# In particular, see 
# <URL:http://httpd.apache.org/docs/2.2/mod/directives.html>
# for a discussion of each configuration directive.
#
# Do NOT simply read the instructions in here without understanding
# what they do.  They're here only as hints or reminders.  If you are unsure
# consult the online docs. You have been warned.  
#
# Configuration and logfile names: If the filenames you specify for many
# of the server's control files begin with "/" (or "drive:/" for Win32), the
# server will use that explicit path.  If the filenames do *not* begin
# with "/", the value of ServerRoot is prepended -- so "logs/foo.log"
# with ServerRoot set to "/opt/lampp" will be interpreted by the
# server as "/opt/lampp/logs/foo.log".

#
# ServerRoot: The top of the directory tree under which the server's
# configuration, error, and log files are kept.
#
# Do not add a slash at the end of the directory path.  If you point
# ServerRoot at a non-local disk, be sure to point the LockFile directive
# at a local disk.  If you wish to share the same ServerRoot for multiple
# httpd daemons, you will need to change at least LockFile and PidFile.
#
ServerRoot "/opt/lampp"

#
# Listen: Allows you to bind Apache to specific IP addresses and/or
# ports, instead of the default. See also the <VirtualHost>
# directive.
#
# Change this to Listen on specific IP addresses as shown below to 
# prevent Apache from glomming onto all bound IP addresses.
#
#Listen 12.34.56.78:80
Listen 80

#
# Dynamic Shared Object (DSO) Support
#
# To be able to use the functionality of a module which was built as a DSO you
# have to place corresponding `LoadModule' lines at this location so the
# directives contained in it are actually available _before_ they are used.
# Statically compiled modules (those listed by `httpd -l') do not need
# to be loaded here.
#
# Example:
# LoadModule foo_module modules/mod_foo.so
#
LoadModule authn_file_module modules/mod_authn_file.so
LoadModule authn_dbm_module modules/mod_authn_dbm.so
LoadModule authn_anon_module modules/mod_authn_anon.so
LoadModule authn_dbd_module modules/mod_authn_dbd.so
LoadModule authn_default_module modules/mod_authn_default.so
LoadModule authz_host_module modules/mod_authz_host.so
LoadModule authz_groupfile_module modules/mod_authz_groupfile.so
LoadModule authz_user_module modules/mod_authz_user.so
LoadModule authz_dbm_module modules/mod_authz_dbm.so
LoadModule authz_owner_module modules/mod_authz_owner.so
LoadModule authnz_ldap_module modules/mod_authnz_ldap.so
LoadModule authz_default_module modules/mod_authz_default.so
LoadModule auth_basic_module modules/mod_auth_basic.so
LoadModule auth_digest_module modules/mod_auth_digest.so
LoadModule file_cache_module modules/mod_file_cache.so
LoadModule cache_module modules/mod_cache.so
LoadModule disk_cache_module modules/mod_disk_cache.so
LoadModule mem_cache_module modules/mod_mem_cache.so
# mod_dbd doesn't work in Apache 2.2.3: getting always heaps of "glibc detected *** corrupted double-linked list" on shutdown - oswald, 10sep06
#LoadModule dbd_module modules/mod_dbd.so
LoadModule bucketeer_module modules/mod_bucketeer.so
LoadModule dumpio_module modules/mod_dumpio.so
LoadModule echo_module modules/mod_echo.so
LoadModule case_filter_module modules/mod_case_filter.so
LoadModule case_filter_in_module modules/mod_case_filter_in.so
LoadModule ext_filter_module modules/mod_ext_filter.so
LoadModule include_module modules/mod_include.so
LoadModule filter_module modules/mod_filter.so
LoadModule charset_lite_module modules/mod_charset_lite.so
LoadModule deflate_module modules/mod_deflate.so
LoadModule ldap_module modules/mod_ldap.so
LoadModule log_config_module modules/mod_log_config.so
LoadModule logio_module modules/mod_logio.so
LoadModule env_module modules/mod_env.so
LoadModule mime_magic_module modules/mod_mime_magic.so
LoadModule cern_meta_module modules/mod_cern_meta.so
LoadModule expires_module modules/mod_expires.so
LoadModule headers_module modules/mod_headers.so
LoadModule ident_module modules/mod_ident.so
LoadModule usertrack_module modules/mod_usertrack.so
LoadModule unique_id_module modules/mod_unique_id.so
LoadModule setenvif_module modules/mod_setenvif.so
LoadModule proxy_module modules/mod_proxy.so
LoadModule proxy_connect_module modules/mod_proxy_connect.so
LoadModule proxy_ftp_module modules/mod_proxy_ftp.so
LoadModule proxy_http_module modules/mod_proxy_http.so
LoadModule proxy_ajp_module modules/mod_proxy_ajp.so
LoadModule proxy_balancer_module modules/mod_proxy_balancer.so
LoadModule mime_module modules/mod_mime.so
LoadModule dav_module modules/mod_dav.so
LoadModule status_module modules/mod_status.so
LoadModule autoindex_module modules/mod_autoindex.so
LoadModule asis_module modules/mod_asis.so
LoadModule info_module modules/mod_info.so
LoadModule suexec_module modules/mod_suexec.so
LoadModule cgi_module modules/mod_cgi.so
LoadModule cgid_module modules/mod_cgid.so
LoadModule dav_fs_module modules/mod_dav_fs.so
LoadModule vhost_alias_module modules/mod_vhost_alias.so
LoadModule negotiation_module modules/mod_negotiation.so
LoadModule dir_module modules/mod_dir.so
LoadModule imagemap_module modules/mod_imagemap.so
LoadModule actions_module modules/mod_actions.so
LoadModule speling_module modules/mod_speling.so
LoadModule userdir_module modules/mod_userdir.so
LoadModule alias_module modules/mod_alias.so
LoadModule rewrite_module modules/mod_rewrite.so
LoadModule apreq_module modules/mod_apreq2.so
LoadModule ssl_module modules/mod_ssl.so

<IfDefine JUSTTOMAKEAPXSHAPPY>
LoadModule php4_module        modules/libphp4.so
LoadModule php5_module        modules/libphp5.so
</IfDefine>

<IfModule !mpm_winnt_module>
<IfModule !mpm_netware_module>
#
# If you wish httpd to run as a different user or group, you must run
# httpd as root initially and it will switch.  
#
# User/Group: The name (or #number) of the user/group to run httpd as.
# It is usually good practice to create a dedicated user and group for
# running httpd, as with most system services.
#
User nobody
Group nogroup
</IfModule>
</IfModule>

# 'Main' server configuration
#
# The directives in this section set up the values used by the 'main'
# server, which responds to any requests that aren't handled by a
# <VirtualHost> definition.  These values also provide defaults for
# any <VirtualHost> containers you may define later in the file.
#
# All of these directives may appear inside <VirtualHost> containers,
# in which case these default settings will be overridden for the
# virtual host being defined.
#

#
# ServerAdmin: Your address, where problems with the server should be
# e-mailed.  This address appears on some server-generated pages, such
# as error documents.  e.g. admin@your-domain.com
#
ServerAdmin you@example.com

#
# ServerName gives the name and port that the server uses to identify itself.
# This can often be determined automatically, but we recommend you specify
# it explicitly to prevent problems during startup.
#
# If your host doesn't have a registered DNS name, enter its IP address here.
#
#ServerName www.example.com:80
# XAMPP
ServerName localhost

#
# DocumentRoot: The directory out of which you will serve your
# documents. By default, all requests are taken from this directory, but
# symbolic links and aliases may be used to point to other locations.
#
DocumentRoot "/opt/lampp/htdocs"

#
# Each directory to which Apache has access can be configured with respect
# to which services and features are allowed and/or disabled in that
# directory (and its subdirectories). 
#
# First, we configure the "default" to be a very restrictive set of 
# features.  
#
<Directory />
    Options FollowSymLinks
    AllowOverride None
    #XAMPP
    #Order deny,allow
    #Deny from all
</Directory>

#
# Note that from this point forward you must specifically allow
# particular features to be enabled - so if something's not working as
# you might expect, make sure that you have specifically enabled it
# below.
#

#
# This should be changed to whatever you set DocumentRoot to.
#
<Directory "/opt/lampp/htdocs">
    #
    # Possible values for the Options directive are "None", "All",
    # or any combination of:
    #   Indexes Includes FollowSymLinks SymLinksifOwnerMatch ExecCGI MultiViews
    #
    # Note that "MultiViews" must be named *explicitly* --- "Options All"
    # doesn't give it to you.
    #
    # The Options directive is both complicated and important.  Please see
    # http://httpd.apache.org/docs/2.2/mod/core.html#options
    # for more information.
    #
    #Options Indexes FollowSymLinks
    # XAMPP
    Options Indexes FollowSymLinks ExecCGI Includes


    #
    # AllowOverride controls what directives may be placed in .htaccess files.
    # It can be "All", "None", or any combination of the keywords:
    #   Options FileInfo AuthConfig Limit
    #
    #AllowOverride None
    # since XAMPP 1.4:
    AllowOverride All


    #
    # Controls who can get stuff from this server.
    #
    Order allow,deny
    Allow from all

</Directory>

#
# DirectoryIndex: sets the file that Apache will serve if a directory
# is requested.
#
<IfModule dir_module>
    #DirectoryIndex index.html
    # XAMPP
    DirectoryIndex index.html index.html.var index.php index.php3 index.php4
</IfModule>

#
# The following lines prevent .htaccess and .htpasswd files from being 
# viewed by Web clients. 
#
<FilesMatch "^\.ht">
    Order allow,deny
    Deny from all
</FilesMatch>

#
# ErrorLog: The location of the error log file.
# If you do not specify an ErrorLog directive within a <VirtualHost>
# container, error messages relating to that virtual host will be
# logged here.  If you *do* define an error logfile for a <VirtualHost>
# container, that host's errors will be logged there and not here.
#
ErrorLog logs/error_log

#
# LogLevel: Control the number of messages logged to the error_log.
# Possible values include: debug, info, notice, warn, error, crit,
# alert, emerg.
#
LogLevel warn

<IfModule log_config_module>
    #
    # The following directives define some format nicknames for use with
    # a CustomLog directive (see below).
    #
    LogFormat "%h %l %u %t \"%r\" %>s %b \"%{Referer}i\" \"%{User-Agent}i\"" combined
    LogFormat "%h %l %u %t \"%r\" %>s %b" common

    <IfModule logio_module>
      # You need to enable mod_logio.c to use %I and %O
      LogFormat "%h %l %u %t \"%r\" %>s %b \"%{Referer}i\" \"%{User-Agent}i\" %I %O" combinedio
    </IfModule>

    #
    # The location and format of the access logfile (Common Logfile Format).
    # If you do not define any access logfiles within a <VirtualHost>
    # container, they will be logged here.  Contrariwise, if you *do*
    # define per-<VirtualHost> access logfiles, transactions will be
    # logged therein and *not* in this file.
    #
    CustomLog logs/access_log common

    #
    # If you prefer a logfile with access, agent, and referer information
    # (Combined Logfile Format) you can use the following directive.
    #
    #CustomLog logs/access_log combined
</IfModule>

<IfModule alias_module>
    #
    # Redirect: Allows you to tell clients about documents that used to 
    # exist in your server's namespace, but do not anymore. The client 
    # will make a new request for the document at its new location.
    # Example:
    # Redirect permanent /foo http://www.example.com/bar

    #
    # Alias: Maps web paths into filesystem paths and is used to
    # access content that does not live under the DocumentRoot.
    # Example:
    # Alias /webpath /full/filesystem/path
    #
    # If you include a trailing / on /webpath then the server will
    # require it to be present in the URL.  You will also likely
    # need to provide a <Directory> section to allow access to
    # the filesystem path.

    #
    # ScriptAlias: This controls which directories contain server scripts. 
    # ScriptAliases are essentially the same as Aliases, except that
    # documents in the target directory are treated as applications and
    # run by the server when requested rather than as documents sent to the
    # client.  The same rules about trailing "/" apply to ScriptAlias
    # directives as to Alias.
    #
    ScriptAlias /cgi-bin/ "/opt/lampp/cgi-bin/"

</IfModule>

<IfModule cgid_module>
    #
    # ScriptSock: On threaded servers, designate the path to the UNIX
    # socket used to communicate with the CGI daemon of mod_cgid.
    #
    #Scriptsock logs/cgisock
</IfModule>

#
# "/opt/lampp/cgi-bin" should be changed to whatever your ScriptAliased
# CGI directory exists, if you have that configured.
#
<Directory "/opt/lampp/cgi-bin">
    AllowOverride None
    Options None
    Order allow,deny
    Allow from all
</Directory>

#
# DefaultType: the default MIME type the server will use for a document
# if it cannot otherwise determine one, such as from filename extensions.
# If your server contains mostly text or HTML documents, "text/plain" is
# a good value.  If most of your content is binary, such as applications
# or images, you may want to use "application/octet-stream" instead to
# keep browsers from trying to display binary files as though they are
# text.
#
DefaultType text/plain

<IfModule mime_module>
    #
    # TypesConfig points to the file containing the list of mappings from
    # filename extension to MIME-type.
    #
    TypesConfig etc/mime.types

    #
    # AddType allows you to add to or override the MIME configuration
    # file specified in TypesConfig for specific file types.
    #
    #AddType application/x-gzip .tgz
    #
    # AddEncoding allows you to have certain browsers uncompress
    # information on the fly. Note: Not all browsers support this.
    #
    #AddEncoding x-compress .Z
    #AddEncoding x-gzip .gz .tgz
    #
    # If the AddEncoding directives above are commented-out, then you
    # probably should define those extensions to indicate media types:
    #
    AddType application/x-compress .Z
    AddType application/x-gzip .gz .tgz

    #
    # AddHandler allows you to map certain file extensions to "handlers":
    # actions unrelated to filetype. These can be either built into the server
    # or added with the Action directive (see below)
    #
    # To use CGI scripts outside of ScriptAliased directories:
    # (You will also need to add "ExecCGI" to the "Options" directive.)
    #
    #AddHandler cgi-script .cgi
    # XAMPP, since LAMPP 0.9.8:
    AddHandler cgi-script .cgi .pl

    # For files that include their own HTTP headers:
    #AddHandler send-as-is asis

    # For server-parsed imagemap files:
    #AddHandler imap-file map

    # For type maps (negotiated resources):
    #AddHandler type-map var

    #
    # Filters allow you to process content before it is sent to the client.
    #
    # To parse .shtml files for server-side includes (SSI):
    # (You will also need to add "Includes" to the "Options" directive.)
    #
    # XAMPP
    AddType text/html .shtml
    AddOutputFilter INCLUDES .shtml
</IfModule>

#
# The mod_mime_magic module allows the server to use various hints from the
# contents of the file itself to determine its type.  The MIMEMagicFile
# directive tells the module where the hint definitions are located.
#
#MIMEMagicFile etc/magic

#
# Customizable error responses come in three flavors:
# 1) plain text 2) local redirects 3) external redirects
#
# Some examples:
#ErrorDocument 500 "The server made a boo boo."
#ErrorDocument 404 /missing.html
#ErrorDocument 404 "/cgi-bin/missing_handler.pl"
#ErrorDocument 402 http://www.example.com/subscription_info.html
#

#
# EnableMMAP and EnableSendfile: On systems that support it, 
# memory-mapping or the sendfile syscall is used to deliver
# files.  This usually improves server performance, but must
# be turned off when serving from networked-mounted 
# filesystems or if support for these functions is otherwise
# broken on your system.
#
EnableMMAP off
EnableSendfile off

# Supplemental configuration
#
# The configuration files in the etc/extra/ directory can be 
# included to add extra features or to modify the default configuration of 
# the server, or you may simply copy their contents here and change as 
# necessary.

# Server-pool management (MPM specific)
#Include etc/extra/httpd-mpm.conf

# Multi-language error messages
Include etc/extra/httpd-multilang-errordoc.conf

# Fancy directory listings
Include etc/extra/httpd-autoindex.conf

# Language settings
#Include etc/extra/httpd-languages.conf

# User home directories
#Include etc/extra/httpd-userdir.conf

# Real-time info on requests and configuration
#Include etc/extra/httpd-info.conf

# Virtual hosts
#Include etc/extra/httpd-vhosts.conf

# Local access to the Apache HTTP Server Manual
#Include etc/extra/httpd-manual.conf

# Distributed authoring and versioning (WebDAV)
#Include etc/extra/httpd-dav.conf

# Various default settings
Include etc/extra/httpd-default.conf

# Secure (SSL/TLS) connections
<IfModule ssl_module>
# XAMPP
<IfDefine SSL>
Include etc/extra/httpd-ssl.conf
</IfDefine>
</IfModule>
#
# Note: The following must must be present to support
#       starting without SSL on platforms with no /dev/random equivalent
#       but a statically compiled-in mod_ssl.
#
<IfModule ssl_module>
SSLRandomSeed startup builtin
SSLRandomSeed connect builtin
</IfModule>

# XAMPP
Include etc/extra/httpd-xampp.conf
```

I don't know about SSH, I've never tried/don't know how. I'll look up how, though

---

### Post by volkswagner on 2009-09-13
If you are running a desktop version on your server, I would do all your testing on that machine before moving to other networked machines.

Are you sure XAMPP is running?

The following will show you if the service is running.

```
top
```

Try restarting it to see if things change.

```
/opt/lampp/lampp restart
```


You may also try entering the full url to test on your local machine.

[http://localhost/xampp/index.php](http://localhost/xampp/index.php)

Verify you have the index.html or index.php in the correct location.

```
ls -alt /opt/lampp/htdocs
```

You may have better luck on the XAMPP forums, as most folks here are running LAMPP stack.

---

### Post by talsemgeest on 2009-09-13
> **woodsonoversoul said:**
> Alright! Using '192.168.1.3' In my router controls, I was able to successfully forward port 80 (Or at least that's what canyouseeme.org says...) One question I have is, why does canyouseeme.org show a different address than '192.168.1.3'? It shows some 68.52.***.* number. And when trying to load '192.168.1.3' in my laptop's browser it loads it's local 'localhost' page. I've never set a firewall up, so unless one is installed by default in Ubuntu 9.04, then I shouldn't have one. My router is a Netgear WGR614v8. I'll plug my laptop into the router and see if that gives me different results than wirelessly...Thanks for all the advice/suggestions
It shows the different address because it is showing your external IP address, the address of your router to the rest of the internet.

---

### Post by woodsonoversoul on 2009-09-13
The server is runing, it's a music site and I've been listening to it all day

---

### Post by talsemgeest on 2009-09-14
> **woodsonoversoul said:**
> The server is runing, it's a music site and I've been listening to it all day
Glad to hear :)

---

### Post by woodsonoversoul on 2009-09-14
What I mean to say is, the server is running fine on my local machine, I just can't link it to the internet. And what I mean by that is, yes my machine does have internet access, and yes the server software is running, but I can't figure out how to access it from an external machine... Arg.

---

### Post by woodsonoversoul on 2009-09-14
Whoa! Alright! when I type in the address I got from dyndns.com into an external computer's browser it tries to connect to my localhost page!! It says it can't, "establish a connection to the server" but the url changes to "http://localhost/musicneverstopped/index.php" which is where I'm trying to get to! So now, how do I get it to connect to the server? Where could mistakes lie? Thanks to all in advance :)

---

### Post by woodsonoversoul on 2009-09-15
bump for some fresh eyes...Thanks to all who have helped

---

### Post by talsemgeest on 2009-09-16
> **woodsonoversoul said:**
> Whoa! Alright! when I type in the address I got from dyndns.com into an external computer's browser it tries to connect to my localhost page!! It says it can't, "establish a connection to the server" but the url changes to "http://localhost/musicneverstopped/index.php" which is where I'm trying to get to! So now, how do I get it to connect to the server? Where could mistakes lie? Thanks to all in advance :)
Sounds like a problem with the webpage you have on the server, you need to change the location to be the domain name, not "localhost". For example in Wordpress it has the option to change it in the admin control panel.

---

### Post by woodsonoversoul on 2009-09-16
Thanks talsemgeest. I'll start looking in my config files...

---

### Post by woodsonoversoul on 2009-09-16
Do you think it could have something to do with these lines from httpd.config?

```
#
# ServerName gives the name and port that the server uses to identify itself.
# This can often be determined automatically, but we recommend you specify
# it explicitly to prevent problems during startup.
#
# If your host doesn't have a registered DNS name, enter its IP address here.
#
#ServerName www.example.com:80
# XAMPP
ServerName localhost

```

---

### Post by woodsonoversoul on 2009-09-16
changed:
ServerName localhost

to:
ServerName [www.theAddressIGotFromDyndns.com:80](www.theAddressIGotFromDyndns.com:80)

and nothing changed

changed:
Listen 80

to:
Listen ipIGotFromCanyouseeme.org:80

and it broke xampp

it's so weird that it gets the correct file location from [theAddressIGotFromDyndns.com](theAddressIGotFromDyndns.com). It's like it can get to the file, but doesn't have the correct permissions to access it...

---

### Post by woodsonoversoul on 2009-09-16
typing "addressIGotFromDyndns.com".com into mozzilla's url bar tries to access my local host

typing www."addressIGotFromDyndns.com".com into mozzilla's url bar just returns "can't find the server"

Don't know if that's relevant, just adding information.

Also, when I use "addressIGotFromDyndns.com".com the favicon turns into the xampp favicon just for a second before I get "Firefox can't establish a connection to the server at localhost." and then changes into the exclamation point thingy

---

### Post by wojox on 2009-09-16
> **woodsonoversoul said:**
> I am trying to set up a server for a single website. I believe I already have the port forwarded. When I go to my router's admin page and it's port forwarding options I see this set as the only port forwarded...
 # 	Service Name 	Start Port 	End Port 	Server IP Address
 1	HTTP	        80	        80	        192.168.*.*

Did you leave the *.* out on this thread. There in the port forward right ?

Also port forward the same thing with port 443.

---

### Post by woodsonoversoul on 2009-09-16
I'll double check but I'm pretty sure I replaced *.* with the last two digits of the actual ip address, I'm just nervous about giving out my info, and I'm not really knowledgeable so I don't know what should be kept private and what's okay to share.

What does 443 work with? I'll try it as soon as I'm home. Thanks :)

---

### Post by woodsonoversoul on 2009-09-16
bump for the night crew. Any ideas?

---

### Post by wojox on 2009-09-16
443 is for ssl which I couldn't for the life of me get an external connection unless I port forwarded it. It's on by default for Apache2.

---

### Post by woodsonoversoul on 2009-09-16
Damn. Now I'm getting timeout errors. 

danandjen.homelinux.com anyone else getting anything different?

---

### Post by woodsonoversoul on 2009-09-16
Wow. Just for a second today it almost worked. I've been playing with php/mysql/javascript/html for a little over 5 years, and today, for the first time, I almost had something on the web. Now it looks like somehow I've taken a step back and instead of showing the proper address in the url bar it just continually loads until timeout. I forwarded port 443, but then everything went haywire and now I can't even see the server on my local network, so I un-forwarded it. If I get things back to normal I'll try forwarding it again. Back to the drawing board. Any other ideas? Anything of mine (config files, etc.) anyone needs to see?

P.S. I'm not trying to be whiny, I just get really excited thinking how close I am...

---

### Post by woodsonoversoul on 2009-09-16
After forwarding port 443, I unplugged the modem for about 20 sec and the router for 20 sec more. I thought maybe I needed re-start them that way. Could that have caused things to go haywire?

---

### Post by woodsonoversoul on 2009-09-17
bump for today

---

### Post by woodsonoversoul on 2009-09-18
bump for today...

---

### Post by hessiess on 2009-09-19
> **woodsonoversoul said:**
> Wow. Just for a second today it almost worked. I've been playing with php/mysql/javascript/html for a little over 5 years, and today, for the first time, I almost had something on the web. Now it looks like somehow I've taken a step back and instead of showing the proper address in the url bar it just continually loads until timeout. I forwarded port 443, but then everything went haywire and now I can't even see the server on my local network, so I un-forwarded it. If I get things back to normal I'll try forwarding it again. Back to the drawing board. Any other ideas? Anything of mine (config files, etc.) anyone needs to see?

P.S. I'm not trying to be whiny, I just get really excited thinking how close I am...

Your ISP may be blocking external access to ports.

---

### Post by talsemgeest on 2009-09-19
Ignore this post.

---

### Post by mandarin77 on 2009-10-13
okay. i think this is probably simpler than it looks to everyone. As a sidenote, I just setup my humble server with very little to-do. (web server and misc other services, mysql, tomcat, openssh).
 
First thing to note here: Some ISP's block port 80 for web serving, but really not too much anymore. However in my case, **_i locked down my DSL router's firewall soo tight, that it blocked my server_** unless I opened a DMZ to the server. off-hand, i use AT&T Uverse DSL.
 
So, if you use AT&T - log into your DSL router's config page (usually the IP is the one listed for "default gateway"). Go into the firewall advanced settings and open a DMZ to your server. If your server works now, then you have the "outbound firewall" settings too tight. You can keep a DMZ, or you can open a single port and uncheck security settings until your server works again.
 
That was my problem, which was "I can't get a connection from an outside computer."
 
The 192.168.x.x number is the local IP address for a "non-internet" network. You have to "go outside" this network by way of your router to get a "Internet IP" which your router probably has. Your router actually has the internet IP, and you forward ports or the entire IP range (DMZ) to your server. In the DMZ case, your server actually gets some random Internet IP number besides 192.x.x.x which... cuts off the ability to share locally, openly (like Windows XP - share folder to local network - easy), and securely from your server.
 
-------
 
Beyond that, there are endless things to check. Your computer could have a software firewall, but Ubuntu server does not have it on as default. When you get things setup, you want to turn it on. I had to make NO CHANGES to my ubuntu-server software firewall to get my server up and on the internet.
 
If you run your server through a wireless router (different than the DSL/Cable router)... it, too, can have a firewall, and you could also be sub-netting inside a subnet (off-hand, subnetting may not matter to this problem).
 
okay, i'm out for the day.
 
mandarin

---

### Post by dukyle on 2009-11-10
All,

These forums have been very helpful in the past...so hear goes my first request...

*Running Koala Deskop
*XAMPP
*Drupal

drupal directory is /opt..../htdocs/drupal

Am successful when opening browser and going to localhost -> drupal pops up.

Trying to be able to go to localhost/fileserver and get a apache index listing of all folders.

I have a second automatically mounted NTFS hard drive that I use for fileserver

I've modified vhosts & /etc/hosts file
I've allowed in .conf files to read in httpd-vhosts.conf
I've created a symbolic link from /media/fileshare to /opt/.../htdocs/drupal

they only thing i can think of is that I am logged in as a user who does not have ownership of /media/fileserver but have r+w access.

....please don't bump...
thanks.

---

