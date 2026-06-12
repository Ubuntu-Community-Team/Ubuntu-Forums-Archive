---
title: "ASP.NET website using mod_mono configuration"
date: 2019-11-16
forum: Server Platforms
---

### Post by talentdotnet on 2019-11-16
Good morning everybody,
in my **Ubuntu 18.04 LTS Server** I have installed **mod_mono** in order to execute my ASP.NET web site.

I have configured an Apache2 Virtual Host as necessary, and my website run perfect _if I reach it using the IP Address_ of the Server:

**xxx.xxx.xxx.xxx/mywebsite.it/Default.aspx ---> OK**

Then, I have configured the DNS to link the IP Server Address with the name "www.mywebsite.it".

Now, if I try to reach the web site using the registered domain name _I receive a "500 Internal Server Error"_.

**[www.mywebsite.it]("http://www.mywebsite.it") ---> KO!!!! [www.mywebsite.it/Default.aspx]("http://www.mywebsite.it/Default.aspx") ---> KO!!!!**

I don't understand what I can do to correct the problem. I think I have tested all possible configuration, but I'm a new ubuntu user and I move as a nerd.

This is my conf web file:

```
<VirtualHost *:80>
    ServerAdmin talent.dotnet@gmail.com
    ServerName mywebsite.it
    ServerAlias www.mywebsite.it

    DocumentRoot "/var/www/html/mywebsite.it/"

    DirectoryIndex Default.aspx index.php index.html
    MonoAutoApplication disabled
    AddHandler mono .aspx .ascx .asax .ashx .config .cs .vb .asmx .axd

    MonoPath mywebsite.it "/etc/mono/4.5"
    MonoServerPath mywebsite.it /etc/mod-mono-server4
    MonoSetEnv mywebsite.it MONO_IOMAP=all

    Alias /mywebsite.it "var/www/html/mywebsite.it"
    AddMonoApplications mywebsite.it "/:/var/www/html/mywebsite.it"

    ErrorLog ${APACHE_LOG_DIR}/mywebsite.it.it_error.log 
    CustomLog ${APACHE_LOG_DIR}/mywebsite.it_access.log combined 

    <Directory /var/www/html/mywebsite.it/>
        Options Indexes FollowSymLinks
        AllowOverride All
        Require all granted
        #Order allow,deny
        Allow from all
    </Directory>

    <Location "/mywebsite.it">
        #Order allow,deny
        Allow from all
        MonoSetServerAlias mywebsite.it
        SetHandler mono
        SetOutputFilter DEFLATE
        SetEnvIfNoCase Request_URI "\.(?:gif|jpe?g|png)$" no-gzip dont-vary
    </Location>

    <IfModule mod_deflate.c>
        AddOutputFilterByType DEFLATE text/html text/plain text/xml text/javascript
    </IfModule>

</VirtualHost>

```

This is the Apache error.log file (where amac is mywebsite.it):

```
[Fri Nov 08 21:37:32.390392 2019] [mpm_prefork:notice] [pid 18291] AH00169: caught SIGTERM, shutting down
[Fri Nov 08 21:37:33.566970 2019] [so:warn] [pid 20318] AH01574: module mono_module is already loaded, skipping
[Fri Nov 08 21:37:33.620226 2019] [:error] [pid 20324] Failed running '/usr/bin/mod-mono-server2 --filename /tmp/mod_mono_server_global --nonstop --master (null) (null) (null) (null) (null) (null) (null) (null)'. Reason: No such file or directory
[Fri Nov 08 21:37:33.654006 2019] [:error] [pid 20329] Failed running '/usr/bin/mod-mono-server2 --filename /tmp/mod_mono_server_global --nonstop --master (null) (null) (null) (null) (null) (null) (null) (null)'. Reason: No such file or directory
[Fri Nov 08 21:37:33.670365 2019] [:error] [pid 20331] Failed running '/etc/mod-mono-server4 --filename /tmp/mod_mono_server_amac --applications /:/var/www/html/amac --nonstop (null) (null) (null) (null) (null) (null) (null)'. Reason: No such file or directory
[Fri Nov 08 21:37:33.818705 2019] [mpm_prefork:notice] [pid 20322] AH00163: Apache/2.4.29 (Ubuntu) mod_mono/3.13 OpenSSL/1.1.1d configured -- resuming normal operations
[Fri Nov 08 21:37:33.818741 2019] [core:notice] [pid 20322] AH00094: Command line: '/usr/sbin/apache2'
[Fri Nov 08 21:37:38.113890 2019] [:error] [pid 20381] Failed running '/etc/mod-mono-server4 --filename /tmp/mod_mono_server_amac --applications /:/var/www/html/amac --nonstop (null) (null) (null) (null) (null) (null) (null)'. Reason: No such file or directory
[Fri Nov 08 21:37:40.136482 2019] [:error] [pid 20406] Failed running '/etc/mod-mono-server4 --filename /tmp/mod_mono_server_amac --applications /:/var/www/html/amac --nonstop (null) (null) (null) (null) (null) (null) (null)'. Reason: No such file or directory
[Fri Nov 08 21:37:42.154300 2019] [:error] [pid 20442] Failed running '/etc/mod-mono-server4 --filename /tmp/mod_mono_server_amac --applications /:/var/www/html/amac --nonstop (null) (null) (null) (null) (null) (null) (null)'. Reason: No such file or directory
[Fri Nov 08 21:37:44.146976 2019] [:error] [pid 20335] Failed to connect to mod-mono-server after several attempts to spawn the process.
[Fri Nov 08 21:37:44.231098 2019] [:error] [pid 20447] Failed running '/etc/mod-mono-server4 --filename /tmp/mod_mono_server_amac --applications /:/var/www/html/amac --nonstop (null) (null) (null) (null) (null) (null) (null)'. Reason: No such file or directory
[Fri Nov 08 21:37:46.242551 2019] [:error] [pid 20562] Failed running '/etc/mod-mono-server4 --filename /tmp/mod_mono_server_amac --applications /:/var/www/html/amac --nonstop (null) (null) (null) (null) (null) (null) (null)'. Reason: No such file or directory
[Fri Nov 08 21:37:48.256714 2019] [:error] [pid 20565] Failed running '/etc/mod-mono-server4 --filename /tmp/mod_mono_server_amac --applications /:/var/www/html/amac --nonstop (null) (null) (null) (null) (null) (null) (null)'. Reason: No such file or directory
[Fri Nov 08 21:37:50.251437 2019] [:error] [pid 20336] Failed to connect to mod-mono-server after several attempts to spawn the process.

```

---

### Post by QIII on 2019-11-16
Moved to Server Platforms as a better fit.

---

### Post by talentdotnet on 2019-11-16
ok thank you very much. I hope someone could help me.

---

