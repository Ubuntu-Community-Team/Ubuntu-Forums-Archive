---
title: "Automated setup script"
date: 2012-07-26
forum: Server Platforms
---

### Post by sandyd on 2012-07-26
I currently host a few people on my webserver, and I want to make it a more automated process.

During the process, I need to

a) Create the user with a specific uid (all hosted people are created under the 2xxx uids) on the NFS server, which hosts all the files.
b) Create the user with the same uid/gid on the webserver, so that they can access the files on the NFS server
c) Create a pure-ftpd user (using puredb), while setting the uid/gid

So far, all of that has been figured out.

[s]What I havent:[/s]
d) Copy over a default nginx user file, and add the username as the virtualhost (i.e. $name.sandyd.me), and add the username in order to have a seperate log file). Add the username to the php-fpm section as well.

e) Copy over a default php-fpm config, and add the username/group to  allow them to have a seperate php-fpm process.

[s]Any idea how to accomplish the above?[/s]

[B]All done!

* Scripts below updated.
[/B] 
#current bash script
```

#!/bin/bash

#last UID/GID used
cur_uid="/opt/user_setup/cur_uid"

#List of used usernames
usr_list="/opt/user_setup/usr_list"

#Get Unused GID
gid=$(($(cat $cur_id)+1))

uid=$gid
echo $gid > $cur_uid

echo -n "Please enter the desired username: "
read name

if [ $name == "" ]; then
    echo "Cannot use an empty username"
    exit 1

grep -i "$name" "$usr_list"

elif      [ $? == 0 ]; then
    echo "Username already in use"
    exit 1
else
    echo "$name" > $usr_list
    #SSH to NFS to setup the user accounts
    echo "Setting up user account on NFS"
    ssh root@10.0.0.1 -c groupadd -g $gid $name
    ssh root@10.0.0.1 -c useradd -u $uid -g $gid -M -N $name

    #NFS and Webserver usernames should have same UID to allow access
    groupadd -g $gid $name
    useradd -u $uid -g $gid -M -N -Z guest_u $name

    #chown the folders used for holding the files
    echo "Setting NFS user permissions"
    ssh root@10.0.0.1 -c mkdir /opt/backup/main/home/$name
    ssh root@10.0.0.1 -c chown $name:$name /opt/backup/main/home/$name

    #create the ftp users
    echo "Setting up pure-ftpd user"
    pure-pw useradd -u $uid -g $gid -d /opt/nfs/main/home/$name
    
    #Create the Nginx virtual host
    echo "Setting up nginx"
    sed "s/_username_/$name/" /etc/nginx/vh_templates/default > /etc/nginx/sites/$name

    #Setup a php-fpm process for user
    echo "Setting up php"
    mkdir /opt/php/sesh/$name
    chown $name:$name /opt/php/sesh/$name
    sed "s/_username_/$name/" /etc/php-fpm.d/default > /etc/php-fpm.d/$name.conf

    #Restarting all services
    
    #Restart Varnish (clear cache)
    service varnish restart

    #Restart php-fpm
    service php-fpm restart

    #Restart Nginx
    service nginx restart
fi
echo "Setup Complete!"

```/etc/nginx/vh_templates/default
```
server {
    listen 127.0.0.1:80;
#        listen 63.141.254.9:80;
#       listen somename:8080;
        server_name _username_.sandyd.me 63.141.254.19;
    port_in_redirect off;
        root /opt/nfs/main/home/_username_/public_html;
    error_log /var/log/nginx/sites/_username_.sandyd.me_error_log warn;
        index index.html index.htm index.php;
    set_real_ip_from 127.0.0.1;
    real_ip_header X-Forwarded-For;
        autoindex on;

        location ~ \.php$ {    
        try_files $uri =404;
                fastcgi_pass unix:/var/run/php-fpm/php-fpm-_username_.sock;
                fastcgi_index index.php;
                include fastcgi_params;
        }
}

```/etc/opt/php-fpm.d/default
```

[$name]

; The address on which to accept FastCGI requests.
; Valid syntaxes are:
;   'ip.add.re.ss:port'    - to listen on a TCP socket to a specific address on
;                            a specific port;
;   'port'                 - to listen on a TCP socket to all addresses on a
;                            specific port;
;   '/path/to/unix/socket' - to listen on a unix socket.
; Note: This value is mandatory.
listen = /var/run/php-fpm/php-fpm-_username_.sock

; Set listen(2) backlog. A value of '-1' means unlimited.
; Default Value: -1
;listen.backlog = -1
 
; List of ipv4 addresses of FastCGI clients which are allowed to connect.
; Equivalent to the FCGI_WEB_SERVER_ADDRS environment variable in the original
; PHP FCGI (5.2.2+). Makes sense only with a tcp listening socket. Each address
; must be separated by a comma. If this value is left blank, connections will be
; accepted from any ip address.
; Default Value: any
;listen.allowed_clients = 127.0.0.1

; Set permissions for unix socket, if one is used. In Linux, read/write
; permissions must be set in order to allow connections from a web server. Many
; BSD-derived systems allow connections regardless of permissions. 
; Default Values: user and group are set as the running user
;                 mode is set to 0666
listen.owner = nginx
listen.group = nginx
listen.mode = 0777

; Unix user/group of processes
; Note: The user is mandatory. If the group is not set, the default user's group
;       will be used.
; RPM: apache Choosed to be able to access some dir as httpd
user = _username_
; RPM: Keep a group allowed to write in log dir.
group = _username_

; Choose how the process manager will control the number of child processes.
; Possible Values:
;   static  - a fixed number (pm.max_children) of child processes;
;   dynamic - the number of child processes are set dynamically based on the
;             following directives:
;             pm.max_children      - the maximum number of children that can
;                                    be alive at the same time.
;             pm.start_servers     - the number of children created on startup.
;             pm.min_spare_servers - the minimum number of children in 'idle'
;                                    state (waiting to process). If the number
;                                    of 'idle' processes is less than this
;                                    number then some children will be created.
;             pm.max_spare_servers - the maximum number of children in 'idle'
;                                    state (waiting to process). If the number
;                                    of 'idle' processes is greater than this
;                                    number then some children will be killed.
; Note: This value is mandatory.
pm = dynamic

; The number of child processes to be created when pm is set to 'static' and the
; maximum number of child processes to be created when pm is set to 'dynamic'.
; This value sets the limit on the number of simultaneous requests that will be
; served. Equivalent to the ApacheMaxClients directive with mpm_prefork.
; Equivalent to the PHP_FCGI_CHILDREN environment variable in the original PHP
; CGI.
; Note: Used when pm is set to either 'static' or 'dynamic'
; Note: This value is mandatory.
pm.max_children = 30

; The number of child processes created on startup.
; Note: Used only when pm is set to 'dynamic'
; Default Value: min_spare_servers + (max_spare_servers - min_spare_servers) / 2
pm.start_servers = 10

; The desired minimum number of idle server processes.
; Note: Used only when pm is set to 'dynamic'
; Note: Mandatory when pm is set to 'dynamic'
pm.min_spare_servers = 5

; The desired maximum number of idle server processes.
; Note: Used only when pm is set to 'dynamic'
; Note: Mandatory when pm is set to 'dynamic'
pm.max_spare_servers = 20
 
; The number of requests each child process should execute before respawning.
; This can be useful to work around memory leaks in 3rd party libraries. For
; endless request processing specify '0'. Equivalent to PHP_FCGI_MAX_REQUESTS.
; Default Value: 0
;pm.max_requests = 500

; The URI to view the FPM status page. If this value is not set, no URI will be
; recognized as a status page. By default, the status page shows the following
; information:
;   accepted conn    - the number of request accepted by the pool;
;   pool             - the name of the pool;
;   process manager  - static or dynamic;
;   idle processes   - the number of idle processes;
;   active processes - the number of active processes;
;   total processes  - the number of idle + active processes.
; The values of 'idle processes', 'active processes' and 'total processes' are
; updated each second. The value of 'accepted conn' is updated in real time.
; Example output:
;   accepted conn:   12073
;   pool:             www
;   process manager:  static
;   idle processes:   35
;   active processes: 65
;   total processes:  100
; By default the status page output is formatted as text/plain. Passing either
; 'html' or 'json' as a query string will return the corresponding output
; syntax. Example:
;   http://www.foo.bar/status
;   http://www.foo.bar/status?json
;   http://www.foo.bar/status?html
; Note: The value must start with a leading slash (/). The value can be
;       anything, but it may not be a good idea to use the .php extension or it
;       may conflict with a real PHP file.
; Default Value: not set 
;pm.status_path = /status
 
; The ping URI to call the monitoring page of FPM. If this value is not set, no
; URI will be recognized as a ping page. This could be used to test from outside
; that FPM is alive and responding, or to
; - create a graph of FPM availability (rrd or such);
; - remove a server from a group if it is not responding (load balancing);
; - trigger alerts for the operating team (24/7).
; Note: The value must start with a leading slash (/). The value can be
;       anything, but it may not be a good idea to use the .php extension or it
;       may conflict with a real PHP file.
; Default Value: not set
;ping.path = /ping

; This directive may be used to customize the response of a ping request. The
; response is formatted as text/plain with a 200 response code.
; Default Value: pong
;ping.response = pong
 
; The timeout for serving a single request after which the worker process will
; be killed. This option should be used when the 'max_execution_time' ini option
; does not stop script execution for some reason. A value of '0' means 'off'.
; Available units: s(econds)(default), m(inutes), h(ours), or d(ays)
; Default Value: 0
;request_terminate_timeout = 0
 
; The timeout for serving a single request after which a PHP backtrace will be
; dumped to the 'slowlog' file. A value of '0s' means 'off'.
; Available units: s(econds)(default), m(inutes), h(ours), or d(ays)
; Default Value: 0
;request_slowlog_timeout = 0
 
; The log file for slow requests
; Default Value: not set
; Note: slowlog is mandatory if request_slowlog_timeout is set
slowlog = /var/log/php-fpm/www-slow.log
 
; Set open file descriptor rlimit.
; Default Value: system defined value
;rlimit_files = 1024
 
; Set max core size rlimit.
; Possible Values: 'unlimited' or an integer greater or equal to 0
; Default Value: system defined value
;rlimit_core = 0
 
; Chroot to this directory at the start. This value must be defined as an
; absolute path. When this value is not set, chroot is not used.
; Note: chrooting is a great security feature and should be used whenever 
;       possible. However, all PHP paths will be relative to the chroot
;       (error_log, sessions.save_path, ...).
; Default Value: not set
;chroot = 
 
; Chdir to this directory at the start. This value must be an absolute path.
; Default Value: current directory or / when chroot
;chdir = /var/www
 
; Redirect worker stdout and stderr into main error log. If not set, stdout and
; stderr will be redirected to /dev/null according to FastCGI specs.
; Default Value: no
;catch_workers_output = yes
 
; Limits the extensions of the main script FPM will allow to parse. This can
; prevent configuration mistakes on the web server side. You should only limit
; FPM to .php extensions to prevent malicious users to use other extensions to
; exectute php code.
; Note: set an empty value to allow all extensions.
; Default Value: .php
;security.limit_extensions = .php .php3 .php4 .php5

; Pass environment variables like LD_LIBRARY_PATH. All $VARIABLEs are taken from
; the current environment.
; Default Value: clean env
;env[HOSTNAME] = $HOSTNAME
;env[PATH] = /usr/local/bin:/usr/bin:/bin
;env[TMP] = /tmp
;env[TMPDIR] = /tmp
;env[TEMP] = /tmp

; Additional php.ini defines, specific to this pool of workers. These settings
; overwrite the values previously defined in the php.ini. The directives are the
; same as the PHP SAPI:
;   php_value/php_flag             - you can set classic ini defines which can
;                                    be overwritten from PHP call 'ini_set'. 
;   php_admin_value/php_admin_flag - these directives won't be overwritten by
;                                     PHP call 'ini_set'
; For php_*flag, valid values are on, off, 1, 0, true, false, yes or no.

; Defining 'extension' will load the corresponding shared extension from
; extension_dir. Defining 'disable_functions' or 'disable_classes' will not
; overwrite previously defined php.ini values, but will append the new value
; instead.

; Default Value: nothing is defined by default except the values in php.ini and
;                specified at startup with the -d argument
;php_admin_value[sendmail_path] = /usr/sbin/sendmail -t -i -f www@my.domain.com
;php_flag[display_errors] = off
php_admin_value[error_log] = /opt/php/logs/_username_.sandyd.me.log
php_admin_value[session.save_path] = /opt/php/sesh/_username_
php_admin_flag[log_errors] = on
php_admin_value[memory_limit] = 256M

```

---

### Post by koenn on 2012-07-26
would this work :

- in the files, replace the $name with a litteral placeholder, eg xNAMEx

- in your script, copy the files, then run sed to replace the placeholder with the value of your $name variable

proof of concept:
```


:~$ cat testfile
this is about xNAMEx

:~$ name=koenn

:~$ sed -i s/xNAMEx/$name/g testfile

:~$ cat testfile
this is about koenn


```

You'll need to organize it a bit, eg make a temp copy, sed it, copy it vs sed the file and redirect the output to it's final destination  vs copy the file, edit it, ... 
I'm sure you're capable of working out the details.

---

### Post by sandyd on 2012-07-26
> **koenn said:**
> would this work :

- in the files, replace the $name with a litteral placeholder, eg xNAMEx

- in your script, copy the files, then run sed to replace the placeholder with the value of your $name variable

proof of concept:
```


:~$ cat testfile
this is about xNAMEx

:~$ name=koenn

:~$ sed -i s/xNAMEx/$name/g testfile

:~$ cat testfile
this is about koenn


```You'll need to organize it a bit, eg make a temp copy, sed it, copy it vs sed the file and redirect the output to it's final destination  vs copy the file, edit it, ... 
I'm sure you're capable of working out the details.
thanks koenn - this worked out great!

---

### Post by koenn on 2012-07-27
> **sandyd said:**
> thanks koenn - this worked out great!
my pleasure.

---

